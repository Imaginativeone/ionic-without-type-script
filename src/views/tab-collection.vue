<template>
  <ion-page>
    <!-- <ion-tabs #myTabs tabsPlacement="top" (ionChange)="onTabsChange($event)"> -->
    <!-- <ion-tabs (ionChange)="onTabsChange($event)"> -->
    <!-- ok let me give you a hint if you don’t need two-way databinding. In your template you can define a select html element as below

 <ion-select name="periodSelected" ionChange="onChange($event)" >
  <ion-option value="1">Ex1</ion-option>
 <ion-option value="2">Ex2</ion-option>
 </ion-select>
in your component.ts
onChange($event){
console.log($event.target.value);
}

if you do need two-way data binding, then you have to use ngModel.

 -->
    <ion-tabs>
      <ion-tab-bar slot="bottom">
        <ion-tab-button :ionChange=onTabsChange($event) v-for="tab in tabs" :key="tab.tab" :tab="tab.tab" :href="tab.route">
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
  props:{ tabs: { default: ()=>[] }},
  methods: {

    onTabsChange(event) {
      console.log('event', event);
    }

  },
  setup() {
    return {
      ellipse, 
      square, 
      triangle,
    }
  }
}
</script>