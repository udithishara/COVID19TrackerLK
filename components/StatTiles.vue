<template>
  <div class="stat_tiles">
    <div>
      <p class="stat__number stat--new">{{ stats.local_new_cases }}</p>
      <p class="stat__type">New Cases</p>
    </div>
    <div>
      <p class="stat__number">{{ stats.local_deaths }}</p>
      <p class="stat__type">Deaths</p>
    </div>
    <div>
      <p class="stat__number stat--admitted">{{ stats.local_total_number_of_individuals_in_hospitals }}</p>
      <p class="stat__type">Admitted</p>
    </div>
    <div>
      <p class="stat__number stats--recovered">{{ stats.local_recovered }}</p>
      <p class="stat__type">Recovered</p>
    </div>
    <div>
      <p class="stat__number stat--active">{{ stats.local_active_cases }}</p>
      <p class="stat__type">Active</p>
    </div>
    <div>
      <p class="stat__number stat--total">{{ stats.local_total_cases }}</p>
      <p class="stat__type">Total Cases</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'StatTiles',
  props: {
    stats: {
      type: [Object, Array],
      default: () => {
        return null
      }
    }
  }
}
</script>
