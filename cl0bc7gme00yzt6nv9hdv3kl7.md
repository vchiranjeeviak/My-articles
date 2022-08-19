## Html A-Z

Hey everyone, I am writing this blog as a part of my #100DaysOfWeb3 . It's day 3 and I am writing whatever I learnt in past 2 days.

- Apart from the "HTML is not a programming language" joke, let's see what we need to know about HTML.

<h3>Let's take a shallow dive into how web works</h3>

- Until we know how web works, we can't fully appreciate any web technology.

<h4>Let's see how request-response cycle works in web.</h4>

1. A user sends a request to a server through his browser. This request can be made in many ways like clicking on a link, writing a url and hitting enter, searching etc.
2. Whenever a server receives a request, it sends back a response to the browser which sent the request, if the request is valid.

<h4>What's inside this response?</h4>

- Most of the times, it contains 3 files.
- One is a HTML file, one is CSS file and other one is JavaScript file.
- CSS and JavaScript files are not mandatory in a response but a HTML file is mandatory in every response.
- Most modern day applications contain all three of them.


<h4>What's the purpose of each of these files?</h4>

- HTML file brings the content that server wants to send as response.
- CSS file brings the styles which define how the content in HTML file is going to look on browser.
- JavaScript file brings the behaviour of this page. Like what happens when we click/hover on something etc. Any movement is taken care by JavaScript.

I think, by now we have answer to the question **Why HTML?**. 

<h2>HTML</h2>

<h4>What is HTML?</h4>

- **HTML** stands for **HyperText Markup Language**.
- And yes, it's not a programming language. A programming language involves logic.
- HTML doesn't have any logic. It just displays whatever we have written. We can't write a loop, if statement, switch-case etc.
- We use HTML to display different types of data. 

<h4>Elements and Tags</h4>

- An element in HTML is a way of displaying data. There are different ways in which we want to display our data such as headings, images, tables etc. These all are elements in HTML.
- A tag helps us in using these elements in our page.
- Some elements have both opening and closing tags. 

```HTML
<opening tag> </closing tag>
```

- Some elements have only one tag which is self closing.

```HTML
<self closing tag />
```


<h3>How to follow from here?</h3>

