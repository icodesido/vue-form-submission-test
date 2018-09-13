<template>
  <main>
    <form 
      class="policy-form" 
      name='policy-form'
      role="form" 
      method="POST" 
      ref="policyForm"
      v-on:submit.prevent="submitPolicyForm">

    <div class="errors" v-if="!reference" v-for="error in errors" v-bind:key="error">{{ error }}</div>
    <div class="reference" v-if="reference">Your reference number is: 
      <strong class="reference-number">{{ reference }}</strong>
    </div>

      <fieldset class="policy-form__fieldset">
        <legend class="policy-form__legend">Your details</legend>

        <label for="title" class="policy-form__label">Title</label>
        <select id="title" class="policy-form__select" name="title" v-model="title">
          <option value="">Please select one</option>
          <option>Mr</option>
          <option>Mrs</option>
          <option>Ms</option>
        </select>

        <label for="first_name" class="policy-form__label">First name</label>
        <input id="first_name" type="input" class="policy-form__input" name="first_name" v-model="first_name">

        <label for="last_name" class="policy-form__label">Last name</label>
        <input id="last_name" type="input" class="policy-form__input" name="last_name" v-model="last_name">

      </fieldset>

      <fieldset class="policy-form__fieldset">
        <legend class="policy-form__legend">Your business</legend>

        <label for="ern" class="policy-form__label">Employee ERN</label>
        <input id="ern" type="input" class="policy-form__input" name="ern" v-model="ern">

        <div class="checkbox__container">
          <input id="ern_exempt" type="checkbox" class="policy-form__checkbox" name="ern_exempt" v-model="ern_exempt" value="true">
          <label for="ern_exempt" class="policy-form__label--checkbox">We're either exempt from having an ERN or we can provide it within 30 days.</label>
        </div>

        <label for="address" class="policy-form__label">Premises address</label>
        <textarea id="address" type="input" class="policy-form__input policy-form__textarea" name="address" v-model="address"></textarea>
      </fieldset>

      <fieldset class="policy-form__fieldset">
        <legend class="policy-form__legend">Your policy</legend>
        <label for="policy_start_date" class="policy-form__label">Policy start date</label>
        <input id="policy_start_date" type="date" class="policy-form__input" name="policy_start_date" v-model="policy_start_date">
      </fieldset>

      <fieldset class="policy-form__fieldset">
        <legend class="policy-form__legend">Your account</legend>
        <label for="password" class="policy-form__label">Password</label>
        <input id="password" type="password" class="policy-form__input" name="password" v-model="password">
        <label for="password_confirmation" class="policy-form__label">Confirm password</label>
        <input id="password_confirmation" type="password" class="policy-form__input" name="password_confirmation" v-model="password_confirmation">
      </fieldset>

      <div class="footer">
        <div class="footer__total">
          <p class="footer__para">Total premium</p>
          <p class="footer__amount">{{ currency }}{{ total}}</p>
          <p class="footer__para">per monht. 0% APR, Tax inc.</p>
        </div>
        <button type="submit" ref="submit" class="policy-form__button">Confirm</button>
      </div>

    </form>
  </main>
</template>

<script>
export default {
  data() {
    return {
      title: '',
      first_name: '',
      last_name: '',
      ern: '',
      ern_exempt: true,
      address: '',
      policy_start_date: '',
      password: '',
      password_confirmation: '',
      currency: '£',
      total: '223.50',
      errors: [],
      reference: ''
    }
  },
  name: 'Form',
  methods: {

    submitPolicyForm() {

      //this.$refs.submit.classList.add('u-submitting');

      this.axios.post('https://dr-frontend-test-api.herokuapp.com/api/accounts', {
        title: this.title, 
        first_name: this.first_name,
        last_name: this.last_name,
        ern: this.ern,
        ern_exempt: this.ern_exempt,
        address: this.address,
        policy_start_date: this.policy_start_date,
        password: this.password,
        password_confirmation: this.password_confirmation,
      }).then(this.formSuccess, this.formError);
      },

      formSuccess(succ) {
        this.reference = succ.data.ref;
        window.scrollTo(0,0);
      },

      formError(err) {
        const errors = [...Object.values(err.response.data.errors)];
        this.errors = [].concat.apply([], errors);
        window.scrollTo(0,0);
      },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .policy-form {
    padding: 0 20px;
    font-size: 14px;
    background-color: #fafafa;
    border-top: 1px solid #f0f0f0;
  }

  .policy-form__fieldset {
    border: none;
    border-top: 1px solid #f0f0f0;
    margin: 20px 0 0 0;
    padding: 0;
  }

  .policy-form__legend {
    margin: 0;
    font-size: 12px;
    color: #aaa;
  }

  .policy-form__label {
    display: block;
    margin: 15px 0 8px 0; 
  }

  .policy-form__select {
    height: 32px;
    width: 198px;
    background-color: #fff;    
  }

  .checkbox__container {
    float: left;
    font-size: 10px;
    margin: 12px 0 20px 0;
  }

  .policy-form__checkbox {
    float: left;
    margin-right: 8px;
  }

  .policy-form__input {
    width: 228px;
    padding-left: 6px;
    height: 28px;
    font-size: 13px;
    box-sizing: content-box;
    border: 1px solid #979797;
    border-radius: 3px;
  }

  .policy-form__textarea {
    appearance: textfield;
    min-height: 89px;
  }

  .errors {
    color: #ff2c6f;
    margin: 20px 0;
  }

  .reference {
    margin: 20px 0;
  }

  .reference-number {
    display: block;
    font-size: 18px;    
    color: #ff2c6f;    
  }

  .footer {
    background-color: #ff2c6f;
    color: #fff;
    margin-left: -20px;
    width: 320px;
    height: 60px;
    padding: 10px 20px;
    margin-top: 40px;
    display: flex;
    align-items: center;
    justify-content: space-between;  
  }

  .footer__para {
    font-size: 10px;
    margin: 0; 
  }

  .footer__amount {
    font-size: 26px;
    margin: 0;
  }

  .policy-form__button {
    width: 130px;
    height: 40px;
    background-color: #f4b400;
    border: none;
    font-size: 16px;
    color: white;
  }
  .policy-form__button:hover,
  .policy-form__button:active,
  .policy-form__button:focus {
    transition: all .5s ease-in;
    background-color: #c79200;
  }
</style>
