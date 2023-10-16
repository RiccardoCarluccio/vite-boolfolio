<script>
import axios from "axios";

export default {
	data() {
		return {
			projects: [],
			pagination: {}
		};
	},
	methods: {
		fetchData() {
			axios.get(url ?? "http://127.0.0.1:8000/api/projects")
				.then((response) => {
				this.projects = response.data.data;
				delete response.data.data;
				this.pagination = response.data;
      });
		},
		getImageUrl(project) {
			return `http://127.0.0.1:8000/api/projects/${project.image}`;
		}
	},
	mounted() {
		this.fetchData();
	}
};
</script>

<template>
  <div v-for="project in projects" :key="project.id">
    <div>{{ project.title }}</div>
    <div>{{ project.description }}</div>
  </div>
</template>

<style scoped>

</style>