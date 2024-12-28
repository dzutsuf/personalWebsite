<template>
  <div class="info-card">
    <div class="iconc">{{ iconc }}</div>
    <h3>{{ title }}</h3>
    <p>{{ content }}</p>
    <a :href="link" target="_blank" rel="noopener noreferrer">Learn More</a>
  </div>
</template>

<script>
export default {
  name: "InfoCard",
  props: {
    iconc: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    content: {
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
.info-card {
  background-color: #ffffff;
  border: 1px solid #dcdde1;
  border-radius: 10px;
  padding: 20px;
  text-align: center;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.info-card:hover {
  transform: translateY(-5px);
}

.info-card .iconc {
  font-size: 2.5rem;
  margin-bottom: 10px;
  color: #3498db;
}

.info-card h3 {
  font-size: 1.2rem;
  margin-bottom: 5px;
  color: #2c3e50;
}

.info-card p {
  font-size: 1rem;
  color: #7f8c8d;
  margin-bottom: 10px;
}

.info-card a {
  text-decoration: none;
  color: #3498db;
  font-weight: bold;
  font-size: 0.9rem;
}
</style>
