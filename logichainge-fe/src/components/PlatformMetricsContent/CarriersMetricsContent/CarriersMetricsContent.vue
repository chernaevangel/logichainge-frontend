<template>
    <div id="platform-metrics-secondary-content">
        <div id="platform-metrics-secondary-content-row">
                    <div id="platform-metrics-secondary-content-box-wrapper">
                        <keep-alive>
                            <ActiveCarriersContentBox
                            name="Active Carriers"
                            />
                        </keep-alive>
                    </div>
                    <div id="platform-metrics-secondary-content-box-wrapper">
                        <keep-alive>
                            <TopTenCarriersContentBox
                            name="Top 10 Carriers"/>
                        </keep-alive>
                    </div>

        </div>
                <div id="platform-metrics-secondary-content-row">
                    <div id="platform-metrics-secondary-content-box-wrapper">
                        <div id="platform-metrics-secondary-content-box">
                            
                           
    
                               <keep-alive>
                                <RetentionRateContentBox/>
                               </keep-alive>
                          
                           
                        </div>
                    </div>
                    <div id="platform-metrics-secondary-content-box-wrapper">
                        <keep-alive>
                            <CarriersSatisfactionRateContentBox
                            name="Average carriers satsifaction rate"
                            />
                        </keep-alive>
                    </div>

                </div>

    </div>

</template>



<script>

import axios from "axios";
import ActiveCarriersContentBox from "./CarriersMetricsContentBox/ActiveCarriersContentBox.vue";
import TopTenCarriersContentBox from "./CarriersMetricsContentBox/TopTenCarriersContentBox.vue";
import CarriersSatisfactionRateContentBox from "./CarriersMetricsContentBox/CarriersSatisfactionRateContentBox.vue";
import RetentionRateContentBox from "./CarriersMetricsContentBox/RetentionRateContentBox.vue";

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
            .get(`http://127.0.0.1:8000/platformMetrics`)
            .then((response) => {
            // JSON responses are automatically parsed.
            this.posts = response.data;
            // console.log(response.data)
        })
            .catch((e) => {
            this.errors.push(e);
        });
    },
    components: { ActiveCarriersContentBox, TopTenCarriersContentBox, CarriersSatisfactionRateContentBox, RetentionRateContentBox }
};

</script>

<style scoped>
    #platform-metrics-secondary-content{
        height: 88%;
        width: 100%;
        display: flex;
        flex-direction: column;

    }

    #platform-metrics-secondary-content-row{
        height: 50%;
        width: 100%;
        display: flex;

    }

    #platform-metrics-secondary-content-box-wrapper{
        height: 100%;
        width: 50%;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    #platform-metrics-secondary-content-box{
        height: 90%;
        width: 85%;
        border-radius: 10px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

   

    #platform-metrics-secondary-content-box-content{
        height: 85%;
        width: 100%;
    }
</style>