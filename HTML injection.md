# HTML Injection

## Overview

HTML Injection is a web vulnerability that occurs when a website displays user input without properly sanitizing or validating it. If the application treats user input as HTML instead of plain text, an attacker can inject HTML code into the page.

HTML Injection is considered a client-side vulnerability because the malicious code is rendered and executed by the user's browser.

---

## Why Does HTML Injection Occur?

Many websites accept user input through forms, search bars, comments, usernames, or profile fields.

Example:

```html
<input type="text" id="name">
<button onclick="sayHi()">Submit</button>

<p id="output"></p>
```

JavaScript:

```javascript
function sayHi() {
    let name = document.getElementById("name").value;
    document.getElementById("output").innerHTML =
        "Hello " + name;
}
```

If a user enters:

```text
Pratham
```

The output becomes:

```text
Hello Pratham
```

However, if an attacker enters:

```html
<h1>YOU HAVE BEEN HACKED</h1>
```

The browser interprets this as HTML and renders:

# YOU HAVE BEEN HACKED

instead of displaying the text itself.

---

## Example of HTML Injection

### User Input

```html
<h1>Welcome!</h1>
```

### Vulnerable Code

```javascript
document.getElementById("output").innerHTML = userInput;
```

### Result

The browser renders the `<h1>` tag as HTML.

---

## Common HTML Injection Payloads

### Heading Injection

```html
<h1>Injected Heading</h1>
```

### Bold Text

```html
<b>Injected Bold Text</b>
```

### Italic Text

```html
<i>Injected Italic Text</i>
```

### Moving Text

```html
<marquee>Injected Text</marquee>
```

### Image Injection

```html
<img src="image.jpg">
```

---

## Why Is HTML Injection Dangerous?

An attacker may:

* Modify the appearance of a webpage.
* Deface a website.
* Trick users with fake messages.
* Display malicious content.
* Mislead users into revealing sensitive information.

Example:

```html
<h1 style="color:red">Website Compromised</h1>
```

---

## Relationship with Cross-Site Scripting (XSS)

HTML Injection is often considered a precursor to Cross-Site Scripting (XSS).

Comparison:

| HTML Injection          | XSS                        |
| ----------------------- | -------------------------- |
| Injects HTML            | Injects JavaScript         |
| Changes page appearance | Executes malicious scripts |
| Lower severity          | Higher severity            |

Example XSS payload:

```html
<script>alert('XSS')</script>
```

---

## Root Cause

The vulnerability usually occurs when developers use:

```javascript
innerHTML
```

instead of safer alternatives such as:

```javascript
textContent
```

or

```javascript
innerText
```

---

## Prevention and Mitigation

### 1. Sanitize User Input

Remove or escape dangerous HTML tags before displaying user input.

Example:

```html
<h1>Hello</h1>
```

becomes:

```html
&lt;h1&gt;Hello&lt;/h1&gt;
```

The browser now displays:

```text
<h1>Hello</h1>
```

instead of rendering it.

---

### 2. Use textContent Instead of innerHTML

Unsafe:

```javascript
element.innerHTML = userInput;
```

Safe:

```javascript
element.textContent = userInput;
```

---

### 3. Validate Input

Accept only expected characters and reject unnecessary HTML tags.

---

### 4. Implement Content Security Policy (CSP)

CSP helps reduce the impact of client-side injection attacks.

---

## Detection Techniques

When testing a web application:

1. Find an input field.
2. Enter HTML tags.

Example:

```html
<h1>Test</h1>
```

3. Observe the output.

If the browser renders the HTML instead of displaying it as text, the application may be vulnerable to HTML Injection.

---

## Key Takeaways

* Never trust user input.
* HTML Injection occurs when user input is rendered as HTML.
* Unsanitized input can modify the appearance of a webpage.
* Proper input validation and sanitization are essential.
* Using `textContent` instead of `innerHTML` significantly reduces risk.

---

## References

* OWASP: HTML Injection
* TryHackMe - Web Fundamentals
* MDN Web Docs - DOM Security
