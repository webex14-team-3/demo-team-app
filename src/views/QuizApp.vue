<templete>
<div class="allContainer">
  <h1>Q.{{ quiz.text }}</h1>
  <img class="img" v-bind:src="quizImg" v-bind:alt="quiz.text"/>
  <div class="container">
  <button @click="pushButton(choice)" v-for="(choice, i) in quiz.choices" :key="i" >
    {{ choice.text }}
  </button>
  </div>
  <div>{{ feedback }}</div>
</div>
</templete>

<script>
export default {
  data() {
    return {
      feedback: "aiueo",
      img: "Ganymede.jpg",
      quiz: {
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
}
</script>
