<script>
//bisogna importare axios per poter fare la chiamata ajax
// AJAX = Asyncronous JavaScript And Xml
import axios from 'axios';

export default {
  data() {
    return{
      projectList: [],
    }
  },
  methods: {
    getProjects() {
      axios.get('http://127.0.0.1:8000/api/projects')
      .then((response) => {
        console.log(response.data.results);
        this.projectList = response.data.results;
      })
      .catch(function(error){
        console.log(error);
      }) 
    }
  },
  created() {
    this.getProjects();
  }
  
}
</script>

<template>
<main class="container">
    <div class="row d-flex justify-content-center">
        <div><h1 class="text-center">PROJECTS</h1></div>
        <div class="col-3 m-3 p-3 card" v-for="singleProject in projectList" :key="singleProject.id">
            <div class="card-body">
                <p><strong>{{ singleProject.name }}</strong></p>
                <p>{{ singleProject.short_description }}</p>
                <p>{{ singleProject.type.name }}</p>
            </div>
        </div>
    </div>
</main>
</template>

<style scoped>
</style>
