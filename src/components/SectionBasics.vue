<template>
  <div class="basics">
    <h1>{{data.name}}</h1>
    <h2>{{data.label}}</h2>
    <div id="basics">
      <section class="contact">
        <div v-if="data.website" class="website">
          <strong>Website</strong>
          <a href="{{data.website}}" target="_blank">{{data.website}}</a>
        </div>
        <div v-if="data.email" class="email">
          <strong>Email</strong>
          {{data.email}}
        </div>
        <div v-if="data.phone" class="phone">
          <strong>Phone</strong>
          {{data.phone}}
        </div>
      </section>
      <section v-if="data.summary" class="summary">
        <p>{{data.summary}}</p>
      </section>

        <section v-if="data.location" id="location">
          <h3>Location</h3>
          <div v-if="data.location.address" class="address">
            <strong>Address</strong>
            {{data.location.address}}
          </div>

          <div v-if="data.location.postalCode" class="postalCode">
            <strong>Postal code</strong>
            {{data.location.postalCode}}
          </div>

          <div v-if="data.location.city" class="city">
            <strong>City</strong>
            {{data.location.city}}
          </div>

          <div v-if="data.location.countryCode" class="countryCode">
            <strong>Country code</strong>
            {{data.location.countryCode}}
          </div>

          <div v-if="data.location.region" class="region">
            <strong>Region</strong>
            {{data.location.region}}
          </div>
        </section>

      <section v-if="data.profiles" id="profiles">
        <h3>Profiles</h3>
        <div v-for="profile in data.profiles" class="item">

          <strong v-if="profile.network" class="network">
            {{profile.network}}
          </strong>


          <div v-if="profile.username" class="username no-print">
            <a href="{{profile.url}}">{{profile.username}}</a>
          </div>


          <div v-if="profile.url" class="url print-only">
            <a href="{{profile.url}}">{{profile.url}}</a>
          </div>

        </div>
      </section>
    </div>
  </div>
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
