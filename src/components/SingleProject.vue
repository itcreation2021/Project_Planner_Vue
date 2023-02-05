<template>
<div class="project" :class="{complete:project.complete}">
    <div class="flexing">
        <div>
            <h4 class="text-primary" @click="showDetail = !showDetail"> {{ project.title }} </h4>
        </div>
        <div class="text-primary">
            <span class="material-icons" @click="deleteProject">
                delete
            </span>
            <span class="material-icons">
                edit
            </span>
            <span class="material-icons" @click="completeProject">
                done
            </span>
        </div>
    </div>
        <p> {{ project.complete }} </p>
    <p class="text-black-50" v-if="showDetail"> {{ project.detail }} </p>
</div>
</template>

<script>
export default {
    data() {
        return {
            showDetail: false,
            api: "http://localhost:3000/projects/"

        }
    },
    methods: {
        deleteProject() {
            let deleteRoute = this.api + this.project.id;
            fetch(deleteRoute, { method: "DELETE" })
            this.$emit("delete",this.project.id)
        },
        completeProject() {
            let updateCompleteRoute = this.api + this.project.id;
            fetch(updateCompleteRoute, {
                method: "PATCH",
                headers: {
                    "Content-Type":"application/json"
                },
                body:JSON.stringify(
                    {
                        complete:!this.project.complete
                    }
                )
            })
            .then(() => {
                this.$emit("complete",this.project.id)
            })
            .catch((err) => {
                console.log(err)
            })
        }
    },
    props: ['project']
}
</script>

<style>
.project{
    padding: 20px;
    margin: 10px;
    background: #f0f0f0;
    border-radius: 8px;
    border-left: 6px solid crimson;
}
h4{
    cursor: pointer;
}
.flexing{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
span{
    margin-left: 20px;
}
span:hover{
    color:#777777;
    cursor: pointer;
}
.complete{
    border-left-color: green;
}
</style>