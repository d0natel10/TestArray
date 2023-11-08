<script setup>
import { ref} from 'vue'

const tank = ref([
  { id: 1, type: 'mango', price: 35 },
  { id: 2, type: 'mango', price: 77 },
  { id: 3, type: 'potato', price: 84 },
  { id: 4, type: 'potato', price: 25 },
  { id: 5, type: 'mango', price: 33 },
  { id: 6, type: 'apple', price: 50 },
  { id: 7, type: 'mango', price: 89 },
  { id: 8, type: 'apple', price: 60 },
  { id: 9, type: 'mango', price: 51 },
  { id: 10, type: 'apple', price: 82 },
]);

const modifyOriginalArray = () => { //Функция для изменения массива Tank
  tank.value = tank.value.filter(item => item.type !== 'potato').map(item => {
    if (item.type === 'apple') {
      return { ...item, price: item.price * 2 };
    } else {
      return item;
    }
  });
};

const createNewArray = () => { //Функция для создания нового массива
  const newArray = tank.value.filter(item => item.type !== 'mango').map(item => {
    if (item.type === 'apple') {
      return { ...item, price: item.price * 3 };
    } else {
      return item;
    }
  });
  return newArray;
};

const modifiedTank = createNewArray(); //Новый массив
modifyOriginalArray(); //Вызов функции, которая изменяет массив
</script>

<template> 
<p>Вывод нового массива: </p>
  <ul>
    <li v-for="item in modifiedTank" :key="item.id">
      {{ item.id }} - Type: {{ item.type }}, Price: {{ item.price }} 
    </li>
  </ul>
<p>Вывод изменненного массива Tank: </p>
  <ul>
    <li v-for="item in tank" :key="item.id">
      {{ item.id }} - Type: {{ item.type }}, Price: {{ item.price }} 
    </li>
  </ul>
</template>

