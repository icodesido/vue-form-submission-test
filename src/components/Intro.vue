<template>
  <div class="intro">
    <div>
      <h1 class="intro__header">{{ header }}</h1>
      <p class="intro__para">{{ para }}</p>
    </div>
  </div>
</template>

<script>
export default {
	data() {
		return {
			header: 'One last step',
			para: 'To save your quote and process your policy, we’ll need you to confirm your detail'
		}
	},
  name: 'Intro'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .intro {
    padding: 30px 20px 15px;
  }

  .intro__header {
    font-weight: normal;
    font-size: 22px;
    color: #ff2c6f;
  }

  .intro__para {
    font-size: 14px;
    line-height: 1.5;
  }
</style>
