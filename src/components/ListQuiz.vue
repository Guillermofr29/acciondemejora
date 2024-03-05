<template>
    <div>
        {{ CorrectAnswers.map(x => x.answer) }}
        <h1>Acción de mejora</h1>
        <ul>
            <ItemQuiz v-bind="quest" v-for="(quest, index) in Quests" :id="index" :key="index" />
        </ul>
    </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';
import ItemQuiz from './ItemQuiz.vue';
import QuizData from '@/data/QuizData';

const Quests = ref([...QuizData]);

const CorrectAnswers = computed(() => Quests.value.map(x => ({ answer: x.answer })));
</script>


<style scoped>
h1 {
    text-align: center;
}

div {
    margin: 15px 0;
}
</style>