<template>
  <n-layout-sider
    :width="220"
    :native-scrollbar="false"
    :collapsed="collapsed"
    collapse-mode="width"
    show-trigger="bar"
    bordered
    @update:collapsed="toggle"
  >
    <router-link to="/" #="{ navigate, href }" custom>
      <n-a class="logo" :href="href" @click="navigate">
       
        <span>RES Portal</span>
      </n-a>
    </router-link>
    <n-menu
      :value="currentKey"
      :default-expanded-keys="expandedKeys"
      :options="options"
      :root-indent="18"
      @update:value="
        (k) => {
          currentKey = k;
        }
      "
    />
  </n-layout-sider>
</template>

<script lang="ts" setup>
import { h, ref, computed, watchEffect } from "vue";

import { useRoute, RouterLink } from "vue-router";
import type { MenuOption } from "naive-ui";
import type { MenuType } from "@/composables/useMenu";
import { MenuItems } from "@/composables/useMenu";
import { useUserStore } from "@/stores/user";
import Icon from "@/components/Icon.vue";
const userStore = useUserStore();
const collapsed = computed(() => userStore.sidebarCollapsed);

const toggle = async (): Promise<void> =>
  await userStore.toggleSidebarCollapsed();
const menus = MenuItems();
const mapping = (items: MenuType[]): MenuOption[] =>
  items.map((item) => ({
    ...item,
    key: item.id,
    label:
      item.name != null
        ? () => h(RouterLink, { to: item }, { default: () => item.label })
        : item.label,
    icon: item.icon != null ? () => h(Icon, { type: item.icon }) : undefined,
    children: item.children && mapping(item.children),
  }));

const options = computed(() => (menus ? mapping(menus) : []));

const route = useRoute();
const currentKey = ref<string>("");
const expandedKeys = ref<string[]>([]);

const routeMatched = (menu: MenuType): boolean => {
  return (
    route.name === menu.name &&
    (menu.params == null ||
      JSON.stringify(route.params) === JSON.stringify(menu.params))
  );
}

const matchExpanded = (items: MenuType[]): boolean => {
  let matched = false;
  for (const item of items) {
    if (item.children != null) {
      matchExpanded(item.children) && expandedKeys.value.push(item.id);
    }
    if (routeMatched(item)) {
      currentKey.value = item.id;
      matched = true;
    }
  }
  return matched;
}

watchEffect(() => menus && matchExpanded(menus));
</script>

<style scoped>
.logo {
  position: sticky;
  top: 0;
  z-index: 1;
  display: flex;
  align-items: center;
  padding: 12px 20px;
  background: var(--color);
  font-size: 1.8em;
  font-weight: 600;
  line-height: 1;
  text-decoration: none;
  transition: padding 0.3s var(--bezier), font-size 0.3s var(--bezier);
}

.n-layout-sider--collapsed .logo {
  padding: 8px;
  font-size: 0;
}

.logo svg {
  flex: 0 0 32px;
  height: 32px;
  margin-right: 12px;
  transition: margin 0.3s var(--bezier);
}

.n-layout-sider--collapsed .logo svg {
  margin-right: 0;
}
</style>
