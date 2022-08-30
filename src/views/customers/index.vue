<script setup lang="ts">
import { ref } from "vue";
let customers = ref([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);
</script>
<template>
    <br>
    <ul>
        <li v-for="v in customers" v-bind:key="v">
            <router-link :to="{ name: 'customer-details', params: { customerId: v } }">
                Customer {{  v  }}
            </router-link>
        </li>
    </ul>
    <router-view></router-view>

</template>