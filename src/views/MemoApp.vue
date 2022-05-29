<template>
  <div class="body">
    <h1>Vue メモ</h1>
    <div class="memoList">
      <!-- ボタンの設定 -->
      <div class="textMemo">
        <input type="text" v-model="inputValue" id="checkInput" />
        <button class="button" v-on:click="addButton">追加</button>
        <button class="button" v-on:click="deleteAllButton">全て消す</button>
      </div>

      <!-- メモの設定 -->
      <ul class="memoList">
        <div class="memo" v-for="(memo, index) in memos" :key="index">
          <div id="checkContent">
            <input
              id="typeCheckbox"
              type="checkbox"
              required="チェックしてください"
            />
            <label id="checkButton" for="checkFor">
              <div class="checks">
                {{ memo.text }}
              </div>
            </label>
            <button class="appearButton" v-on:click="deletebutton(index)">
              削除
            </button>
          </div>
        </div>
      </ul>
    </div>
  </div>
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
.body {
  padding-left: 5rem;
  padding-right: 5rem;
  display: flex;
  flex-direction: column;
  align-items: stretch;
  max-width: 512px;
  margin-left: auto;
  margin-right: auto;
  text-align: center;
  user-select: none;
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

.typeCheckbox {
  position: relative;
  margin: 5px 10px;
}

input:checked + label {
  color: rgb(87, 91, 109);
  background-color: rgb(186, 203, 203);
}

#checkContent {
  display: flex;
}

.appearButton {
  cursor: pointer;
  background-color: gainsboro;
  border: solid 1px black;
  border-radius: 3px;
  padding: 2px 3px;
  font-size: 15px;
}
.appearButton:active {
  transform: translateY(2px);
}
.checks {
  font-size: 20px;
  font-weight: bold;
}
</style>
