<template>
  <div id="container">
    <ion-button @click="tabs" color="primary">Tabs</ion-button>
    <strong>{{ name }}</strong>
    <p>TabGeneric
      <a target="_blank" 
          rel="noopener noreferrer" 
          href="https://ionicframework.com/docs/components">Generic Components
      </a>
    </p>
  </div>
</template>

<script>
export default {
  name: 'TabGeneric',
  props: {
    name: String
  },
  methods:{
    tabs(){
      this.$router.push({ path: '/tabs/tab1' })
    },
    tabs2(){
        
    }
  }

}
</script>

<style scoped>
#container {
  text-align: center;
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  color: #8c8c8c;
  margin: 0;
}

#container a {
  text-decoration: none;
}
</style>