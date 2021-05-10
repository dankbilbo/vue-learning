<template>

    <h1>@{{user.username}}</h1>
    <h3><u style="color : red">{{fullName}}</u></h3>
    <h3>{{followers}}</h3>
    <button v-on:click="follow">Subcribe</button>
    <div style="margin-top : 30px">
        <div class="admin-profile-logo" v-if="user.isAdmin"> ADMIN </div>
        <div class="admin-profile-logo" v-else> MEMBER </div>
    </div>
    <table align="center" style="margin-top : 30px">
        <tr>
            <th>ID</th>
            <th>Content</th>
        </tr>
        <!-- <tr>
            <td><p>{{user.statuses[0].id}}</p></td>
            <td><p>{{user.statuses[0].content}}</p></td>
        </tr>
        <tr>
            <td><p>{{user.statuses[1].id}}</p></td>
            <td><p>{{user.statuses[1].content}}</p></td>
        </tr> -->
    
    <tr v-for="status in user.statuses" :key="status.id" >
        <td>status {{status.id}} : </td>
        <td>{{status.content}}</td>
    </tr>
    </table>
</template>

<script>
export default {
  name: 'UserProfile',
  data(){
    return {
      followers : 0,
      user : {
        id : 1,
        username : "admin",
        firstName : "Nghia",
        lastName : "Bui",
        isAdmin : false,
        statuses : [
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
