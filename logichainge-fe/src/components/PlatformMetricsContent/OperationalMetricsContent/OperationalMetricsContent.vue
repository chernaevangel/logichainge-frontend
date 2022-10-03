<template>
    <div id="platform-metrics-initial-content">
        <div id="platform-metrics-initial-content-row">
           <div id="platform-metrics-initial-content-box-wrapper">
                <div id="platform-metrics-initial-content-box">
                    <div id="platform-metrics-initial-content-box-title">
                        Utilization Rate
                    </div>
                    <div id="platform-metrics-initial-content-box-content">
                         
                                <div v-for="post of posts">
                                    <p>{{post.operationalMetrics.utilizationRate}}</p>
                                </div>
                          
                    </div>
                </div>
           
           </div>
           <div id="platform-metrics-initial-content-box-wrapper">
           
                <div id="platform-metrics-initial-content-box">
                    <div id="platform-metrics-initial-content-box-title">
                        Delivery times
                    </div>
                    <div id="platform-metrics-initial-content-box-content">
                        <div v-for="post of posts">
                            <p>{{post.operationalMetrics.deliveryTimes}}</p>
                        </div>

                    </div>
                </div>
            </div>
            <div id="platform-metrics-initial-content-box-wrapper">
                <div id="platform-metrics-initial-content-box">
                    <div id="platform-metrics-initial-content-box-title">
                         Carrying costs
                    </div>
                    <div id="platform-metrics-initial-content-box-content">
                        <div v-for="post of posts">
                            <p>{{post.operationalMetrics.carryingCosts}}</p>
                        </div>

                    </div>
                </div>
            </div>
        </div>
        <div id="platform-metrics-initial-content-row">
            <div id="platform-metrics-initial-content-box-wrapper">
                <div id="platform-metrics-initial-content-box">
                    <div id="platform-metrics-initial-content-box-title">
                        Average Time for Order Completion
                    </div>
                    <div id="platform-metrics-initial-content-box-content">
                        <div v-for="post of posts">
                            <p>{{post.operationalMetrics.avgTimeOrderCompletion}}</p>
                        </div>

                    </div>

                </div>
            </div>
            <div id="platform-metrics-initial-content-box-wrapper">
                <div id="platform-metrics-initial-content-box">
                    <div id="platform-metrics-initial-content-box-title">
                        Percent Correct Auto-Filled Fields
                    </div>
                    <div id="platform-metrics-initial-content-box-content">
                        <div v-for="post of posts">
                            <p>{{post.operationalMetrics.percentCorrectAFFields}}</p>
                        </div>

                    </div>

                </div>
             </div>
             <div id="platform-metrics-initial-content-box-wrapper">
                <div id="platform-metrics-initial-content-box">
                    <div id="platform-metrics-initial-content-box-title">
                        Amount Critical Issues
                    </div>
                    <div id="platform-metrics-initial-content-box-content">
                        <div v-for="post of posts">
                            <p>{{post.operationalMetrics.numberCriticalIssues}}</p>
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
            .get(`http://127.0.0.1:8000/platformMetrics`)
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
    #platform-metrics-initial-content{
        height: 88%;
        width: 100%;
        display: flex;
        flex-direction: column;
    }

    #platform-metrics-initial-content-row{
        height: 50%;
        width: 100%;
        display: flex;
    }

    #platform-metrics-initial-content-box-wrapper{
        height: 100%;
        width: 33.33%;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    #platform-metrics-initial-content-box{
        height: 90%;
        width: 90%;
        border-radius: 10px;
        display: flex;
        flex-direction: column;
        background-color: rgb(201, 191, 191);
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
       color: grey;
    }

    #platform-metrics-initial-content-box-content{
        height: 85%;
        width: 100%;
    }

</style>