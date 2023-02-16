<template>
  <h2>Edit Project</h2>
  <form @submit.prevent="editProject">
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
    },
    methods: {
        editProject() {
        fetch(this.uri, {
            method: "PATCH",
            headers: { "Content-Type": "application/json" },
            body: JSON.stringify({ 
                title: this.title,
                details: this.details }),
        })
        .then(()=>{this.$router.push('/')})
        .catch(e => console.log(e.message))
        }
    }

}
</script>
