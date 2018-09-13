<template>
  <main>
    <form class="form">
      <h1>{{ msg }}</h1>
    </form>
  </main>
</template>

<script>
export default {
  name: 'Form',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
