<template>
  <h2>ItemList</h2>
  <div v-for="item in items" :key="item.name">
    <div class="item" :class="{ over500: item.price >= 500 }">
      <div class="name">名前: {{ item.name }}</div>
      <div class="price">価格: {{ item.price }}</div>
    </div>
  </div>
  <div>
    <label>
      名前
      <input v-model="newItemName" type="text" />
    </label>
    <label>
      価格
      <input v-model="newItemPrice" type="number" />
    </label>
    <button @click="addItem">add</button>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup(){
    const items = ref([
        { name: "卵", price: 100 },
        { name: "リンゴ", price: 160 },
    ]);

    const newItemName = ref("");
    const newItemPrice = ref(0);
    const addItem = () => {
      if(newItemName.value != "" && newItemPrice.value != 0){
        items.value.push({ name: newItemName.value, price: newItemPrice.value });
      }
    };
    return { items, newItemName, newItemPrice, addItem };
  },
};
</script>

<style>
.over500{
    color: red;
}
</style>