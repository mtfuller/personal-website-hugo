---
title: "Contact"
summary: "Feel free to send me a message and say hi."
keywords: ["contact", "Thomas Fuller", "message", "connect"]
draft: false
---

<form name="contact-form" accept-charset="utf-8" action="https://formspree.io/f/mrgrlabr" method="post">
    <label for="fullname">
      Full name
      <input type="text" id="fullname" name="fullname" placeholder="John Smith" required>
    </label>
    <label for="email">
      Email
      <input type="text" id="email" name="email" placeholder="john.smith@example.com" required>
    </label>
    <label for="reason">Reason</label>
    <select id="reason" required>
        <option value="Wanted to connect">Wanted to connect</option>
        <option value="Interested in your services">Interested in your services</option>
        <option value="Just wanted to say hi">Just wanted to say hi</option>
        <option value="Other">Other</option>
    </select>
    <label for="message">Message</label>
    <textarea id="message"></textarea>
    <input type="hidden" name="_subject" id="email-subject" value="Contact Form Submission">
    <div class="g-recaptcha" data-sitekey="6LePyEYcAAAAAKhnpMZoOrW8g9pV8wQh_PFDkPSr"></div>
    <button type="submit">Send Message</button>
</form>