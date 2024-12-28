<template>
  <div class="my-project">
    <h1 class="title">My Project</h1>
    <div class="project-container">
      <ProjectBox
        v-for="(project, index) in projects"
        :key="index"
        :imageUrl="project.imageUrl"
        :title="project.title"
        :description="project.description"
        :link="project.link"
      />
    </div>
  </div>
</template>

<script>
import ProjectBox from "../component/ProjectBox.vue";
import rajawaliFarm from "../assets/logorajawalifarm.png";
import yourable from "../assets/logo_yourable.png";
import aksara from "../assets/logoAksara.png";

export default {
  name: "MyProject",
  components: {
    ProjectBox,
  },
  data() {
    return {
      projects: [
        {
          imageUrl: rajawaliFarm,
          title: "Rajawali Farm",
          description:
            "Building partners in website development for Pt. Rajawali Farm to increase company credibility",
          link: "https://rajawali-farm-website.vercel.app/",
        },
        {
          imageUrl: yourable,
          title: "YOURABLE",
          description:
            "Design and build an assistant application for someone with hearing and vision impairments.",
          link: "https://www.youtube.com/watch?v=DQqm5xAaOvU",
        },
        {
          imageUrl: aksara,
          title: "AKSARA",
          description:
            "A smart app innovation aims to boost elementary school children's enthusiasm in reading",
          link: "https://youtu.be/QzV4d7QWv1s",
        },
      ],
    };
  },
};
</script>

<style>
.my-project {
  min-height: 100vh;
  width: 100%;
  padding: 40px;
  background-color: #f4f4f4;
  font-family: Arial, sans-serif;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.title {
  text-align: center;
  font-size: 2.5rem;
  margin-bottom: 20px;
  font-weight: bold;
}

.project-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
}
</style>
