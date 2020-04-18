<template>
  <div class="container">
    <h2 class="mb-0">
      Sri Lanka COVID-19 Stat Tracker
    </h2>
    <p class="font-italic mt-0">
      Last Updated:
      <span class="font-weight-bold">
        {{ formatDate() }}
      </span>
    </p>
    <StatTiles :stats="data" />

    <h3>Hospital Data</h3>
    <div class="lang_switch">
      <button :class="['lang_switch__lang', { active : active_lang == 'name_en' }]" name="name_en" @click.prevent="getCurrentLang">English</button>
      <button :class="['lang_switch__lang', { active : active_lang == 'name_si' }]" name="name_si" @click.prevent="getCurrentLang">සිංහල</button>
      <button :class="['lang_switch__lang', { active : active_lang == 'name_ta' }]" name="name_ta" @click.prevent="getCurrentLang">தமிழ்</button>
    </div>
    <Hospital v-for="item in data.hospital_data" :key="item.hospital_id" :hospital="item" :language="currentLang" />
  </div>
</template>

<script>
import axios from 'axios'
import Hospital from '~/components/Hospital.vue'
import StatTiles from '~/components/StatTiles.vue'

export default {
  name: 'App',
  components: {
    Hospital,
    StatTiles
  },
  data() {
    return {
      currentLang: 'name',
      active_lang: 'name_en',
      data: []
    }
  },
  mounted () {
    axios
      .get('https://hpb.health.gov.lk/api/get-current-statistical')
      .then((response) => {
        if (response.status === 200 && response.data.success === true) {
          this.data = response.data.data
        }
      })
      .catch(function (error) {
        alert(error)
      })
  },
  methods: {
    formatDate() {
      if (this.data.update_date_time) {
        return new Date(this.data.update_date_time).toDateString() + ', ' + new Date(this.data.update_date_time).toLocaleTimeString()
      }
    },
    getCurrentLang(e) {
      this.currentLang = e.target.name
      this.toggleLangActive(e.target.name)
    },
    toggleLangActive(el) {
      this.active_lang = el
    }
  }
}
</script>
