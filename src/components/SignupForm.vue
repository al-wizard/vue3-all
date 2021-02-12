<template>
    <h4 class="text-left">Signup Form here</h4>
        <form @submit.prevent="handleSubmit">
            <div class="input-group my-4">
                <div class="input-group-prepend">
                    <span class="input-group-text">Email</span><br>
                        <input v-model="email" class="form-control" type="email" required />
                </div>
            </div>         
            <div class="input-group my-4">
                <div class="input-group-prepend">
                    <span class="input-group-text">Password</span><br>
                        <input v-model="password" class="form-control" type="password" required />
                </div>
            </div>
        <hr>
            <p class="lead text-left my-2">Role:</p>
            <div class="input-group mb-4">
                 <select class="form-control" v-model="role">
                    <option value="choose">choose option</option> 
                    <option value="developer">web developer</option>
                    <option value="designer">web designer</option>
                 </select>
            </div>
        <hr>
            <p class="lead text-left mt-2">Choose:</p>
            <div class="input-group my-3">
                <div class="input-group-prepend">
                    <div class="input-group-text">
                        <input type="checkbox" value="alex" v-model="names">
                    </div>
                </div>
                <span class="ml-2">Alex</span>
                <div class="ml-2 input-group-prepend">
                    <div class="input-group-text">
                        <input type="checkbox" value="viki" v-model="names">
                    </div>
                </div>
                <span class="ml-2">Viki</span>
                <div class="ml-2 input-group-prepend">
                        <div class="input-group-text">
                            <input type="checkbox" value="katiko" v-model="names">
                        </div>
                </div>
                <span class="ml-2">Katiko</span>   
            </div>
        <hr>
            <p class="lead text-left mt-2">Add Skills to your skills array:</p>
                <div class="ml-2 input-group-prepend">
                    <div class="input-group-text">
                        <input class="form-control" type="text" v-model="tempSkill" @keyup.alt="addSkill">        
                    </div>
                </div>
            <p class="text-left text-info my-3">Skills added:</p>
            <h3 v-if="WarningAlert" class="text-warning">{{ WarningText }}</h3>
                <div v-for="skill in skills" :key="skill" class="float-sm-left">                     
                    <small class="skill" @click="deleteSkill(skill)"> {{ skill }}</small> 
                </div>

        <div class="clearfix">&nbsp;</div>
        <hr>
            <div class="input-group my-5">
            <div class="input-group-prepend">
                <div class="input-group-text">
                <input type="checkbox" v-model="terms">
                </div>
            </div>
            <span class="ml-2">Accept Terms and Conditions</span>
        </div>   

        <hr>
            <button class="btn btn-primary">Submit all of this</button>  
            <div v-if="passwordError" class="error text-danger mt-3">{{ passwordError }}</div>        
    </form>              
</template>

<script>
import App from '../App.vue'
export default {
  components: { App },
   data() {
       return {
           email: 'guitar.ageiii@gmail.com',
           password: '',
           role: 'choose',
           terms: false,
           names: ['alex'],
           tempSkill: '',
           skills: [],
           WarningText: '',
           WarningAlert: false,
           passwordError: ''
       }
   },
   methods: {
       addSkill(e) {
           if(e.key === ',' && this.tempSkill) {
               if(!this.skills.includes(this.tempSkill)) {
                   this.WarningAlert = false
                   this.WarningText = ''
                   this.skills.push(this.tempSkill)                
               } else {
                   this.WarningAlert = true
                   this.WarningText = 'Skill Repeat Detected!'
               }
               this.tempSkill = '' 
           }
       },
       deleteSkill(skill){
           this.skills = this.skills.filter((item)=>{
               return skill !== item
           })
       },
       handleSubmit() {
           console.log('Form is submitting ... wait...')
           this.passwordError = this.password.length > 5 ? ' ' : 'Password must be at least 6 char long'

           if(this.passwordError){
                console.log("Email: ", this.email)
                console.log("Password: ", this.password)
                console.log("Role: ", this. role)
                console.log("Chosen names: ", this.names)
                console.log("Your skills: ", this.skills)  
                console.log("Terms accepted: ", this.terms)  
           }
       }
   }
}
</script>

<style>
   .skill {
       background-color: #333;
       color: white;
       border-radius: 10px;
       padding: 10px;
       margin-right: 1px;
       cursor: pointer;
   }
   .error {
       font-size: 12px;
       font-weight: bold;
   }
</style>