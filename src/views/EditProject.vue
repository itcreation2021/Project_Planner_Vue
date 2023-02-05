<template>
  <h1 class="text-primary">Edit Project </h1>

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
      <button class="btn btn-primary" @click="updateProject">Update Project</button>
    </div>
  </form>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return{
      title: "",
      detail:""
    }
  },
  mounted() {
    fetch("http://localhost:3000/projects/" + this.id)
    .then((res) => {
      return res.json()
    })
    .then((datas) => {
      this.title = datas.title,
        this.detail = datas.detail
    })
    .catch((err) => {
      console.log(err)
  })
  },
  methods: {
    updateProject() {
      fetch("http://localhost:3000/projects/" + this.id, {
        method: "PATCH",
        headers: {
          "Content-Type": "application/json"
        },
        body: JSON.stringify(
          {
            title: this.title,
            detail: this.detail,
          }
        )
      })
      .then((res) => {
        return res.json()
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