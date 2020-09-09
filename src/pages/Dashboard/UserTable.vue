<template>
<base-table :data="tableData"
            :columns="columns">
        <template slot="columns">
          <th>Year</th>
          <th>No. of matches</th>
        </template>
        <template slot-scope="{row}">
          <td>{{row.year}}</td>
          <td>{{row.matches}}</td>
        </template>
</base-table>
</template>
<script>
  import { BaseTable } from "@/components";
  export default {
    data() {
    return {
      columns: ["year", "matches"],
      tableData: [
        {
          year: 2008,
          matches: 2
        },
        {
          year: 2009,
          matches: 3
        },
        {
          year: 2011,
          matches: 3
        },
        {
          year: 2014,
          matches: 1
        },
        {
          year: 2015,
          matches: 2
        },
        {
          year: 2016,
          matches: 4
        },
        {
          year: 2017,
          matches: 1
        },
      ]
    }
  },
    components: {
      BaseTable
    },
    computed: {
      table(){
        return this.$t('dashboard.usersTable');
      }
    }
  }
</script>
<style>
</style>
