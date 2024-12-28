<template>
  <div class="skills-container" :class="{ 'animate-section': animate }">
    <h1>My Skills</h1>
    <div class="skills-list">
      <div
        class="skill-card"
        v-for="(skill, index) in skills"
        :key="index"
        :class="{ 'animate-card': animate }"
        :style="{ animationDelay: `${index * 0.2}s` }"
      >
        <div class="skill-icon" :style="{ background: skill.iconBgColor }">
          <img v-if="skill.svg" :src="skill.svg" alt="" class="svg-icon" />
          <i v-else :class="skill.icon"></i>
        </div>
        <div class="skill-details">
          <h3>{{ skill.name }}</h3>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import arduino from "../assets/Arduino.svg";
import opencvSVG from "../assets/OpenCV.svg";

export default {
  data() {
    return {
      skills: [
        {
          name: "HTML",
          icon: "fab fa-html5",
          iconBgColor: "linear-gradient(45deg, #E44D26, #F06529)",
        },
        {
          name: "CSS",
          icon: "fab fa-css3-alt",
          iconBgColor: "linear-gradient(45deg, #2965F1, #61DAFB)",
        },
        {
          name: "JavaScript",
          icon: "fab fa-js-square",
          iconBgColor: "linear-gradient(45deg, #F7DF1E, #F1C40F)",
        },
        {
          name: "React",
          icon: "fab fa-react",
          iconBgColor: "linear-gradient(45deg, #61DAFB, #00D8FF)",
        },
        {
          name: "Vuejs",
          icon: "fab fa-vuejs",
          iconBgColor: "linear-gradient(45deg, #42b883, #35495E)",
        },
        {
          name: "Python",
          icon: "fab fa-python",
          iconBgColor: "linear-gradient(45deg, #FFE873, #4B8BBE)",
        },
        {
          name: "OpenCV",
          svg: opencvSVG,
          iconBgColor: "linear-gradient(45deg, #ff0000, #0000ff, #00cc00)",
        },
        {
          name: "Figma",
          icon: "fab fa-figma",
          iconBgColor: "linear-gradient(45deg, #F24E1E, #A259FF)",
        },
        {
          name: "Arduino",
          svg: arduino,
          iconBgColor: "linear-gradient(45deg, #3399ff, #Ffff)",
        },
        {
          name: "Git",
          icon: "fab fa-git-alt",
          iconBgColor: "linear-gradient(45deg, #F1502F, #D53F3E)",
        },
      ],
      animate: false,
    };
  },
  mounted() {
    const observer = new IntersectionObserver(
      ([entry]) => {
        if (entry.isIntersecting) {
          this.animate = true;
        }
      },
      { threshold: 0.3 }
    );

    observer.observe(this.$el);
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
  transform: translateY(30px);
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
  padding: 10px 0;
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
  transform: scale(0.9);
  opacity: 0;
  transition: transform 0.3s ease, opacity 0.3s ease;
  animation: fadeInScale 0.5s ease forwards;
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

@keyframes fadeInScale {
  0% {
    opacity: 0;
    transform: scale(0.9);
  }
  100% {
    opacity: 1;
    transform: scale(1);
  }
}

@media (max-width: 768px) {
  .skills-list {
    flex-direction: column;
    align-items: center;
  }

  .skills-container {
    padding: 10px;
  }
}
</style>
