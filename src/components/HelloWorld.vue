<template>
  <div class="hello">
    <h1>WELCOME TO QUIZPAW!</h1>

    <h2>Best Bear quiz results:</h2>
  
    
    <div  class="bearsNames">
      <p @click="addAVote">{{this.frienderly[0].option}}</p>
      <p>{{this.frienderly[1].option}}</p>
      <p>{{this.frienderly[2].option}}</p>
      <p>{{this.frienderly[3].option}}</p>
    </div>
   
    <div class="wrapperTotals">
      <p>TOTAL GRIZZLY: {{totalForGrizzly}}</p>
      <p>TOTAL PANDA: {{totalForPanda}}</p>
      <p>TOTAL POLAR: {{totalForPolar}}</p>
      <p>TOTAL BLACK BEAR: {{totalForBlackBear}}</p>
    </div>

    <div class="wrapperQuizPawResults">
      <p> QuizPaw: {{quizPaw.grizzly}}</p>
      <p> QuizPaw: {{quizPaw.panda}}</p>
      <p> QuizPaw: {{quizPaw.polar}}</p>
      <p> QuizPaw: {{quizPaw.blackBear}}</p>    
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
      votesConnectMe: [],
      addVoteGrizzly: null,
    }
  },
  methods: {
    addAVote() {
      console.log("I workkkkk")
     
     
     return this.totalForGrizzly++
    }
  },

  computed: {
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
    },

    totalForGrizzly: {
      get() {
         return  this.frienderly[0].votes + this.connectMe[0].votes + this.quizPaw.grizzly
      },

      set(newValue) {
        console.log(newValue)
        return newValue
      }
    },

/*     totalForGrizzly() {
         return  this.frienderly[0].votes + this.connectMe[0].votes + this.quizPaw.grizzly
    }, */

    totalForPanda() {
       return this.frienderly[1].votes + this.connectMe[1].votes + this.quizPaw.panda 
    },

    totalForPolar() {
       return this.frienderly[2].votes + this.connectMe[2].votes + this.quizPaw.polar 
    },

    totalForBlackBear() {
       return this.frienderly[3].votes + this.connectMe[3].votes + this.quizPaw.blackBear 
    },


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

.bearsNames {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}

.wrapperTotals {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}

.wrapperQuizPawResults {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
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
