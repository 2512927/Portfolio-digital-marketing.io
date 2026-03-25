Portfolio digital marketing index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Digital Marketing Agency</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
  <script src="https://kit.fontawesome.com/yourkitid.js" crossorigin="anonymous"></script>
  <style>
    * {margin:0; padding:0; box-sizing:border-box; font-family:'Poppins', sans-serif;}
    body {background: linear-gradient(135deg,#667eea,#764ba2); color:#333;}

    header {
      background: rgba(255,255,255,0.1);
      backdrop-filter: blur(10px);
      padding: 15px 30px;
      display:flex;
      justify-content:space-between;
      align-items:center;
      position:sticky;
      top:0;
      z-index:1000;
    }

    header h1 {color:white;}

    nav {
      display:flex;
      align-items:center;
    }

    nav a {
      color:white;
      margin:0 15px;
      text-decoration:none;
      font-weight:500;
    }

    .menu-toggle {
      display:none;
      font-size:24px;
      color:white;
      cursor:pointer;
    }

    .mobile-menu {
      display:none;
      flex-direction:column;
      position:absolute;
      top:70px;
      right:20px;
      background:white;
      border-radius:10px;
      padding:15px;
    }

    .mobile-menu a {
      color:#333;
      margin:10px 0;
    }

    .hero {
      height:90vh;
      display:flex;
      justify-content:center;
      align-items:center;
      flex-direction:column;
      text-align:center;
      color:white;
    }

    .hero h2 {font-size:3rem; margin-bottom:10px;}
    .hero p {font-size:1.2rem; margin-bottom:20px;}

    .btn {
      background:#ff7a18;
      color:white;
      padding:12px 25px;
      border:none;
      border-radius:25px;
      cursor:pointer;
      transition:0.3s;
    }

    .btn:hover {background:#ff3d00;}

    section {
      padding:60px 20px;
      background:white;
      margin:20px;
      border-radius:20px;
    }

    .services {
      display:grid;
      grid-template-columns: repeat(auto-fit,minmax(200px,1fr));
      gap:20px;
    }

    .card {
      padding:20px;
      border-radius:15px;
      background:linear-gradient(135deg,#89f7fe,#66a6ff);
      color:white;
      transition:0.3s;
    }

    .card:hover {transform:translateY(-10px);}

    .social-icons {
      margin-top:15px;
    }

    .social-icons i {
      margin:0 10px;
      font-size:20px;
      color:white;
      cursor:pointer;
    }

    .contact input, .contact textarea {
      width:100%;
      padding:10px;
      margin:10px 0;
      border-radius:10px;
      border:1px solid #ccc;
    }

    footer {
      text-align:center;
      padding:20px;
      color:white;
    }

    @media(max-width:768px) {
      nav a {display:none;}
      .menu-toggle {display:block;}
    }
  </style>
</head>
<body>

<header>
  <h1>My Agency</h1>
  <nav>
    <a href="#">Home</a>
    <a href="#services">Services</a>
    <a href="#contact">Contact</a>
  </nav>
  <div class="menu-toggle" onclick="toggleMenu()">☰</div>
  <div class="mobile-menu" id="mobileMenu">
    <a href="#">Home</a>
    <a href="#services">Services</a>
    <a href="#contact">Contact</a>
  </div>
</header>

<div class="hero">
  <h2>Grow Your Business Online</h2>
  <p>We help you scale with powerful digital marketing strategies</p>
  <button class="btn">Get Started</button>
  <div class="social-icons">
    <i class="fab fa-facebook"></i>
    <i class="fab fa-instagram"></i>
    <i class="fab fa-twitter"></i>
    <i class="fab fa-linkedin"></i>
  </div>
</div>

<section id="services">
  <h2>Our Services</h2>
  <div class="services">
    <div class="card">SEO Optimization</div>
    <div class="card">Social Media Marketing</div>
    <div class="card">Google Ads (PPC)</div>
    <div class="card">Content Marketing</div>
  </div>
</section>

<section>
  <h2>About Us</h2>
  <p>We are a results-driven digital marketing agency focused on helping businesses grow online with innovative strategies.</p>
</section>

<section id="contact" class="contact">
  <h2>Contact Us</h2>
  <input type="text" placeholder="Your Name">
  <input type="email" placeholder="Your Email">
  <textarea placeholder="Your Message"></textarea>
  <button class="btn">Send Message</button>
</section>

<footer>
  <p>© 2026 Digital Agency | All Rights Reserved</p>
</footer>

<script>
function toggleMenu() {
  const menu = document.getElementById('mobileMenu');
  menu.style.display = menu.style.display === 'flex' ? 'none' : 'flex';
}
</script>

</body>
</html>
