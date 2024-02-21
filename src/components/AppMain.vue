<template lang="">
  
   <main class="container-fluid">
        <section class="row">
            <div>
                <h1>Our Projects:</h1>
            </div>

            <ul>
                <li v-for="project in projects" :key="project.id">

                    {{ project.title }}

                </li>
            </ul>

        </section>
    </main>

</template>
<script>

import axios from 'axios';
 
export default {
    name:'AppMain',

    data(){
      return{
        projects: [],
      }
        
    },

    methods:{
        getProjects(){
            axios.get('http://127.0.0.1:8000/api/projects', {
                params: {
                }
            })
            .then((response) => {
                console.log(response.data.results);
                this.projects = response.data.results;
            })
            .catch(function (error) {
                console.warn(error);
            })
            .finally(function () {
                // always executed
            });
        }
    },

    created(){
        this.getProjects();
    }
}
</script>
<style lang="">
    
</style>