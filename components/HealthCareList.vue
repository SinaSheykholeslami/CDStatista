<template>
  <div v-if="paginatedList.length > 0" class="overflow-x-auto rounded-lg">
    <table class="min-w-full bg-white border border-gray-200">
      <thead>
        <tr class="bg-gray-100 border-b-2 border-r-2">
          <th class="py-1 md:py-2 px-2 md:px-4 text-left">Rank</th>
          <th class="py-1 md:py-2 px-2 md:px-4 text-left">Name</th>
          <th class="py-1 md:py-2 px-2 md:px-4 text-left">Country</th>
          <th class="py-1 md:py-2 px-2 md:px-4 text-left">City</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="hospital in paginatedList" :key="hospital.id" class="border-b border-r hover:bg-gray-50">
          <th class="py-1 md:py-2 px-2 md:px-4 text-left border-r-2 border-gray-200">{{ hospital.rank }}</th>
          <th class="py-1 md:py-2 px-2 md:px-4 text-left border-r-2 border-gray-200">{{ hospital.name }}</th>
          <th class="py-1 md:py-2 px-2 md:px-4 text-left border-r-2 border-gray-200">{{ hospital.country }}</th>
          <th class="py-1 md:py-2 px-2 md:px-4 text-left border-gray-200">{{ hospital.city }}</th>
        </tr>
      </tbody>
    </table>
    <div class="flex justify-between mt-4">
      <button @click="prevPage" :disabled="currentPage === 1" class="px-4 py-2 bg-gray-200 rounded">Previous</button>
      <span>Page {{ currentPage }} of {{ totalPages }}</span>
      <button @click="nextPage" :disabled="currentPage === totalPages" class="px-4 py-2 bg-gray-200 rounded">Next</button>
    </div>
  </div>
  <div v-else>
    <p>No data available.</p>
  </div>
</template>

<script setup>
const props = defineProps({
  list: {
    type: Array,
    required: true,
    default: () => []
  }
});

const currentPage = ref(1);
const itemsPerPage = 10;

const totalPages = computed(() => {
  return Math.ceil(props.list.length / itemsPerPage);
});

const paginatedList = computed(() => {
  const start = (currentPage.value - 1) * itemsPerPage;
  const end = start + itemsPerPage;
  return props.list.slice(start, end);
});

const nextPage = () => {
  if (currentPage.value < totalPages.value) {
    currentPage.value++;
  }
};

const prevPage = () => {
  if (currentPage.value > 1) {
    currentPage.value--;
  }
};
</script>

<style scoped>

</style>