<template>
  <div class="hello">
    <h1>WELCOME TO QUIZPAW!</h1>

    <h2>Best Bear quiz results:</h2>

    <div class="bears" v-for="element in frienderly" :key="element.votes">
        <h2>TOTAL: </h2>
        <h1> {{element.option}}</h1>
        <p>Freinderly: {{element.votes}}</p>
        <p v-for="vote in connectMeVotes" :key="vote">ConnectMe: {{vote}}</p> 
     <!--  <div v-for="el in connectMe" :key="el.option"> 
        <p>Connectme: {{el.votes}}</p>
      </div> -->
    </div>
    <!--  <p v-for="vote in votes" :key="vote">ConnectMe: {{vote}}</p> -->

<!--     <div v-for="name in getNamesInFrienderly" :key="name">
       <p>{{name}}</p>
       <p v-for="vote in getVotesInFrienderly" :key="vote">{{vote}}</p>
    </div> -->
      
    
    



        <!--      <div class="grizzly">
                <h1>Grizzly</h1>
                <h2>TOTAL: </h2>
                <p>QuizPaw: </p>
                <p>Frienderly: {{ this.grizzlyTotal}} </p>
                <p>ConnectMe: </p>
              </div>

              <div class="panda">
                <h1>Panda</h1>
                <h2>TOTAL: </h2>
                <p>QuizPaw: </p>
                <p>Frienderly: </p>
                <p>ConnectMe: </p>
              </div>

              <div class="polar">
                <h1>Polar</h1>
                <h2>TOTAL: </h2>
                <p>QuizPaw: </p>
                <p>Frienderly: </p>
                <p>ConnectMe: </p>
              </div>

              <div class="BlackBear">
                <h1>Black Bear</h1>
                <h2>TOTAL: </h2>
                <p>QuizPaw: </p>
                <p>Frienderly: </p>
                <p>ConnectMe: </p>
              </div> -->
  
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      frienderly: [
        {
          option:"Grizzly",
          votes: 201
        },
        {
          option:"Panda",
          votes: 195
        },
        {
          option:"Polar",
          votes: 304
        },
        {
          option: "Black Bear",
          votes: 236
        }
      ],

      connectMe: [
        {
          option:"Grizzly",
          votes: 145
        },
        {
          option:"Panda",
          votes: 349
        },
        {
          option:"Polar",
          votes: 431
        },
        {
          option: "Black Bear",
          votes: 219
        }
      ],

      quizPaw: {
        grizzly: 218,
        panda: 353,
        polar: 237,
        blackBear: 161
      },
      votes: [],
      bearsNames: [],
    }
  },
  methods: {

  },

  computed: {
    connectMeVotes() {
        this.connectMe.forEach(element => {
          this.votes.push(element.votes);
          console.log("votesss", this.votes)
        return this.votes
      })
      return this.votes
    },
 /*    getNamesInFrienderly() {
      this.frienderly.filter(element => {
        this.bearsNames.push(element.option);
        return this.bearsNames
      })
      return this.bearsNames
    },

    getVotesInFrienderly() {
      this.frienderly.filter(element => {
        this.votes.push(element.votes);
        return this.votes
      })
      return this.votes
    } */
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.bears {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}


</style>
