<template>
    <div class="w-100 p-3">
        <div class="col-sm-auto">
            <form @submit.prevent = "addAnimal">
                <div class="form-group">
                    <label for="kind">Animal</label>
                    <input type="text" class="form-control" id="kind" placeholder="Animal..." v-model="newAnimal.kind">
                </div>
                <div class="form-group">
                    <label for="name">Animal Name</label>
                    <input type="text" class="form-control" id="name" placeholder="Animal Name..." v-model="newAnimal.name">
                </div>
                <div class="form-group">
                    <label for="dateOfBrth">Email address</label>
                    <input type="number" class="form-control" id="dateOfBrth" aria-describedby="emailHelp" placeholder="Date of birth..." v-model="newAnimal.dateOfBrth">
                </div>
                <button type="submit" class="btn btn-secondary btn-sm">Add Animal</button>
            </form>
        </div>
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
                    <td>
                        <button class="btn btn-secondary btn-sm" @click="removeAnimal(index)">Remove</button>
                        <button class="btn btn-secondary btn-sm" @click="moveToTop(animal)">Move Top</button>
                    </td>
                </tr>
                </tbody>
            </table>
        </div>
        <div class="col-md-auto">
            <table class="table">
                <thead class="bg-secondary text-white">
                <tr>
                    <th scope="col">Surface Name</th>
                    <th scope="col">Surface</th>
                    <th>&nbsp;</th>
                </tr>
                </thead>
                <tbody>
                <tr v-for="(sectory, index) in sectors" :key="index">
                    <td>{{ sectory.name}}</td>
                    <td>{{ sectory.surface }}</td>
                    <td>
                        <button class="btn btn-secondary btn-sm" @click="viewAlert(sectory.name)">Alert</button>
                    </td>
                </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>

    const sectors = [
        {name: 'Garden',surface:'Water'},
        {name: 'Zoo',surface:'Water'},
        {name: 'Zoo',surface:'Wood'},

    ];

    export default {
        name: "AnimalList",

        data(){
            return {
                animals: [
                    {kind: 'dog', name: 'Rex', dateOfBrth: 2017-10-18, sector: sectors[0]},
                    {kind: 'cat', name: 'Mio', dateOfBrth: 2017-4-18, sector: sectors[1]},
                    {kind: 'dog', name: 'Leo', dateOfBrth: 2016-10-18, sector: sectors[2]},
                    {kind: 'mouse', name: 'Miki', dateOfBrth: '', sector: sectors[1]},
                    {kind: 'fish', name: 'Bub', dateOfBrth: 2014-10-18, sector: sectors[0]}
                ],
                newAnimal:{
                    kind: '',
                    name: '',
                    dateOfBrth: ''
                },
                sectors: sectors,
                isDiseble: true

            }

        },
        methods: {
            removeAnimal(index){
                this.animals.splice(index,1)
            },
            moveToTop(animal){

                this.animals.splice(this.animals.indexOf(animal),1);
                this.animals.unshift(animal);
            },
            addAnimal(){
                this.animals.push(this.newAnimal);
                this.newAnimal = {}
            },
            viewAlert(sector){

                var animalsList = '';
                for(var i=0; i < this.animals.length; i++) {
                    if(this.animals[i].sector.name === sector) {
                        animalsList += this.animals[i].name + ' ';
                    }
                }
                alert(animalsList);
            },

        }
    }

</script>

<style scoped>

</style>