<template>
  <div v-if="data" class="work">
	<section id="work">
		<h2>Work</h2>
		<div v-for="work in data" class="item">
			<h3 v-if="work.company" class="name">
				{{work.company}}
			</h3>
			<div class="date">
				<span v-if="work.startDate" class="startDate">
					{{work.startDate | date '%b, %Y'}}
				</span>
				<span v-if="work.endDate && work.endDate != 'present'" class="endDate">
					- {{work.endDate | date '%b, %Y'}}
				</span>
				<span v-else class="endDate">
					- Present
				</span>
			</div>
			<div v-if="work.position" class="position">
				{{work.position}}
			</div>
			<div v-if="work.website" class="website">
				<a href="{{work.website}}">{{work.website}}</a>
			</div>
			<div v-if="work.summary" class="summary">
				<p>{{work.summary}}</p>
			</div>
			<ul v-if="work.highlights" class="highlights">
				<li v-for="highlight in work.highlights">{{highlight}}</li>
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
