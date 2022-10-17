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
                                <GChart :type="type" :data="data" :options="options" />
                            </div>
                
        </div>
    </div>
</template>

<script>
import { GChart } from 'vue-google-charts/legacy';


export default {
  name: 'GoogleChart',
  components: {
    GChart,
  },
  data() {
    return {
      type: 'LineChart',
      data:[
            ['Year', '2021 Metrics'],
            ['January', 8175000],
            ['February', 3792000],
            ['March', 2695000],
            ['April', 2099000],
            ['May', 1526000],
            ['June', 1522000]
            ],
      options: {
            title: 'Delivery Times',
            curveType: 'function',
            legend: { position: 'bottom' },
            width: 420,
                height: 250,
            },
    };
  },
};
    // import axios from "axios";
    //     import {  Line as LineChartGenerator } from 'vue-chartjs/legacy'
    
    //     import {
    //         Chart as ChartJS,
    //         Title,
    //         Tooltip,
    //         Legend,
    //         LineElement,
    //         LinearScale,
    //         CategoryScale,
    //         PointElement
    //         } from 'chart.js'
    
        
    //     ChartJS.register(Title,
    //         Tooltip,
    //         Legend,
    //         LineElement,
    //         LinearScale,
    //         CategoryScale,
    //         PointElement)
     
    //     export default {
    //         name: 'LineChart',
    //             components: {
    //             LineChartGenerator
    //         },
    //             props: {
    //                 name: String,
    //                 utilizationRate: Array,
    //                 chartId: {
    //                 type: String,
    //                 default: 'line-chart'
    //                 },
    //                 datasetIdKey: {
    //                 type: String,
    //                 default: 'label'
    //                 },
    //                 width: {
    //                 type: Number,
    //                 default: 440
    //                 },
    //                 height: {
    //                 type: Number,
    //                 default: 200
    //                 },
    //                 cssClasses: {
    //                 default: '',
    //                 type: String
    //                 },
    //                 styles: {
    //                 type: Object,
    //                 default: () => {}
    //                 },
    //                 plugins: {
    //                 type: Array,
    //                 default: () => {}
    //                 }
    //             },

           
    //        emits: ['chart:updated'],
    //        data() {
    //            return {
    //                posts: [],
    //                errors: [],
    //                chartData: {
    //                     labels: ['January',
    //                         'February',
    //                         'March',
    //                         'April',
    //                         'May',
    //                         'June',
    //                         'July'],
    //                     datasets: [ {
    //                             label: 'Delivery times',
    //                             backgroundColor: '#f87979',
    //                             data: [40, 39, 10, 40, 39, 80, 40]
    //                         } ]
    //                 },
    //                 chartOptions: {
    //                     responsive: true,
    //                      maintainAspectRatio: false
    //                 }
    //            };
    //        },
    //        // Pulls posts when the component is created.
    //        created() {
    //            axios
    //                .get(`http://127.0.0.1:8000/platformMetrics`)
    //                .then((response) => {
    //                this.posts = response.data;
    //             //    this.chartData.labels=[ '2020', '2024', '2022' ];
               
    //            })
    //                .catch((e) => {
    //                this.errors.push(e);
    //            });
    //        },
    //         computed: {
                
    //             }
    //        ,
    //          mounted(){
    //             const ctx = document.getElementById('platform-metrics-initial-content-graph');
    //             new ChartJS(ctx, this.planetChartData);
    //        }
    //     };
    
    </script>
    
    <style scoped>
        #platform-metrics-initial-content-box{
            height: 90%;
            width: 90%;
            border-radius: 10px;
            display: flex;
            flex-direction: column;
         
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