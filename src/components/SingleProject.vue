<template>
<div class="project">
    <div class="flexing">
        <div>
            <h3 @click="showDetail = !showDetail"> {{ project.title }} </h3>
        </div>
        <div>
            <span class="material-icons">
                delete
            </span>
            <span class="material-icons">
                edit
            </span>
            <span class="material-icons">
                done
            </span>
        </div>
    </div>
    <p v-if="showDetail"> {{ project.detail }} </p>
</div>
</template>

<script>
export default {
    data() {
        return {
            showDetail: false

        }
    },
    methods: {
       
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
h3{
    color: indigo;
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
</style>