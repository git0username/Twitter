<template>
  <div id="app">
    <Form v-on:result-event1="appAction"/>
    <Tweet
    v-for="(item, index) in tweeted"
    v-bind:key="index" 
    v-bind:item="item"
    v-bind:index="index"
    />
    
  </div>
</template>

<script>
import Form from './components/form.vue';
import Tweet from './components/tweet.vue';

export default {
  name: "app",
 props: {
  

  },

  components: {
    Form,
    Tweet    
  },
  
  data() {
    return {
      tweet_obj:{},
      count:0,       
      tweeted:[],
      // tweetStorage:{},      
  }
  },


  methods: { 
    appAction(user,date,tweet) {      
      // this.tweet_obj = {};
      console.log(this.count);      
      console.log(this.tweet_obj);
      this.tweet_obj['user']=user;
      this.tweet_obj['date']=date;
      this.tweet_obj['tweet']=tweet;
      // console.log(this.tweet_obj);    

      const tweet1 = Object.assign({},this.tweet_obj);
      
      localStorage.setItem(this.count,JSON.stringify(tweet1));
      this.tweeted.unshift(tweet1);

      
      
      console.log(this.tweeted);

      this.user=user;
 
      this.count++;
      

    }
},

//  computed: {
//     reverseItems() {
//       return this.tweeted.slice().reverse();
//     },
//   },

mounted(){
  console.log(localStorage.length);
  if(localStorage.getItem(0)!=null){
  for(let i=0;i<localStorage.length-1;i++){
  let data = JSON.parse(localStorage.getItem(i))
  this.tweeted.unshift(data);
  }
  }
  console.log(this.tweeted)
},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
