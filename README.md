<html lang="en"><head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UMWTV South Africa - Official Government Partnership</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Font Awesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Three.js -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <!-- GSAP for animations -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.11.4/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.11.4/ScrollTrigger.min.js"></script>
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        'sa-red': '#FF0000',
                        'sa-blue': '#0000FF',
                        'sa-green': '#00FF00',
                        'sa-yellow': '#FFFF00',
                        'sa-black': '#000000',
                        'sa-white': '#FFFFFF',
                        'umwtv-blue': '#0056b3',
                        'umwtv-light-blue': '#4a90e2',
                    },
                    fontFamily: {
                        sans: ['Arial', 'Helvetica', 'sans-serif'],
                        serif: ['Georgia', 'serif'],
                    },
                }
            }
        }
    </script>
    
    <style>
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .animate-fade-in {
            animation: fadeIn 0.8s ease-out forwards;
        }
        
        .timeline-item {
            position: relative;
            padding-left: 30px;
            margin-bottom: 2rem;
        }
        
        .timeline-item::before {
            content: '';
            position: absolute;
            left: 0;
            top: 0;
            height: 100%;
            width: 2px;
            background-color: #0056b3;
        }
        
        .timeline-item::after {
            content: '';
            position: absolute;
            left: -6px;
            top: 0;
            height: 14px;
            width: 14px;
            border-radius: 50%;
            background-color: #0056b3;
        }
        
        .building-canvas {
            width: 100%;
            height: 400px;
            background-color: #f0f0f0;
            border-radius: 8px;
        }
        
        .flag-animation {
            animation: wave 10s linear infinite;
            transform-origin: center bottom;
        }
        
        @keyframes wave {
            0% { transform: rotate(0deg); }
            25% { transform: rotate(5deg); }
            50% { transform: rotate(0deg); }
            75% { transform: rotate(-5deg); }
            100% { transform: rotate(0deg); }
        }
        
        .news-ticker {
            overflow: hidden;
            white-space: nowrap;
            position: relative;
            padding: 10px 0;
        }
        
        .news-ticker-content {
            display: inline-block;
            animation: ticker 30s linear infinite;
        }
        
        @keyframes ticker {
            0% { transform: translateX(100%); }
            100% { transform: translateX(-100%); }
        }
        
        .hover-scale {
            transition: transform 0.3s ease;
        }
        
        .hover-scale:hover {
            transform: scale(1.03);
        }
        
        .glass-effect {
            background: rgba(255, 255, 255, 0.2);
            backdrop-filter: blur(8px);
            -webkit-backdrop-filter: blur(8px);
            border: 1px solid rgba(255, 255, 255, 0.3);
        }
    </style>
