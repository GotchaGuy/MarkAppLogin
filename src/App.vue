<template>
  <div id="app">
      <div id="unique">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
      | <router-link to="/profile">Profile</router-link>
    </div>
    <button class="mode" @click="inputModeChange">
      <div >    
        <i v-bind:class="light"></i>
      </div>
    </button>
    
    <router-view/>

        </div>
  </div>
</template>



<script>
export default {
  name: "hq",
  data() {
    return {
                    light: "far fa-lightbulb",
                }
            },
            mounted() {
                var lightMode = agCookie.read("mode");
                if (lightMode == null || lightMode == "light") {
                    this.light = "far fa-lightbulb";
                        unique.classList.add("light");
                } else {
                    this.light = "fas fa-lightbulb";
                        unique.classList.add("dark");
                }
            },
            methods: {
                inputModeChange: function() {

                    var lightMode = agCookie.read("mode");
                        var unique = document.getElementById("unique");
                    if (lightMode == "light") {
                        this.light = "fas fa-lightbulb";
                        unique.classList.remove("light");
                        unique.classList.add("dark");
                        agCookie.create("mode", "dark", 10);
                    } else {
                        this.light = "far fa-lightbulb";
                        unique.classList.remove("dark");
                        unique.classList.add("light");
                        agCookie.create("mode", "light", 10);
                    }

                }

            }
            
        }
    </script>


<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#app #unique {
    height: 100vh;
}
#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active,
#app .dark #nav a.router-link-exact-active {
  color: #42b983;
}

 body {
            margin: 0;
            padding: 0;
        }

  button.mode {
    background-color: yellow;
    border: none;
    border-radius: 20%;
    margin-bottom: 20px;

  }
 /* light mode */
   #app .light {
   background-color: rgb(238, 235, 235);
   color: rgb(49, 56, 71);
    }

   /* dark mode */
     #app .dark {
     background-color: rgb(49, 56, 71);
      color:  rgb(221, 183, 11);
    }

</style>