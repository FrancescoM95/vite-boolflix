<script>
export default {
    name: 'FormInput',
    data: () => ({
        currentValue: ''
    }),
    emits: ['value-change']
}
</script>

<template>
    <input type="text" class="form-control" placeholder="Cerca..." v-model.trim="currentValue"
        @keyup="$emit('value-change', currentValue)" autofocus>
</template>
  
<style lang="scss"></style>