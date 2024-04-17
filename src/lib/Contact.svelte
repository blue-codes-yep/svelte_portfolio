<script lang="ts">
  import emailjs from "@emailjs/browser";

  let name: string = "";
  let email: string = "";
  let subject: string = "";
  let message: string = "";

  function handleSubmit(event: Event): void {
    event.preventDefault();

    // Basic email validation
    const emailPattern = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
    if (!emailPattern.test(email)) {
      alert("Please enter a valid email address.");
      return;
    }

    // Prepare the data to be sent
    const templateParams = {
      from_name: name,
      from_email: email,
      subject: subject,
      message: message
    };

    emailjs.send("service_3l5x6vo", "template_m2ljvc6", templateParams, "2g3dRHAuSfMG0NL-6")
      .then((response) => {
        console.log("SUCCESS!", response.status, response.text);
        // Reset the form fields after successful email sending
        name = "";
        email = "";
        subject = "";
        message = "";
        alert("Your message has been sent successfully!");
      })
      .catch((err) => {
        console.log("FAILED...", err);
        alert("Failed to send the message, please try again.");
      });

  }
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
    <textarea id="message" bind:value={message} required />

    <button type="submit">Send</button>
  </form>
</section>

<style>
  form {
    border: 2px solid var(--border-color);
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
