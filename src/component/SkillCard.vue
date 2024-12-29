<template>
  <div class="skill-card">
    <div class="skill-icon" :style="{ backgroundColor: iconBgColor }">
      <i :class="icon"></i>
    </div>
    <div class="skill-details">
      <h3>{{ skill }}</h3>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    skill: String,
    icon: String,
    iconBgColor: String,
  },
};
</script>

<style scoped>
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
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  width: 150px; /* Menyesuaikan lebar kartu */
  height: 180px; /* Menyesuaikan tinggi kartu */
  text-align: center;
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
</style>
