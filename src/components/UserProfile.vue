<template>

    <h1>@{{user.username}}</h1>
    <h3><u style="color : red">{{fullName}}</u></h3>
    <h3>{{followers}}</h3>
    <button v-on:click="follow">Subcribe</button>
    <div style="margin-top : 30px">
        <div class="admin-profile-logo" v-if="user.isAdmin"> ADMIN </div>
        <div class="admin-profile-logo" v-else> MEMBER </div>
    </div>
    <div>
        <Statuses v-for="status in user.post" :key="status.id" :username="user.username" :status="status"/>
    </div>
</template>

<script>

import Statuses from "./components/Status"

export default {
  name: 'UserProfile',
  components : {Statuses},
  data(){
    return {
      followers : 0,
      user : {
        id : 1,
        username : "admin",
        firstName : "Nghia",
        lastName : "Bui",
        isAdmin : false,
        post : [
            {id : 1, content : "bruh"},
            {id : 2 , content : "bruh2"}
        ]
      }
    }
  },
  watch:{
    followers(newFollowersCount, oldFollowersCount){
      if(oldFollowersCount < newFollowersCount){
        console.log("any1 subeds")
      }
    }
  },
  computed:{
    fullName(){
      return `${this.user.firstName + this.user.lastName} `
    }
  },
  methods:{
    follow(){
      this.followers++;
    }
  },
  mounted(){
    this.follow();
  }
}
</script>

<style>
    .admin-profile-logo{
        background : purple;
        color : white;
        margin: auto;
        border-radius: 5px;
    }
</style>
