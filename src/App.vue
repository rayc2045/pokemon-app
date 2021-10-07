<template>
  <div
    class="w-screen h-screen"
    @dragstart.prevent @selectstart.prevent @contextmenu.prevent
  >
    <div class="mt-10 flex justify-center ">
      <router-link class="py-4 text-4xl text-yellow-700" to="/"
        >
        Pokemon Picker
      </router-link>
    </div>
    <router-view />
  </div>
</template>
