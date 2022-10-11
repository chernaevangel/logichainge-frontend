<template>
    <div id="platform-metrics-initial-content-box">
        <div id="platform-metrics-initial-content-box-title">
            {{name}}
        </div>
        <div id="platform-metrics-initial-content-box-content">
             
                    <div id="platform-metrics-initial-content-json"
                     v-for="post of utilizationRate">
                        <p>{{post.operationalMetrics.utilizationRate}}</p>
                    </div>
                    
                    
                            <div id="platform-metrics-initial-content-graph">
                                <keep-alive>
                                    <Radar
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
    import axios from "axios";
        import { Radar} from 'vue-chartjs/legacy'
    
        import {
            Chart as ChartJS,
            Title,
            Tooltip,
            Legend,
            PointElement,
            LineElement,
            RadialLinearScale
            } from 'chart.js'
    
        
        ChartJS.register(Title,
        Title,
        Tooltip,
        Legend,
        PointElement,
        RadialLinearScale,
        LineElement)
            
        export default {
            name: 'RadarChart',
                components: {
                    Radar
            },
                props: {
                    name: String,
                    utilizationRate: Array,
                    chartId: {
                    type: String,
                    default: 'radar-chart'
                    },
                    datasetIdKey: {
                    type: String,
                    default: 'label'
                    },
                    width: {
                    type: Number,
                    default: 440
                    },
                    height: {
                    type: Number,
                    default: 225
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
                    default: () => {}
                    }
                },

           
           emits: ['chart:updated'],
           data() {
               return {
                   posts: [],
                   errors: [],
                   chartData: {
        labels: [
          'Address',
          'Postcode',
          'Company Name',
          'Order Fields',
          'Shippment Fields',
          'Carrier Fields',
          'Details'
        ],
        datasets: [
          {
            label: '1-st half 2022',
            backgroundColor: '#f1b840',
            borderColor: '#f1b840',
            pointBackgroundColor: 'rgba(179,181,198,1)',
            pointBorderColor: '#fff',
            pointHoverBackgroundColor: '#fff',
            pointHoverBorderColor: 'rgba(179,181,198,1)',
            data: [65, 59, 90, 81, 56, 55, 40]
          },
          {
            label: '2-nd half 2022',
            backgroundColor: 'rgba(255,99,132,1)',
            borderColor: 'rgba(255,99,132,1)',
            pointBackgroundColor: 'rgba(255,99,132,1)',
            pointBorderColor: '#fff',
            pointHoverBackgroundColor: '#fff',
            pointHoverBorderColor: 'rgba(255,99,132,1)',
            data: [28, 48, 40, 19, 96, 27, 100]
          }
        ]
      },
                    chartOptions: {
                        responsive: true,
                         maintainAspectRatio: false
                    }
               };
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
    #platform-metrics-initial-content-box{
        height: 90%;
        width: 90%;
        border-radius: 10px;
        display: flex;
        flex-direction: column;
        background-color: rgb(201, 191, 191);
    }

    #platform-metrics-initial-content-box-title{
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

    #platform-metrics-initial-content-box-content{
        height: 85%;
        width: 100%;
        display: flex;
        flex-direction: column;
    }

    #platform-metrics-initial-content-json{
        height: 10%;
        width: 100%;
        font-size: 0.8vw;
        display: flex;
        
    }

    #platform-metrics-initial-content-graph{
        height: 90%;
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
    }

</style>