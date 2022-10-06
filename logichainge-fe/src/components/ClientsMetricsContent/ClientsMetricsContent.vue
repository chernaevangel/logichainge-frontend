<template>
    <div id="client-metrics-content-wrapper">
        <div id="client-metrics-content-switcher">
            <div id="platform-metrics-content-switcher-MMC"
            v-on:click="component = 'MMC-Component'"
            >
                Management Metrics
            </div>
            <div id="platform-metrics-content-switcher-SMC"
            v-on:click="component = 'SMC-Component'"
            >
                Shippments Metrics
            </div>
        </div>

        <keep-alive>
            <component v-bind:is="component"></component>
        </keep-alive>
        
         <!-- <ManagementMetricsContent/>
         <ShipmentsMetricsContent/> -->
             
    </div>
</template>


<script>
import ManagementMetricsContent from "./ManagementMetricsContent/ManagementMetricsContent.vue";
import ShipmentsMetricsContent from "./ShipmentsMetricsContent/ShipmentsMetricsContent.vue";


export default {
    data() {
        return{
            component: "MMC-Component"
        };
        
    },
    // Pulls posts when the component is created.
    created() {
        
    },
    components : { 
         'MMC-Component':ManagementMetricsContent,
         'SMC-Component':ShipmentsMetricsContent
         }
};

</script>


<style scoped>
    #client-metrics-content-wrapper{
        height: 100%;
        width: 100%;
        display: flex;
        flex-direction: column;
    }

    #client-metrics-content-switcher{
        height: 12%;
        width: 100%;
        display: flex;
        background-color: rgb(199, 194, 194);
    }


    #platform-metrics-content-switcher-MMC{
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

    #platform-metrics-content-switcher-MMC:hover{
        opacity: 0.8;
    }
    #platform-metrics-content-switcher-SMC{
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

    #platform-metrics-content-switcher-SMC:hover{
        opacity: 0.8;
    }


</style>