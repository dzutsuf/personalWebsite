<template>
  <section class="contact-section">
    <div class="contact-header">
      <h2>Let's Get Connected</h2>
      <p>Feel free to reach out for collaborations or just a friendly chat!</p>
    </div>
    <div class="contact-content">
      <div class="contact-info">
        <InfoCard
          v-for="(info, index) in contactInfo"
          :key="index"
          :iconc="info.iconc"
          :title="info.title"
          :content="info.content"
          :link="info.link"
        />
      </div>
      <form class="contact-form" @submit.prevent="handleSubmit">
        <input
          v-model="form.name"
          type="text"
          placeholder="Your Name"
          required
        />
        <input
          v-model="form.email"
          type="email"
          placeholder="Your Email"
          required
        />
        <textarea
          v-model="form.message"
          placeholder="Your Message"
          rows="5"
          required
        ></textarea>
        <button type="submit">Send Message</button>
      </form>
    </div>
  </section>
</template>

<script>
import InfoCard from "../component/InfoCard.vue";

export default {
  name: "ContactSection",
  components: {
    InfoCard,
  },
  data() {
    return {
      contactInfo: [
        {
          iconc: "📧",
          title: "Email",
          content: "othmadsyd@gmail.com",
          link: "mailto:othmadsyd@gmail.com",
        },
        {
          iconc: "📱",
          title: "Phone",
          content: "+62 857 0740 0991",
          link: "https://wa.me/6285707400991",
        },
      ],
      form: {
        name: "",
        email: "",
        message: "",
      },
    };
  },
  methods: {
    handleSubmit() {
      alert(
        `Message sent!\nName: ${this.form.name}\nEmail: ${this.form.email}\nMessage: ${this.form.message}`
      );
      this.form.name = "";
      this.form.email = "";
      this.form.message = "";
    },
  },
};
</script>

<style scoped>
.contact-section {
  width: 100%;
  padding: 40px;

  font-family: "Arial", sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
}

.contact-header {
  text-align: center;
}

.contact-header h2 {
  font-size: 2.5rem;
  color: #fca94f;
  margin-bottom: 10px;
}

.contact-header p {
  font-size: 1rem;
  color: #f7bd7f;
}

.contact-content {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
  width: 100%;
  max-width: 1000px;
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: 20px;
  flex: 1;
}

.contact-form {
  background-color: #ffffff;
  border: 1px solid #dcdde1;
  border-radius: 10px;
  padding: 20px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.contact-form input,
.contact-form textarea {
  width: 100%;
  padding: 10px;
  border: 1px solid #dcdde1;
  border-radius: 5px;
  font-size: 1rem;
}

.contact-form button {
  background-color: #fca94f;
  color: white;
  border: none;
  padding: 10px;
  border-radius: 5px;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.contact-form button:hover {
  background-color: transparent;
  border: solid #fca94f;
  color: #fca94f;
}
</style>
