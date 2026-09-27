<script setup>
import { ref } from "vue";
import { StarIcon } from "@heroicons/vue/24/solid";
import { items } from "./movies.json";

const movies = ref(items);
</script>

<template>
  <div class="h-full w-full overflow-y-auto bg-gray-900 p-8 flex">
    <div
      class="m-auto grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 max-w-7xl w-full"
    >
      <div
        v-for="movie in movies"
        :key="movie.id"
        class="bg-white rounded-lg overflow-hidden shadow-lg flex flex-col"
      >
        <img
          :src="movie.image"
          :alt="movie.name"
          class="w-full h-[520px] object-cover"
        />
        <div class="p-6 flex flex-col flex-1 justify-between">
          <div>
            <h2 class="text-xl font-bold text-gray-900 mb-2">
              {{ movie.name }}
            </h2>
            <div class="flex flex-wrap gap-1 mb-4">
              <span
                v-for="genre in movie.genres"
                :key="genre"
                class="bg-indigo-500 text-white text-xs font-semibold px-2 py-0.5 rounded-full"
              >
                {{ genre }}
              </span>
            </div>
            <p class="text-gray-700 text-sm leading-relaxed mb-4">
              {{ movie.description }}
            </p>
          </div>
          <div class="flex items-center gap-2 text-sm text-gray-700">
            <span>Rating: ({{ movie.rating }}/5)</span>
            <div class="flex items-center gap-1">
              <StarIcon
                v-for="star in movie.rating"
                :key="star"
                class="w-4 h-4 text-yellow-500"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
