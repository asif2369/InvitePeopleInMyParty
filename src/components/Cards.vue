<script setup lang="ts">
enum GENDER {
    MALE,
    FEMALE,
}
defineProps<{
    memberSingle: {
        id: number;
        name: string;
        sex: GENDER;
    };
}>();
</script>

<template>
    <div
        :style="{
            backgroundColor:
                memberSingle.sex === GENDER.MALE ? '#226E6F' : '#6A1102',
        }"
    >
        <!-- #226E6F' : '#6A1102' -->
        {{ memberSingle.name }}
    </div>
</template>

<style scoped>
div {
    background-color: lightblue;
    border-radius: 5px;
    margin-top: 0.5rem;
    text-align: center;
    padding: 0.5rem;
    color: #fff;
    font-size: 1.5rem;
}
</style>
