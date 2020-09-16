<template>
    <div class="content">
        <div v-show="sign">
            <p>{{ msg }}</p>
            <form v-on:submit.prevent="xyz()">
            <div class="formFields">
            <input class="email" v-model="email" type="email" name="emailAddr" placeholder="Your Email Address *" required :disabled="tf">
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
          buttonMsg: "Sign Up Now ▶",
          tf: false,
          email: '',
          intr: ''
      }
  },
  methods:{
      xyz: function(){
          console.log("Email: "+this.email+"\nInterest: "+this.intr);
          this.buttonMsg="Submitting...";
          this.tf=true;
          setTimeout(() => {this.sign=false; this.thank=true}, 2000);
          
      }
  }
}
</script>

<style scoped>
.content{
    margin-top: 5%;
}
.formFields{
    display: flex;
    flex-direction: row;
    margin-top: 5%;
}
input{
    width:49%;
    display: block;
    padding: 2%;
    font-style: italic;
    font-size: 16px;
}

input:disabled, input.email:disabled{
    background-color: white;
}

.email{
    margin-right:2%;
}
input.email:focus:invalid {
    border-color:#D02035;
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