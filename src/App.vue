<template>
    <div id="app">

        <tabula
                v-bind:arr="list"
                v-on:sort-id="SortId"
                v-on:sort-name="SortName"
                v-on:sort-date="SortBirth"
                v-on:remove-item="Removeitem"
                @toggleCheckbox="ToggleCheckbox"
        />
    </div>

</template>

<script>
    import tabula from '@/components/tabula'

    export default {
        name: 'App',
        data() {
            // var a = new Date(1994, 10, 18, 8, 23, 0)
            // var b = new Date(1991, 11, 17, 7, 29, 0)
            // var c = new Date(1996, 6, 19, 5, 27, 0)
            // var d = new Date(1993, 8, 16, 3, 24, 0)
            // var e = new Date(1999, 5, 11, 8, 24, 0)
            // var f = new Date(1987, 3, 12, 3, 29, 44)
            return {
                list: [
                    {id: 3, name: 'Cris', birth: "March 12, 2014", completed: false},
                    {id: 2, name: 'Bob', birth: "March 12, 2074", completed: false},
                    {id: 4, name: 'David', birth: "March 12, 2084", completed: false},
                    {id: 5, name: 'Eva', birth: "March 12, 2004", completed: false},
                    {id: 1, name: 'Fray', birth: "March 13, 2014", completed: false},
                    {id: 6, name: 'Ann', birth: "March 12, 2019", completed: false}
                ],

            }
        },
        components: {
            tabula
        },
        watch: {
            list: function (val) {
                console.log('val list', val)
            }},
        methods: {
            SortId(id) {

                this.list = this.list.sort(function (a, b) {
                    return a.id - b.id
                })
            },
            SortName(name) {
                this.list = this.list.sort(function (a, b) {
                    var nameA = a.name, nameB = b.name
                    if (nameA < nameB)
                        return -1
                    if (nameA > nameB)
                        return 1
                    return 0
                })
            },
            SortBirth() {
                console.log('jjjjjj')
                this.list = this.list.sort(function (a, b) {

                    var dateA = new Date(a.birth), dateB = new Date(b.birth)
                    console.log(dateA, dateB)
                    return dateA - dateB

                })
            },
            Removeitem(name) {
                this.list = this.list.filter(t => t.name !== name)
            },
            ToggleCheckbox(i) {
                console.log('i', i)
                i.completed = !i.completed
            }
        }
    }
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
