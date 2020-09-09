<template>
  <div>
    <vue-good-table
      :columns="columns"
      :rows="data"
      :search-options="{
        enabled: true,
        trigger: 'enter',
        skipDiacritics: true,
        placeholder: 'Search this table'}" />
  </div>
</template>
<script>
  import data from '../../assets/data.json'
  import { VueGoodTable } from 'vue-good-table';


  export default {
    components: {
      VueGoodTable
    },
    data() {
      return {
        data,
        columns: [
          {
            label: 'ID',
            field: 'id',
          },
          {
            label: 'Season',
            field: 'season',
          },
          {
            label: 'City',
            field: 'city',
          },
          {
            label: 'Date',
            field: 'date',
          },
          {
            label: 'Team1',
            field: 'team1',
          },
          {
            label: 'Team2',
            field: 'team2',
          },
          {
            label: 'Toss winner',
            field: 'toss_winner',
          },
          {
            label: 'Toss Decision',
            field: 'toss_decision',
          },
          {
            label: 'Result',
            field: 'result',
          },
          {
            label: 'DL Applied',
            field: 'dl_applied',
          },
          {
            label: 'Winner',
            field: 'winner',
          },
          {
            label: 'Win by Runs',
            field: 'win_by_runs',
          },
          {
            label: 'Win by Wickets',
            field: 'win_by_wickets',
          },
          {
            label: 'Player of match',
            field: 'player_of_match',
          },
          {
            label: 'Venue',
            field: 'venue',
          },
          {
            label: 'Umpire 1',
            field: 'umpire1',
          },
          {
            label: 'Umpire 2',
            field: 'umpire2',
          },
        ],
      }
    },
}
</script>
<style>
</style>

