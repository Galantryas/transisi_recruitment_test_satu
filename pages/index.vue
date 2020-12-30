<template>
  <v-container class="container">
    <v-layout class="box">
      <div class="left-box">
        <div class="inleft">
          <v-btn
            class="mx-2 cornerup"
            depressed
            fab
            small
            dark
            color="#3A3E4E"
          >
            <img src="~/static/reverse.png" alt="">
          </v-btn>
          <h1 style="color:white;">Hi Samantha</h1>
          <h4>Welcome back to the workplace, we missed You!</h4>
          <form method="get" action="/search" class="search">
            <input type="text" size="40" placeholder="Search Task or Project..." />
          </form>
          <h3 style="color:white;">Projects <a>(13)</a></h3>
          <v-row
            no-gutters
            style="margin-top:5%;"
          >
            <v-col class="gridcon">
              <div>
                <img class="project-img" src="~/static/p1.jpg">
              </div>
              <a class="project-txt">Green House</a>
              <div class="project-img">
                <img class="project-img two" src="~/static/p2.jpg">
              </div>
              <a class="project-txt">Travel App</a>
            </v-col>
            <v-col class="gridcon">
              <div>
                <img class="project-img" src="~/static/p3.jpg">
              </div>
              <a class="project-txt">Cyber Punk</a>
              <div class="project-img">
                <v-badge
                  avatar
                  bordered
                  overlap class="two"
                >
                  <template v-slot:badge>
                    <v-avatar>
                      <img src="~/static/white.jpg">
                    </v-avatar>
                  </template>
                    <img class="project-img" src="~/static/p4.jpg">
                </v-badge>
              </div>
              <a class="project-txt">Landing Page</a>
            </v-col>
            <v-col class="gridcon">
              <div class="project-img">
                <v-badge
                  avatar
                  bordered
                  overlap
                >
                  <template v-slot:badge>
                    <v-avatar>
                      <img src="~/static/white.jpg">
                    </v-avatar>
                  </template>
                    <img class="project-img" src="~/static/p5.jpg">
                </v-badge>
              </div>
              <a class="project-txt">Easy Crypto</a>
              <div class="project-img" style="background-color:black;margin-top:10%;">
                <h1 style="color:white;">8+</h1>
              </div>
            </v-col>
          </v-row>
        </div>
      </div>
      <div class="right-box">
        <div class="inright">
          <v-row no-gutters class="top-right">
            <v-col
              cols="12"
              sm="6"
              md="8"  
            >
              <h2 style="color:black;">Cyber Punk</h2>
              <h4 style="margin-top:2%;color:#DADADC;">Lorem ipsum dolor sit amet consectetur adipisicing elit. Nesciunt exercitationem est nobis perferendis.</h4>
            </v-col>
            <v-col
              cols="6"
              md="4"
            >
            <v-avatar size="40">
              <img
                src="https://cdn.vuetifyjs.com/images/john.jpg"
                alt="John"
              >
            </v-avatar>
            <v-avatar size="40">
              <img
                src="https://avatars0.githubusercontent.com/u/9064066?v=4&s=460"
                alt="John"
              >
            </v-avatar>
            <v-avatar size="40">
              <img
                src="https://cdn.vuetifyjs.com/images/cards/server-room.jpg"
                alt="John"
              >
            </v-avatar>
            <v-btn
              class="mx-2"
              elevation="2"
              fab
              dark
              small
              depressed
              outlined
              color="#FFFFFF"
            >
              <v-icon color="#DBDBDD">
                mdi-plus
              </v-icon>
            </v-btn>
            </v-col>
          </v-row>
          <div>
            <v-row no-gutters>
              <v-col
                cols="12"
                sm="6"
                md="8"
              >
                <h4 class="bottom-right" style="color:black;">Today</h4>
              </v-col>
              <v-col
                cols="6"
                md="4"
              >
                <img style="padding-left:75%;" src="~/static/three-dots.png" alt="">
              </v-col>
            </v-row>
            <hr/>
            <v-simple-table class="bottom-right-2">
              <template v-slot:default>
                <tbody>
                  <tr
                    v-for="item in taskList"  
                    :key="item.task"
                  >
                    <td>
                      <label class="containerr">
                        <input type="checkbox">
                        <span class="checkmark"></span>
                      </label>
                    </td>
                    <td style="color:#BCBDC0;">{{ item.task }}</td>
                    <td v-if="item.status=='In Progress'" style="color:rgb(183, 194, 241);">
                      <div
                        class="chipss"
                        style="background-color:#E0F5F6;"
                      >
                      {{ item.status }}</div>
                    </td>
                    <td v-else-if="item.status=='Assigned'" style="color:rgb(121, 46, 196);">
                      <div
                        class="chipss"
                        style="background-color:rgb(168, 135, 201);"
                      >
                      {{ item.status }}</div>
                    </td>
                    <td v-else-if="item.status=='Commited'" style="color:rgb(137, 138, 141);">
                      <div
                        class="chipss"
                        style="background-color:#EDEEF0;"
                      >
                      {{ item.status }}</div>
                    </td>
                    <td v-else="" style="color:rgb(250, 170, 156);">
                      <div
                        class="chipss"
                        style="background-color:#FEEEE6;"
                      >
                      {{ item.status }}</div>
                    </td>
                  </tr>
                </tbody>
              </template>
            </v-simple-table>
            <v-btn
              class="mx-2 corner"
              fab
              dark
              color="#884CC6"
              @click="AddNew()"
            >
              <v-icon dark>
                mdi-plus
              </v-icon>
            </v-btn>
          </div>
        </div>
      </div>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  components: {
  },
  data() {
    return {
      taskList: [
        {
        "task": "Create artificial intelligence",
        "status":"Commited",
        },
        {
        "task": "Fixing all hole in the moon",
        "status":"In Progress",
        },
        {
        "task": "Change design of earth",
        "status":"Assigned",
        }
      ],
    };
  },
  methods:{
    AddNew(){
      var addnew = {
        "task": "",
        "status":"",
      }
      var possible = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";
      for (var i = 0; i < 10; i++){
        addnew.task += possible.charAt(Math.floor(Math.random() * possible.length));
        addnew.status += possible.charAt(Math.floor(Math.random() * possible.length));
      }
      this.taskList.push(addnew);
      console.log(this.taskList);
    }
  }
}
</script>

