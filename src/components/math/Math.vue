<template>
  <div class="math">
    <Title></Title>
    <div class="progress">
      <div class="progress-bar" :style="{ width: this.progressStyle + '%' }"></div>
    </div>
    <div class="box">
      <transition name="flip" mode="out-in">
        <StartScreen v-if="state == 'start'" @onStart="onStart"></StartScreen>

        <Question v-else-if="state == 'question'"
                  @success="onQuestSuccess"
                  @error="onQuestError"
        >
        </Question>

        <Message v-else-if="state == 'message'"
                  :type="message.type"
                  :text="message.text"
                  @onNext="onNext"
        >
        </Message>

        <ResultScreen v-else-if="state == 'results'"></ResultScreen>
        <div v-else>Default State</div>
      </transition>
    </div>
  </div>
</template>

<script>
import Title from "@/components/common/Title";
import StartScreen from "@/components/math/StartScreen";
import Question from "@/components/math/Question";
import Message from "@/components/math/Message";
import ResultScreen from "@/components/math/ResultScreen";

export default {
  name: 'Math',
  data() {
    return {
      title: 'Math',
      state: 'start',
      stats: {
        success: 0,
        desault: 0
      },
      message: {
        type: '',
        text: ''
      },
      questMax: 3
    };
  },
  computed: {
    questDone() {
      return this.stats.success++;
    },
    progressStyle() {
      return {
        width: this.questDone / this.questMax * 100
      };
    }
  },
  methods: {
    onStart() {
      this.state = 'question';
    },
    onQuestSuccess() {
      this.state = 'message';
      this.message.text = 'Good Job';
      this.message.type = 'success';
      this.stats.success++;
    },
    onQuestError(msg) {
      this.state = 'message';
      this.message.text = msg;
      this.message.type = 'warning';
      this.stats.error++;
    },
    onNext() {
      if (this.questDone < this.questMax) {
        this.state = 'question';
      } else {
        this.state = 'results';
      }
    }
  },
  components: {
    Title,
    StartScreen,
    Question,
    Message,
    ResultScreen
  }
};
</script>

<style lang="scss" scoped>
@import url(https://stackpath.bootstrapcdn.com/bootstrap/4.1.1/css/bootstrap.min.css);

.box {
  margin: 20px 0;
}

.flip-enter {
}

.flip-leave {
}

.flip-enter-active {
  animation: flipInX 0.2s linear;
}

.flip-leave-active {
  animation: flipOutX 0.2s linear;
}

.progress-bar {
  transition: width 0.5s;
}

@keyframes flipInX {
  from {
    transform: rotateX(90deg);
  }
  to {
    transform: rotateX(0deg);
  }
}

@keyframes flipOutX {
  from {
    transform: rotateX(0deg);
  }
  to {
    transform: rotateX(90deg);
  }
}
</style>
