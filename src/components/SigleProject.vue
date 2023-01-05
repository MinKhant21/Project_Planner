<template>
   <div class="project" @click="ShowDetail=!ShowDetail">
        <h3>{{ project.title }}</h3>
        <p v-if="ShowDetail"> {{ project.detail }}</p>
   </div>
</template>

<script>
export default {
    props:['project'],
    data(){
        return{
            ShowDetail:false
        }
    }
}
</script>

<style>
    .project{
        background-color: #f2f2f2;
        padding: 10px;
        margin: 10px;
    }
    h3{
        color:indigo;
    }
</style>