<style lang="scss" scoped>
  .container{
    max-width: 100vw;
    padding:0px;
  }
  .box{
    display:flex;
    height: 100vh;
    width: 100vw;
  }
  .box-right{
    display:flex;
    position: relative;
    height: 100vh;
    width: 40%;
  }
  .top-right{
    margin-top: 5%;
    margin-left: 5%;
    max-height: 20vh;
  }
  .bottom-right{
    margin-left: 7%;
  }
  .bottom-right-2{
    margin-left: 5%;
    margin-right:5%;
    tr{
    border-bottom: none !important;
    }
    td{
    border-bottom: none !important;
    }
  }
  .left-box{
    display: flex;
    background-color: #252A40;
    flex-direction: column;
    width: 50vw;
    height: 100vh;
  }
  .right-box{
    display: flex;
    background-color: #252A40;
    flex-direction: column;
    width: 50vw;
    height: 100vh;
    padding: 1.5vh 1.5vh 1.5vh 1.5vh;
  }
  .inright{
    display: flex;
    background-color: rgb(255, 255, 255);
    flex-direction: column;
    width: 47vw;
    height: 100vh;
    border-radius: 2%;
  }
  .inleft{
    display: flex;
    background-color: #252A40;
    flex-direction: column;
    width: 35vw;
    height: 70vh;
    margin-left:15%;
    margin-top:15%;
  }
  .chipss{
    border-radius:20px;
    height:70%;
    width:100%;
    display:flex;
    align-items:center;
    justify-content:center;
  }
  .containerr {
  display: block;
  position: relative;
  padding-left: 35px;
  margin-bottom: 12px;
  cursor: pointer;
  font-size: 22px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  }
  .containerr input {
    position: absolute;
    opacity: 0;
    cursor: pointer;
    height: 0;
    width: 0;
  }
  .checkmark {
    position: absolute;
    top: 0;
    left: 0;
    height: 25px;
    width: 25px;
    background-color: #eee;
    border-radius: 50%;
  }
  .containerr:hover input ~ .checkmark {
    background-color: #ccc;
  }
  .containerr input:checked ~ .checkmark {
    background-color: #77E7E8;
    border-radius: 50%;
  }
  .checkmark:after {
    content: "";
    position: absolute;
    display: none;
  }
  .containerr input:checked ~ .checkmark:after {
    display: block;
  }
  .containerr .checkmark:after {
    left: 9px;
    top: 5px;
    width: 5px;
    height: 10px;
    border: solid white;
    border-width: 0 3px 3px 0;
    -webkit-transform: rotate(45deg);
    -ms-transform: rotate(45deg);
    transform: rotate(45deg);
  }
  .corner{
    position: fixed;
    bottom: 5%;
    right: 2%;
  }
  .cornerup{
    position: fixed;
    top: 2%;
    left: 1%;
  }
  h4{
    color:#6A6C7F;
  }
  h3{
    padding-top: 20%;
    a{
      color:#6A6C7F;
      cursor: auto;
    }
  }
  hr{
    margin: 2% 5% 0% 5%;
    color: #DADADC;
  }
  .search input[type="text"] {
    background: url(../static/searchh.png) no-repeat 15px 15px rgb(255, 255, 255);
    background-color: #3A3F53;
    border: 0 none;
    color: #6A6C7F;
    width: 75%;
    height: 90%;
    padding: 6px 15px 6px 35px;
    margin-top: 5%;
    border-radius: 20px;
    &::placeholder {
      padding-left: 5%;
    }
  }
  .project-img{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    border-radius: 20px;
    width: 12vh;
    height: 12vh;
  }
  .two{
    margin-top: 30%;
  }
  .project-txt{
    margin-top: 15%;
    color: #6A6C7F;
  }
  .gridcon{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>