</head>
<body class="bg-gray-50 font-sans">
    <!-- Header Section -->
    <header class="bg-white shadow-md">
        <div class="container mx-auto px-4 py-3 flex justify-between items-center">
            <div class="flex items-center space-x-4">
                <img src="https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/367f6167bd314f2c8d0669fa92a2857c~tplv-a9rns2rl98-image.image?lk3s=8e244e95&amp;rcl=20260117141629AA7658D6934F9935D0B3&amp;rrcfp=e75484ac&amp;x-expires=1769235389&amp;x-signature=E88LeWnDyitYKweKVNaQA9Nz33U%3D" alt="UMWTV Logo" class="h-12">
                <div class="hidden md:block">
                    <h1 class="text-xl font-bold text-gray-800">UMWTV South Africa</h1>
                    <p class="text-sm text-gray-600">Official Government Partnership</p>
                </div>
            </div>
            <div class="flex items-center space-x-4">
                <img src="https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/24244bc17b4c4d1e9a6ca5914d2a083d~tplv-a9rns2rl98-image.image?lk3s=8e244e95&amp;rcl=20260117174153A43F4DC82431614B2F2B&amp;rrcfp=e75484ac&amp;x-expires=1769247715&amp;x-signature=AfVt6ewccBqDiZbchlgs3HfLheY%3D" alt="South African Flag" class="h-10 flag-animation">
                <div class="relative">
                    <button id="language-toggle" class="flex items-center space-x-1 bg-gray-100 px-3 py-1 rounded-full text-sm">
                        <span>English</span>
                        <i class="fas fa-chevron-down text-xs"></i>
                    </button>
                    <div id="language-dropdown" class="absolute right-0 mt-2 w-32 bg-white rounded-md shadow-lg hidden z-10">
                        <ul>
                            <li><a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">English</a></li>
                            <li><a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Afrikaans</a></li>
                            <li><a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100"> isiZulu</a></li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </header>

    <!-- Breaking News Ticker -->
    <div class="bg-red-600 text-white">
        <div class="container mx-auto px-4">
            <div class="news-ticker">
                <div class="news-ticker-content">
                    <span class="font-bold mr-4">BREAKING NEWS:</span>
                    UMWTV receives official certification from South African Government on January 7, 2026 | 
                    Construction of new Cape Town headquarters to be completed by May 2026 | 
                    UMWTV partners with local businesses to boost South African economy | 
                    Government officials praise UMWTV's contribution to digital infrastructure development
                </div>
            </div>
        </div>
    </div>

    <!-- Hero Section -->
    <section class="relative bg-cover bg-center" style="background-image: url('https://p3-doubao-search-sign.byteimg.com/tos-cn-i-be4g95zd3a/1501627107655155727~tplv-be4g95zd3a-image.jpeg?lk3s=feb11e32&amp;x-expires=1784181520&amp;x-signature=2ljiSZmpEhd5MWGXlv0vVytPok8%3D');">
        <div class="absolute inset-0 bg-gradient-to-r from-blue-900/80 to-transparent"></div>
        <div class="container mx-auto px-4 py-20 md:py-32 relative z-10">
            <div class="max-w-2xl text-white">
                <h1 class="text-3xl md:text-5xl font-bold mb-4 animate-fade-in">UMWTV &amp; South African Government Partnership</h1>
                <p class="text-lg md:text-xl mb-8 animate-fade-in" style="animation-delay: 0.2s;">Boosting South African economic growth by enabling online work and order fulfillment via video.
</p>
                <div class="flex flex-wrap gap-4 animate-fade-in" style="animation-delay: 0.4s;">
                    <a href="#about" class="bg-white text-blue-800 hover:bg-blue-100 px-6 py-3 rounded-full font-medium transition duration-300">Learn More</a>
                    <a href="#timeline" class="bg-transparent border-2 border-white text-white hover:bg-white/10 px-6 py-3 rounded-full font-medium transition duration-300">View Timeline</a>
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-16 bg-white">
        <div class="container mx-auto px-4">
            <div class="text-center mb-12">
                <h2 class="text-3xl font-bold text-gray-800 mb-4">About Our Partnership</h2>
                <div class="w-24 h-1 bg-blue-600 mx-auto"></div>
            </div>
            
            <div class="grid md:grid-cols-2 gap-12 items-center">
                <div class="hover-scale">
                    <img src="https://p11-doubao-search-sign.byteimg.com/tos-cn-i-be4g95zd3a/918651663094382685~tplv-be4g95zd3a-image.jpeg?lk3s=feb11e32&amp;x-expires=1784181521&amp;x-signature=vHhygZTPAsEV9GBeUXAeX7PeZDA%3D" alt="South African Parliament" class="rounded-lg shadow-lg w-full h-auto">
                </div>
                <div>
                    <h3 class="text-2xl font-bold text-gray-800 mb-4">UMWTV's Strategic Partnership with South Africa: Creating Online Jobs and Improving People's Livelihoods
</h3>
                    <p class="text-gray-700 mb-6">UMWTV is proud to announce the official launch of its partnership with the South African Government, a significant milestone in our global development strategy. This collaboration aims to improve the quality of life for all South Africans and directly address unemployment by creating numerous online jobs. Local residents can earn a stable daily income by watching videos on the UMWTV platform. At the same time, the project will also increase the viewership of film and television companies—achieving a win-win situation, thereby boosting economic activity and improving the living standards of people across the country.
