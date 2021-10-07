<script>
import { useRoute } from 'vue-router';
import { reactive, toRefs } from 'vue';
export default {
  setup() {
    const route = useRoute();
    const state = reactive({
      pokemon: null
    });

    fetch(`https://pokeapi.co/api/v2/pokemon/${route.params.slug}/`)
      .then(res => res.json())
      .then(data => {
        console.log(data);
        state.pokemon = data;
      })

    return {
      ...toRefs(state)
    }
  }
}

</script>

<template>
  <div class="about">
    <div v-if="pokemon" class="w-3/12 p-4 mt-8 m-auto bg-purple-100 rounded-md shadow-2xl flex justify-center flex-col items-center">
      <h3 class="text-2xl text-green-900 uppercase">{{ pokemon.name }}</h3>
      <div class="flex justify-center">
        <img class="w-48" :src="pokemon.sprites.front_shiny" alt="pokemon front">
        <img class="w-48" :src="pokemon.sprites.back_shiny" alt="pokemon back">
      </div>
      <h5 class="mt-2">
        <span
          v-for="(type, idx) in pokemon.types" :key="idx"
          class="text-blur-900 inline-block"
        >
          {{ `${type.type.name}${idx === pokemon.types.length - 1 ? '' : ' /&nbsp;'}` }}
        </span>
      </h5>
    </div>
  </div>
</template>
