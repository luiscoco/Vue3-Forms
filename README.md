# vue-forms

https://codesandbox.io/p/github/luiscoco/Vue3_Sample5_Forms

https://stackblitz.com/github/luiscoco/Vue3_Sample5_Forms

In Vue 3, forms can be created and managed using the v-model directive, which provides two-way data binding between form input elements and the component's data. You can handle form submissions and perform validations using various Vue features and methods. Here's an example to demonstrate how forms can be used in Vue 3:
 
```vue
<template>
  <form @submit="handleSubmit">
    <label for="name">Name:</label>
    <input type="text" id="name" v-model="name" />

    <label for="email">Email:</label>
    <input type="email" id="email" v-model="email" />

    <button type="submit">Submit</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      email: ''
    };
  },
  methods: {
    handleSubmit(event) {
      event.preventDefault();

      // Perform validation or any other necessary logic
      if (this.name && this.email) {
        // Form is valid, perform further actions (e.g., submit to server)
        console.log('Form submitted:', { name: this.name, email: this.email });

        // Reset form fields
        this.name = '';
        this.email = '';
      } else {
        // Display an error message or handle invalid form state
        console.log('Form is invalid');
      }
    }
  }
};
</script>
``` 
 
In the above example, we have a simple form with two input fields for name and email. The v-model directive is used to bind the input values to the component's data properties name and email. The @submit event listener is attached to the form element to handle the form submission.

In the handleSubmit method, we prevent the default form submission behavior using event.preventDefault(). Then, you can perform any required validation or additional logic. In this case, we check if both the name and email fields have values. If the form is valid, you can proceed with further actions, such as submitting the form data to a server. In this example, we simply log the form data to the console and reset the form fields.

Note that you can add additional validation logic, error handling, and styling to enhance the form's functionality and user experience.

Here's the modified code that includes the <script lang="ts" setup> tag and utilizes the Composition API features in Vue 3:
 
```vue
<template>
  <form @submit="handleSubmit">
    <label for="name">Name:</label>
    <input type="text" id="name" v-model="name" />

    <label for="email">Email:</label>
    <input type="email" id="email" v-model="email" />

    <button type="submit">Submit</button>
  </form>
</template>

<script lang="ts" setup>
import { ref } from 'vue';

const name = ref('');
const email = ref('');

function handleSubmit(event: Event) {
  event.preventDefault();

  // Perform validation or any other necessary logic
  if (name.value && email.value) {
    // Form is valid, perform further actions (e.g., submit to server)
    console.log('Form submitted:', { name: name.value, email: email.value });

    // Reset form fields
    name.value = '';
    email.value = '';
  } else {
    // Display an error message or handle invalid form state
    console.log('Form is invalid');
  }
}
</script>
```

In the modified code, we use the <script lang="ts" setup> tag to enable the use of TypeScript and the Composition API. The ref function from the Composition API is imported and used to create reactive variables name and email. The values of these variables are accessed using the .value property.

The handleSubmit function is now typed with Event to specify the type of the event object. Inside the function, we can directly use the reactive variables name.value and email.value to access the input values. The rest of the code remains the same, including the form submission logic and form reset.
  
## The event.preventDefault() method
It is used to prevent the default behavior of an event. In the context of form submission, calling event.preventDefault() is typically used to prevent the form from being submitted in the traditional way, which would cause a page reload or navigation.

By default, when a <form> element is submitted, the browser performs a full page refresh or navigates to the URL specified in the action attribute of the form. This default behavior might not be desirable in many cases, especially in single-page applications built with frameworks like Vue.

In Vue, when you handle form submission using methods or event listeners, you often want to perform custom logic, such as data validation, making an asynchronous request, or updating the UI, without triggering a page reload or navigation. By calling event.preventDefault(), you prevent the default behavior of form submission and take full control over what happens when the form is submitted.

Instead of the default behavior, you can then write your own logic to handle the form data, perform validations, make API requests, update the component's state, or perform any other necessary actions. This gives you the flexibility to implement custom behavior and maintain the application's state and UI without disrupting the overall user experience.

In the provided code example, calling event.preventDefault() in the handleSubmit function ensures that the form does not get submitted in the traditional way, allowing you to perform custom actions like logging the form data and resetting the form fields.

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
