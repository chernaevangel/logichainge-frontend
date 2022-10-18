<template>
    <div id="client-metrics-initial-content">
        <div id="client-metrics-initial-content-row">
                    <div id="client-metrics-initial-content-box-wrapper">
                        <keep-alive>
                            <RevenueMetricsContentBox
                            name="Sales Revenue"
                            />
                        </keep-alive>
                    </div>
                    <div id="client-metrics-initial-content-box-wrapper">
                       <keep-alive>
                         <GrossProfitMargingContentBox
                         name="Gross Profit Margin"
                         />
                       </keep-alive>
                    </div>

        </div>
                <div id="client-metrics-initial-content-row">
                    <div id="client-metrics-initial-content-box-wrapper">
                       
    
                               <keep-alive>
                                <RRContentBox/>
                               </keep-alive>
                          
                           
                    </div>
                    <div id="client-metrics-initial-content-box-wrapper">
                    
    
                                <keep-alive>
                                    <CSRContentBox/>
                                </keep-alive>
                          
                           
                    </div>

                </div>

    </div>

</template>



<script>

import axios from "axios";
import RevenueMetricsContentBox from "./ManagementMetricsContent/RevenueMetricsContentBox.vue";
import GrossProfitMargingContentBox from "./ManagementMetricsContent/GrossProfitMargingContentBox.vue";
import RRContentBox from "./ManagementMetricsContent/RRContentBox.vue";
import CSRContentBox from "./ManagementMetricsContent/CSRContentBox.vue";

export default {
    data() {
        return {
            posts: [],
            errors: [],
        };
    },
    // Pulls posts when the component is created.
    created() {
        axios
            .get(`http://127.0.0.1:8000/clientMetrics`)
            .then((response) => {
            // JSON responses are automatically parsed.
            this.posts = response.data;
            // console.log(response.data)
        })
            .catch((e) => {
            this.errors.push(e);
        });
    },
    components: { RevenueMetricsContentBox, GrossProfitMargingContentBox, RRContentBox, CSRContentBox }
};

</script>

<style scoped>
    #client-metrics-initial-content{
        height: 88%;
        width: 100%;
        display: flex;
        flex-direction: column;

    }

    #client-metrics-initial-content-row{
        height: 50%;
        width: 100%;
        display: flex;
       
    }

    #client-metrics-initial-content-box-wrapper{
        height: 100%;
        width: 50%;
        display: flex;
        justify-content: center;
        align-items: center;
   
    }

    #client-metrics-initial-content-box{
        height: 90%;
        width: 85%;
        border-radius: 10px;
        display: flex;
        flex-direction: column;
       justify-content: center;
       align-items: center;
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
    }
</style>