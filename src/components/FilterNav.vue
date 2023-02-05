<template>
<ul class="nav my-3">
    <li class="nav-item">
        <button class="btn text-black-50 text-uppercase" @click="filterBy('all')" :class="{ buttonactive : current === 'all'}">all</button>    
    </li>
    <li class="nav-item ">
        <button class="btn text-black-50 text-uppercase" @click="filterBy('complete')" :class="{buttonactive:current === 'complete'}">complete</button>
    </li>
    <li class="nav-item">
        <button class="btn text-black-50 text-uppercase" @click="filterBy('ongoing')" :class="{buttonactive:current === 'ongoing'}">ongoing</button>
    </li>
</ul>
</template>

<script>
export default {
    methods: {
        filterBy(value) {
            this.$emit('filterValue',value)
        }
    },
    props: ['current']
}
</script>

<style>
a.router-link-active {
    border-bottom: 3px solid;
    padding-bottom: 4px;
}
.buttonactive{
    font-weight: bolder;
    color: #000;
}
</style>