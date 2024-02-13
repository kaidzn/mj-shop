<template>
    <div class="container">
        <img :src="menuItem.image" alt="Item Image">
        <div class="info">
            <div class="title">
                <p>{{ menuItem.name }}</p>
                <p>{{ menuItem.price }}</p>
            </div>
            <p>{{ menuItem.info }}</p>
        </div>
    </div>
</template>
<script>
import { useRoute } from 'vue-router';
import { onMounted, ref } from 'vue';
import menuItems from "../menu.json"

const route = useRoute()
const menuItem = ref(null)
const {id} = route.params

onMounted(() => {
    const m = menuItems.find(m => m.id === parseInt(id));
    menuItem.value = m
})
</script>

<style>

</style>