
This exercise will create a simple flask server with a small book library. A focus of this lesson is to set and call cookies for added convenience in loging into this server. 

# What Are Cookies?

Cookies, formally known as HTTP cookies, are text files with small pieces of information that are stored on a web browser. These small pieces of information are usually in the form of name-value pairs. The information that a cookie is composed of is sent by the server along with the response to the request sent by the web browser. The browser stores this information in the form of a cookie and sends it back to the same server with the later requests. This helps the server identify if the two requests are coming from the same browser.

# What Are Cookies Used For?

Cookies are used for remembering stateful information for logins and other purposes in the stateless HTTP protocol. The uses of cookies can be categorized into three broad categories.

First, cookies are useful for ***session management***. A website might generate a unique ID number for each visitor and store that ID number on each user's machine using a cookie file. One way that cookies are useful is that “they can be used for shopping carts on e-commerce sites”. Cookies are used for ensuring that the user is logged in for the entire session. It also helps in remembering the shopping carts, game scores, and other data within a session.

Cookies are also helpful for ***user personalization*** on a web browser. Cookies are helpful in remembering user preferences, themes, and other settings which makes it easy for users to configure page settings.

Another common way that cookies can be used for ***tracking activity***. Cookies are used for tracking users’ browsing behaviors and by websites to recommend products or send advertisements based on browsing history.

# What Is the Lifespan of a Cookie?

Session cookies are typically deleted when the session ends. The session start time and session end time is usually determined by the browser, which is based on the user activity. For permanent cookies, their lifespan is based on an expiration date and time. These types of cookies have a predetermined expiration date and time and that’s when they are deleted from the browser.

To forcefully remove, or pop, a cookie, you should set the cookie attribute `max_age` to 0 in the decorator function that does this. The code below shows how to do this for a general cookie:

``` python
@app.route('/delete-cookie/')

def delete_cookie():

    res = make_response("Your_desired_message")

    res.set_cookie('foo', 'bar', max_age=0)

    return res
```


# Application

## Setting cookies within code
Cookies are set and called within the template routes wihtin a try block of code that looks something like this:
``` python
try: 
    user = request.cookies.get("CookieName")
    return render_template('template.html')
```
In the event that a cookie has not been set, an `except` statement will be added to the try block:
``` python
try: 
    user = request.cookies.get("CookieName")
    return render_template('template.html')
except:
    return render_template("register.html")
```
where register.html refers to a template file with instruction for setting the cookie. 

## test
After initializing the app, login with the designated user name and password (in this case, testuser for both). 