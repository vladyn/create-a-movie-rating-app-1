<script setup>
import { ref } from "vue";
import { StarIcon } from "@heroicons/vue/24/solid";
import { items } from "./movies.json";

const movies = ref(items);

function updateRating(movieOrIdOrIndex, star) {
  if (typeof movieOrIdOrIndex === "object" && movieOrIdOrIndex !== null) {
    movieOrIdOrIndex.rating = star;
  } else if (typeof movieOrIdOrIndex === "number") {
    const movie = movies.value.find((m) => m.id === movieOrIdOrIndex);
    if (movie) {
      movie.rating = star;
    } else if (movies.value[movieOrIdOrIndex]) {
      movies.value[movieOrIdOrIndex].rating = star;
    }
  }
}
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
              <button
                v-for="star in 5"
                :key="star"
                type="button"
                :disabled="movie.rating === star"
                class="cursor-pointer disabled:cursor-not-allowed"
                @click="updateRating(movie, star)"
              >
                <StarIcon
                  class="w-4 h-4"
                  :class="star <= movie.rating ? 'text-yellow-500' : 'text-gray-500'"
                />
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
