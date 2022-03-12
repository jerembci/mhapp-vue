<script setup>
import { RouterLink } from "vue-router";
</script>

<template>
    <nav class="navbar-expand-md flex-md-column flex-row">
        <header class="title">
            <RouterLink to="/" class="green">MHWDB</RouterLink>
            <button class="navbar-toggler border-0 float-end" type="button" data-bs-toggle="collapse" data-bs-target="#sidebarToggler" aria-controls="sidebarToggler" aria-expanded="false">
                <i class="bi bi-list toggler"></i>
            </button>
        </header>
        <div class="collapse navbar-collapse" id="sidebarToggler">
            <ul>
                <li class="sub-header">
                    <span>DATABASE</span>
                </li>
                <li>
                    <RouterLink to="/monsters" class="green">Monsters</RouterLink>
                </li>
                <li>
                    <RouterLink to="/weapons" class="green">Weapons</RouterLink>
                </li>
                <li>
                    <RouterLink to="/armor" class="green">Armor</RouterLink>
                </li>
                <li>
                    <RouterLink to="/locations" class="green">Locations</RouterLink>
                </li>
            </ul>
        </div>
    </nav>
</template>

<style>

.title {
  padding: 1rem 0.5rem;
  background-color: #0c0d0d;
  border-radius: 6px 0 0 0;
  text-align: center;
  letter-spacing: 2.5px;
  font-size: 1.35rem;
}

.navbar-toggler:focus {
    box-shadow: none !important;
    outline: none !important;
}

.navbar-toggler {
    position: absolute;
    right: 10px;

}

.sub-header {
  letter-spacing: 1px;
  padding-top: 1rem;
  color: #b3bcde;
}

.toggler {
    color: white;
}

ul {
  list-style: none;
  padding: 1rem 1.5rem;
}

ul > li,
a {
  padding: 7px 7px 7px 5px;
}

a {
  padding: 0;
}
</style>
