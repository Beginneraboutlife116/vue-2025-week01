<script setup>
import { ref } from 'vue'

const items = ref([
  {
    id: 1,
    name: '珍珠奶茶',
    description: '香濃奶茶搭配QQ珍珠',
    price: 50,
    stock: 20,
    isEditing: false,
  },
  {
    id: 2,
    name: '冬瓜檸檬',
    description: '清新冬瓜配上新鮮檸檬',
    price: 45,
    stock: 18,
    isEditing: false,
  },
  {
    id: 3,
    name: '翡翠檸檬',
    description: '綠茶與檸檬的完美結合',
    price: 55,
    stock: 34,
    isEditing: false,
  },
  {
    id: 4,
    name: '四季春茶',
    description: '香醇四季春茶，回甘無比',
    price: 45,
    stock: 10,
    isEditing: false,
  },
  {
    id: 5,
    name: '阿薩姆奶茶',
    description: '阿薩姆紅茶搭配香醇鮮奶',
    price: 50,
    stock: 25,
    isEditing: false,
  },
  {
    id: 6,
    name: '檸檬冰茶',
    description: '檸檬與冰茶的清新組合',
    price: 45,
    stock: 20,
    isEditing: false,
  },
  {
    id: 7,
    name: '芒果綠茶',
    description: '芒果與綠茶的獨特風味',
    price: 55,
    stock: 18,
    isEditing: false,
  },
  {
    id: 8,
    name: '抹茶拿鐵',
    description: '抹茶與鮮奶的絕配',
    price: 60,
    stock: 20,
    isEditing: false,
  },
])

function addItem(id) {
  const item = items.value.find((item) => item.id === id)

  if (item) {
    item.stock++
  }
}

function removeItem(id) {
  const item = items.value.find((item) => item.id === id)

  if (item && item.stock > 0) {
    item.stock--
  }
  if (item && item.stock < 0) {
    item.stock = 0
  }
}

function clickEditButton(id) {
  const item = items.value.find((item) => item.id === id)

  if (item) {
    item.isEditing = !item.isEditing
  }
}

function resetChanges() {
  items.value = [
    {
      id: 1,
      name: '珍珠奶茶',
      description: '香濃奶茶搭配QQ珍珠',
      price: 50,
      stock: 20,
      isEditing: false,
    },
    {
      id: 2,
      name: '冬瓜檸檬',
      description: '清新冬瓜配上新鮮檸檬',
      price: 45,
      stock: 18,
      isEditing: false,
    },
    {
      id: 3,
      name: '翡翠檸檬',
      description: '綠茶與檸檬的完美結合',
      price: 55,
      stock: 34,
      isEditing: false,
    },
    {
      id: 4,
      name: '四季春茶',
      description: '香醇四季春茶，回甘無比',
      price: 45,
      stock: 10,
      isEditing: false,
    },
    {
      id: 5,
      name: '阿薩姆奶茶',
      description: '阿薩姆紅茶搭配香醇鮮奶',
      price: 50,
      stock: 25,
      isEditing: false,
    },
    {
      id: 6,
      name: '檸檬冰茶',
      description: '檸檬與冰茶的清新組合',
      price: 45,
      stock: 20,
      isEditing: false,
    },
    {
      id: 7,
      name: '芒果綠茶',
      description: '芒果與綠茶的獨特風味',
      price: 55,
      stock: 18,
      isEditing: false,
    },
    {
      id: 8,
      name: '抹茶拿鐵',
      description: '抹茶與鮮奶的絕配',
      price: 60,
      stock: 20,
      isEditing: false,
    },
  ]
}
</script>

<template>
  <table>
    <thead>
      <tr>
        <th scope="col">品項</th>
        <th scope="col">描述</th>
        <th scope="col">價格</th>
        <th scope="col">庫存</th>
        <th scope="col">操作</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="item in items" :key="item.id">
        <td>
          <input v-show="item.isEditing" v-model="item.name" type="text" />
          <span v-show="!item.isEditing">{{ item.name }}</span>
        </td>
        <td>
          <input v-show="item.isEditing" v-model="item.description" type="text" />
          <small v-show="!item.isEditing">{{ item.description }}</small>
        </td>
        <td>
          <input v-show="item.isEditing" v-model="item.price" type="number" />
          <span v-show="!item.isEditing">{{ item.price }}</span>
        </td>
        <td>
          <button @click="removeItem(item.id)">-</button>
          {{ item.stock }}
          <button @click="addItem(item.id)">+</button>
        </td>
        <td>
          <button v-show="item.isEditing" @click="clickEditButton(item.id)">儲存</button>
          <button v-show="!item.isEditing" @click="clickEditButton(item.id)">修改</button>
        </td>
      </tr>
    </tbody>
  </table>
  <button @click="resetChanges">復原</button>
</template>

<style scoped></style>
