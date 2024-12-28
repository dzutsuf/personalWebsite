<template>
  <header class="Navbar">
    <div class="container">
      <div class="logo">
        <h1>PersonalWeb</h1>
      </div>
      <nav class="nav">
        <ul>
          <li>
            <a href="javascript:void(0)" class="cta-button" @click="goToAboutMe"
              >About</a
            >
          </li>
          <li>
            <a
              href="javascript:void(0)"
              class="cta-button"
              @click="goToMyProject"
              >My Project</a
            >
          </li>
          <li>
            <a href="javascript:void(0)" class="cta-button" @click="goToContact"
              >Contact</a
            >
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  methods: {
    goToAboutMe() {
      const aboutMeSection = document.getElementById("AboutMe");
      if (aboutMeSection) {
        aboutMeSection.scrollIntoView({ behavior: "smooth" });
      }
    },
    goToMyProject() {
      const myProjectSection = document.getElementById("MyProject");
      if (myProjectSection) {
        myProjectSection.scrollIntoView({ behavior: "smooth" });
      }
    },
    goToContact() {
      const contactSection = document.getElementById("ContactMe");
      if (contactSection) {
        contactSection.scrollIntoView({ behavior: "smooth" });
      }
    },
  },
};
</script>

<style>
.Navbar {
  width: 100%;
  animation: slideIn 0.6s ease-out;
}

@keyframes slideIn {
  0% {
    transform: translateY(-100%);
    opacity: 0;
  }
  100% {
    transform: translateY(0);
    opacity: 1;
  }
}

.container {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 30px 8%;
}

.nav ul {
  display: flex;
  list-style-type: none;
  margin: 0;
  padding: 0;
}

.nav li {
  margin: 0 30px;
  color: #fff1c5;
  font-size: 18px;
  font-weight: 600;
}

.nav li:hover {
  color: orange;
  transition: color 0.3s ease;
}

.logo {
  color: #fff1c5;
  font-size: 25px;
  font-weight: 600;
}
</style>
