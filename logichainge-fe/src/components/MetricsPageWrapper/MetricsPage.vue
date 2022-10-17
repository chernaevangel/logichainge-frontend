<template>
    <div id="initial-metrics-page-wrapper">
            <div id="navigation-wrapper">

            </div>
            <div id="metrics-contentload-wrapper">
                <div id="metrics-content-title-wrapper">
                     <div id="metrics-content-title-box">
                        Report dashboard
                     </div>
                </div>
                <div id="metrics-content-category-navigation-wrapper">
                    <div id="navigation-initial-wrapper">
                        <div id="LG-metrics-box-wrapper"
                        v-on:click="component = 'content-pm'"
                      
                        >
                                LC Platform Metrics
                        </div>
                        <div id="C-metrics-box-wrapper"
                        v-on:click="component = 'content-cl'"
                        >
                               Client Metrics
                        </div>

                    </div>
                </div>
        
                <div id="metrics-content-wrapper">
                            <!-- <ul v-if="posts && posts.length">
                                <li v-for="post of posts">
                                    <p>{{post.revenue}}</p>
                                
                                </li>
                            </ul> -->
                   <!-- <PlatformMetricsContent/> -->
                   <!-- <ClientsMetricsContent/> -->
                   <keep-alive>
                   <component v-bind:is="component"></component>
                   </keep-alive>
                            <!-- <ul v-if="errors && errors.length">
                                <li v-for="error of errors">
                                    {{error.message}}
                                </li>
                            </ul> -->
                </div>

                       

            </div>
        
    </div>
  </template>
  
  <script>
    import PlatformMetricsContent from "../PlatformMetricsContent/PlatformMetricsContent.vue";
    import ClientsMetricsContent from "../ClientsMetricsContent/ClientsMetricsContent.vue";

    export default {

    data() {
        return {
            component: 'content-pm'
        };
    },
    // Pulls posts when the component is created.
    created() {
        // axios
        //     .get(`http://127.0.0.1:8000/managementMetrics`)
        //     .then((response) => {
        //     // JSON responses are automatically parsed.
        //     this.posts = response.data;
        //     // console.log(response.data)
        // })
        //     .catch((e) => {
        //     this.errors.push(e);
        // });
    },
    components: { 
        'content-pm' : PlatformMetricsContent,
        'content-cl' : ClientsMetricsContent
    }
};

    components : {
        PlatformMetricsContent
    }

  </script>
  
  <style scoped>

    #initial-metrics-page-wrapper{
        height: 100%;
        width: 100%;
        display: flex;
    }

    #navigation-wrapper{
        height: 100%;
        width: 5%;
        display: flex;
        background-color: #1e2b50 !important;
    }

    #navigation-initial-wrapper{
        height: 100%;
        width: 25%;
        margin-left: 2%;
        display: flex;
        flex-direction: row;
    }

    #LG-metrics-box-wrapper{
         height:  100%;
         width: 50%;
         align-items: center;
        cursor: pointer;
        display: flex;
        font-size: .875rem;
        font-weight: 600;
        justify-content: flex-start;
        letter-spacing: .04em;
        font-weight: 600;
        line-height: normal;
        min-width: 90px;
        max-width: 360px;
        outline: none;
        opacity: 0.6;
        position: relative;
        text-align: center;
        text-decoration: none;
        text-transform: uppercase;
        font-family: Roboto,sans-serif;
        
    }

    #LG-metrics-box-wrapper:hover{
        opacity: 0.8;
    }

    #C-metrics-box-wrapper{
        height:  100%;
        width: 50%;
        align-items: center;
       cursor: pointer;
       display: flex;
       font-size: .875rem;
       font-weight: 600;
       justify-content: center;
       letter-spacing: .04em;
       line-height: normal;
       min-width: 90px;
       max-width: 360px;
       outline: none;
       opacity: 0.6;
       position: relative;
       text-align: center;
       text-decoration: none;
       text-transform: uppercase;
       font-family: Roboto,sans-serif;
      
   }

   #C-metrics-box-wrapper:hover{
    opacity: 0.8;
   }

    
    #metrics-contentload-wrapper{
        height: 100%;
        width: 95%;
        display: flex;
        flex-direction: column;
    }

    #metrics-content-title-wrapper{
        height: 10%;
        width: 100%;
        display: flex;
    }


    #metrics-content-title-box{
        height: 100%;
        width: 25%;
        margin-left: 2%;
        display: flex;
        font-weight: 500;
        font-size: 1rem;
        text-transform: uppercase;
        font-family: Roboto,sans-serif;
        line-height: 1.5;
        letter-spacing: .0666666667em;
        color: grey;
        justify-content: flex-start;
        align-items: center;
    }

    #metrics-content-category-navigation-wrapper{
        height: 10%;
        width: 100%;
        display: flex;
    }

    #metrics-content-wrapper{
        height: 100%;
        width: 100%;
        display: flex;
        background-color: rgb(231, 231, 231);
        box-shadow: rgba(0, 0, 0, 0.05) 0px 6px 24px 0px, rgba(0, 0, 0, 0.08) 0px 0px 0px 1px;
    }

    
  
  
  </style>