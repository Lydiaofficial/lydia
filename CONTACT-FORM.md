# Making the contact form deliver

The form posts to Web3Forms and the message lands in your inbox.
No backend, no Cloudflare Functions, and it keeps working if you move host again.

## Setup, about two minutes

1. Go to web3forms.com. Either button gets you to the same place, so take
   whichever is offered. What you are after is an **Access Key**: a long
   string that looks like `a1b2c3d4-e5f6-7890-abcd-ef1234567890`.
   You give them the email address you want messages delivered to, they send
   the key to that address. There is nothing to configure and no form to build
   on their side, because the form lives in your HTML.
2. Copy the key out of that email.
3. In `index.html`, find this line near the top of the script:

       var FORM_KEY = 'YOUR_WEB3FORMS_ACCESS_KEY';

4. Paste the key between the quotes. Commit and push.

Until the key is set, the form refuses to send and says "Form key not set yet"
rather than pretending to work.

## What arrives

Subject line: `Portfolio: <their subject>`
Reply-to is set to their address, so hitting Reply in Gmail goes to them.
The body carries their message.

## Spam

A honeypot field called `botcheck` is submitted empty. Bots that fill every
field get discarded by Web3Forms. Free tier is 250 submissions a month.

## If you would rather not use a third party

Alternative: a Cloudflare Pages Function at `/functions/api/contact.js` that
calls the Resend API, with `RESEND_API_KEY` set as an environment variable in
the Pages dashboard. More control, more moving parts, and it needs a verified
sending domain. Ask and I will write it.

Worth knowing: the old free MailChannels route from Cloudflare Workers has been
discontinued, so "send email straight from a Worker for free" is no longer an
option.
