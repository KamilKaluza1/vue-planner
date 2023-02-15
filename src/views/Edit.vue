<template>
 <h2>Edit Project</h2>
 <form @submit.prevent="handleSubmit">
    <label>Title</label>
    <input v-model="title" type="text" required />
    <label>Details</label>
    <textarea v-model="details" required></textarea>

    <button>Update Project</button>
  </form>
</template>

<script>
export default{
    props:['id'],
    data(){
        return{
            title: '',
            details: '',
            uri: 'http://localhost:3000/projects/' + this.id
        }
    },
    mounted(){
        fetch(this.uri)
        .then(res => res.json())
        .then(data => {
            this.title = data.title
            this.details = data.details
        })
    }

}
</script>