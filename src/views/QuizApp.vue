<templete>
<div class="allContainer">
  <h1>Q.{{ quiz.title }}</h1>
  <img class="img" v-bind:src="quizImg" v-bind:alt="quiz.title"/>
  <div class="container">
   <button @click="pushButton" v-for="(choice, i) in quiz.choices" :key="i" >
    {{ quiz.choices.text }}
   </button>
  </div>
</div>
</templete>

<script></script>
