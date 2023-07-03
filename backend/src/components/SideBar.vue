<template>
    <div class="w-[200px] transition-all bg-indigo-700 text-gray-300 py-4 px-2">
        <RouterLink :to="{name: 'app.dashboard'}"
            class="flex items-center py-1 px-3 rounded transition-colors hover:bg-black/10 mb-2">
            <span class="mr-3"><i class="bi bi-house-door "></i></span>
            <span class="">Dashboard</span>

        </RouterLink>
        <RouterLink :to="{name: 'app.products'}"
            class="flex items-center py-1 px-3 rounded transition-colors hover:bg-black/10 mb-2">
            <span class="mr-3"><i class="bi bi-list"></i></span>
            <span>Products</span>

        </RouterLink>
        <RouterLink :to="{name: 'app.dashboard'}"
            class="flex items-center py-1 px-3 rounded transition-colors hover:bg-black/10 mb-2">
            <span class="mr-3"><i class="bi bi-people"></i></span>
            <span>Users</span>

        </RouterLink>
        <RouterLink :to="{name: 'app.dashboard'}"
            class="flex items-center py-1 px-3 rounded transition-colors hover:bg-black/10 mb-2">
            <span class="mr-3"><i class="bi bi-reception-4"></i></span>
            <span>Reports</span>

        </RouterLink>
    </div>

</template>

<script setup>
import { RouterLink } from 'vue-router';


</script>

<style scoped>
</style>
