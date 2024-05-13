 
 <template>

  <div class="app">
  <h1><b><p> WELCOME TO GUESSING GAME</p></b></h1>
  
  
  
  <div>
    
    <h1>Guessing Game</h1>
    <div v-if="!gameOver">
      <label for="guessInput">Enter your guess (1-10):</label>
      <input type="number" id="guessInput" v-model.number="userGuess" @keyup.enter="checkGuess ">
      <button @click="checkGuess">Submit Guess</button>
      <div v-if="message">{{ message }}</div>
    </div>
    <div v-else>
      <h2>Congratulations! You guessed the correct number in {{ attempts }} attempts.</h2>
      <button @click="restartGame">Play Again</button>
    </div>
  </div>

  </div>
</template>

<script>
export default {
  data() {
    return {
      secretNumber: Math.floor(Math.random() * 10) + 1,
      userGuess: null,
      message: '',
      attempts: 0,
      gameOver: false
    };
  },
  methods: {
    checkGuess() {
      if (this.userGuess === this.secretNumber) {
        this.message = 'Congratulations! You guessed the correct number!';
        this.gameOver = true;
      } else if (this.userGuess > this.secretNumber) {
        this.message = 'Too high! Try again.';
      } else {
        this.message = 'Too low! Try again.';
      }
      this.attempts++;
    },
    restartGame() {
      this.secretNumber = Math.floor(Math.random() * 10) + 1;
      this.userGuess = null;
      this.message = '';
      this.attempts = 1;
      this.gameOver = false;
    }
  }
};
</script>


<style scoped>

.app {
  
  max-width: 600px;
  margin: auto;
  background-color: green; /* Set your desired background color here */
  padding: 20px;
  border-radius: 60px;
  box-shadow: 0 0 20px ;
}

h1, h2 {
  text-align: center;
}
div{
  background-color:rgb(27, 201, 71) ;
  width: 100%;
}
#guessInput{
  width: 20%;
  height: 40px;
  border-radius:40px;
  border-top: 34px 0 0 53px  ;
  background-color:blue ;
 

}
p{
  text-align: center;
  color: black;
}
button{
  height: 40px;
  border-radius:50px;
  background-color:#ff00ff;
}
body{
background-color: black;
}


</style>



 

