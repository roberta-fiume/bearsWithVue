<template>
  <div class="hello">
    <h1>WELCOME TO QUIZPAW!</h1>

    <h2>Best Bear quiz results:</h2>

   <!--  <div class="bears" v-for="element in frienderly" :key="element.votes">
        <h2>TOTAL: </h2>
        <h1> {{element.option}}</h1>
        <p>Freinderly: {{element.votes}}</p>
        <p v-for="vote in connectMeVotes" :key="vote">ConnectMe: {{vote}}</p> 
    </div> -->
  
  <div class="wrapperBearsnames">
    <div v-for="name in getNamesInFrienderly" :key="name" class="bearsNames">
       <p>{{name}}</p>
    </div>
  </div>

  <div>
    
  </div>

  <div  class="wrapperFrienderlyVotes">
    <div v-for="vote in getVotesInFrienderly" :key="vote">
      <p>Frienderly: {{vote}}</p>
    </div>
  </div>  
    
  <div class="wrapperConnectMeVotes">
     <div v-for="el in getVotesInConnectMe" :key="el">
      <p>ConnectMe: {{el}}</p>
    </div>
  </div>
   
  
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
      votesConnectMe: []
    }
  },
  methods: {

  },

  computed: {
 /*    connectMeVotes() {
        this.connectMe.forEach(element => {
          this.votes.push(element.votes);
          console.log("votesss", this.votes)
        return this.votes
      })
      return this.votes
    }, */
    getNamesInFrienderly() {
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
    },
    getVotesInConnectMe() {
       this.connectMe.filter(element => {
        this.votesConnectMe.push(element.votes);
        return this.votesConnectMe
      })
      return this.votesConnectMe
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

/* .bears {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
} */

.wrapperBearsnames {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
.bearsNames {
  width: 100px;
  display: flex;
  flex-direction: row;
  border: 2px solid lightcoral;
}

.wrapperFrienderlyVotes {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}

.wrapperConnectMeVotes {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}


</style>
