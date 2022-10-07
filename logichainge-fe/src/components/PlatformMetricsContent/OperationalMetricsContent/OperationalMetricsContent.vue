<template>
    <div id="platform-metrics-initial-content">
        <div id="platform-metrics-initial-content-row">
           <div id="platform-metrics-initial-content-box-wrapper">
            <keep-alive>
                <component :is="component" 
                name="Utilization Rate"
                :utilizationRate="posts"
                />

        
            </keep-alive>   
           </div>
           <div id="platform-metrics-initial-content-box-wrapper">
           
            <keep-alive>
                <component :is="component" 
                name="Delivery times"/>
        
            </keep-alive>   
                 
            </div>
            <div id="platform-metrics-initial-content-box-wrapper">
                <keep-alive>
                    <component :is="component" 
                    name="Carrying costs"
                    />
                </keep-alive>   
                       
            </div>
        </div>
        <div id="platform-metrics-initial-content-row">
            <div id="platform-metrics-initial-content-box-wrapper">
                <keep-alive>
                    <component :is="component" 
                    name="Average Time for Order Completion"
                    />
                </keep-alive>   
                
            </div>
            <div id="platform-metrics-initial-content-box-wrapper">
                <keep-alive>
                    <component :is="component" 
                    name="Percent Correct Auto-Filled Fields"
                    />
                </keep-alive>   
                           
             </div>
             <div id="platform-metrics-initial-content-box-wrapper">
                <keep-alive>
                    <component :is="component" 
                    name="Amount Critical Issues"
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
import OperationalMetricsContentBox from "./OperationalMetricsContentBox/OperationalMetricsContentBox.vue";

    ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)
    
    export default {
        name: 'BarChart',
            components: {  
                'OMCB-Component' : OperationalMetricsContentBox },
            props: {
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
                default: 440
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
       data() {
           return {
               posts: [],
               errors: [],
               chartData: {
                    labels: [ '2020', '2021', '2022' ],
                    datasets: [ {
                        label : 'Utilization Rate',
                        data: [36, 20, 12] } ]
                },
                chartOptions: {
                    responsive: true
                },
                component : 'OMCB-Component'
           };
       },
       // Pulls posts when the component is created.
       created() {
           axios
               .get(`http://127.0.0.1:8000/platformMetrics`)
               .then((response) => {
               // JSON responses are automatically parsed.
               this.posts = response.data;
               // console.log(response.data)
           })
               .catch((e) => {
               this.errors.push(e);
           });
       }
    };
    
    </script>



<style scoped>
    #platform-metrics-initial-content{
        height: 88%;
        width: 100%;
        display: flex;
        flex-direction: column;
    }

    #platform-metrics-initial-content-row{
        height: 50%;
        width: 100%;
        display: flex;
    }

    #platform-metrics-initial-content-box-wrapper{
        height: 100%;
        width: 33.33%;
        display: flex;
        justify-content: center;
        align-items: center;
    }

 

</style>