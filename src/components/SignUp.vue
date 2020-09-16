<template>
    <div class="content">
        <div v-show="sign">
            <p>{{ msg }}</p>
            <form v-on:submit.prevent="xyz()">
                <p class="errorClass" :style="{visibility: error ? 'visible' : 'hidden'}">{{errorMsg}}</p>
            <div class="formFields">
            <input :disabled="tf" id="email" v-model="email" type="text" name="emailAddr" placeholder="Your Email Address *" @change="changeListener">
            <input list="intr" v-model="intr" name="interest" placeholder="Your Interests" :disabled="tf">
            <datalist id="intr">
                <option value="Developement"></option>
                <option value="Project Management"></option>
                <option value="Graphic Design"></option>
                <option value="Marketing"></option>
            </datalist>
            </div>
            <button id="signUpButton" type="submit" :disabled="tf">{{buttonMsg}}</button>
            </form>
        </div>

        <div v-show="thank">
            <h3>Thanks for your interest!</h3>
            <p>We will review your application and contact you for additional information should your background and experience meet the requirements of one of our openings</p>
        </div>
    </div>
</template>

<script>
export default {
  name: 'SignUp',
  props:{
      msg : String
  },
  data(){
      return{
          sign: true,
          thank:false,
          error: false,
          errorMsg: "Please enter a valid email address.",
          buttonMsg: "Sign Up Now ▶",
          tf: false,
          email: '',
          intr: ''
      }
  },
  methods:{
      xyz: function(){
          if (this.valid()){
            console.log("Email: "+this.email+"\nInterest: "+this.intr);
            this.tf=true;
            this.buttonMsg="Submitting...";            
            setTimeout(() => {this.sign=false; this.thank=true}, 2000);
          }
          
      },

      valid: function(){
          var mailformat = /^[a-z0-9!#$%&'*+/=?^_`{|}~-]+(?:\.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)*@(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?\.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?/;
          if(this.email.match(mailformat))
          {
              return true;
          }
          else{
              this.error=true;
              document.getElementById("email").style.borderColor="#D02035";              
              return false;              
          }
      },

      changeListener: function(){
        document.getElementById("email").style.borderColor="#FFFFFF";
        this.error=false;
      }
  }
}
</script>

<style scoped>
.content{
    margin-top: 5%;
}
form{
     margin-top: 3%;
}
.formFields{
    display: flex;
    flex-direction: row;   
}

.errorClass{
    font-size: 12px;
    width:49%;
    text-align: right;
}

input{
    width:49%;
    display: block;
    padding: 2%;
    font-style: italic;
    font-size: 16px;
}

input:disabled, #email:disabled{
    background-color: white;
}

#email{
    margin-right:2%;
}

#signUpButton{
    margin-top: 2%;
    padding: 2%;
    width: 100%;
    font-weight: bold;
    font-size: 20px;
    font-style: normal;
    color: white;
    background-color: #D02035;
    border: none;
    cursor: pointer;
    border-radius: 5px;
}

h3{
    font-weight: bold;
    font-size: 35px;
}

</style>