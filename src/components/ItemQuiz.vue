<template>
    <div class="item-quiz">
        <p>{{ props.title }}</p>
        {{ selectedIndex }}
        <select v-model="selectedOption" @change="seleccionarRespuesta">
            <option v-for="(option, index) in props.options" :key="index" :value="index + 1">
                {{ option }}
            </option>
        </select>
    </div>
</template>

<script setup lang="ts">
import type { IQuiz } from '@/interface/IQuiz';
import { defineProps, ref } from 'vue';

const props = defineProps<IQuiz>();
const selectedOption = ref<number | null>(null);
const selectedIndex = ref<number | null>(null);

const seleccionarRespuesta = () => {
    selectedIndex.value = selectedOption.value !== null ? selectedOption.value - 1 : null;
};
</script>