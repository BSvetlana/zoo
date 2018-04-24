<template>
    <div class="w-100 p-3">
        <div class="col-md-auto">
            <table class="table">
                <thead class="bg-secondary text-white">
                <tr>
                    <th scope="col">Animal</th>
                    <th scope="col">Name</th>
                    <th scope="col">Birth</th>
                    <th>&nbsp;</th>
                </tr>
                </thead>
                <tbody>
                <tr v-for="(animal, index) in animals" :key="index">
                    <td>{{ animal.kind }}</td>
                    <td>{{ animal.name }}</td>
                    <td  v-if="animal.dateOfBrth === ''">Nepoznat</td>
                    <td v-else>{{ animal.dateOfBrth }}</td>
                    <td><button class="btn btn-secondary btn-sm" @click="removeAnimal(index)">Remove</button></td>
                </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
    export default {
        name: "AnimalList",
        data(){
            return {
                animals: [
                    {kind: 'dog', name: 'Rex', dateOfBrth: 2017-10-18},
                    {kind: 'cat', name: 'Mio', dateOfBrth: 2017-4-18},
                    {kind: 'dog', name: 'Leo', dateOfBrth: 2016-10-18},
                    {kind: 'mouse', name: 'Miki', dateOfBrth: ''},
                    {kind: 'fish', name: 'Bub', dateOfBrth: 2014-10-18},
                ],
                seen(){
                    this.animal.dateOfBrth = 'Nepoznat';
                }
            }

        },
        methods: {
            removeAnimal(index){
                this.animals.splice(index,1)
            }
        }
    }

</script>

<style scoped>

</style>