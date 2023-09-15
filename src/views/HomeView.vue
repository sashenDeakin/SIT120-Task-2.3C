<script setup>
import { ref, onMounted } from "vue";
import ProjectComponent from "../components/projectComponontes.vue";

const posts = ref([]);

const fetchPost = async () => {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/posts");
    const data = await response.json();

    posts.value = data;
  } catch (error) {
    console.log(error);
  }
};

onMounted(fetchPost);

const postFrontSize = ref(1);

function increaseSize() {
  postFrontSize.value += 1;
}

function discreteSize() {
  postFrontSize.value -= 1;
}
</script>

<template>
  <div>
    <div>
      <p>Post Page</p>
    </div>
    <ol class="beautiful-list">
      <li v-for="post in posts">{{ post.title }}</li>
    </ol>
    <hr />
    <div class="card-list" :style="{ fontSize: postFrontSize + 'em' }">
      <ProjectComponent
        v-for="post in posts"
        :key="post.id"
        :id="post.id"
        :title="post.title"
        :body="post.body"
        @increase-size="increaseSize"
        @discase-size="discreteSize"
        ><!-- Button WIth Slot Two -->
        Post Front Size: {{ postFrontSize }}
        <template #footer> This is Name SLot </template>
      </ProjectComponent>
    </div>
  </div>
</template>

<style scoped>
.beautiful-list {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
  grid-auto-rows: minmax(100px, auto);
}

.card-list {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 10px;
  grid-auto-rows: minmax(100px, auto);
}
.beautiful-list li {
  background-color: #f0f0f0;
  border-radius: 8px;
  margin: 8px 0;
  padding: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  text-transform: uppercase;
  text-align: center;
}

.beautiful-list li::before {
  content: "\2022";
  color: #ff7f50;
  font-size: 1.2em;
  margin-right: 10px;
}

/* Hover effect */
.beautiful-list li:hover {
  transform: scale(1.05);
  transition: transform 0.2s ease-in-out;
  background-color: #e0e0e0;
}
</style>
