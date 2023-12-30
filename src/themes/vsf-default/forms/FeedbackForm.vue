<template>
    <div class="forms_detail Career">
      <form @submit.prevent="submitForm" v-if="!submitted">
        <label for="firstName">First Name:</label>
        <input placeholder="First Name" class="first_name cstm-input" id="first-name" type="text" v-model="formData.firstName" required />
  
        <label for="middleName">Middle Name:</label>
        <input  placeholder="Middle Name" class="middle_name cstm-input" id="middle-name" type="text" v-model="formData.middleName" />
  
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
        <input placeholder="Date of Birth " class="dob cstm-input" type="date" v-model="formData.dob" required />
  
        <label for="phoneNumber">Phone Number:</label>
        <input placeholder="Phone Number" class="phonenumber cstm-input" type="tel" v-model="formData.phoneNumber" required />
  
        <label for="feedback">Feedback (100-125 words):</label>
        <textarea placeholder="Feedback (100-125 words)" class="feedback cstm-input" v-model="formData.feedback" required></textarea>
  
        <label for="imageUpload">Image Upload:</label>
        <input placeholder="Image Upload" class="image_upload cstm-input" type="file" @change="handleImageUpload" accept="image/*" />
  
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
    name: 'CareerForm',
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
          // Send the email to your email address
          Email.send({
            Host: "smtp.elasticemail.com",
            Username: "humanabstract9@gmail.com",
            Password: "1B9F22996B66A8740340E33D305549C344C2",
            To: 'support@humansabstract.com',
            From: 'humanabstract9@gmail.com',
            Subject: 'Form Submission',
            Body: this.getEmailBody(),
          }).then((message) => {
            this.submitted = true;
            this.sendThankYouEmail();
          });
      } else {
      console.error("Form data is missing or incomplete.");
          }
        },
        sendThankYouEmail() {
          Email.send({
            Host: "smtp.elasticemail.com",
            Username: "humanabstract9@gmail.com",
            Password: "1B9F22996B66A8740340E33D305549C344C2",
            To: this.formData.email,
            From: 'humanabstract9@gmail.com',
            Subject: 'Thank You for Submitting the Form',
            Body: 'Thank you for submitting the form. We appreciate your interest!',
          }).then((message) => {
            console.log('Thank-you email sent to the user.');
          });
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
        Feedback (100-125 words): ${this.formData.feedback}
        Image Upload: ${this.formData.imageUpload}
        `;
      },
    },
  
    mounted(){
      const firstNameInput = document.querySelector('.first_name');
    const middleNameInput = document.querySelector('.middle_name');
    const lastNameInput = document.querySelector('.last_name');
    const ageInput = document.querySelector('.age');
    const genderInput = document.querySelector('.gender');
    const emailInput = document.querySelector('.email');
    const phoneNumberInput = document.querySelector('.phonenumber');
    const faxNumberInput = document.querySelector('.feedback');
    const imageUpload = document.querySelector('.image_upload');
  
    },
  };
  </script>
    <style scoped>

@media only screen and (min-device-width: 768px) and (max-device-width: 991px) {
  .forms_detail.Career {
              padding-bottom: 50px !important;
          }
    
}

    @media only screen and (min-device-width: 320px) and (max-device-width: 767px) {
          .forms_detail.Career {
              padding-bottom: 50px !important;
          }
    
    }   
    
    
    
    </style>
  