# Exploiting an API endpoint using documentation

![api-6492491_1280](https://github.com/user-attachments/assets/e1e2a526-3b24-4744-8190-a8af005f1aea)

---
## Objective

- To solve the lab, we are supposed to find the exposed API documentation and delete `carlos`. We can login into our account using the following credentials: `wiener:peter`.



> **Required Knowledge to keep in mind** 
```
So as to solve this lab, we will need to know:
  - What API documentation is.
  - How API documentation may be useful to an attacker.
  - How to discover API documentation.
```

---

## Methodology

1. Click on **My account**.
<img width="635" alt="login section" src="https://github.com/user-attachments/assets/7ff15181-992c-414f-bc98-170c5ec8ffe6" />

Then, log in to the application with the credentials that we were given, `wiener:peter`(username:password respectively).

<img width="606" alt="logins" src="https://github.com/user-attachments/assets/983b23e3-63c5-4444-99cf-447ef065b5d4" />

---

2. Open Burp suite and get it ready for some action💪😎. If you don't have burp suite installed on your computer, you can download it from [here](https://portswigger.net/burp/releases/professional-community-2024-11-2?requestededition=community&requestedplatform=). You can download the **Professional Edition**, or the **Community Edition** depending on your OS.

With our Burp Suite up and running, get the proxy intercept on 🚧🚥.

<img width="192" alt="image" src="https://github.com/user-attachments/assets/eecc38d8-ece9-41de-aae1-0f1eae063dae" />

Update the email address on our browser with the *intercept* still being "on" on our burp suite, and we will now have captured some traffic, as shown below.👇

<img width="475" alt="captured traffic" src="https://github.com/user-attachments/assets/50639875-c745-44a7-8c6c-248f529a3f1c" />

---

3. On our Burp Suite, "right click" on the *Request* window which contains `PATCH /api/user/wiener` and select **Send to Repeater**.
<img width="476" alt="send to repeater" src="https://github.com/user-attachments/assets/e0c86d71-fcba-402b-a18c-4b302d9ade8c" />

---

4. Switch to the *Repeater* tab, and **[Send]** the  `PATCH /api/user/wiener` request.

    🚨Notice, This retrieves credentials for the user `wiener` on the *Response* window. Cool, right? 😏
   
   <img width="960" alt="Retrieved credentials" src="https://github.com/user-attachments/assets/238db794-8680-4570-9044-145abe3d1f0d" />

---

5. Time to play🕹️🎮 with the request until we get an API documentation so that we can solve the lab. It's going to be fun🥳.

Let;s try to remove the user `wiener` from the path of the request, so that the new endpoint is now `PATCH /api/user`, then send the request and see what will happen.

<img width="344" alt="weiner removal" src="https://github.com/user-attachments/assets/2f453bc7-d327-4506-bfca-e5404bebaa5f" />

This returns an **"error"** `"Malformed URL: expecting an identifier"` 😪💔. Ooh mehn!😫

But even the reason being behind the error is that there is no *user identifier* ... 

It is like calling out someone, that you don't know and you are standing at a distance, and you don't know their name, and they are in a big crowd, chances are; you won't even know where to start.😕💁

<img width="715" alt="error 1" src="https://github.com/user-attachments/assets/3cfbbc23-8b13-4fca-9a07-f2739324aea2" />

---

6. We proceed by removing `/user` from the path of the request, so that the endpoint reads `PATCH /api`, then **[Send]** the request.

Hurray!!! 🎆🎉🎊. 

Notice the error is gone? 😁😉 That's a good sign.

<img width="721" alt="response" src="https://github.com/user-attachments/assets/dd18609e-8883-4812-a182-9e14e74e959e" />

However, in some Burp Suites, depending on the configurations set, the **Response** does not return any HTML or further information back. For my case, I have used the default configurations on Burp Suite, meaning there are no changes I have made in my Burp Suite settings after downloading it...everything is apparently on default ⚙️.

---
> What you can do is;

7. Right click on the *Response* and select **[Show response in browser]**.

<img width="362" alt="Repsonse in browser" src="https://github.com/user-attachments/assets/766bec37-81b7-4d53-8a23-922d945ad67c" />

Copy the URL so that we can investigate the Response further after altering with the path of the endpoint.

![response in browser](https://github.com/user-attachments/assets/d57e6cdb-35da-49d1-a21c-b5712dc87322)

---
8. Paste the URL we have copied from our Burp Suite onto a web browser.

There we go! An API documentation that is pretty interactive 🤓.
It has the different API functions in a nice little table with more details about them.

<img width="650" alt="API doc in browser" src="https://github.com/user-attachments/assets/124c970a-1122-402f-b439-7d667117054a" />

---

9. Our mission was to eliminate `carlos` using the `DELETE` function in the API.

When I hovered the mouse on one of the rows, I noticed the delete row can be selected, and upon clicking on it, I was prompted to enter a *username: String*...

..and, Bye Bye `carlos`!😏 "...

<img width="584" alt="enemy on sight" src="https://github.com/user-attachments/assets/67b48d9f-72b1-4f86-a34f-7282056ffe71" />

And just like that... 'adios muchachas!'👋...peace!💆✌️

> Don't Forget our Mission Objective was: `"...find the exposed API documentation and delete [carlos]`

<img width="512" alt="image" src="https://github.com/user-attachments/assets/efc33ac9-64e5-401b-9bee-ae816c750842" />

⭐ Mission complete on 'status 200'😎

<img width="338" alt="final pic" src="https://github.com/user-attachments/assets/3a7c329f-8dab-49f3-903d-454ecfb0a2f9" />

And just like that, we have our lab solved. 

---

### Conclusion
It's quite fascinating that as hacker🧑🏻‍💻, once you get such a table on your hands🤲 with the capabilities of deleting someone elses username from an application after gaining access to an API documentation like that...It can be quite destructive💣💥 and can cause frustrations 😣, and the app may lose its users. 

I can imagine if it were Facebook or X 😂 and one lands on such a documentation, with the delete feature on it...the guy(hacker) can take a username, in this case, for a user who uses the app, maybe for business 💰🪙 purposes on a daily basis, and that is all they got so that their business can run. A blackmail can take place😂😂😂. It would be so evil😭 that I can't imagine being in the business-person's shoes.

---

### Reference

[PortSwigger](https://portswigger.net/web-security/learning-paths/api-testing) - Web Security Academy - API Testing

---
### Date Completed

- Jan 8 2024
