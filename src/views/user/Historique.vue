<template>
    <div class="block">
        <div class="calcul">
            <div class="user__main__title">
                <h1>HISTORIQUE</h1>
                <hr>
            </div>
            <div class="main__table">
                <table v-if="userCalculation.length !== 0">
                    <thead>
                        <tr>
                            <th> Jours </th>
                            <th> Heures </th>
                            <th> Calculs </th>

                        </tr>
                    </thead>
                    <tbody v-if="userCalculation" v-for="element in userCalculation">
                        <tr v-if="element.id_calculation == userData._id">
                            <td>{{ element.date }}</td>
                            <td>{{ element.hours }}</td>
                            <td>{{ element.calculation }}</td>
                        </tr>
                    </tbody>

                </table>
            </div>
        </div>
    </div>
</template>

<script lang="ts" setup>
import { userOpeationStore } from '@/stores/operation'
import { useUserStore } from '@/stores/user'
import { storeToRefs } from 'pinia'


const { userData } = storeToRefs(useUserStore())
const { user } = useUserStore()
user()

const { userCalculation } = storeToRefs(userOpeationStore())
console.log(userCalculation);

const { getCalculation } = userOpeationStore()
getCalculation()


</script>

<style scoped>
.main__table {
    overflow-x: auto;
    padding-bottom: 15px;
}

table {
    width: 100%;
    border: 1px solid var(--base-color);
    /* border-collapse: collapse; */
}

thead {
    width: 100%;
}

tbody {
    width: 100%;
}

thead th {
    text-align: left;
    padding: 10px 5px;
    background-color: var(--base-color);
    color: var(--color-white);
    font-size: 18px;
    font-weight: bold;
}

tbody tr td {
    padding: 5px;
    letter-spacing: 2px;
    background-color: var(--color-gray-tertiary);
    color: var(--base-color);
    font-weight: bold;
    white-space: nowrap;
}

.user__info div {
    display: flex;
    gap: 15px;
}
.calcul {
    display: flex;
    flex-direction: column;
    gap: 15px;
}
</style>