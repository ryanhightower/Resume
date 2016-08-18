<template>
  	<section v-if="data" id="volunteer">
  		<h2>Volunteer</h2>
  		<div v-for="volunteer in data" class="item">
  			<h3 class="company">
  				{{volunteer.organization}}
  			</h3>
  			<div class="date">
  				<span v-if="volunteer.startDate" class="startDate">
  					{{volunteer.startDate | date '%b, %Y'}}
  				</span>
  				<span v-if="volunteer.endDate && volunteer.endDate!='present'" class="endDate">
  					- {{volunteer.endDate | date '%b, %Y'}}
  				</span>
  				<span v-else class="endDate">
  					- Present
  				</span>
  			</div>
  			<div v-if="volunteer.position" class="position">
  				{{volunteer.position}}
  			</div>
  			<div v-if="volunteer.website" class="website">
  				<a href="{{volunteer.website}}">{{volunteer.website}}</a>
  			</div>
  			<div v-if="volunteer.summary" class="summary">
  				<p>{{volunteer.summary}}</p>
  			</div>
  			<ul v-if="volunteer.highlights" class="highlights">
  				<li v-for="h in volunteer.highlights">{{h}}</li>
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
