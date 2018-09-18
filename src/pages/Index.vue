<template>
<q-layout>
  <q-layout-header>
    <q-toolbar color="white">
      <q-toolbar-title class="absolute-center">
        <p class="text-red-10 q-display-1">Dlike</p>
      </q-toolbar-title>
    </q-toolbar>
  </q-layout-header>
  <q-page-container>
    <q-page class="absolute-center" style="padding-top: 25px;">
      <q-card inline class="q-ma-sm" style="width:250px;">
        <q-card-media>
          <img src="https://opensource.google.com/assets/static/images/home/blog/blog_image_1.jpg">
        </q-card-media>
        <q-card-actions align="around">
          <q-btn flat round color="red" icon="favorite" />
          <q-btn flat round color="faded" icon="bookmark" />
          <q-btn flat round color="primary" icon="share" />
        </q-card-actions>
      </q-card>
    </q-page>
  </q-page-container>
</q-layout>
</template>

<style>
</style>

<script>
export default {
  name: 'Index',
  data () {
    return {
      props: {
        maximum_block_size: this.main()
      }
    }
  },
  methods: {
    main: async function () {
      await this.$steemClient.database.getChainProperties().then((props) => {
        console.log(`Maximum blocksize consensus: ${props.maximum_block_size} bytes`)
        this.props = props
      })
      return this.props.maximum_block_size
    }
  },
  mounted () {
    // just so you can do it this way too
    // this.main().catch(console.error)
  }
}
</script>