</p>
                    <p class="text-gray-700 mb-6">Since our initial market entry in 2024, UMWTV has worked closely with government officials to understand the unique needs of the South African market and develop tailored solutions that align with national development priorities.</p>
                    <div class="flex items-center space-x-4">
                        <div class="flex -space-x-2">
                            <img src="https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/529452db461b476cb482cfcbb1a77da0~tplv-a9rns2rl98-image.image?lk3s=8e244e95&amp;rcl=2026011717413554D93885C7658764709E&amp;rrcfp=e75484ac&amp;x-expires=1769247696&amp;x-signature=OnbN%2F20reg6oW6Wnbe7yYElqDac%3D" alt="South African Flag" class="h-8 w-8 rounded-full border-2 border-white">
                            <img src="https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/daee0b9e657949ee911bf258420806ac~tplv-a9rns2rl98-image.image?lk3s=8e244e95&amp;rcl=20260117141639BD313AEBE16CD84D729A&amp;rrcfp=e75484ac&amp;x-expires=1769235400&amp;x-signature=3qKPKVRyPNOCQZgoa8A7Ed6sT44%3D" alt="UMWTV Logo" class="h-8 w-8 rounded-full border-2 border-white">
                        </div>
                        <span class="text-gray-600">Official Partnership since January 2025</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Certification Section -->
    <section class="py-16 bg-gray-50">
        <div class="container mx-auto px-4">
            <div class="text-center mb-12">
                <h2 class="text-3xl font-bold text-gray-800 mb-4">Official Certification</h2>
                <div class="w-24 h-1 bg-blue-600 mx-auto"></div>
                <p class="text-gray-600 mt-4 max-w-2xl mx-auto">On January 7, 2026, UMWTV received formal certification and approval from the South African government to build its headquarters in Cape Town, demonstrating our commitment to service and compliance with local regulations.
</p>
            </div>
            
            <div class="max-w-4xl mx-auto bg-white rounded-xl shadow-lg overflow-hidden hover-scale">
                <div class="bg-blue-700 py-4 px-6">
                    <h3 class="text-xl font-bold text-white">CERTIFICATE OF APPROVAL</h3>
                </div>
                <div class="p-8">
                    <div class="flex justify-between items-start mb-8">
                        <div>
                            <h4 class="text-lg font-bold text-gray-800">Government of South Africa</h4>
                            <p class="text-gray-600">Department of Communications and Digital Technologies</p>
                        </div>
                        <img src="https://p9-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/539404690e3946aa8d275f04baa7d31d~tplv-a9rns2rl98-image.image?lk3s=8e244e95&amp;rcl=202601171635429C46BC42B7084A5D52E2&amp;rrcfp=e75484ac&amp;x-expires=1769243744&amp;x-signature=qOY49EKzbnn19SmFCJHVZG15v%2BQ%3D" alt="South African Flag" class="h-16">
                    </div>
                    
                    <div class="border-t border-b border-gray-200 py-6 mb-6">
                        <p class="text-center text-gray-800 mb-4">This is to certify that</p>
                        <p class="text-center text-2xl font-bold text-blue-700 mb-4">UMWTV</p>
                        <p class="text-center text-gray-800">has been officially approved and certified to operate in the Republic of South Africa</p>
                        <p class="text-center text-gray-600 mt-2">Date of Certification: January 7, 2026</p>
                    </div>
                    
                    <div class="flex justify-between items-center">
                        <div>
                            <p class="text-gray-600">Certificate Number: SA-DCDT-2026-001</p>
                            <p class="text-gray-600">Valid Until: January 7, 2031</p>
                        </div>
                        <div class="text-right">
                            <p class="font-bold text-gray-800">Thabo Masebe</p>
                            <p class="text-gray-600">Director-General</p>
                            <p class="text-gray-600">Department of Communications and Digital Technologies</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Timeline Section -->
    <section id="timeline" class="py-16 bg-white">
        <div class="container mx-auto px-4">
            <div class="text-center mb-12">
                <h2 class="text-3xl font-bold text-gray-800 mb-4">Our Journey in South Africa</h2>
                <div class="w-24 h-1 bg-blue-600 mx-auto"></div>
            </div>
            
            <div class="max-w-3xl mx-auto">
                <div class="timeline-item animate-fade-in" style="animation-delay: 0.1s;">
                    <div class="bg-blue-50 p-6 rounded-lg shadow-sm">
                        <span class="inline-block bg-blue-600 text-white text-sm px-3 py-1 rounded-full mb-3">2024</span>
                        <h3 class="text-xl font-bold text-gray-800 mb-2">Market Entry &amp; Exploration</h3>
                        <p class="text-gray-700">UMWTV has begun trial operations in South Africa, conducting market research and establishing initial partnerships with local businesses and government agencies.
