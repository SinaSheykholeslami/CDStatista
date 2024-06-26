<template>
  <div>
    <div class="container mx-auto p-2 md:p-4">
      <div v-if="isFetching" class="pending">
        <p class="my-5">Loading Data...</p>
      </div>
      <HealthCareList v-else :list="list" />
    </div>
  </div>
</template>

<script setup>
const { isFetching, data: list } = useFetch(
  'https://r.statista.com/wp-content/themes/statista-theme/addons/services/rankinglist.php?ranking_id=P-173224&topic_hub=healthcare', {
  lazy: false,
  transform: (list) => {
    return list.rankingList.map((hospital) => {
      return {
        id: hospital.id,
        rank: hospital.rank,
        name: hospital.hospital.name,
        country: hospital.hospital.country,
        city: hospital.hospital.city,
      }
    })
  }
})

useHead({
  title: 'Statista | Healthcare',
  meta:[{
    name: 'description',
    content: 'Statista | Healthcare'
  }]
})
</script>

<style scoped>
  .pending {
    margin-top: 20px;
    margin-bottom: 20px;
  }
</style>
