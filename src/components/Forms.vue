<template>
  <form-wizard @onComplete="onComplete">
    <tab-content title="About You" :selected="true">
      <div class="form-group">
        <label for="fullName">Full Name</label>
        <input
          type="text"
          class="form-control"
          :class="hasError('fullName') ? 'is-invalid' : ''"
          placeholder="Enter your name"
          v-model="formData.fullName"
        />
        <div v-if="hasError('fullName')" class="invalid-feedback">
          <div class="error" v-if="!$v.formData.fullName.required">
            Please provide a valid name.
          </div>
        </div>
      </div>
      <div class="form-group">
        <label for="email">Your Email</label>
        <input
          type="email"
          class="form-control"
          :class="hasError('email') ? 'is-invalid' : ''"
          placeholder="Enter your email"
          v-model="formData.email"
        />
        <div v-if="hasError('email')" class="invalid-feedback">
          <div class="error" v-if="!$v.formData.email.required">
            Email field is required
          </div>
          <div class="error" v-if="!$v.formData.email.email">
            Should be in email format
          </div>
        </div>
      </div>
      <div class="form-group">
        <label for="phone">Your Phone</label>
        <input
          type="text"
          class="form-control"
          :class="hasError('phone') ? 'is-invalid' : ''"
          placeholder="Enter your phone"
          v-model="formData.phone"
        />
        <div v-if="hasError('phone')" class="invalid-feedback">
          <div class="error" v-if="!$v.formData.phone.required">
            phone field is required
          </div>
            <div class="error" v-if="!$v.formData.phone.numeric">
             Should be in phone format
          </div>
        </div>
      </div>
    </tab-content>
    <tab-content title="About your Company">
      <div class="form-group">
        <label for="companyName">Name of last company have u worked in :</label>
        <input
          type="text"
          class="form-control"
          :class="hasError('companyName') ? 'is-invalid' : ''"
          placeholder="Enter Name of last company have u worked in"
          v-model="formData.companyName"
        />
        <div v-if="hasError('companyName')" class="invalid-feedback">
          <div class="error" v-if="!$v.formData.companyName.required">
            Please provide a valid company name.
          </div>
        </div>
      </div>
      <div class="form-group">
        <label for="salary">last salary :</label>
        <input
          type="text"
          class="form-control"
          :class="hasError('salary') ? 'is-invalid' : ''"
          placeholder="Enter last salary"
          v-model="formData.salary"
        />
        <div v-if="hasError('salary')" class="invalid-feedback">
          <div class="error" v-if="!$v.formData.salary.required">
            Please provide last salary.
          </div>
          <div class="error" v-if="!$v.formData.salary.numeric">
            Should be a valid value.
          </div>
        </div>
      </div>
    </tab-content>
    <tab-content title="Finishing Up">
      <div class="form-group">
        <h1>You results :</h1>
        <table class="table table-user-information">
          <tbody>
            <tr>
              <td>full Name :</td>
              <td>{{ formData.fullName }}</td>
            </tr>
            <tr>
              <td>Number phone :</td>
              <td>{{formData.phone}}</td>
            </tr>

            <tr>
              <td>Email :</td>
              <td>{{formData.email}}</td>
            </tr>

            <tr>
              <td>last Company name:</td>
              <td>{{formData.companyName}}</td>
            </tr>

            <tr>
              <td>last salary:</td>
              <td>{{formData.salary}}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </tab-content>
  </form-wizard>
</template>


<script>
import { FormWizard, TabContent, ValidationHelper } from "vue-step-wizard";
import "vue-step-wizard/dist/vue-step-wizard.css";
import { required } from "vuelidate/lib/validators";
import { email } from "vuelidate/lib/validators";
import { numeric } from "vuelidate/lib/validators";

export default {
  name: "Forms",
  components: {
    FormWizard,
    TabContent,
  },
  mixins: [ValidationHelper],
  data() {
    return {
      formData: {
        fullName: "",
        email: null,
        phone: null,
        companyName: null,
        salary: null,
      },
      validationRules: [
        {
          fullName: { required },
          email: { required, email },
          phone: { required, numeric },
        },
        { companyName: { required }, salary: { required, numeric } },
      ],
    };
  },
  methods: {
    onComplete() {
      console.log(this.formData);
    },
  },
};
</script>