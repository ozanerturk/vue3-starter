<script setup lang="ts">
import { ref } from "vue";
let points = ref([1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);
</script>
    <template>
    <ul>
        <li v-for="v in points" v-bind:key="v">
            <router-link :to="{ name: 'point-details', params: { customerId: $route.params.customerId, pointId: v } }">
                Point {{  v  }}
            </router-link>
        </li>
    </ul>

</template>