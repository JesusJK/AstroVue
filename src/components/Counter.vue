<script setup>
import { ref } from 'vue';

let number = ref(0);
let time = ref(0);
let interval;
let ok = false;

function add() {
    if (number.value == 0) {
        interval = setInterval(() => {
            time.value++
        }, 1000);
    }
    number.value++

    if (number.value == 50) {
        clearInterval(interval);
    }
}


</script>

<template>

    <div class="mb-40">

        <div @click="add()"
            class="flex mt-80 items-center my-2 mx-auto justify-center w-24 h-24 roundead hover:bg-blue-500 text-white bg-blue-400">
            {{ number }}
        </div>
        <div v-show="number > 0"
            class="flex items-center my-2 mx-auto justify-center w-32 h-24 roundead border-gray-500 border-2 text-white bg-blue-400">
            {{ time }}
        </div>

        <div v-if="number == 0"
            class="w-max mb-48 h-20 mx-auto py-1 px-2 rounded flex items-center text-white bg-blue-400">
            Dale click 🐱‍👤
        </div>

        <div v-show="number >= 50 && time >= 10"
            class="flex items-center my-2 mx-auto justify-center w-52 h-24 roundead bg-red-600 text-white">Muy Lento
            🐢</div>
        <div v-show="number >= 50 && time == 9"
            class="flex items-center my-2 mx-auto justify-center w-52 h-24 roundead bg-yellow-400 text-white">Promedio
            🚶‍♂️</div>
        <div v-show="number >= 50 && time <= 8"
            class="flex items-center my-2 mx-auto justify-center w-52 h-24 roundead bg-green-500 text-white">Cheetos alv
            🐆</div>




    </div>
</template>