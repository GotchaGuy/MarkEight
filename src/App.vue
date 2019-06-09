<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <!-- <router-link to="/profile">Profile</router-link> -->
    </div>
    <button class="mode" @click="inputModeChange">
      <div >    
        <i v-bind:class="light"></i>
      </div>
    </button>
     <section>
            <div class="uno">
                <h1>Login</h1>
                <p>{{ loginDesc }}</p>
            </div>
            <div class="dos">
                <h2>Email</h2>
                <input  type="text" id="email" v-model="newUN" v-bind:placeholder="placeholderUN">
                <div>
                    <h2>Password</h2>
                    <div @click="inputTypeChange" class="eye">
                        <i v-bind:class="visual"></i>
                    </div>
                </div>
                <input  v-model="newP" v-bind:type="inputType" v-bind:placeholder="placeholderP">
                <button @click="validate" >Log in</button>
                <p id="error"></p>
            </div>
        </section>
  </div>
</template>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

 body {
            margin: 0;
            padding: 0;
            background-color: rgb(238, 235, 235);
        }

  button.mode {
    background-color: yellow;
    border: none;
    border-radius: 20%;

  }

        section {
            max-width: 600px;
            max-height: 300px;
            font-family: "Helvetica";
            margin: 100px auto 0 auto;
            text-align: left;
        }
        /* div uno */
        section div.uno {
            background-color: white;
            height: 230px;
            width: 300px;
            float: left;
            margin-top: 35px;
            box-sizing: border-box;
            padding: 40px;
            
        }
        
        section div.uno h1 {
            font-size: bold;
            font-size: 30px;
            
        }
        section div.uno p {
            color: rgb(190, 190, 190);
        }
        /* div dos */
        section div.dos {
            background-color: rgb(49, 56, 71);
            height: 300px;
            width: 300px;
            float: left;
            border-radius: 2%;
            box-sizing: border-box;
            padding: 40px;
            
            
        }
        section div.dos h2 {
            width: 70px;
            font-weight: 100;
            font-size: 16px;
            margin-bottom: 5px;;
            margin-top: 0;
            color: rgb(190, 190, 190);
            
        }
        
        section div.dos div h2 {
            float: left;
        }
        div.eye {
            float: left;
        }
        div.eye i {
            color: rgb(190, 190, 190);
            margin-left: 5px;
        }
        section div.dos button {
            width: 220px;
            height: 40px;
            margin-top: 20px;
            background-color: white;
            border: none;
        }
        .dos input {
            background-color: rgb(49, 56, 71);
            color: rgb(190, 190, 190);
            width: 170px;
            margin-bottom: 20px;
            border: none;
        }
        .dos p {
            color: rgb(190, 190, 190);
            font-size: 12px;
        }

         .back {
         background-color: rgb(49, 56, 71) !important;
        }

        .backDos {
          background-color: rgb(88, 88, 88) !important;
           color:  rgb(221, 183, 11) !important;
          border: rgb(221, 183, 11) 1px solid !important;
        }

        .backUno {
          background-color: rgb(31, 36, 46) !important;
           color:  rgb(221, 183, 11) !important;
          border: rgb(221, 183, 11) 1px solid !important;
        }
</style>

<script>
export default {
  name: "hq",
  data() {
    return {
                    loginDesc: "By logging in you agree to the ridiculously long terms you didn't bother to read.",
                    placeholderUN: "me@example.com",
                    placeholderP: "MyPw123%&%",
                    inputType: "password",
                    visual: "fas fa-eye-slash",
                    newUN: "",
                    newP: "",
                    password: "flawlessPandas",
                    // unlock: false,

                    light: "far fa-lightbulb",
                }
            },
            methods: {
                inputTypeChange: function() {
                    if (this.inputType == "password") {
                        this.inputType = "text";
                        this.visual = "fas fa-eye";
                    } else {
                        this.inputType = "password";
                        this.visual = "fas fa-eye-slash"
                    }
                },
                inputModeChange: function() {
                  var divUno = document.querySelector("div.uno");
                  var divDos = document.querySelector("div.dos");
                  var body = document.querySelector("body");
                  var inputs = document.querySelectorAll("input");
                  var logIn = document.querySelector("div.dos button");

                    if (this.light == "far fa-lightbulb") {
                     this.light = "fas fa-lightbulb";

                      body.classList.add("back");
                      divUno.classList.add("backUno");
                       divDos.classList.add("backDos");
                       for (let i=0;i<inputs.length;i++) {
                      inputs[i].classList.add("backDos");
                       }
                        logIn.classList.add("backUno");

                    } else {
                      this.light = "far fa-lightbulb";

                       body.classList.remove("back");
                      divUno.classList.remove("backUno");
                         divDos.classList.remove("backDos");
                         for (let i=0;i<inputs.length;i++) {
                      inputs[i].classList.remove("backDos");
                       }
                        logIn.classList.remove("backUno");
                         
                        
                    }
                },
                // locked: function() {
                //   if(this.unlock != true) {
                //     alert("You need to login in order to access the Profile page.");
                //     this.$router.push({path: "/"});
                //   }
                // },
                validate: function() {
                    var email = document.getElementById("email").value;
                    var atSign = email.indexOf("@");
                    
                    var error = document.getElementById("error");
                    var mistakes = "";
                    var hasErrors = false;

                    if (this.newP != this.password){
                        mistakes += "Entered password is incorrect. ";
                        hasErrors = true;
                    }

                    if (this.newP.length < 8){
                        mistakes += "8 or more characters are required for the password. ";
                        hasErrors = true;
                    }
                    
                    if (atSign === -1) {
                        mistakes += "The email is missing an '@' sign.";
                        hasErrors = true;
                    }
                    if (hasErrors === true) {
                        error.innerHTML = mistakes;
                        // this.unlock = false;
                        return false;
                    } else {
                        alert("Login confirmed");
                        this.$router.push({ path: '/profile' });
                        // this.unlock = true;
                        return true;
                    }
                },
            }
            
        }
    </script>
