<script setup lang="ts">
import { computed, ref } from "vue";
import Cards from "./components/Cards.vue";

enum GENDER {
    MALE,
    FEMALE,
}

interface Member {
    id: number;
    name: string;
    sex: GENDER;
}

const name = ref("");
const gender = ref(GENDER.MALE);
const memberArr = ref<Member[]>([]);

const addMemberFunc = (): void => {
    if (name.value) {
        memberArr.value.push({
            id: Math.floor(Math.random() * 1000000),
            name: name.value,
            sex: gender.value,
        });
    }

    name.value = "";
    gender.value = GENDER.MALE;
};

const count = computed<{
    female: number;
    male: number;
}>(() => {
    return memberArr.value.reduce(
        (countObj, c) => {
            if (c.sex === GENDER.MALE) {
                return {
                    ...countObj,
                    male: countObj.male + 1,
                };
            }

            return {
                ...countObj,
                female: countObj.female + 1,
            };
        },
        { male: 0, female: 0 }
    );
});
</script>

<template>
    <main>
        <div class="container">
            <h1>People invited to my Party</h1>
            <p>Enter <b>name</b>, select <b>gender</b> and hit <b>enter</b></p>
            <br />
            <div class="input-container">
                <input
                    v-model="name"
                    type="text"
                    placeholder="Name..."
                    @keypress.enter="addMemberFunc"
                />

                <select v-model="gender" @keypress.enter="addMemberFunc">
                    <option :value="GENDER.MALE">Male</option>
                    <option :value="GENDER.FEMALE">Female</option>
                </select>
            </div>

            <Cards v-for="m in memberArr" :key="m.id" :memberSingle="m" />

            <div v-if="memberArr.length > 0" class="total-count">
                <br />
                <hr />
                <p>Male = {{ count.male }}</p>
                <p>Female = {{ count.female }}</p>
            </div>
        </div>
    </main>
</template>

<style scoped>
main {
    display: flex;
    height: 100vh;
    align-items: center;
    justify-content: center;
    background-color: #e3f2ff;
}

h1 {
    font-size: 3rem;
    font-weight: bold;
}

h3 {
    color: #226e6f;
    font-size: 1.75rem;
    border-bottom: 1px solid #222;
    padding-top: 5rem;
}

h4 {
    color: #226e6f;
    font-size: 1.25rem;
    border-bottom: 1px solid #222;
    padding-top: 5rem;
}

b {
    font-weight: bold;
}

.container {
    padding: 3rem;
}

input,
select {
    width: 100%;
    padding: 1rem;
    margin-bottom: 0.5rem;
    font-size: 1.5rem;
    border: 1px solid #222;
}
</style>
