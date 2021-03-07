<template>
  <v-main>
    <article>
      <div class="midashi">
        <h1>{{ page.title }}</h1>
        <p class="text--secondary">{{$dateFns.format(page.created_at,'yyyy-MM-dd')}}</p>
      </div>
      <nuxt-content :document="page" />
    </article>
    <v-container class="mt-15">
      <v-col align="center" col=4>
        <a class="text--primary underline" href="/">記事一覧</a>
      </v-col>
    </v-container>
  </v-main>
</template>

<script>
export default {
  async asyncData ({ $content, params }) {
    const slug = params.slug
    const page = await $content('articles/'+ slug).fetch()

    return {
      page
    }
  }
}
</script>

<style lang="scss">
article{
  .midashi{
    margin: 2.8rem 0 1.6rem;
  }
h2{
    position: relative;
    margin: 2.8rem 0 1.6rem;
    font-size: 1.2rem;
    font-weight: 400;
    line-height: 2rem;
    letter-spacing: .05rem;
}
h2:after{
  content: "";
    width: 100%;
    height: 1px;
    position: absolute;
    bottom: 0;
    left: 0;
    background-color: var(--v-accent-base);
    opacity: .4;
}
h3{
  position: relative;
  margin: 2.8rem 0 1.6rem;
  font-size: 1.0rem;
  font-weight: 400;
  line-height: 2rem;
  letter-spacing: .05rem;
}
h3:after{
  content: "";
    width: 100%;
    height: 1px;
    position: absolute;
    bottom: 0;
    left: 0;
    background-color: var(--v-accent-lighten2);
    opacity: .4;
}
}
.underline{
  text-decoration: dashed underline;
}

blockquote{
  border-left-width: 4px;
    border-left-style: solid;
    border-color: #ddd;
    font-size: 1.125rem;
    font-style: italic;
    margin: 0 0 1em;
    padding: 0% 3%;
}
</style>
