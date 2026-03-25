index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Digital Marketing Agency</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="font-sans text-gray-800">

<!-- Navbar -->
<header class="fixed w-full bg-white shadow z-50">
  <div class="max-w-7xl mx-auto flex justify-between items-center p-4">
    <h1 class="text-2xl font-bold">DM Agency</h1>
    <nav class="space-x-6 hidden md:block">
      <a href="#" class="hover:text-blue-600">Home</a>
      <a href="#services" class="hover:text-blue-600">Services</a>
      <a href="#about" class="hover:text-blue-600">About</a>
      <a href="#contact" class="hover:text-blue-600">Contact</a>
    </nav>
  </div>
</header>

<!-- Hero -->
<section class="h-screen flex items-center justify-center bg-gradient-to-r from-blue-500 to-indigo-600 text-white text-center">
  <div>
    <h2 class="text-5xl font-bold mb-4">Grow Your Business Online</h2>
    <p class="mb-6">We help brands scale with powerful digital marketing strategies.</p>
    <a href="#contact" class="bg-white text-blue-600 px-6 py-3 rounded-full font-semibold">Get Started</a>
  </div>
</section>

<!-- Services -->
<section id="services" class="py-16 max-w-7xl mx-auto px-4">
  <h2 class="text-3xl font-bold text-center mb-10">Our Services</h2>
  <div class="grid md:grid-cols-3 gap-6">
    <div class="p-6 shadow rounded-xl">
      <h3 class="font-bold text-xl mb-2">SEO</h3>
      <p>Improve your website ranking on search engines.</p>
    </div>
    <div class="p-6 shadow rounded-xl">
      <h3 class="font-bold text-xl mb-2">Social Media</h3>
      <p>Grow your brand on social platforms.</p>
    </div>
    <div class="p-6 shadow rounded-xl">
      <h3 class="font-bold text-xl mb-2">PPC Ads</h3>
      <p>Run high-converting ad campaigns.</p>
    </div>
  </div>
</section>

<!-- About -->
<section id="about" class="bg-gray-100 py-16 px-4">
  <div class="max-w-4xl mx-auto text-center">
    <h2 class="text-3xl font-bold mb-4">About Us</h2>
    <p>We are a team of marketing experts helping businesses grow digitally with innovative strategies.</p>
  </div>
</section>

<!-- Contact -->
<section id="contact" class="py-16 px-4">
  <div class="max-w-xl mx-auto">
    <h2 class="text-3xl font-bold text-center mb-6">Contact Us</h2>
    <form class="space-y-4">
      <input type="text" placeholder="Name" class="w-full p-3 border rounded" required>
      <input type="email" placeholder="Email" class="w-full p-3 border rounded" required>
      <textarea placeholder="Message" class="w-full p-3 border rounded" required></textarea>
      <button class="w-full bg-blue-600 text-white py-3 rounded">Send Message</button>
    </form>
  </div>
</section>

<!-- Footer -->
<footer class="bg-black text-white text-center p-4">
  <p>© 2026 Digital Marketing Agency. All rights reserved.</p>
</footer>

</body>
</html>
