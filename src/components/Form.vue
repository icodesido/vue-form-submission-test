<template>
  <main>
    <form 
      class="policy-form" 
      name='policy-form'
      role="form" 
      method="POST" 
      ref="policyForm"
      v-on:submit.prevent="submitPolicyForm">
      
      <p>Your details</p>
      <label for="title" class="policy-form__label" name="title">Title</label>
      <select id="title" class="policy-form__select" required>
        <option value="">Please select one</option>
        <option>Mr</option>
        <option>Mrs</option>
        <option>Ms</option>
      </select>

      <label for="first_name" class="policy-form__label">First name</label>
      <input id="first_name" type="input" class="policy-form__input" name="first_name" required>

      <label for="last_name" class="policy-form__label">Last name</label>
      <input id="last_name" type="input" class="policy-form__input" name="last_name" required>

      <p>Your business</p>
      <label for="ern" class="policy-form__label">Employee ERN</label>
      <input id="ern" type="input" class="policy-form__input" name="ern">

      <input id="ern_exempt" type="checkbox" class="policy-form__input" name="ern_exempt" required>
      <label for="ern_exempt" class="policy-form__label">We're either exempt from having an ERN or we can provide it within 30 days.</label>

      <label for="address" class="policy-form__label">Address</label>
      <textarea id="address" type="input" class="policy-form__input" name="address" required></textarea>

      <p>Your policy</p>
      <label for="policy_start_date" class="policy-form__label">Policy start date</label>
      <input id="policy_start_date" type="date" class="policy-form__input" name="policy_start_date" required>

      <p>Your account</p>
      <label for="password" class="policy-form__label">Password</label>
      <input id="password" type="password" class="policy-form__input" name="password" required>
      <label for="confirm_password" class="policy-form__label">Confirm password</label>
      <input id="confirm_password" type="password" class="policy-form__input" name="confirm_password" required>


      <div class="footer">
        <div class="footer__total">
          <p class="footer__header">Total premium</p>
          <p class="footer__amount">{{ currency }}{{ total}}</p>
          <p class="footer__tc">per monht. 0% APR, Tax inc.</p>
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
      firsName: '',
      lastName: '',
      employeeErn: '',
      address: '',
      policyStartDate: '',
      password: '',
      currency: '£',
      total: '223.50'
    }
  },
  name: 'Form',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
