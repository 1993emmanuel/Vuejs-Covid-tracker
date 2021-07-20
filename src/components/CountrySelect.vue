<template>
  <select @change="onChange" v-model="selected" class="form-select mt-10 block w-full border p-3 rounded mt-10">
      <option value="0">Select Country</option>
      <option :value="country.ID" v-for="country in countries" :key="country.id">
          {{country.Country}}
      </option>
  </select>
</template>

<script>
export default {
    name : 'CountrySelect',
    props : {
        countries : Array,
    },
    data(){
        return{
            selected : 0
        }
    },
    methods:{
        onChange(){
            const country = this.countries.find( (item) => item.ID === this.selected )
            this.$emit('get-Country',country)
        }
    }
}
</script>