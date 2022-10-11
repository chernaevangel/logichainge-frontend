<template>

    <div id="client-metrics-secondary-content-box">
        <div id="client-metrics-secondary-content-box-title">
            {{name}}
        </div>
        <div id="client-metrics-secondary-content-box-content">

            <div v-for="post of posts">
                <p>{{post.carriersMetrics.numActiveCarriers}}</p>
            </div>
            <div id="platform-metrics-initial-content-graph">
                <keep-alive>
                    <LineChartGenerator
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
        import {  Line as LineChartGenerator } from 'vue-chartjs/legacy'
    
        import {
            Chart as ChartJS,
            Title,
            Tooltip,
            Legend,
            LineElement,
            LinearScale,
            CategoryScale,
            PointElement
            } from 'chart.js'
    
        
        ChartJS.register(Title,
            Tooltip,
            Legend,
            LineElement,
            LinearScale,
            CategoryScale,
            PointElement)
     
        export default {
            name: 'LineChart',
                components: {
                LineChartGenerator
            },
                props: {
                    name: String,
                    utilizationRate: Array,
                    chartId: {
                    type: String,
                    default: 'line-chart'
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
                    default: 205
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
                        labels: ['January',
                            'February',
                            'March',
                            'April',
                            'May',
                            'June',
                            'July'],
                        datasets: [ {
                                label: 'Active Carriers',
                                backgroundColor: '#008000',
                                data: [32,33 , 35, 41, 45, 42, 48]
                            } ]
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