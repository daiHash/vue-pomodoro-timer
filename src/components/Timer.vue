<template>
  <div class="timer">
    <h1>{{ title }}</h1>
    <div id="buttons">
    <!--     Start TImer -->
      <button 
        id="start" 
        class="button is-dark is-large" 
        v-if="!timer"
        @click="startTimer">
        start timer
          <!-- <i class="far fa-play-circle"></i> -->
      </button>
      <!--     Pause Timer -->
      <button 
        id="stop" 
        class="button is-dark is-large" 
        v-if="timer"
        @click="stopTimer">
        stop timer
          <!-- <i class="far fa-pause-circle"></i> -->
      </button>
      <!--     Restart Timer -->
      <button 
        id="reset" 
        class="button is-dark is-large" 
        v-if="resetButton"
        @click="resetTimer">
          reset
          <!-- <i class="fas fa-undo"></i> -->
      </button>
    </div>

    <h2 class="pomodoro__timer">
      <span id="minutes">{{ minutes }}</span>
      <span id="middle">:</span>
      <span id="seconds">{{ seconds }}</span>
    </h2>
    
  </div>
</template>

<script>
export default {
  name: 'Timer',
  data () {
    return {
      msg: 'Welcome to the Pomodoro Timer',
      timer: null,
      totalTime: (25 * 60),
      resetButton: false,
      title: "Let the countdown begin!!"
    }
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => this.countdown(), 1000);
      this.resetButton = true;
      this.title = "Greatness is within sight!!"
    },
    stopTimer() {
      clearInterval(this.timer);
      this.timer = null;
      this.resetButton = true;
      this.title = "Never quit, keep going!!"
    },
    resetTimer() {
      this.totalTime = (25 * 60);
      clearInterval(this.timer);
      this.timer = null;
      this.resetButton = false;
      this.title = "Let the countdown begin!!"
    },
    padTime(time) {
      return (time < 10 ? '0' : '') + time;
    },
    countdown() {
      if(this.totalTime >= 1){
        this.totalTime--;
      } else{
        this.totalTime = 0;
        this.resetTimer()
      }
    }
  },
  computed: {
    minutes() {
      let minutes = Math.floor(this.totalTime / 60);
      return this.padTime(minutes);
    },
    seconds() {
      let seconds = this.totalTime - (this.minutes * 60);
      return this.padTime(seconds);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.timer {
  padding-top: 50px;
  #buttons {
    button {
      padding: 10px;
      border-radius: 5px;
      cursor: pointer;
      outline: 0;
    }
  }
  .pomodoro__timer {
    font-size: 5rem;
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translate(-50%, 0);
  }
  @media all and (max-width: 768px) {
    .pomodoro__timer {
      font-size: 3rem;
      bottom: -12%;
    }
  }
}

h1, h2 {
  font-weight: normal;
}

</style>
