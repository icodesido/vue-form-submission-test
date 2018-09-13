<template>
  <div class="home">
    <Header msg="Welcome to Your Vue.js App"/>
    <Intro msg="Welcome to Your Vue.js App"/>
    <Form msg="Welcome to Your Vue.js App"/>

  </div>
</template>

<script>
// @ is an alias to /src
import Header from '@/components/Header.vue'
import Intro from '@/components/Intro.vue'
import Form from '@/components/Form.vue'

export default {
  name: 'home',
  components: {
    Header,
    Intro,
    Form
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
	body { 
		max-width: 360px;
		margin: 0 auto;
		padding: 0;
		color: #444;
	}
</style>