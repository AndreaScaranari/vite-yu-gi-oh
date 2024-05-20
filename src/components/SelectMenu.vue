<script>
export default {
    name: "SelectMenu",
    data: () => ({ selectedOption: "" }),
    props: {
        defaultLabel: String,
        defaultValue: String,
        options: Array
    },
    emits: ["option-change"]
};
</script>

<template>
    <select v-model="selectedOption" @change="$emit('option-change', selectedOption)">
        <option :value="defaultValue || ''">{{ defaultLabel || "---" }}</option>
        <option :value="option.value" v-for="option in options" :key="option.id">{{ option.label }}</option>
    </select>
</template>

<style lang="scss" scoped>
select {
    padding: 0.5rem 1rem;
    border-radius: 10px;
}
</style>