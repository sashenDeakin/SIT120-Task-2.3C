<template>
  <div class="card">
    <div class="card-content">
      <p>Id: {{ id }}</p>
      <h2>Title {{ title }}</h2>
      <br />
      Description
      <p>{{ body }}</p>
      <div style="align-items: center; text-align: center; grid: 50px">
        <button
          class="beautiful-button increase"
          @click="$emit('increase-size')"
        >
          Increase Front
        </button>
        <button
          class="beautiful-button decrease"
          @click="$emit('discase-size')"
        >
          Decrease Front
        </button>
        <button style="margin-top: 4px"><slot></slot></button>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  title: String,
  id: Number,
  body: String,
});
</script>

<style scoped>
.card {
  max-width: 300px;
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  margin: 20px;
  overflow: hidden;
  transition: transform 0.2s;
}

.card:hover {
  transform: scale(1.05);
}

.card-content {
  padding: 20px;
}

.card-content a {
  display: block;
  margin-top: 10px;
  text-decoration: none;
  color: #007bff;
  font-weight: bold;
}

.card-content a:hover {
  text-decoration: underline;
}

.beautiful-button {
  display: inline-block;
  padding: 10px 20px;
  font-size: 13px;
  margin: 1px;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease-in-out;
}

.decrease {
  background-color: green;
}

.increase {
  background-color: #007bff;
}

.increase:hover {
  background-color: #0056b3;
}

.decrease:hover {
  background-color: #0056b3;
}

.beautiful-button:focus {
  outline: none;
  box-shadow: 0 0 5px rgba(0, 123, 255, 0.5);
}

.beautiful-button:active {
  transform: translateY(2px);
}
</style>
