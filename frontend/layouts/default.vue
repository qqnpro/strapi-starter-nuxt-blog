<template>
  <div>

    <nav class="uk-navbar-container" uk-navbar>
        <div class="uk-navbar-left">

          <ul class="uk-navbar-nav">
              <li><a href="#modal-full" uk-toggle><span uk-icon="icon: table"></span></a></li>
              <li>
                <a href="/">Directech Blog
                </a>
              </li>
          </ul>

        </div>

        <div class="uk-navbar-right">
          <ul class="uk-navbar-nav">
              <li v-for="category in categories">
                <router-link :to="{ name: 'categories-id', params: { id: category.id }}" tag="a">{{ category.name }}
                </router-link>
              </li>
          </ul>
        </div>
    </nav>

    <div id="modal-full" class="uk-modal-full" uk-modal>
        <div class="uk-modal-dialog">
            <button class="uk-modal-close-full uk-close-large" type="button" uk-close></button>
            <div class="uk-grid-collapse uk-child-width-1-2@s uk-flex-middle" uk-grid>
                <div class="uk-background-cover" style="background-image: url('https://www.directech.ca/img/mac_it_sec.jpg');" uk-height-viewport></div>
                <div class="uk-padding-large">
                    <img src="https://www.directech.ca/img/logo-dt.png">
                    <h2>Helping small businesses and solopreneurs get the best of IT...  One blog article at a time.</h2>                    
                    <div class="uk-width-1-2@s">
                        <ul class="uk-nav-primary uk-nav-parent-icon" uk-nav>
                          <li v-for="category in categories">
                            <router-link class="uk-modal-close" :to="{ name: 'categories-id', params: { id: category.id }}" tag="a">{{ category.name }}
                            </router-link>
                          </li>
                        </ul>
                    </div>
                    <p class="uk-text-light">Pssst! If you LOVE coffee as much as we do...  <br />Donate to our <a href=""><b>Half & Half</b></a> initiative.</p>
                </div>
            </div>
        </div>
    </div>

    <nuxt />
  </div>
</template>

<script>
import categoriesQuery from '~/apollo/queries/category/categories'

export default {
  data() {
    return {
      categories: [],
    }
  },
  apollo: {
    categories: {
      prefetch: true,
      query: categoriesQuery
    }
  }
}

</script>  
