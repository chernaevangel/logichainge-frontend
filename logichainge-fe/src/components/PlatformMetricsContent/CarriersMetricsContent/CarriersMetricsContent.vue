<template>
    <div id="client-metrics-secondary-content">
        <div id="client-metrics-secondary-content-row">
                    <div id="client-metrics-secondary-content-box-wrapper">
                        <keep-alive>
                            <ActiveCarriersContentBox
                            name="Active Carriers"
                            />
                        </keep-alive>
                    </div>
                    <div id="client-metrics-secondary-content-box-wrapper">
                        <keep-alive>
                            <TopTenCarriersContentBox
                            name="Top 10 Carriers"/>
                        </keep-alive>
                    </div>

        </div>
                <div id="client-metrics-secondary-content-row">
                    <div id="client-metrics-secondary-content-box-wrapper">
                        <div id="client-metrics-secondary-content-box">
                            <div id="client-metrics-secondary-content-box-title">
                                Retention Rate
                            </div>
                            <div id="client-metrics-secondary-content-box-content">
    
                                <div v-for="post of posts">
                                    <p>{{post.carriersMetrics.retentionRate}}</p>
                                </div>
                          
                            </div>
                        </div>
                    </div>
                    <div id="client-metrics-secondary-content-box-wrapper">
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
    components: { ActiveCarriersContentBox, TopTenCarriersContentBox, CarriersSatisfactionRateContentBox }
};

</script>

<style scoped>
    #client-metrics-secondary-content{
        height: 88%;
        width: 100%;
        display: flex;
        flex-direction: column;

    }

    #client-metrics-secondary-content-row{
        height: 50%;
        width: 100%;
        display: flex;
       
    }

    #client-metrics-secondary-content-box-wrapper{
        height: 100%;
        width: 50%;
        display: flex;
        justify-content: center;
        align-items: center;
   
    }

    #client-metrics-secondary-content-box{
        height: 90%;
        width: 85%;
        border-radius: 10px;
        display: flex;
        flex-direction: column;
        background-color: rgb(201, 191, 191);
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
        color: grey;
    }

    #client-metrics-secondary-content-box-content{
        height: 85%;
        width: 100%;
    }
</style>