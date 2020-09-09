<template>
  <div>
    <div class="heading">
      <h1 class="text-center">Check out some interesting stats about IPL!</h1>
      <h6 class="sub text-center">We are not at all trying to lure you into watching IPL using these juicy numbers! &#128521;</h6>
    </div>

    <div class="row">
      <div class="col-lg-4">
        <card type="chart">
          <template slot="header">
            <h5 class="card-category">Fun Fact - 51.4% of toss winners were match winners</h5>
            <h3 class="card-title"><i class="tim-icons icon-coins text-primary "></i> Toss wins per team</h3>
          </template>
          <div class="chart-area">
            <line-chart style="height: 100%" chart-id="purple-line-chart" :chart-data="tossWinsPerTeam.chartData"
              :gradient-colors="tossWinsPerTeam.gradientColors" :gradient-stops="tossWinsPerTeam.gradientStops"
              :extra-options="tossWinsPerTeam.extraOptions">
            </line-chart>
          </div>
        </card>
      </div>
      <div class="col-lg-4">
        <card type="chart">
          <template slot="header">
            <h5 class="card-category">Mumbai Indians won the most matches!</h5>
            <h3 class="card-title"><i class="tim-icons icon-book-bookmark text-info"></i>Wins per Team</h3>
          </template>
          <div class="chart-area">
            <bar-chart style="height: 100%" chart-id="blue-bar-chart" :chart-data="winsperteam.chartData"
              :gradient-stops="winsperteam.gradientStops" :extra-options="winsperteam.extraOptions">
            </bar-chart>
          </div>
        </card>
      </div>
      <div class="col-lg-4">
        <card>
          <h2 class="card-title">Do you know? <i class="tim-icons icon-light-3"></i></h2>
          <h4>M Chinnaswamy Stadium had the highest number of matches that is - <span class="text-success">63</span>.
          </h4>
        </card>
        <card>
          <h2 class="card-title">Wanna see some amazing numbers? <i class="tim-icons icon-light-3"></i></h2>
          <h4>Mumbai Indians has played more than <span class="text-info">150</span> matches in total.</h4>
        </card>
      </div>
    </div>
    <div class="row">
      <div class="col-lg-6 col-md-12">
        <card type="chart">
          <template slot="header">
            <h5 class="card-category">We know you care about Run Rate of your favourite team</h5>
            <h3 class="card-title"><i class="tim-icons icon-chart-bar-32 text-primary"></i> Performance of Teams based on
              Winning Runs</h3>
          </template>
          <div class="chart-area">
            <bar-chart style="height: 100%" chart-id="purple-line-chart" :chart-data="teamPerformanceRuns.chartData"
              :gradient-colors="teamPerformanceRuns.gradientColors" :gradient-stops="teamPerformanceRuns.gradientStops"
              :extra-options="teamPerformanceRuns.extraOptions">
            </bar-chart>
          </div>
        </card>
      </div>
      <div class="col-lg-6 col-md-12">
        <card type="chart">
          <template slot="header">
            <h5 class="card-category">Look who's winning by how many wickets!</h5>
            <h3 class="card-title"><i class="tim-icons icon-chart-bar-32 text-primary "></i> Performance of Teams based on
              Winning wickets</h3>
          </template>
          <div class="chart-area">
            <line-chart style="height: 100%" chart-id="purple-line-chart" :chart-data="teamPerformanceWickets.chartData"
              :gradient-colors="teamPerformanceWickets.gradientColors"
              :gradient-stops="teamPerformanceWickets.gradientStops"
              :extra-options="teamPerformanceWickets.extraOptions">
            </line-chart>
          </div>
        </card>
      </div>
    </div>
    <div class="row">
      <div class="col-lg-4">
        <card class="card" :header-classes="{'text-right': isRTL}">
          <h4 slot="header" class="card-title">No. of matches where D/L method was applied, season wise</h4>
          <div class="table-responsive">
            <user-table></user-table>
          </div>
        </card>
      </div>
      <div class="col-lg-4">
        <card>
          <h2 class="card-title">Interesting Toss Stats <i class="tim-icons icon-light-3"></i></h2>
          <h4><span class="text-success">57.1%</span> of Toss decisions were to Field and <span
              class="text-success">53.6%</span> of those teams won the respective matches.</h4>
        </card>
        <card type="chart">
          <template slot="header">
            <h5 class="card-category">Looking for your favourite umpire? Take a look at this!</h5>
            <h3 class="card-title"><i class="tim-icons icon-tap-02 text-success "></i> Top Umpires of the match</h3>
          </template>
          <div class="chart-area">
            <line-chart style="height: 100%" chart-id="green-line-chart" :chart-data="topUmpires.chartData"
              :gradient-stops="topUmpires.gradientStops" :extra-options="topUmpires.extraOptions">
            </line-chart>
          </div>
        </card>
      </div>
      <div class="col-lg-4">
        <card type="chart">
          <template slot="header">
            <h5 class="card-category">CH Gayle was awarded as Player of the match 18 times!</h5>
            <h3 class="card-title"><i class="tim-icons icon-single-02 text-success "></i> Players vs The count of Player of
              match</h3>
          </template>
          <div class="chart-area">
            <line-chart style="height: 100%" chart-id="green-line-chart" :chart-data="playersVsCount.chartData"
              :gradient-stops="playersVsCount.gradientStops" :extra-options="playersVsCount.extraOptions">
            </line-chart>
          </div>
        </card>
      </div>
    </div>
  </div>
