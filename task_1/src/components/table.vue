<template>
    <div>
        <h1>Response:</h1>
        <table>
            <tr v-for="item of table" :key="item.id">
                <td>{{ item.id}}</td>
                <td>{{ item.name }}</td>
                <td>{{ item.age }}</td>
                <td>{{ item.phone }}</td>
            </tr>
        </table>
    </div>
</template>

<script>
    export default{
        name: "Table",
        data(){
            return {
                table: [],
                URL: "https://bitbucket.org/GuestOne/goodline-test-task/raw/aa16bc87df8355deef678f4b69a2b6d9fe0f9832/frontend/data.json"
            }
        },
        mounted(){
            fetch(this.URL)
                .then(resultJSON => resultJSON.json())
                .then(data => {
                    for (let el of data){
                        this.table.push(el)
                    }
                });
        }
    }
</script>

<style lang="sass">
    table
        border: 3px solid black
    td
        border: 1px solid black
        padding: 0 5px
</style>