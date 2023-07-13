<template>
  <header class="px-4 py-12 sm:px-6 lg:px-8">
    <div class="flex justify-between items-center mx-auto max-w-[37.5rem] pt-20 text-center pb-20">
      <div class="flex items-center space-x-3">
        <img loading="lazy" src="/logo.png" alt="Inkly" class="w-20 h-20" />
        <h1 class="text-4xl font-extrabold tracking-tight text-slate-700 sm:text-5xl">
          Inkly
        </h1>
      </div>
      <nav class="space-x-4">
        <a href="/login" class="p-10 text-slate-900 hover:text-slate-700 ">Login</a>
        <a href="/register" class="text-slate-900 hover:text-slate-700">Register</a>
      </nav>
    </div>
    <div class="mx-auto max-w-[37.5rem]">
      <p class="mt-4 text-base leading-7 text-slate-600">
        INKLY is a technologically advanced platform that connects artists with clients, allowing artists to provide a range of services, including tattoos, paintings, graphic designs, photography, and more.
      </p>
    </div>
  </header>
</template>

<script setup></script>

<style scoped>
.form-input {
  @apply block h-10 w-full rounded-md bg-white pr-3 pl-12 text-slate-900 shadow-md shadow-black/5 ring-1 ring-slate-900/5 placeholder:text-slate-400 focus:outline-none focus:ring-2 focus:ring-primary sm:text-sm sm:leading-6;
}
.form-submit {
  @apply inline-flex justify-center rounded-lg text-sm font-semibold py-2.5 px-4 bg-slate-900 text-white hover:bg-slate-700 ml-4 flex-none;
}
</style>