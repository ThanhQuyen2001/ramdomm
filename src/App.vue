<template>
    <div class="container mx-auto">
        <div class="screen-game flex-center">
            <div
                class="card mb-3 flex-center"
                v-for="(item, index) in data"
                :key="index"
                @click="changeOpen(index)"
            >
                <h3 v-if="item.open" class="text-white">
                    {{item.value}}. {{ item.name }}
                </h3>
                <h3 v-else class="text-white">Click to open</h3>
            </div>
        </div>
        <button @click="randomName()">Ngẫu nhiên tên</button>
        <button @click="handleBeforeStart()">Bắt đầu</button>
    </div>
</template>

<script setup>
import { ref } from 'vue'
const counter = ref(1)
const numberFind = ref(0)
numberFind.value = Math.floor(Math.random() * 8) + 1
const data = ref([
    {
        value: 1,
        open: false,
        name: '',
    },
    {
        value: 2,
        open: false,
        name: '',
    },
    {
        value: 3,
        open: false,
        name: '',
    },
    {
        value: 4,
        open: false,
        name: '',
    },
    {
        value: 5,
        open: false,
        name: '',
    },
    {
        value: 6,
        open: false,
        name: '',
    },
    {
        value: 7,
        open: false,
        name: '',
    },
    {
        value: 8,
        open: false,
        name: '',
    },
    {
        value: 9,
        open: false,
        name: '',
    },
])
const names = ref([
    'Nhi',
    'Trang',
    'Vui',
    'Quyền',
    'Bửu',
    'Vũ',
    'Nhật',
    'Thiên',
    'Q.Anh',
])
const randomName = () => {
    names.value.sort(() => {
        const randomNumber = Math.random() < 0.5 ? -1 : 1
        return randomNumber
    })
    data.value = data.value.map((item, index) => {
        return {
            ...item,
            name: names.value[index],
            open: true,
        }
    })
}
randomName()
const handleBeforeStart = () => {
    counter.value = 1
    data.value.sort(() => {
        const randomNumber = Math.random() < 0.5 ? -1 : 1
        return randomNumber
    })
    data.value = data.value.map(item => {
        return {
            ...item,
            open: false,
        }
    })
}
const changeOpen = index => {
    if(data.value[index].open === true) return

    data.value[index].open = true
    data.value[index].value = counter.value
    counter.value++
}
</script>
