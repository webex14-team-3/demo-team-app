<template>
  <div class="allContainer">
    <h1>Q.{{ quiz.text }}</h1>
    <img class="img" v-bind:src="quizImg" v-bind:alt="quiz.text" />
    <div class="container">
      <button
        @click="pushButton(choice)"
        v-for="(choice, index) in quiz.choices"
        :key="index"
      >
        {{ choice.text }}
      </button>
    </div>
    <div>{{ feedback }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      feedback: "",
      img: "@/views/images/Ganymede.jpg",
      quiz: [
        {
          text: "この星の名前は何でしょう？",
          img: "Ganymede.jpg",
          choices: [
            {
              text: "ゴリアテ",
              isCorrect: false,
              feedback: "no",
            },
            {
              text: "ゼニガメ",
              isCorrect: false,
              feedback: "no",
            },
            {
              text: "ガニメデ",
              isCorrect: true,
              feedback: "yes",
            },
          ],
        },
        {
          text: "数字は？",
          img: "Two.jpeg",
          choices: [
            {
              text: "１",
              isCorrect: false,
              feedback: "no",
            },
            {
              text: "３",
              isCorrect: false,
              feedback: "no",
            },
            {
              text: "２",
              isCorrect: true,
              feedback: "yes",
            },
          ],
        },
      ],
    }
  },
  methods: {
    pushButton(choice) {
      this.feedback = choice.feedback
      if (choice.isCorrect) {
        console.log("yes")
      }
    },
  },
  computed: {
    quizImg(imgInd) {
      return require("./images/" + this.quiz[imgInd].img)
    },
  },
}
</script>

<style scoped>
.allContainer {
  text-align: center;
}

.container {
  display: flex;
  justify-content: center;
}
</style>
