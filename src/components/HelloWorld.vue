<template>
  <div class="hello">
    <h1>WELCOME TO QUIZPAW!</h1>

    <h2>Best Bear quiz results:</h2>

    <div  class="bearsNames">
      <p @click="addAVote(bearName.option)" v-for="bearName in frienderly" :key="bearName.option">{{bearName.option}}</p>
    </div> 

     <div  class="wrapperTotals">
      <p v-for="total in totals" :key="total.name"> TOTAL: {{total.total}}</p>
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
      <div v-for="vote in getVotesInConnectMe" :key="vote">
        <p>ConnectMe: {{vote}}</p>
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
      finalResult: null,
      totals: 0,
      groupedGrizzly: null 
    }

  },

    created() {
      this.totals = this.createArrayOfTotals();
      let finalResult = this.removeDeplicates();    
    },

  computed: {

    frienderlyAndConnectMeMerged() {
      return  [...this.frienderly, ...this.connectMe];   
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

  
    totalForGrizzly() {
      let finalResult = this.removeDeplicates();
      const grizzlyTotal = finalResult.find( ({ option }) => option === "Grizzly" );

      return grizzlyTotal.votes + this.quizPaw.grizzly   
    },

    totalForPanda() {
      let finalResult = this.removeDeplicates();
      const pandaTotal = finalResult.find( ({ option }) => option === "Panda" );

      return pandaTotal.votes + this.quizPaw.panda 
    },

    totalForPolar() {
      let finalResult = this.removeDeplicates();
      const polarTotal = finalResult.find( ({ option }) => option === "Polar" );

      return polarTotal.votes + this.quizPaw.polar 
    },

    totalForBlackBear() {
      let finalResult = this.removeDeplicates();
      const blackBearTotal = finalResult.find( ({ option }) => option === "Black Bear" );

      return blackBearTotal.votes + this.quizPaw.blackBear 
    },

    totalForEachBear() {
      return [
           {
              name: "Grizzly",
              total: this.totalForGrizzly
            },
            {
              name: "Panda",
              total: this.totalForPanda
            },
            {
              name: "Polar",
              total: this.totalForPolar
            },
            {
              name: "Black Bear",
              total: this.totalForBlackBear
            }
         ];
      },
  },

    methods: {

      addAVote(bearName) {
        this.totals = this.createArrayOfTotals();
        
        this.totals.forEach(element => {
            if (element.name === bearName) {
              element.total++;
            }
        });
      },

      createArrayOfTotals() {
        this.totals = this.totalForEachBear;

        return this.totals
      },

    
      sumObjValuesWithsameKeys() {
        let frienderlyAndConnectMe = this.frienderlyAndConnectMeMerged.reduce(function(accumulator, currentValue) {
          var object = accumulator.filter(function(obj){
              return obj.option === currentValue.option;
          }).pop() || {option: currentValue.option, votes: 0};

          object.votes += currentValue.votes;
          accumulator.push(object);
          return accumulator;
        },[]);

        return frienderlyAndConnectMe

      },

      removeDeplicates() {
        let frienderlyAndConnectMe = this.sumObjValuesWithsameKeys();
        let finalResult = frienderlyAndConnectMe.filter(function(item, index, element) {
                          return index === element.indexOf(item);
                        });
        return finalResult
      }
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

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
