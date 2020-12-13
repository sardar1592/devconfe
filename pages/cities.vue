<template>
    <div>
<Menu/> 
        <section class="text-gray-700 body-font">
  <div class="container px-5 py-24 mx-auto">
    <div class="flex flex-wrap w-full mb-20">
      <div class="w-full mb-6 lg:w-1/2 lg:mb-0">
        <h1 class="mb-2 text-2xl font-medium text-gray-900 sm:text-3xl title-font">List of Cities</h1>
        <div class="w-20 h-1 bg-indigo-500 rounded"></div>
      </div>
      <p class="w-full text-base leading-relaxed lg:w-1/2">Whatever cardigan tote bag tumblr hexagon brooklyn asymmetrical gentrify, subway tile poke farm-to-table. Franzen you probably haven't heard of them man bun deep jianbing selfies heirloom prism food truck ugh squid celiac humblebrag.</p>
    </div>
    <div class="flex flex-wrap -m-4">
      <div class="p-4 xl:w-1/4 md:w-1/2" v-for="city in cities" :key="city.id">
        <div class="p-6 bg-gray-100 rounded-lg">
          <img class="object-cover object-center w-full h-40 mb-6 rounded" :src="city.pic" :alt="city.name">
          <h3 class="text-xs font-medium tracking-widest text-indigo-500 title-font">{{city.state}}</h3>
          <h2 class="mb-4 text-lg font-medium text-gray-900 title-font">{{city.name}}</h2>
          <p class="text-base leading-relaxed">{{city.history}}</p>
        </div>
      </div>
    </div>
  </div>
</section>
    </div>
</template>

<script>
export default {
    
    async asyncData({$axios, error}){

        try {

           const {data} =  await $axios.get('http://127.0.0.1:8000/api/cities')

           return {

               cities:data.data
           }
            
        } catch (e) {
            
            error({

                statusCode:503,
                message:'Unable to fetch Cities'

            });
        }


    }
}
</script>