<template>

    <div id="platform-metrics-secondary-content-box">
       
        <div id="platform-metrics-secondary-content-box-content">

            <div v-for="post of posts">
                <p>{{post.carriersMetrics.numActiveCarriers}}</p>
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
            ['January', 90],
            ['February', 70],
            ['March', 80],
            ['April',80],
            ['May', 90],
            ['June', 100]
            ],
      options: {
            title: 'Average Carriers Satisfaction Rate',
            curveType: 'function',
            legend: { position: 'bottom' },
            width: 620,
            height: 250,
            colors: ['#1b9e77']
            },
    };
  },
};
    
    </script>
    
    <style scoped>
        #client-metrics-secondary-content-box{
            height: 90%;
            width: 85%;
            border-radius: 10px;
            display: flex;
            flex-direction: column;
           
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
           
        }
    
        #client-metrics-secondary-content-box-content{
            height: 85%;
            width: 100%;
        }
    
    </style>