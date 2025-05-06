<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Simple Website</title>
    <style>
        /* CSS for styling */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            line-height: 1.6;
        }
        header {
            background-color: #333;
            color: white;
            text-align: center;
            padding: 1rem;
            border: 1px solid black;
        }
        nav {
            background-color: #f4f4f4;
            padding: 1rem;
        }
        nav a {
            margin: 0 1rem;
            text-decoration: none;
            color: #333;
        }
        nav a:hover {
            color: #007BFF;
        }
        .container {
            max-width: 800px;
            margin: 2rem auto;
            padding: 0 1rem;
        }
        footer {
            background-color: #333;
            color: white;
            text-align: center;
            padding: 1rem;
            position: fixed;
            bottom: 0;
            width: 100%;
            border: 1px solid black;
        }
        /* Form styling */
        form {
            margin-top: 1rem;
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
            max-width: 400px;
        }
        input[type="text"], input[type="email"] {
            padding: 0.5rem;
            font-size: 1rem;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            padding: 0.5rem;
            font-size: 1rem;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        .form-message {
            margin-top: 0.5rem;
            color: green;
            display: none;
        }
        @media (max-width: 600px) {
            nav a {
                display: block;
                margin: 0.5rem 0;
            }
        }
    </style>
</head>
<body>
    <header>
        <h1>Welcome to My Website</h1>
    </header>
    <nav>
        <a href="#home">Home</a>
        <a href="#about">About</a>
        <a href="#forms">Forms</a>
        <a href="#contact">Contact</a>
    </nav>
    <div class="container">
        <h2>About Us</h2>
        <p>This is a simple website built with HTML and CSS. You can customize this template by adding your own content, styles, and pages.</p>
        <h2 id="forms">Forms</h2>
        <p>Fill out the form below to send us a message.</p>
        <form id="contact-form" action="https://formspree.io/f/your-form-id" method="POST">
            <input type="text" name="name" placeholder="Your Name" required>
            <input type="email" name="email" placeholder="Your Email" required>
            <input type="text" name="message" placeholder="Your Message" required>
            <button type="submit">Submit</button>
        </form>
        <p class="form-message" id="form-message">Thank you! Your message has been sent.</p>
    </div>
    <footer>
        <p>© 2025 My Website. All rights reserved.</p>
    </footer>
    <script>
        // Formspree AJAX submission to prevent page redirect
        const form = document.getElementById('contact-form');
        const formMessage = document.getElementById('form-message');
        form.addEventListener('submit', async (e) => {
            e.preventDefault();
            const formData = new FormData(form);
            try {
                const response = await fetch(form.action, {
                    method: 'POST',
                    body: formData,
                    headers: {
                        'Accept': 'application/json'
                    }
                });
                if (response.ok) {
                    formMessage.style.display = 'block';
                    form.reset();
                    setTimeout(() => { formMessage.style.display = 'none'; }, 5000);
                } else {
                    alert('Error sending message. Please try again.');
                }
            } catch (error) {
                alert('Network error. Please check your connection.');
            }
        });
    </script>
</body>
</html>
