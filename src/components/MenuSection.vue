<template>
    <div class="ct-btns">
        <button 
        v-for="category in categories" 
        :key="category"
        @click="filterItems(category)"
        :class="{'active' : selectedCategory === category}">
            {{ category }}
        </button>
    </div>
    <div class="menu-container">
        <div class="menu-item" 
        v-for="item in filteredItems" 
        :key="item.id"
        @click="router.push(`/menu/${menu.id}`)">
            <div>
                <img :src="item.image" alt="Menu Item">
                <div class="title">
                    <div>{{ item.name }}</div>
                    <div>{{ item.price }}</div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import menu from "../menu.json";
import categories from "../category.json";
import { useRoute, Router } from "vue-router";

export default{
    name: 'MenuSection',
    data(){
        return{
            menu,
            categories,
            selectedCategory: 'All'
        }
    },
    computed: {
        filteredItems(){
            if(this.selectedCategory === "All") return this.menu;
            return this.menu.filter(item => item.category === this.selectedCategory);
        }
    },
    methods: {
        filterItems(category){
            this.selectedCategory = category;
        }
    }
}
</script>
<style>
.ct-btns{
    display: flex;
    gap: 0.8rem;
  }

  button {
  background-color: transparent;
  color: #fff;
  font-family: 'Poppins', sans-serif;
  border: none;
  cursor: pointer;
  font-size: 1.5rem;
  }

  
  button:hover  {
    background-color: rgb(196, 109, 196);
    border-radius: 15px;
    padding: 12px 8px;
  }
  
  .active {
    background-color: rgb(196, 109, 196);
    border-radius: 15px;
    padding: 12px 8px;
}

  .ct-btns{
    display: flex;
    flex-direction: row;
    gap: 2rem;
  }

  .menu-container {
    display: grid;
    grid-template-columns: repeat(3, 1fr); /* Three columns */
    grid-column-gap: 20px; /* Adjust gap between columns */
    grid-row-gap: 20px; /* Adjust gap between rows */
    margin-top: 1rem;
  }
  .menu-item{
    background-color: rgb(196, 109, 196);
    padding: 0.5rem;
  }
  .title{
    display: flex;
    flex-direction: row;
    width: 100%;    
    justify-content: space-around;
    padding: 25px;
}
  
  .menu-item {
  cursor: pointer;
  }
</style>