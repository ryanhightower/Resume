<template>
	<section v-if="data" id="languages">
		<h2>Languages</h2>
		<div v-for="l in data" class="item">
			<div v-if="l.language" class="language">
				{{l.language}}
			</div>
			<div v-if="l.fluency" class="fluency">
				<em>{{l.fluency}}</em>
			</div>
		</div>
	</section>
</template>

<script>
export default {
  props: ['data'],
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
h1 {
  color: #42b983;
}
</style>