</template>
<script>
  import LineChart from '@/components/Charts/LineChart';
  import BarChart from '@/components/Charts/BarChart';
  import * as chartConfigs from '@/components/Charts/config';
  import UserTable from './Dashboard/UserTable';
  import config from '@/config';
  import messages from '../assets/data.json';
  export default {

    components: {
      LineChart,
      BarChart,
      UserTable
    },
    data() {
      return {
        messages,
        teamPerformanceWickets: {
          extraOptions: chartConfigs.purpleChartOptions1,
          chartData: {
            labels: ['Mumbai Indians', 'Chennai Super Kings', 'Kolkata Knight Riders', 'Royal Challengers Bangalore',
              'Kings XI Punjab', 'Rajasthan Royals', 'Delhi Daredevils',
              'Sunrisers Hyderabad', 'Deccan Chargers', 'Pune Warriors', 'Rising Pune Supergiant',
              'Kochi Tuskers Kerala'
            ],
            datasets: [{
              label: "Winning wickets",
              fill: true,
              borderColor: config.colors.primary,
              borderWidth: 2,
              borderDash: [],
              borderDashOffset: 0.0,
              pointBackgroundColor: config.colors.primary,
              pointBorderColor: 'rgba(255,255,255,0)',
              pointHoverBackgroundColor: config.colors.primary,
              pointBorderWidth: 20,
              pointHoverRadius: 4,
              pointHoverBorderWidth: 15,
              pointRadius: 4,
              data: [6.0, 6.0, 7.0, 7.0, 6.0, 6.0, 6.5, 7.0, 6.0, 6.5, 7.0, 7.5],
            }]
          },
          gradientColors: config.colors.primaryGradient,
          gradientStops: [1, 0.2, 0],
        },
        teamPerformanceRuns: {
          extraOptions: chartConfigs.barChartOptions1,
          chartData: {
            labels: ['Mumbai Indians', 'Chennai Super Kings', 'Kolkata Knight Riders', 'Royal Challengers Bangalore',
              'Kings XI Punjab', 'Rajasthan Royals', 'Delhi Daredevils',
              'Sunrisers Hyderabad', 'Deccan Chargers', 'Pune Warriors', 'Rising Pune Supergiant',
              'Kochi Tuskers Kerala'
            ],
            datasets: [{
              label: "Winning Runs",
              fill: true,
              borderColor: config.colors.danger,
              borderWidth: 2,
              borderDash: [],
              borderDashOffset: 0.0,
              pointBackgroundColor: config.colors.danger,
              pointBorderColor: 'rgba(255,255,255,0)',
              pointHoverBackgroundColor: config.colors.danger,
              pointBorderWidth: 20,
              pointHoverRadius: 4,
              pointHoverBorderWidth: 15,
              pointRadius: 4,
              data: [25.0, 24.0, 23.0, 24.0, 22.5, 31.0, 17.0, 20.0, 14.5, 23.0, 20.0, 11.5],
            }]
          },
          gradientColors: config.colors.primaryGradient,
          gradientStops: [1, 0.2, 0],
        },
        tossWinsPerTeam: {
          extraOptions: chartConfigs.purpleChartOptions,
          chartData: {
            labels: ['Mumbai Indians', 'Chennai Super Kings', 'Kolkata Knight Riders', 'Royal Challengers Bangalore',
              'Kings XI Punjab', 'Rajasthan Royals', 'Delhi Daredevils',
              'Sunrisers Hyderabad', 'Deccan Chargers', 'Pune Warriors', 'Rising Pune Supergiant',
              'Kochi Tuskers Kerala'
            ],
            datasets: [{
              label: "Toss wins",
              fill: true,
              borderColor: config.colors.primary,
              borderWidth: 2,
              borderDash: [],
              borderDashOffset: 0.0,
              pointBackgroundColor: config.colors.primary,
              pointBorderColor: 'rgba(255,255,255,0)',
              pointHoverBackgroundColor: config.colors.primary,
              pointBorderWidth: 20,
              pointHoverRadius: 4,
              pointHoverBorderWidth: 15,
              pointRadius: 4,
              data: [83, 66, 77, 67, 67, 61, 77, 34, 43, 20, 13, 8],
            }]
          },
          gradientColors: config.colors.primaryGradient,
          gradientStops: [1, 0.2, 0],
        },
        playersVsCount: {
          extraOptions: chartConfigs.orangeChartOptions,
          chartData: {
            labels: ['CH Gayle', 'YK Pathan', 'AB de Villiers', 'DA Warner', 'RG Sharma', 'SK Raina', 'G Gambhir',
              'MS Dhoni', 'AM Rahane', 'MEK Hussey'
            ],
            datasets: [{
              label: "Count",
              fill: true,
              borderColor: config.colors.danger,
              borderWidth: 1,
              borderDash: [],
              borderDashOffset: 0.0,
              pointBackgroundColor: config.colors.danger,
              pointBorderColor: 'rgba(255,255,255,0)',
              pointHoverBackgroundColor: config.colors.danger,
              pointBorderWidth: 20,
              pointHoverRadius: 4,
              pointHoverBorderWidth: 15,
              pointRadius: 4,
              data: [18, 16, 15, 15, 14, 14, 13, 13, 12, 12],
            }]
          },
          gradientColors: ['rgba(66,134,121,0.15)', 'rgba(66,134,121,0.0)', 'rgba(66,134,121,0)'],
          gradientStops: [1, 0.04, 0],
        },
        topUmpires: {
          extraOptions: chartConfigs.greenChartOptions,
          chartData: {
            labels: ['HDPK Dharmasena', 'S Ravi', 'AK Chaudhary', 'C Shamshuddin', 'SJA Taufel', 'Asad Rauf',
              'M Erasmus', 'BR Doctrove', 'RE Koertzen', 'CK Nandan'
            ],
            datasets: [{
              label: "Count",
              fill: true,
              borderColor: config.colors.info,
              borderWidth: 1,
              borderDash: [],
              borderDashOffset: 0.0,
              pointBackgroundColor: config.colors.info,
              pointBorderColor: 'rgba(255,255,255,0)',
              pointHoverBackgroundColor: config.colors.info,
              pointBorderWidth: 20,
              pointHoverRadius: 4,
              pointHoverBorderWidth: 15,
              pointRadius: 4,
              data: [84, 83, 57, 56, 55, 51, 51, 42, 41, 41],
            }]
          },
          gradientColors: ['rgba(66,134,121,0.15)', 'rgba(66,134,121,0.0)', 'rgba(66,134,121,0)'],
          gradientStops: [1, 0.04, 0],
        },
        winsperteam: {
          extraOptions: chartConfigs.barChartOptions,
          chartData: {
            labels: ['Mumbai Indians', 'Chennai Super Kings', 'Kolkata Knight Riders', 'Royal Challengers Bangalore',
              'Kings XI Punjab', 'Rajasthan Royals', 'Delhi Daredevils',
              'Sunrisers Hyderabad', 'Deccan Chargers', 'Pune Warriors', 'Rising Pune Supergiant',
              'Kochi Tuskers Kerala'
            ],
            datasets: [{
              label: "Wins",
              fill: true,
              borderColor: config.colors.info,
              borderWidth: 2,
              borderDash: [],
              borderDashOffset: 0.0,
              data: [92, 77, 77, 71, 69, 63, 61, 40, 29, 13, 12, 10, 6],
            }]
          },
          gradientColors: config.colors.primaryGradient,
          gradientStops: [1, 0.4, 0],
        }
      }
    },
    computed: {
      enableRTL() {
        return this.$route.query.enableRTL;
      },
      isRTL() {
        return this.$rtl.isRTL;
      },
      bigLineChartCategories() {
        return this.$t('dashboard.chartCategories');
      }
    },
    methods: {
      initBigChart(index) {
        let chartData = {
          datasets: [{
            fill: true,
            borderColor: config.colors.primary,
            borderWidth: 2,
            borderDash: [],
            borderDashOffset: 0.0,
            pointBackgroundColor: config.colors.primary,
            pointBorderColor: 'rgba(255,255,255,0)',
            pointHoverBackgroundColor: config.colors.primary,
            pointBorderWidth: 20,
            pointHoverRadius: 4,
            pointHoverBorderWidth: 15,
            pointRadius: 4,
            data: this.bigLineChart.allData[index]
          }],
          labels: ['JAN', 'FEB', 'MAR', 'APR', 'MAY', 'JUN', 'JUL', 'AUG', 'SEP', 'OCT', 'NOV', 'DEC'],
        }
        this.$refs.bigChart.updateGradients(chartData);
        this.bigLineChart.chartData = chartData;
        this.bigLineChart.activeIndex = index;
      },
    }
  };
</script>
<style>
  .heading {
    margin-top: 2rem;
    margin-bottom: 6rem;
  }
  .sub {
      margin: 0;
    }
</style>
