<template>
  <div class="hello">
    <h1>WELCOME TO QUIZPAW!</h1>

    <h2>Best Bear quiz results:</h2>
  
    
<!--     <div  class="bearsNames">
      <p @click="addAVoteToGrizzly">{{this.frienderly[0].option}}</p>
      <p @click="addAVoteToPanda">{{this.frienderly[1].option}}</p>
      <p @click="addAVoteToPolar">{{this.frienderly[2].option}}</p>
      <p @click="addAVoteToBlackBear">{{this.frienderly[3].option}}</p>
    </div> -->

    <div  class="bearsNames">
      <p @click="addAVote(bearName.option)" v-for="bearName in frienderly" :key="bearName.option">{{bearName.option}}</p>
    </div> 

     <div  class="wrapperTotals">
      <p v-for="total in totals" :key="total.name"> TOTAL: {{total.total}}</p>
    <!--   <p> TOTAL PANDA: </p>
      <p> TOTAL POLAR: </p>
      <p> TOTAL BLACK BEAR: </p> -->
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
   
    <!-- <div class="wrapperTotals">
      <p>TOTAL GRIZZLY: {{finalResultGrizzly}} </p>
      <p>TOTAL PANDA: {{finalResultPanda}}</p>
      <p>TOTAL POLAR: {{finalResultPolar}}</p>
      <p>TOTAL BLACK BEAR: {{finalResultBlackBear}}</p>
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
    </div -->
    
    
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
  /*     finalResultGrizzly: null,
      finalResultPanda: null,
      finalResultPolar: null,
      finalResultBlackBear: null */
      
    }

  },

    created() {
      this.totals = this.createArrayOfTotals();
      console.log("show me array", this.totals);
      const result = this.findGrizzly();
      console.log(" this is result", result)
     /*  this.finalResultGrizzly = this.totalForGrizzly;
      this.finalResultPanda = this.totalForPanda;
      this.finalResultPolar = this.totalForPolar;
      this.finalResultBlackBear = this.totalForBlackBear; */
    },

  computed: {
    
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
      return this.frienderly[0].votes + this.connectMe[0].votes + this.quizPaw.grizzly   
    },

    totalForPanda() {
       return this.frienderly[1].votes + this.connectMe[1].votes + this.quizPaw.panda 
    },

    totalForPolar() {
       return this.frienderly[2].votes + this.connectMe[2].votes + this.quizPaw.polar 
    },

    totalForBlackBear() {
       return this.frienderly[3].votes + this.connectMe[3].votes + this.quizPaw.blackBear 
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

    frienderlyAndConnectMeMerged() {
     return  [...this.frienderly, ...this.connectMe];
        
    },



    /* totalForGrizzly() {
      return this.frienderly[0].votes + this.connectMe[0].votes + this.quizPaw.grizzly   
    },

    totalForPanda() {
       return this.frienderly[1].votes + this.connectMe[1].votes + this.quizPaw.panda 
    },

    totalForPolar() {
       return this.frienderly[2].votes + this.connectMe[2].votes + this.quizPaw.polar 
    },

    totalForBlackBear() {
       return this.frienderly[3].votes + this.connectMe[3].votes + this.quizPaw.blackBear 
    },

    
    resultForGrizzly: {
        get() {
          console.log("I'm calleddd get result")
            return  this.finalResultGrizzly
        },

        set(newValue) {
            this.finalResultGrizzly = newValue;
            console.log("result grizzly", this.finalResultGrizzly) 
       } 
    }, 

    resultForPanda: {
      get() {
        console.log("I'm calleddd get result")
          return  this.finalResultPanda
      },

      set(newValue) {
          this.finalResultPanda = newValue;
          console.log("result panda", this.finalResultPanda) 
      } 
    }, 

    resultForPolar: {
      get() {
        console.log("I'm calleddd get result")
          return  this.finalResultPolar
      },

      set(newValue) {
          this.finalResultPolar = newValue;
          console.log("result polar", this.finalResultPolar) 
      } 
    },
    
    resultForBlackBear: {
      get() {
        console.log("I'm calleddd get result")
          return  this.finalResultBlackBear
      },

      set(newValue) {
          this.finalResultBlackBear = newValue;
          console.log("result black bear", this.finalResultBlackBear) 
      } 
    },   */
    
  },

    methods: {
  /*     addAVoteToGrizzly() {  
        this.finalResultGrizzly++;
      },
      addAVoteToPanda() {  
        this.finalResultPanda++;
      },
      addAVoteToPolar() {  
        this.finalResultPolar++;
      },
      addAVoteToBlackBear() {
        this.finalResultBlackBear++;
      }
 */
      addAVote(bearName) {
        this.totals = this.createArrayOfTotals();
        console.log("array of totals", this.totals);      
        console.log("THIS IS EL", bearName); 
      
        this.totals.forEach(element => {
            if (element.name === bearName) {
              element.total++
              console.log("element increased", element.total)
            }
        });
      },

      createArrayOfTotals() {

            /* totalForEachBear.push(this.totalForGrizzly, this.totalForPanda, this.totalForPolar, this.totalForBlackBear); */
            this.totals = this.totalForEachBear;

            return this.totals

        },

    
        groupByProperty(bear) {
          return bear.option === "Grizzly";

         /*  return objectArray.reduce(function (acc, obj) {
            console.log("this is acc",acc);
            console.log("this is objj", obj)
          
                    let key = obj[property];  
                    console.log("this is keyy", key);
                     if (!acc[key]) {
                      acc[key] = []
                    }
                    acc[key].push(obj);
                    return acc
            ,
                  }, {}) */
          },

          findGrizzly() {
            console.log("this is my arrayyyyyyy", this.frienderlyAndConnectMeMerged)
            return this.frienderlyAndConnectMeMerged.find(this.groupByProperty);
            
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
