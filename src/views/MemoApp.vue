<template>
  <div class="allContainer">
    <h1>Todoリスト</h1>
    <div>
      <input
        type="text"
        v-model="inputMemo"
        class="addInput"
        placeholder="買うものを書いてね"
      />
      <div>
        <button class="topButton" v-on:click="addButton">アイテム追加</button>
        <button class="topButton" v-on:click="selectButton()">選択消去</button>
        <button class="topButton" v-on:click="allDeleteButton">全て消す</button>
      </div>
    </div>
    <ul>
      <li class="memo" v-for="(item, index) in items" :key="index">
        <label class="memoContent">
          <input type="checkbox" v-model="item.done" class="checkboxed" />
          <span v-bind:class="{ done: item.done }" class="message">
            {{ item.text }}
          </span>
          <button v-on:click="deleteButton(index)" class="deleteButton">
            削除
          </button>
        </label>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputMemo: "",
      items: [],
    }
  },
  created() {
    this.items = JSON.parse(localStorage["items"] || "[]")
  },
  methods: {
    addButton() {
      if (this.inputMemo !== "") {
        this.items.push({ text: this.inputMemo })
        localStorage.setItem("items", JSON.stringify(this.items))
        this.inputMemo = ""
      }
    },
    selectButton() {
      if (window.confirm("本当に削除しますか？")) {
        let remains = []
        for (let i = 0; i < this.items.length; i++) {
          if (!this.items[i].done) {
            remains.push(this.items[i])
          }
        }
        this.items = remains
        localStorage.setItem("items", JSON.stringify(this.items))
      }
    },
    allDeleteButton() {
      if (window.confirm("本当に削除しますか？")) {
        this.items = []
        localStorage.clear()
      }
    },
    deleteButton(index) {
      if (window.confirm("本当に削除しますか？")) {
        this.items.splice(index, 1)
        localStorage.setItem("items", JSON.stringify(this.items))
      }
    },
  },
  computed: {},
}
</script>

<style scoped>
.allContainer {
  padding: 0px;
  margin: 0px;
  text-align: center;
}

.addInput {
  min-width: 75%;
  margin: 5px auto;
  user-select: none;
}

.topButton {
  margin: 0 5px;
  max-width: 45%;
  background-color: pink;
  border: 1px solid orange;
  border-radius: 5px;
  font-size: 20px;
  font-weight: bold;
  user-select: none;
}

button:hover {
  cursor: pointer;
  filter: brightness(102%);
}

button:active {
  transform: scale(0.98);
}

ul {
  list-style-type: none;
  border: 2px solid black;
  min-height: 450px;
  min-width: 80%;
  overflow: auto;
}

.done {
  text-decoration: line-through;
}

.message {
  user-select: none;
}

.memo {
  border: 2px solid black;
  margin: 5px auto;
  max-width: 90%;
  min-height: 30px;
  overflow-y: auto;
  overflow-wrap: break-word;
  word-wrap: break-word;
  display: flex;
  justify-content: space-between;
  position: relative;
}

input[type="checkbox"] {
  margin: 5px;
  margin-right: 10px;
}

.message {
  font-size: large;
  font-weight: bold;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
}

.deleteButton {
  background-color: pink;
  border: 1px solid orange;
  border-radius: 5px;
  font-size: 15px;
  font-weight: bold;
  padding: 5px;
  height: 40px;
  width: 50px;
}

.memoContent {
  /* border: 2px solid blue; */
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
