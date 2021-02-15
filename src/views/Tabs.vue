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
    tabs: [],
    childTabs: [
      { tab: "tab1", icon: ellipse, route: "/tabs/tab1", label: "Home" },
      { tab: "tab3", icon: triangle, route: "/tabs/tab3", label: "Tab 3" },
      { tab: "tab4", icon: ellipse, route: "/tabs/tab4", label: "Tab 4" },
      { tab: "tab5", icon: square, route: "/tabs/tab5", label: "Tab 5" },
      { tab: "tab6", icon: triangle, route: "/tabs/tab6", label: "Tab 6" },
    ],
    masterTabs: [
      { tab: "tab1", icon: ellipse, route: "/tabs/tab1", label: "Tab 1" },
      { tab: "tab2", icon: square, route: "/tabs/tab2", label: "Tab 2" },
      { tab: "tab3", icon: triangle, route: "/tabs/tab3", label: "Tab 3" },
    ],
  }),
  watch: {
    $route(to) {
      //console.log("new route", to);

      if (
        this.childTabs
          .filter((x) => x.tab != "tab1")
          .map((x) => x.route)
          .includes(to.fullPath)
      ) {
        if (
          this.tabs.map((x) => x.route).join() !==
          this.childTabs.map((x) => x.route).join()
        ) {
          this.tabs = [];
          setTimeout(() => {
            console.log("check1", this.childTabs.map((x) => x.route).join());
            console.log("check2", this.tabs.map((x) => x.route).join());

            this.tabs = this.childTabs;
          }, 50);
        }
      } else if(this.masterTabs.map(x=>x.route).includes(to.fullPath)) {        
          this.tabs = [];
          setTimeout(() => {
            this.tabs = this.masterTabs;
          }, 50);        
      }else {
        this.tab = [];
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
    } else this.tabs = this.masterTabs;
  },
  components: {
    TabCollection,
    //,IonLabel, IonTabs, IonTabBar, IonTabButton, IonIcon, IonPageTabCollection
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