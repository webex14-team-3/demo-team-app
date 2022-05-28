<template>
  <body>
    <h1>Vue メモ</h1>
    <div class="memoList">
      <div class="addFieldMemo">
        <input type="text" v-model="inputValue" />
        <button v-on:click="addButton">追加</button>
        <button v-on:click="deleteAllButton">全て消す</button>
      </div>
      <ul class="memoListContainer">
        {{
          inputValue
        }}
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
        this.inputmemo = ""
      }
      console.log(this.memos)
    },

    deleteAll: function (index) {
      this.memos.splice(0)
      console.log(`this.memos:${index.length}`)
      console.log(index)
    },
  },
}
</script>

<style scoped>
body {
  text-align: center;
}

.memoList {
  padding-left: 5rem;
  padding-right: 5rem;
  display: flex;
  flex-direction: column;
  align-items: stretch;
  max-width: 512px;
  margin-left: auto;
  margin-right: auto;
}

.memoListContainer {
  padding: 0;
}

.memo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem;
  border-radius: 5px;
}

.memo:hover {
  color: white;
  background-color: #b23b61;
}

.memoText {
  margin-left: 2rem;
  text-align: left;
}

.memoText--done {
  text-decoration-line: line-through;
}

.memoDelete {
  margin-left: 1rem;
  padding: 0.5rem 0.5rem;
  border: solid 1px black;
  border-radius: 5px;
  background-color: white;
}

.memoDelete:hover {
  background-color: #b2ae3b;
  border-radius: 5px;
}

.addMemoField {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.addMemoFieldInput {
  padding: 10px;
}
.addMemoFieldButton {
  padding: 0.5rem 0.5rem;
  border: solid 1px black;
  border-radius: 5px;
  background-color: white;
}

.addMemoFieldButton:hover {
  background-color: #b2ae3b;
  border-radius: 5px;
}
</style>
