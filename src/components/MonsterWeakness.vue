<script setup>
import { computed, ref } from "vue";
import { RouterLink } from "vue-router";

const props = defineProps(["weaknesses", "resistances"]);

const processedWeaknesses = computed(() => {
    let res = {
        "fire": {normal: 0, cond: 0}, 
        "poison": {normal: 0, cond: 0},
        "water": {normal: 0, cond: 0},
        "sleep": {normal: 0, cond: 0},
        "thunder": {normal: 0, cond: 0},
        "paralysis": {normal: 0, cond: 0},
        "ice": {normal: 0, cond: 0},
        "blast": {normal: 0, cond: 0},
        "dragon": {normal: 0, cond: 0},
        "stun": {normal: 0, cond: 0}}
    props.weaknesses.forEach(weakness => {
        if (weakness.condition == null) {
            res[weakness.element]["normal"] = weakness.stars
            res[weakness.element]["cond"] = weakness.stars
        } else {
            res[weakness.element]["cond"] = weakness.stars
        }
    })
    props.resistances.forEach(resistance => {
        if (resistance.condition == null) {
            res[resistance.element]["normal"] = 0
        } else {
            res[resistance.element]["cond"] = 0
        }

    })
    return res
})

const condition = computed(() => {
    let cond = ""
    props.weaknesses.forEach(weakness => {
        if (weakness.condition) {
            cond = weakness.condition
        }
    })
    props.resistances.forEach(resistance => {
        if (resistance.condition) {
            cond = resistance.condition
        }
    })
    return cond
})

</script>

