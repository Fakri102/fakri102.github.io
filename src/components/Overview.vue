<template>
  <div>
    <Card title="Overview">
      <p class="lead">
        Hello, I'm <strong>{{ personal.full_name }}</strong>, a Junior Web Developer
      </p>
      <p>
        I'm a junior full stack developer. Interested in web development. loves exploring new technologies in web application development.
      </p>
      <!-- <p>
        Web development frameworks that I have used are vue js and laravel
      </p> -->
      <!-- <p>
          <a href="https://bit.ly/3ipyV8p" target="_blank">My CV</a>
      </p> -->

    </Card>
  </div>
</template>
<script>
import Card from './Card.vue'

export default {
  name: "Overview",
  props: {
    'socials': {
      type: Array,
      required: true,
      default: function() {
        return []
      }
    },
    'personal': {
      type: Object,
      required: true,
      default: function() {
        return {}
      }
    },
  },
  components: {
    Card,
  },
  data: () => ({
    isPaid: false
  }),
  created() {
    if (process.isClient) {
      if (document.monetization) {
        document.monetization.addEventListener('monetizationstart', event => {
          if (document.monetization.state === 'started') {
            this.isPaid = true
          }
        });
      }
    }
  },
}
</script>
<style lang="scss" scoped>
.lead {
  color: #000;
}
</style>