</p>
                    </div>
                </div>
                
                <div class="timeline-item animate-fade-in" style="animation-delay: 0.2s;">
                    <div class="bg-blue-50 p-6 rounded-lg shadow-sm">
                        <span class="inline-block bg-blue-600 text-white text-sm px-3 py-1 rounded-full mb-3">January 2025</span>
                        <h3 class="text-xl font-bold text-gray-800 mb-2">Official Launch</h3>
                        <p class="text-gray-700">UMWTV officially launched its operations in South Africa in January 2025. With the support of the South African government, UMWTV is recruiting a large number of online employees nationwide to watch videos, fulfill film and television company orders, and promote South Africa's economic development.
</p>
                    </div>
                </div>
                
                <div class="timeline-item animate-fade-in" style="animation-delay: 0.3s;">
                    <div class="bg-blue-50 p-6 rounded-lg shadow-sm">
                        <span class="inline-block bg-blue-600 text-white text-sm px-3 py-1 rounded-full mb-3">March 2025</span>
                        <h3 class="text-xl font-bold text-gray-800 mb-2">Government Certification</h3>
                        <p class="text-gray-700">UMWTV has received official certification and support from the South African government, reflecting the company's contribution to South Africa's economic growth.
</p>
                    </div>
                </div>
                
                <div class="timeline-item animate-fade-in" style="animation-delay: 0.4s;">
                    <div class="bg-blue-50 p-6 rounded-lg shadow-sm">
                        <span class="inline-block bg-blue-600 text-white text-sm px-3 py-1 rounded-full mb-3">May 2026</span>
                        <h3 class="text-xl font-bold text-gray-800 mb-2">Cape Town Headquarters Planning and Construction
</h3>
                        <p class="text-gray-700">UMWTV has begun planning and construction on its modern headquarters building in Cape Town, which will serve as the regional hub for the company's business operations in Southern Africa. Full completion is expected in May.
</p>
                    </div>
                </div>
                
                <div class="timeline-item animate-fade-in" style="animation-delay: 0.5s;">
                    <div class="bg-blue-50 p-6 rounded-lg shadow-sm">
                        <span class="inline-block bg-green-600 text-white text-sm px-3 py-1 rounded-full mb-3">Future Plans</span>
                        <h3 class="text-xl font-bold text-gray-800 mb-2">Expansion &amp; Innovation</h3>
                        <p class="text-gray-700">UMWTV plans to expand its operations in South Africa, invest in local talent development, foster innovation through research collaborations with universities, and launch more work initiatives.
</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Building Project Section -->
    <section class="py-16 bg-gray-900 text-white">
        <div class="container mx-auto px-4">
            <div class="text-center mb-12">
                <h2 class="text-3xl font-bold mb-4">UMWTV headquarters in Cape Town (preview image)
