<template>
    <div id="platform-metrics-content-wrapper">
        <div id="platform-metrics-content-switcher">
            switcher
        </div>
        
        <OperationalMetricsContent/>    
             
    </div>
</template>


<script>
import OperationalMetricsContent from "./OperationalMetricsContent/OperationalMetricsContent.vue";


export default {
    data() {
        
    },
    // Pulls posts when the component is created.
    created() {
        
    },
    components : { OperationalMetricsContent }
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
        background-color: rgb(199, 194, 194);
    }

   

</style>