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
             <div id="platform-metrics-content-filter-wrapper">
                <div id="platform-metrics-content-filter-divider">

                </div>
                <div id="platform-metrics-content-filter-sorter-wrapper">
                    <div id="platform-metrics-content-filter">
                        filter
                    </div>
                    <div id="platform-metrics-content-sorter">
                        sorter
                    </div>
                </div>
                <div id="platform-metrics-content-export-wrapper">
                        <div id="platform-metrics-content-export-button">
                            export
                        </div>
                </div>

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
   
    #platform-metrics-content-filter-wrapper{
        height: 100%;
        width: 63%;
        display: flex;
 
    }

    #platform-metrics-content-filter-divider{
        height: 100%;
        width: 35%;
       
    }

    #platform-metrics-content-filter-sorter-wrapper{
        width: 45%;
        height: 100%;
        display: flex;
    }

    #platform-metrics-content-filter{
        width: 50%;
        height: 100%;
        display: flex;

        background-color: rgb(155, 152, 152);
    }

    #platform-metrics-content-sorter{
        width: 50%;
        height: 100%;
        display: flex;
        background-color: rgb(171, 173, 171);
    }

    #platform-metrics-content-export-wrapper{
        height: 100%;
        width: 20%;
        display: flex;
        justify-content: center;
        align-items: center;
      
    }

    #platform-metrics-content-export-button{
        height: 60%;
        width: 60%;
        border-radius: 14px;
        text-transform: uppercase;
        font-weight: 500;
        color: rgb(97, 96, 96);
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 0.8vw;
        box-shadow: rgba(83, 81, 81, 0.24) 0px 3px 8px;
        background-color: rgb(223, 215, 215);
        cursor: pointer;
    }

    #platform-metrics-content-export-button:hover{
        opacity: 0.7;
    }

</style>