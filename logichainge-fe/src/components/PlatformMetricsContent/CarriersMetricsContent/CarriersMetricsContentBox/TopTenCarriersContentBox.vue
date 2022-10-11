<template>

    <div id="client-metrics-secondary-content-box">
        <div id="client-metrics-secondary-content-box-title">
            {{name}}
        </div>
        <div id="client-metrics-secondary-content-box-content">

            <div v-for="post of posts">
                <!-- <p>{{post.carriersMetrics.numActiveCarriers}}</p> -->
            </div>
    
            <div id="platform-metrics-initial-content-graph">
               
                <keep-alive>
                    <Pie
                        :chart-options="chartOptions"
                        :chart-data="chartData"
                        :chart-id="chartId"
                        :dataset-id-key="datasetIdKey"
                        :plugins="plugins"
                        :css-classes="cssClasses"
                        :styles="styles"
                        :width="width"
                        :height="height"
                    />
                </keep-alive>
            </div>
      
        </div>
    </div>
    
</template>


<script>
import { Pie } from 'vue-chartjs/legacy'
  
  import {
    Chart as ChartJS,
    Title,
    Tooltip,
    Legend,
    ArcElement,
    CategoryScale
  } from 'chart.js'
  
  ChartJS.register(Title, Tooltip, Legend, ArcElement, CategoryScale)
  
  export default {
    name: 'PieChart',
    components: {
      Pie
    },
    props: {
      name: String,
      chartId: {
        type: String,
        default: 'pie-chart'
      },
      datasetIdKey: {
        type: String,
        default: 'label'
      },
      width: {
        type: Number,
        default: 300
      },
      height: {
        type: Number,
        default: 200
      },
      cssClasses: {
        default: '',
        type: String
      },
      styles: {
        type: Object,
        default: () => {}
      },
      plugins: {
        type: Array,
        default: () => []
      }
    },
    emits: ['chart:updated'],
    data() {
      return {
        chartData: {
          labels: ['LogiTrans1',
           'LogiTrans2',
            'LogiTrans3',
             'LogiTrans4',
             'LogiTrans5',
            'LogiTrans6',
             'LogiTrans7'],
          datasets: [
            {
              backgroundColor: [
              '#41B883', 
              '#E46651', 
              '#E8411D', 
              '#33E203',
              '#FFA07A', 
              '#17D7CE',
              '#CD5C5C'],
              data: [10, 8 , 2, 20, 30, 12, 18]
            }
          ]
        },
        chartOptions: {
          responsive: true,
          maintainAspectRatio: false
        }
      }
    },
           // Pulls posts when the component is created.
           created() {
               axios
                   .get(`http://127.0.0.1:8000/platformMetrics`)
                   .then((response) => {
                   this.posts = response.data;
                //    this.chartData.labels=[ '2020', '2024', '2022' ];
               
               })
                   .catch((e) => {
                   this.errors.push(e);
               });
           },
            computed: {
                
                }
           ,
             mounted(){
                const ctx = document.getElementById('platform-metrics-initial-content-graph');
                new ChartJS(ctx, this.planetChartData);
           }
        };
  

</script>

<style scoped>
    #client-metrics-secondary-content-box{
        height: 90%;
        width: 85%;
        border-radius: 10px;
        display: flex;
        flex-direction: column;
        background-color: rgb(201, 191, 191);
    }

    #client-metrics-secondary-content-box-title{
        height: 15%;
        width: 95%;
        display: flex;
        padding-left: 5%;
        align-items: center;
        font-size: 1.1vw;
        text-transform: uppercase;
        font-weight: 500;
        font-family: Roboto,sans-serif;
        color: grey;
    }

    #client-metrics-secondary-content-box-content{
        height: 85%;
        width: 100%;
    }

</style>