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
                    {{ item.name }}
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
const stop = ref(false)
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
    {
        value: 10,
        open: false,
        name: '',
    },
])
const names = ref([
    'Nhi',
    'Nhật',
    'Trang',
    'Vui',
    'Quyền',
    'Bửu',
    'Nhật',
    'Vũ',
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
    stop.value = false
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
    if (stop.value === true) return
    data.value[index].open = true
    stop.value = true
}
</script>
