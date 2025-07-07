# Email Setup Guide for Netzilo Contact Form

The contact form has been configured to send emails to `sales@netzilo.com` using EmailJS. Follow these steps to complete the setup:

## 1. Create EmailJS Account

1. Go to [EmailJS.com](https://www.emailjs.com/)
2. Sign up for a free account (allows 200 emails/month)
3. Verify your email address

## 2. Create Email Service

1. In your EmailJS dashboard, go to "Email Services"
2. Click "Add New Service"
3. Choose your email provider (Gmail, Outlook, etc.)
4. Follow the setup instructions for your provider
5. Note down your **Service ID** (e.g., `service_xyz123`)

## 3. Create Email Template

1. Go to "Email Templates" in your dashboard
2. Click "Create New Template"
3. Use this template content:

**Template Name:** `netzilo_contact_form`

**Subject:** `New Contact Form Submission - {{first_name}} {{last_name}}`

**Content:**
```
New contact form submission from Netzilo website:

Name: {{first_name}} {{last_name}}
Email: {{email}}
Company: {{company}}

Message:
{{message}}

---
This email was sent from the Netzilo contact form.
```

4. Set the "To Email" field to: `sales@netzilo.com`
5. Save the template and note down your **Template ID** (e.g., `template_abc456`)

## 4. Get Your Public Key

1. Go to "Account" > "General" in your EmailJS dashboard
2. Find your **Public Key** (e.g., `abcdef123456`)

## 5. Update the Contact Form

Replace the placeholder values in `contact/index.html`:

```javascript
// Replace these values with your actual EmailJS credentials:
emailjs.init("YOUR_PUBLIC_KEY");        // Replace with your Public Key
emailjs.send('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', templateParams)
//           ^Replace this^     ^Replace this^
```

## 6. Test the Setup

1. Open the contact page in your browser
2. Fill out the form with test data
3. Submit the form
4. Check `sales@netzilo.com` inbox for the test email
5. Verify the form shows a success message

## Alternative: Server-Side Solution

If you prefer a server-side solution, you can:

1. Create a simple Node.js/Express server with nodemailer
2. Deploy it to services like Netlify Functions, Vercel, or Heroku
3. Update the form to POST to your server endpoint

## Security Notes

- EmailJS public key is safe to expose in client-side code
- Consider setting up domain restrictions in EmailJS dashboard
- Monitor your email quota to avoid service interruption
- Set up email notifications for quota warnings

## Troubleshooting

- **Form not sending:** Check browser console for errors
- **Emails not received:** Verify EmailJS service configuration
- **Wrong template:** Ensure Template ID matches exactly
- **Quota exceeded:** Upgrade EmailJS plan or implement rate limiting

The contact form is now ready to send emails to `sales@netzilo.com` when visitors submit inquiries! 