</h2>
                <div class="w-24 h-1 bg-blue-500 mx-auto"></div>
                <p class="mt-4 max-w-2xl mx-auto">Our state-of-the-art building in Cape Town is scheduled for completion in May 2026, designed to serve as a hub for innovation and collaboration.</p>
            </div>
            
            <div class="grid md:grid-cols-2 gap-12 items-center">
                <div>
                    <h3 class="text-2xl font-bold mb-4">A Vision for Sustainable Architecture</h3>
                    <p class="mb-6">Our new headquarters in Cape Town is more than just an office building – it's a symbol of our commitment to South Africa's future. Designed with sustainability in mind, the building features energy-efficient systems, green spaces, and cutting-edge technology infrastructure.</p>
                    
                    <div class="space-y-4 mb-8">
                        <div class="flex items-start">
                            <div class="bg-blue-600 p-2 rounded-full mr-4">
                                <i class="fas fa-building text-white"></i>
                            </div>
                            <div>
                                <h4 class="font-bold">25,000 Square Meters</h4>
                                <p class="text-gray-300">Modern office space with flexible work areas</p>
                            </div>
                        </div>
                        
                        <div class="flex items-start">
                            <div class="bg-blue-600 p-2 rounded-full mr-4">
                                <i class="fas fa-leaf text-white"></i>
                            </div>
                            <div>
                                <h4 class="font-bold">Green Building Certification</h4>
                                <p class="text-gray-300">LEED Platinum certified with sustainable design features</p>
                            </div>
                        </div>
                        
                        <div class="flex items-start">
                            <div class="bg-blue-600 p-2 rounded-full mr-4">
                                <i class="fas fa-users text-white"></i>
                            </div>
                            <div>
                                <h4 class="font-bold">UMWTV South Africa Headquarters
</h4>
                                <p class="text-gray-300">In the future, it will create more than 500 office jobs across South Africa and employ more than 11,000 long-term South African headquarters staff.
</p>
                            </div>
                        </div>
                    </div>
                    
                    <div class="flex space-x-4">
                        <button id="view-gallery-btn" class="bg-blue-600 hover:bg-blue-700 px-6 py-3 rounded-lg font-medium transition duration-300">
                            View Gallery
                        </button>
                    </div>
                </div>
                
                <div class="hover-scale">
                    <img src="https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/super_tool/10ec920a5ceb4b3794d2cf128ac8df1e~tplv-a9rns2rl98-image.image?lk3s=8e244e95&amp;rcl=20260117135828595FB4D684C8EB4E24E1&amp;rrcfp=f06b921b&amp;x-expires=1771221539&amp;x-signature=811%2FxiiVlvew6vaPVF7IDmH8mqs%3D" alt="UMWTV Cape Town Headquarters" class="rounded-lg shadow-lg w-full h-auto">
                </div>
            </div>
            
        </div>
    </section>

    <!-- Benefits Section -->
    <section class="py-16 bg-white">
        <div class="container mx-auto px-4">
            <div class="text-center mb-12">
                <h2 class="text-3xl font-bold text-gray-800 mb-4">Benefits to South Africa</h2>
                <div class="w-24 h-1 bg-blue-600 mx-auto"></div>
            </div>
            
            <div class="grid md:grid-cols-3 gap-8">
                <div class="bg-blue-50 p-8 rounded-xl shadow-sm hover-scale">
                    <div class="bg-blue-600 text-white w-16 h-16 rounded-full flex items-center justify-center mb-6">
                        <i class="fas fa-chart-line text-2xl"></i>
                    </div>
                    <h3 class="text-xl font-bold text-gray-800 mb-4">Economic Growth</h3>
                    <p class="text-gray-700">UMWTV's investment in South Africa will contribute to GDP growth, create new job opportunities, and stimulate local businesses through strategic partnerships and supply chain development.</p>
                </div>
                
                <div class="bg-blue-50 p-8 rounded-xl shadow-sm hover-scale">
                    <div class="bg-blue-600 text-white w-16 h-16 rounded-full flex items-center justify-center mb-6">
                        <i class="fas fa-laptop-code text-2xl"></i>
                    </div>
                    <h3 class="text-xl font-bold text-gray-800 mb-4">Improve life
</h3>
                    <p class="text-gray-700">UMWTV’s video-watching side hustle has become a reliable financial lifeline for countless South Africans. By earning daily income through our platform, they are regaining economic security and making tangible improvements to their daily lives.
</p>
                </div>
                
                <div class="bg-blue-50 p-8 rounded-xl shadow-sm hover-scale">
                    <div class="bg-blue-600 text-white w-16 h-16 rounded-full flex items-center justify-center mb-6">
                        <i class="fas fa-graduation-cap text-2xl"></i>
                    </div>
                    <h3 class="text-xl font-bold text-gray-800 mb-4">Training new members
