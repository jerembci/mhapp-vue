<script setup>
import { RouterLink } from "vue-router";

defineProps(["name", "monsterType", "pageMonsterType"]);
</script>

<template>
  <RouterLink
    v-if="monsterType === pageMonsterType"
    class="monster-card green"
    :to="'/monsters/' + name">
    <img
      class="monster-img"
      :src="'../../monsters/' + name + '.png'"
      :alt="name"
    />
    <small>{{ name }}</small>
  </RouterLink>
</template>

<style>
img {
  width: 64px;
}

.monster-card {
  display: flex;
  flex-direction: column;
  background-color: #1f1f1f;
  border-radius: 4px;
  margin: 5px;
  text-align: center;
  padding: 0.75rem;
}

.monster-img {
  width: 64px;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 5px;
  align-self: center;
}
</style>
