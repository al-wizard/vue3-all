<template>
  <div class="container">
    

    <div class="card my-3">
        <div class="card-body">
          <div class="card-title text-left"><h4>{{ title }}</h4></div>
          <div class="card-text">
              <div class="input-group my-4">
                <input class="form-control" type="text" ref="name">
                  <div class="input-group-append">
                    <button class="btn btn-outline-secondary" @click="handleClick">click me</button>
                  </div>
              </div>
              
                    <teleport to=".modals" v-if="showModal">
                        <Modal theme="sale" @close="toggleModal">
                          <h1>Givaway!</h1>
                          <p>Grab your swag for half price!</p>

                          <template v-slot:links>
                            <a href="#">sign up now</a> <a href="#">more info</a>
                          </template>
                        </Modal>
                    </teleport>
                <button class="my-2 btn" @click="toggleModal">Toggle Modal</button>
          </div>
        </div>
      </div>

    <div class="card">
      <div class="card-body">
        <div class="card-text">
          <SignupForm />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Modal from './components/Modal'
import SignupForm from './components/SignupForm'
  export default {
    name: 'App',
    components: { Modal, SignupForm },
    data() {
      return {
        title: 'My First Vue App',
        header: 'Sign Up',
        text: 'Hurry up man or you miss a lot of things!',
        showModal: false
      }
    },
    methods: {
      handleClick() {
        console.log(this.$refs.name)
        this.$refs.name.classList.add('active')
        this.$refs.name.focus()       
      },
      toggleModal(){
        this.showModal = !this.showModal
      }
    }
  }
</script>

<style>
    #app, .modals {
      font-family: Avenir, Helvetica, Arial, sans-serif;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
      text-align: center;
      color: #2c3e50;
      margin-top: 60px;
    }
</style>
