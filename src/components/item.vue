<template>

    <tr class="my-table" v-bind:class="{innactive:i.completed}">

        <td class="my-table_item">
            <input type="checkbox" v-on:change="$emit('toggleCheckbox', i)" />
            {{i.id}}
        </td>
        <td class="my-table_item">{{i.name}}</td>
        <td class="my-table_item">{{i.birth}}
            <button v-on:click="$emit('remove-item', i.name)">Remove</button>
        </td>
    </tr>

</template>

<script>
    export default {
        props: ['i']
    }
</script>

<style>
    /*.my-table {*/
    /*    display: flex;*/
    /*    justify-content: space-between;*/
    /*}*/

    /*.my-table_item {*/
    /*    border: 1px solid orangered;*/
    /*}*/


    td, th {
        border: 1px solid #dddddd;
        text-align: left;
        padding: 8px;
    }

    button{
        margin-left: 20px
    }

    .innactive {
        background-color: #757575;
    }
</style>