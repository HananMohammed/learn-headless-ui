<template>
  <div class="min-h-screen bg-gray-200 text-gray-900">
    <div class="container mx-auto">
      <h5 class="font-bold text-xl pt-2"> Menu (Dropdown)</h5>

      <Menu>
        <MenuButton class="flex items-center bg-blue-400 text-white rounded px-4 py-2">
          <span>More</span>
          <ChevronDownIcon class="w-5 h-5 ml-2"/>
        </MenuButton>

        <transition enter-active-class="transition duration-200 ease-out"
                    enter-from-class="transform scale-75 opacity-0"
                    enter-to-class="transform scale-100 opacity-100"
                    leave-active-class="transition duration-100 ease-in"
                    leave-from-class="transform scale-100 opacity-100"
                    leave-to-class="transform scale-75 opacity-0">

          <MenuItems class="absolute bg-white rounded-lg shadow-md flex flex-col focus:outline-none mt-2 w-56 origin-top-left">
            <div class="px-1 py-1">
              <MenuItem v-slot="{ active }">
                <button :class="[
                    active ? 'bg-violet-500 text-white' : 'text-gray-900',
                    'group flex w-full items-center rounded-md px-2 py-2 text-sm',
                  ]">
                  <PencilSquareIcon class="mr-2 h-5 w-5 text-violet-400"/>
                  <span class="ml-2">Edit</span>
                </button>
              </MenuItem>

              <MenuItem v-slot="{ active }">
                <button :class="[
                    active ? 'bg-violet-500 text-white' : 'text-gray-900',
                    'group flex w-full items-center rounded-md px-2 py-2 text-sm',
                  ]">
                  <TrashIcon class="mr-2 h-5 w-5 text-violet-400"/>
                  <span class="ml-2">Delete</span>
                </button>
              </MenuItem>
            </div>

            <div class="px-1 py-1">
              <MenuItem v-slot="{ active }">
                <button
                    :class="[
                    active ? 'bg-violet-500 text-white' : 'text-gray-900',
                    'group flex w-full items-center rounded-md px-2 py-2 text-sm',
                  ]"
                >
                  <ArchiveBoxIcon
                      :active="active"
                      class="mr-2 h-5 w-5 text-violet-400"
                      aria-hidden="true"
                  />
                  Archive
                </button>
              </MenuItem>
              <MenuItem v-slot="{ active }">
                <button
                    :class="[
                    active ? 'bg-violet-500 text-white' : 'text-gray-900',
                    'group flex w-full items-center rounded-md px-2 py-2 text-sm',
                  ]"
                >
                  <TicketIcon
                      :active="active"
                      class="mr-2 h-5 w-5 text-violet-400"
                      aria-hidden="true"
                  />
                  Move
                </button>
              </MenuItem>
            </div>

          </MenuItems>
        </transition>
      </Menu>


    </div>
  </div>
</template>

<script setup>
import {Menu, MenuButton, MenuItems, MenuItem} from '@headlessui/vue'
import {ChevronDownIcon, PencilSquareIcon, TrashIcon, ArchiveBoxIcon, TicketIcon} from '@heroicons/vue/24/solid'

</script>

<style scoped>

</style>
