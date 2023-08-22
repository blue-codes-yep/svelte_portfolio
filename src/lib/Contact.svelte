<script lang="ts">
  import { onMount } from 'svelte';

  let name: string = '';
  let email: string = '';
  let subject: string = '';
  let message: string = '';

  function handleSubmit(event: Event): void {
    event.preventDefault();

    // Basic email validation
    const emailPattern = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
    if (!emailPattern.test(email)) {
      alert('Please enter a valid email address.');
      return;
    }

    // Here you can send the form data to a server or handle it as needed
    console.log('Form submitted:', { name, email, subject, message });

    // Optionally, reset the form fields
    name = '';
    email = '';
    subject = '';
    message = '';
  }

  onMount(() => {
    // Additional initialization code if needed
  });
</script>


<section id="contact">
    <h1>Contact</h1>
    <form on:submit={handleSubmit}>
      <label for="name">Name:</label>
      <input type="text" id="name" bind:value={name} required />
    
      <label for="email">Email:</label>
      <input type="email" id="email" bind:value={email} required />
    
      <label for="subject">Subject:</label>
      <input type="text" id="subject" bind:value={subject} />
    
      <label for="message">Message:</label>
      <textarea id="message" bind:value={message} required></textarea>
    
      <button type="submit">Send</button>
    </form>
  
  </section>
  
  <style>
    form {
      max-width: 600px;
      margin: 0 auto;
      padding: 100px;
      background-color: var(--background-color);
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
  
    label {
      display: block;
      font-weight: bold;
      margin-bottom: 5px;
    }
  
    input,
    textarea {
      width: 100%;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
      font-size: 16px;
      margin-bottom: 20px;
      transition: border-color 0.3s ease;
    }
  
    input:focus,
    textarea:focus {
      border-color: #007bff;
      outline: none;
    }
  
    textarea {
      resize: vertical;
      min-height: 100px;
    }
  
    button {
      padding: 10px 20px;
      background-color: #007bff;
      color: #fff;
      border: none;
      border-radius: 5px;
      font-size: 16px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
  
    button:hover {
      background-color: #0056b3;
    }
  </style>