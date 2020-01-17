<template>
  <div id="home">
    <ul class="collection with-header">
      <li class="collection-header"><h4>Workouts</h4></li>
      <li v-for="Workout in workouts" v-bind:key="Workout.id" class="collection-item">
          <div class="chip" >{{Workout.Datum}}</div>
        {{Workout.Workout}} {{Workout.mail}}
         <router-link class="secondary-content" v-bind:to="{ name: 'view-workout', params: { Workout: Workout.Workout }}"><i class="btn blue text-white">Open</i></router-link>
      </li>
    </ul>
    <div class="fixed-action-btn">
      <router-link to="/new" class="btn-floating btn-large blue">
        <i class="fa fa-plus"></i>
      </router-link>
    </div>
  </div>
</template>

<script>
  import db from './firebaseInit'
  export default {
    name: 'home',
    data () {
      return {
        workouts: [],
        loading: true
      }
    },
    created () {
      db.collection('workouts').get().then((querySnapshot) => {
        this.loading = false
        querySnapshot.forEach((doc) => {
          const data = {
            'id': doc.id,
            'mail': doc.data().mail,
            'Workout': doc.data().Workout,
            'Datum': doc.data().Datum,
            'Exercise1': this.Exercise1,
            'Sets1': this.Sets1,
            'Reps1': doc.data().Reps1,
            'Weight1': doc.data().Weight1,
            'Exercise2': doc.data().Exercise2,
            'Sets2': doc.data().Sets2,
            'Reps2': doc.data().Reps2,
            'Weight2': doc.data().Weight2,
            'Exercise3': doc.data().Exercise3,
            'Sets3': doc.data().Sets3,
            'Reps3': doc.data().Reps3,
            'Weight3': doc.data().Weight3,
            'Exercise4': doc.data().Exercise4,
            'Sets4': doc.data().Sets4,
            'Reps4': doc.data().Reps4,
            'Weight4': doc.data().Weight4,
            'Exercise5': doc.data().Exercise5,
            'Sets5': doc.data().Sets5,
            'Reps5': doc.data().Reps5,
            'Weight5': doc.data().Weight5,
            'Exercise6': doc.data().Exercise6,
            'Sets6': doc.data().Sets6,
            'Reps6': doc.data().Reps6,
            'Weight6': doc.data().Weight6,
            'Exercise7': doc.data().Exercise7,
            'Sets7': doc.data().Sets7,
            'Reps7': doc.data().Reps7,
            'Weight7': doc.data().Weight7,
            'Exercise8': doc.data().Exercise8,
            'Sets8': doc.data().Sets8,
            'Reps8': doc.data().Reps8,
            'Weight8': doc.data().Weight8
          }
          this.workouts.push(data)
        })
      })
    }
  }
</script>