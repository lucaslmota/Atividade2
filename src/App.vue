<template>
  <div id="app">
    <Inputs />
    <Table :tables="tasks"/>
    
  </div>
</template>

<script>
import Inputs from './components/Inputs'
import Table from './components/Table'

export default {
  components: {Inputs, Table},
  data() {
    return {
      tasks: this.tasks
    }
  }
}
</script>

<style>

</style>
