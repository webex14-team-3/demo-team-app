<template>
  <div class="allContainer">
    <h2>Q.{{ quizzes.text }}</h2>
    <img v-bind:src="quizzes.image" />
    <div>
      <button
        v-for="(choice, i) in quizzes.choices"
        :key="i"
        v-on:click="pushButton(choice)"
      ></button>
    </div>
    <div>{{ feedback }}</div>
    <button v-on:click="nextButton" v-if="nextTrue">次の問題</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      feedback: "",
      nextTrue: false,
      quizzes: [
        {
          text: "この星の名前は何でしょう？",
          image: "Ganymede.jpg",
          choices: [
            {
              text: "ゴリアテ",
              isCorrect: false,
              feedback:
                "残念！ゴリアテは、旧約聖書に登場するダビデに石で殺される巨人だよ。",
            },
            {
              text: "ゼニガメ",
              isCorrect: false,
              feedback:
                "残念！ゼニガメは、クサガメまたはニホンイシガメの幼体だよ。",
            },
            {
              text: "ガニメデ",
              isCorrect: true,
              feedback: "正解！ガニメデは、木星の第三惑星だよ！",
            },
          ],
        },
        {
          text: "いま、何問目？",
          image: "Two.jpeg",
          choices: [
            {
              text: "１",
              isCorrect: false,
              feedback: "残念！ひとつ少ないよ。",
            },
            {
              text: "２",
              isCorrect: true,
              feedback: "正解！１でも３でもないよ！",
            },
            {
              text: "３",
              isCorrect: false,
              feedback: "残念！ひとつ多いよ。",
            },
          ],
        },
        {
          text: "この城の名前は？",
          image: "Maruoka.png",
          choices: [
            {
              text: "丸岡城",
              isCorrect: true,
              feedback: "正解！どこからどうみても丸岡城だね。",
            },
            {
              text: "丸亀城",
              isCorrect: true,
              feedback: "残念！どこからどうみても丸亀城ではないよ。",
            },
            {
              text: "丸子城",
              isCorrect: false,
              feedback: "残念！どこからどうみても丸子城ではないよ。",
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
        console.log("hellow")
      }
    },
  },
}
</script>

<style scoped>
.allContainer {
  text-align: center;
}
</style>
