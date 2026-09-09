# HTTP & HTTPS Fundamentals

## What is HTTP?

HTTP stands for **Hypertext Transfer Protocol**.

It is a client-server protocol used for communication between a client (such as a web browser) and a web server.

For example, when I open:

```text
https://www.example.com
```

my browser sends an HTTP request to the server, and the server sends back an HTTP response.

HTTP is **stateless**. This means the server does not automatically remember previous requests from the same client.

Web applications create state at the application level using things such as:

* Cookies
* Session IDs
* Tokens

For example, after logging into a website, the server may give my browser a session cookie. The browser sends that cookie with later requests so the server knows that I am already authenticated.

---

# HTTP Methods

HTTP uses **methods** to tell the server what the client wants to do.

The main methods are:

| Method  | Purpose                                    |
| ------- | ------------------------------------------ |
| GET     | Retrieve data                              |
| POST    | Send/create data                           |
| PUT     | Replace/update data                        |
| DELETE  | Delete data                                |
| PATCH   | Partially update data                      |
| HEAD    | Retrieve headers without the response body |
| OPTIONS | Ask what methods/options are supported     |
| CONNECT | Establish a tunnel                         |
| TRACE   | Diagnostic loop-back request               |

The two methods I will encounter most often as a beginner are:

```text
GET
POST
```

---

# Understanding a URL

Example:

```text
https://www.iamlearning.thm/contact
```

Break it down:

```text
https://www.iamlearning.thm/contact
│       └──────────────────┘
│                │
│                └── Host
│
└── Scheme

/contact = Path
```

More clearly:

| Part   | Value                 | Meaning                         |
| ------ | --------------------- | ------------------------------- |
| Scheme | `https`               | Protocol used to communicate    |
| Host   | `www.iamlearning.thm` | Server/hostname being contacted |
| Path   | `/contact`            | Resource being requested        |

### Easy way to remember

```text
SCHEME://HOST/PATH
```

Example:

```text
https://www.iamlearning.thm/contact
```

```text
https://        → Scheme
www.iamlearning.thm → Host
/contact        → Path
```

---

# GET Request

A GET request is used to **retrieve a resource** from a server.

For example:

```http
GET /contact HTTP/1.1
Host: www.iamlearning.thm
```

The browser may send additional headers such as:

```http
User-Agent:
Accept:
Cookie:
```

The server processes the request and sends an HTTP response.

---

# HTTP Request → HTTP Response

The basic communication looks like this:

```text
            HTTP REQUEST
Browser ─────────────────────> Web Server
                                │
                                │
                                ▼
                           Process request
                                │
                                │
Browser <───────────────────── Web Server
            HTTP RESPONSE
```

The response contains:

1. **Status code**
2. **Response headers**
3. **Response body**

Example:

```http
HTTP/1.1 200 OK

Content-Type: text/html

<html>
    <body>
        <h1>Hello</h1>
    </body>
</html>
```

---

# Important HTTP Status Codes

| Code | Meaning                |
| ---- | ---------------------- |
| 200  | OK / successful        |
| 201  | Created                |
| 301  | Permanently redirected |
| 302  | Temporary redirect     |
| 400  | Bad Request            |
| 401  | Unauthorized           |
| 403  | Forbidden              |
| 404  | Not Found              |
| 500  | Internal Server Error  |

I should especially remember:

```text
200 → Success
301/302 → Redirect
400 → Bad request
401 → Authentication required
403 → Access forbidden
404 → Resource not found
500 → Server error
```

---

# Browser Developer Tools

I can inspect HTTP requests directly from a browser.

In Firefox/Chrome:

```text
F12
↓
Network
↓
Reload the page
↓
Click a request
```

The Network tab allows me to see information such as:

* Request URL
* HTTP method
* Status code
* Request headers
* Response headers
* Cookies
* Response body
* Remote IP address

This is important for cybersecurity because it lets me see how a web application communicates with its server.

---

# Cybersecurity Relevance

Understanding HTTP is important for security because many attacks involve manipulating or abusing HTTP requests.

Examples include:

* SQL Injection
* Cross-Site Scripting (XSS)
* Command Injection
* Path Traversal
* Authentication attacks
* Session attacks
* CSRF
* HTTP request smuggling

As a blue-team/security analyst, understanding normal HTTP traffic helps me recognize suspicious traffic.

For example:

```text
Normal:
GET /index.html

Potentially suspicious:
GET /../../../../etc/passwd
```

or:

```text
Normal:
GET /products?id=15

Potentially suspicious:
GET /products?id=15' OR '1'='1
```

The important idea is:

> **To detect malicious web traffic, I first need to understand what normal web traffic looks like.**

---

# Quick Revision

## URL

```text
https://www.iamlearning.thm/contact
```

**Scheme:**

```text
https
```

**Host:**

```text
www.iamlearning.thm
```

**Path:**

```text
/contact
```

Remember:

```text
SCHEME://HOST/PATH
```

## GET

GET is used to retrieve a resource.

```http
GET /contact HTTP/1.1
Host: www.iamlearning.thm
```

## Response

The server sends back:

```text
Status Code
Headers
Body
```

Example:

```text
200 OK
```

means the request was successful.

---

# My Takeaway

HTTP is not just something I need to memorize for a networking class. It is one of the foundations of web security.

I should be comfortable looking at a URL or HTTP request and immediately identifying:

```text
Scheme
Host
Port
Path
Method
Headers
Cookies
Status Code
Response
```

These are fundamentals I want to become very comfortable with before moving deeper into web security and detection engineering.
