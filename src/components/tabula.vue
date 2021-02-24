<template>
    <table class="common-table">
        <tr>
            <th class="date-name" v-on:click="$emit('sort-id', arr.id)">Number</th>
            <th class="date-name" v-on:click="$emit('sort-name', arr.name)">Name</th>
            <th class="date-name" v-on:click="$emit('sort-date')">Date</th>
        </tr>
        <item
                v-for="i of arr"
                :key="i.id"
                v-bind:i="i"
                v-on:remove-item="Removeitem"
                @toggleCheckbox="ToggleCheckbox"
        />
    </table>
</template>

<script>
    import item from '@/components/item'

    export default {
        props: ['arr'],
        components: {item},
        methods: {
            Removeitem(name) {
                this.$emit('remove-item', name)
            },
            ToggleCheckbox(i) {
                this.$emit('toggleCheckbox', i)
            }
        }
    }
</script>

<style scoped>
    table {
        font-family: arial, sans-serif;
        border-collapse: collapse;
        width: 40%;
        margin: 50px auto;
    }

    td, th {
        border: 1px solid #dddddd;
        text-align: left;
        padding: 8px;
    }

    .date-name{
        cursor: pointer;
    }
</style>