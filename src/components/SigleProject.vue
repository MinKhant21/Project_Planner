<template>
   <div class="project" :class="{complete:project.complete,falsecomplete:project.complete == false}">
        <div class="flexing">
            <div>
                <h3 @click="ShowDetail=!ShowDetail">{{ project.title }}</h3>
                <!-- <p> {{ project.complete }}</p> -->
                <p v-if="ShowDetail"> {{ project.detail }}</p>
            </div>
            <div>
                <span class="material-symbols-outlined" @click="deleteProject">
                delete
                </span>
                <span class="material-symbols-outlined">
                edit
                </span>
                <span class="material-symbols-outlined" @click="doneProject">
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
            ShowDetail:false,
            complete:null,
        }
    },
    methods:{
        deleteProject()
        {
            let api = 'http://localhost:3000/projects/';
            fetch(api+'/'+this.project.id,{method:'DELETE'})
            .then((id)=>{
                return this.$emit('delete',this.project.id)
            })
            .catch((error)=>{
                console.log(error)
            })
        },
        doneProject()
        {
            let api = 'http://localhost:3000/projects'
            fetch(api+'/'+this.project.id,{
                method:'PATCH',
                headers:{
                    "Content-type" : 'application/json'
                },
                body:JSON.stringify({
                    complete :this.complete=!this.project.complete
                }),
            })
            .then(()=>{
                this.$emit("complete",this.project.id)
            })
            .catch((err)=>{
                console.log(err)
            })
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
    .complete{
        border-left:6px solid greenyellow;
    }
    .falsecomplete{
        border-left:6px solid red;
    }
</style>