<template>
  <h1>Vue メモ</h1>
  <div class="memo-list">
    <ul class="memo-list_container">
      <li class="memo" v-for="(memo, index) in memos" :key="index">
        <div class="memo_checkbox">
          <input type="checkbox" />
        </div>
        <div class="memo_text">
          {{ memo.text }}
        </div>
        <button class="memo_delete" v-on:click="deletememo(index)">削除</button>
      </li>
    </ul>
    <div class="add-memo-field">
      <input class="add-memo-field_input" type="text" v-model="inputmemo" />
      <button class="add-memo-field_button" v-on:click="addmemo">
        追加する
      </button>
      <button class="all-delete_button" v-on:click="alldelete">全て消す</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputmemo: "",
      memos: [{ text: "あいうえお" }, { text: "かきくけこ " }],
    }
  },
  methods: {
    addmemo: function () {
      if (this.inputmemo !== "") {
        this.memos.push({ text: this.inputmemo })
        this.inputmemo = ""
      }
      console.log(this.memos)
    },
    deletememo: function (index) {
      this.memos.splice(index, 1)
      console.log(this.memos)
    },
  },
}
</script>

<style>
:root {
  --main-color: #b23b61;
  --text-color: #fff;
  --text-hover-color: #fff;
  --button-border-color: #000;
  --button-bg-color: #fff;
}

button {
  background-color: gainsboro;
  border: solid 1px black;
  border-radius: 5px;
  padding: 0.5rem 0.5rem;
  cursor: pointer;
}

button:active {
  transform: translateY(2px);
}

.memo-list {
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

.memo-list__container {
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
  color: var(--text-color);
  background-color: var(--main-color);
}

.memo__text {
  margin-left: 2rem;
  text-align: left;
}

.memo__text--done {
  text-decoration-line: line-through;
}

.memo__delete {
  margin-left: 1rem;
}

.add-memo-field {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.add-memo-field__input {
  padding: 10px;
}
</style>
