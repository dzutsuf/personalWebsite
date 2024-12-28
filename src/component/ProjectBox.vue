<template>
  <div class="project-box">
    <div class="avatar" style="height: 130px; width: 130px">
      <img :src="imageUrl" height="130" width="130" />
    </div>
    <h2 class="project-title">{{ title }}</h2>
    <p class="project-description">{{ description }}</p>
    <a
      :href="link"
      class="project-link"
      target="_blank"
      rel="noopener noreferrer"
    >
      View Project
    </a>
  </div>
</template>

<script>
export default {
  name: "ProjectBox",
  props: {
    imageUrl: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
    link: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
.project-box {
  padding: 20px;
  background-color: #ffffff;
  border: 1px solid #ddd;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  text-align: center;
  width: 300px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.avatar {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 130px;
  width: 130px;
  margin: 0 auto;

  overflow: hidden;
}

.avatar img {
  object-fit: cover;
  display: block;
}

.project-box:hover {
  transform: translateY(-10px);
  box-shadow: 0 6px 10px rgba(0, 0, 0, 0.15);
}

.project-title {
  font-size: 1.5rem;
  margin-bottom: 10px;
  color: #333;
}

.project-description {
  font-size: 1rem;
  margin-bottom: 15px;
  color: #555;
}

.project-link {
  font-size: 1rem;
  color: #007bff;
  text-decoration: none;
  font-weight: bold;
}

.project-link:hover {
  text-decoration: underline;
}
</style>
