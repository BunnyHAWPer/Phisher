# Expressify

**A lightning-fast Python web framework inspired by Express.js**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://github.com/bunnyhawper/expressify/blob/main/LICENSE)
[![Python: 3.7+](https://img.shields.io/badge/Python-3.7%2B-blue)](https://www.python.org/downloads/)
[![PyPI Version](https://img.shields.io/badge/PyPI-1.0.0-blue)](https://pypi.org/project/expressify/)
[![Maintained](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/bunnyhawper/expressify)
[![Made with Python](https://img.shields.io/badge/Made%20with-Python-1f425f.svg)](https://www.python.org/)

**Expressify** brings the elegance of Express.js to Python, offering a familiar API with Pythonic features.
Build web applications and APIs with minimal code and maximum productivity.

> **Note:** Expressify is still in active development. This is an open-source project, and contributions are highly encouraged! Feel free to submit pull requests, report issues, or suggest new features.

---

## Quick Links
- [Why Expressify?](#-why-expressify)
- [Features](#-features)
- [Installation](#-installation)
- [Quick Start](#-quick-start)
- [Examples](#-examples)
- [Contributing](#-contributing)
- [Author](#-author)

---

## ✨ Why Expressify?

### 🔄 Familiar Express.js API
If you love Express.js but prefer Python, Expressify offers the best of both worlds. The framework provides a nearly identical API to Express.js while embracing Python's elegance.

### 💪 Modern Python Features
Built for modern Python, Expressify leverages async/await for high performance and implements type hints for better IDE support and code completion.

### 🚀 High Performance
Powered by ASGI and Uvicorn, Expressify delivers exceptional performance for web applications and APIs, rivaling other high-performance Python frameworks.

### ⚡ Minimal Boilerplate
Write less code to achieve more. Expressify's concise API lets you define routes, middleware, and handlers with minimal overhead:

```python
@app.get('/hello/:name')
def hello(req, res):
    res.send(f"Hello, {req.params['name']}!")
```

### 🧩 Robust Middleware Ecosystem
The middleware system mirrors Express.js, allowing easy implementation of authentication, logging, CORS, and more with a simple `app.use()` call.

### 🔍 Built for Developer Experience
With excellent error messages, hot reloading, and comprehensive documentation, Expressify prioritizes developer productivity.

### 📚 Complete Web Framework
Everything you need is built-in: routing, middleware, templating, static file serving, and more. No need to piece together multiple libraries.

## 🚀 Features

- ⚡ **Simple and intuitive API** similar to Express.js
- 🧩 **Middleware support** with next() functionality
- 🔗 **Route parameters** and query string parsing
- 📄 **JSON and form data handling** out of the box
- 📁 **Static file serving** for your web assets
- 🔄 **CORS middleware** for cross-origin requests
- 🖥️ **Template rendering** with Jinja2
- ⚙️ **Content negotiation** for API responses
- 🍪 **Cookie handling** with signed cookies
- 🔐 **Session management** with multiple backends
- ⏱️ **Async/await support** for modern Python
- 🛡️ **Error handling** with custom error pages
- 🚀 **Built on ASGI** with Uvicorn for high performance
- 🧪 **Production-ready** with minimal overhead
- 🔥 **Hot reloading** for rapid development

## 📦 Installation

Install Expressify with pip:

```bash
pip install expressify
```

This installs the latest version of Expressify with all dependencies.

## 🏁 Quick Start

Create your first Expressify application in just a few lines of code:

```python
from expressify import expressify

# Create a new Expressify application
app = expressify()

# Define a route using decorator style
@app.get('/')
def home(req, res):
    res.send('Hello, World!')

# JSON response example (function style)
def get_data(req, res):
    res.json({
        'message': 'This is JSON data',
        'success': True,
        'data': [1, 2, 3, 4, 5]
    })
app.get('/api/data', get_data)

# Route parameters example
@app.get('/users/:id')
def get_user(req, res):
    user_id = req.params['id']
    res.send(f'User ID: {user_id}')

# Start the server
if __name__ == '__main__':
    app.listen(3000)
    print('Server running at http://localhost:3000')
```

## 🧩 Middleware Architecture

Expressify's middleware system is its most powerful feature, allowing you to process requests and responses in a modular way:

```python
from expressify import expressify, Middleware

app = expressify()

# Add built-in middleware
app.use(Middleware.logger(':method :url :status :response-time ms'))
app.use(Middleware.cors(origins=['http://localhost:3000']))
app.use(Middleware.body_parser())
app.use(Middleware.static('public'))

# Custom middleware
async def auth_middleware(req, res, next):
    if not req.headers.get('Authorization'):
        return res.status(401).json({'error': 'Unauthorized'})
    await next()

app.use(auth_middleware)
```

## 🛣️ Router Support

Organize your routes modularly using Router objects:

```python
from expressify import expressify, Router

app = expressify()

# Create a router
api = Router()

# Define routes on the router
@api.get('/users')
def get_users(req, res):
    res.json(['user1', 'user2', 'user3'])

@api.post('/users')
def create_user(req, res):
    res.status(201).json({'message': 'User created'})

# Mount the router with a prefix
app.use('/api', api)
```

## 🔍 Examples

Expressify comes with comprehensive examples to help you get started:

- **Basic examples** - Hello world, routing, request/response handling
- **Middleware examples** - Custom middleware, error handling, CORS
- **Template rendering** - Jinja2 templates, layouts, partials
- **Static files** - Serving CSS, JS, images, and other static assets
- **Error handling** - Custom error pages, error middleware
- **RESTful API** - Complete API implementation with CRUD operations
- **Express.js features** - Content negotiation, cookies, sessions

Check out the examples directory for complete code examples.

## 📖 Development Tools

### Hot Reloading

Expressify includes a development server with hot reloading. Run your app with:

```bash
python dev.py app.py
```

This will automatically restart the server when your code changes, making development faster and more efficient.

## 🤝 Contributing

Expressify is an open-source project in active development and welcomes contributions from the community! Here's how you can help:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

Feel free to contribute by:
- Adding new features
- Fixing bugs
- Improving documentation
- Writing tests
- Suggesting enhancements

No contribution is too small, and all are appreciated!

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Dhruv Rawat**

- GitHub: [bunnyhawper](https://github.com/bunnyhawper)
- LinkedIn: [Dhruv Rawat](https://www.linkedin.com/in/dhruv-rawat)
- Email: [dhruvrwt1211@gmail.com](mailto:dhruvrwt1211@gmail.com)

---

<p align="center">Made with ❤️ in Python</p> 
