<template>
    <div v-if="job">
        <h1>{{ job.title }}</h1>
        <p>The job ID is : {{ id }}</p>
        <p>{{ job.details }}</p>
    </div>
    <div v-else>
        <p>Loading Job Details...</p>
    </div>
</template>

<script>
export default {
    props:['id'],
    mounted() {
      fetch('http://localhost:3000/jobs/' + this.id)/* By Using Json Server */
      .then(response => response.json())
      .then(data => this.job = data)
      .catch(err => console.log(err.message))
    },
    data() {
        return {
            /* id: this.$route.params.id */
            job:null
        }
    },
}
</script>

<style>

</style>