<template>
	<section v-if="data" id="education">
		<h2>Education</h2>
		<div v-for="edu in data" class="item">
			<div class="date">
				<span v-if="edu.startDate" class="startDate">
					{{edu.startDate | date '%b, %Y'}}
				</span>
				<span v-if="edu.endDate && edu.endDate!='present'" class="endDate">
					- {{edu.endDate | date '%b, %Y'}}
				</span>
				<span v-else class="endDate">
					- Present
				</span>
			</div>
			<div v-if="edu.institution" class="institution">
				{{edu.institution}}
			</div>
			<div v-if="edu.area" class="area">
				{{edu.area}}
			</div>
			<div v-if="edu.studyType" class="studyType">
				{{edu.studyType}}
			</div>
			<div v-if="edu.gpa" class="gpa">
				GPA: {{edu.gpa}}
			</div>
			<ul v-if="edu.courses" class="courses">
				<li v-for="course in edu.courses">{{course}}</li>
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
