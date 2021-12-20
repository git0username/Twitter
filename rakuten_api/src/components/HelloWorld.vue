<template>
  <div>
    <v-btn v-on:click="getData">データを取得する。</v-btn>
    <h4>{{ title }}</h4>
    <h4>{{ author }}</h4>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",

  data() {
    return {
      title: "a",
      author: "a",
    };
  },

  async mounted() {
    const url =
      "https://app.rakuten.co.jp/services/api/BooksTotal/Search/20170404?format=json&keyword=javascript&booksGenreId=000&applicationId=1074639811262691163";

    const response = await fetch(url);
    const data = await response.json();
    // return data;
    console.log(data.Items[1]);
    this.title = data.Items[1].Item.title;
    this.author = data.Items[1].Item.author;
  },
};
</script>

  // methods:{
  //   async getData(){
  //     const url =
  //     "https://app.rakuten.co.jp/services/api/BooksTotal/Search/20170404?format=json&keyword=javascript&booksGenreId=000&applicationId=1074639811262691163"

  //     const response = await fetch(url);
  //   const data = await response.json();
  //   // return data;
  //   console.log(data.Items[2].Item.title);
  //   this.title=data.Item[2].Item.title;
  //   this.author=data.Item[2].Item.author;
  //   },


  //   },
 

  // data: () => ({
  //   ecosystem: [
  //     {
  //       text: 'vuetify-loader',
  //       href: 'https://github.com/vuetifyjs/vuetify-loader',
  //     },
  //     {
  //       text: 'github',
  //       href: 'https://github.com/vuetifyjs/vuetify',
  //     },
  //     {
  //       text: 'awesome-vuetify',
  //       href: 'https://github.com/vuetifyjs/awesome-vuetify',
  //     },
  //   ],
  //   importantLinks: [
  //     {
  //       text: 'Chat',
  //       href: 'https://community.vuetifyjs.com',
  //     },
  //     {
  //       text: 'Made with Vuetify',
  //       href: 'https://madewithvuejs.com/vuetify',
  //     },
  //     {
  //       text: 'Twitter',
  //       href: 'https://twitter.com/vuetifyjs',
  //     },
  //     {
  //       text: 'Articles',
  //       href: 'https://medium.com/vuetify',
  //     },
  //   ],
  //   logo,
  //   whatsNext: [
  //     {
  //       text: 'Explore components',
  //       href: 'https://vuetifyjs.com',
  //     },
  //     {
  //       text: 'Roadmap',
  //       href: 'https://vuetifyjs.com/introduction/roadmap/',
  //     },
  //     {
  //       text: 'Frequently Asked Questions',
  //       href: 'https://vuetifyjs.com/getting-started/frequently-asked-questions',
  //     },
  //   ],
  // }),


