<script>
// import NameComp from "./components/NameComp.vue"
import axios from "axios";

export default{

  data() {
    return {

      projects: [],
      urlBase: 'http://127.0.0.1:8000'

    }
  },


  mounted() {

    this.getProjects();

  },



  methods: {

    getProjects(){
      axios.get(`${this.urlBase}/api/projects`)
      .then( res => {
        console.log(res.data);
        this.projects = res.data.projects
      })
    }


  }
}






</script>

<template>
  

  
</template>

<style lang="scss">

@use "./style/main.scss" as *;



</style>