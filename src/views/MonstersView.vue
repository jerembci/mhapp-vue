<script setup>
import { computed, onMounted, ref } from "vue";
import MonsterCard from "../components/MonsterCard.vue";

const monsters = ref([]);
const pageMonsterType = ref("large");
const activeLarge = computed(() => ({
  active: pageMonsterType.value == "large",
  green: pageMonsterType.value == "small",
}));

const activeSmall = computed(() => ({
  active: pageMonsterType.value == "small",
  green: pageMonsterType.value == "large",
}));

async function getMonsters() {
  let response = await fetch("https://mhw-db.com/monsters");
  const data = await response.json();
  monsters.value = data;
}

onMounted(() => {
  getMonsters();
});

const sortedMonsters = computed(() => {
  return monsters.value.slice(0).sort((a, b) => a.name.localeCompare(b.name));
});

</script>

<template>
  <header class="page-header">
    <span class="monsters-title">MONSTERS</span>
    <ol class="breadcrumb m-0 monster-type-change">
      <a @click="pageMonsterType = 'large'" :class="activeLarge" class="breadcrumb-item">LARGE</a>
      <a @click="pageMonsterType = 'small'" :class="activeSmall" class="breadcrumb-item">SMALL</a>
    </ol>
    <!-- <div class="monster-type-change">
      <a @click="pageMonsterType = 'large'" :class="activeLarge">Large</a>
      <span>/</span>
      <a @click="pageMonsterType = 'small'" :class="activeSmall">Small</a>
    </div> -->
  </header>
  <div class="content">
    <div class="monsters">
      <MonsterCard
        v-for="monster in sortedMonsters"
        :key="monster.id"
        :name="monster.name"
        :pageMonsterType="pageMonsterType"
        :monsterType="monster.type" />
    </div>
  </div>
</template>

<style>
.monsters {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
}

.monster-type-change {
  float: right;
}

.monster-type-change > a {
  text-decoration: none !important;
}

.monster-type-change > a:hover {
  cursor: pointer;
}

.active {
  color: var(--color-text);
}

.active:hover {
  color: var(--color-text);
}

</style>
