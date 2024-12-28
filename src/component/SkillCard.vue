<template>
  <div
    class="skills-container"
    ref="skillsContainer"
    :class="{ 'animate-section': animateSection }"
  >
    <h1>My Skills</h1>
    <div class="skills-list">
      <div
        class="skill-card"
        v-for="(skill, index) in skills"
        :key="index"
        :class="{ 'animate-card': animateSection }"
        :style="{ animationDelay: `${index * 0.2}s` }"
      >
        <div class="skill-icon" :style="{ backgroundColor: skill.iconBgColor }">
          <i :class="skill.icon"></i>
        </div>
        <div class="skill-details">
          <h3>{{ skill.name }}</h3>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      skills: [
        { name: "HTML", icon: "fab fa-html5", iconBgColor: "#E44D26" },
        { name: "CSS", icon: "fab fa-css3-alt", iconBgColor: "#2965F1" },
        {
          name: "JavaScript",
          icon: "fab fa-js-square",
          iconBgColor: "#F7DF1E",
        },
        { name: "Vue.js", icon: "fab fa-vuejs", iconBgColor: "#42b883" },
        { name: "React", icon: "fab fa-react", iconBgColor: "#61DAFB" },
        { name: "Python", icon: "fab fa-python", iconBgColor: "#3776AB" },
        { name: "Figma", icon: "fab fa-figma", iconBgColor: "#F24E1E" },
        { name: "Git", icon: "fab fa-git-alt", iconBgColor: "#F1502F" },
      ],
      animateSection: false,
    };
  },
  mounted() {
    const observer = new IntersectionObserver(
      ([entry]) => {
        if (entry.isIntersecting) {
          this.animateSection = true;
          observer.unobserve(this.$refs.skillsContainer);
        }
      },
      { threshold: 0.3 }
    );

    observer.observe(this.$refs.skillsContainer);
  },
};
</script>

<style scoped>
.skills-container {
  max-width: 1200px;
  margin: 40px auto;
  padding: 20px;
  text-align: center;
  color: #fca94f;
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.5s ease, transform 0.5s ease;
}

.skills-container.animate-section {
  opacity: 1;
  transform: translateY(0);
}

h1 {
  margin-bottom: 20px;
  font-size: 32px;
  font-weight: bold;
  color: #fca94f;
}

.skills-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
}

.skill-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: #333;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  color: #fff;
  text-align: center;
  width: 150px;
  height: 180px;
  opacity: 0;
  transform: translateY(20px);
  animation: fadeInUp 0.5s ease forwards;
}

.skill-card.animate-card {
  animation-play-state: running;
}

.skill-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
}

.skill-icon {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 30px;
  margin-bottom: 15px;
  color: #fff;
  transition: transform 0.3s ease;
}

.skill-icon:hover {
  transform: scale(1.1);
}

.skill-details h3 {
  margin: 0;
  font-size: 18px;
  font-weight: 600;
  color: #fff;
}

@keyframes fadeInUp {
  0% {
    opacity: 0;
    transform: translateY(20px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
