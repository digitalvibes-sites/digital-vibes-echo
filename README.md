# Digital Vibes Echo

Edit your Digital Vibes website by asking Claude, in English or Spanish. Change your hours, phone number, address or online booking link, update any text, add or reorder sections like services, FAQ and reviews, and add new photos.

This plugin is for business owners whose website is built and hosted by [Digital Vibes Design](https://digitalvibes.design). You need a Digital Vibes account to sign in.

## Use it

1. Install the plugin, then connect Digital Vibes from its Connectors tab.
2. Sign in with the email you gave Digital Vibes. You'll get a code by email.
3. Ask Claude, for example: "What's on my website?" or "Change our Saturday hours to 9 to 1."

Every change is saved as a private draft. Claude sends you a preview link, and nothing goes live until you say "publish". You can also discard a draft or undo the last publish.

## What's inside

- A skill that tells Claude how to edit the site safely: look at the site first, keep English and Spanish in step, show a preview, and publish only when you say so.
- One remote MCP server, `https://edit.digitalvibes.design/mcp`. The plugin runs no local code, hooks or scripts.

## Data

- **What is sent:** the changes you ask for (text, business details, section changes), photos you upload through the upload link, and links to photos that are already online. They go to edit.digitalvibes.design, the Digital Vibes site editor.
- **Where it goes:** the editor saves each change as a draft in your website's code repository on GitHub and builds a private preview on Vercel. Uploaded photos pass briefly through Cloudflare R2 storage and are deleted after they are added to your site.
- **Sign-in:** handled by WorkOS. Only the website linked to your email can be edited.
- **What is kept:** a log of each change (who, what, when) so Digital Vibes can support you. Nothing is sent anywhere else.

Privacy policy: https://digitalvibes.design/privacy-policy
Terms: https://digitalvibes.design/terms
Support: hey@digitalvibes.design
