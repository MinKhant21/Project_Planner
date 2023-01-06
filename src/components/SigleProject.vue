<template>
   <div class="project" >
        <div class="flexing">
            <div>
                <h3 @click="ShowDetail=!ShowDetail">{{ project.title }}</h3>
                <p v-if="ShowDetail"> {{ project.detail }}</p>
            </div>
            <div>
                <span class="material-symbols-outlined">
                delete
                </span>
                <span class="material-symbols-outlined">
                edit
                </span>
                <span class="material-symbols-outlined">
                done
                </span>
            </div>
        </div>
        
        
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
    .flexing{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    h3{
        color:indigo;
        cursor: pointer;
    }
    span{
        cursor: pointer;
    }
    span:hover{
        background-color: rgb(188, 148, 156);
    }
</style>