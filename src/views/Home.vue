<template>
  <main v-if="!loading">
    <DateTitle :text="title" :dataDate="dataDate" />
    <DataBoxes :stats="stats" />

    <CountrySelect @get-Country="getCountryData"  :countries="countries" />
    <button 
      @click="clearCountryData"
      v-if="stats.Country"
      class="bg-green-700 text-white rounded p-3 mt-10 focus:outline-none hover:bg-green-600">
      Clear Country
    </button>

      <Footer />
  </main>

  <main class="flex flex-col aling-center justify-center text-center" v-else>
    <div class="text-gray-500 text-3xl mt-10 mb-6">
      fetching data
    </div>
    <img :src="loadingImg" class="w-24 m-auto" >
      <Footer />
  </main>


</template>

<script>

  import DateTitle from '../components/DataTitle.vue';
  import DataBoxes from '../components/DataBoxes.vue';
  import CountrySelect from '../components/CountrySelect.vue';
  import Footer from '../components/Footer.vue';

export default {
  name: 'Home',
  data(){
    return {
      loading : true,
      title : 'Global',
      dataDate : '',
      stats : {},
      countries : [],
      loadingImg : require('../assets/hourglass.gif')
    }
  },
  components: {
    DateTitle,
    DataBoxes,
    CountrySelect,
    Footer,
  },
  methods:{
    async fetchCovidData(){
      const res = await fetch(`https://api.covid19api.com/summary`);
      const data = await res.json();
      return data;
    },
    getCountryData(country){
      this.stats = country;
      this.title = country.Country;
    },
    async clearCountryData(){
      this.loading = true;
      const data = await this.fetchCovidData();
      this.title="Global";
      this.stats = data.Global;
      this.loading = false;
    }
  },
  async created(){
    const data = await this.fetchCovidData();
    this.dataDate = data.Date;
    this.stats = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  }
}
</script>
