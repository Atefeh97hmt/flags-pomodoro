<template>
<div class="bg-gray-100">
<div>
    <div class="container grid grid-cols-4 gap-5 mx-auto bg-white px-5 py-3 rounded-2xl mb-4">
        <div class="relative">
          <svg class="absolute border-r-2 pr-1 left-1 top-2" width="30px" height="30px" fill="#000000" viewBox="0 -8 72 72" id="Layer_1" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"><title>world</title><path d="M59.25,12.42l-.83.27L54,13.08l-1.27,2-.91-.29L48.23,11.6l-.52-1.66L47,8.16l-2.23-2-2.63-.51-.06,1.2,2.58,2.52,1.26,1.48-1.42.75-1.15-.34-1.73-.73,0-1.39L39.42,8.2l-.75,3.29L36.38,12l.23,1.84,3,.57.52-2.93,2.46.37,1.14.67h1.84L46.8,15l3.34,3.38-.25,1.32-2.69-.34-4.64,2.34-3.34,4-.43,1.78H37.58l-2.23-1-2.17,1,.54,2.29.94-1.09,1.67,0-.12,2,1.38.4L39,32.67,41.2,32l2.57.4,3,.8,1.48.18,2.52,2.86,4.87,2.86-3.15,6-3.32,1.54-1.26,3.44-4.81,3.21-.51,1.85A28,28,0,0,0,59.25,12.42Z"></path><path d="M39.22,42.63l-2-3.78L39.05,35l-1.87-.56-2.1-2.11-4.66-1L28.88,28v1.92H28.2l-4-5.44V20l-2.94-4.78-4.67.83H13.43l-1.59-1,2-1.6-2,.46A28,28,0,0,0,36,56a29,29,0,0,0,3.51-.25l-.29-3.39s1.29-5,1.29-5.2S39.22,42.63,39.22,42.63Z"></path><path d="M18.41,9l5-.7,2.29-1.25,2.58.74,4.12-.23,1.42-2.22,2.05.34,5-.47,1.38-1.52,2-1.29,2.74.41,1-.15a27.91,27.91,0,0,0-33.51,7.49h0ZM37.18,2.78,40,1.21l1.84,1.06-2.66,2-2.54.26-1.14-.74ZM28.71,3,30,3.54,31.63,3l.9,1.56-3.82,1L26.88,4.5S28.67,3.35,28.71,3Z"></path></g></svg>
<select id="countries" class="input-search">
  <option v-for="continent in continents"
              :key="continent.id"
              :value="continent.value"  value=""> {{ continent.label }} </option>
</select>
<p class="w-full">
       Every Countery in {{ selectedCountinent  }} 
</p>

          </div>
        <div class="relative">
          <svg class="absolute border-r-2 pr-1 left-1 top-2" width="30px" height="30px" viewBox="0 -0.5 25 25" fill="none" xmlns="http://www.w3.org/2000/svg"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <path fill-rule="evenodd" clip-rule="evenodd" d="M5.5 10.7655C5.50003 8.01511 7.44296 5.64777 10.1405 5.1113C12.8381 4.57483 15.539 6.01866 16.5913 8.55977C17.6437 11.1009 16.7544 14.0315 14.4674 15.5593C12.1804 17.0871 9.13257 16.7866 7.188 14.8415C6.10716 13.7604 5.49998 12.2942 5.5 10.7655Z" stroke="#000000" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"></path> <path d="M17.029 16.5295L19.5 19.0005" stroke="#000000" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"></path> </g></svg>
            <!-- <input type="text" class="input-search" placeholder="Name" required> -->
           <aput class="input-search" v-model="countryName" name="first_name" id="fname" label="First Name"/> 
          </div>
</div>
</div>

  <div class="container grid grid-cols-4 gap-5 mx-auto bg-white p-5 rounded-2xl">
    <div class="w-full rounded h-full" v-for="country in countries"
        :key="country.cca3">
        <NuxtLink
          :to="{
            name: 'singlecountry',
            params: {
              singlecountry: country.name.common,
            //   singlecountryImage: country.flags.png,
            },
          }"
        >
        <div class="w-full rounded-2xl h-40 relative">
          <img
            class="absolute w-full h-full left-0 right-0 bottom-0 top-0 object-cover rounded-r-xl border-l-8 shadow"
            :src="country.flags.png"
            :alt="country.flags.alt"
            :title="country.name.common"
          />
        </div>
<div class="flex justify-start items-center pt-3">
<p class="font-semibold text-sm">{{ country.name.common }}</p>
<p class="text-sm text-gray-300 ps-3">{{ country.name.common }}</p>
</div>
</NuxtLink>
</div>    
</div>
</div>
</template>
<script setup>
import _ from 'lodash';
import { ref } from "vue";
const countries = ref([]);

const countryName = ref('default')
const updateCountyName = (v) => {
  countryName.value = v
}


const getCountries = async (query) => {
  const url = query
    ? `https://restcountries.com/v3.1/name/${query}`
    : "https://restcountries.com/v3.1/all";
  const response = await fetch(url);
  countries.value = await response.json();
};

getCountries();



const continents = [
  {
    id: 1,
    label: 'All',
    value: ''
  },
  {
    id: 2,
    label: 'Asia',
    value: 'asia'
  },
  {
    id: 3,
    label: 'America',
    value: 'americas'
  },
  {
    id: 4,
    label: 'Africa',
    value: 'africa'
  },
  {
    id: 5,
    label: 'Europe',
    value: 'europe'
  },
  {
    id: 6,
    label: 'Oceania',
    value: 'oceania'
  }
]


var selectedCountinent = _.map(continents.label, function(o) {
    if (o.continents.label == "Asia") return o;
});

// Remove undefines from the array
selectedCountinent = _.without(selectedCountinent.label, undefined) 
</script>

<style>
.input-search{
  @apply bg-gray-100 border-2 border border-gray-100 text-gray-900 text-sm rounded-lg hover:border-black block w-full p-2.5 ps-10

}

</style>