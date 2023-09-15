<template>
  <div>This is from project Components</div>

  <br />
  Title {{ title }}

  <br />

  Id: {{ id }}

  <br />

  Description
  <p>{{ body }}</p>
  <button @click="$emit('increase-size')">Increase Front</button>
  <button>Button with slot</button>
  <button><slot></slot></button>
</template>

<script setup>
const props = defineProps({
  title: String,
  id: Number,
  body: String,
});
</script>
