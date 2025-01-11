<script lang="ts" setup>
    // const props = defineProps<{ isChecked?: boolean }>();
    const props = withDefaults(
        defineProps<{
            isChecked: boolean
        }>(),
        {  isChecked: false
        }
    )
</script>

<template>
    <label :class="{ checked: isChecked }">
        <input 
            type="checkbox" 
            :checked="isChecked"
            @change="$emit('toggle')"
            />
        <slot></slot>
    </label>
</template>

<style scoped>
    label {
        cursor: pointer;
    }
    .checked {
        text-decoration: line-through;
    }
</style>