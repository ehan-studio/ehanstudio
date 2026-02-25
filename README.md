# ehanstudio
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ehan Studio | Creative Digital Agency</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=Syne:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Space Grotesk', sans-serif;
            background: #0a0a0a;
            color: #ffffff;
            overflow-x: hidden;
        }
        
        .font-display {
            font-family: 'Syne', sans-serif;
        }
        
        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #0a0a0a;
        }
        ::-webkit-scrollbar-thumb {
            background: #333;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #555;
        }
        
        /* Noise Texture Overlay */
        .noise-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 9999;
            opacity: 0.03;
            background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)'/%3E%3C/svg%3E");
        }
        
        /* Magnetic Button Effect */
        .magnetic-btn {
            transition: transform 0.3s cubic-bezier(0.23, 1, 0.32, 1);
        }
        
        /* Text Reveal Animation */
        .reveal-text {
            clip-path: polygon(0 0, 100% 0, 100% 100%, 0% 100%);
        }
        
        .reveal-text span {
            display: inline-block;
            transform: translateY(100%);
            opacity: 0;
            animation: revealUp 0.8s cubic-bezier(0.16, 1, 0.3, 1) forwards;
        }
        
        @keyframes revealUp {
            to {
                transform: translateY(0);
                opacity: 1;
            }
        }
        
        /* Gradient Text */
        .gradient-text {
            background: linear-gradient(135deg, #fff 0%, #888 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .gradient-text-accent {
            background: linear-gradient(135deg, #ff6b6b 0%, #feca57 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        /* Marquee Animation */
        .marquee-container {
            overflow: hidden;
            white-space: nowrap;
        }
        
        .marquee-content {
            display: inline-block;
            animation: marquee 20s linear infinite;
        }
        
        @keyframes marquee {
            0% { transform: translateX(0); }
            100% { transform: translateX(-50%); }
        }
        
        /* Card Hover Effects */
        .project-card {
            transition: all 0.5s cubic-bezier(0.23, 1, 0.32, 1);
        }
        
        .project-card:hover {
            transform: translateY(-10px);
        }
        
        .project-card:hover .project-image {
            transform: scale(1.05);
        }
        
        .project-image {
            transition: transform 0.7s cubic-bezier(0.23, 1, 0.32, 1);
        }
        
        /* Cursor Follower */
        .cursor-dot,
        .cursor-outline {
            position: fixed;
            top: 0;
            left: 0;
            transform: translate(-50%, -50%);
            border-radius: 50%;
            z-index: 9999;
            pointer-events: none;
        }
        
        .cursor-dot {
            width: 5px;
            height: 5px;
            background-color: white;
        }
        
        .cursor-outline {
            width: 30px;
            height: 30px;
            border: 1px solid rgba(255, 255, 255, 0.5);
            transition: width 0.2s, height 0.2s, background-color 0.2s;
        }
        
        .cursor-outline.hover {
            width: 60px;
            height: 60px;
            background-color: rgba(255, 255, 255, 0.1);
            border-color: transparent;
        }
        
        /* Navigation */
        .nav-link {
            position: relative;
            overflow: hidden;
        }
        
        .nav-link::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 1px;
            background: white;
            transform: translateX(-100%);
            transition: transform 0.3s ease;
        }
        
        .nav-link:hover::after {
            transform: translateX(0);
        }
        
        /* Service Card Stack */
        .service-card {
            transition: all 0.5s cubic-bezier(0.23, 1, 0.32, 1);
        }
        
        /* Floating Animation */
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
        }
        
        .float-animation {
            animation: float 6s ease-in-out infinite;
        }
        
        /* Grid Background */
        .grid-bg {
            background-size: 50px 50px;
            background-image: linear-gradient(to right, rgba(255, 255, 255, 0.03) 1px, transparent 1px),
                              linear-gradient(to bottom, rgba(255, 255, 255, 0.03) 1px, transparent 1px);
        }
        
        /* Smooth Scroll */
        html {
            scroll-behavior: smooth;
        }
        
        /* Loading Screen */
        .loader {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #0a0a0a;
            z-index: 10000;
            display: flex;
            justify-content: center;
            align-items: center;
            transition: opacity 0.5s ease, visibility 0.5s ease;
        }
        
        .loader.hidden {
            opacity: 0;
            visibility: hidden;
        }
        
        .loader-text {
            font-size: 2rem;
            font-weight: 700;
            letter-spacing: 0.2em;
            animation: pulse 1.5s ease-in-out infinite;
        }
        
        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.3; }
        }
    </style>
