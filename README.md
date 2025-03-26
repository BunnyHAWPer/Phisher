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
  <a href="#-contributing">Contributing</a>
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

### 📚 Complete Web Framework Features
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

## 📋 Request & Response

Expressify provides intuitive request and response objects similar to Express.js:

### Request Object
- `req.params` - Route parameters
- `req.query` - Query string parameters
- `req.body` - Request body (JSON, form data)
- `req.headers` - Request headers
- `req.cookies` - Request cookies
- `req.path` - Request path
- `req.method` - Request method
- `req.ip` - Client IP address
- `req.hostname` - Host name
- `req.protocol` - HTTP protocol
- `req.secure` - HTTPS check

### Response Object
- `res.send()` - Send response
- `res.json()` - Send JSON response
- `res.status()` - Set status code
- `res.redirect()` - Redirect to URL
- `res.render()` - Render template
- `res.cookie()` - Set cookie
- `res.clear_cookie()` - Clear cookie
- `res.type()` - Set content type
- `res.format()` - Content negotiation
- `res.append()` - Append header
- `res.end()` - End response

## 🔍 Examples

Expressify comes with a rich set of examples to get you started:

### Basic Examples
- **[Hello World](/examples/01-basic/hello_world.py)** - Simple "Hello World" example
- **[Routing](/examples/02-routing/routes.py)** - Demonstrates routing capabilities
- **[Request Data](/examples/03-requests/request_data.py)** - Shows handling of request data

### Advanced Examples
- **[Middleware](/examples/03-middleware/)** - Middleware usage examples
- **[Templates](/examples/04-templates/)** - Template rendering examples
- **[Static Files](/examples/05-static-files/)** - Serving static files
- **[Error Handling](/examples/06-error-handling/)** - Error handling approaches
- **[RESTful API](/examples/07-restful-api/)** - Complete RESTful API example
- **[Express Features](/examples/09-express-features/)** - Express.js-like features

## 📚 Documentation

For detailed documentation on all features:

- **[Request Object](/docs/request.md)** - All request properties and methods
- **[Response Object](/docs/response.md)** - All response properties and methods
- **[Routing](/docs/routing.md)** - Detailed routing documentation
- **[Middleware](/docs/middleware.md)** - Middleware documentation
- **[Templates](/docs/templates.md)** - Template rendering guide
- **[Deployment](/docs/deployment.md)** - Deployment guide

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

See [CONTRIBUTING.md](CONTRIBUTING.md) for more details.

## 📄 License

Distributed under the MIT License. See [LICENSE](LICENSE) for more information.

## 👤 Author

**Dhruv Rawat**

- GitHub: [@bunnyhawper](https://github.com/bunnyhawper)
- Email: [dhruvrwt1211@gmail.com](mailto:dhruvrwt1211@gmail.com)
- LinkedIn: [Dhruv Rawat](https://linkedin.com/in/dhruv-rawat)

## 💖 Support

If you find Expressify helpful, consider:
- ⭐ Starring the project on GitHub
- 🐛 Reporting issues
- 🔄 Submitting pull requests
- 📢 Spreading the word

---

<div align="center">
  <sub>Built with ❤️ by Dhruv Rawat</sub>
  <br>
  <sub>Inspired by Express.js, crafted for Python</sub>
</div> 
