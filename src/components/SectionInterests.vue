<template>
  <section v-if="data" id="interests">
    <h2>Interests</h2>
    <div v-for="interest in data" class="item">
      <div v-if="interest.name" class="name">
        {{interest.name}}
      </div>
      <ul v-if="interest.keywords" class="keywords">
        <li v-for="k in interest.keywords">{{k}}</li>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
  props: ['data', 'class'],
  data () {
    return {

      // note: changing this line won't causes changes
      // with hot-reload because the reloaded component
      // preserves its current state and we are modifying
      // its initial state.
      msg: 'Hello World!'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2, h3, h4 {
  color: #42b983;
}
</style>
