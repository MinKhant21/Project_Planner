<template>
  <h1>Home</h1>
  <div v-for="project in projects" :key="project.id">
    <SigleProject :project="project" @delete="deleteformchild" @complete="completeProject"></SigleProject>
  </div>
</template>

<script>
import SigleProject from './SigleProject'
export default {
  components: { SigleProject },
    name:'Home',
    data(){
      return{
        projects : [],
      }
    },
    mounted(){
      fetch("http://localhost:3000/projects")
      .then((response)=>{
        return response.json();
      })
      .then((data)=>{
        this.projects = data
      })
      .catch(()=>{

      })
    },
    methods:{
      deleteformchild(id)
      {
        this.projects = this.projects.filter((project)=>{
          return project.id!=id
        })
      },
      completeProject(id)
      {
        let findProject = this.projects.find((id)=>{
          return findProject.complete =! findProject.complete
        })
      }

    }
}
</script>

<style>

</style>