<template>
  <section class="todoapp">
    <VHeader></VHeader>
    <List></List>
    <VFooter></VFooter>
  </section>
</template>

<script>
  import Header from './header'
  import List from './list'
  import Footer from './footer'
  export default {
    components: {
      VHeader: Header,
      List,
      VFooter: Footer
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  @import "index.css";
</style>
