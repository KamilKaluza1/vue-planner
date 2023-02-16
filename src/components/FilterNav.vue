<template>
  <nav class="filter-nav">
    <button @click="updateFilter('all')" :class="{ active: (current === 'all') }">
      All Projects
    </button>
    <button
      @click="updateFilter('ongoing')"
      :class="{ active: (current === 'ongoing') }"
    >
      Ongoing Projects
    </button>
    <button
      @click="updateFilter('complete')"
      :class="{ active: (current === 'complete') }"
    >
      Complete Projects
    </button>
  </nav>
</template>

<script>
export default {
  props: ["current"],
  methods: {
    updateFilter(by) {
      this.$emit("filterChange", by);
    },
  },
};
</script>

<style scoped>
button {
  background: none;
  border: none;
  color: #bbb;
  outline: none;
  font-size: 12px;
  text-transform: uppercase;
  margin-right: 10px;
  letter-spacing: 1px;
  font-weight: bold;
  cursor: pointer;
}
.active{
    color: black;
}
</style>
