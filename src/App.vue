<template>
  <div class="min-h-screen bg-gray-200 text-gray-900">
    <div class="container mx-auto">
      <h5 class="font-bold text-xl pt-2"> Dialog (Modal)</h5>

      <button class="flex items-center bg-blue-400 text-white rounded px-4 py-2"
              @click="openModal">
          open Modal
      </button>

      <TransitionRoot appear :show="isOpen" as="template">
        <Dialog as="div" @close="closeModal" class="relative z-10">
          <TransitionChild
              as="template"
              enter="duration-300 ease-out"
              enter-from="opacity-0"
              enter-to="opacity-100"
              leave="duration-200 ease-in"
              leave-from="opacity-100"
              leave-to="opacity-0"
          >
            <div class="fixed inset-0 bg-black/25" />
          </TransitionChild>

          <div class="fixed inset-0 overflow-y-auto">
            <div
                class="flex min-h-full items-center justify-center p-4 text-center"
            >
              <TransitionChild
                  as="template"
                  enter="duration-300 ease-out"
                  enter-from="opacity-0 scale-95 rotate-180"
                  enter-to="opacity-100 scale-100 rotate-0"
                  leave="duration-200 ease-in"
                  leave-from="opacity-100 scale-100 rotate-0"
                  leave-to="opacity-0 scale-95 rotate-180"
              >
                <DialogPanel
                    class="w-full max-w-md transform overflow-hidden rounded-2xl bg-white p-6 text-left align-middle shadow-xl transition-all"
                >
                  <DialogTitle
                      as="h3"
                      class="text-lg font-medium leading-6 text-gray-900"
                  >
                    Payment successful
                    <button class="absolute top-3 right-3"   @click="closeModal">
                      <XCircleIcon class="h-5 w-5 text-gray-500" />
                    </button>
                  </DialogTitle>
                  <div class="mt-2">
                    <p class="text-sm text-gray-500">
                      Your payment has been successfully submitted. We’ve sent you
                      an email with all of the details of your order.
                    </p>
                  </div>

                  <div class="mt-4">
                    <button
                        type="button"
                        class="inline-flex justify-center rounded-md border border-transparent bg-blue-100 px-4 py-2 text-sm font-medium text-blue-900 hover:bg-blue-200 focus:outline-none focus-visible:ring-2 focus-visible:ring-blue-500 focus-visible:ring-offset-2"
                        @click="closeModal"
                    >
                      Got it, thanks!
                    </button>
                  </div>
                </DialogPanel>
              </TransitionChild>
            </div>
          </div>
        </Dialog>
      </TransitionRoot>

    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import {
  TransitionRoot,
  TransitionChild,
  Dialog,
  DialogPanel,
  DialogTitle,
} from '@headlessui/vue'

import {XCircleIcon} from '@heroicons/vue/24/outline'

const isOpen = ref(false)

function closeModal() {
  isOpen.value = false
}
function openModal() {
  isOpen.value = true
}
</script>

<style scoped>

</style>
