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
  
  <h1>My projects</h1>

  <div class="container mt-5">
    <div class="row">
        
        <div class="col-md-4 mb-4" v-for="(elem,index) in projects" :key="index">
            <div class="card">

                <img :src="`${urlBase}/storage/${elem.image}`" class="card-img-top" alt="">

                <div class="card-body">

                    <h2 class="card-title fw-bold">{{ elem.title }}</h2>

                    <!-- {{-- <p class="card-text">{{ $project->languages }}</p> --}} -->

                    <!-- {{-- Mostra i linguaggi selezionati --}} -->
                    <div>
                        <p>Programming languages:</p>
                        <!-- <div class="card-text d-flex gap-2 fw-normal">
                            @foreach ($project->technologies as $technology)
                                <p>{{ $technology->name }}</p>
                            @endforeach
                        </div> -->
                    </div>

                    <div class="d-flex gap-3">
                        <p class="">Project type:</p>
        
                        <!-- @isset($project->type)
                        <p class="fw-normal">{{ $project->type->name }}</p>
                        @endisset -->
                    </div>

                    <a href="" class="btn btn-primary">View Details</a>
                    <!-- <a href="{{ route('projects.show', $project->id) }}" class="btn btn-primary">View Details</a> -->

                </div>
            </div>
        </div>
    </div>
  </div>


</template>

<style lang="scss">

@use "./style/main.scss" as *;



</style>