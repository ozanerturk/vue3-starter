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
        <svg
          id="Layer_1"
          version="1.1"
          xmlns="http://www.w3.org/2000/svg"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          x="0px"
          y="0px"
          width="602px"
          height="473px"
          viewBox="0 0 602 473"
          enable-background="new 0 0 602 473"
          xml:space="preserve"
        >
          <image
            id="image0"
            width="602"
            height="473"
            x="0"
            y="0"
            href="data:image/png;base64,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
RK5CYII="
          />
        </svg>
        <span>Devstack</span>
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