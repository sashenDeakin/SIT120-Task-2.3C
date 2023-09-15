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

import datafld from "../data/data.json";
const datalist = ref();
</script>

<template>
  <div :style="{ fontSize: postFrontSize + 'em' }">
    <div>
      <p>Post Page</p>
    </div>
    <!--   <ol>
    <li v-for="post in posts">{{ post.title }}</li>
  </ol> -->

    <div>
      <ProjectComponent
        v-for="post in posts"
        :key="post.id"
        :id="post.id"
        :title="post.title"
        :body="post.body"
        @increase-size="increaseSize"
        ><!-- Button WIth Slot Two -->
        {{ post.id }}
        <template #footer> This is Name SLot </template>
      </ProjectComponent>
    </div>
  </div>
</template>
