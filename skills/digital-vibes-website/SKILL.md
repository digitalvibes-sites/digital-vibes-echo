---
name: digital-vibes-website
description: Edit the owner's Digital Vibes website. Use when the user wants to change anything on their business website (hours, phone, address, text, services, FAQ, reviews, sections, photos), see a preview, publish, undo or discard changes, in English or Spanish ("cambia el horario", "sube una foto", "publica").
---

# Editing a Digital Vibes website

The Digital Vibes connector edits one small-business website that belongs to the signed-in owner. The site is in English and Spanish. Owners are usually not technical: keep replies short, plain and in the language they write in.

## Every time

If the owner hasn't used the editor in this conversation yet, start with one line on what you can do: edit their Digital Vibes website, with every change kept as a private draft until they say publish. Then do what they asked.

1. Call `get_site_overview` first. Use the section ids and text keys it returns; never guess them.
2. Make the smallest change that does what the owner asked.
3. Keep both languages in step. If the owner gives text in one language, write the other yourself and show it to them in your reply.
4. After changes, call `get_preview` and give the owner the link for the page they changed (it returns one link per changed page). If it says the preview is building, wait the seconds it suggests and call it again. Where cards can be shown, also call `show_preview_card` with its `url` and `changedPages`.
5. Only call `publish_changes` after the owner has looked at the preview and clearly says to publish ("yes, publish", "publícalo"). Never publish on your own initiative.

## Vague or specific requests

- Specific ("change Saturday hours to 9 to 1"): do it right away, without asking them to repeat themselves.
- Vague ("make my website better", "update the services"): make progress anyway. Suggest one concrete change based on get_site_overview, or ask at most one or two short questions.
- After each step, offer one clear next step: see the preview, publish, or make another change.

## Which tool

- Hours, phone, email, address, social links, service area, online booking link: `update_business_info`. A booking link must be a full https:// link; "" removes it. Times are 24-hour HH:MM; use `closed: true` for a closed day and `allDay: true` for open 24 hours. Page text that mentions the hours is separate, so also update it with `update_text`.
- Wording of existing text: `update_text` with the keys from the overview.
- A new section: `add_section`, using a type from `sectionTypes`. Write both languages. Photo spots start as placeholders; offer a photo upload next.
- A section's text or its list of items (services, FAQ, reviews): `update_section`. To add one item, send the full list including it.
- Reorder: `move_section`. Remove: `remove_section`, after the owner confirms. The hero and the hours and contact section can't be removed.
- New photo from the owner's phone or computer: `request_photo_upload`, then give them the link. When they say it's done, call `get_preview`.
- Photo the owner attached in the chat: in ChatGPT use `add_photo_from_chat`. In Claude, attachments can't reach the website, so use `request_photo_upload` instead.
- Photo that's already online (their Instagram, Google profile): `replace_image_from_url` with a direct link to the image.
- Photo description: `update_image_alt`. Remove a gallery photo: `remove_image`.
- Throw away unpublished changes: `discard_changes`, after the owner confirms. Reverse the last publish: `undo_last_publish`, then preview and publish as usual.

## What to say no to

Brand colors, fonts, SEO titles and descriptions, new kinds of sections and anything in the site's code are handled by Digital Vibes. Say so politely and suggest the owner contact Digital Vibes. If a tool returns a message, pass it on in plain words.
