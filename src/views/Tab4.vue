<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tab 4</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab 4</ion-title>
        </ion-toolbar>
      </ion-header>
      <!-- <ExploreContainer name="Tab 1 page" /> -->
      <TabGeneric name="tab 4" />
    </ion-content>
  </ion-page>
</template>

<script>
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';
// import ExploreContainer from '@/components/ExploreContainer.vue';
import TabGeneric from '@/components/TabGeneric.vue';

export default  {
  name: 'Tab1',
  components: { 
    // ExploreContainer, 
    TabGeneric, 
    IonHeader, IonToolbar, IonTitle, IonContent, IonPage }
}
</script>