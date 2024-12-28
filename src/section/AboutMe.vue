<template>
  <section
    id="about-me"
    class="about-me"
    :class="{ 'animate-in': inViewport, 'animate-out': !inViewport }"
  >
    <div class="container">
      <div class="title-container">
        <h2>About Me</h2>
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
  background-color: #f4f4f4;
  font-family: "Arial", sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  opacity: 0;
  transform: translateY(50px);
  transition: opacity 1s ease, transform 1s ease;
}

.about-me.animate-in {
  opacity: 1;
  transform: translateY(0);
}

.about-me.animate-out {
  opacity: 0;
  transform: translateY(50px);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.title-container {
  width: 100%;
  margin-bottom: 10px;
  color: black;
}

h2 {
  font-size: 2.5rem;
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
}

.text-container p {
  font-size: 1.2rem;
  line-height: 1.8;
  margin-bottom: 15px;
  text-align: justify;
}

.text-container p span {
  font-weight: bold;
  color: #f4a261;
}

.text-container p:last-of-type {
  margin-bottom: 0;
}
</style>
