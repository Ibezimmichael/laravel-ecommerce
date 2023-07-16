<template>
    <div v-if="currentUser.id"  class="min-h-full bg-gray-200 flex">
        <!-- side bar -->
        <SideBar :class="{'-ml-[200px]': !sidebarOpened}"/>

        <div class="flex-1">
            <Navbar @toggle-sidebar="toggleSidebar"></Navbar>

        <main class="p-6">
            <div class="p-4 rounded bg-white">
                <router-view></router-view>
            </div>
        </main>
        <!--      Content-->
        </div>
    </div>
    <div v-else class="min-h-full bg-gray-200 flex items-center justify-center">
        <Spinner/>
    </div>
</template>


<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue';
import SideBar from './SideBar.vue';
import Navbar from './Navbar.vue';
import store from '../store';
import Spinner from './core/Spinner.vue';

const {title} = defineProps({
    title: String
});

const currentUser = computed(() => store.state.user.data);


const sidebarOpened = ref(true);

function toggleSidebar() {
    sidebarOpened.value = !sidebarOpened.value
}
function handleSidebarOpened() {
    sidebarOpened.value = window.outerWidth > 768;

}

onMounted(() => {
    store.dispatch('getUser')
    handleSidebarOpened();
    window.addEventListener('resize', handleSidebarOpened);
})

onUnmounted(() => {
    window.removeEventListener('resize', handleSidebarOpened);
});



</script>

<style scoped>
</style>

