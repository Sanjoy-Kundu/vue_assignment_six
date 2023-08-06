<script setup>
import {ref, reactive} from 'vue'

const users = reactive([
{email: 's@gmail.com', password: '12345'},
{email: 'labib@gmail.com', password:'12345'},
{email: 'sabuj@gmail.com', password:'12345'}
]);

let error_message = ref('')
let isErrorFirst = ref(false);
let dashboard_status = ref(true);


const loginEmail = ref('');
const loginPassword = ref('');
const loginPageActive = ref(true);



const registrationEmail = ref('');
const registrationPassword = ref('');
const registrationConfirmPassword = ref('');



function registrationPage(){
  loginPageActive.value = false
}
function loginPage(){
  loginPageActive.value = true;
}



function loginSubmit(){
  const user = users.find(info => info.email == loginEmail.value && info.password == loginPassword.value);
  if(user){
    dashboard_status.value = false
  }else{
    isErrorFirst.value = true
    error_message.value = "Your Email and Password does not match";
  }
}

function registrationSubmit(){
  if(registrationPassword.value != registrationConfirmPassword.value){
    isErrorFirst.value = true
    error_message.value = "Your Password and confirm Password does not match";
  }else{
      dashboard_status.value = false

  }


}
</script>

<template>
 <!-- login form start -->
 <section class="h-screen" v-if="loginPageActive">
  <div class="container h-full px-6 py-24" v-if="dashboard_status">
    <div class="g-6 flex h-full flex-wrap items-center justify-center lg:justify-between">
      <!-- Left column container with background-->
      <div class="mb-12 md:mb-0 md:w-8/12 lg:w-6/12">
        <img src="https://tecdn.b-cdn.net/img/Photos/new-templates/bootstrap-login-form/draw2.svg" class="w-full" alt="Phone image" />
      </div>

      <!-- Right column container with form -->
      <div class="md:w-8/12 lg:ml-6 lg:w-5/12">
        <h1 class="text-2xl text-center mb-5">Wellcome To Your Login Page</h1>
        <!-- alert  message-->
        <div class="p-4 mb-4 text-sm text-red-800 rounded-lg bg-red-50 dark:bg-gray-800 dark:text-red-400" role="alert" v-if="isErrorFirst">
            <span class="font-medium">{{ error_message }}</span>
          </div>
        <!-- alert  message-->


        <form @submit.prevent="">
            <label class="block mb-3">
              <span class="block text-lg font-medium text-slate-700">User Email</span>
              <!-- Using form state modifiers, the classes can be identical for every input -->
              <input type="email" v-model="loginEmail" placeholder="Enter Your Email"  class="mt-1 block w-full px-3 py-2 bg-white border border-slate-300 rounded-md text-sm shadow-sm placeholder-slate-400
                focus:outline-none focus:border-sky-500 focus:ring-1 focus:ring-sky-500
                disabled:bg-slate-50 disabled:text-slate-500 disabled:border-slate-200 disabled:shadow-none
              "/>
            </label>

            <label class="block mb-3">
              <span class="block text-lg font-medium text-slate-700">User Password</span>
              <!-- Using form state modifiers, the classes can be identical for every input -->
              <input type="password" v-model="loginPassword" placeholder="Enter Your Password"  class="mt-1 block w-full px-3 py-2 bg-white border border-slate-300 rounded-md text-sm shadow-sm placeholder-slate-400
                focus:outline-none focus:border-sky-500 focus:ring-1 focus:ring-sky-500
                disabled:bg-slate-50 disabled:text-slate-500 disabled:border-slate-200 disabled:shadow-none
                invalid:border-pink-500 invalid:text-pink-600
                focus:invalid:border-pink-500 focus:invalid:ring-pink-500
              "/>
            </label>

            <button class="border-2 bg-indigo-500 p-2 text-white " @click="loginSubmit()"> Login</button>
          </form>
          <p>Create a new account? <a @click="registrationPage()" class="text-cyan-600 cursor-pointer">Registration Now</a></p>
      </div>
    </div>
  </div>
  <!---dashboard start-->
  <div class="container h-full px-6 py-24" v-else>
      <div class="p-20 bg-orange-200 mx-auto">
        <h1 class="text-orange-400 font-bold text-center mb-3">Wllcome to my Dashboard</h1>
        <div class="bg-white rounded-lg shadow-2xl md:flex">
          <img src="https://images.unsplash.com/photo-1593642532744-d377ab507dc8" alt="Laptop on Desk" class="md:w-1/3 rounded-t-lg md:rounded-l-lg md:rounded-t-none" />
          <div class="p-6">
            <h2 class="font-bold text-xl md:text-3xl mb-2 text-orange-700">Name: Sanjoy Kundu</h2>
            <h2 class="font-bold text-md md:text-md  mb-2 text-orange-700">Email: sanjoykundu187@gmail.com</h2>
            <h2 class="font-bold text-md md:text-md  mb-2 text-orange-700">Profession: Backend Developer (Laravel)</h2>
          </div>
        </div>
      </div>
   </div>
  <!--dashboard end-->
