<template>
  <div>
    <b-embed type="iframe"
      aspect="16by9"
      :src="`https://api.bbbbbb.me/jx/?url=${vidoUrl}`"
      allowfullscreen
    ></b-embed>
  </div>
</template>

<script>
export default {
  name: 'Embeds',
  props: {
    vidoUrl: {
      type: String,
      default: ''
    }
  },
  methods: {
    analysis (link) {
      this.vidoUrl = link
    }
  }
}
</script>