- I have created a simple HTML page which has zero CSS.
- Obviously it looks ugly.
- But I will link it here, I will use code whatever I have used to make it.
[Click here to see ugly looking plain HTML page](https://htmlbychiru.netlify.app/)

<h3>Doctype</h3>

- The doctype represents the type of the document.
- Each type of document has it's own doctype. For example HTML4 has it's own doctype and HTML5 has it's own doctype.
- It's the first line of a HTML document.
- The doctype for HTML5 looks like:

```HTML
<!DOCTYPE html>
``` 

**After doctype, then comes the "html" element, and it contains two elements which are "head" and "body". If a HTML document is considered as a tree, html is the root and head and body are it's children.**

```HTML
<html>
     <head>
     </head>
     <body>
     </body>
</html>
```

<h3>Head of HTML page</h3>

- Head contains the meta data.
- Meta data is the data about the html document like encoding (UTF or ASCII), title (which is visible on tab of the page in browser), styles (in some cases), script (JavaScript) etc. 

```HTML
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sample</title>
</head>
```

<h3>Body of HTML page</h3>

- Whatever we want to display as part of our page, we place them inside body.
        
<h4>Attributes</h4>

- Attributes are key/value pairs.
- They are properties which lets us define a tag more appropriately.
- A tag can have multiple attributes depending on the purpose.

<h4>Inline vs Block level elements </h4>

- Inline elements let other inline elements to be placed in the same line. (h, p, div etc )
- Block level elements push other elements to the next line. (img, a, span etc)
 
<h4>Text Data</h4>

HTML provides different elements to display text data. They are:
1. Headings (h1, h2, h3, h4, h5, h6).
2. Paragraph (p).
3. Anchor (a). An anchor tag needs **href** attribute which takes an url as value so that whenever that link is clicked, it takes it to that url given.


- **Headings** are used to display headings and each of them display in different sizes. We can change those sizes using CSS which is out of context for this blog (h1, h2, h3,..).
- **Paragraph** is used to display normal text (p).
- **Anchor** is used to display links (a).

```HTML
<h1>Hello Prendss..</h1>
<p><a href="https://github.com/vchiranjeeviak/sample_html">click here</a> to go to the github repository of this page.</p>
```

<h4>Lists</h4>

HTML has two types of lists. They are:
1. Ordered list (ol).
2. Unordered list (ul).


- **Ordered list** gives ordering to list items by numbering them.
- **Unordered list** doesn't give ordering to list items. It just places a symbol before list item.
- Both these list types have **list items** (li).

```HTML
<p>The order in which we need to learn frontend development is:</p>
<ol>
      <li>HTML</li>
      <li>CSS</li>
      <li>JavaScript</li>
 </ol>
 <p>To develop backend we need to know:</p>
 <ul>
       <li>A server side language.</li>
       <li>A database.</li>
 </ul>
```
<h4>Media</h4>

- We can also display images, audio, videos in HTML.
- **Images** (img) takes an attribute **src** which accepts the link or path to the image and **alt** attribute which accepts text to show if the image is not loaded or used by the screen readers.
- **Audio** (audio) has **source** element inside it which takes two attributes **src** to take link or path and **type** to take type of file.
- **Video** (video) also works same as audio except we use video tag instead of audio.

```HTML
<audio controls>
        <source src="horse.ogg" type="audio/ogg">
        <source src="horse.mp3" type="audio/mpeg">
        Your browser does not support the audio tag.
</audio>
```

- In the project I linked above, I used youtube video. When you click share on a youtube video, you will see an option called **embed**. If you click on it, it gives us a tag to use. I used the same thing.

```HTML
<iframe width="560" height="315" src="https://www.youtube.com/embed/UB1O30fR-EE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
```

<h4>Tables</h4>

When we want to display something in a tabular format, we use tables (table). There are two parts in a table. They are:
1. Table head (thead).
2. Table body (tbody).


- Generally, the top most row of a table is considered as **table head**.
- Everything else goes into **table body**.
- Head or Body, they are divided into **rows** (tr).
- Every row is divided into **cells** (td).
- To span a cell into multiple rows, we use **rowspan** attribute. 
- To span a cell into multiple columns, we use **colspan** attribute.
- **th** is used to make a cell bold.

```HTML
<table>
           <thead>
                       <th>Time</th>
                       <th>Weekdays</th>
                       <th>weekends</th>
            </thead>
            <tbody>
                        <tr>
                             <th>Morning</th>
                             <td rowspan="2">Boring</td>
                             <td rowspan="4">Chill</td>
                        </tr>
                        <tr>
                             <th>Afternoon</th>
                        </tr>
                        <tr>
                             <th>Evening</th>
                             <td rowspan="2">Chill</td>
                        </tr>
                        <tr>
                             <th>Night</th>
                        </tr>
            </tbody>
</table>
```

<h4>Forms</h4>

- **Forms** (form) are used to send some data from user to backend.
- A form can have multiple **inputs** (input).
- An input tag takes an important attribute **type** whose value decides what type of input it takes.
- Some types those are taken by input are: 
    1. text.
    2. email.
    3. password.
    4. date.
    5. submit.
    6. radio.
    7. file and many more.
- A form should have an input of type **submit** to submit the form.

```HTML
<form>
        <h4>Fill your details to see magic:</h4>
        <div>
            <label>Name:</label>
            <input type="text" name="name">
        </div>
        <br>
        <div>
            <label>Email:</label>
            <input type="email" name="email">
        </div>
        <br>
        <div>
            <label>password:</label>
            <input type="password" name="password">
        </div>
        <br>
        <div>
            <label>Date of Birth:</label>
            <input type="date" name="dob">
        </div>
        <br>
        <div>
            <label>Gender:</label>
            <input type="radio" name="gender" value="Female" id="female">
            <label for="female">Female</label>
            <input type="radio" name="gender" value="Male" id="male">
            <label for="male">Male</label>
            <input type="radio" name="gender" value="Others" id="others">
            <label for="others">Others</label>
        </div>
        <br>
        <label>What day it is?</label>
        <select name="day" id="day">
            <option value="monday">Monday</option>
            <option value="tuesday">Tuesday</option>
            <option value="wednesday">Wednesday</option>
            <option value="thursday">Thursday</option>
            <option value="friday">Friday</option>
            <option value="saturday">Saturday</option>
            <option value="sunday">Sunday</option>
        </select>
        <br>
        <br>
        <label>Upload pic of your beautiful face:</label>
        <input type="file" name="pic" id="pic">
        <br>
        <br>
        <input type="submit">
    </form>
```

<h4>Div and Span</h4>

- Both **div** and **span** are containerising elements.
- It means that we use them to containerise or group some part of document for some purposes, usually to apply some collective styling.
- The difference between div and span is that div is **block** level element and span is **inline** element.

<h4>Semantic HTML</h4>

- HTML5 supports semantic tags.
- Tags such as section, aside, header, footer etc.
- They work exactly same as a div. But their names help us understand code better by differentiating different parts of document with different names.