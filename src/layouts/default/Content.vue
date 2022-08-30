
<script setup lang="ts">
import { ref } from "vue";
import router from "@/router";

const getUrl = (index: number) => {
  return router.currentRoute.value.path.split('/').slice(0,index+1).join('/');
}
</script>
<template>
  <n-layout-content content-style="padding: 24px; min-height: 85vh">
    <n-breadcrumb v-for="(v,i) in $route.path.split('/')">
      <n-breadcrumb-item>
        <router-link :to="{ path:getUrl(i) }">
          {{  v  }}
        </router-link>
      </n-breadcrumb-item>
    </n-breadcrumb>
    <router-view />
  </n-layout-content>
</template>
