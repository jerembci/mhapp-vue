<script setup>
import { onMounted, ref } from "vue";
import { RouterLink } from "vue-router";
import MonsterBox from "../components/MonsterBox.vue";
import MonsterWeakness from "../components/MonsterWeakness.vue";

const props = defineProps(["monsterName"]);

const monster = ref({});
const loading = ref(true);

async function getMonster() {
  let response = await fetch(
    'https://mhw-db.com/monsters?q={"name":"' + props.monsterName + '"}'
  );
  const data = await response.json();
  monster.value = data[0];
  loading.value = false;
}

onMounted(() => {
  getMonster();
});
</script>

<template>
  <header class="page-header">
    <ol class="breadcrumb m-0">
      <RouterLink to="/monsters" class="monsters-title breadcrumb-item"
        >MONSTERS</RouterLink>
      <span class="breadcrumb-item active">{{ monsterName }}</span>
    </ol>
  </header>
  <div v-if="!loading" class="content">
    <MonsterBox 
        :name="monsterName"
        :species="monster.species"
        :description="monster.description"
        :elements="monster.elements"
        :ailments="monster.ailments"/>
    <MonsterWeakness
        :weaknesses="monster.weaknesses"
        :resistances="monster.resistances" />
  </div>
</template>

<style scoped>
.page-header {
  text-transform: uppercase;
}

.breadcrumb-item:not(.active) {
  text-decoration: none;
  color: #b3bcde;
}

.breadcrumb-item:not(.active)::after {
  height: 2px;
  position: absolute;
  width: 0;
  left: 0;
  bottom: -5px;
  background-color: #b3bcde;
  content: "";
  transition: all 0.2s ease;
}

.breadcrumb-item:not(.active):hover:after {
  width: 100%;
}

.breadcrumb-item.active {
  color: #636c72;
}

</style>
