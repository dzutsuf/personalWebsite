<template>
  <div class="bg">
    <div class="Greeting">
      <div class="greet-content">
        <h3 class="h3">Hello, I am</h3>
        <h1 class="h1">Utsman Ahmad</h1>
        <h2 class="h2">
          <div class="role-container">
            <span class="static-text">Junior </span>
            <span id="changing-text" class="dynamic-text"></span>
          </div>
        </h2>
        <div class="social-icons">
          <a
            href="https://www.linkedin.com/in/utsman-ahmad-58ba90253/"
            class="icon"
            target="_blank"
            rel="noopener noreferrer"
          >
            <i class="fab fa-linkedin"></i>
          </a>

          <a
            href="https://www.instagram.com/syuhada_ahm/"
            class="icon"
            target="_blank"
            rel="noopener noreferrer"
          >
            <i class="fab fa-instagram"></i>
          </a>

          <a
            href="https://github.com/dzutsuf"
            class="icon"
            target="_blank"
            rel="noopener noreferrer"
          >
            <i class="fab fa-github"></i>
          </a>
        </div>
        <CustomButton
          label="Curriculum Vitae"
          colorClass="primary"
          :download="true"
          fileUrl="https://drive.google.com/file/d/1zaBBNC9EXWkntbEwglif7RUFUf18vXnD/view?usp=sharing"
          fileName="CV-Utsman.pdf"
          target="_blank"
          rel="noopener noreferrer"
        />
      </div>
      <div class="profile-picture">
        <img src="../assets/profile.png" alt="Utsman Ahmad" />
      </div>
    </div>
  </div>
</template>

<script>
import CustomButton from "../component/ButtonComp.vue";

export default {
  name: "GreetingU",
  data() {
    return {
      texts: ["WebDev", "ML Engineer"],
      textIndex: 0,
    };
  },
  components: {
    CustomButton,
  },
  mounted() {
    this.displayText();
  },
  methods: {
    displayText() {
      const changingText = document.getElementById("changing-text");
      const currentText = this.texts[this.textIndex];

      changingText.innerHTML = "";

      [...currentText].forEach((char, index) => {
        const span = document.createElement("span");
        span.textContent = char;
        span.style.animationDelay = `${index * 0.1}s`;
        changingText.appendChild(span);
      });

      this.textIndex = (this.textIndex + 1) % this.texts.length;

      setTimeout(this.displayText, currentText.length * 100 + 2000);
    },
  },
};
</script>

<style>
.Greeting {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-right: 70px;
  margin-right: 70px;
  padding-left: 70px;
  margin-left: 70px;
}

.greet-content {
  color: white;
}

.h3 {
  font-size: 40px;
  margin-bottom: 10px;
  font-weight: bold;
}

.h1 {
  font-size: 70px;
  margin-bottom: 10px;
  font-weight: bold;
}

.h2 {
  font-size: 40px;
  color: #f4a261;
  font-weight: bold;
}

.role-container {
  display: inline-block;
  align-items: baseline;
  overflow: hidden;
}

.static-text {
  font-size: 2.5rem;
  font-weight: bold;
  color: #f4a261;
}

.dynamic-text {
  font-size: 2.5rem;
  font-weight: bold;
  color: #f4a261;
  margin-left: 0.3rem;
  overflow: hidden;
}

.dynamic-text span {
  display: inline-block;
  position: relative;
  transform: translateY(100%);
  animation: textReveal 2s cubic-bezier(0.19, 1, 0.22, 1) forwards;
}

@keyframes textReveal {
  0% {
    transform: translateY(100%);
  }

  90% {
    transform: translateY(0);
  }
  100% {
    transform: translateY(-100%);
  }
}

.icon {
  display: inline-flex;
  justify-content: center;
  align-items: center;
  margin: 30px 15px 30px 0;
  width: 50px;
  height: 50px;
  font-size: 24px;
  color: #f4a261;
  text-decoration: none;
  border: 2px solid #f4a261;
  border-radius: 50%;
  transition: color 0.3s ease, border-color 0.3s ease;
}

.icon:hover {
  background-color: #fca94f;
  color: #222831;
  box-shadow: 0 0 20px #fca94f;
}

.profile-picture {
  position: relative;
  width: 500px;
  height: 500px;
  border-radius: 50%;
  overflow: hidden;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
  margin-top: 20px;
}

.frame img {
  width: 250px;
  height: auto;
  object-fit: cover;
  border: none;
}
</style>