</head>
<body class="antialiased">
    <!-- Loading Screen -->
    <div class="loader" id="loader">
        <div class="loader-text font-display">EHAN STUDIO</div>
    </div>
    
    <!-- Noise Overlay -->
    <div class="noise-overlay"></div>
    
    <!-- Custom Cursor -->
    <div class="cursor-dot hidden md:block"></div>
    <div class="cursor-outline hidden md:block"></div>
    
    <!-- Navigation -->
    <nav class="fixed top-0 left-0 w-full z-50 px-6 py-6 mix-blend-difference">
        <div class="max-w-7xl mx-auto flex justify-between items-center">
            <a href="#" class="font-display text-2xl font-bold tracking-tighter hover:opacity-70 transition-opacity">
                EHAN<span class="text-gray-500">.</span>
            </a>
            
            <div class="hidden md:flex items-center gap-8">
                <a href="#work" class="nav-link text-sm uppercase tracking-widest hover:text-gray-400 transition-colors">Work</a>
                <a href="#services" class="nav-link text-sm uppercase tracking-widest hover:text-gray-400 transition-colors">Services</a>
                <a href="#about" class="nav-link text-sm uppercase tracking-widest hover:text-gray-400 transition-colors">About</a>
                <a href="#contact" class="nav-link text-sm uppercase tracking-widest hover:text-gray-400 transition-colors">Contact</a>
            </div>
            
            <button class="md:hidden magnetic-btn p-2" id="menuBtn">
                <i data-lucide="menu" class="w-6 h-6"></i>
            </button>
        </div>
    </nav>
    
    <!-- Mobile Menu -->
    <div class="fixed inset-0 bg-black z-40 transform translate-x-full transition-transform duration-500 ease-out" id="mobileMenu">
        <div class="flex flex-col items-center justify-center h-full gap-8">
            <a href="#work" class="font-display text-4xl font-bold hover:text-gray-400 transition-colors mobile-link">Work</a>
            <a href="#services" class="font-display text-4xl font-bold hover:text-gray-400 transition-colors mobile-link">Services</a>
            <a href="#about" class="font-display text-4xl font-bold hover:text-gray-400 transition-colors mobile-link">About</a>
            <a href="#contact" class="font-display text-4xl font-bold hover:text-gray-400 transition-colors mobile-link">Contact</a>
            <button class="absolute top-6 right-6 p-2" id="closeMenu">
                <i data-lucide="x" class="w-8 h-8"></i>
            </button>
        </div>
    </div>

    <!-- Hero Section -->
    <section class="relative min-h-screen flex items-center justify-center overflow-hidden grid-bg">
        <!-- Background Elements -->
        <div class="absolute inset-0 overflow-hidden">
            <div class="absolute top-1/4 left-1/4 w-96 h-96 bg-purple-500/20 rounded-full blur-[120px] float-animation"></div>
            <div class="absolute bottom-1/4 right-1/4 w-96 h-96 bg-orange-500/20 rounded-full blur-[120px] float-animation" style="animation-delay: -3s;"></div>
        </div>
        
        <div class="relative z-10 text-center px-6 max-w-6xl mx-auto">
            <div class="mb-6 overflow-hidden">
                <p class="text-sm md:text-base uppercase tracking-[0.3em] text-gray-400 reveal-text">
                    <span style="animation-delay: 0.1s">Creative</span>
                    <span style="animation-delay: 0.2s">Digital</span>
                    <span style="animation-delay: 0.3s">Studio</span>
                </p>
            </div>
            
            <h1 class="font-display text-6xl md:text-8xl lg:text-9xl font-bold leading-none mb-8">
                <div class="overflow-hidden">
                    <span class="block reveal-text">
                        <span style="animation-delay: 0.4s">WE CREATE</span>
                    </span>
                </div>
                <div class="overflow-hidden">
                    <span class="block reveal-text gradient-text-accent">
                        <span style="animation-delay: 0.6s">DIGITAL</span>
                    </span>
                </div>
                <div class="overflow-hidden">
                    <span class="block reveal-text">
                        <span style="animation-delay: 0.8s">EXPERIENCES</span>
                    </span>
                </div>
            </h1>
            
            <div class="overflow-hidden mt-12">
                <p class="text-lg md:text-xl text-gray-400 max-w-2xl mx-auto reveal-text">
                    <span style="animation-delay: 1s">
                        Transforming brands through bold design, innovative technology, and strategic thinking.
                    </span>
                </p>
            </div>
            
            <div class="mt-12 overflow-hidden reveal-text">
                <span style="animation-delay: 1.2s; display: inline-block;">
                    <a href="#work" class="magnetic-btn inline-flex items-center gap-3 px-8 py-4 border border-white/20 rounded-full hover:bg-white hover:text-black transition-all duration-300 group">
                        <span class="text-sm uppercase tracking-widest">View Our Work</span>
                        <i data-lucide="arrow-down-right" class="w-4 h-4 group-hover:rotate-45 transition-transform"></i>
                    </a>
                </span>
            </div>
        </div>
        
        <!-- Scroll Indicator -->
        <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 animate-bounce">
            <i data-lucide="chevron-down" class="w-6 h-6 text-gray-500"></i>
        </div>
    </section>

    <!-- Marquee Section -->
    <div class="py-8 border-y border-white/10 bg-black overflow-hidden">
        <div class="marquee-container">
            <div class="marquee-content font-display text-4xl md:text-6xl font-bold text-transparent stroke-text">
                <span class="mx-8 text-white/10">BRANDING</span>
                <span class="mx-8 text-white">WEB DESIGN</span>
                <span class="mx-8 text-white/10">DEVELOPMENT</span>
                <span class="mx-8 text-white">MOTION</span>
                <span class="mx-8 text-white/10">STRATEGY</span>
                <span class="mx-8 text-white">UI/UX</span>
                <span class="mx-8 text-white/10">BRANDING</span>
                <span class="mx-8 text-white">WEB DESIGN</span>
                <span class="mx-8 text-white/10">DEVELOPMENT</span>
                <span class="mx-8 text-white">MOTION</span>
                <span class="mx-8 text-white/10">STRATEGY</span>
                <span class="mx-8 text-white">UI/UX</span>
            </div>
        </div>
    </div>

    <!-- Selected Work Section -->
    <section id="work" class="py-32 px-6 relative">
        <div class="max-w-7xl mx-auto">
            <div class="flex flex-col md:flex-row justify-between items-end mb-20">
                <div>
                    <p class="text-sm uppercase tracking-widest text-gray-500 mb-4">Portfolio</p>
                    <h2 class="font-display text-5xl md:text-7xl font-bold">Selected<br>Work</h2>
                </div>
                <div class="mt-6 md:mt-0">
                    <a href="#" class="inline-flex items-center gap-2 text-sm uppercase tracking-widest hover:text-gray-400 transition-colors group">
                        View All Projects
                        <i data-lucide="arrow-right" class="w-4 h-4 group-hover:translate-x-2 transition-transform"></i>
                    </a>
                </div>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <!-- Project 1 -->
                <div class="project-card group cursor-pointer">
                    <div class="relative overflow-hidden rounded-lg aspect-[4/3] mb-6">
                        <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent z-10 opacity-0 group-hover:opacity-100 transition-opacity duration-500"></div>
                        <img src="https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?w=800&q=80" alt="Project 1" class="project-image w-full h-full object-cover">
                        <div class="absolute bottom-6 left-6 z-20 transform translate-y-4 opacity-0 group-hover:translate-y-0 group-hover:opacity-100 transition-all duration-500">
                            <span class="px-4 py-2 bg-white text-black text-xs uppercase tracking-widest rounded-full">View Case</span>
                        </div>
                    </div>
                    <div class="flex justify-between items-start">
                        <div>
                            <h3 class="font-display text-2xl font-bold mb-2">Aurora Finance</h3>
                            <p class="text-gray-400 text-sm">Brand Identity & Web Platform</p>
                        </div>
                        <span class="text-gray-600 text-sm">2024</span>
                    </div>
                </div>
                
                <!-- Project 2 -->
                <div class="project-card group cursor-pointer md:mt-24">
                    <div class="relative overflow-hidden rounded-lg aspect-[4/3] mb-6">
                        <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent z-10 opacity-0 group-hover:opacity-100 transition-opacity duration-500"></div>
                        <img src="https://images.unsplash.com/photo-1558655146-9f40138edfeb?w=800&q=80" alt="Project 2" class="project-image w-full h-full object-cover">
                        <div class="absolute bottom-6 left-6 z-20 transform translate-y-4 opacity-0 group-hover:translate-y-0 group-hover:opacity-100 transition-all duration-500">
                            <span class="px-4 py-2 bg-white text-black text-xs uppercase tracking-widest rounded-full">View Case</span>
                        </div>
                    </div>
                    <div class="flex justify-between items-start">
                        <div>
                            <h3 class="font-display text-2xl font-bold mb-2">Nexus Tech</h3>
                            <p class="text-gray-400 text-sm">Digital Experience & Motion</p>
                        </div>
                        <span class="text-gray-600 text-sm">2024</span>
                    </div>
                </div>
                
                <!-- Project 3 -->
                <div class="project-card group cursor-pointer">
                    <div class="relative overflow-hidden rounded-lg aspect-[4/3] mb-6">
                        <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent z-10 opacity-0 group-hover:opacity-100 transition-opacity duration-500"></div>
                        <img src="https://images.unsplash.com/photo-1561070791-2526d30994b5?w=800&q=80" alt="Project 3" class="project-image w-full h-full object-cover">
                        <div class="absolute bottom-6 left-6 z-20 transform translate-y-4 opacity-0 group-hover:translate-y-0 group-hover:opacity-100 transition-all duration-500">
                            <span class="px-4 py-2 bg-white text-black text-xs uppercase tracking-widest rounded-full">View Case</span>
                        </div>
                    </div>
                    <div class="flex justify-between items-start">
                        <div>
                            <h3 class="font-display text-2xl font-bold mb-2">Velvet Studio</h3>
                            <p class="text-gray-400 text-sm">E-commerce & Brand Strategy</p>
                        </div>
                        <span class="text-gray-600 text-sm">2023</span>
                    </div>
                </div>
                
                <!-- Project 4 -->
                <div class="project-card group cursor-pointer md:mt-24">
                    <div class="relative overflow-hidden rounded-lg aspect-[4/3] mb-6">
                        <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent z-10 opacity-0 group-hover:opacity-100 transition-opacity duration-500"></div>
                        <img src="https://images.unsplash.com/photo-1550745165-9bc0b252726f?w=800&q=80" alt="Project 4" class="project-image w-full h-full object-cover">
                        <div class="absolute bottom-6 left-6 z-20 transform translate-y-4 opacity-0 group-hover:translate-y-0 group-hover:opacity-100 transition-all duration-500">
                            <span class="px-4 py-2 bg-white text-black text-xs uppercase tracking-widest rounded-full">View Case</span>
                        </div>
                    </div>
                    <div class="flex justify-between items-start">
                        <div>
                            <h3 class="font-display text-2xl font-bold mb-2">Quantum Labs</h3>
                            <p class="text-gray-400 text-sm">Interactive Installation</p>
                        </div>
                        <span class="text-gray-600 text-sm">2023</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Services Section -->
    <section id="services" class="py-32 px-6 bg-neutral-900/30 relative overflow-hidden">
        <div class="absolute inset-0 grid-bg opacity-50"></div>
        
        <div class="max-w-7xl mx-auto relative z-10">
            <div class="mb-20">
                <p class="text-sm uppercase tracking-widest text-gray-500 mb-4">What We Do</p>
                <h2 class="font-display text-5xl md:text-7xl font-bold max-w-4xl">We build digital products that matter</h2>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                <!-- Service 1 -->
                <div class="service-card group p-8 border border-white/10 rounded-2xl hover:bg-white hover:text-black transition-all duration-500 cursor-pointer">
                    <div class="mb-6 text-gray-500 group-hover:text-black transition-colors">
                        <i data-lucide="palette" class="w-10 h-10"></i>
                    </div>
                    <h3 class="font-display text-2xl font-bold mb-4">Brand Identity</h3>
                    <p class="text-gray-400 group-hover:text-gray-600 text-sm leading-relaxed">
                        Strategic brand development including visual identity, guidelines, and comprehensive brand systems.
                    </p>
                    <div class="mt-6 flex items-center gap-2 text-sm uppercase tracking-widest opacity-0 group-hover:opacity-100 transition-opacity">
                        <span>Learn More</span>
                        <i data-lucide="arrow-right" class="w-4 h-4"></i>
                    </div>
                </div>
                
                <!-- Service 2 -->
                <div class="service-card group p-8 border border-white/10 rounded-2xl hover:bg-white hover:text-black transition-all duration-500 cursor-pointer">
                    <div class="mb-6 text-gray-500 group-hover:text-black transition-colors">
                        <i data-lucide="monitor" class="w-10 h-10"></i>
                    </div>
                    <h3 class="font-display text-2xl font-bold mb-4">Web Design</h3>
                    <p class="text-gray-400 group-hover:text-gray-600 text-sm leading-relaxed">
                        Immersive digital experiences crafted with cutting-edge design principles and user-centric approaches.
                    </p>
                    <div class="mt-6 flex items-center gap-2 text-sm uppercase tracking-widest opacity-0 group-hover:opacity-100 transition-opacity">
                        <span>Learn More</span>
                        <i data-lucide="arrow-right" class="w-4 h-4"></i>
                    </div>
                </div>
                
                <!-- Service 3 -->
                <div class="service-card group p-8 border border-white/10 rounded-2xl hover:bg-white hover:text-black transition-all duration-500 cursor-pointer">
                    <div class="mb-6 text-gray-500 group-hover:text-black transition-colors">
                        <i data-lucide="code-2" class="w-10 h-10"></i>
                    </div>
                    <h3 class="font-display text-2xl font-bold mb-4">Development</h3>
                    <p class="text-gray-400 group-hover:text-gray-600 text-sm leading-relaxed">
                        Robust frontend and backend solutions built with modern technologies and scalable architecture.
                    </p>
                    <div class="mt-6 flex items-center gap-2 text-sm uppercase tracking-widest opacity-0 group-hover:opacity-100 transition-opacity">
                        <span>Learn More</span>
                        <i data-lucide="arrow-right" class="w-4 h-4"></i>
                    </div>
                </div>
                
                <!-- Service 4 -->
                <div class="service-card group p-8 border border-white/10 rounded-2xl hover:bg-white hover:text-black transition-all duration-500 cursor-pointer">
                    <div class="mb-6 text-gray-500 group-hover:text-black transition-colors">
                        <i data-lucide="play-circle" class="w-10 h-10"></i>
                    </div>
                    <h3 class="font-display text-2xl font-bold mb-4">Motion Design</h3>
                    <p class="text-gray-400 group-hover:text-gray-600 text-sm leading-relaxed">
                        Dynamic animations and motion graphics that bring brands to life across all digital touchpoints.
                    </p>
                    <div class="mt-6 flex items-center gap-2 text-sm uppercase tracking-widest opacity-0 group-hover:opacity-100 transition-opacity">
                        <span>Learn More</span>
                        <i data-lucide="arrow-right" class="w-4 h-4"></i>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-32 px-6 relative">
        <div class="max-w-7xl mx-auto">
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 items-center">
                <div class="relative">
                    <div class="aspect-[3/4] rounded-2xl overflow-hidden">
                        <img src="https://images.unsplash.com/photo-1497366216548-37526070297c?w=800&q=80" alt="Studio" class="w-full h-full object-cover hover:scale-105 transition-transform duration-700">
                    </div>
                    <div class="absolute -bottom-8 -right-8 w-48 h-48 bg-gradient-to-br from-orange-500 to-purple-600 rounded-2xl -z-10"></div>
                </div>
                
                <div>
                    <p class="text-sm uppercase tracking-widest text-gray-500 mb-4">About Us</p>
                    <h2 class="font-display text-5xl md:text-6xl font-bold mb-8">Crafting digital excellence since 2018</h2>
                    <div class="space-y-6 text-gray-400 text-lg leading-relaxed">
                        <p>
                            Ehan Studio is a multidisciplinary creative agency specializing in brand strategy, digital design, and technology. We partner with ambitious brands to create meaningful connections through exceptional digital experiences.
                        </p>
                        <p>
                            Our team of strategists, designers, and developers work collaboratively to deliver solutions that not only look stunning but drive real business results. We believe in the power of design to transform businesses and touch lives.
                        </p>
                    </div>
                    
                    <div class="grid grid-cols-3 gap-8 mt-12 pt-12 border-t border-white/10">
                        <div>
                            <span class="font-display text-4xl font-bold gradient-text-accent">150+</span>
                            <p class="text-gray-500 text-sm mt-2">Projects Delivered</p>
                        </div>
                        <div>
                            <span class="font-display text-4xl font-bold gradient-text-accent">40+</span>
                            <p class="text-gray-500 text-sm mt-2">Happy Clients</p>
                        </div>
                        <div>
                            <span class="font-display text-4xl font-bold gradient-text-accent">12</span>
                            <p class="text-gray-500 text-sm mt-2">Awards Won</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Testimonials -->
    <section class="py-32 px-6 bg-neutral-900/30">
        <div class="max-w-5xl mx-auto text-center">
            <i data-lucide="quote" class="w-12 h-12 text-gray-600 mx-auto mb-8"></i>
            <blockquote class="font-display text-3xl md:text-5xl font-bold leading-tight mb-8">
                "Ehan Studio transformed our digital presence completely. Their attention to detail and creative vision exceeded all our expectations."
            </blockquote>
            <div class="flex items-center justify-center gap-4">
                <img src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?w=100&q=80" alt="Client" class="w-12 h-12 rounded-full object-cover">
                <div class="text-left">
                    <p class="font-bold">Marcus Chen</p>
                    <p class="text-gray-500 text-sm">CEO, TechVentures</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-32 px-6 relative overflow-hidden">
        <div class="absolute inset-0 bg-gradient-to-b from-transparent via-purple-900/10 to-transparent"></div>
        
        <div class="max-w-4xl mx-auto relative z-10 text-center">
            <p class="text-sm uppercase tracking-widest text-gray-500 mb-4">Get In Touch</p>
            <h2 class="font-display text-5xl md:text-7xl font-bold mb-8">Let's create<br>something great</h2>
            <p class="text-gray-400 text-lg mb-12 max-w-2xl mx-auto">
                Have a project in mind? We'd love to hear about it. Let's discuss how we can help bring your vision to life.
            </p>
            
            <a href="mailto:hello@ehan.studio" class="magnetic-btn inline-flex items-center gap-4 px-12 py-6 bg-white text-black rounded-full text-lg font-bold hover:scale-105 transition-transform group">
                <span>Start a Project</span>
                <i data-lucide="arrow-up-right" class="w-5 h-5 group-hover:rotate-45 transition-transform"></i>
            </a>
            
            <div class="mt-20 flex flex-col md:flex-row justify-center items-center gap-8 text-gray-500">
                <a href="mailto:hello@ehan.studio" class="hover:text-white transition-colors">hello@ehan.studio</a>
                <span class="hidden md:block">•</span>
                <a href="tel:+1234567890" class="hover:text-white transition-colors">+1 (234) 567-890</a>
                <span class="hidden md:block">•</span>
                <span>New York, NY</span>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="py-12 px-6 border-t border-white/10">
        <div class="max-w-7xl mx-auto flex flex-col md:flex-row justify-between items-center gap-6">
            <div class="font-display text-2xl font-bold">EHAN<span class="text-gray-500">.</span></div>
            
            <div class="flex gap-6">
                <a href="#" class="hover:text-gray-400 transition-colors"><i data-lucide="twitter" class="w-5 h-5"></i></a>
                <a href="#" class="hover:text-gray-400 transition-colors"><i data-lucide="instagram" class="w-5 h-5"></i></a>
                <a href="#" class="hover:text-gray-400 transition-colors"><i data-lucide="linkedin" class="w-5 h-5"></i></a>
                <a href="#" class="hover:text-gray-400 transition-colors"><i data-lucide="dribbble" class="w-5 h-5"></i></a>
            </div>
            
            <p class="text-gray-600 text-sm">© 2024 Ehan Studio. All rights reserved.</p>
        </div>
    </footer>

    <script>
        // Initialize Lucide Icons
        lucide.createIcons();
        
        // Remove Loader
        window.addEventListener('load', () => {
            setTimeout(() => {
                document.getElementById('loader').classList.add('hidden');
            }, 1000);
        });
        
        // Custom Cursor
        const cursorDot = document.querySelector('.cursor-dot');
        const cursorOutline = document.querySelector('.cursor-outline');
        
        window.addEventListener('mousemove', (e) => {
            const posX = e.clientX;
            const posY = e.clientY;
            
            cursorDot.style.left = `${posX}px`;
            cursorDot.style.top = `${posY}px`;
            
            cursorOutline.animate({
                left: `${posX}px`,
                top: `${posY}px`
            }, { duration: 500, fill: "forwards" });
        });
        
        // Hover effect for cursor
        const interactiveElements = document.querySelectorAll('a, button, .project-card, .service-card');
        interactiveElements.forEach(el => {
            el.addEventListener('mouseenter', () => cursorOutline.classList.add('hover'));
            el.addEventListener('mouseleave', () => cursorOutline.classList.remove('hover'));
        });
        
        // Mobile Menu
        const menuBtn = document.getElementById('menuBtn');
        const closeMenu = document.getElementById('closeMenu');
        const mobileMenu = document.getElementById('mobileMenu');
        const mobileLinks = document.querySelectorAll('.mobile-link');
        
        menuBtn.addEventListener('click', () => {
            mobileMenu.classList.remove('translate-x-full');
        });
        
        closeMenu.addEventListener('click', () => {
            mobileMenu.classList.add('translate-x-full');
        });
        
        mobileLinks.forEach(link => {
            link.addEventListener('click', () => {
                mobileMenu.classList.add('translate-x-full');
            });
        });
        
        // Magnetic Button Effect
        const magneticBtns = document.querySelectorAll('.magnetic-btn');
        magneticBtns.forEach(btn => {
            btn.addEventListener('mousemove', (e) => {
                const rect = btn.getBoundingClientRect();
                const x = e.clientX - rect.left - rect.width / 2;
                const y = e.clientY - rect.top - rect.height / 2;
                
                btn.style.transform = `translate(${x * 0.3}px, ${y * 0.3}px)`;
            });
            
            btn.addEventListener('mouseleave', () => {
                btn.style.transform = 'translate(0, 0)';
            });
        });
        
        // Scroll Reveal Animation
        const observerOptions = {
            threshold: 0.1,
            rootMargin: "0px 0px -50px 0px"
        };
        
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = "1";
                    entry.target.style.transform = "translateY(0)";
                }
            });
        }, observerOptions);
        
        // Observe elements
        document.querySelectorAll('.project-card, .service-card').forEach((el, index) => {
            el.style.opacity = "0";
            el.style.transform = "translateY(30px)";
            el.style.transition = `all 0.6s cubic-bezier(0.23, 1, 0.32, 1) ${index * 0.1}s`;
            observer.observe(el);
        });
        
        // Parallax Effect on Scroll
        window.addEventListener('scroll', () => {
            const scrolled = window.pageYOffset;
            const parallaxElements = document.querySelectorAll('.float-animation');
            
            parallaxElements.forEach((el, index) => {
                const speed = 0.5 + (index * 0.1);
                el.style.transform = `translateY(${scrolled * speed}px)`;
            });
        });
        
        // Smooth scroll for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });
    </script>
</body>
</html>
