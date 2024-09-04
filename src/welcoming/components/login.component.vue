<script>
/*
 * @name register-developer
 * @description
 * This component is responsible for registering a new developer.
 * It emits an event to the parent component when the developer is registered.
 * @emits login
 */
export default {
  name: "login.component",
  data() {
    return {
      firstName: '',
      lastName: '',
      edad: 0,
      errors:[]
    }
  },
  methods: {
    /**
     * @method onSubmit
     * @description
     * This method is called when the form is submitted.
     * It emits the developer-registered event with the developer object.
     */
    onSubmit() {
      console.log("Registering developer");
    },

    checkForm:function(e) {
      if(this.firstName && this.lastName) return true;
      this.errors = [];
      if(!this.firstName) this.errors.push("firstName required.");
      if(!this.lastName) this.errors.push("lastName required.");

      if(this.edad<18) this.errors.push("Es menor de edad.por que te falta" + (18-this.edad));
      e.preventDefault();
    }
  }
}
</script>

<template>
  <div>
    <h2>New Developer</h2>
    <div>
      <form @submit.prevent="checkForm">

        <p v-if="errors.length">
          <b>Please correct the following error(s):</b>
          <ul>
            <li v-for="error in errors">{{ error }}</li>
          </ul>
        </p>

        <div>
          <label for="firstName">First Name</label>
          <input type="text" id="firstName" v-model="firstName" required/>
        </div>
        <div>
          <label for="lastName">Last Name</label>
          <input type="text" id="lastName" v-model="lastName" />
        </div>
        <div>
          <label for="edad">Edad</label>
          <input type="text" id="firstName" v-model.number="edad" />
        </div>
        <div>
          <button type="submit">Register</button>
        </div>
      </form>
    </div>
  </div>
</template>

<style scoped>

</style>