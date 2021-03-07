<template>
 <v-main>
   <v-container>
     <a :href="about.slug">
       About Me
     </a>
     <ul class="list-style">
       
       <li v-for="page in pages" :key="page.title" class="py-5">
         <v-hover v-slot="{ hover }">
          <a v-bind:href="'articles/'+ page.slug">
          <v-card outlined :elevation="hover ? 12 : 2"
              :class="{ 'on-hover': hover }">
            <v-card-title>{{ page.title }}</v-card-title>
            <v-card-text>{{ page.description }}</v-card-text>
            <v-card-text>{{ $dateFns.format(page.created_at ,'yyyy-MM-dd') }}</v-card-text>
          </v-card>
          </a>
          </v-hover>
        </li>
        
     </ul>
     
      
   </v-container>
 </v-main>
</template>

<script>
export default {
  async asyncData ({ $content }) {
    const pages = await $content('articles').sortBy('created_at','desc').fetch()
    const about = await $content('about').fetch()
    return {
      pages,
      about
    }
  }
}
</script>

<style lang="scss">
  .list-style{
    list-style-type: none;
  }
  
  ul{
    padding-left: 0 !important;
  }
</style>