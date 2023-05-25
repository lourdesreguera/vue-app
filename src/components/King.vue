<script setup>
import { computed } from '@vue/reactivity';
import { kings } from '../datos'

const props = defineProps(['kingNumber'])
const img = computed(() =>
    'https://www.html6.es/img/rey_' + kings[props.kingNumber].name + '.png'
)
const name = computed(() => kings[props.kingNumber].name.charAt(0).toUpperCase() + kings[props.kingNumber].name.toLowerCase().slice(1))
</script>

<template>
    <main>
        <h1>Cena {{ kingNumber + 1 }} con el rey <span class="name">{{ name }}</span></h1>
        <h2>Precio: <span class="price">{{ kings[kingNumber].price }}€</span></h2>
        <div v-if="kings[kingNumber].weekends" class="tag weekends">
            <p>(Solo fines de semana)</p>
        </div>
        <div v-else class="tag noWeekends">
            <p>(De lunes a domingo)</p>
        </div>
        <div v-if="kings[kingNumber].price < 100" class="dto">
            <p>Ahora un 10% dto: <span class="dtoPrice">{{ (kings[kingNumber].price * 0.9).toFixed(2) }}€</span></p>
            <img src="../assets/oferta.jpg" alt="Oferta" class="dtoImg">
        </div>
        <img :src="img" :alt="name" class="kingImg">
    </main>
</template>

<style scoped>

.kingImg {
    margin: 1.5rem 0 3rem 0;
}

h1 {
    font-size: 1.5rem;
    font-weight: 600;
}

h2 {
    font-size: 1.25rem;
    font-weight: 600;
}

.name {
    color: rgb(2, 114, 2);
    font-size: 1.75rem;
    font-weight: 600;

}

.price {
    color: rgb(2, 114, 2);
    font-size: 1.5rem;
    font-weight: 600;

}

.tag {
    background-color: rgb(2, 114, 2);
    padding: 0.25rem 1rem;
    border-radius: 5px;
    color: #fff;
}

.noWeekends {
    background-color: rgb(2, 114, 2);
}

.weekends {
    background-color: rgb(243, 32, 0);
}

.dto {
    margin-top: 1.5rem;
    display: flex;
    align-items: center;
    justify-content: center;
}

.dtoPrice {
    color: rgb(2, 114, 2);
    font-size: 1.25rem;
}

.dtoImg {
    width: 4rem;
    margin-left: 0.5rem;
}
</style>