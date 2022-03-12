<script setup>
import { RouterLink } from "vue-router";

defineProps(["name", "species", "description", "elements", "ailments"]);
</script>

<template>
    <div class="monster-box">
      <div class="box-head row gx-0">
        <div class="col-md-6 d-flex">
          <img
            class="monster-box-img"
            :src="'../../monsters/' + name + '.png'"
            :alt="name"
          />
          <div class="monster-info align-self-center">
            <p class="monster-name text-white m-0">{{ name }}</p>
            <p class="monster-species m-0">{{ species }}</p>
          </div>
        </div>
        <div class="col-md-6 d-flex">
          <div v-if="elements[0]" class="monster-elements mx-auto">
            <p class="text-center">Elements</p>
            <img
              v-for="element in elements"
              :key="element"
              :src="'../../status/' + element + '.png'"
              :alt="element"
            />
          </div>
          <div v-if="ailments[0]" class="monster-ailments mx-auto">
            <p class="text-center">Ailments</p>
            <img
              v-for="ailment in ailments"
              :key="ailment"
              :src="'../../status/' + ailment.name + '.png'"
              :alt="ailment.name"
            />
          </div>
        </div>
      </div>
      <div class="box-info row align-items-center gx-0">
        <p class="monster-description m-0">
          {{ description }}
        </p>
      </div>
    </div>
</template>

<style>

    .monster-box {
    background-color: #1f1f1f;
    border-radius: 6px;
    }

    .box-head {
    display: flex;
    align-items: center;
    border-bottom: 1px solid #272727;
    padding: 1rem 1.5rem;
    }

    .box-info {
    padding: 1rem 1.5rem;
    }

    .monster-box-img {
    width: 128px;
    margin: 0 1.5rem 0 0;
    }

    .monster-name {
    align-self: center;
    text-transform: uppercase;
    letter-spacing: 2px;
    font-size: 1.5rem;
    }

    .monster-species {
    text-transform: capitalize;
    }

    .monster-description {
    text-align: justify;
    }

</style>
