<template>

    <div id="platform-metrics-secondary-content-box">
     
        <div id="platform-metrics-secondary-content-box-content">

            <div v-for="post of posts">
                <!-- <p>{{post.carriersMetrics.numActiveCarriers}}</p> -->
            </div>
    
            <div id="platform-metrics-secondary-content-graph">
              <GChart :type="type" :data="data" :options="options" 
              />

                
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
      type: 'PieChart',
      data: [
        ['Task', 'Percent'],
        ['Logistics1', 11],
        ['Logistics2', 2],
        ['Logistics3 ', 2],
        ['Logistics4', 2],
        ['Logistics5', 7],
      ],
      options: {
          title: 'Top 10 Active Carriers',
          pieHole: 0.4,

          width: 620,
          height: 250,
          
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