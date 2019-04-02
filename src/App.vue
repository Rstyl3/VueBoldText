<template>
  <div id="app">
    <template v-for="message in messages" >
         <b v-if="users.find((u) => {return u.name.toLowerCase() == message.toLowerCase()} )" :key="message.id">@{{message}}</b>
         <template v-else>{{message}}</template>
    </template>
  </div>
</template>

<script>

export default {
  name: 'app',
  components: {
  },
  data() {
    return {
      msg: '@Severin_Hasselhof sdasdas johan@exflow.com  @Jeremiah_Unsullied sadasd @Jeremiah_U@sadsadsa',
      users: [
        { id: 1, name: "Severin_Hasselhof" },
        { id: 2, name: "Johan_Hamburger" },
        { id: 3, name: "Thomas_Brokeback" },
        { id: 4, name: "Erik_Ender" },
        { id: 5, name: "Jeremiah_Unsullied" }
      ]
    }
  },
  computed: {
    messages() {
       //return this.msg.replace(/\s@[a-zA-Z0-9_]*/ig, function(m){return '<b>'+ m +'</b>'})

       let userlist = new RegExp(this.users.map(n => '@' + n.name).join('|'), 'gim')
       console.log(userlist)
       console.log( this.msg.split(/@([\w]*)/ig))
      return this.msg.split(/@([\w]*)/ig)
    },
  },

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
