<template>
<div id="app">

  <button @click.prevent="show.json = !show.json" class="btn-toggle no-print">Show as JSON</button>
  <div v-show="show.json" transition="fadeRight" class="json animated">
    <pre>{{resume | json}}</pre>
  </div>

  <div  v-show="!show.json" transition="fadeLeft" class="animated resume-wrap">
    <p class="print-only">View this resume online at <strong>http://ryanhightower.com/resume/imagine-learning</strong> for an enhanced reading experience.</p>
    <div id="resume">
      <section-basics :data="resume.basics"></section-basics>
      <section-work :data="resume.work"></section-work>
      <section-volunteer :data="resume.volunteer"></section-volunteer>
      <section-education :data="resume.education"></section-education>
      <section-skills :data="resume.skills"></section-skills>
      <section-languages :data="resume.languages"></section-languages>
      <section-interests :class="no-print" :data="resume.interests"></section-interests>
    </div>
  </div>
</div>
</template>

<script>
// import Vue from 'vue'
import SectionBasics from './components/SectionBasics'
import SectionWork from './components/SectionWork'
import SectionVolunteer from './components/SectionVolunteer'
import SectionEducation from './components/SectionEducation'
import SectionLanguages from './components/SectionLanguages'
import SectionSkills from './components/SectionSkills'
import SectionInterests from './components/SectionInterests'
// import SectionAwards from './components/SectionAwards'
// import SectionReferences from './components/SectionReferences'
const resume = require('./assets/resume.json')

// Vue.transition('fade-left', {
//   enterClass: 'fadeInLeft',
//   leaveClass: 'fadeOutLeft'
// })
// Vue.transition('fade-right', {
//   enterClass: 'fadeInRightBig',
//   leaveClass: 'fadeOutRightBig'
// })
// Vue.transition('fade', {
//   // enterClass: 'fadeIn',
//   // leaveClass: 'fadeOut',
//   // enter: function (el, done) {
//   //   console.log('fading in!', el)
//   //   el.classList.add('fadeIn')
//   //   done()
//   // },
//   // leave: function (el, done) {
//   //   console.log('fading OUT!', el)
//   //   el.classList.add('fadeOut')
//   //   done()
//   // }
// })

export default {
  data () {
    return {
      resume,
      show: {
        json: false
      }
    }
  },
  components: {
    SectionBasics,
    SectionWork,
    SectionVolunteer,
    SectionEducation,
    SectionLanguages,
    SectionSkills,
    SectionInterests
    // SectionAwards,
    // SectionReferences
  }

}
</script>

<style>
@import "~/static/animate.min.css";

pre {white-space:pre-wrap;}
*{ transition: all .3s ease; box-sizing: border-box; }
li:hover { color:rgba(255, 0, 50, 1);}
li:nth-child(5n+2):hover { color:rgba(255, 125, 50, 1);}
/*li:nth-child(5n+3):hover { color:rgba(225, 220, 80, 1);}*/
li:nth-child(5n+3):hover { color:#42b983;}
li:nth-child(5n+4):hover { color:rgba(80, 140, 220, 1);}
li:nth-child(5n+5):hover { color:rgba(180, 40, 210, 1);}
section:hover{ transform: translateX(3px); color: #545454; }

html{width: 100%;}
body {
  width: 100%;
	/*background: #fff;*/
	/*font: 15px Source Sans Pro, Arial, Helvetica, sans-serif;*/
	line-height: 1.4;
	margin: 50px 0;
	margin-bottom: 100px;
}

.btn-toggle{ position: fixed;top:20px; right: 40px; z-index:999; }
.json, .resume-wrap{ position: absolute; top:0px; left: 0; padding: 20px; background: #fff; width: 100%; }
#resume {
  background: #fff;
  color: #787878;
  margin-top: -100px;
  font-family: Source Sans Pro, Helvetica, sans-serif;
}

#resume a {
  color: #42b983;
  text-decoration: none;
}


em {
	color: #999;
}
p {
	line-height: 1.4;
}
ul {
	margin-bottom: 0;
}
section {
	margin-bottom: 2em;
}
blockquote {
	margin: 0;
	margin-bottom: 1em;
}
.item {
	margin-bottom: 1em;
}
#resume {
	margin: 0 auto;
	max-width: 640px;
	padding: 0 20px;
}
#basics {
	margin-bottom: -10px;
}
#basics h3 {
	margin-top: 1.5em;
}
#basics .contact strong,
#location strong {
	clear: both;
	float: left;
	line-height: 1.3;
	width: 120px;
}
#profiles,
#skills,
#education,
#interests  {
	overflow: hidden;
}
#profiles .item,
#skills .item,
#education .item,
#interests .item {
	float: left;
	width: 50%;
}
/************************************************************/
/* Media Queries */
/************************************************************/
@media screen {
  .print-only{
    display: none;
  }
}
@media print {
  html{ font-size: 75% }
  h1,h2,h3,h4,h5,h6{ margin: }
  .no-print{
    display: none;
  }
  .hidden-print{
    visibility: hidden;
  }
}
/************************************************************/
/* Transitions */
/************************************************************/
.fade-transition, .fadeRight-transition, .fadeLeft-transition {
    opacity: 1;
    transform: translatex(0);
    transition: all 0.3s ease;
}

.fade-transition.fade-enter, .fade-transition.fade-leave,
.fadeRight-transition.fadeRight-leave, .fadeRight-transition.fadeRight-enter,
.fadeLeft-transition.fadeLeft-leave, .fadeLeft-transition.fadeLeft-enter {
    opacity: 0;
}
.fade-transition.fade-leave { transform: translateX(50%); }
.fade-transition.fade-enter { transform: translateX(-50%); }
.fadeRight-transition.fadeRight-leave, .fadeRight-transition.fadeRight-enter { transform: translateX(50%); }
.fadeLeft-transition.fadeLeft-leave, .fadeLeft-transition.fadeLeft-enter { transform: translateX(-50%); }

/* delay here */
.fade-transition.delay {
    transition-delay: 0.3s;
}

</style>
