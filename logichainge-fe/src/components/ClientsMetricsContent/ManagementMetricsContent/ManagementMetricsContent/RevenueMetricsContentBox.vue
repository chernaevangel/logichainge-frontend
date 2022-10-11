<template>
    <div id="client-metrics-initial-content-box">
        <div id="client-metrics-initial-content-box-title">
            {{name}}
        </div>
        <div id="client-metrics-initial-content-box-content">

            <div v-for="post of posts">
                <p>{{post.managementMetics.salesRevenue}}</p>
            </div>

            <div id="client-metrics-initial-content-graph">
                <keep-alive>
                    <Bar
                
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
    import { Bar } from 'vue-chartjs/legacy'

    import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

    
    ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)
 
    export default {
        name: 'BarChart',
            components: { Bar },
            props: {
                name: String,
                utilizationRate: Array,
                chartId: {
                type: String,
                default: 'bar-chart'
                },
                datasetIdKey: {
                type: String,
                default: 'label'
                },
                width: {
                type: Number,
                default: 550
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
                type: Object,
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
                    'January', 
                    'February', 
                    'March', 
                    'April', 
                    'May', 
                    'June'  ],
                    datasets: [ {
                        label : 'Revenue',
                        backgroundColor: '	#48B406	',
                        data: [112000, 112500 , 114500, 113500, 111111, 113500] } ]
                },
                chartOptions: {
                    responsive: true
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
    #client-metrics-initial-content-box{
        height: 90%;
        width: 85%;
        border-radius: 10px;
        display: flex;
        flex-direction: column;
        background-color: rgb(201, 191, 191);
    }

    #client-metrics-initial-content-box-title{
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

    #client-metrics-initial-content-box-content{
        height: 85%;
        width: 100%;
        display: flex;
        flex-direction: column;
    }

    #client-metrics-initial-content-json{
        height: 10%;
        width: 100%;
        font-size: 0.8vw;
        display: flex;
        
    }

    #client-metrics-initial-content-graph{
        height: 90%;
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
    }

</style>