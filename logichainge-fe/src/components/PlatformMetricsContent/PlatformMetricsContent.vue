<template>
    <div id="platform-metrics-content-wrapper">
        <div id="platform-metrics-content-switcher">
             <div id="platform-metrics-content-switcher-OMC"
             v-on:click="component = 'OMC-Component'"
             >
                  Operational Metrics
             </div>
             <div id="platform-metrics-content-switcher-CMC"
             v-on:click="component = 'CMC-Component'"
             >
                Carriers Metrics
             </div>
        </div>

        <keep-alive>
            <component v-bind:is="component"></component>
        </keep-alive>
        
        <!-- <OperationalMetricsContent/>  
        <CarriersMetricsContent/> -->
             
    </div>
</template>


<script>
import OperationalMetricsContent from "./OperationalMetricsContent/OperationalMetricsContent.vue";
import CarriersMetricsContent from "./CarriersMetricsContent/CarriersMetricsContent.vue";


export default {
    data() {
        return {
            component: 'OMC-Component'
        };
    },
    // Pulls posts when the component is created.
    created() {
        
    },
    components : {
        "OMC-Component" : OperationalMetricsContent, 
        'CMC-Component' : CarriersMetricsContent }
};


</script>


<style scoped>

    #platform-metrics-content-wrapper{
        height: 100%;
        width: 100%;
        display: flex;
        flex-direction: column;
    }

    #platform-metrics-content-switcher{
        height: 12%;
        width: 100%;
        display: flex;
        background-color: rgb(199, 194, 194);
    }

    #platform-metrics-content-switcher-OMC{
        height: 100%;
        width: 15%;
        margin-left: 2.5%;
        cursor: pointer;
        display: flex;
        font-size: 0.96 vw;
        font-weight: 600;
        text-transform: uppercase;
        justify-content: center;
        align-items: center;
    }

    #platform-metrics-content-switcher-OMC:hover{
        opacity: 0.8;
    }
    #platform-metrics-content-switcher-CMC{
        height: 100%;
        width: 20%;
        cursor: pointer;
        display: flex;
        font-size: 0.96 vw;
        font-weight: 600;
        text-transform: uppercase;
        justify-content: flex-start;
        align-items: center;
    }

    #platform-metrics-content-switcher-CMC:hover{
        opacity: 0.8;
    }
   

</style>