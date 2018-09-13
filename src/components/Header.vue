<template>
  <header class="header">
    <img alt="Digital Risks logo" src="../assets/digital-risks-white@2x.png" width="104" height="22">
    <span>Call us on 0333 772 0759</span>
  </header>
</template>

<script>
export default {
  name: 'Header',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	.header { 
		background-color: #ff2c6f;
		color: #fff;
		height: 57px;
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 0 20px;
	}
</style>
