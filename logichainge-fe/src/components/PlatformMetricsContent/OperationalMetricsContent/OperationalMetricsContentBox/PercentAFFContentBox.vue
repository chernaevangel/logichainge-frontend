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
      type: 'ComboChart',
      data:  [
            [
                'Month',
                'Address',
                'Postcode',
                'Company Name',
                'Order Details',
                'Shipment Details',
                'Average',
            ],
            ['January', 98, 90, 90, 90, 10, 69.5],
            ['February', 98, 90, 90, 90, 10, 69.5],
            ['March', 98, 90, 90, 90, 10, 69.6],
            ['April', 98, 90, 90, 90, 10, 69.5],
            ['May', 98, 90, 90, 90, 10, 69.5],
            ['June', 98, 90, 90, 90, 10, 69.5],
            ],
      options: {
    title: 'Percent Auto-Filled Fields',
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