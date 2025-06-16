<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Orange Chemist - Build Your Personalized Skincare Routine</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --orange: #F56A0A;
            --green: #00A859;
            --beige: #FDE6C2;
            --soft-black: #222222;
            --white: #ffffff;
            --light-gray: #f8f9fa;
            --shadow: 0 4px 20px rgba(0,0,0,0.1);
            --border-radius: 12px;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, var(--beige) 0%, #fff8ef 100%);
            color: var(--soft-black);
            line-height: 1.6;
            overflow-x: hidden;
        }

        .container {
            max-width: 100%;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            position: relative;
            background: linear-gradient(135deg, var(--beige) 0%, #fff 100%);
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><circle cx="20" cy="20" r="2" fill="%23F56A0A" opacity="0.1"/><circle cx="80" cy="40" r="1.5" fill="%2300A859" opacity="0.1"/><circle cx="60" cy="80" r="1" fill="%23F56A0A" opacity="0.1"/></svg>') repeat;
            animation: float 20s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
        }

        .hero-content {
            position: relative;
            z-index: 2;
            max-width: 400px;
            margin: 0 auto;
        }

        .hero h1 {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 1rem;
            background: linear-gradient(135deg, var(--orange), var(--green));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: slideInUp 0.8s ease-out;
        }

        .hero p {
            font-size: 1.1rem;
            margin-bottom: 2rem;
            color: var(--soft-black);
            opacity: 0.8;
            animation: slideInUp 0.8s ease-out 0.2s both;
        }

        @keyframes slideInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .cta-button {
            background: linear-gradient(135deg, var(--orange), #ff7a1a);
            color: white;
            padding: 15px 40px;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
            animation: slideInUp 0.8s ease-out 0.4s both;
        }

        .cta-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(245, 106, 10, 0.3);
        }

        /* Routine Builder Section */
        .routine-builder {
            padding: 60px 0;
            background: white;
        }

        .section-title {
            text-align: center;
            font-size: 2rem;
            font-weight: 600;
            margin-bottom: 3rem;
            color: var(--soft-black);
        }

        .step {
            margin-bottom: 3rem;
            opacity: 0;
            transform: translateY(20px);
            transition: all 0.5s ease;
        }

        .step.active {
            opacity: 1;
            transform: translateY(0);
        }

        .step h3 {
            font-size: 1.3rem;
            margin-bottom: 1.5rem;
            color: var(--green);
            font-weight: 600;
        }

        .options-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 12px;
            margin-bottom: 2rem;
        }

        .option-card {
            background: white;
            border: 2px solid #e9ecef;
            border-radius: var(--border-radius);
            padding: 15px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .option-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.4), transparent);
            transition: left 0.5s;
        }

        .option-card:hover::before {
            left: 100%;
        }

        .option-card:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow);
        }

        .option-card.selected {
            border-color: var(--orange);
            background: linear-gradient(135deg, var(--orange), #ff7a1a);
            color: white;
            transform: scale(1.05);
        }

        .option-card.selected-concern {
            border-color: var(--green);
            background: linear-gradient(135deg, var(--green), #00c466);
            color: white;
        }

        /* Routine Display */
        .routine-display {
            display: none;
            margin-top: 3rem;
        }

        .routine-display.show {
            display: block;
            animation: fadeInUp 0.5s ease-out;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .routine-section {
            background: var(--light-gray);
            border-radius: var(--border-radius);
            padding: 20px;
            margin-bottom: 20px;
        }

        .routine-section h4 {
            color: var(--orange);
            font-size: 1.2rem;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .product-card {
            background: white;
            border-radius: var(--border-radius);
            padding: 15px;
            margin-bottom: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            transition: transform 0.2s ease;
        }

        .product-card:hover {
            transform: translateX(5px);
        }

        .product-info h5 {
            font-size: 0.9rem;
            font-weight: 600;
            margin-bottom: 4px;
        }

        .product-info p {
            font-size: 0.8rem;
            color: #666;
            margin-bottom: 4px;
        }

        .product-price {
            font-weight: 600;
            color: var(--green);
        }

        .whatsapp-btn {
            background: #25D366;
            color: white;
            border: none;
            border-radius: 20px;
            padding: 8px 16px;
            font-size: 0.8rem;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        .whatsapp-btn:hover {
            background: #128C7E;
            transform: scale(1.05);
        }

        /* WhatsApp Integration */
        .whatsapp-section {
            background: linear-gradient(135deg, #25D366, #128C7E);
            color: white;
            padding: 40px 0;
            text-align: center;
        }

        .whatsapp-section h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
        }

        .whatsapp-section p {
            margin-bottom: 2rem;
            opacity: 0.9;
        }

        .whatsapp-order-btn {
            background: white;
            color: #25D366;
            padding: 15px 30px;
            border: none;
            border-radius: 50px;
            font-weight: 600;
            cursor: pointer;
            margin: 10px;
            transition: all 0.3s ease;
        }

        .whatsapp-order-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(255,255,255,0.3);
        }

        /* Why Orange Chemist */
        .why-section {
            padding: 60px 0;
            text-align: center;
        }

        .why-content {
            max-width: 600px;
            margin: 0 auto;
        }

        .why-section h3 {
            font-size: 1.8rem;
            margin-bottom: 1rem;
            color: var(--orange);
        }

        .why-section p {
            font-size: 1.1rem;
            margin-bottom: 2rem;
            color: var(--soft-black);
        }

        .badges {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 20px;
            margin-top: 2rem;
        }

        .badge {
            background: white;
            padding: 15px 20px;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            display: flex;
            align-items: center;
            gap: 8px;
            transition: transform 0.2s ease;
        }

        .badge:hover {
            transform: translateY(-3px);
        }

        .badge-icon {
            color: var(--green);
            font-size: 1.2rem;
        }

        /* Testimonials */
        .testimonials {
            background: var(--light-gray);
            padding: 60px 0;
        }

        .testimonials h3 {
            text-align: center;
            font-size: 1.8rem;
            margin-bottom: 3rem;
            color: var(--soft-black);
        }

        .testimonial-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            max-width: 1000px;
            margin: 0 auto;
        }

        .testimonial {
            background: white;
            padding: 25px;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            position: relative;
        }

        .testimonial::before {
            content: '"';
            position: absolute;
            top: -10px;
            left: 20px;
            font-size: 4rem;
            color: var(--orange);
            opacity: 0.3;
        }

        .testimonial-text {
            margin-bottom: 15px;
            font-style: italic;
        }

        .stars {
            color: #FFD700;
            margin-bottom: 10px;
        }

        .testimonial-author {
            font-weight: 600;
            color: var(--green);
        }

        /* Footer */
        .footer {
            background: var(--soft-black);
            color: white;
            padding: 40px 0;
            text-align: center;
        }

        .footer-buttons {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 15px;
            margin-bottom: 2rem;
        }

        .footer-btn {
            background: transparent;
            color: white;
            border: 2px solid white;
            padding: 12px 24px;
            border-radius: 25px;
            text-decoration: none;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .footer-btn:hover {
            background: white;
            color: var(--soft-black);
            transform: translateY(-2px);
        }

        .footer-tagline {
            margin-top: 2rem;
            opacity: 0.8;
            font-style: italic;
        }

        /* Mobile Responsiveness */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2rem;
            }
            
            .hero p {
                font-size: 1rem;
            }
            
            .options-grid {
                grid-template-columns: 1fr 1fr;
            }
            
            .product-card {
                flex-direction: column;
                align-items: flex-start;
                gap: 10px;
            }
            
            .testimonial-grid {
                grid-template-columns: 1fr;
            }
            
            .badges {
                flex-direction: column;
                align-items: center;
            }
        }

        /* Animations */
        .pulse {
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
    </style>
</head>
<body>
    <!-- Hero Section -->
    <section class="hero" id="hero">
        <div class="container">
            <div class="hero-content">
                <h1>Build Your Personalized Skincare Routine 🧴</h1>
                <p>Find the right AM & PM products based on your skin type and concerns — available at Orange Chemist.</p>
                <button class="cta-button pulse" onclick="scrollToBuilder()">Start Now</button>
            </div>
        </div>
    </section>

    <!-- Interactive Routine Builder -->
    <section class="routine-builder" id="routine-builder">
        <div class="container">
            <h2 class="section-title">Let's Build Your Perfect Routine ✨</h2>
            
            <!-- Step 1: Skin Type -->
            <div class="step active" id="step1">
                <h3>Step 1: What's your skin type? 🌟</h3>
                <div class="options-grid">
                    <div class="option-card" onclick="selectSkinType('oily')">
                        <div style="font-size: 2rem; margin-bottom: 8px;">💧</div>
                        <div>Oily</div>
                    </div>
                    <div class="option-card" onclick="selectSkinType('dry')">
                        <div style="font-size: 2rem; margin-bottom: 8px;">🏜️</div>
                        <div>Dry</div>
                    </div>
                    <div class="option-card" onclick="selectSkinType('combination')">
                        <div style="font-size: 2rem; margin-bottom: 8px;">🌓</div>
                        <div>Combination</div>
                    </div>
                    <div class="option-card" onclick="selectSkinType('sensitive')">
                        <div style="font-size: 2rem; margin-bottom: 8px;">🌸</div>
                        <div>Sensitive</div>
                    </div>
                    <div class="option-card" onclick="selectSkinType('normal')">
                        <div style="font-size: 2rem; margin-bottom: 8px;">✨</div>
                        <div>Normal</div>
                    </div>
                </div>
            </div>

            <!-- Step 2: Skin Concerns -->
            <div class="step" id="step2">
                <h3>Step 2: Select your skin concerns 🎯</h3>
                <div class="options-grid">
                    <div class="option-card" onclick="toggleConcern('acne')">
                        <div style="font-size: 2rem; margin-bottom: 8px;">🔴</div>
                        <div>Acne</div>
                    </div>
                    <div class="option-card" onclick="toggleConcern('pigmentation')">
                        <div style="font-size: 2rem; margin-bottom: 8px;">🟤</div>
                        <div>Pigmentation</div>
                    </div>
                    <div class="option-card" onclick="toggleConcern('dark-circles')">
                        <div style="font-size: 2rem; margin-bottom: 8px;">👁️</div>
                        <div>Dark Circles</div>
                    </div>
                    <div class="option-card" onclick="toggleConcern('aging')">
                        <div style="font-size: 2rem; margin-bottom: 8px;">⏰</div>
                        <div>Aging</div>
                    </div>
                    <div class="option-card" onclick="toggleConcern('dullness')">
                        <div style="font-size: 2rem; margin-bottom: 8px;">🌫️</div>
                        <div>Dullness</div>
                    </div>
                    <div class="option-card" onclick="toggleConcern('uneven-tone')">
                        <div style="font-size: 2rem; margin-bottom: 8px;">🎨</div>
                        <div>Uneven Tone</div>
                    </div>
                    <div class="option-card" onclick="toggleConcern('sensitivity')">
                        <div style="font-size: 2rem; margin-bottom: 8px;">❤️‍🩹</div>
                        <div>Sensitivity</div>
                    </div>
                    <div class="option-card" onclick="toggleConcern('sun-damage')">
                        <div style="font-size: 2rem; margin-bottom: 8px;">☀️</div>
                        <div>Sun Damage</div>
                    </div>
                </div>
                <button class="cta-button" onclick="generateRoutine()" style="margin-top: 20px;">Generate My Routine</button>
            </div>

            <!-- Routine Display -->
            <div class="routine-display" id="routine-display">
                <h3 style="text-align: center; margin-bottom: 2rem; color: var(--green);">Your Personalized Routine 🌟</h3>
                
                <div class="routine-section">
                    <h4>🌅 Morning Routine</h4>
                    <div id="am-routine"></div>
                </div>

                <div class="routine-section">
                    <h4>🌙 Evening Routine</h4>
                    <div id="pm-routine"></div>
                </div>
            </div>
        </div>
    </section>

    <!-- WhatsApp Integration -->
    <section class="whatsapp-section">
        <div class="container">
            <h3>Ready to Order? 📱</h3>
            <p>Get your personalized routine delivered to your doorstep!</p>
            <button class="whatsapp-order-btn" onclick="orderViaWhatsApp()">
                📱 Order via WhatsApp
            </button>
            <button class="whatsapp-order-btn" onclick="uploadPrescription()">
                📋 Upload Prescription
            </button>
        </div>
    </section>

    <!-- Why Orange Chemist -->
    <section class="why-section">
        <div class="container">
            <div class="why-content">
                <h3>Why Orange Chemist? 🧡</h3>
                <p>"A neighborhood wellness store trusted by thousands in Navi Mumbai. Medicines to skincare, ice creams to baby care — all under one roof."</p>
                
                <div class="badges">
                    <div class="badge">
                        <span class="badge-icon">📍</span>
                        <span>Available in Kharghar</span>
                    </div>
                    <div class="badge">
                        <span class="badge-icon">🚚</span>
                        <span>Free Home Delivery</span>
                    </div>
                    <div class="badge">
                        <span class="badge-icon">🛒</span>
                        <span>10+ Product Categories</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Testimonials -->
    <section class="testimonials">
        <div class="container">
            <h3>What Our Customers Say ⭐</h3>
            <div class="testimonial-grid">
                <div class="testimonial">
                    <div class="stars">⭐⭐⭐⭐⭐</div>
                    <p class="testimonial-text">Got my skincare kit recommended and delivered within 2 hours! Amazing service! 😊</p>
                    <div class="testimonial-author">- Priya M.</div>
                </div>
                <div class="testimonial">
                    <div class="stars">⭐⭐⭐⭐⭐</div>
                    <p class="testimonial-text">Very helpful team and wide variety of brands. They know exactly what works for different skin types!</p>
                    <div class="testimonial-author">- Rajesh K.</div>
                </div>
                <div class="testimonial">
                    <div class="stars">⭐⭐⭐⭐⭐</div>
                    <p class="testimonial-text">My dermatologist sent me here and now I don't go anywhere else. Trusted quality every time! 🙌</p>
                    <div class="testimonial-author">- Anita S.</div>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <div class="container">
            <div class="footer-buttons">
                <a href="https://maps.google.com/?q=Orange+Chemist+Kharghar" class="footer-btn" target="_blank">
                    📍 Store Locator
                </a>
                <a href="tel:+919820796184" class="footer-btn">
                    📞 Call Now
                </a>
                <a href="https://wa.me/919820796184" class="footer-btn" target="_blank">
                    📦 WhatsApp Order
                </a>
            </div>
            <p class="footer-tagline">"Orange Chemist — Kharghar's Trusted Wellness Store. From frozen to first aid." ❄️🏥</p>
        </div>
    </footer>

    <script>
        let selectedSkinType = '';
        let selectedConcerns = [];

        const skinCareProducts = {
            cleanser: {
                oily: { name: 'Salicylic Acid Face Wash', brand: 'The Derma Co', price: '₹399', benefit: 'Controls oil & prevents breakouts' },
                dry: { name: 'Hyaluronic Acid Cleanser', brand: 'Minimalist', price: '₹349', benefit: 'Gentle cleansing with hydration' },
                combination: { name: 'Niacinamide Face Wash', brand: 'Plum', price: '₹325', benefit: 'Balances T-zone, gentle on cheeks' },
                sensitive: { name: 'Gentle Foaming Cleanser', brand: 'Cetaphil', price: '₹599', benefit: 'Soap-free, non-irritating' },
                normal: { name: 'Vitamin C Face Wash', brand: 'Mamaearth', price: '₹299', benefit: 'Brightening daily cleanser' }
            },
            toner: {
                oily: { name: 'Niacinamide Toner', brand: 'The Ordinary', price: '₹590', benefit: 'Minimizes pores & controls oil' },
                dry: { name: 'Hyaluronic Acid Toner', brand: 'Good Vibes', price: '₹245', benefit: 'Deep hydration boost' },
                combination: { name: 'Rose Water Toner', brand: 'Kama Ayurveda', price: '₹395', benefit: 'Balances pH naturally' },
                sensitive: { name: 'Chamomile Toner', brand: 'Himalaya', price: '₹155', benefit: 'Soothes & calms irritation' },
                normal: { name: 'Vitamin C Toner', brand: 'Dot & Key', price: '₹345', benefit: 'Brightens & evens skin tone' }
            },
            moisturizer: {
                oily: { name: 'Oil-Free Moisturizer', brand: 'Neutrogena', price: '₹449', benefit: 'Lightweight, non-comedogenic' },
                dry: { name: 'Intense Repair Cream', brand: 'CeraVe', price: '₹899', benefit: '24hr hydration lock' },
                combination: { name: 'Gel-Cream Moisturizer', brand: 'Clinique', price: '₹2450', benefit: 'Perfect for mixed skin zones' },
                sensitive: { name: 'Daily Face Cream', brand: 'Cetaphil', price: '₹560', benefit: 'Fragrance-free, gentle formula' },
                normal: { name: 'Daily Moisturizer', brand: 'Olay', price: '₹399', benefit: 'Maintains healthy skin barrier' }
            },
            sunscreen: {
                oily: { name: 'Aqua Gel Sunscreen SPF 50', brand: 'Re\'equil', price: '₹490', benefit: 'Matte finish, no white cast' },
                dry: { name: 'Hydrating Sunscreen SPF 30', brand: 'Lakme', price: '₹350', benefit: 'Sun protection + moisture' },
                combination: { name: 'Tinted Sunscreen SPF 40', brand: 'Lotus', price: '₹425', benefit: 'Coverage + protection' },
                sensitive: { name: 'Mineral Sunscreen SPF 50', brand: 'Blue Nectar', price: '₹799', benefit: 'Chemical-free, gentle' },
                normal: { name: 'Daily Sunscreen SPF 30', brand: 'Nivea', price: '₹299', benefit: 'Light, everyday protection' }
            },
            serum: {
                acne: { name: 'Niacinamide 10% Serum', brand: 'The Derma Co', price: '₹599', benefit: 'Reduces acne & oil production' },
                pigmentation: { name: 'Vitamin C Serum', brand: 'Minimalist', price: '₹599', benefit: 'Fades dark spots & brightens' },
                aging: { name: 'Retinol Serum', brand: 'The Ordinary', price: '₹990', benefit: 'Reduces fine lines & wrinkles' },
                dullness: { name: 'Alpha Arbutin Serum', brand: 'Good Vibes', price: '₹349', benefit: 'Instant glow & radiance' },
                'dark-circles': { name: 'Caffeine Eye Serum', brand: 'The Inkey List', price: '₹750', benefit: 'Reduces puffiness & dark circles' },
                'uneven-tone': { name: 'Kojic Acid Serum', brand: 'Be Bodywise', price: '₹449', benefit: 'Evens skin tone naturally' },
                sensitivity: { name: 'Centella Serum', brand: 'COSRX', price: '₹1200', benefit: 'Calms irritation & redness' },
                'sun-damage': { name: 'Arbutin + Kojic Serum', brand: 'Pilgrim', price: '₹495', benefit: 'Repairs sun damage' }
            },
            nightcream: {
                oily: { name: 'Oil Control Night Gel', brand: 'Garnier', price: '₹299', benefit: 'Overnight oil control' },
                dry: { name: 'Rich Night Cream', brand: 'L\'Oreal', price: '₹799', benefit: 'Overnight repair & hydration' },
                combination: { name: 'Multi-Action Night Cream', brand: 'Pond\'s', price: '₹179', benefit: 'Targets multiple concerns' },
                sensitive: { name: 'Gentle Night Moisturizer', brand: 'Aveeno', price: '₹899', benefit: 'Overnight healing' },
                normal: { name: 'Anti-Aging Night Cream', brand: 'Olay', price: '₹649', benefit: 'Prevents signs of aging' }
            }
        };

        function scrollToBuilder() {
            document.getElementById('routine-builder').scrollIntoView({ behavior: 'smooth' });
        }

        function selectSkinType(type) {
            selectedSkinType = type;
            
            // Remove selecte
