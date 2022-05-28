<template>
  <body>
    <h1>Vue メモ</h1>
    <div class="memoList">
      <!-- ボタンの設定 -->
      <div class="textMemo">
        <input type="text" v-model="inputValue" />
        <button class="button" v-on:click="addButton">追加</button>
        <button class="button" v-on:click="deleteAllButton">全て消す</button>
      </div>

      <!-- メモの設定 -->
      <ul class="memoList">
        <div class="memo" v-for="(memo, index) in memos" :key="index">
          <input class="checkbox" type="checkbox" />
          <div>
            {{ memo.text }}
            <button class="appearButton" v-on:click="deletebutton(index)">
              削除
            </button>
          </div>
        </div>
      </ul>
    </div>
  </body>
</template>

<script>
export default {
  data() {
    return {
      inputValue: "",
      memos: JSON.parse(localStorage.list || "[]"),
    }
  },
  methods: {
    addButton: function () {
      if (this.inputValue !== "") {
        this.memos.push({ text: this.inputValue })
        this.inputValue = ""
      }
      console.log(this.memos)
    },
    deleteAllButton: function (index) {
      this.memos.splice(0)
      console.log(`this.memos:${index.length}`)
      console.log(index)
    },
    deletebutton: function (index) {
      this.memos.splice(index, 1)
      console.log(this.memos)
    },
  },
}
</script>

<style scoped>
body {
  padding-left: 5rem;
  padding-right: 5rem;
  display: flex;
  flex-direction: column;
  align-items: stretch;
  max-width: 512px;
  margin-left: auto;
  margin-right: auto;
  text-align: center;
}

.button {
  cursor: pointer;
  background-color: gainsboro;
  border: solid 1px black;
  border-radius: 3px;
  padding: 1px 1px;
}

.button:active {
  transform: translateY(2px);
}

.memoList {
  padding: 0;
}

.memo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem;
  border-radius: 5px;
}

.checkbox:checked {
  color: white;
  background-color: #b23b61;
}

.content {
  margin-left: 2rem;
  text-align: left;
}

.content--done {
  text-decoration-line: line-through;
}

.appearButton {
  cursor: pointer;
}
.appearButton:active {
  transform: translateY(2px);
}
</style>
