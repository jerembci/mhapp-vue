<script setup>
import { RouterView } from "vue-router";
import Sidebar from "./components/Sidebar.vue";
</script>

<template>
  <div class="app-wrapper container-lg flex-wrap px-0">
    <aside class="col-12 col-lg-2 col-md-3 sidebar-nav">
      <Sidebar />
    </aside>
    <main class="col-lg-10 col-md-9">
      <RouterView />
    </main>
  </div>
</template>

<style>
@import "@/assets/base.css";

#app {
  margin: 0 auto;
  font-weight: normal;
  width: 100%;
}

.app-wrapper {
  background-color: #0e0f0f;
  border-radius: 6px;
  display: flex;
}

.sidebar-nav {
  border-right: 1px solid rgba(48, 52, 54, 0.05);
}


.green {
  text-decoration: none;
  color: hsla(160, 100%, 37%, 1);
  transition: 0.4s;
}

.green:hover {
  color: hsla(160, 100%, 37%, 1);
}

@media (hover: hover) {
  .green:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

.page-header {
  background-color: #272727;
  padding: 1rem 2rem;
  letter-spacing: 2.5px;
  font-size: 1.35rem;
  border-radius: 0 4px 0 0;
  color: #b3bcde;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

main {
  width: 100%;
}

body {
  background-color: #1f1f1f !important;
}

.content {
  padding: 1.5rem;
  color: #ccd9e8;
}



@media (min-width: 992px) {
  #app {
    padding: 2rem 0 2rem 0;
  }
}
</style>
