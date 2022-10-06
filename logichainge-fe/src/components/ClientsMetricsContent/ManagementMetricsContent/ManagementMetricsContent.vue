<template>
    <div id="client-metrics-initial-content">
        <div id="client-metrics-initial-content-row">
                    <div id="client-metrics-initial-content-box-wrapper">
                        <div id="client-metrics-initial-content-box">
                            <div id="client-metrics-initial-content-box-title">
                                Sales Revenue
                            </div>
                            <div id="client-metrics-initial-content-box-content">
    
                                <div v-for="post of posts">
                                    <p>{{post.managementMetics.salesRevenue}}</p>
                                </div>
                          
                            </div>
                        </div>
                    </div>
                    <div id="client-metrics-initial-content-box-wrapper">
                        <div id="client-metrics-initial-content-box">
                            <div id="client-metrics-initial-content-box-title">
                                Gross Profit Margin
                            </div>
                            <div id="client-metrics-initial-content-box-content">
    
                                <div v-for="post of posts">
                                    <p>{{post.managementMetics.grossProfitMargin}}</p>
                                </div>
                          
                            </div>
                        </div>
                    </div>

        </div>
                <div id="client-metrics-initial-content-row">
                    <div id="client-metrics-initial-content-box-wrapper">
                        <div id="client-metrics-initial-content-box">
                            <div id="client-metrics-initial-content-box-title">
                                Retention Rate
                            </div>
                            <div id="client-metrics-initial-content-box-content">
    
                                <div v-for="post of posts">
                                    <p>{{post.managementMetics.retentionRate}}</p>
                                </div>
                          
                            </div>
                        </div>
                    </div>
                    <div id="client-metrics-initial-content-box-wrapper">
                        <div id="client-metrics-initial-content-box">
                            <div id="client-metrics-initial-content-box-title">
                                Carriers Satisfaction Rate
                            </div>
                            <div id="client-metrics-initial-content-box-content">
    
                                <div v-for="post of posts">
                                    <p>{{post.managementMetics.carriersSatisfactionRate}}</p>
                                </div>
                          
                            </div>
                        </div>
                    </div>

                </div>

    </div>

</template>



<script>

import axios from "axios";

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
   }
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
        background-color: rgb(201, 191, 191);
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