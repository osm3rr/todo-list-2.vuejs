<script lang="ts" setup>
    import {ref } from 'vue';
    import type { Ref } from 'vue';
    import ListItem from './ListItem.vue';
    type Item = {
        title: string,
        checked?: boolean
    };

    const listItems: Ref<Item[]> = ref([
        {title: 'Aprender Vue 3', checked: true },
        {title: 'Hacer ejercicio', checked: false },
        {title: 'Leer un libro al mes'},
    ])

    const updateItem = (item: Item): void => {
        const updatedItem = findItemInList(item) 
        if (updatedItem) {
            toggleItemChecked(updatedItem);
        }
    }

    const findItemInList = (item: Item): Item | undefined => {
        return listItems.value.find(
            (itemInList:Item) => itemInList.title === item.title);
    }

    const toggleItemChecked = (item: Item): void => {
        item.checked = !item.checked;
    }

</script>

<template>
    <ul>
        <li :key="key" v-for="(item, key) in listItems">
            <ListItem :isChecked="item.checked" @toggle="updateItem(item)">
                {{item.title}}
            </ListItem>
        </li>
    </ul>
</template>

<style scoped>
    ul {
        list-style: none;
    }
    li {
        margin: 0.5rem 0;
    }
</style>