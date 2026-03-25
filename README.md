# Portfolio-digital-marketing.io

                 
import React, { useState, useEffect } from 'react';
import { 
  BarChart3, 
  Megaphone, 
  Search, 
  PenTool, 
  Mail, 
  CheckCircle2, 
  ArrowRight, 
  Star, 
  Menu, 
  X, 
  TrendingUp,
  Target,
  Users,
  Facebook,
  Twitter,
  Instagram,
  Linkedin,
  Send
} from 'lucide-react';

export default function App() {
  const [isScrolled, setIsScrolled] = useState(false);
  const [mobileMenuOpen, setMobileMenuOpen] = useState(false);
  const [formStatus, setFormStatus] = useState('idle'); // idle, submitting, success

  // Handle smooth scrolling and sticky header
  useEffect(() => {
    const handleScroll = () => {
      setIsScrolled(window.scrollY > 50);
    };
    window.addEventListener('scroll', handleScroll);
    
    // Add smooth scroll behavior to html
    document.documentElement.style.scrollBehavior = 'smooth';
    
    return () => {
      window.removeEventListener('scroll', handleScroll);
      document.documentElement.style.scrollBehavior = 'auto';
    };
  }, []);

  const handleNavClick = (e, targetId) => {
    e.preventDefault();
    setMobileMenuOpen(false);
    const target = document.getElementById(targetId);
    if (target) {
      target.scrollIntoView({ behavior: 'smooth', block: 'start' });
    }
  };

  const handleFormSubmit = (e) => {
    e.preventDefault();
    setFormStatus('submitting');
    // Simulate API call
    setTimeout(() => {
      setFormStatus('success');
      setTimeout(() => setFormStatus('idle'), 3000);
      e.target.reset();
    }, 1500);
  };

  const navigation = [
    { name: 'About', href: 'about' },
    { name: 'Services', href: 'services' },
    { name: 'Work', href: 'portfolio' },
    { name: 'Pricing', href: 'pricing' },
    { name: 'Blog', href: 'blog' },
  ];

  return (
    <div className="min-h-screen bg-slate-50 text-slate-900 font-sans selection:bg-blue-200">
      
      {/* --- NAVIGATION --- */}
      <header 
        className={`fixed top-0 w-full z-50 transition-all duration-300 ${
          isScrolled ? 'bg-white/90 backdrop-blur-md shadow-sm py-4' : 'bg-transparent py-6'
        }`}
      >
        <div className="container mx-auto px-6 md:px-12 flex items-center justify-between">
          <div className="flex items-center gap-2 cursor-pointer" onClick={(e) => handleNavClick(e, 'hero')}>
            <TrendingUp className="w-8 h-8 text-blue-600" />
            <span className="text-2xl font-bold tracking-tighter">Elevate<span className="text-blue-600">.</span></span>
          </div>

          {/* Desktop Nav */}
          <nav className="hidden md:flex items-center gap-8">
            {navigation.map((item) => (
              <a 
                key={item.name} 
                href={`#${item.href}`}
                onClick={(e) => handleNavClick(e, item.href)}
                className="text-sm font-medium text-slate-600 hover:text-blue-600 transition-colors"
              >
                {item.name}
              </a>
            ))}
            <a 
              href="#contact"
              onClick={(e) => handleNavClick(e, 'contact')}
              className="bg-slate-900 hover:bg-blue-600 text-white px-6 py-2.5 rounded-full text-sm font-medium transition-all shadow-lg shadow-slate-900/20 hover:shadow-blue-600/30"
            >
              Get Started
            </a>
          </nav>

          {/* Mobile Menu Toggle */}
          <button 
            className="md:hidden text-slate-900"
            onClick={() => setMobileMenuOpen(!mobileMenuOpen)}
          >
            {mobileMenuOpen ? <X className="w-6 h-6" /> : <Menu className="w-6 h-6" />}
          </button>
        </div>

        {/* Mobile Nav Dropdown */}
        {mobileMenuOpen && (
          <div className="md:hidden absolute top-full left-0 w-full bg-white shadow-xl border-t border-slate-100 py-4 px-6 flex flex-col gap-4">
            {navigation.map((item) => (
              <a 
                key={item.name} 
                href={`#${item.href}`}
                onClick={(e) => handleNavClick(e, item.href)}
                className="text-base font-medium text-slate-700 block py-2"
              >
                {item.name}
              </a>
            ))}
            <a 
              href="#contact"
              onClick={(e) => handleNavClick(e, 'contact')}
              className="bg-blue-600 text-white text-center px-6 py-3 rounded-lg text-sm font-medium mt-2"
            >
              Get Started
            </a>
          </div>
        )}
      </header>

      {/* --- HERO SECTION --- */}
      <section id="hero" className="relative pt-32 pb-20 md:pt-48 md:pb-32 overflow-hidden">
        {/* Background Decorative Elements */}
        <div className="absolute top-0 left-0 w-full h-full overflow-hidden -z-10">
          <div className="absolute top-[-10%] left-[-10%] w-96 h-96 bg-blue-200/50 rounded-full blur-3xl opacity-60"></div>
          <div className="absolute bottom-[-10%] right-[-10%] w-[500px] h-[500px] bg-indigo-200/50 rounded-full blur-3xl opacity-60"></div>
        </div>

        <div className="container mx-auto px-6 md:px-12 text-center">
          <div className="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-blue-50 text-blue-700 text-sm font-semibold mb-8 border border-blue-100">
            <span className="relative flex h-2 w-2">
              <span className="animate-ping absolute inline-flex h-full w-full rounded-full bg-blue-400 opacity-75"></span>
              <span className="relative inline-flex rounded-full h-2 w-2 bg-blue-600"></span>
            </span>
            Top Digital Agency 2026
          </div>
          <h1 className="text-5xl md:text-7xl font-extrabold tracking-tight text-slate-900 mb-6 max-w-4xl mx-auto leading-tight">
            Scale Your Brand With <br className="hidden md:block"/>
            <span className="text-transparent bg-clip-text bg-gradient-to-r from-blue-600 to-indigo-600">
              Data-Driven Marketing
            </span>
          </h1>
          <p className="text-lg md:text-xl text-slate-600 mb-10 max-w-2xl mx-auto leading-relaxed">
            We turn clicks into clients. Partner with our award-winning agency to dominate your market, increase ROI, and build lasting customer relationships.
          </p>
          <div className="flex flex-col sm:flex-row items-center justify-center gap-4">
            <a 
              href="#contact"
              onClick={(e) => handleNavClick(e, 'contact')}
              className="w-full sm:w-auto px-8 py-4 bg-blue-600 hover:bg-blue-700 text-white rounded-full font-semibold transition-all shadow-lg shadow-blue-600/30 flex items-center justify-center gap-2 group"
            >
              Grow Your Business Online
              <ArrowRight className="w-4 h-4 group-hover:translate-x-1 transition-transform" />
            </a>
            <a 
              href="#portfolio"
              onClick={(e) => handleNavClick(e, 'portfolio')}
              className="w-full sm:w-auto px-8 py-4 bg-white hover:bg-slate-50 text-slate-900 border border-slate-200 rounded-full font-semibold transition-all shadow-sm flex items-center justify-center gap-2"
            >
              View Our Work
            </a>
          </div>
          
          {/* Trust Indicators */}
          <div className="mt-20 pt-10 border-t border-slate-200/60 max-w-4xl mx-auto">
            <p className="text-sm font-medium text-slate-400 mb-6 uppercase tracking-wider">Trusted by innovative companies</p>
            <div className="flex flex-wrap justify-center items-center gap-8 md:gap-16 opacity-60 grayscale">
              {/* Mock Company Logos */}
              <h3 className="text-2xl font-bold font-serif">Acme Corp</h3>
              <h3 className="text-xl font-bold tracking-widest">GLOBAL</h3>
              <h3 className="text-2xl font-bold italic">TechFlow</h3>
              <h3 className="text-2xl font-black">NEXUS</h3>
            </div>
          </div>
        </div>
      </section>

      {/* --- ABOUT US SECTION --- */}
      <section id="about" className="py-20 bg-white">
        <div className="container mx-auto px-6 md:px-12">
          <div className="grid lg:grid-cols-2 gap-16 items-center">
            <div className="relative">
              <div className="aspect-square rounded-3xl overflow-hidden relative">
                <img 
                  src="https://images.unsplash.com/photo-1552664730-d307ca884978?auto=format&fit=crop&q=80&w=1000" 
                  alt="Team strategy meeting" 
                  className="object-cover w-full h-full"
                  onError={(e) => {
                    e.target.onerror = null; 
                    e.target.src = "data:image/svg+xml;charset=UTF-8,%3Csvg%20width%3D%22800%22%20height%3D%22800%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%3Crect%20width%3D%22100%25%22%20height%3D%22100%25%22%20fill%3D%22%23e2e8f0%22%2F%3E%3Ctext%20x%3D%2250%25%22%20y%3D%2250%25%22%20font-family%3D%22sans-serif%22%20font-size%3D%2224%22%20fill%3D%22%2364748b%22%20dominant-baseline%3D%22middle%22%20text-anchor%3D%22middle%22%3EImage%20Placeholder%3C%2Ftext%3E%3C%2Fsvg%3E";
                  }}
                />
              </div>
              {/* Floating Stat Card */}
              <div className="absolute -bottom-8 -right-8 bg-white p-6 rounded-2xl shadow-xl border border-slate-100 hidden md:block">
                <div className="flex items-center gap-4">
                  <div className="w-12 h-12 bg-blue-100 rounded-full flex items-center justify-center text-blue-600">
                    <Target className="w-6 h-6" />
                  </div>
                  <div>
                    <h4 className="text-3xl font-bold text-slate-900">98%</h4>
                    <p className="text-sm font-medium text-slate-500">Client Retention</p>
                  </div>
                </div>
              </div>
            </div>
            
            <div>
              <h2 className="text-blue-600 font-semibold tracking-wide uppercase text-sm mb-3">About Elevate</h2>
              <h3 className="text-4xl md:text-5xl font-bold text-slate-900 mb-6 leading-tight">
                We blend creativity with pure data.
              </h3>
              <p className="text-lg text-slate-600 mb-8 leading-relaxed">
                Founded in 2018, Elevate started with a simple mission: to help businesses navigate the complexities of the digital landscape. We don't believe in one-size-fits-all strategies. Instead, we craft bespoke campaigns driven by analytics, audience behavior, and bold creativity.
              </p>
              
              <div className="space-y-6">
                <div className="flex gap-4">
                  <div className="mt-1 w-10 h-10 rounded-full bg-indigo-50 flex items-center justify-center flex-shrink-0 text-indigo-600">
                    <CheckCircle2 className="w-5 h-5" />
                  </div>
                  <div>
                    <h4 className="text-xl font-bold text-slate-900 mb-2">Our Mission</h4>
                    <p className="text-slate-600">To empower brands to reach their full potential through innovative, transparent, and results-driven digital marketing.</p>
                  </div>
                </div>
                <div className="flex gap-4">
                  <div className="mt-1 w-10 h-10 rounded-full bg-blue-50 flex items-center justify-center flex-shrink-0 text-blue-600">
                    <Users className="w-5 h-5" />
                  </div>
                  <div>
                    <h4 className="text-xl font-bold text-slate-900 mb-2">Our Vision</h4>
                    <p className="text-slate-600">To be the global benchmark for digital excellence, fostering growth for our clients and our team.</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* --- SERVICES SECTION --- */}
      <section id="services" className="py-24 bg-slate-50">
        <div className="container mx-auto px-6 md:px-12">
          <div className="text-center max-w-3xl mx-auto mb-16">
            <h2 className="text-blue-600 font-semibold tracking-wide uppercase text-sm mb-3">Our Expertise</h2>
            <h3 className="text-3xl md:text-5xl font-bold text-slate-900 mb-6">Comprehensive Marketing Solutions</h3>
            <p className="text-lg text-slate-600">We provide end-to-end digital marketing services designed to increase your visibility, traffic, and revenue.</p>
          </div>

          <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
            {/* Service 1 */}
            <div className="bg-white p-8 rounded-2xl shadow-sm border border-slate-100 hover:shadow-xl hover:-translate-y-1 transition-all duration-300 group">
              <div className="w-14 h-14 bg-blue-50 text-blue-600 rounded-xl flex items-center justify-center mb-6 group-hover:bg-blue-600 group-hover:text-white transition-colors">
                <Search className="w-7 h-7" />
              </div>
              <h4 className="text-xl font-bold text-slate-900 mb-3">SEO Optimization</h4>
              <p className="text-slate-600 mb-4 leading-relaxed">
                Dominate search engine rankings. Our data-backed SEO strategies ensure your brand is found by customers actively searching for your services.
              </p>
              <a href="#contact" className="inline-flex items-center text-blue-600 font-medium hover:text-blue-800">
                Learn more <ArrowRight className="w-4 h-4 ml-1" />
              </a>
            </div>

            {/* Service 2 */}
            <div className="bg-white p-8 rounded-2xl shadow-sm border border-slate-100 hover:shadow-xl hover:-translate-y-1 transition-all duration-300 group">
              <div className="w-14 h-14 bg-indigo-50 text-indigo-600 rounded-xl flex items-center justify-center mb-6 group-hover:bg-indigo-600 group-hover:text-white transition-colors">
                <Megaphone className="w-7 h-7" />
              </div>
              <h4 className="text-xl font-bold text-slate-900 mb-3">Social Media Marketing</h4>
              <p className="text-slate-600 mb-4 leading-relaxed">
                Build a loyal community. We create engaging content and manage your social presence to foster brand awareness and direct engagement.
              </p>
              <a href="#contact" className="inline-flex items-center text-indigo-600 font-medium hover:text-indigo-800">
                Learn more <ArrowRight className="w-4 h-4 ml-1" />
              </a>
            </div>

            {/* Service 3 */}
            <div className="bg-white p-8 rounded-2xl shadow-sm border border-slate-100 hover:shadow-xl hover:-translate-y-1 transition-all duration-300 group">
              <div className="w-14 h-14 bg-emerald-50 text-emerald-600 rounded-xl flex items-center justify-center mb-6 group-hover:bg-emerald-600 group-hover:text-white transition-colors">
                <BarChart3 className="w-7 h-7" />
              </div>
              <h4 className="text-xl font-bold text-slate-900 mb-3">Pay-Per-Click (PPC)</h4>
              <p className="text-slate-600 mb-4 leading-relaxed">
                Instant visibility, measurable ROI. We manage targeted ad campaigns across Google Ads and social platforms to drive high-intent traffic.
              </p>
              <a href="#contact" className="inline-flex items-center text-emerald-600 font-medium hover:text-emerald-800">
                Learn more <ArrowRight className="w-4 h-4 ml-1" />
              </a>
            </div>

            {/* Service 4 */}
            <div className="bg-white p-8 rounded-2xl shadow-sm border border-slate-100 hover:shadow-xl hover:-translate-y-1 transition-all duration-300 group">
              <div className="w-14 h-14 bg-purple-50 text-purple-600 rounded-xl flex items-center justify-center mb-6 group-hover:bg-purple-600 group-hover:text-white transition-colors">
                <PenTool className="w-7 h-7" />
              </div>
              <h4 className="text-xl font-bold text-slate-900 mb-3">Content Marketing</h4>
              <p className="text-slate-600 mb-4 leading-relaxed">
                Storytelling that converts. From blog posts to whitepapers, we create valuable content that establishes authority and nurtures leads.
              </p>
              <a href="#contact" className="inline-flex items-center text-purple-600 font-medium hover:text-purple-800">
                Learn more <ArrowRight className="w-4 h-4 ml-1" />
              </a>
            </div>

            {/* Service 5 */}
            <div className="bg-white p-8 rounded-2xl shadow-sm border border-slate-100 hover:shadow-xl hover:-translate-y-1 transition-all duration-300 group">
              <div className="w-14 h-14 bg-orange-50 text-orange-600 rounded-xl flex items-center justify-center mb-6 group-hover:bg-orange-600 group-hover:text-white transition-colors">
                <Mail className="w-7 h-7" />
              </div>
              <h4 className="text-xl font-bold text-slate-900 mb-3">Email Marketing</h4>
              <p className="text-slate-600 mb-4 leading-relaxed">
                Automated growth sequences. We design and execute personalized email campaigns that turn subscribers into lifelong customers.
              </p>
              <a href="#contact" className="inline-flex items-center text-orange-600 font-medium hover:text-orange-800">
                Learn more <ArrowRight className="w-4 h-4 ml-1" />
              </a>
            </div>

            {/* CTA Service Card */}
            <div className="bg-slate-900 p-8 rounded-2xl shadow-xl flex flex-col justify-center items-center text-center group relative overflow-hidden">
               <div className="absolute top-0 left-0 w-full h-full bg-gradient-to-br from-blue-600/20 to-indigo-600/20 z-0"></div>
              <div className="relative z-10">
                <h4 className="text-2xl font-bold text-white mb-4">Need a Custom Strategy?</h4>
                <p className="text-slate-300 mb-6">Let's build a tailored plan that fits your exact business goals.</p>
                <a 
                  href="#contact" 
                  onClick={(e) => handleNavClick(e, 'contact')}
                  className="bg-white text-slate-900 px-6 py-3 rounded-full font-semibold hover:bg-blue-50 transition-colors inline-block"
                >
                  Book a Consultation
                </a>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* --- PORTFOLIO / CASE STUDIES --- */}
      <section id="portfolio" className="py-24 bg-white">
        <div className="container mx-auto px-6 md:px-12">
          <div className="flex flex-col md:flex-row md:items-end justify-between mb-16 gap-6">
            <div className="max-w-2xl">
              <h2 className="text-blue-600 font-semibold tracking-wide uppercase text-sm mb-3">Case Studies</h2>
              <h3 className="text-3xl md:text-5xl font-bold text-slate-900">Proven Results.</h3>
            </div>
            <a href="#contact" className="text-blue-600 font-semibold hover:text-blue-800 flex items-center gap-2">
              View all case studies <ArrowRight className="w-5 h-5" />
            </a>
          </div>

          <div className="grid md:grid-cols-2 gap-10">
            {/* Case Study 1 */}
            <div className="group cursor-pointer">
              <div className="relative overflow-hidden rounded-2xl mb-6 bg-slate-100 aspect-[4/3]">
                <img 
                  src="https://images.unsplash.com/photo-1460925895917-afdab827c52f?auto=format&fit=crop&q=80&w=800" 
                  alt="E-commerce Growth Graph" 
                  className="object-cover w-full h-full group-hover:scale-105 transition-transform duration-500"
                />
                <div className="absolute top-4 left-4 bg-white/90 backdrop-blur-sm px-4 py-2 rounded-full text-sm font-bold text-slate-900 shadow-sm">
                  +240% Revenue
                </div>
              </div>
              <h4 className="text-2xl font-bold text-slate-900 mb-2 group-hover:text-blue-600 transition-colors">TechWear E-Commerce Scaling</h4>
              <p className="text-slate-600 mb-4">Complete SEO overhaul and aggressive PPC scaling led to record-breaking Q4 revenue.</p>
              <div className="flex gap-2">
                <span className="text-xs font-semibold px-3 py-1 bg-slate-100 text-slate-600 rounded-full">SEO</span>
                <span className="text-xs font-semibold px-3 py-1 bg-slate-100 text-slate-600 rounded-full">PPC</span>
              </div>
            </div>

            {/* Case Study 2 */}
            <div className="group cursor-pointer">
              <div className="relative overflow-hidden rounded-2xl mb-6 bg-slate-100 aspect-[4/3]">
                <img 
                  src="https://images.unsplash.com/photo-1551288049-bebda4e38f71?auto=format&fit=crop&q=80&w=800" 
                  alt="Data Dashboard" 
                  className="object-cover w-full h-full group-hover:scale-105 transition-transform duration-500"
                />
                <div className="absolute top-4 left-4 bg-white/90 backdrop-blur-sm px-4 py-2 rounded-full text-sm font-bold text-slate-900 shadow-sm">
                  15k New Leads
                </div>
              </div>
              <h4 className="text-2xl font-bold text-slate-900 mb-2 group-hover:text-blue-600 transition-colors">SaaS Lead Generation</h4>
              <p className="text-slate-600 mb-4">Content marketing and automated email sequences decreased Customer Acquisition Cost by 45%.</p>
              <div className="flex gap-2">
                <span className="text-xs font-semibold px-3 py-1 bg-slate-100 text-slate-600 rounded-full">Content</span>
                <span className="text-xs font-semibold px-3 py-1 bg-slate-100 text-slate-600 rounded-full">Email</span>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* --- TESTIMONIALS SECTION --- */}
      <section className="py-24 bg-slate-900 text-white relative overflow-hidden">
        {/* Background glow */}
        <div className="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[800px] bg-blue-600/20 rounded-full blur-[100px] -z-10"></div>
        
        <div className="container mx-auto px-6 md:px-12">
          <div className="text-center max-w-3xl mx-auto mb-16">
            <h2 className="text-blue-400 font-semibold tracking-wide uppercase text-sm mb-3">Client Feedback</h2>
            <h3 className="text-3xl md:text-5xl font-bold mb-6">Don't just take our word for it.</h3>
          </div>

          <div className="grid md:grid-cols-3 gap-8">
            {/* Testimonial 1 */}
            <div className="bg-slate-800/50 backdrop-blur-sm p-8 rounded-2xl border border-slate-700">
              <div className="flex text-yellow-400 mb-6">
                <Star className="w-5 h-5 fill-current" /><Star className="w-5 h-5 fill-current" /><Star className="w-5 h-5 fill-current" /><Star className="w-5 h-5 fill-current" /><Star className="w-5 h-5 fill-current" />
              </div>
              <p className="text-lg text-slate-300 mb-8 italic">"Elevate completely transformed our online presence. Within 6 months, our organic traffic tripled, and our sales team has never been busier."</p>
              <div className="flex items-center gap-4">
                <div className="w-12 h-12 bg-slate-600 rounded-full overflow-hidden">
                   <img src="https://images.unsplash.com/photo-1494790108377-be9c29b29330?auto=format&fit=crop&q=80&w=150" alt="Sarah J." className="w-full h-full object-cover"/>
                </div>
                <div>
                  <h4 className="font-bold">Sarah Jenkins</h4>
                  <p className="text-sm text-slate-400">CMO, TechFlow</p>
                </div>
              </div>
            </div>

            {/* Testimonial 2 */}
            <div className="bg-slate-800/50 backdrop-blur-sm p-8 rounded-2xl border border-slate-700">
              <div className="flex text-yellow-400 mb-6">
                <Star className="w-5 h-5 fill-current" /><Star className="w-5 h-5 fill-current" /><Star className="w-5 h-5 fill-current" /><Star className="w-5 h-5 fill-current" /><Star className="w-5 h-5 fill-current" />
              </div>
              <p className="text-lg text-slate-300 mb-8 italic">"The team's attention to detail and data-driven approach is unmatched. Our ROAS on Facebook ads went from 1.5x to 4.2x in just two quarters."</p>
              <div className="flex items-center gap-4">
                <div className="w-12 h-12 bg-slate-600 rounded-full overflow-hidden">
                  <img src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?auto=format&fit=crop&q=80&w=150" alt="Michael C." className="w-full h-full object-cover"/>
                </div>
                <div>
                  <h4 className="font-bold">Michael Chen</h4>
                  <p className="text-sm text-slate-400">Founder, StyleHouse</p>
                </div>
              </div>
            </div>

            {/* Testimonial 3 */}
            <div className="bg-slate-800/50 backdrop-blur-sm p-8 rounded-2xl border border-slate-700">
              <div className="flex text-yellow-400 mb-6">
                <Star className="w-5 h-5 fill-current" /><Star className="w-5 h-5 fill-current" /><Star className="w-5 h-5 fill-current" /><Star className="w-5 h-5 fill-current" /><Star className="w-5 h-5 fill-current" />
              </div>
              <p className="text-lg text-slate-300 mb-8 italic">"Choosing Elevate was the best marketing decision we've made. Their SEO content strategy established us as industry thought leaders."</p>
              <div className="flex items-center gap-4">
                <div className="w-12 h-12 bg-slate-600 rounded-full overflow-hidden">
                  <img src="https://images.unsplash.com/photo-1438761681033-6461ffad8d80?auto=format&fit=crop&q=80&w=150" alt="Elena R." className="w-full h-full object-cover"/>
                </div>
                <div>
                  <h4 className="font-bold">Elena Rodriguez</h4>
                  <p className="text-sm text-slate-400">Director, Nexus Health</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* --- PRICING SECTION --- */}
      <section id="pricing" className="py-24 bg-slate-50">
        <div className="container mx-auto px-6 md:px-12">
          <div className="text-center max-w-3xl mx-auto mb-16">
            <h2 className="text-blue-600 font-semibold tracking-wide uppercase text-sm mb-3">Transparent Pricing</h2>
            <h3 className="text-3xl md:text-5xl font-bold text-slate-900 mb-6">Plans to fuel your growth.</h3>
            <p className="text-lg text-slate-600">No hidden fees, no long-term lock-ins. Just pure value.</p>
          </div>

          <div className="grid md:grid-cols-3 gap-8 max-w-6xl mx-auto items-center">
            {/* Basic Plan */}
            <div className="bg-white p-8 rounded-3xl shadow-sm border border-slate-200">
              <h4 className="text-xl font-bold text-slate-900 mb-2">Starter</h4>
              <p className="text-slate-500 text-sm mb-6">Perfect for small businesses getting started.</p>
              <div className="mb-8">
                <span className="text-4xl font-extrabold text-slate-900">$999</span>
                <span className="text-slate-500">/month</span>
              </div>
              <ul className="space-y-4 mb-8">
                <li className="flex items-start gap-3"><CheckCircle2 className="w-5 h-5 text-blue-500 shrink-0" /><span className="text-slate-600">Basic SEO Audit & Setup</span></li>
                <li className="flex items-start gap-3"><CheckCircle2 className="w-5 h-5 text-blue-500 shrink-0" /><span className="text-slate-600">2 Social Media Platforms</span></li>
                <li className="flex items-start gap-3"><CheckCircle2 className="w-5 h-5 text-blue-500 shrink-0" /><span className="text-slate-600">Monthly Performance Report</span></li>
                <li className="flex items-start gap-3"><CheckCircle2 className="w-5 h-5 text-slate-300 shrink-0" /><span className="text-slate-400 line-through">PPC Management</span></li>
                <li className="flex items-start gap-3"><CheckCircle2 className="w-5 h-5 text-slate-300 shrink-0" /><span className="text-slate-400 line-through">Dedicated Account Manager</span></li>
              </ul>
              <a href="#contact" className="block w-full py-3 px-4 bg-slate-100 hover:bg-slate-200 text-slate-900 font-bold text-center rounded-xl transition-colors">Choose Starter</a>
            </div>

            {/* Pro Plan (Highlighted) */}
            <div className="bg-slate-900 text-white p-8 md:py-12 rounded-3xl shadow-2xl border border-slate-800 relative transform md:-translate-y-4 z-10">
              <div className="absolute top-0 left-1/2 -translate-x-1/2 -translate-y-1/2 bg-gradient-to-r from-blue-600 to-indigo-600 text-white text-xs font-bold px-4 py-1.5 rounded-full uppercase tracking-wider">
                Most Popular
              </div>
              <h4 className="text-xl font-bold mb-2">Growth</h4>
              <p className="text-slate-400 text-sm mb-6">For brands ready to scale aggressively.</p>
              <div className="mb-8">
                <span className="text-5xl font-extrabold">$2,499</span>
                <span className="text-slate-400">/month</span>
              </div>
              <ul className="space-y-4 mb-8">
                <li className="flex items-start gap-3"><CheckCircle2 className="w-5 h-5 text-blue-400 shrink-0" /><span className="text-slate-200">Advanced SEO & Content Strategy</span></li>
                <li className="flex items-start gap-3"><CheckCircle2 className="w-5 h-5 text-blue-400 shrink-0" /><span className="text-slate-200">All Social Platforms Management</span></li>
                <li className="flex items-start gap-3"><CheckCircle2 className="w-5 h-5 text-blue-400 shrink-0" /><span className="text-slate-200">PPC Campaign Management ($5k spend)</span></li>
                <li className="flex items-start gap-3"><CheckCircle2 className="w-5 h-5 text-blue-400 shrink-0" /><span className="text-slate-200">Bi-weekly Strategy Calls</span></li>
                <li className="flex items-start gap-3"><CheckCircle2 className="w-5 h-5 text-blue-400 shrink-0" /><span className="text-slate-200">Dedicated Account Manager</span></li>
              </ul>
              <a href="#contact" className="block w-full py-4 px-4 bg-blue-600 hover:bg-blue-500 text-white font-bold text-center rounded-xl transition-colors shadow-lg shadow-blue-600/30">Choose Growth</a>
            </div>

            {/* Premium Plan */}
            <div className="bg-white p-8 rounded-3xl shadow-sm border border-slate-200">
              <h4 className="text-xl font-bold text-slate-900 mb-2">Enterprise</h4>
              <p className="text-slate-500 text-sm mb-6">Custom solutions for market leaders.</p>
              <div className="mb-8">
                <span className="text-4xl font-extrabold text-slate-900">Custom</span>
              </div>
              <ul className="space-y-4 mb-8">
                <li className="flex items-start gap-3"><CheckCircle2 className="w-5 h-5 text-blue-500 shrink-0" /><span className="text-slate-600">Omnichannel Marketing Strategy</span></li>
                <li className="flex items-start gap-3"><CheckCircle2 className="w-5 h-5 text-blue-500 shrink-0" /><span className="text-slate-600">Custom Web Development & CRO</span></li>
                <li className="flex items-start gap-3"><CheckCircle2 className="w-5 h-5 text-blue-500 shrink-0" /><span className="text-slate-600">Unlimited Ad Spend Management</span></li>
                <li className="flex items-start gap-3"><CheckCircle2 className="w-5 h-5 text-blue-500 shrink-0" /><span className="text-slate-600">Full PR & Media Buying</span></li>
                <li className="flex items-start gap-3"><CheckCircle2 className="w-5 h-5 text-blue-500 shrink-0" /><span className="text-slate-600">24/7 Priority Support</span></li>
              </ul>
              <a href="#contact" className="block w-full py-3 px-4 bg-slate-100 hover:bg-slate-200 text-slate-900 font-bold text-center rounded-xl transition-colors">Let's Talk</a>
            </div>
          </div>
        </div>
      </section>

      {/* --- BLOG SECTION --- */}
      <section id="blog" className="py-24 bg-white">
        <div className="container mx-auto px-6 md:px-12">
          <div className="flex flex-col md:flex-row md:items-end justify-between mb-16 gap-6">
            <div className="max-w-2xl">
              <h2 className="text-blue-600 font-semibold tracking-wide uppercase text-sm mb-3">Insights</h2>
              <h3 className="text-3xl md:text-5xl font-bold text-slate-900">Latest from the Blog.</h3>
            </div>
            <a href="#" className="text-blue-600 font-semibold hover:text-blue-800 flex items-center gap-2">
              Read all articles <ArrowRight className="w-5 h-5" />
            </a>
          </div>

          <div className="grid md:grid-cols-3 gap-8">
            {/* Article 1 */}
            <article className="group cursor-pointer">
              <div className="overflow-hidden rounded-2xl mb-4 aspect-video">
                <img src="https://images.unsplash.com/photo-1432821596592-e2c18b78144f?auto=format&fit=crop&q=80&w=600" alt="Blog Post" className="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"/>
              </div>
              <div className="text-sm font-semibold text-blue-600 mb-2">SEO Strategy</div>
              <h4 className="text-xl font-bold text-slate-900 mb-2 group-hover:text-blue-600 transition-colors line-clamp-2">The Future of Search: Navigating AI and Zero-Click Algorithms</h4>
              <p className="text-slate-600 line-clamp-2 mb-4">Learn how generative AI is reshaping the SERPs and what your brand needs to do to maintain visibility.</p>
              <span className="text-sm font-medium text-slate-500">March 15, 2026 • 5 min read</span>
            </article>

            {/* Article 2 */}
            <article className="group cursor-pointer">
              <div className="overflow-hidden rounded-2xl mb-4 aspect-video">
                <img src="https://images.unsplash.com/photo-1611162617474-5b21e879e113?auto=format&fit=crop&q=80&w=600" alt="Blog Post" className="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"/>
              </div>
              <div className="text-sm font-semibold text-indigo-600 mb-2">Social Media</div>
              <h4 className="text-xl font-bold text-slate-900 mb-2 group-hover:text-blue-600 transition-colors line-clamp-2">Video Marketing Mastery for B2B Tech Companies</h4>
              <p className="text-slate-600 line-clamp-2 mb-4">Short-form video isn't just for Gen Z. Discover how B2B brands are leveraging TikTok and Reels for lead gen.</p>
              <span className="text-sm font-medium text-slate-500">March 10, 2026 • 7 min read</span>
            </article>

            {/* Article 3 */}
            <article className="group cursor-pointer">
              <div className="overflow-hidden rounded-2xl mb-4 aspect-video">
                <img src="https://images.unsplash.com/photo-1551288049-bebda4e38f71?auto=format&fit=crop&q=80&w=600" alt="Blog Post" className="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"/>
              </div>
              <div className="text-sm font-semibold text-emerald-600 mb-2">PPC & Analytics</div>
              <h4 className="text-xl font-bold text-slate-900 mb-2 group-hover:text-blue-600 transition-colors line-clamp-2">Understanding Multi-Touch Attribution in 2026</h4>
              <p className="text-slate-600 line-clamp-2 mb-4">Stop guessing which channel drives sales. A comprehensive guide to setting up proper attribution models.</p>
              <span className="text-sm font-medium text-slate-500">March 2, 2026 • 6 min read</span>
            </article>
          </div>
        </div>
      </section>

      {/* --- CONTACT SECTION --- */}
      <section id="contact" className="py-24 bg-slate-50 relative">
        <div className="container mx-auto px-6 md:px-12">
          <div className="bg-white rounded-3xl shadow-xl overflow-hidden flex flex-col lg:flex-row">
            
            {/* Contact Info (Left) */}
            <div className="lg:w-2/5 bg-slate-900 text-white p-10 md:p-16 relative overflow-hidden">
              <div className="absolute top-0 right-0 w-64 h-64 bg-blue-600/30 rounded-full blur-3xl -translate-y-1/2 translate-x-1/2"></div>
              
              <h3 className="text-3xl font-bold mb-4 relative z-10">Let's talk about your project.</h3>
              <p className="text-slate-300 mb-10 relative z-10">Fill out the form, and our team will get back to you within 24 hours to schedule a discovery call.</p>
              
              <div className="space-y-6 relative z-10">
                <div className="flex items-start gap-4">
                  <div className="w-10 h-10 rounded-full bg-slate-800 flex items-center justify-center shrink-0">
                    <Mail className="w-5 h-5 text-blue-400" />
                  </div>
                  <div>
                    <h5 className="font-semibold text-slate-200">Email Us</h5>
                    <p className="text-slate-400 mt-1">hello@elevateagency.com</p>
                  </div>
                </div>
                <div className="flex items-start gap-4">
                  <div className="w-10 h-10 rounded-full bg-slate-800 flex items-center justify-center shrink-0">
                    <TrendingUp className="w-5 h-5 text-blue-400" />
                  </div>
                  <div>
                    <h5 className="font-semibold text-slate-200">Call Us</h5>
                    <p className="text-slate-400 mt-1">+1 (555) 123-4567</p>
                  </div>
                </div>
              </div>

              <div className="mt-16 relative z-10">
                <h5 className="font-semibold text-slate-200 mb-4">Follow us</h5>
                <div className="flex gap-4">
                  <a href="#" className="w-10 h-10 rounded-full bg-slate-800 flex items-center justify-center hover:bg-blue-600 transition-colors text-white"><Twitter className="w-5 h-5" /></a>
                  <a href="#" className="w-10 h-10 rounded-full bg-slate-800 flex items-center justify-center hover:bg-blue-600 transition-colors text-white"><Linkedin className="w-5 h-5" /></a>
                  <a href="#" className="w-10 h-10 rounded-full bg-slate-800 flex items-center justify-center hover:bg-blue-600 transition-colors text-white"><Instagram className="w-5 h-5" /></a>
                  <a href="#" className="w-10 h-10 rounded-full bg-slate-800 flex items-center justify-center hover:bg-blue-600 transition-colors text-white"><Facebook className="w-5 h-5" /></a>
                </div>
              </div>
            </div>

            {/* Contact Form (Right) */}
            <div className="lg:w-3/5 p-10 md:p-16">
              <h3 className="text-2xl font-bold text-slate-900 mb-8">Send us a message</h3>
              
              <form onSubmit={handleFormSubmit} className="space-y-6">
                <div className="grid md:grid-cols-2 gap-6">
                  <div className="space-y-2">
                    <label htmlFor="name" className="text-sm font-medium text-slate-700">Full Name</label>
                    <input 
                      type="text" 
                      id="name" 
                      required
                      className="w-full px-4 py-3 rounded-xl border border-slate-200 focus:border-blue-600 focus:ring-2 focus:ring-blue-600/20 outline-none transition-all bg-slate-50"
                      placeholder="John Doe"
                    />
                  </div>
                  <div className="space-y-2">
                    <label htmlFor="email" className="text-sm font-medium text-slate-700">Email Address</label>
                    <input 
                      type="email" 
                      id="email" 
                      required
                      className="w-full px-4 py-3 rounded-xl border border-slate-200 focus:border-blue-600 focus:ring-2 focus:ring-blue-600/20 outline-none transition-all bg-slate-50"
                      placeholder="john@example.com"
                    />
                  </div>
                </div>
                
                <div className="space-y-2">
                  <label htmlFor="service" className="text-sm font-medium text-slate-700">Service Interested In</label>
                  <select 
                    id="service" 
                    className="w-full px-4 py-3 rounded-xl border border-slate-200 focus:border-blue-600 focus:ring-2 focus:ring-blue-600/20 outline-none transition-all bg-slate-50 appearance-none"
                  >
                    <option value="">Select a service...</option>
                    <option value="seo">SEO Optimization</option>
                    <option value="ppc">PPC Advertising</option>
                    <option value="social">Social Media</option>
                    <option value="content">Content Marketing</option>
                    <option value="full">Full Service Stack</option>
                  </select>
                </div>

                <div className="space-y-2">
                  <label htmlFor="message" className="text-sm font-medium text-slate-700">Your Message</label>
                  <textareatextarea 
                    id="message" 
                    rows="4" 
                    required
                    className="w-full px-4 py-3 rounded-xl border border-slate-200 focus:border-blue-600 focus:ring-2 focus:ring-blue-600/20 outline-none transition-all bg-slate-50 resize-none"
                    placeholder="Tell us about your goals..."
                  ></textarea>
                </div>

                <button 
                  type="submit" 
                  disabled={formStatus === 'submitting'}
                  className="w-full py-4 bg-blue-600 hover:bg-blue-700 text-white font-bold rounded-xl transition-all shadow-lg shadow-blue-600/30 flex items-center justify-center gap-2 disabled:opacity-70"
                >
                  {formStatus === 'idle' && <><Send className="w-5 h-5" /> Send Message</>}
                  {formStatus === 'submitting' && 'Sending...'}
                  {formStatus === 'success' && <><CheckCircle2 className="w-5 h-5" /> Message Sent!</>}
                </button>
              </form>
            </div>
          </div>
        </div>
      </section>

      {/* --- FOOTER --- */}
      <footer className="bg-slate-950 text-slate-400 py-16 border-t border-slate-900">
        <div className="container mx-auto px-6 md:px-12">
          <div className="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-5 gap-8 lg:gap-12 mb-12">
            
            {/* Brand Column */}
            <div className="col-span-2 lg:col-span-2">
              <div className="flex items-center gap-2 mb-6">
                <TrendingUp className="w-7 h-7 text-blue-500" />
                <span className="text-2xl font-bold tracking-tighter text-white">Elevate<span className="text-blue-500">.</span></span>
              </div>
              <p className="text-sm leading-relaxed mb-6 max-w-sm">
                A premium digital marketing agency dedicated to scaling brands through data-driven strategies and creative excellence.
              </p>
            </div>

            {/* Links Column */}
            <div>
              <h6 className="text-white font-semibold mb-4">Company</h6>
              <ul className="space-y-3 text-sm">
                <li><a href="#about" onClick={(e) => handleNavClick(e, 'about')} className="hover:text-blue-400 transition-colors">About Us</a></li>
                <li><a href="#portfolio" onClick={(e) => handleNavClick(e, 'portfolio')} className="hover:text-blue-400 transition-colors">Careers</a></li>
                <li><a href="#blog" onClick={(e) => handleNavClick(e, 'blog')} className="hover:text-blue-400 transition-colors">News & Blog</a></li>
                <li><a href="#contact" onClick={(e) => handleNavClick(e, 'contact')} className="hover:text-blue-400 transition-colors">Contact</a></li>
              </ul>
            </div>

            {/* Services Column */}
            <div>
              <h6 className="text-white font-semibold mb-4">Services</h6>
              <ul className="space-y-3 text-sm">
                <li><a href="#services" onClick={(e) => handleNavClick(e, 'services')} className="hover:text-blue-400 transition-colors">SEO Optimization</a></li>
                <li><a href="#services" onClick={(e) => handleNavClick(e, 'services')} className="hover:text-blue-400 transition-colors">PPC Campaigns</a></li>
                <li><a href="#services" onClick={(e) => handleNavClick(e, 'services')} className="hover:text-blue-400 transition-colors">Social Media</a></li>
                <li><a href="#services" onClick={(e) => handleNavClick(e, 'services')} className="hover:text-blue-400 transition-colors">Content Strategy</a></li>
              </ul>
            </div>

            {/* Legal Column */}
            <div>
              <h6 className="text-white font-semibold mb-4">Legal</h6>
              <ul className="space-y-3 text-sm">
                <li><a href="#" className="hover:text-blue-400 transition-colors">Privacy Policy</a></li>
                <li><a href="#" className="hover:text-blue-400 transition-colors">Terms of Service</a></li>
                <li><a href="#" className="hover:text-blue-400 transition-colors">Cookie Policy</a></li>
              </ul>
            </div>
          </div>

          <div className="pt-8 border-t border-slate-800 flex flex-col md:flex-row items-center justify-between gap-4 text-sm">
            <p>&copy; {new Date().getFullYear()} Elevate Digital Agency. All rights reserved.</p>
            <p className="flex items-center gap-1">Designed with <span className="text-red-500">♥</span> for growth.</p>
          </div>
        </div>
      </footer>

    </div>
  );
}
