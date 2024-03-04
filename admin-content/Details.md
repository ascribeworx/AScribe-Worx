- Icons: https://fontawesome.com/icons

- Contact Us Image: https://www.freepik.com/free-vector/contact-us-concept-illustration_8690678.htm#query=contact%20us&position=3&from_view=keyword&track=ais&uuid=fff22875-2736-446c-91c0-d1edf374c27b

- To create illustrations: https://wepik.com/
- Download illustration vector images: https://www.freepik.com/

Carousels
1. 1st : technical article/blogs
2. 2nd: user-manual/step-to step guide
3. 3rd: software documentation/api documentation
4. 4th: language paraphrasing/document-translation (hindi, spanish, english)
5. 5th: logo design/ infant name suggestion


#### Discarded Contact Us
```html
    <div class="container">
        <h4>Get in touch with Us!</h4>

        <div class="container">
            <div class="row">
                <div class="col-6">
                    <img class="mx-5" src="./images/contact_us.gif" style="height: 350px; width: 450px;"
                        alt="Contact Us">

                    <div class="row">
                        <div class="col mt-3">
                            <i class="fa-solid fa-envelope"></i> <a href="mailto:worxascribe@gmail.com"
                                class="anchor anchor-hover">worxascribe@gmail.com</a>
                        </div>
                        <div class="col mt-3">
                            <i class="fa-solid fa-phone"></i> (+91) 79037 45948
                        </div>
                    </div> 
                    <i class="mt-3 me-3 fa-brands fa-square-facebook"></i>
                    <i class="mt-3 me-3 fa-brands fa-square-x-twitter"></i>
                    <i class="mt-3 me-3 fa-brands fa-linkedin"></i>
                    <i class="mt-3 fa-brands fa-square-instagram"></i>
                </div>
                <div class="col-6 mt-3">
                    <form>
                        <div class="row">
                            <div class="col mb-3">
                                <label for="firstName" class="form-label">First Name</label>
                                <input type="text" class="form-control" id="firstName" placeholder="" required>
                            </div>
                            <div class="col mb-3">
                                <label for="lastName" class="form-label">Last Name</label>
                                <input type="text" class="form-control" id="lastName" placeholder="" required>
                            </div>
                        </div>
                        <div class="mb-3">
                            <label for="emailID" class="form-label">Email address</label>
                            <input type="email" class="form-control" id="emailID" aria-describedby="emailHelp" required>
                        </div>
                        <div class="mb-3">
                            <label for="message" class="form-label">Message</label>
                            <textarea class="form-control" id="message" rows="5" required></textarea>
                        </div>
                        <button type="submit" class="float-end contact-button btn-sm btn-dark text-white">Send</button>
                    </form>
                </div>
            </div>
        </div>
    </div> 
```

#### Old Contact Us section
```html
    <div class="container py-5">
        <div class="row py-5 g-3">
            <div class="col-md-6 first_col">
                <h1 class="text-center mt-5">Get in Touch with Us
                </h1>
                <form class="p-4 mt-2">
                    <div class="mb-3">
                        <label for="name" class="form-label">Enter your Name</label>
                        <input type="text" class="form-control" id="name">
                    </div>
                    <div class="mb-3">
                        <label for="email" class="form-label">Enter your email ID</label>
                        <input type="email" class="form-control" id="email">
                    </div>
                    <div class="mb-3">
                        <label for="message" class="form-label">Enter your massage</label>
                        <textarea type="text" class="form-control" id="message" rows="3"></textarea>
                    </div>
                    <div class="mb-3">
                        <button class="btn btn-primary">Send Now</button>
                    </div>
                </form>
            </div>
            <div class="col-md-6 sec_col">
                <img src="./images/contact-us-image.svg" class="img-fluid">
            </div>
        </div>
        <div class="row-last">
            <div class="row row-cols-1 row-cols-md-3  p-3 text-white">
                <div class="col">
                    <h6><i class="fa-solid fa-phone"></i> Call Us&nbsp; </h6>
                    <p>
                        (+91) 79037 45948
                    </p>
                </div>
                <div class="col">
                    <h6><i class="fa-solid fa-envelope"></i> Email Us&nbsp; </h6>
                    <p><a href="mailto:worxascribe@gmail.com" class="anchor anchor-hover">worxascribe@gmail.com</a>
                    </p>
                </div>
                <div class="col">
                    <h6><i class="fa-solid fa-user-plus"></i> Follow Us </h6>
                    <p>
                        <i class="me-3 fa-brands fa-square-facebook"></i>
                        <i class="me-3 fa-brands fa-square-x-twitter"></i>
                        <i class="me-3 fa-brands fa-linkedin"></i>
                        <i class="fa-brands fa-square-instagram"></i>
                    </p>
                </div>
            </div>
        </div>
    </div>
```


```python

import Flask
    # Flask,
    # g,
    # redirect,
    # render_template,
    # Response,
    # request,
    # url_for,
    # session,


from flask_mail import Mail, Message

app = Flask(__name__)

# Configuring mail and extracting Password from file
email = "gotocoders@gmail.com"
f = open("credentials.txt", "r")
password = f.read()
f.close()


mail = Mail(app)

# Configuring email
app.config["MAIL_SERVER"] = "smtp.gmail.com"
app.config["MAIL_PORT"] = 465
app.config["MAIL_USERNAME"] = email
app.config["MAIL_PASSWORD"] = password
app.config["MAIL_USE_SSL"] = True
mail = Mail(app)


@app.route("/")
def home():
    return render_template("index.html")

@app.route("/about")
def about():
    return render_template("about-us.html")

@app.route("/contact", methods=["POST", "GET"])
def contact():
    if request.method == "POST":
        cname = request.form["name"]
        cemail = request.form["email"]
        cphone = request.form["phone"]
        cmessage = request.form["message"]
        contact = Contact(cname=cname, cemail=cemail, cphone=cphone, cmessage=cmessage)
        db.session.add(contact)
        db.session.commit()

        msg = Message(
            "UnTuned Contact Response",
            sender=email,
            recipients=[cemail],
        )
        msg.body = f"""
        Hi {cname}, 

        Thank you for contacting us. 

        We've recieved your message and will get back to you within 24 hours.
        
        Best Regards,
        Team UnTuned
        """
        mail.send(msg)

    return render_template("contact-us.html")
    
if __name__ == "__main__":
    app.run(debug=True)
```