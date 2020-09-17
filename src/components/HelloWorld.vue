<template>
  <div class="hello">
    <h1>WELCOME TO QUIZPAW!</h1>

    <h2>Best Bear quiz results:</h2>

    <div class="bears">
      <div class="grizzly">
        <h1>Grizzly</h1>
        <h2>TOTAL: </h2>
        <p>QuizPaw: </p>
        <p>Frienderly: </p>
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
      }
    }
  },
  methods: {

  },

  computed: {

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.bears {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}


</style>
