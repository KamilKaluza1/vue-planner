<template>
  <div class="project" :class="{complete: project.complete}">
    <div class="actions" @click="showDetails">
      <h3>{{ project.title }}</h3>
      <div class="icons">
        <span @click="toggleComplete" class="material-icons nike"> done </span>
        <span class="material-icons"> edit </span>
        <span @click="deleteProject" class="material-icons"> delete  </span>
    </div>
    </div>
    <div v-if="details" class="details">
      <p>{{ project.details }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["project"],
  data() {
    return {
      details: false,
      uri: 'http://localhost:3000/projects/' + this.project.id
    };
  },
  methods: {
    showDetails() {
      this.details = !this.details;
    },
    deleteProject(){
        fetch(this.uri, {method: 'DELETE'})
        .then(() => this.$emit('delete', this.project.id))
        .catch(err => console.log(err.message))
    },
    toggleComplete(){
        fetch(this.uri, {
            method:"PATCH",
            headers:{'Content-Type': 'application/json'},
            body: JSON.stringify({complete: !this.project.complete})
        }).then(() => {
            this.$emit('complete', this.project.id)
        }).catch(err => console.log(err.message))
    }
  },
};
</script>

<style>
.project {
  margin: 20px auto;
  background: white;
  padding: 10px 20px;
  border-radius: 5px;
  box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.08);
  border-left: 4px solid red;
}
h3 {
  cursor: pointer;
}
.actions{
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.material-icons{
    cursor: pointer;
}
.material-icons:hover{
    color: #777;
}
.project.complete{
    border-left: 4px solid green;
}
.project.complete .nike{
    color: green;
}
</style>
