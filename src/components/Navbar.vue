<template>
<ul class="nav justify-content-center fw-bold mt-5">
    <li class="nav-item">
        <router-link to="/" class="nav-link active">Projects</router-link>
    </li>
    <li class="nav-item">
        <router-link :to="{ name:'AddProject'}" class="nav-link">Add Project</router-link>
    </li>
</ul>
</template>

<script>
export default {

}
</script>

<style>
a.router-link-active{
    border-bottom: 3px solid;
    padding-bottom: 4px;
}
</style>