<template>
	<section v-if="data" id="skills">
		<h2>Skills</h2>
		<div v-for="skill in data" class="item">
			<div v-if="skill.name" class="name">
				{{skill.name}}
			</div>
			<div v-if="skill.level" class="level">
				<em>{{skill.level}}</em>
			</div>
			<ul v-if="skill.keywords" class="keywords">
				<li v-for="k in skill.keywords">{{k}}</li>
			</ul>
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