</h3>
                    <p class="text-gray-700">UMWTV is committed to nurturing local talent through tailored training programs, hands-on internships, and strategic collaborations with educational institutions—driving higher employment rates and fueling economic growth across South Africa.
</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Testimonials Section -->
    <section class="py-16 bg-gray-50">
        <div class="container mx-auto px-4">
            <div class="text-center mb-12">
                <h2 class="text-3xl font-bold text-gray-800 mb-4">Government &amp; Partner Testimonials</h2>
                <div class="w-24 h-1 bg-blue-600 mx-auto"></div>
            </div>
            
            <div class="grid md:grid-cols-2 gap-8">
                <div class="bg-white p-8 rounded-xl shadow-sm hover-scale">
                    <div class="flex items-center mb-6">
                        <div class="bg-blue-100 p-3 rounded-full mr-4">
                            <i class="fas fa-user-tie text-blue-600 text-xl"></i>
                        </div>
                        <div>
                            <h4 class="font-bold text-gray-800">The Honourable Khumbudzo Ntshavheni</h4>
                            <p class="text-gray-600">Minister of Communications and Digital Technologies</p>
                        </div>
                    </div>
                    <blockquote class="text-gray-700 italic mb-4">
                        “UMWTV’s investment in South Africa will greatly boost our digital economy. Their commitment to infrastructure development and creating more online jobs aligns perfectly with our national priorities. We look forward to building a long-term and fruitful partnership with them.”                 </blockquote>
                    <div class="flex">
                        <i class="fas fa-star text-yellow-400"></i>
                        <i class="fas fa-star text-yellow-400"></i>
                        <i class="fas fa-star text-yellow-400"></i>
                        <i class="fas fa-star text-yellow-400"></i>
                        <i class="fas fa-star text-yellow-400"></i>
                    </div>
                </div>
                
                <div class="bg-white p-8 rounded-xl shadow-sm hover-scale">
                    <div class="flex items-center mb-6">
                        <div class="bg-blue-100 p-3 rounded-full mr-4">
                            <i class="fas fa-building text-blue-600 text-xl"></i>
                        </div>
                        <div>
                            <h4 class="font-bold text-gray-800">Sipho Pityana</h4>
                            <p class="text-gray-600">CEO, Business Unity South Africa</p>
                        </div>
                    </div>
                    <blockquote class="text-gray-700 italic mb-4">
                        “UMWTV’s partnership with the South African government demonstrates the powerful force of public-private partnerships in driving economic growth. UMWTV’s approach to localization and online work development sets a positive example for other multinational companies.”
                    </blockquote>
                    <div class="flex">
                        <i class="fas fa-star text-yellow-400"></i>
                        <i class="fas fa-star text-yellow-400"></i>
                        <i class="fas fa-star text-yellow-400"></i>
                        <i class="fas fa-star text-yellow-400"></i>
                        <i class="fas fa-star text-yellow-400"></i>
                    </div>
                </div>
            </div>
        </div>
    </section>



    <!-- Footer -->
    <footer class="bg-gray-900 text-white py-12">
        <div class="container mx-auto px-4">
            <div class="grid md:grid-cols-4 gap-8">
                <div>
                    <img src="https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/0d1bf3231cad492a840866c0a5adb74b~tplv-a9rns2rl98-image.image?lk3s=8e244e95&amp;rcl=20260117141650202599AE48DD694F734A&amp;rrcfp=e75484ac&amp;x-expires=1769235410&amp;x-signature=54xJ6VUCvvZLDSWUd1Vu%2FLoAVrk%3D" alt="UMWTV Logo" class="h-12 mb-4">
                    <p class="text-gray-400 mb-4">UMWTV, a global leader in online part-time jobs, is committed to driving innovation and economic growth in South Africa.
