<template>
  <div class="form-group" style="padding:30px">
     <div>
       <input type="text" placeholder="ユーザー名を入力" v-model="user" class="form-control"> 
       </div>
    <p>ユーザー名：{{user}}</p>
    <textarea v-model="tweet" rows="5" col="10" class="form-control" placeholder="今何してる？"></textarea>
    <button class="btn- btn-info text-white mt-2" v-on:click="doAction1">ツイートする</button>    
    
    <p>過去のツイート</p>
  </div>
</template>

   

<script>
export default {
  name: "Form",

props: {
    // msg: String,    
  },

  data() {
    return {      
      user:'',
      tweet:'',
      date:'', 
           
    };
  },

  methods: {
  //   doAction() {      
  //     this.$emit("result-event",this.userimp)
  // },
    doAction1() {
      if(this.tweet==''){
        alert('tweetを入力してください。');
      }else{
      this.date=new Date().toUTCString();
      this.$emit("result-event1",this.user,this.date,this.tweet);
      this.tweet='';
      }
      },
  }
};
</script>

 <style>
/* .no-click{
  pointer-events:none;
} */
</style>

    