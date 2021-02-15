<template>
  <ion-page>
    <ion-tabs>
      <ion-tab-bar slot="bottom">
        <ion-tab-button v-for="tab in tabs" :key="tab.tab" :tab="tab.tab" :href="tab.route">
          <ion-icon :icon="tab.icon" />
          <ion-label>{{tab.label}}</ion-label>
        </ion-tab-button>

        <!-- <TabGeneric name="Generic Component" /> -->

      </ion-tab-bar>
    </ion-tabs>
  </ion-page>
</template>

<script>
import { IonTabBar, IonTabButton, IonTabs, IonLabel, IonIcon, IonPage } from '@ionic/vue';
import { ellipse, square, triangle } from 'ionicons/icons';

export default {
  name: 'Tabs',
  components: { IonLabel, IonTabs, IonTabBar, IonTabButton, IonIcon, IonPage },
  props:{tabs:{default:()=>[]}},
  setup() {
    return {
      ellipse, 
      square, 
      triangle,
    }
  }
}
</script>