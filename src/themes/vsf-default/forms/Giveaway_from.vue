<template>
  <div class="forms_detail giveaway">
    <form @submit.prevent="submitForm" v-if="!submitted">
      <label for="firstName">First Name:</label>
      <input placeholder="First Name" class="first_name cstm-input" id="first-name" type="text" v-model="formData.firstName" required />

      <label for="middleName">Middle Name:</label>
      <input placeholder="Middle Name" class="middle_name cstm-input" id="middle-name" type="text" v-model="formData.middleName" />

      <label for="lastName">Last Name:</label>
      <input placeholder="Last Name" class="last_name cstm-input" type="text" v-model="formData.lastName" required />

      <label for="email">Email:</label>
      <input placeholder="Email" class="email cstm-input" id="from_email" type="email" v-model="formData.email" required />

      <label for="age">Age:</label>
      <input placeholder="Age" class="age cstm-input" type="number" v-model="formData.age" required />

      <label class="gender" for="gender">Gender:</label>
      <select v-model="formData.gender" required>
        <option value disabled>Gender</option>
        <option value="male">Male</option>
        <option value="female">Female</option>
        <option value="other">Other</option>
      </select>

      <label for="dob">Date of Birth:</label>
      <input placeholder="Date of Birth" class="dob cstm-input" type="date" v-model="formData.dob" required />

      <label for="phoneNumber">Phone Number:</label>
      <input placeholder="Phone Number" class="phonenumber cstm-input" type="tel" v-model="formData.phoneNumber" required />

      <label for="faxNumber">Fax Number:</label>
      <input placeholder="Fax Number" class="faxnumber" type="tel" v-model="formData.faxNumber" />

      <label for="mailingAddress">Mailing Address:</label>
      <textarea placeholder="Mailing Address" class="mailing_address cstm-input" v-model="formData.mailingAddress" ></textarea>

      <label for="lastJobTitle">Last Job Title:</label>
      <input placeholder="Last Job Title" class="last_job cstm-input" type="text" v-model="formData.lastJobTitle" />

      <label for="lastJobExperience">Last Job Experience In:</label>
      <input placeholder="Last Job Experience In" class="last_experience cstm-input" type="number" v-model="formData.lastJobExperience" />

      <label class="year" for="experienceUnit">Year or Month:</label>
      <select v-model="formData.experienceUnit">
        <option value="years">Years</option>
        <option value="months">Months</option>
      </select>

      <label for="portfolioUrl">Portfolio or CV URL Link:</label>
      <input placeholder="Portfolio or CV URL Link" class="portfolio cstm-input"  type="url" v-model="formData.portfolioUrl" />

      <label for="description">Description (100-125 words):</label>
      <textarea class="description" v-model="formData.description" required></textarea>
      <button class="submit" type="submit">Submit</button>
    </form>
    <div v-else>
      <div class="thanks-message">
        <img class="thumbs-img" src="../assets/icons/thumbs-up.png">
        <p class="message">Thank you for submitting the form!</p>
      </div>
    </div>
  </div>
</template>

<script>
import './form.css'
export default {
  name: 'Giveaway_from',
  data() {
    return {
      formData: {
        firstName: "",
        middleName: "",
        lastName: "",
        age: null,
        gender: "",
        dob: "",
        email: "",
        phoneNumber: "",
        faxNumber: "",
        mailingAddress: "",
        lastJobTitle: "",
        lastJobExperience: null,
        experienceUnit: "years",
        portfolioUrl: "",
        description: "",
      },
      submitted: false,
    };
  },
  methods: {
    submitForm() {
      // Check if the form is valid before sending the email
      if (this.validateForm()) {
        // Send the email using the form data
        Email.send({
          Host : "smtp.elasticemail.com",
          Username : "humanabstract9@gmail.com",
          Password : "1B9F22996B66A8740340E33D305549C344C2",
          To : 'humanabstract9@gmail.com', 
          From : 'humanabstract9@gmail.com',
          Subject: 'Form Submission',
          Body: this.getEmailBody(),
        }).then((message) => {
          this.submitted = true;
        });
      } else {
        console.error("Form data is missing or incomplete.");
      }
    },
    validateForm() {
      // Implement form validation here
      // You can check if required fields are filled, validate email, etc.
      // Return true if the form is valid, false otherwise.
      return (
        this.formData.firstName &&
        this.formData.lastName &&
        this.formData.email &&
        this.formData.description
      );
    },
    getEmailBody() {
      // Create the email body with form data
      return `
        First Name: ${this.formData.firstName}
        Middle Name: ${this.formData.middleName}
        Last Name: ${this.formData.lastName}
        Age: ${this.formData.age}
        Gender: ${this.formData.gender}
        Date of Birth: ${this.formData.dob}
        Email: ${this.formData.email}
        Phone Number: ${this.formData.phoneNumber}
        Fax Number: ${this.formData.faxNumber}
        Mailing Address: ${this.formData.mailingAddress}
        Last Job Title: ${this.formData.lastJobTitle}
        Last Job Experience: ${this.formData.lastJobExperience} ${this.formData.experienceUnit}
        Portfolio or CV URL Link: ${this.formData.portfolioUrl}
        Description: ${this.formData.description}
      `;
    },
  },

  mounted(){
    const firstNameInput = document.querySelector('.first_name');
    const middleNameInput = document.querySelector('.middle_name');
    const lastNameInput = document.querySelector('.last_name');
    const ageNameInput = document.querySelector('.age');
    const genderNameInput = document.querySelector('.gender');
    const emailNameInput = document.querySelector('.email');
    const phonenumberNameInput = document.querySelector('.phonenumber');
    const faxnumberNameInput = document.querySelector('.faxnumber');
    const mailing_addressNameInput = document.querySelector('.mailing_address');
    const last_jobNameInput = document.querySelector('.last_job');
    const last_experienceNameInput = document.querySelector('.last_experience');
    const yearNameInput = document.querySelector('.year');
    const portfolioNameInput = document.querySelector('.portfolio');
    const descriptionNameInput = document.querySelector('.description');

  


  },
};
</script>