</p>
                    <div class="flex space-x-4">
                        <a href="#" class="text-gray-400 hover:text-white transition duration-300">
                            <i class="fab fa-twitter"></i>
                        </a>
                        <a href="#" class="text-gray-400 hover:text-white transition duration-300">
                            <i class="fab fa-linkedin"></i>
                        </a>
                        <a href="#" class="text-gray-400 hover:text-white transition duration-300">
                            <i class="fab fa-facebook"></i>
                        </a>
                        <a href="#" class="text-gray-400 hover:text-white transition duration-300">
                            <i class="fab fa-instagram"></i>
                        </a>
                    </div>
                </div>
                
                <div>
                    <h4 class="text-lg font-bold mb-4">Quick Links</h4>
                    <ul class="space-y-2">
                        <li><a href="#about" class="text-gray-400 hover:text-white transition duration-300">About Us</a></li>
                        <li><a href="#timeline" class="text-gray-400 hover:text-white transition duration-300">Our Journey</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition duration-300">Services</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition duration-300">News &amp; Updates</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition duration-300">Careers</a></li>
                    </ul>
                </div>
                
                <div>
                    <h4 class="text-lg font-bold mb-4">
</h4>
                    <ul class="space-y-2">
                        <li><a href="#" class="text-gray-400 hover:text-white transition duration-300"></a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition duration-300"></a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition duration-300"></a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition duration-300"></a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white transition duration-300"></a></li>
                    </ul>
                </div>
                
                <div>
                    <h4 class="text-lg font-bold mb-4">Subscribe to Updates</h4>
                    <p class="text-gray-400 mb-4">Stay informed about UMWTV's activities in South Africa</p>
                    <form class="flex">
                        <input type="email" placeholder="Your email address" class="px-4 py-2 rounded-l-lg focus:outline-none flex-1">
                        <button type="submit" class="bg-blue-600 hover:bg-blue-700 px-4 py-2 rounded-r-lg transition duration-300">
                            <i class="fas fa-paper-plane"></i>
                        </button>
                    </form>
                </div>
            </div>
            
            <div class="border-t border-gray-800 mt-12 pt-8 flex flex-col md:flex-row justify-between items-center">
                <p class="text-gray-400 text-sm mb-4 md:mb-0">© 2026 UMWTV. All rights reserved.</p>
                <div class="flex space-x-6">
                    <a href="#" class="text-gray-400 hover:text-white text-sm transition duration-300">Privacy Policy</a>
                    <a href="#" class="text-gray-400 hover:text-white text-sm transition duration-300">Terms of Service</a>
                    <a href="#" class="text-gray-400 hover:text-white text-sm transition duration-300">Cookie Policy</a>
                </div>
            </div>
        </div>
    </footer>

    <!-- Back to Top Button -->
    <button id="back-to-top" class="fixed bottom-8 right-8 bg-blue-600 text-white w-12 h-12 rounded-full flex items-center justify-center shadow-lg opacity-0 invisible transition-all duration-300">
        <i class="fas fa-arrow-up"></i>
    </button>

    <!-- Modal for Gallery -->
    <div id="gallery-modal" class="fixed inset-0 bg-black/80 z-50 flex items-center justify-center hidden">
        <div class="bg-white rounded-lg max-w-4xl w-full max-h-[90vh] overflow-y-auto">
            <div class="p-6">
                <div class="flex justify-between items-center mb-6">
                    <h3 class="text-2xl font-bold text-gray-800">UMWTV Cape Town Headquarters Gallery</h3>
                    <button id="close-gallery" class="text-gray-500 hover:text-gray-700">
                        <i class="fas fa-times text-xl"></i>
                    </button>
                </div>
                
                <div class="grid grid-cols-2 gap-4">
                    <div class="rounded-lg overflow-hidden">
                        <img src="https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/super_tool/10ec920a5ceb4b3794d2cf128ac8df1e~tplv-a9rns2rl98-image.image?lk3s=8e244e95&amp;rcl=20260117135828595FB4D684C8EB4E24E1&amp;rrcfp=f06b921b&amp;x-expires=1771221539&amp;x-signature=811%2FxiiVlvew6vaPVF7IDmH8mqs%3D" alt="Building Exterior" class="w-full h-48 object-cover">
                        <p class="p-2 text-sm text-gray-600">Building Exterior</p>
                    </div>
                    <div class="rounded-lg overflow-hidden">
                        <img src="https://p3-doubao-search-sign.byteimg.com/tos-cn-i-be4g95zd3a/1501627107655155727~tplv-be4g95zd3a-image.jpeg?lk3s=feb11e32&amp;x-expires=1784181520&amp;x-signature=2ljiSZmpEhd5MWGXlv0vVytPok8%3D" alt="Cape Town Skyline" class="w-full h-48 object-cover">
                        <p class="p-2 text-sm text-gray-600">Cape Town Skyline</p>
                    </div>
                    <div class="rounded-lg overflow-hidden">
                        <img src="https://p3-doubao-search-sign.byteimg.com/tos-cn-i-be4g95zd3a/1501626540727861262~tplv-be4g95zd3a-image.jpeg?lk3s=feb11e32&amp;x-expires=1784181520&amp;x-signature=05aaD8aiiwnAU2F7y%2B3klj5UZFs%3D" alt="Harbor View" class="w-full h-48 object-cover">
                        <p class="p-2 text-sm text-gray-600">Harbor View</p>
                    </div>
                    <div class="rounded-lg overflow-hidden">
                        <img src="https://p11-doubao-search-sign.byteimg.com/labis/64cecf4622255fdb5cced9047aec6e48~tplv-be4g95zd3a-image.jpeg?lk3s=feb11e32&amp;x-expires=1784181520&amp;x-signature=nYc%2Blcn%2Fjg9VYzZQ29C9DWCWSdg%3D" alt="Coastal View" class="w-full h-48 object-cover">
                        <p class="p-2 text-sm text-gray-600">Coastal View</p>
                    </div>
                </div>
                
                <div class="mt-6 text-center">
                    <button id="close-gallery-btn" class="bg-blue-600 hover:bg-blue-700 text-white px-6 py-2 rounded-lg transition duration-300">
                        Close Gallery
                    </button>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Language dropdown toggle
        document.getElementById('language-toggle').addEventListener('click', function() {
            const dropdown = document.getElementById('language-dropdown');
            dropdown.classList.toggle('hidden');
        });
        
        // Close dropdown when clicking outside
        document.addEventListener('click', function(event) {
            const dropdown = document.getElementById('language-dropdown');
            const toggle = document.getElementById('language-toggle');
            
            if (!dropdown.contains(event.target) && !toggle.contains(event.target)) {
                dropdown.classList.add('hidden');
            }
        });
        
        // Back to top button
        const backToTopButton = document.getElementById('back-to-top');
        
        window.addEventListener('scroll', function() {
            if (window.pageYOffset > 300) {
                backToTopButton.classList.remove('opacity-0', 'invisible');
                backToTopButton.classList.add('opacity-100', 'visible');
            } else {
                backToTopButton.classList.remove('opacity-100', 'visible');
                backToTopButton.classList.add('opacity-0', 'invisible');
            }
        });
        
        backToTopButton.addEventListener('click', function() {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        });
        
        
        
        // Gallery Modal
        document.getElementById('view-gallery-btn').addEventListener('click', function() {
            document.getElementById('gallery-modal').classList.remove('hidden');
        });
        
        document.getElementById('close-gallery').addEventListener('click', function() {
            document.getElementById('gallery-modal').classList.add('hidden');
        });
        
        document.getElementById('close-gallery-btn').addEventListener('click', function() {
            document.getElementById('gallery-modal').classList.add('hidden');
        });
        
        // Initialize Three.js model
        
        // Intersection Observer for animations
        document.addEventListener('DOMContentLoaded', function() {
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.style.opacity = 1;
                        entry.target.style.transform = 'translateY(0)';
                    }
                });
            }, { threshold: 0.1 });
            
            document.querySelectorAll('.timeline-item').forEach(item => {
                item.style.opacity = 0;
                item.style.transform = 'translateY(20px)';
                item.style.transition = 'opacity 0.5s ease, transform 0.5s ease';
                observer.observe(item);
            });
        });
    </script>

</body></html>
