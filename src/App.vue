<template>
  <div class="main">
    <Navigation />
    <Count />
    <TableView />
  </div>
</template>

<script>
import Navigation from './components/Navigation.vue';
import Count from './components/Count.vue'
import TableView from './components/TableView.vue'

export default{
  components: {
    Navigation, Count, TableView
  },
}
</script>

<style>
    body {
       margin: 0;
    }
</style>