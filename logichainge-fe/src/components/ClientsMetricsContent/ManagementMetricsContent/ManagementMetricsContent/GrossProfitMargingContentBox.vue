<template>
    <div id="platform-metrics-secondary-content-box">
        <!-- <div id="client-metrics-secondary-content-box-title">
            {{name}}
        </div> -->
        <div id="platform-metrics-secondary-content-box-content">

            <div v-for="post of posts">
                <!-- <p>{{post.carriersMetrics.numActiveCarriers}}</p> -->
            </div>
    
            <div id="platform-metrics-initial-content-graph">
              <GChart :type="type" :data="data" :options="options" 
              :resizeDebounce="500"/>

                
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
      type: 'ComboChart',
      data: [
        [
            'Month',
            'GPM'
        ],
        ['January', 163335],
        ['February', 134335],
        ['March', 155337],
        ['April', 135339],
        ['May', 135336],
        ['June', 135338]
        ],
      options: {
            title: 'Gross Profit Margin',
            vAxis: { title: 'Value' },
            hAxis: { title: 'Month' },
            seriesType: 'bars',
            series: { 5: { type: 'line' } },
            width: 620,
            height: 250,
            
            },
    };
  },
};


</script>


<style scoped>
    #client-metrics-initial-content-box{
        height: 90%;
        width: 85%;
        border-radius: 10px;
        display: flex;
        flex-direction: column;
       
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