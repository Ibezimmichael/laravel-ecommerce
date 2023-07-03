<template>
    <header class="flex justify-between items-center p-2 h-14 shadow bg-white">
        <button @click="emit('toggle-sidebar')"  class="flex items-center justify-center rounded transition-colors w-8 h-8  text-gray-500 hover:bg-black/10">
            <svg xmlns="http://www.w3.org/2000/svg"  class="w-10" fill="none" viewBox="0 0 24 24" strokeWidth={1.5} stroke="currentColor" className="w-6 h-6">
                <path strokeLinecap="round" strokeLinejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5" />
              </svg>
        </button>

        <!-- <div class="px-4"> -->
            <Menu as="div" class="mr-4 relative inline-block text-left">
                <div>
                  <MenuButton
                    class="flex items-center"
                  >
                    <img src="https://randomuser.me/api/portraits/men/49.jpg" alt="" class="rounded-full w-8 mr-2">
                    <small>{{currentUser.name}}</small>
                    <ChevronDownIcon
                      class="ml-2 -mr-1 h-5 w-5 text-indigo-200 hover:text-indigo-100"
                      aria-hidden="true"
                    />
                  </MenuButton>
                </div>

                <transition
                  enter-active-class="transition duration-100 ease-out"
                  enter-from-class="transform scale-95 opacity-0"
                  enter-to-class="transform scale-100 opacity-100"
                  leave-active-class="transition duration-75 ease-in"
                  leave-from-class="transform scale-100 opacity-100"
                  leave-to-class="transform scale-95 opacity-0"
                >
                  <MenuItems
                    class="absolute right-0 mt-2 w-30 origin-top-right divide-y divide-gray-100 rounded-md bg-white shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none"
                  >
                    <div class="px-1 py-1">
                      <MenuItem v-slot="{ active }" class="mr-7">
                        <button
                          :class="[
                            active ? 'bg-indigo-500 text-white' : 'text-gray-900',
                            'group flex w-full items-center rounded-md px-2 py-2 text-sm',
                          ]"
                        >

                          <svg xmlns="http://www.w3.org/2000/svg" class=" mr-2 w-6 h-6" viewBox="0 0 24 24" fill="currentColor" className="w-6 h-6">
                            <path fillRule="evenodd" d="M18.685 19.097A9.723 9.723 0 0021.75 12c0-5.385-4.365-9.75-9.75-9.75S2.25 6.615 2.25 12a9.723 9.723 0 003.065 7.097A9.716 9.716 0 0012 21.75a9.716 9.716 0 006.685-2.653zm-12.54-1.285A7.486 7.486 0 0112 15a7.486 7.486 0 015.855 2.812A8.224 8.224 0 0112 20.25a8.224 8.224 0 01-5.855-2.438zM15.75 9a3.75 3.75 0 11-7.5 0 3.75 3.75 0 017.5 0z" clipRule="evenodd" />
                          </svg>


                          Profile
                        </button>
                      </MenuItem>
                      <MenuItem v-slot="{ active }" class="mr-7">
                        <button
                            @click="logout"
                          :class="[
                            active ? 'bg-indigo-500 text-white' : 'text-gray-900',
                            'group flex w-full items-center rounded-md px-2 py-2 text-sm',
                          ]"
                        >
                          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6 mr-2">
                            <path fill-rule="evenodd" d="M7.5 3.75A1.5 1.5 0 006 5.25v13.5a1.5 1.5 0 001.5 1.5h6a1.5 1.5 0 001.5-1.5V15a.75.75 0 011.5 0v3.75a3 3 0 01-3 3h-6a3 3 0 01-3-3V5.25a3 3 0 013-3h6a3 3 0 013 3V9A.75.75 0 0115 9V5.25a1.5 1.5 0 00-1.5-1.5h-6zm5.03 4.72a.75.75 0 010 1.06l-1.72 1.72h10.94a.75.75 0 010 1.5H10.81l1.72 1.72a.75.75 0 11-1.06 1.06l-3-3a.75.75 0 010-1.06l3-3a.75.75 0 011.06 0z" clip-rule="evenodd" />
                          </svg>

                          Logout
                        </button>
                      </MenuItem>
                    </div>

                  </MenuItems>
                </transition>
              </Menu>
        <!-- </div> -->
    </header>


</template>

<script setup>
import { RouterLink } from 'vue-router';

import { Menu, MenuButton, MenuItems, MenuItem } from '@headlessui/vue'
import { ChevronDownIcon } from '@heroicons/vue/20/solid'
import store from '../store';
import router from '../router';
import { computed } from 'vue';


const emit = defineEmits(['toggle-sidebar'])

const currentUser = computed(() => store.state.user.data);

function logout(){
    store.dispatch('logout')
        .then(() => {
            router.push({name: 'login'})
        })
}


</script>

<style scoped>
</style>
