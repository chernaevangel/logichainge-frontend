<template>
    <div id="client-metrics-content-wrapper">
        <div id="client-metrics-content-switcher">
            <div id="client-metrics-content-switcher-wrapper">
                    <div id="platform-metrics-content-switcher-MMC"
                    v-on:click="component = 'MMC-Component'"
                    >
                        <div id="MMC-Component-title">
                            Management Metrics
                        </div>
                        <div id="MMC-Component-indicator"
                        v-if="component==='MMC-Component'"
                        >

                        </div>
                        <div id="MMC-Component-hidden-indicator"
                        v-if="component==='SMC-Component'"
                        >

                        </div>
                        <div id="SMC-Component-hidden-indicator"
                        v-if="component==='AMC-Component'"
                        >

                        </div>
                       
                    </div>
                    
                    <div id="platform-metrics-content-switcher-SMC"
                    v-on:click="component = 'SMC-Component'"
                    >   
                        <div id="SMC-Component-title">
                            Shippments Metrics
                        </div>
                        <div id="SMC-Component-indicator"
                        v-if="component==='SMC-Component'"
                        >

                        </div>
                        <div id="SMC-Component-hidden-indicator"
                        v-if="component==='MMC-Component'"
                        >

                        </div>
                        <div id="SMC-Component-hidden-indicator"
                        v-if="component==='AMC-Component'"
                        >

                        </div>
                       
                    </div>
                    
                    <div id="platform-metrics-content-switcher-AMC"
                    v-on:click="component = 'AMC-Component'"
                    >   
                        <div id="AMC-Component-title">
                            Advanced Metrics
                        </div>
                        <div id="AMC-Component-indicator"
                        v-if="component==='AMC-Component'"
                        >

                        </div>
                        <div id="AMC-Component-hidden-indicator"
                        v-if="component==='SMC-Component'"
                        >

                        </div>
                        <div id="AMC-Component-hidden-indicator"
                        v-if="component==='MMC-Component'"
                        >

                        </div>
                       
                    </div>
                    
              </div>
            <div id="platform-metrics-content-filter-wrapper">
                <div id="platform-metrics-content-filter-divider">

                </div>
                <div id="platform-metrics-content-filter-sorter-wrapper">
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
                        <div id="platform-metrics-content-export-button">
                            export
                        </div>
                </div>

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
import AdvancedMetricsContent from "./AdvancedMetricsContent/AdvancedMetricsContent.vue";

export default {
    data() {
        return{
            component: "MMC-Component",
            monthSorters: ['Last month', 'Last 3 months', 'Last 6 months', 'Last year', 'Last 2 years']
        };
        
    },
    // Pulls posts when the component is created.
    created() {
        
    },
    components : { 
         'MMC-Component':ManagementMetricsContent,
         'SMC-Component':ShipmentsMetricsContent,
         'AMC-Component':AdvancedMetricsContent
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
    }

    #client-metrics-content-switcher-wrapper{
        height: 100%;
        width: 45%;
        display: flex;
        flex-direction: row;
    }

    #platform-metrics-content-switcher-MMC{
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

    #MMC-Component-title{
        height: 95%;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: flex-end;
       
    }

    #SMC-Component-title{
        height: 95%;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: flex-end;
       
    }

    #MMC-Component-indicator{
        height: 5%;
        width: 92%;
        border-radius: 10px;
        background-color: #1e2b50 ;
    }

    #MMC-Component-hidden-indicator{
        height: 5%;
        width: 92%;
        border-radius: 10px;
    }



    #AMC-Component-title{
        height: 95%;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: flex-end;
       
    }

    #AMC-Component-title{
        height: 95%;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: flex-end;
       
    }

    #AMC-Component-indicator{
        height: 5%;
        width: 92%;
        border-radius: 10px;
        background-color: #1e2b50 ;
    }

    #AMC-Component-hidden-indicator{
        height: 5%;
        width: 92%;
        border-radius: 10px;
    }


    #SMC-Component-indicator{
        height: 5%;
        width: 92%;
        border-radius: 10px;
        background-color: #1e2b50 ;
    }

    #SMC-Component-hidden-indicator{
        height: 5%;
        width: 92%;
        border-radius: 10px;
    }


    #platform-metrics-content-switcher-MMC:hover{
        opacity: 0.8;
    }
    #platform-metrics-content-switcher-SMC{
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

    #platform-metrics-content-switcher-AMC{
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

    #platform-metrics-content-switcher-AMC:hover{
        opacity: 0.8;
    }

    #platform-metrics-content-switcher-SMC:hover{
        opacity: 0.8;
    }

    #platform-metrics-content-filter-wrapper{
        height: 100%;
        width: 63%;
        display: flex;
 
    }

    #platform-metrics-content-filter-divider{
        height: 100%;
        width: 20%;
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
        font-weight: 500;
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
        font-weight: 600;
        box-shadow: rgba(139, 138, 138, 0.24) 0px 3px 8px;
        background-color: rgb(253, 251, 251);
        cursor: pointer;
    }

    #platform-metrics-content-export-button:hover{
        opacity: 0.8;
    }

</style>