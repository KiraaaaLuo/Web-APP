# Flask-MongoDB Web App

## the title of my app
The title of my app is "Kira Luo's Flask-MongoDB Workshop". I changed it via the base.html under templates by rewriting the code as the following 

```ruby
    <header>
      <h1>Kira Luo's Flask-MongoDB Workshop</h1>
```

## a simple description of my app
My app has some changes and extra features developed upon the example app given to us.

Firstly, I changed the title of my app and and some other basic information given. For exmaple, on the footer, I added "Hope everyone is having fun here". Also, on the home page, I changed the background color into green for eye protection by adding the code in base.html:

```ruby
<body style="background-color:green;">
```
And I changed some description and subtitles by adding or changing codes in index.html. Also, I inserted a picture by adding the code:
```ruby
<img src="https://i.pinimg.com/originals/a1/28/7f/a1287fca7800a1a1c81b35ff22bf2369.jpg" alt="Cute Inspirational Quotes"
    width="400" height="400">
```

Besides, for the create_post page, I added 2 boxes here, "The Person you reply" and "The Score you want to give this person's post". Users could then repsond to other users and also give scores to their post. The former one would be texts and the later one should be a number. Thus, users can interact with other users. These 2 features need to change app.py by changing both create_post function and edit_post function, some blocks of code should be updated as the following:
```ruby
def edit_post(mongoid):

    name = request.form['fname']
    message = request.form['fmessage']
    response=request.form['fresponse']
    score=request.form['fscore'] 

    doc = {
        # "_id": ObjectId(mongoid), 
        "name": name, 
        "message": message, 
        "response":response,
        "score":score,
        "created_at": datetime.datetime.utcnow()
    }
```
```ruby
def create_post():
    name = request.form['fname']
    message = request.form['fmessage']
    response=request.form['fresponse'] #It is a new feature, users can respond to other users
    score=request.form['fscore'] #another new feature, give score to other users' comment

    doc = {
        "name": name,
        "message": message, 
        "response":response,
        "score":score,
        "created_at": datetime.datetime.utcnow()
```
If we want to these 2 features function properly, we should also change the edit.html and create.html, for edit.html, I added codes like:
```ruby
  <p>
    The Person you reply:
      <textarea type="text" id="fresponse" name="fresponse">{{doc.response}}</textarea>
  <p>
    The Score you want to give this person's post:
      <textarea type="number" id="fscore" name="fscore">{{doc.score}}</textarea>
```

For the create.html, I added codes like:
```ruby
  <p>
    The Person you reply:
      <textarea type="text" id="fresponse" name="fresponse"></textarea>
  <p>
    The Score you want to give this person's post:
      <textarea type="number" id="fscore" name="fscore"></textarea>
```

Moreover, on the All Posts page, I changed the way the information displayed. Formerly, it shows something like "Posted by steven at 04:03 on 27 April 2022". Since I added the feature of responding to other users and giving scores, I simply changed the information into "Posted by steven responded to kk given a score 7 at 04:03 on 27 April 2022". And users can edit them as well. This is done by changing the read.html:
```ruby
<p class="post">
            Posted by {{doc.name}} responded to {{doc.response}} given a score {{doc.score}} at {{ doc.created_at.strftime("%H:%M on %d %B %Y") }}
            </br>
```
And that is all changes I have made. 

## a link to the deployed copy of my app
The link to my app is https://i6.cims.nyu.edu/~kl3647/web-app-KiraaaLuo/flask.cgi/

Thanks for watching :) 

## Personal Info
This is an individual work

the full name: Kira Luo

NYU Net ID:kl3647

Links to GitHub accounts: https://github.com/dbdesign-assignments-spring2022/web-app-KiraaaLuo

