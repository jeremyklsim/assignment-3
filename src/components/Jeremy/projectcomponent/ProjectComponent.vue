<template>
  <div>
    <h3>Projects Component</h3>

    <div v-for="project in projects" v-bind:key="project.id">
      <div class="d-inline-flex ddelement">
        <div class="row">
        <h4 v-bind:href="project.name" target="_blank">{{ project.name }}</h4>
        <h6>
          Behance Link:
          <a v-bind:href="project.url" target="_blank">{{ project.url }}</a>
        </h6>
        </div>
        <div class="project-photos-cover">
          <img class="project-image" v-bind:src="project.covers[230]">
        </div>
      </div>
      <div>
        <div v-for="photo in project.modules" v-bind:key="project.modules" class="project-photos-cover row">
          <img class="project-images" v-bind:src="photo.sizes.max_1200">
        </div>
      </div>
      <!-- FIX THIS FOR TUESDAY!! -->

      <!-- <div v-for="project in projects" v-bind:key="project.modules">
        <div class="project-photos-cover">
          <img class="project-image" v-bind:src="project.sizes[1400]">
        </div>
      </div>-->
    </div>
  </div>
</template>

<script>
export default {
  name: "ProjectComponent",
  props: ["source"],
  data: function() {
    return {
      projects: []
    };
  },
  methods: {
    getProjects: function() {
      console.log("get");

      this.$http
        .get("https://behance-mock-api.glitch.me/api/projects")
        .then(function(data) {
          console.log("data", data);
          this.projects = data.body.projects;
          console.log(this.projects);
        });
    }
  },
  created: function() {
    this.getProjects();
  }
};
</script>


<style scoped>
.project-images{
  border-radius: 25px;
  /* width: 800px;
  height: auto; */
}

.designer-element {
  margin: 15px;
}

.ddelement {
  width: 100vw;
  padding:20px;
  background-color: #dbdbdb;
}

.ddelement:hover {
  box-shadow: none;
}
</style>
