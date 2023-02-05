<template>
  <h1 class="text-primary mt-5">Add Project</h1>
    <form @submit.prevent="addProject">
        <div class="mb-3">
            <label for="exampleFormControlInput1" class="form-label">Project Title</label>
            <input type="text" class="form-control" id="exampleFormControlInput1" v-model="title">
        </div>
        <div class="mb-3">
            <label for="exampleFormControlTextarea1" class="form-label">Project Detail</label>
            <textarea class="form-control" id="exampleFormControlTextarea1" rows="3" v-model="detail"></textarea>
        </div>
        <div class="text-center">
            <button class="btn btn-primary">Add Project</button>
        </div>
    </form>
</template>

<script>
export default {
    data() {
        return {
            title: "",
            detail:""
        }
    }, 
    methods: {
        addProject() {
            fetch("http://localhost:3000/projects/", {
                method: "POST",
                headers: {
                    "Content-Type": "application/json"
                },
                body: JSON.stringify(
                    {
                        title:this.title,
                        detail:this.detail,
                        complete:false
                    }
                )
            })
            .then(() => {
                this.$router.push("/")
            })
            .catch((err) => {
                console.log(err)
            })
        }
    }
}
</script>

<style>

</style>