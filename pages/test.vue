<template>
  <main class="relative flex bg-slate-100">
    <aside
      class="sticky top-0 flex flex-col items-center justify-between flex-shrink-0 w-20 h-screen py-8 border-r bg-slate-100"
    >
      <!-- Sample Logo  -->
      <svg
        class="w-auto h-8"
        viewBox="0 0 50 39"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M16.4992 2H37.5808L22.0816 24.9729H1L16.4992 2Z"
          class="ccompli1"
          fill="#007AFF"
        ></path>
        <path
          d="M17.4224 27.102L11.4192 36H33.5008L49 13.0271H32.7024L23.2064 27.102H17.4224Z"
          class="ccustom"
          fill="#312ECB"
        ></path>
      </svg>
      <!-- Sample Logo  -->
      <div class="space-y-8">
        <icon name="fluent:channel-24-regular" class="w-6 h-6 text-sky-600" />
        <icon
          name="fluent:data-pie-24-regular"
          class="w-6 h-6 text-slate-400"
        />
        <icon
          name="fluent:mail-inbox-24-regular"
          class="w-6 h-6 text-slate-400"
        />
        <icon
          name="fluent:wallet-credit-card-24-regular"
          class="w-6 h-6 text-slate-400"
        />
      </div>
      <div class="space-y-8">
        <button @click="sidebar = true" class="relative">
          <icon
            name="fluent:panel-right-28-filled"
            class="w-6 h-6 text-slate-400"
          />
        </button>
        <div class="relative" ref="floatingWidget">
          <button @click="showChangelog = !showChangelog">
            <icon
              name="fluent:alert-badge-24-filled"
              class="w-6 h-6 text-slate-400"
            />
          </button>
          <transition
            enter-active-class="transition duration-100 ease-out"
            enter-from-class="transform scale-95 opacity-0"
            enter-to-class="transform scale-100 opacity-100"
            leave-active-class="transition duration-75 ease-in"
            leave-from-class="transform scale-100 opacity-100"
            leave-to-class="transform scale-95 opacity-0"
          >
            <div
              v-if="showChangelog"
              class="h-[450px] w-80 z-20 bg-white rounded-lg shadow-2xl absolute left-[calc(50%+14px)] bottom-[calc(50%+14px)] origin-bottom-left overflow-hidden border border-gray-100"
            >
              <div
                v-if="!iframeLoaded"
                class="flex flex-col items-center justify-center w-full h-full space-y-2 text-slate-700"
              >
                <base-spinner class="w-5 h-5" />
                <p>Loading Feed</p>
              </div>
              <iframe
                src="/widget"
                class="w-full h-full"
                :class="iframeLoaded ? 'opacity-100' : 'opacity-0'"
                frameborder="0"
                @load="iframeLoaded = true"
              ></iframe>
            </div>
          </transition>
        </div>
      </div>
    </aside>
    <section class="flex-grow">
      <header
        class="sticky top-0 flex items-center justify-between p-4 bg-white border-b"
      >
        <div
          class="flex items-center w-full p-3 rounded-full sm:w-1/2 bg-slate-200"
        >
          <icon name="fluent:search-24-filled" class="w-4 h-4 text-slate-400" />
          <p class="ml-4 text-sm truncate text-slate-400">
            Search your transactions, accounts, cards etc...
          </p>
        </div>
        <div class="items-center hidden space-x-2 sm:flex">
          <div
            class="flex items-center justify-center flex-shrink-0 w-12 h-12 p-3 rounded-full bg-slate-200"
          >
            <icon
              name="fluent:alert-badge-24-filled"
              class="w-5 h-5 text-slate-600"
            />
          </div>
          <div
            class="flex items-center justify-center flex-shrink-0 w-12 h-12 p-3 rounded-full bg-slate-200"
          >
            <icon
              name="fluent:person-24-filled"
              class="w-5 h-5 text-slate-600"
            />
          </div>
        </div>
      </header>
      <div class="p-4">
        <div class="mt-4 space-y-8">
          <div class="grid grid-cols-1 gap-6 md:grid-cols-4">
            <div
              class="h-40 bg-white border rounded-lg shadow-sm"
              v-for="n in 4"
              :key="n"
            ></div>
          </div>
          <div class="grid grid-cols-1 gap-6 lg:grid-cols-2">
            <div
              class="bg-white border rounded-lg shadow-sm h-96"
              v-for="n in 4"
              :key="n"
            ></div>
          </div>
        </div>
      </div>
    </section>
    <test-sidebar v-if="sidebar" @close="sidebar = false" ref="overlayWidget" />
    <test-arrow v-if="!showChangelog" class="fixed z-0 bottom-24 left-32" />
  </main>
</template>

<script setup>
import { ref } from "vue";
const showChangelog = ref(false);
const iframeLoaded = ref(false);
const sidebar = ref(false);
const floatingWidget = ref(null);
useClickOutside(floatingWidget, () => (showChangelog.value = false));
</script>

<style scoped>
.icon {
  display: block !important;
}
</style>
