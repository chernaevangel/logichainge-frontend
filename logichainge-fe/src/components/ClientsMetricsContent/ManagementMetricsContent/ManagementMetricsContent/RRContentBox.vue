<template>
    <div id="platform-metrics-initial-content-box">
    
        <div id="platform-metrics-initial-content-box-content">
             
                    <div id="platform-metrics-initial-content-json"
                     v-for="post of utilizationRate">
                        <!-- <p>{{post.operationalMetrics.utilizationRate}}</p> -->
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
      type: 'ComboChart',
      data:  [
            [
                'Month',
                'CRR'
            ],
            ['January', 95],
            ['February', 90],
            ['March', 85],
            ['April', 98],
            ['May', 89],
            ['June', 90],
            ],
      options: {
    title: 'Carriers Retention Rate',
    vAxis: { title: 'Cups' },
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