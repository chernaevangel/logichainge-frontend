<template>
    <div id="platform-metrics-content-wrapper">
        <div id="platform-metrics-content-switcher">
            <div id="platform-metrics-content-switcher-wrapper">           
                <div id="platform-metrics-content-switcher-OMC"
                    v-on:click="component = 'OMC-Component'"
                    >
                        <div id="OMC-Component-title">
                            Operational Metrics
                        </div>
                        <div 
                        v-if="component==='OMC-Component'"
                        id="OMC-Component-indicator">

                        </div>
                        <div 
                        v-if="component==='CMC-Component'"
                        id="OMC-Component-hidden-indicator">

                        </div>
                    </div>
                    <div id="platform-metrics-content-switcher-CMC"
                    v-on:click="component = 'CMC-Component'"
                    >
                        <div id="CMC-Component-title">
                            Carriers Metrics
                        </div>
                        <div id="CMC-Component-indicator"
                        v-if="component==='CMC-Component'"
                        >

                        </div>
                        <div id="CMC-Component-hidden-indicator"
                        v-if="component==='OMC-Component'"
                        >

                        </div>
                    </div>
                </div>
             <div id="platform-metrics-content-filter-wrapper">
                <div id="platform-metrics-content-filter-divider">

                </div>
                <div id="platform-metrics-content-filter-sorter-wrapper">
                    <!-- <div id="platform-metrics-content-filter">
                        <select>
                            <option v-for="(item, key) in monthSorters"
                            :value="key">
                            {{item}}
                            </option>
                        </select>
                    </div> -->
                    <div id="platform-metrics-content-filter">

                    </div>
                    <div id="platform-metrics-content-sorter">
                        <select>
                            <option v-for="(item, key) in monthSorters"
                            :value="key">
                            {{item}}
                            </option>
                        </select>
                    </div>
                </div>
                <div id="platform-metrics-content-export-wrapper">
                        <div
                      
                        id="platform-metrics-content-export-button">
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
            component: 'OMC-Component',
            monthSorters: ['Last month', 'Last 3 months', 'Last 6 months', 'Last year', 'Last 2 years']
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
        
    }

    #platform-metrics-content-switcher-wrapper{
        height: 100%;
        width: 30%;
        display: flex;
        flex-direction: row;
    }

    #platform-metrics-content-switcher-OMC{
        height: 100%;
        width: 53%;
        margin-left: 2.5%;
        cursor: pointer;
        display: flex;
        flex-direction: column;
        font-size: 0.96 vw;
        font-weight: 600;
        text-transform: uppercase;
        justify-content: center;
        align-items: center;
       
    }

    #OMC-Component-title{
        height: 95%;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: flex-end;
       
    }

    #CMC-Component-title{
        height: 95%;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: flex-end;
       
    }

    #OMC-Component-indicator{
        height: 5%;
        width: 92%;
        border-radius: 10px;
        background-color: #1e2b50 ;
    }

    #OMC-Component-hidden-indicator{
        height: 5%;
        width: 92%;
        border-radius: 10px;
    }

    #CMC-Component-indicator{
        height: 5%;
        width: 92%;
        border-radius: 10px;
        background-color: #1e2b50 ;
    }

    #platform-metrics-content-switcher-OMC:hover{
        opacity: 0.8;
    }
    #platform-metrics-content-switcher-CMC{
        height: 100%;
        width: 47%;
        cursor: pointer;
        display: flex;
        font-size: 0.96 vw;
        font-weight: 600;
        text-transform: uppercase;
        justify-content: center;
        flex-direction: column;
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
        align-items: center;
        justify-content: center;
    }

    #platform-metrics-content-filter select{
        height: 50%;
        width: 78%;
        cursor: pointer;
        border: none;
        color: rgb(34, 33, 33);
        border-radius: 5px;
        font-size: 0.89vw;
        background-color: rgb(253, 251, 251);
        box-shadow: rgba(94, 93, 93, 0.24) 0px 3px 8px;
    }

    #platform-metrics-content-filter select option{
        color: rgb(0, 0, 0);
    }

    #platform-metrics-content-sorter{
        width: 50%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    #platform-metrics-content-sorter select{
        height: 50%;
        width: 78%;
        cursor: pointer;
        border: none;
        color: rgb(34, 33, 33);
        border-radius: 5px;
        font-size: 0.89vw;
        background-color: rgb(253, 251, 251);
        box-shadow: rgba(94, 93, 93, 0.24) 0px 3px 8px;
    }
    #platform-metrics-content-sorter select option{
        color: rgb(0, 0, 0);
    }

    #platform-metrics-content-export-wrapper{
        height: 100%;
        width: 20%;
        display: flex;
        justify-content: center;
        align-items: center;
      
    }

    #platform-metrics-content-export-button{
        height: 52%;
        width: 60%;
        border-radius: 6px;
        text-transform: uppercase;
        font-weight: 600;
        color: rgb(49, 48, 48);
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 0.8vw;
        background-color: rgb(253, 251, 251);
        box-shadow: rgba(94, 93, 93, 0.24) 0px 3px 8px;
        cursor: pointer;
    }

    #platform-metrics-content-export-button:hover{
        opacity: 0.8;
    }

</style>