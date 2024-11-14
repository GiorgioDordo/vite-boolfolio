<script>
//bisogna importare axios per poter fare la chiamata ajax
// AJAX = Asyncronous JavaScript And Xml
import axios from 'axios';

export default {
  data() {
    return{

    }
  },
  methods: {
    getProjects() {
      axios.get('http://127.0.0.1:8000/api/projects')
      .then(function(response) {
        console.log(response.data.results);
      })
      .catch(function(error){
        console.log(error);
      }) 
      this.postList = response.data.results;
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
        <div class="col-3 m-3 p-3 card">
            <div class="card-body">
                <p><strong></strong></p>
                <p></p>
                <p></p>
            </div>
        </div>
    </div>
</main>
</template>

<style scoped>
</style>
