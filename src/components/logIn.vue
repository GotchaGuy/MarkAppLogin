<template>
    
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

</template>

<script>
export default {
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
                        return false;
                    } else {
                        alert("Login confirmed");
                        this.$router.push({ path: '/profile' });
                        return true;
                    }
                }
    }
}
</script>

<style>

        section {
            height: 300px;
            max-width: 600px;
            max-height: 300px;
            font-family: "Helvetica";
            margin: 100px auto 0 auto;
            text-align: left;
        }
        /* div uno */
        section div.uno {
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

        /* div dos */
        section div.dos {
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
            
        }
        
        section div.dos div h2 {
            float: left;
        }
        div.eye {
            float: left;
        }
        div.eye i {
            margin-left: 5px;
        }
        section div.dos button {
            width: 220px;
            height: 40px;
            margin-top: 20px;
            border: none;
        }
        .dos input {
            width: 170px;
            margin-bottom: 20px;
            border: none;
        }
        .dos p {
            font-size: 12px;
        }

        /* both modes */
        #app div.uno p,
        #app div.dos {
              color: rgb(190, 190, 190);
        }

        /* light mode */
          #app .light {
            background-color: rgb(238, 235, 235);
        }

        #app .light div.uno,
        #app .light div.dos button {
            color: rgb(49, 56, 71);
          background-color: white;
        }
        
        #app .light div.dos,
        #app .light div.dos input {
            background-color: rgb(49, 56, 71);
        }
        #app .light div.dos p,
        #app .light div.dos input {
            color: rgb(190, 190, 190);
        }
        /* dark mode */
        #app .dark {
            background-color: rgb(49, 56, 71);
        }

        #app .dark div.uno,
        #app .dark div.dos,
        #app .dark div.dos input,
        #app .dark div.dos button {
            color:  rgb(221, 183, 11);
            border: 1px solid rgb(221, 183, 11);

        }
        #app .dark #nav a {
            color: rgb(221, 183, 11);
        } 
        #app .dark div.uno,
        #app .dark div.dos button {
            background-color: rgb(31, 36, 46);
        }
        
        #app .dark div.dos,
        #app .dark div.dos input {
            background-color: rgb(88, 88, 88);
        }
        #app .light div.dos p {
       color: rgb(221, 183, 11);
        }
</style>
