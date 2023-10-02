<template>

  <main v-if="!loading">

    <DataTitle :text= "title" :dataDate= "dataDate" />

  </main>

  <main v-else class="flex-col align-center justify-center text-center">
    
    <div class="text-dark text-4xl mt-10 mb-6">
      Fetching Data
    </div>

    <img :src="loadingImage" alt="">

  </main>  

</template>

<script>

  import DataTitle from '@/components/DataTitle.vue'

  export default {

    name: 'HomeView',

    components: { 

      DataTitle
      
    },

    data () {

      return {

        loading: true,
        title: 'Global',
        dataDate: '',
        stats: {},
        countries: [],
        loadingImage: require('../assets/giphy.gif'),
        text: ''
      
      }

    },

    methods: {

      async fetchCovidData() {

        const res = await fetch ( 'https://rapidapi.com/api-sports/api/covid-193' )
    
        const data = await res.json()

        return data

      },

    },

    async created() {
      
      const data = await this.fetchCovidData()

      console.log(data)

      this.dataDate = data.Cases

      this.stats = data.Global

      this.countries = data.countries

      this.loading = false


    },

  }
</script>

<style>

  img {
    width: 200px;
    height: 200px;
    position: absolute;
    left: 137.7rem;
    top: 22rem;
  }

</style>