<template>
  <div>
    <table>
      <thead>
      <th>Type</th>
      <th>Name</th>
      <th>Date of birth</th>
      </thead>
      <tbody>
        <tr v-for= "(animal,key) in animals" :key="key">
        <td> {{animal.type}} </td>
        <td> {{animal.name}} </td>
        <td> {{animal.dateOfBirth === '' ? 'Unknown' : animal.dateOfBirth }} </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'AnimalList',
  data(){
    return{
      animals:[
        {type: 'Girrafe', name: 'Doe', dateOfBirth: '2017-03-05'},
        {type: 'Tiger', name: 'Johan', dateOfBirth: '2013-07-05'},
        {type: 'Wolf', name: 'Daglas', dateOfBirth: '2003-08-11'},
        {type: 'Monkey', name: 'Sead', dateOfBirth: '2018-04-02'},
        {type: 'Elephant', name: 'Joe', dateOfBirth: '1998-06-05'}
      ]
    }
  }
}
</script>
