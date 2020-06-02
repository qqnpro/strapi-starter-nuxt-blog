<template>
  <div>

    <div class="uk-section">
      <div class="uk-container uk-container-large">
        <img src="https://www.directech.ca/img/DIRECTECH_logo.png">
        <h2>Helping small businesses and solopreneurs get the best of IT...  <br />One blog article at a time.</h2>

        <Articles :articles="articles"></Articles>

      </div>
    </div>

  </div>
</template>

<script>
import articlesQuery from '~/apollo/queries/article/articles'
import Articles from '~/components/Articles'

export default {
  data() {
    return {
      title: 'Directech - Your Safety Net Against Malicious Web Content',
      articles: [],
    }
  },
  head () {
    return {
      title: this.title,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        { hid: 'description', name: 'description', content: 'My custom description' }
      ]
    }
  },
  components: {
    Articles
  },
  apollo: {
    articles: {
      prefetch: true,
      query: articlesQuery,
      variables () {
        return { id: parseInt(this.$route.params.id) }
      }
    }
  }
}
</script>
