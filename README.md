<div align="center">
  <img src="https://i.imgur.com/SYY9Z7H.png" alt="Expressify Logo" width="300">
  <h1>Expressify</h1>
  <p>
    <strong>A lightning-fast Python web framework inspired by Express.js</strong>
  </p>
  <p>
    <a href="https://github.com/bunnyhawper/expressify/blob/main/LICENSE">
      <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License">
    </a>
    <a href="https://www.python.org/downloads/">
      <img src="https://img.shields.io/badge/Python-3.7%2B-blue" alt="Python">
    </a>
    <a href="https://pypi.org/project/expressify/">
      <img src="https://img.shields.io/badge/PyPI-1.0.0-blue" alt="PyPI Version">
    </a>
    <img src="https://img.shields.io/badge/Maintained%3F-yes-green.svg" alt="Maintained">
    <img src="https://img.shields.io/badge/Made%20with-Python-1f425f.svg" alt="Made with Python">
  </p>
</div>

<p align="center">
  <b>Expressify</b> brings the elegance of Express.js to Python, offering a familiar API with Pythonic features.
  <br>Build web applications and APIs with minimal code and maximum productivity.
</p>

---

<div align="center">
  <a href="#-why-expressify">Why Expressify</a> •
  <a href="#-features">Features</a> •
  <a href="#-installation">Installation</a> •
  <a href="#-quick-start">Quick Start</a> •
  <a href="#-examples">Examples</a> •
  <a href="#-documentation">Documentation</a> •
  <a href="#-contributing">Contributing</a> •
  <a href="#-author">Author</a>
</div>

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

Check out the [examples directory](./examples) for complete code examples.

## 📖 Development Tools

### Hot Reloading

Expressify includes a development server with hot reloading. Run your app with:

```bash
python dev.py app.py
```

This will automatically restart the server when your code changes, making development faster and more efficient.

## 📚 Documentation

For detailed documentation on all features, check out the [documentation site](./docs/index.html) or browse the documentation files:

- **[Request Object](./docs/request.md)** - All request properties and methods
- **[Response Object](./docs/response.md)** - All response properties and methods
- **[Routing](./docs/routing.md)** - Detailed routing documentation
- **[Middleware](./docs/middleware.md)** - Middleware documentation
- **[Templates](./docs/templates.md)** - Template rendering guide
- **[Deployment](./docs/deployment.md)** - Deployment guide

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Dhruv Rawat**

- GitHub: [bunnyhawper](https://github.com/bunnyhawper)
- LinkedIn: [Dhruv Rawat](https://www.linkedin.com/in/dhruv-rawat)
- Email: [dhruvrwt1211@gmail.com](mailto:dhruvrwt1211@gmail.com)

---

<p align="center">Made with ❤️ in Python</p> 
