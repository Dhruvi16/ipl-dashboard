<template>
  <div>
    <card class="card">
      <h2 slot="header" class="card-title text-center">Indian Premier League (Match Analysis)</h2>
      <div class="table-responsive">
        <task-list></task-list>
      </div>
    </card>
  </div>
</template>
<script>
  import TaskList from './Dashboard/TaskList';

  export default {
    components: {
      TaskList
    },
  }

</script>
<style>
</style>
