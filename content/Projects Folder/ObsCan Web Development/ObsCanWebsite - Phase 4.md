## Summary

This phase involved creation an application to monitor WhatsApp messages to a specific number and insert any incoming messages 'being the number of homeless people fed' into the database

-------------------------------------------------------------------
## Related Sections/Pre-Reading

- [[ObsCan Website - Project Outline]]
- [[Obscan Website - Phase 1]]
- [[ObsCan Website - Phase 2]]
- [[ObsCanWebsite - Phase 3]]

-------------------------------------------------------------------
## Content

### Choosing WhatsApp for Updates

Let’s be real—getting people to log into a database to update numbers was never going to happen. I mean, even the accountants I work with dodge updating an Excel sheet! Since the volunteers are already organizing on WhatsApp, why not make it as easy as sending a message? One message with the number of people fed, and boom, it’s in the database.

### Finding the Right Tool: Vonage for WhatsApp Integration

Next, I needed a way to connect WhatsApp to my database. After a little research (and a lot of confusion), I discovered that **Vonage** offers a Python-friendly API that lets me send and receive WhatsApp messages programmatically. Perfect! This way, volunteers can text a number, and the app will know exactly what to do.

### Hosting the App on a Web Server

Here’s the thing: if I want the app to respond to messages 24/7, it can’t just sit on my laptop. I needed it “out there” on the internet, always listening and ready to act when a new message arrives. So, I set up a web server using **Render** to host the app. Now, it’s live and always ready to add new feeding data whenever a message comes in.

### Building the App with SQL for Database Magic

Once the basics were set, I built the actual app! It’s a Python app that takes incoming WhatsApp messages and translates them into SQL commands to insert new records. So, when a volunteer texts in “120,” the app knows to add 120 people fed for that day into our Supabase database. Simple but effective!

### Testing with the Volunteers

Of course, I had to make sure it all worked smoothly. I did some test runs with the volunteers to make sure they could text numbers without issues and that each message went straight to the database. It was actually pretty fun watching the numbers pop up automatically!

### The Code is on GitHub

Want to dive into the code? Check out the full app on GitHub—feel free to take a look or even try it out yourself!

https://github.com/BanananaJuice/obscan-whatsapp_db_pusher