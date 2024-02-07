<script>
export default {
    name: 'FormImput',
    data: () => ({
        currentValue: ''
    }),
    emits: ['value-change']
}
</script>

<template>
    <input type="text" class="form-control" placeholder="Cerca..." v-model.trim="currentValue"
        @keyup="$emit('value-change', currentValue)">
</template>
  
<style lang="scss"></style>