</section>
 <!-- login form end -->



 <!-- registration page design -->
 <section class="h-screen" v-else>
  <div class="container h-full px-6 py-24" v-if="dashboard_status">
    <div class="g-6 flex h-full flex-wrap items-center justify-center lg:justify-between">
      <!-- Left column container with background-->
      <div class="mb-12 md:mb-0 md:w-8/12 lg:w-6/12">
        <img src="https://tecdn.b-cdn.net/img/Photos/new-templates/bootstrap-login-form/draw2.webp" class="w-full" alt="Phone image" />
      </div>

      <!-- Right column container with form -->
      <div class="md:w-8/12 lg:ml-6 lg:w-5/12">
        <h1 class="text-2xl text-center mb-5">Please Registration Here.</h1>
     
                <!-- alert  message-->
                <div class="p-4 mb-4 text-sm text-red-800 rounded-lg bg-red-50 dark:bg-gray-800 dark:text-red-400" role="alert" v-if="isErrorFirst">
                    <span class="font-medium">{{ error_message }}</span>
                </div>
              <!-- alert  message-->


        <form  @submit.prevent="">
            <label class="block mb-3">
              <span class="block text-lg font-medium text-slate-700">Email</span>
              <!-- Using form state modifiers, the classes can be identical for every input -->
              <input type="email" v-model="registrationEmail" placeholder="Enter Your Email"  class="mt-1 block w-full px-3 py-2 bg-white border border-slate-300 rounded-md text-sm shadow-sm placeholder-slate-400
                focus:outline-none focus:border-sky-500 focus:ring-1 focus:ring-sky-500
                disabled:bg-slate-50 disabled:text-slate-500 disabled:border-slate-200 disabled:shadow-none
                invalid:border-pink-500 invalid:text-pink-600
                focus:invalid:border-pink-500 focus:invalid:ring-pink-500
              "/>
            </label>

            <label class="block mb-3">
              <span class="block text-lg font-medium text-slate-700"> Password</span>
              <!-- Using form state modifiers, the classes can be identical for every input -->
              <input type="password" v-model="registrationPassword"    placeholder="Enter Your Password"  class="mt-1 block w-full px-3 py-2 bg-white border border-slate-300 rounded-md text-sm shadow-sm placeholder-slate-400
                focus:outline-none focus:border-sky-500 focus:ring-1 focus:ring-sky-500
                disabled:bg-slate-50 disabled:text-slate-500 disabled:border-slate-200 disabled:shadow-none
                invalid:border-pink-500 invalid:text-pink-600
                focus:invalid:border-pink-500 focus:invalid:ring-pink-500
              "/>
            </label>

            <label class="block mb-3">
              <span class="block text-lg font-medium text-slate-700">Confirm Password</span>
              <!-- Using form state modifiers, the classes can be identical for every input -->
              <input type="password" v-model="registrationConfirmPassword" placeholder="Enter Your confirm Password"  class="mt-1 block w-full px-3 py-2 bg-white border border-slate-300 rounded-md text-sm shadow-sm placeholder-slate-400
                focus:outline-none focus:border-sky-500 focus:ring-1 focus:ring-sky-500
                disabled:bg-slate-50 disabled:text-slate-500 disabled:border-slate-200 disabled:shadow-none
                invalid:border-pink-500 invalid:text-pink-600
                focus:invalid:border-pink-500 focus:invalid:ring-pink-500
              "/>
            </label>

            <button class="border-2 bg-indigo-500 p-2 text-white "  @click="registrationSubmit()"> Registration</button>
          </form>
          <p>Already have an Account? <a href="" @click="loginPage()"  class="text-cyan-600 cursor-pointer">Login</a> now.</p>
      </div>
    </div>
  </div>
  <!---dashboard start-->
  <div class="container h-full px-6 py-24" v-else>
      <div class="p-20 bg-orange-200 mx-auto">
        <h1 class="text-orange-400 font-bold text-center mb-3">Wllcome to my Dashboard</h1>
        <div class="bg-white rounded-lg shadow-2xl md:flex">
          <img src="https://images.unsplash.com/photo-1593642532744-d377ab507dc8" alt="Laptop on Desk" class="md:w-1/3 rounded-t-lg md:rounded-l-lg md:rounded-t-none" />
          <div class="p-6">
            <h2 class="font-bold text-xl md:text-3xl mb-2 text-orange-700">Name: new name</h2>
            <h2 class="font-bold text-md md:text-md  mb-2 text-orange-700">Email: abc@gmail.com</h2>
            <h2 class="font-bold text-md md:text-md  mb-2 text-orange-700">Profession: Backend Developer (Laravel)</h2>
          </div>
        </div>
      </div>
   </div>
  <!--dashboard end-->
</section>
 <!-- registration page design -->

</template>

<style scoped>

</style>
