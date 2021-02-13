<template>
  <ion-page>
    <tab-collection v-if="tabs.length" :tabs="tabs"></tab-collection>
  </ion-page>
</template>

<script>

//import { IonTabBar, IonTabButton, IonTabs, IonLabel, IonIcon, IonPage } from '@ionic/vue';
import { ellipse, square, triangle } from "ionicons/icons";
import TabCollection from "./tab-collection.vue";

export default {

  name: "Tabs",
  data: () => ({

    tabs: [
      // { path: "/", redirect: "/tabs/tab1" }
    ],

    childTabs: [  
      { tab: "tab3", icon: triangle, route: "/tabs/tab3", label: "Tab 3" },
      { tab: "tab4", icon: ellipse,  route: "/tabs/tab4", label: "Tab 4" },
      { tab: "tab5", icon: square,   route: "/tabs/tab5", label: "Tab 5" },
      { tab: "tab6", icon: triangle, route: "/tabs/tab6", label: "Tab 6" },
    ],
    
    masterTabs: [
      { tab: "tab1", icon: ellipse,  route: "/tabs/tab1", label: "Tab 1" },
      { tab: "tab2", icon: square,   route: "/tabs/tab2", label: "Tab 2" },
      { tab: "tab3", icon: triangle, route: "/tabs/tab3", label: "Tab 3" },
    ],
  }),

  // Which tab is the CLICKED tab?
  // I think it's "to"
  watch: {
    
    $route(to) {

      // console.log("new route", to);
      console.log('to', to);

      // Tabs
      console.log('this.masterTabs', this.masterTabs);
      console.log('this.childTabs',  this.childTabs);

      if (this.childTabs.map((x) => { 
        
        // console.log('this.childTabs.map.x.route', x.route);
        // console.log('to.fullPath', to.fullPath);
        
        return x.route 
        
        }).includes(to.fullPath)) {

          // Compare the main tabs with the child tabs
          if (this.tabs.map((x) => { 
            
            console.log('x.route', x.route);
            console.log('x.label', x.label);

            return x.route 
            
          }).join() !== this.childTabs.map((x) => x.route).join()) { 

            console.log('tabs',      this.tabs     .map((x) => x.route).join());
            console.log('childTabs', this.childTabs.map((x) => x.route).join());
          
            this.tabs = [];

            setTimeout(() => {

              console.log("check1", this.childTabs.map((x) => { 
                
                // console.log('x', x);              // Proxies for tabs
                // console.log('x.route', x.route);  // Isolate the tab route
                
                return x.route

              }).join());

              // console.log("check2", this.tabs.map((x) => x.route).join());
              // console.log('this.tabs: before', this.tabs);  // Empty array, meant for main tabs

              this.tabs = this.childTabs;

              // console.log('this.tabs: after', this.tabs);   // this.tabs filled with child tabs

            }, 50);
          }
        } 
        else { 
          this.tabs = this.masterTabs; 
        }
    },
  },
  mounted() {
    if (
      this.childTabs
        .map((x) => x.route)
        .includes(this.$router.currentRoute.fullPath)
    ) {
      this.tabs = this.childTabs;
    } 
    else { 

      // console.log('this.tabs', this.tabs);
      // console.log('this.masterTabs', this.masterTabs);

      this.tabs = this.masterTabs;
    }
  },
  components: {
    TabCollection,
    // , IonLabel, IonTabs, IonTabBar, IonTabButton, IonIcon, IonPageTabCollection
  },
  setup() {
    return {
      ellipse,
      square,
      triangle,
    };
  },
};
</script>
