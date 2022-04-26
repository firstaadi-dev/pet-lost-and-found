<script setup>
const { pending, data: pets } = useLazyFetch("/api/pet_lists");
</script>
<template>
  <div v-if="pending">
    Loading ...
  </div>
  <div
    v-else
    class="p-10 grid grid-cols-1 sm:grid-cols-1 md:grid-cols-3 lg:grid-cols-3 xl:grid-cols-3 gap-5"
  >
    <div
      v-for="pet in pets"
      :key="pet"
    >
      <div class="max-w-sm rounded overflow-hidden shadow-lg">
        <div class="px-6 py-4">
          <img src="http://placekitten.com/400/300" />
          <div class="font-bold text-xl mb-2">{{pet.name}}</div>
          <p class="text-gray-700 text-base">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque placerat mi sit amet nisi vestibulum, nec eleifend eros efficitur. Nulla elit nisl, vehicula a quam ac, molestie ornare felis. Mauris semper bibendum ullamcorper.
          </p>
          <ul>
            <li>Jenis: {{pet.type}}</li>
            <li>Daerah: {{pet.daerah}}</li>
            <li>Kontak: {{pet.kontak}}</li>
          </ul>
        </div>
        <div class="px-6 pt-4 pb-2">
          <a
            v-bind:href="'https://wa.me/' + pet.kontak"
            target="_blank"
          >
            <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-full">
              Contact Owner
            </button>
          </a>

        </div>
      </div>
    </div>
  </div>

</template>