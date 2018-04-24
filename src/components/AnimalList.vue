<template>
  <div>
    <form @submit.prevent="addAnimal">
      <label>Type</label>
      <input v-model="newAnimal.type" type="text" placeholder="Type"/>
      <label>Name</label>
      <input v-model="newAnimal.name" type="text" placeholder="Name"/>
      <label>Date of birth</label>
      <input v-model="newAnimal.dateOfBirth" type="text" placeholder="Date of birth"/>
      <button type="submit">Add Animal</button>
    </form>
    <table>
      <thead>
      <th>Type</th>
      <th>Name</th>
      <th>Date of birth</th>
      <th>Sector</th>
      <th>&nbsp;</th>
      <th>&nbsp;</th>
      </thead>
      <tbody>
        <tr v-for= "(animal,key) in animals" :key="key">
        <td> {{animal.type}} </td>
        <td> {{animal.name}} </td>
        <td> {{animal.dateOfBirth === '' ? 'Unknown' : animal.dateOfBirth }} </td>
        <td> {{animal.sector.name}} </td>
        <td><button @click="remove(animal)">Remove</button></td>
        <td><button @click="toTop(key)">Move to top</button></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
const sectors = [
  { name:'Predators', surface: 'kage' },
  { name: 'WaterAnimals', surface: 'water' },
  { name: 'Fawl', surface: 'kage' }
];
export default {
  name: 'AnimalList',
  data(){
    return{
      sectors: sectors,

      animals:[
        {type: 'Girrafe', name: 'Doe', dateOfBirth: '2017-03-05', sector:sectors[2]},
        {type: 'Tiger', name: 'Johan', dateOfBirth: '2013-07-05', sector:sectors[2]},
        {type: 'Wolf', name: 'Daglas', dateOfBirth: '2003-08-11', sector:sectors[1]},
        {type: 'Monkey', name: 'Sead', dateOfBirth: '2018-04-02', sector:sectors[0]},
        {type: 'Elephant', name: 'Joe', dateOfBirth: '1998-06-05', sector:sectors[1]}
      ],
      newAnimal:{
        type:'',
        name: '',
        dateOfBirth: ''
      }
    }
  },
  methods:{
    remove(animal){
      this.animals.splice(this.animals.indexOf(animal), 1)
    },
    toTop(key){ 
      var animal=this.animals.indexOf(this.animals[key])
      this.animals.unshift(this.animals[key])
      this.animals.splice(animal+1, 1)
    },
    addAnimal(){
      this.animals.push(this.newAnimal)
    }
  }
}
</script>
