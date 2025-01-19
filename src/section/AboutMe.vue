<template>
  <section
    id="about-me"
    class="about-me"
    :class="{ 'animate-in': inViewport, 'animate-out': !inViewport }"
  >
    <div class="background-animation"></div>
    <div class="container">
      <div class="title-container">
        <h2>
          <span v-for="(char, index) in title" :key="index" class="char">
            {{ char }}
          </span>
        </h2>
      </div>
      <div class="content">
        <div class="image-container">
          <img :src="photo" alt="Your Photo" />
        </div>
        <div class="text-container">
          <p>
            <span>In my pursuit of an engaging college life</span> as a
            Mechatronics and AI student, I have participated in different
            competitions and projects that combine software and data science.
            Such experience has <span>polished my programming skills</span>,
            increased my comprehension of data analysis, and allowed me to gain
            practical knowledge of machine learning algorithms.
          </p>
          <p>
            These experiences not only enriched my technical skills but also
            enhanced my ability to <span>think critically</span>,
            <span>learn quickly</span> in new circumstances, and
            <span>collaborate effectively</span> with a team.
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import profile from "../assets/aboutme.png";

export default {
  data() {
    return {
      photo: profile,
      inViewport: false,
      title: "About Me",
    };
  },
  mounted() {
    const observer = new IntersectionObserver(
      ([entry]) => {
        this.inViewport = entry.isIntersecting;
      },
      { threshold: 0.1 }
    );

    const aboutMeSection = document.getElementById("about-me");
    if (aboutMeSection) {
      observer.observe(aboutMeSection);
    }
  },
};
</script>

<style scoped>
.about-me {
  height: 100vh;
  width: 100%;
  background: linear-gradient(120deg, #f4a261, #f2b179);
  position: relative;
  font-family: "Arial", sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  opacity: 0;
  transform: translateY(50px);
  transition: opacity 1s ease, transform 1s ease;
  overflow: hidden;
}

.about-me.animate-in {
  opacity: 1;
  transform: translateY(0);
}

.about-me.animate-out {
  opacity: 0;
  transform: translateY(50px);
}

.background-animation {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(-45deg, #f4a261, #e76f51, #f2b179, #fca311);
  background-size: 400% 400%;
  animation: gradientMove 10s ease infinite;
  z-index: -1;
}

@keyframes gradientMove {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 20px;
  text-align: center;
}

.title-container h2 {
  font-size: 2.5rem;
  display: inline-block;
  color: white;
}

.char {
  display: inline-block;
  animation: fadeInChar 0.05s ease forwards;
  opacity: 0;
}

.char:nth-child(n) {
  animation-delay: calc(var(--index) * 0.1s);
}

@keyframes fadeInChar {
  from {
    opacity: 0;
    transform: translateY(-20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.content {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 20px;
  align-items: center;
}

.image-container {
  display: flex;
  justify-content: center;
}

.image-container img {
  width: 80%;
  max-width: 300px;
  border-radius: 20px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  transition: transform 0.5s ease, box-shadow 0.5s ease;
}

.image-container img:hover {
  transform: scale(1.1);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.5);
}

.text-container p {
  font-size: 1.2rem;
  line-height: 1.8;
  margin-bottom: 15px;
  text-align: justify;
  color: white;
}

.text-container p span {
  font-weight: bold;
  color: black;
}

.text-container p:last-of-type {
  margin-bottom: 0;
}
</style>