<template>
    <div class="weaknesses-box mt-3">
        <div class="weaknesses-header d-flex">
            <p class="weaknesses-title text-white">WEAKNESSES</p>
            <p class="align-self-center ms-auto" v-if="condition">() = when {{ condition }}</p>
        </div>
        <table class="weaknesses-table table">
            <tr>
                <th>
                    <div class="d-flex align-items-center justify-content-center">
                        <img class="px-2" src="../../status/fire.png" alt="fire">
                        <i class="bi bi-star-fill stars-filled px-2" v-for="n in processedWeaknesses.fire.normal"></i>
                        <i class="bi bi-star-fill stars-empty px-2" v-for="m in 3-processedWeaknesses.fire.normal"></i>
                    </div> 
                </th>
                <th v-if="condition">
                    <div class="d-flex align-items-center justify-content-center">
                        <span class="parentheses">(</span>
                        <i class="bi bi-star-fill stars-filled px-2" v-for="n in processedWeaknesses.fire.cond"></i>
                        <i class="bi bi-star-fill stars-empty px-2" v-for="m in 3-processedWeaknesses.fire.cond"></i>
                        <span class="parentheses">)</span>
                    </div> 
                </th>
                <th>
                    <div class="d-flex align-items-center justify-content-center">
                        <img class="px-2" src="../../status/poison.png" alt="poison">
                        <i class="bi bi-star-fill stars-filled px-2" v-for="n in processedWeaknesses.poison.normal"></i>
                        <i class="bi bi-star-fill stars-empty px-2" v-for="m in 3-processedWeaknesses.poison.normal"></i>
                    </div>
                </th>
            </tr>
            <tr>
                <th>
                    <div class="d-flex align-items-center justify-content-center">
                        <img class="px-2" src="../../status/water.png" alt="water">
                        <i class="bi bi-star-fill stars-filled px-2" v-for="n in processedWeaknesses.water.normal"></i>
                        <i class="bi bi-star-fill stars-empty px-2" v-for="m in 3-processedWeaknesses.water.normal"></i>
                    </div>
                </th>
                <th v-if="condition">
                    <div class="d-flex align-items-center justify-content-center">
                        <span class="parentheses">(</span>
                        <i class="bi bi-star-fill stars-filled px-2" v-for="n in processedWeaknesses.water.cond"></i>
                        <i class="bi bi-star-fill stars-empty px-2" v-for="m in 3-processedWeaknesses.water.cond"></i>
                        <span class="parentheses">)</span>
                    </div> 
                </th>
                <th>
                    <div class="d-flex align-items-center justify-content-center">
                        <img class="px-2" src="../../status/sleep.png" alt="sleep">
                        <i class="bi bi-star-fill stars-filled px-2" v-for="n in processedWeaknesses.sleep.normal"></i>
                        <i class="bi bi-star-fill stars-empty px-2" v-for="m in 3-processedWeaknesses.sleep.normal"></i>
                    </div>
                </th>                
            </tr>
            <tr>
                <th>
                    <div class="d-flex align-items-center justify-content-center">
                        <img class="px-2" src="../../status/thunder.png" alt="thunder">
                        <i class="bi bi-star-fill stars-filled px-2" v-for="n in processedWeaknesses.thunder.normal"></i>
                        <i class="bi bi-star-fill stars-empty px-2" v-for="m in 3-processedWeaknesses.thunder.normal"></i>
                    </div>
                </th>
                <th v-if="condition">
                    <div class="d-flex align-items-center justify-content-center">
                        <span class="parentheses">(</span>
                        <i class="bi bi-star-fill stars-filled px-2" v-for="n in processedWeaknesses.thunder.cond"></i>
                        <i class="bi bi-star-fill stars-empty px-2" v-for="m in 3-processedWeaknesses.thunder.cond"></i>
                        <span class="parentheses">)</span>
                    </div> 
                </th>
                <th>
                    <div class="d-flex align-items-center justify-content-center">
                        <img class="px-2" src="../../status/paralysis.png" alt="paralysis">
                        <i class="bi bi-star-fill stars-filled px-2" v-for="n in processedWeaknesses.paralysis.normal"></i>
                        <i class="bi bi-star-fill stars-empty px-2" v-for="m in 3-processedWeaknesses.paralysis.normal"></i>
                    </div>
                </th>                
            </tr>
            <tr>
                <th>
                    <div class="d-flex align-items-center justify-content-center">
                        <img class="px-2" src="../../status/ice.png" alt="ice">
                        <i class="bi bi-star-fill stars-filled px-2" v-for="n in processedWeaknesses.ice.normal"></i>
                        <i class="bi bi-star-fill stars-empty px-2" v-for="m in 3-processedWeaknesses.ice.normal"></i>
                    </div>
                </th>
                <th v-if="condition">
                    <div class="d-flex align-items-center justify-content-center">
                        <span class="parentheses">(</span>
                        <i class="bi bi-star-fill stars-filled px-2" v-for="n in processedWeaknesses.ice.cond"></i>
                        <i class="bi bi-star-fill stars-empty px-2" v-for="m in 3-processedWeaknesses.ice.cond"></i>
                        <span class="parentheses">)</span>
                    </div> 
                </th>
                <th>
                    <div class="d-flex align-items-center justify-content-center">
                        <img class="px-2" src="../../status/blast.png" alt="blast">
                        <i class="bi bi-star-fill stars-filled px-2" v-for="n in processedWeaknesses.blast.normal"></i>
                        <i class="bi bi-star-fill stars-empty px-2" v-for="m in 3-processedWeaknesses.blast.normal"></i>
                    </div>
                </th>                
            </tr>
            <tr>
                <th>
                    <div class="d-flex align-items-center justify-content-center">
                        <img class="px-2" src="../../status/dragon.png" alt="dragon">
                        <i class="bi bi-star-fill stars-filled px-2" v-for="n in processedWeaknesses.dragon.normal"></i>
                        <i class="bi bi-star-fill stars-empty px-2" v-for="m in 3-processedWeaknesses.dragon.normal"></i>
                    </div>
                </th>
                <th v-if="condition">
                    <div class="d-flex align-items-center justify-content-center">
                        <span class="parentheses">(</span>
                        <i class="bi bi-star-fill stars-filled px-2" v-for="n in processedWeaknesses.dragon.cond"></i>
                        <i class="bi bi-star-fill stars-empty px-2" v-for="m in 3-processedWeaknesses.dragon.cond"></i>
                        <span class="parentheses">)</span>
                    </div> 
                </th>
                <th>
                    <div class="d-flex align-items-center justify-content-center">
                        <img class="px-2" src="../../status/stun.png" alt="stun">
                        <i class="bi bi-star-fill stars-filled px-2" v-for="n in processedWeaknesses.stun.normal"></i>
                        <i class="bi bi-star-fill stars-empty px-2" v-for="m in 3-processedWeaknesses.stun.normal"></i>
                    </div>
                </th>                
            </tr>
        </table>
    </div>
</template>

<style>

    .weaknesses-box {
        background-color: #1f1f1f;
        border-radius: 6px;
    }

    .weaknesses-header {
        padding: 0.5rem 1.5rem;
        border-bottom: 1px solid #272727;
    }

    .weaknesses-title {
        font-size: 1.5rem;
        letter-spacing: 2px;
        padding-top: 1rem;
    }

    .weaknesses-table {
        padding: 1.5rem !important;
    }

    .parentheses {
        font-size: 1.5rem;
        color: #6c757d;
    }

    .bi-star-fill {
        font-size: 1.5rem;
    }

    .stars-filled {
        color: rgb(199, 168, 33);
    }

    .stars-empty {
        color: #636c72;
    }

</style>