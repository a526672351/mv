<template>
  <div id="app">
    <b-jumbotron>
      <template slot="header">
        Video Analysis
      </template>
      <template slot="lead">
        Designed to provide users with free vip video online resolution service, so that you can watch the paid video of major video sites without spending money. Currently supports Tencent vip video, iQiyi vip video, Mango TV member, Sohu VIP video, pptv member analysis, etc.
      </template>
      <hr class="my-4">
      <Embeds :vidoUrl='vidoUrl'/>
      <hr class="my-4">
      <!-- Using components -->
      <b-input-group prepend="Link">
        <b-form-input v-model="link" placeholder="Please enter a video play address"></b-form-input>
        <b-input-group-append>
          <b-btn variant="secondary" :data-clipboard-text="copyLink" id="tooltipButton-1" class="share">Share</b-btn>
          <b-tooltip target="tooltipButton-1" placement="top">
            Copy Video Address
          </b-tooltip>
          <b-btn variant="success" @click="submit">Analysis</b-btn>
        </b-input-group-append>
      </b-input-group>
    </b-jumbotron>
  </div>
</template>

<script>
import ClipboardJS from 'clipboard'
import queryString from 'query-string'
import Embeds from './components/Embeds.vue'

export default {
  name: 'app',
  components: {
    Embeds
  },
  data () {
    return {
      link: '',
      updateUrl: ''
    }
  },
  computed: {
    copyLink() {
      return `${location.href.replace(/\?.*/, '')}?vip=${encodeURIComponent(this.link)}`
    },
    vidoUrl() {
      return encodeURIComponent(this.updateUrl)
    }
  },
  mounted () {
    const parse = queryString.parse(location.search)
    if (parse.vip) {
      this.link = decodeURIComponent(parse.vip)
      this.submit()
    }
    new ClipboardJS('.share')
  },
  methods: {
    submit () {
      this.updateUrl = this.link
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.jumbotron {
  background: url(./assets/video.jpg);
  background-repeat: no-repeat;
  background-size: cover;
  width: 100%;
  margin-bottom: 0rem;
  color: #ffffff;
}
</style>
