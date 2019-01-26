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
      <Embeds :vidoUrl='updateUrl'/>
      <hr class="my-4">
      <!-- Using components -->
      <b-input-group prepend="Link">
        <b-form-input v-model="link" placeholder="Please enter a video play address"></b-form-input>
        <b-input-group-append>
          <b-btn variant="success" @click="submit">Analysis</b-btn>
        </b-input-group-append>
      </b-input-group>
    </b-jumbotron>
  </div>
</template>

<script>
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
