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

    import axios from "axios";
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
            ['January', 500],
            ['February', 200],
            ['March', 500],
            ['April',900],
            ['May', 600],
            ['June', 200]
            ],
      options: {
            title: 'Average Time For Order Completion ',
            curveType: 'function',
            legend: { position: 'bottom' },
            width: 420,
                height: 250,
            colors: ['#1b9e77']
            },
    };
  },
};
    
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