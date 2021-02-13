<template>
  <div>
    <h1>home page</h1>
     <ion-button @click="tabs" color="primary">Tabs</ion-button>
     <ion-button @click="tabs2" color="secondary">New Tabs</ion-button>
     <!-- <ion-router>
      <ion-route-redirect from="/" to="/tab/tab1"></ion-route-redirect>
      <ion-route-redirect from="/" to="/tab/tab3"></ion-route-redirect>
    </ion-router> -->
  </div>
</template>
<script>
export default {
    methods:{
        tabs(){
          this.$router.push({ path: '/tabs/tab1' })
        },
        tabs2(){
            
        }
    }
}
</script>