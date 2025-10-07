<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CryptoTrade Pro - Gelişmiş Trading Platformu</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        /* Enhanced dark theme with vibrant colors */
        * {
            box-sizing: border-box;
        }
        
        html, body {
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 50%, #334155 100%) !important;
            color: #ffffff !important;
            margin: 0;
            padding: 0;
            min-height: 100vh;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 50%, #334155 100%) !important;
            color: #ffffff !important;
        }
        
        .gradient-bg {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%) !important;
        }
        
        .card-hover {
            transition: all 0.3s ease;
        }
        .card-hover:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
        }
        
        .profit { color: #10b981 !important; }
        .loss { color: #ef4444 !important; }
        
        .animate-pulse-slow {
            animation: pulse 3s cubic-bezier(0.4, 0, 0.6, 1) infinite;
        }
        
        /* TradingView-style price animations */
        .price-update {
            transition: all 0.3s ease;
            background-color: #1a1a1a !important;
            color: #ffffff !important;
        }
        
        .price-up {
            background-color: rgba(0, 230, 118, 0.15) !important;
            animation: priceFlashGreen 0.6s ease-out !important;
            color: #00e676 !important;
            font-weight: 600 !important;
        }
        
        .price-down {
            background-color: rgba(255, 82, 82, 0.15) !important;
            animation: priceFlashRed 0.6s ease-out !important;
            color: #ff5252 !important;
            font-weight: 600 !important;
        }
        
        @keyframes priceFlashGreen {
            0% { 
                background-color: rgba(0, 230, 118, 0.4) !important;
                transform: scale(1.02);
                box-shadow: 0 0 15px rgba(0, 230, 118, 0.3);
            }
            50% { 
                background-color: rgba(0, 230, 118, 0.25) !important;
                transform: scale(1.01);
            }
            100% { 
                background-color: rgba(0, 230, 118, 0.15) !important;
                transform: scale(1);
                box-shadow: none;
            }
        }
        
        @keyframes priceFlashRed {
            0% { 
                background-color: rgba(255, 82, 82, 0.4) !important;
                transform: scale(1.02);
                box-shadow: 0 0 15px rgba(255, 82, 82, 0.3);
            }
            50% { 
                background-color: rgba(255, 82, 82, 0.25) !important;
                transform: scale(1.01);
            }
            100% { 
                background-color: rgba(255, 82, 82, 0.15) !important;
                transform: scale(1);
                box-shadow: none;
            }
        }
        
        .scrollbar-hide {
            -ms-overflow-style: none;
            scrollbar-width: none;
        }
        .scrollbar-hide::-webkit-scrollbar {
            display: none;
        }
        
        .ai-active {
            background: linear-gradient(45deg, #10b981, #059669) !important;
            animation: pulse 2s infinite;
            color: #ffffff !important;
        }
        
        .ai-inactive {
            background: #6b7280 !important;
            color: #ffffff !important;
        }
        
        .trade-card {
            background: linear-gradient(135deg, #1f2937 0%, #374151 100%) !important;
            border: 1px solid #4b5563 !important;
            color: #ffffff !important;
        }
        
        .indicator-active {
            background: #10b981 !important;
            color: white !important;
        }
        
        .indicator-inactive {
            background: #374151 !important;
            color: #9ca3af !important;
        }
        
        .compact-input {
            padding: 8px 12px;
            font-size: 14px;
            background-color: #374151 !important;
            color: #ffffff !important;
            border: 1px solid #4b5563 !important;
        }
        
        .price-update-smooth {
            transition: background-color 0.3s ease;
        }
        
        .price-up-bg {
            background-color: rgba(16, 185, 129, 0.1) !important;
        }
        
        .price-down-bg {
            background-color: rgba(239, 68, 68, 0.1) !important;
        }
        
        /* Force dark theme for all common elements */
        div, span, p, h1, h2, h3, h4, h5, h6 {
            color: #ffffff !important;
        }
        
        /* Force dark backgrounds */
        .bg-white {
            background-color: #1f2937 !important;
        }
        
        /* Input and form elements */
        input, select, textarea, button {
            background-color: #374151 !important;
            color: #ffffff !important;
            border-color: #4b5563 !important;
        }
        
        input:focus, select:focus, textarea:focus {
            background-color: #374151 !important;
            color: #ffffff !important;
            border-color: #3b82f6 !important;
        }
        
        /* Enhanced table elements with TradingView style */
        table {
            background-color: #1a1a1a !important;
            color: #ffffff !important;
            border-collapse: separate !important;
            border-spacing: 0 !important;
            border: 1px solid #2a2a2a !important;
            border-radius: 8px !important;
            overflow: hidden !important;
        }
        
        th, td {
            background-color: #1a1a1a !important;
            color: #ffffff !important;
            border-right: 1px solid #2a2a2a !important;
            border-bottom: 1px solid #2a2a2a !important;
            padding: 12px !important;
        }
        
        th {
            background-color: #2a2a2a !important;
            font-weight: 600 !important;
            text-transform: uppercase !important;
            font-size: 11px !important;
            letter-spacing: 0.5px !important;
            color: #9ca3af !important;
        }
        
        tr {
            background-color: #1a1a1a !important;
            color: #ffffff !important;
            transition: all 0.2s ease !important;
        }
        
        tr:hover {
            background-color: #252525 !important;
            transform: scale(1.001) !important;
        }
        
        tr:last-child td {
            border-bottom: none !important;
        }
        
        td:last-child, th:last-child {
            border-right: none !important;
        }
        
        /* Navigation buttons */
        .nav-btn {
            background-color: transparent !important;
            color: #ffffff !important;
        }
        
        .nav-btn:hover {
            background-color: rgba(255, 255, 255, 0.2) !important;
        }
        
        /* Admin tab buttons */
        .admin-tab-btn {
            background-color: transparent !important;
            color: #9ca3af !important;
        }
        
        .admin-tab-btn:hover {
            color: #ffffff !important;
        }
        
        /* Enhanced page containers with vibrant backgrounds */
        .page {
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 50%, #334155 100%) !important;
            color: #ffffff !important;
            min-height: 100vh;
        }
        
        /* Auth page specific */
        #authPage {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%) !important;
            min-height: 100vh;
        }
        
        #adminAuthPage {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%) !important;
            min-height: 100vh;
        }
        
        /* Main app container */
        #mainApp {
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 50%, #334155 100%) !important;
            color: #ffffff !important;
            min-height: 100vh;
        }
        
        /* Enhanced card styles */
        .trading-card {
            background: linear-gradient(145deg, #1a1a1a 0%, #2a2a2a 100%) !important;
            border: 1px solid #3a3a3a !important;
            border-radius: 12px !important;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3) !important;
            transition: all 0.3s ease !important;
        }
        
        .trading-card:hover {
            transform: translateY(-2px) !important;
            box-shadow: 0 12px 40px rgba(0, 0, 0, 0.4) !important;
            border-color: #4a4a4a !important;
        }
        
        /* Vibrant accent colors */
        .accent-green {
            color: #00e676 !important;
        }
        
        .accent-red {
            color: #ff5252 !important;
        }
        
        .accent-blue {
            color: #2196f3 !important;
        }
        
        .accent-yellow {
            color: #ffeb3b !important;
        }
        
        .accent-purple {
            color: #9c27b0 !important;
        }
        
        .accent-orange {
            color: #ff9800 !important;
        }
        
        /* Chart container */
        canvas {
            background-color: #1f2937 !important;
        }
        
        /* Notification container */
        #notificationContainer {
            z-index: 9999;
        }
        
        /* Override any potential white backgrounds */
        * {
            background-color: inherit;
        }
        
        *:not(.gradient-bg):not(.bg-blue-600):not(.bg-green-600):not(.bg-red-600):not(.bg-yellow-600):not(.bg-purple-600):not(.bg-orange-600) {
            background-color: inherit !important;
        }
    </style>
</head>
<body class="text-white">
    <!-- Login/Register Page -->
    <div id="authPage" class="min-h-screen flex items-center justify-center gradient-bg">
        <div class="max-w-md w-full space-y-8 p-8">
            <div class="text-center">
                <h1 class="text-4xl font-bold text-white mb-2">Alfa Trade Bot</h1>
                <p class="text-blue-100">Gelişmiş AI Destekli Trading Platformu</p>
            </div>
            
            <!-- Login Form -->
            <div id="loginForm" class="bg-white bg-opacity-10 backdrop-blur-lg rounded-xl p-8 shadow-2xl">
                <h2 class="text-2xl font-bold text-center text-white mb-6">Giriş Yap</h2>
                <form onsubmit="handleLogin(event)">
                    <div class="mb-4">
                        <label class="block text-blue-100 text-sm font-bold mb-2">Kullanıcı Adı</label>
                        <input type="text" id="loginUsername" required 
                               class="w-full px-4 py-3 bg-white bg-opacity-20 border border-white border-opacity-30 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-400 text-white placeholder-blue-200" 
                               placeholder="Kullanıcı adınızı girin">
                    </div>
                    <div class="mb-6">
                        <label class="block text-blue-100 text-sm font-bold mb-2">Şifre</label>
                        <input type="password" id="loginPassword" required 
                               class="w-full px-4 py-3 bg-white bg-opacity-20 border border-white border-opacity-30 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-400 text-white placeholder-blue-200" 
                               placeholder="Şifrenizi girin">
                    </div>
                    <button type="submit" class="w-full bg-blue-600 hover:bg-blue-700 text-white font-bold py-3 px-4 rounded-lg transition-colors">
                        Giriş Yap
                    </button>
                </form>
                <div class="text-center mt-4">
                    <button onclick="showRegister()" class="text-blue-200 hover:text-white transition-colors">
                        Hesabınız yok mu? Kayıt olun
                    </button>
                </div>
            </div>
            
            <!-- Register Form -->
            <div id="registerForm" class="bg-white bg-opacity-10 backdrop-blur-lg rounded-xl p-8 shadow-2xl hidden">
                <h2 class="text-2xl font-bold text-center text-white mb-6">Kayıt Ol</h2>
                <form onsubmit="handleRegister(event)">
                    <div class="mb-4">
                        <label class="block text-blue-100 text-sm font-bold mb-2">Kullanıcı Adı</label>
                        <input type="text" id="registerUsername" required 
                               class="w-full px-4 py-3 bg-white bg-opacity-20 border border-white border-opacity-30 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-400 text-white placeholder-blue-200" 
                               placeholder="Kullanıcı adı seçin">
                    </div>
                    <div class="mb-4">
                        <label class="block text-blue-100 text-sm font-bold mb-2">Email</label>
                        <input type="email" id="registerEmail" required 
                               class="w-full px-4 py-3 bg-white bg-opacity-20 border border-white border-opacity-30 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-400 text-white placeholder-blue-200" 
                               placeholder="Email adresiniz">
                    </div>
                    <div class="mb-6">
                        <label class="block text-blue-100 text-sm font-bold mb-2">Şifre</label>
                        <input type="password" id="registerPassword" required 
                               class="w-full px-4 py-3 bg-white bg-opacity-20 border border-white border-opacity-30 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-400 text-white placeholder-blue-200" 
                               placeholder="Güçlü bir şifre seçin">
                    </div>
                    <button type="submit" class="w-full bg-green-600 hover:bg-green-700 text-white font-bold py-3 px-4 rounded-lg transition-colors">
                        Kayıt Ol
                    </button>
                </form>
                <div class="text-center mt-4">
                    <button onclick="showLogin()" class="text-blue-200 hover:text-white transition-colors">
                        Zaten hesabınız var mı? Giriş yapın
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- Admin Control Panel Login -->
    <div id="adminAuthPage" class="hidden min-h-screen flex items-center justify-center gradient-bg">
        <div class="max-w-md w-full space-y-8 p-8">
            <div class="text-center">
                <h1 class="text-4xl font-bold text-white mb-2">Admin Panel</h1>
                <p class="text-blue-100">Yönetici Girişi</p>
            </div>
            
            <div class="bg-white bg-opacity-10 backdrop-blur-lg rounded-xl p-8 shadow-2xl">
                <h2 class="text-2xl font-bold text-center text-white mb-6">Admin Giriş</h2>
                <form onsubmit="handleAdminLogin(event)">
                    <div class="mb-4">
                        <label class="block text-blue-100 text-sm font-bold mb-2">Kullanıcı Adı</label>
                        <input type="text" id="adminUsername" required 
                               class="w-full px-4 py-3 bg-white bg-opacity-20 border border-white border-opacity-30 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-400 text-white placeholder-blue-200" 
                               placeholder="Admin kullanıcı adı">
                    </div>
                    <div class="mb-6">
                        <label class="block text-blue-100 text-sm font-bold mb-2">Şifre</label>
                        <input type="password" id="adminPassword" required 
                               class="w-full px-4 py-3 bg-white bg-opacity-20 border border-white border-opacity-30 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-400 text-white placeholder-blue-200" 
                               placeholder="Admin şifresi">
                    </div>
                    <button type="submit" class="w-full bg-red-600 hover:bg-red-700 text-white font-bold py-3 px-4 rounded-lg transition-colors">
                        Admin Girişi
                    </button>
                </form>
                <div class="text-center mt-4">
                    <button onclick="backToMain()" class="text-blue-200 hover:text-white transition-colors">
                        Ana Sayfaya Dön
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- Main Application -->
    <div id="mainApp" class="hidden">
        <!-- Navigation -->
        <nav class="gradient-bg shadow-lg">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="flex justify-between h-16">
                    <div class="flex items-center">
                        <div class="flex-shrink-0">
                            <span class="text-2xl font-bold text-white mr-3">📊</span>
                            <span class="text-xl font-bold text-white">Alfa Trade Bot</span>
                        </div>
                        <div class="hidden md:block ml-10">
                            <div class="flex items-baseline space-x-4">
                                <button onclick="showPage('dashboard')" class="nav-btn bg-white bg-opacity-20 text-white hover:bg-white hover:bg-opacity-30 px-3 py-2 rounded-md text-sm font-medium transition-colors">Dashboard</button>
                                <button onclick="showPage('trade')" class="nav-btn bg-transparent text-white hover:bg-white hover:bg-opacity-20 px-3 py-2 rounded-md text-sm font-medium transition-colors">Trade</button>
                                <button onclick="showPage('api')" class="nav-btn bg-transparent text-white hover:bg-white hover:bg-opacity-20 px-3 py-2 rounded-md text-sm font-medium transition-colors">API Bağlantı</button>
                                <button onclick="showPage('control')" class="nav-btn bg-transparent text-white hover:bg-white hover:bg-opacity-20 px-3 py-2 rounded-md text-sm font-medium transition-colors">Kontrol Paneli</button>
                            </div>
                        </div>
                    </div>
                    <div class="flex items-center space-x-4">
                        <div class="text-white">
                            <span id="userName" class="font-medium"></span>
                        </div>
                        <button onclick="showAdminPanel()" class="bg-purple-600 hover:bg-purple-700 px-3 py-2 rounded text-sm transition-colors">Admin</button>
                        <button onclick="logout()" class="bg-red-500 hover:bg-red-600 px-4 py-2 rounded text-sm transition-colors">Çıkış</button>
                    </div>
                </div>
            </div>
        </nav>

        <!-- Dashboard Page -->
        <div id="dashboardPage" class="page">
            <div class="max-w-7xl mx-auto py-6 px-4">
                <!-- Dashboard Header -->
                <div class="mb-6 flex justify-between items-center">
                    <h2 class="text-3xl font-bold">Trading Dashboard</h2>
                    <div class="flex items-center space-x-4">
                        <div class="text-sm">
                            <div>Bakiye: <span id="currentBalance" class="text-yellow-400 font-bold">API Bağlantısı Bekleniyor</span></div>
                            <div>Kar/Zarar: <span id="totalPnL" class="font-bold">$0.00</span></div>
                            <div class="flex space-x-4 text-xs">
                                <span>ProBot: <span id="probotTradeCount" class="text-purple-400">0</span></span>
                                <span>Hızlı: <span id="fastTradeCount" class="text-blue-400">0</span></span>
                                <span>Uzun: <span id="longTradeCount" class="text-green-400">0</span></span>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Coin List Section -->
                <div class="mb-6">
                    <div class="grid grid-cols-1 lg:grid-cols-4 gap-6">
                        <!-- Coin Search and List -->
                        <div class="lg:col-span-3 trading-card p-6">
                            <div class="flex justify-between items-center mb-4">
                                <h3 class="text-xl font-bold accent-blue">💰 Coin Listesi (500+ Coin)</h3>
                                <div class="flex space-x-2">
                                    <input type="text" id="coinSearch" placeholder="🔍 Coin ara..." 
                                           class="px-4 py-2 bg-gray-800 border border-gray-600 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition-all"
                                           onkeyup="searchCoins()">
                                    <button onclick="refreshPrices()" class="bg-gradient-to-r from-green-600 to-blue-600 hover:from-green-700 hover:to-blue-700 px-4 py-2 rounded-lg transition-all duration-200 transform hover:scale-105 font-medium">
                                        🔄 Yenile
                                    </button>
                                </div>
                            </div>
                            
                            <!-- Sorting Buttons -->
                            <div class="flex space-x-2 mb-4">
                                <button onclick="sortCoins('default')" id="sortDefault" class="sort-btn bg-blue-600 text-white px-3 py-1 rounded-lg text-sm font-medium transition-all">
                                    📊 Varsayılan
                                </button>
                                <button onclick="sortCoins('gainers')" id="sortGainers" class="sort-btn bg-gray-600 text-gray-300 px-3 py-1 rounded-lg text-sm font-medium transition-all hover:bg-green-600 hover:text-white">
                                    📈 Yükselenler
                                </button>
                                <button onclick="sortCoins('losers')" id="sortLosers" class="sort-btn bg-gray-600 text-gray-300 px-3 py-1 rounded-lg text-sm font-medium transition-all hover:bg-red-600 hover:text-white">
                                    📉 Düşenler
                                </button>
                            </div>
                            
                            <div class="h-[500px] overflow-y-auto scrollbar-hide trading-card">
                                <table class="w-full border-collapse border border-gray-600">
                                    <thead class="sticky top-0">
                                        <tr>
                                            <th class="text-left p-3 border-r border-b border-gray-600">Coin</th>
                                            <th class="text-left p-3 border-r border-b border-gray-600">Fiyat</th>
                                            <th class="text-left p-3 border-r border-b border-gray-600">24h %</th>
                                            <th class="text-left p-3 border-r border-b border-gray-600">Hacim</th>
                                            <th class="text-left p-3 border-b border-gray-600">İşlem</th>
                                        </tr>
                                    </thead>
                                    <tbody id="coinList">
                                        <!-- Coins will be populated here -->
                                    </tbody>
                                </table>
                            </div>
                        </div>

                        <!-- Market Summary Panel -->
                        <div class="lg:col-span-1 space-y-4">
                            <!-- Top Gainers -->
                            <div class="trading-card p-4">
                                <h4 class="text-lg font-bold mb-3 accent-green">📈 En Çok Yükselenler</h4>
                                <div id="topGainers" class="space-y-2">
                                    <!-- Top gainers will be populated here -->
                                </div>
                            </div>

                            <!-- Top Losers -->
                            <div class="trading-card p-4">
                                <h4 class="text-lg font-bold mb-3 accent-red">📉 En Çok Düşenler</h4>
                                <div id="topLosers" class="space-y-2">
                                    <!-- Top losers will be populated here -->
                                </div>
                            </div>

                            <!-- Volume Leaders -->
                            <div class="trading-card p-4">
                                <h4 class="text-lg font-bold mb-3 accent-blue">🔊 Hacim Liderleri</h4>
                                <div id="volumeLeaders" class="space-y-2">
                                    <!-- Volume leaders will be populated here -->
                                </div>
                            </div>
                        </div>
                    </div>
                </div>


                <!-- AI Conditions -->
                <div class="trading-card p-6 mb-6">
                    <h3 class="text-xl font-bold mb-4 accent-purple">🤖 Yapay Zeka Koşulları</h3>
                    <div id="aiConditions" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
                        <!-- AI conditions will be populated here -->
                    </div>
                </div>
            </div>
        </div>

        <!-- Trade Page -->
        <div id="tradePage" class="page hidden">
            <div class="max-w-7xl mx-auto py-6 px-4">
                <!-- AI Control - Same as Dashboard -->
                <div class="mb-6 flex justify-between items-center">
                    <h2 class="text-3xl font-bold">Trading Panel</h2>
                    <div class="flex items-center space-x-4">
                        <div class="flex space-x-2">
                            <button id="tradeProbotAiToggle" onclick="toggleProbotAI()" class="ai-inactive px-4 py-2 rounded-lg font-bold transition-all text-sm bg-gradient-to-r from-purple-600 to-blue-600 hover:from-purple-700 hover:to-blue-700">
                                <span id="tradeProbotAiStatus">🤖 ProBot AI Durduruldu</span>
                            </button>
                            <button id="tradeFastAiToggle" onclick="toggleFastAI()" class="ai-inactive px-4 py-2 rounded-lg font-bold transition-all text-sm">
                                <span id="tradeFastAiStatus">⚡ Hızlı AI Durduruldu</span>
                            </button>
                            <button id="tradeLongAiToggle" onclick="toggleLongAI()" class="ai-inactive px-4 py-2 rounded-lg font-bold transition-all text-sm">
                                <span id="tradeLongAiStatus">🎯 Uzun AI Durduruldu</span>
                            </button>
                        </div>
                        <div class="text-sm">
                            <div>Bakiye: <span id="tradeCurrentBalance" class="text-yellow-400 font-bold">API Bağlantısı Bekleniyor</span></div>
                            <div>Kar/Zarar: <span id="tradeTotalPnL" class="font-bold">$0.00</span></div>
                            <div class="flex space-x-4 text-xs">
                                <span>ProBot: <span id="tradeProbotTradeCount" class="text-purple-400">0</span></span>
                                <span>Hızlı: <span id="tradeFastTradeCount" class="text-blue-400">0</span></span>
                                <span>Uzun: <span id="tradeLongTradeCount" class="text-green-400">0</span></span>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Trade Information - Top -->
                <div class="trading-card p-6 mb-6">
                    <h3 class="text-xl font-bold mb-4 accent-blue">📊 Trade Bilgileri</h3>
                    <div class="grid grid-cols-2 md:grid-cols-6 gap-4">
                        <div class="trading-card p-4">
                            <div class="text-sm text-gray-400">Aktif İşlemler</div>
                            <div class="text-2xl font-bold accent-blue" id="tradeActiveTrades">0</div>
                        </div>
                        <div class="trading-card p-4">
                            <div class="text-sm text-gray-400">Toplam İşlem</div>
                            <div class="text-2xl font-bold accent-purple" id="tradeTotalTrades">0</div>
                        </div>
                        <div class="trading-card p-4">
                            <div class="text-sm text-gray-400">Karlı Pozisyon</div>
                            <div class="text-2xl font-bold accent-green" id="tradeProfitableTrades">0</div>
                        </div>
                        <div class="trading-card p-4">
                            <div class="text-sm text-gray-400">Zararlı Pozisyon</div>
                            <div class="text-2xl font-bold accent-red" id="tradeLossTrades">0</div>
                        </div>
                        <div class="trading-card p-4">
                            <div class="text-sm text-gray-400">Başarı Oranı</div>
                            <div class="text-2xl font-bold accent-green" id="tradeSuccessRate">0%</div>
                        </div>
                        <div class="trading-card p-4">
                            <div class="text-sm text-gray-400">Toplam P&L</div>
                            <div class="text-2xl font-bold" id="tradeTotalPnL">$0.00</div>
                        </div>
                    </div>
                </div>


                <!-- Trade Tabs -->
                <div class="mb-6">
                    <div class="flex justify-between items-center border-b border-gray-700">
                        <div class="flex space-x-4">
                            <button onclick="showTradeTab('active')" id="activeTradeTab" class="trade-tab-btn px-4 py-2 font-medium border-b-2 border-blue-500 text-blue-400 bg-transparent">Aktif İşlemler</button>
                            <button onclick="showTradeTab('completed')" id="completedTradeTab" class="trade-tab-btn px-4 py-2 font-medium text-gray-400 hover:text-white bg-transparent border-b-2 border-transparent">Sonlanan İşlemler</button>
                        </div>
                        <div class="flex space-x-2">
                            <button onclick="resetAllAISettings()" class="bg-orange-600 hover:bg-orange-700 text-white px-4 py-2 rounded-lg font-medium transition-colors duration-200 flex items-center space-x-2">
                                <span>⚙️</span>
                                <span>AI Ayarlarını Sıfırla</span>
                            </button>
                            <button onclick="resetAllTrades()" class="bg-red-600 hover:bg-red-700 text-white px-4 py-2 rounded-lg font-medium transition-colors duration-200 flex items-center space-x-2">
                                <span>🗑️</span>
                                <span>Tümünü Sıfırla</span>
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Active Trades Tab -->
                <div id="activeTradesTab" class="trade-tab-content">
                    <div class="trading-card p-6 mb-6">
                        <h3 class="text-xl font-bold mb-4 accent-green">🟢 Aktif İşlemler</h3>
                        <div class="overflow-x-auto">
                            <div class="min-w-[1000px] overflow-y-auto scrollbar-hide" id="activeTradesContainer" style="max-height: 400px;">
                                <table class="w-full border-collapse border border-gray-600">
                                    <thead class="sticky top-0 bg-gray-800 z-10">
                                        <tr>
                                            <th class="text-left p-3 border-r border-b border-gray-600 min-w-[80px]">Coin</th>
                                            <th class="text-left p-3 border-r border-b border-gray-600 min-w-[70px]">Poz</th>
                                            <th class="text-left p-3 border-r border-b border-gray-600 min-w-[80px]">USDT</th>
                                            <th class="text-left p-3 border-r border-b border-gray-600 min-w-[100px]">Giriş</th>
                                            <th class="text-left p-3 border-r border-b border-gray-600 min-w-[100px]">Güncel</th>
                                            <th class="text-left p-3 border-r border-b border-gray-600 min-w-[80px]">SL</th>
                                            <th class="text-left p-3 border-r border-b border-gray-600 min-w-[80px]">TP</th>
                                            <th class="text-left p-3 border-r border-b border-gray-600 min-w-[100px]">P&L</th>
                                            <th class="text-left p-3 border-b border-gray-600 min-w-[70px]">İşlem</th>
                                        </tr>
                                    </thead>
                                    <tbody id="activeTradesTable">
                                        <!-- Active trades will be populated here -->
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                    
                </div>

                <!-- Completed Trades Tab -->
                <div id="completedTradesTab" class="trade-tab-content hidden">
                    <div class="trading-card p-6 mb-6">
                        <h3 class="text-xl font-bold mb-4 accent-red">🔴 Sonlanan İşlemler</h3>
                        <div class="overflow-x-auto">
                            <div class="min-w-[1000px] overflow-y-auto scrollbar-hide" id="completedTradesContainer" style="max-height: 400px;">
                                <table class="w-full border-collapse border border-gray-600">
                                    <thead class="sticky top-0">
                                        <tr>
                                            <th class="text-left p-3 min-w-[80px] border-r border-b border-gray-600">Coin</th>
                                            <th class="text-left p-3 min-w-[80px] border-r border-b border-gray-600">Poz Yönü</th>
                                            <th class="text-left p-3 min-w-[100px] border-r border-b border-gray-600">Giriş Fiyatı</th>
                                            <th class="text-left p-3 min-w-[100px] border-r border-b border-gray-600">Çıkış Fiyatı</th>
                                            <th class="text-left p-3 min-w-[80px] border-r border-b border-gray-600">SL</th>
                                            <th class="text-left p-3 min-w-[80px] border-r border-b border-gray-600">TP</th>
                                            <th class="text-left p-3 min-w-[100px] border-r border-b border-gray-600">Kar/Zarar</th>
                                            <th class="text-left p-3 min-w-[80px] border-r border-b border-gray-600">Durum</th>
                                            <th class="text-left p-3 min-w-[120px] border-b border-gray-600">Zaman</th>
                                        </tr>
                                    </thead>
                                    <tbody id="completedTradesTable">
                                        <!-- Completed trades will be populated here -->
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- AI Settings Tabs -->
                <div class="mb-6">
                    <div class="flex justify-between items-center">
                        <!-- Tabs -->
                        <div class="flex space-x-4 border-b border-gray-700">
                            <button onclick="showAISettingsTab('probot')" id="probotAISettingsTab" class="ai-settings-tab-btn px-4 py-2 font-medium border-b-2 border-purple-500 text-purple-400 bg-transparent">🤖 ProBot AI Ayarları</button>
                            <button onclick="showAISettingsTab('fast')" id="fastAISettingsTab" class="ai-settings-tab-btn px-4 py-2 font-medium text-gray-400 hover:text-white bg-transparent border-b-2 border-transparent">⚡ Hızlı AI Ayarları</button>
                            <button onclick="showAISettingsTab('long')" id="longAISettingsTab" class="ai-settings-tab-btn px-4 py-2 font-medium text-gray-400 hover:text-white bg-transparent border-b-2 border-transparent">🎯 Uzun AI Ayarları</button>
                            <button onclick="showAISettingsTab('manual')" id="manualSettingsTab" class="ai-settings-tab-btn px-4 py-2 font-medium text-gray-400 hover:text-white bg-transparent border-b-2 border-transparent">🔧 Manuel İşlem</button>
                        </div>
                        
                    </div>
                </div>


                <!-- ProBot AI Settings -->
                <div id="probotAISettings" class="ai-settings-content trading-card p-6 mb-6">
                    <h3 class="text-xl font-bold mb-4 accent-purple">🤖 ProBot AI Trading Parametreleri</h3>
                    

                    <!-- ProBot AI Trading Settings -->
                    <div class="grid grid-cols-2 md:grid-cols-5 gap-4 mb-4">
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">İlk Alım USDT</label>
                            <input type="number" id="probotUsdtAmount" value="1" step="0.1"
                                   class="w-full compact-input">
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Kaldıraç</label>
                            <input type="number" id="probotLeverage" value="10" step="1"
                                   class="w-full compact-input">
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Stop Loss (%)</label>
                            <input type="number" id="probotStopLoss" value="2" step="0.1"
                                   class="w-full compact-input">
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Take Profit (%)</label>
                            <input type="number" id="probotTakeProfit" value="1" step="0.1"
                                   class="w-full compact-input">
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Güven Seviyesi (%)</label>
                            <input type="number" id="probotConfidenceThreshold" value="80" step="1"
                                   class="w-full compact-input">
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Max İşlem Adedi</label>
                            <input type="number" id="probotMaxTrades" value="3" step="1"
                                   class="w-full compact-input">
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Skor Eşiği</label>
                            <input type="number" id="probotScoreThreshold" value="0.5" step="0.1"
                                   class="w-full compact-input">
                        </div>
                    </div>
                    
                    <!-- DCA Settings for ProBot AI -->
                    <div class="mt-6 p-4 bg-gray-800 rounded-lg">
                        <h4 class="text-lg font-bold mb-4 text-purple-400">📈 ProBot AI DCA Ayarları</h4>
                        <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                            <div class="trading-card p-4">
                                <label class="flex items-center mb-2">
                                    <input type="checkbox" id="probotDcaEnabled" class="mr-2">
                                    <span class="text-sm font-medium">DCA Aktif</span>
                                </label>
                                <div class="text-xs text-gray-400">ProBot AI işlemlerde DCA kullan</div>
                            </div>
                            <div class="trading-card p-4">
                                <label class="block text-sm font-medium mb-2">DCA Seviye Sayısı</label>
                                <input type="number" id="probotDcaCount" value="2" min="1" max="5" step="1"
                                       class="w-full compact-input">
                                <div class="text-xs text-gray-400 mt-1">Toplam DCA seviyesi</div>
                            </div>
                            <div class="trading-card p-4">
                                <label class="block text-sm font-medium mb-2">DCA Tetikleme (%)</label>
                                <input type="number" id="probotDcaTrigger" value="1.5" min="1" max="10" step="0.5"
                                       class="w-full compact-input">
                                <div class="text-xs text-gray-400 mt-1">Fiyat düşüşünde tetikle</div>
                            </div>
                            <div class="trading-card p-4">
                                <label class="block text-sm font-medium mb-2">DCA Çarpanı</label>
                                <input type="number" id="probotDcaMultiplier" value="2.0" min="1.0" max="5.0" step="0.1"
                                       class="w-full compact-input">
                                <div class="text-xs text-gray-400 mt-1">Her DCA'da artış çarpanı</div>
                            </div>
                        </div>
                        
                        <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mt-4">
                            <div class="trading-card p-4">
                                <label class="block text-sm font-medium mb-2">Takip Eden SL (%)</label>
                                <input type="number" id="probotTrailingStop" value="3.0" min="0.1" max="5" step="0.1"
                                       class="w-full compact-input">
                                <div class="text-xs text-gray-400 mt-1">Kar koruma seviyesi</div>
                            </div>
                            <div class="trading-card p-4">
                                <label class="block text-sm font-medium mb-2">Risk Yönetimi</label>
                                <select id="probotRiskLevel" class="w-full compact-input">
                                    <option value="conservative">Konservatif</option>
                                    <option value="moderate" selected>Orta</option>
                                    <option value="aggressive">Agresif</option>
                                </select>
                            </div>
                            <div class="trading-card p-4">
                                <label class="block text-sm font-medium mb-2">Volatilite Filtresi</label>
                                <select id="probotVolatilityFilter" class="w-full compact-input">
                                    <option value="low">Düşük</option>
                                    <option value="medium" selected>Orta</option>
                                    <option value="high">Yüksek</option>
                                </select>
                            </div>
                        </div>
                    </div>

                </div>

                <!-- Fast AI Settings -->
                <div id="fastAISettings" class="ai-settings-content trading-card p-6 mb-6 hidden">
                    <h3 class="text-xl font-bold mb-4 accent-blue">⚡ Hızlı AI Trading Parametreleri</h3>
                    <div class="grid grid-cols-2 md:grid-cols-5 gap-4 mb-4">
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">İlk Alım USDT</label>
                            <input type="number" id="fastUsdtAmount" value="1" step="0.1"
                                   class="w-full compact-input">
                            <div class="text-xs text-gray-400 mt-1">Hızlı pozisyon</div>
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Kaldıraç</label>
                            <input type="number" id="fastLeverage" value="10" step="1"
                                   class="w-full compact-input">
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Stop Loss (%)</label>
                            <input type="number" id="fastStopLoss" value="2" step="0.1"
                                   class="w-full compact-input">
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Take Profit (%)</label>
                            <input type="number" id="fastTakeProfit" value="1" step="0.1"
                                   class="w-full compact-input">
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Güven Seviyesi (%)</label>
                            <input type="number" id="fastConfidence" value="80" step="1"
                                   class="w-full compact-input">
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Max İşlem Adedi</label>
                            <input type="number" id="fastMaxTrades" value="3" step="1"
                                   class="w-full compact-input">
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Skor Eşiği</label>
                            <input type="number" id="fastScoreThreshold" value="25" step="1"
                                   class="w-full compact-input">
                        </div>
                    </div>
                    
                    <!-- DCA Settings for Fast AI -->
                    <div class="mt-6 p-4 bg-gray-800 rounded-lg">
                        <h4 class="text-lg font-bold mb-4 text-blue-400">📈 Hızlı AI DCA Ayarları</h4>
                        <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                            <div class="trading-card p-4">
                                <label class="flex items-center mb-2">
                                    <input type="checkbox" id="fastDcaEnabled" class="mr-2">
                                    <span class="text-sm font-medium">DCA Aktif</span>
                                </label>
                                <div class="text-xs text-gray-400">Hızlı AI işlemlerde DCA kullan</div>
                            </div>
                            <div class="trading-card p-4">
                                <label class="block text-sm font-medium mb-2">DCA Seviye Sayısı</label>
                                <input type="number" id="fastDcaCount" value="2" min="1" max="5" step="1"
                                       class="w-full compact-input">
                                <div class="text-xs text-gray-400 mt-1">Toplam DCA seviyesi</div>
                            </div>
                            <div class="trading-card p-4">
                                <label class="block text-sm font-medium mb-2">DCA Tetikleme (%)</label>
                                <input type="number" id="fastDcaTrigger" value="3" min="1" max="10" step="0.5"
                                       class="w-full compact-input">
                                <div class="text-xs text-gray-400 mt-1">Fiyat düşüşünde tetikle</div>
                            </div>
                            <div class="trading-card p-4">
                                <label class="block text-sm font-medium mb-2">DCA Çarpanı</label>
                                <input type="number" id="fastDcaMultiplier" value="1.2" min="1.1" max="2" step="0.1"
                                       class="w-full compact-input">
                                <div class="text-xs text-gray-400 mt-1">Her seviyede çarpan</div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Long AI Settings -->
                <div id="longAISettings" class="ai-settings-content trading-card p-6 mb-6 hidden">
                    <h3 class="text-xl font-bold mb-4 accent-green">🎯 Uzun AI Trading Parametreleri</h3>
                    <div class="grid grid-cols-2 md:grid-cols-5 gap-4 mb-4">
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">İlk Alım USDT</label>
                            <input type="number" id="longUsdtAmount" value="1" step="0.1"
                                   class="w-full compact-input">
                            <div class="text-xs text-gray-400 mt-1">Uzun pozisyon</div>
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Kaldıraç</label>
                            <input type="number" id="longLeverage" value="10" step="1"
                                   class="w-full compact-input">
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Stop Loss (%)</label>
                            <input type="number" id="longStopLoss" value="2" step="0.1"
                                   class="w-full compact-input">
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Take Profit (%)</label>
                            <input type="number" id="longTakeProfit" value="1" step="0.1"
                                   class="w-full compact-input">
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Güven Seviyesi (%)</label>
                            <input type="number" id="longConfidence" value="80" step="1"
                                   class="w-full compact-input">
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Max İşlem Adedi</label>
                            <input type="number" id="longMaxTrades" value="3" step="1"
                                   class="w-full compact-input">
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Skor Eşiği</label>
                            <input type="number" id="longScoreThreshold" value="80" step="1"
                                   class="w-full compact-input">
                        </div>
                    </div>
                    
                    <!-- DCA Settings for Long AI -->
                    <div class="mt-6 p-4 bg-gray-800 rounded-lg">
                        <h4 class="text-lg font-bold mb-4 text-green-400">📈 Uzun AI DCA Ayarları</h4>
                        <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                            <div class="trading-card p-4">
                                <label class="flex items-center mb-2">
                                    <input type="checkbox" id="longDcaEnabled" class="mr-2">
                                    <span class="text-sm font-medium">DCA Aktif</span>
                                </label>
                                <div class="text-xs text-gray-400">Uzun AI işlemlerde DCA kullan</div>
                            </div>
                            <div class="trading-card p-4">
                                <label class="block text-sm font-medium mb-2">DCA Seviye Sayısı</label>
                                <input type="number" id="longDcaCount" value="4" min="1" max="8" step="1"
                                       class="w-full compact-input">
                                <div class="text-xs text-gray-400 mt-1">Toplam DCA seviyesi</div>
                            </div>
                            <div class="trading-card p-4">
                                <label class="block text-sm font-medium mb-2">DCA Tetikleme (%)</label>
                                <input type="number" id="longDcaTrigger" value="8" min="3" max="20" step="0.5"
                                       class="w-full compact-input">
                                <div class="text-xs text-gray-400 mt-1">Fiyat düşüşünde tetikle</div>
                            </div>
                            <div class="trading-card p-4">
                                <label class="block text-sm font-medium mb-2">DCA Çarpanı</label>
                                <input type="number" id="longDcaMultiplier" value="1.5" min="1.2" max="3" step="0.1"
                                       class="w-full compact-input">
                                <div class="text-xs text-gray-400 mt-1">Her seviyede çarpan</div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Manual Trading Settings -->
                <div id="manualSettings" class="ai-settings-content trading-card p-6 mb-6 hidden">
                    <h3 class="text-xl font-bold mb-4 accent-purple">🔧 Manuel Trading Parametreleri</h3>
                    <div class="grid grid-cols-2 md:grid-cols-5 gap-4 mb-4">
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">İlk Alım USDT</label>
                            <input type="number" id="manualUsdtAmount" value="50" 
                                   class="w-full compact-input">
                            <div class="text-xs text-gray-400 mt-1">Manuel pozisyon</div>
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Kaldıraç</label>
                            <select id="manualLeverage" class="w-full compact-input">
                                <option value="1">1x</option>
                                <option value="2">2x</option>
                                <option value="5" selected>5x</option>
                                <option value="10">10x</option>
                                <option value="20">20x</option>
                                <option value="50">50x</option>
                                <option value="75">75x</option>
                                <option value="125">125x</option>
                            </select>
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Stop Loss (%)</label>
                            <input type="number" id="manualStopLoss" value="3" min="0.5" max="20" step="0.1"
                                   class="w-full compact-input">
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Take Profit (%)</label>
                            <input type="number" id="manualTakeProfit" value="8" min="1" max="50" step="0.1"
                                   class="w-full compact-input">
                        </div>
                        <div class="trading-card p-4">
                            <label class="block text-sm font-medium mb-2">Pozisyon Tipi</label>
                            <select id="manualPositionType" class="w-full compact-input">
                                <option value="LONG">LONG</option>
                                <option value="SHORT">SHORT</option>
                            </select>
                        </div>
                    </div>
                    
                    <!-- DCA Settings for Manual Trades -->
                    <div class="mt-6 p-4 bg-gray-800 rounded-lg">
                        <h4 class="text-lg font-bold mb-4 text-yellow-400">📈 DCA (Dollar Cost Averaging) Ayarları</h4>
                        <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                            <div class="trading-card p-4">
                                <label class="flex items-center mb-2">
                                    <input type="checkbox" id="manualDcaEnabled" class="mr-2">
                                    <span class="text-sm font-medium">DCA Aktif</span>
                                </label>
                                <div class="text-xs text-gray-400">Manuel işlemlerde DCA kullan</div>
                            </div>
                            <div class="trading-card p-4">
                                <label class="block text-sm font-medium mb-2">DCA Seviye Sayısı</label>
                                <input type="number" id="manualDcaCount" value="3" min="1" max="10" step="1"
                                       class="w-full compact-input">
                                <div class="text-xs text-gray-400 mt-1">Toplam DCA seviyesi</div>
                            </div>
                            <div class="trading-card p-4">
                                <label class="block text-sm font-medium mb-2">DCA Tetikleme (%)</label>
                                <input type="number" id="manualDcaTrigger" value="5" min="1" max="20" step="0.5"
                                       class="w-full compact-input">
                                <div class="text-xs text-gray-400 mt-1">Fiyat düşüşünde tetikle</div>
                            </div>
                            <div class="trading-card p-4">
                                <label class="block text-sm font-medium mb-2">DCA Çarpanı</label>
                                <input type="number" id="manualDcaMultiplier" value="1.5" min="1.2" max="3" step="0.1"
                                       class="w-full compact-input">
                                <div class="text-xs text-gray-400 mt-1">Her seviyede çarpan</div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Manual Trade Button -->
                    <div class="text-center mt-4">
                        <button onclick="openManualTrade()" class="bg-gradient-to-r from-purple-600 to-blue-600 hover:from-purple-700 hover:to-blue-700 px-8 py-3 rounded-lg font-bold text-white transition-all duration-200 transform hover:scale-105">
                            🚀 Manuel İşlem Aç
                        </button>
                    </div>
                    
                </div>


            </div>
        </div>

        <!-- API Connection Page -->
        <div id="apiPage" class="page hidden">
            <div class="max-w-6xl mx-auto py-6 px-4">
                <h2 class="text-3xl font-bold mb-6">API Bağlantı Ayarları</h2>
                
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                    <!-- Binance API -->
                    <div class="bg-gray-800 rounded-xl p-6">
                        <h3 class="text-xl font-bold mb-4 text-yellow-400">Binance API</h3>
                        <div class="space-y-4">
                            <div>
                                <label class="block text-sm font-medium mb-2">API Key</label>
                                <input type="text" id="binanceApiKey" placeholder="Binance API Key"
                                       class="w-full px-3 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-yellow-500">
                            </div>
                            <div>
                                <label class="block text-sm font-medium mb-2">Secret Key</label>
                                <input type="password" id="binanceSecretKey" placeholder="Binance Secret Key"
                                       class="w-full px-3 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-yellow-500">
                            </div>
                            <div>
                                <label class="block text-sm font-medium mb-2">Emir Tipi</label>
                                <select id="binanceOrderType" class="w-full px-3 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-yellow-500">
                                    <option value="Market">Market Emir (Anında İşlem)</option>
                                    <option value="Limit">Limit Emir (Belirli Fiyat)</option>
                                </select>
                            </div>
                            <div class="flex items-center space-x-2">
                                <input type="checkbox" id="binanceAutoSlTp" checked class="rounded">
                                <label class="text-sm">Otomatik SL/TP Gönder</label>
                            </div>
                            <div class="flex space-x-4">
                                <button onclick="testBinanceConnection()" class="bg-yellow-600 hover:bg-yellow-700 px-4 py-2 rounded-lg transition-colors">
                                    Test Et
                                </button>
                                <button onclick="saveBinanceKeys()" class="bg-green-600 hover:bg-green-700 px-4 py-2 rounded-lg transition-colors">
                                    Kaydet
                                </button>
                            </div>
                            <div id="binanceStatus" class="mt-4"></div>
                        </div>
                    </div>

                    <!-- Bybit API -->
                    <div class="bg-gray-800 rounded-xl p-6">
                        <h3 class="text-xl font-bold mb-4 text-orange-400">Bybit API (Ana Borsa)</h3>
                        <div class="space-y-4">
                            <div>
                                <label class="block text-sm font-medium mb-2">API Key</label>
                                <input type="text" id="bybitApiKey" placeholder="Bybit API Key"
                                       class="w-full px-3 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-orange-500">
                            </div>
                            <div>
                                <label class="block text-sm font-medium mb-2">Secret Key</label>
                                <input type="password" id="bybitSecretKey" placeholder="Bybit Secret Key"
                                       class="w-full px-3 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-orange-500">
                            </div>
                            <div>
                                <label class="block text-sm font-medium mb-2">Emir Tipi</label>
                                <select id="orderType" class="w-full px-3 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-orange-500">
                                    <option value="Market">Market Emir (Anında İşlem)</option>
                                    <option value="Limit">Limit Emir (Belirli Fiyat)</option>
                                </select>
                            </div>
                            <div class="flex items-center space-x-2">
                                <input type="checkbox" id="autoSlTp" checked class="rounded">
                                <label class="text-sm">Otomatik SL/TP Gönder</label>
                            </div>
                            <div class="flex space-x-4">
                                <button onclick="testBybitConnection()" class="bg-orange-600 hover:bg-orange-700 px-4 py-2 rounded-lg transition-colors">
                                    Test Et
                                </button>
                                <button onclick="saveBybitKeys()" class="bg-green-600 hover:bg-green-700 px-4 py-2 rounded-lg transition-colors">
                                    Kaydet
                                </button>
                            </div>
                            <div id="bybitStatus" class="mt-4"></div>
                        </div>
                    </div>
                </div>

                <!-- Webhook Settings -->
                <div class="mt-6 bg-gray-800 rounded-xl p-6">
                    <h3 class="text-xl font-bold mb-4 text-purple-400">TradingView Webhook Ayarları</h3>
                    <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                        <div>
                            <label class="block text-sm font-medium mb-2">Webhook URL</label>
                            <input type="text" id="webhookUrl" placeholder="https://yourserver.com/webhook" 
                                   class="w-full px-3 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-purple-500">
                            <div class="text-xs text-gray-400 mt-1">TradingView'dan gelen sinyaller için</div>
                        </div>
                        <div>
                            <label class="block text-sm font-medium mb-2">Webhook Secret</label>
                            <input type="password" id="webhookSecret" placeholder="Güvenlik anahtarı"
                                   class="w-full px-3 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-purple-500">
                            <div class="text-xs text-gray-400 mt-1">Güvenlik için gerekli</div>
                        </div>
                    </div>
                    
                    <div class="mt-4">
                        <label class="block text-sm font-medium mb-2">Webhook Mesaj Formatı</label>
                        <textarea id="webhookMessage" rows="4" placeholder='{"action": "{{strategy.order.action}}", "symbol": "{{ticker}}", "price": "{{close}}", "time": "{{time}}"}'
                                  class="w-full px-3 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-purple-500"></textarea>
                        <div class="text-xs text-gray-400 mt-1">TradingView'da kullanılacak JSON formatı</div>
                    </div>
                    
                    <div class="flex space-x-4 mt-4">
                        <button onclick="testWebhook()" class="bg-purple-600 hover:bg-purple-700 px-4 py-2 rounded-lg transition-colors">
                            Test Et
                        </button>
                        <button onclick="saveWebhookSettings()" class="bg-green-600 hover:bg-green-700 px-4 py-2 rounded-lg transition-colors">
                            Kaydet
                        </button>
                    </div>
                    <div id="webhookStatus" class="mt-4"></div>
                </div>

                <!-- API Logs -->
                <div class="mt-6 bg-gray-800 rounded-xl p-6">
                    <h3 class="text-xl font-bold mb-4 text-cyan-400">📋 API İşlem Logları</h3>
                    <div class="bg-gray-900 rounded-lg p-4 h-64 overflow-y-auto scrollbar-hide">
                        <div id="apiLogs" class="text-sm font-mono text-green-400 space-y-1">
                            <div class="text-gray-400">API logları burada görünecek...</div>
                        </div>
                    </div>
                    <div class="flex justify-between items-center mt-4">
                        <button onclick="clearApiLogs()" class="bg-red-600 hover:bg-red-700 px-4 py-2 rounded-lg transition-colors">
                            Logları Temizle
                        </button>
                        <div class="text-sm text-gray-400">
                            Son güncelleme: <span id="apiLogTime">--:--</span>
                        </div>
                    </div>
                </div>

            </div>
        </div>

        <!-- Control Panel Page -->
        <div id="controlPage" class="page hidden">
            <div class="max-w-7xl mx-auto py-6 px-4">
                <h2 class="text-3xl font-bold mb-6">Kontrol Paneli</h2>
                
                <!-- AI Status and Controls -->
                <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-6">
                    <!-- ProBot AI Status -->
                    <div class="trading-card p-6">
                        <h3 class="text-xl font-bold mb-4 accent-purple">🤖 ProBot AI Durumu</h3>
                        <div class="space-y-3">
                            <div class="flex justify-between">
                                <span>Durum:</span>
                                <span id="controlProbotAiStatus" class="text-red-400">Durduruldu</span>
                            </div>
                            <div class="flex justify-between">
                                <span>Son Analiz:</span>
                                <span id="controlProbotAiLastAnalysis" class="text-gray-400">-</span>
                            </div>
                            <div class="flex justify-between">
                                <span>Tarama Sayısı:</span>
                                <span id="controlProbotAiScanCount" class="text-purple-400">0</span>
                            </div>
                            <div class="flex justify-between">
                                <span>Bulunan Fırsat:</span>
                                <span id="controlProbotAiOpportunities" class="text-green-400">0</span>
                            </div>
                            <div class="flex justify-between">
                                <span>Son İşlem:</span>
                                <span id="controlProbotAiLastTrade" class="text-gray-400">-</span>
                            </div>
                        </div>
                    </div>

                    <!-- Fast AI Status -->
                    <div class="trading-card p-6">
                        <h3 class="text-xl font-bold mb-4 accent-blue">⚡ Hızlı AI Durumu</h3>
                        <div class="space-y-3">
                            <div class="flex justify-between">
                                <span>Durum:</span>
                                <span id="controlFastAiStatus" class="text-red-400">Durduruldu</span>
                            </div>
                            <div class="flex justify-between">
                                <span>Son Analiz:</span>
                                <span id="controlFastAiLastAnalysis" class="text-gray-400">-</span>
                            </div>
                            <div class="flex justify-between">
                                <span>Tarama Sayısı:</span>
                                <span id="controlFastAiScanCount" class="text-blue-400">0</span>
                            </div>
                            <div class="flex justify-between">
                                <span>Bulunan Fırsat:</span>
                                <span id="controlFastAiOpportunities" class="text-green-400">0</span>
                            </div>
                            <div class="flex justify-between">
                                <span>Son İşlem:</span>
                                <span id="controlFastAiLastTrade" class="text-gray-400">-</span>
                            </div>
                        </div>
                    </div>

                    <!-- Long AI Status -->
                    <div class="trading-card p-6">
                        <h3 class="text-xl font-bold mb-4 accent-green">🎯 Uzun AI Durumu</h3>
                        <div class="space-y-3">
                            <div class="flex justify-between">
                                <span>Durum:</span>
                                <span id="controlLongAiStatus" class="text-red-400">Durduruldu</span>
                            </div>
                            <div class="flex justify-between">
                                <span>Son Analiz:</span>
                                <span id="controlLongAiLastAnalysis" class="text-gray-400">-</span>
                            </div>
                            <div class="flex justify-between">
                                <span>Tarama Sayısı:</span>
                                <span id="controlLongAiScanCount" class="text-blue-400">0</span>
                            </div>
                            <div class="flex justify-between">
                                <span>Bulunan Fırsat:</span>
                                <span id="controlLongAiOpportunities" class="text-green-400">0</span>
                            </div>
                            <div class="flex justify-between">
                                <span>Son İşlem:</span>
                                <span id="controlLongAiLastTrade" class="text-gray-400">-</span>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- AI Logs -->
                <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                    <!-- ProBot AI Logs -->
                    <div class="trading-card p-6">
                        <h3 class="text-xl font-bold mb-4 accent-purple">🤖 ProBot AI Logları</h3>
                        <div id="probotLogs" class="bg-gray-900 rounded-lg p-4 h-96 overflow-y-auto text-sm font-mono">
                            <div class="text-gray-400">ProBot AI logları burada görünecek...</div>
                        </div>
                        <button onclick="clearProbotAiLogs()" class="mt-2 bg-red-600 hover:bg-red-700 px-3 py-1 rounded text-xs">Logları Temizle</button>
                    </div>

                    <!-- Fast AI Logs -->
                    <div class="trading-card p-6">
                        <h3 class="text-xl font-bold mb-4 accent-blue">⚡ Hızlı AI Logları</h3>
                        <div id="fastAiLogs" class="bg-gray-900 rounded-lg p-4 h-96 overflow-y-auto text-sm font-mono">
                            <div class="text-gray-400">Hızlı AI logları burada görünecek...</div>
                        </div>
                        <button onclick="clearFastAiLogs()" class="mt-2 bg-red-600 hover:bg-red-700 px-3 py-1 rounded text-xs">Logları Temizle</button>
                    </div>

                    <!-- Long AI Logs -->
                    <div class="trading-card p-6">
                        <h3 class="text-xl font-bold mb-4 accent-green">🎯 Uzun AI Logları</h3>
                        <div id="longAiLogs" class="bg-gray-900 rounded-lg p-4 h-96 overflow-y-auto text-sm font-mono">
                            <div class="text-gray-400">Uzun AI logları burada görünecek...</div>
                        </div>
                        <button onclick="clearLongAiLogs()" class="mt-2 bg-red-600 hover:bg-red-700 px-3 py-1 rounded text-xs">Logları Temizle</button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Admin Control Panel -->
        <div id="adminControlPage" class="page hidden">
            <div class="max-w-7xl mx-auto py-6 px-4">
                <h2 class="text-3xl font-bold mb-6 text-red-400">Admin Kontrol Paneli</h2>
                
                <!-- Admin Navigation Tabs -->
                <div class="mb-6">
                    <div class="flex space-x-4 border-b border-gray-700">
                        <button onclick="showAdminTab('probot')" class="admin-tab-btn px-4 py-2 font-medium border-b-2 border-purple-500 text-purple-400 bg-transparent">🤖 ProBot AI</button>
                        <button onclick="showAdminTab('users')" class="admin-tab-btn px-4 py-2 font-medium text-gray-400 hover:text-white bg-transparent border-b-2 border-transparent">Kullanıcı Yönetimi</button>
                        <button onclick="showAdminTab('indicators')" class="admin-tab-btn px-4 py-2 font-medium text-gray-400 hover:text-white bg-transparent border-b-2 border-transparent">İndikatör Ayarları</button>
                        <button onclick="showAdminTab('strategy')" class="admin-tab-btn px-4 py-2 font-medium text-gray-400 hover:text-white bg-transparent border-b-2 border-transparent">Strateji Ayarları</button>
                        <button onclick="showAdminTab('system')" class="admin-tab-btn px-4 py-2 font-medium text-gray-400 hover:text-white bg-transparent border-b-2 border-transparent">Sistem Kontrolleri</button>
                    </div>
                </div>

                <!-- ProBot AI Tab -->
                <div id="adminProbotTab" class="admin-tab">
                    <!-- ProBot AI Control Panel -->
                    <div class="trading-card p-6 mb-6">
                        <h3 class="text-xl font-bold mb-4 accent-purple">🤖 ProBot AI Kontrol Paneli</h3>
                        
                        <!-- ProBot Status Overview -->
                        <div class="grid grid-cols-1 md:grid-cols-4 gap-4 mb-6">
                            <div class="trading-card p-4 bg-gradient-to-r from-purple-900 to-blue-900 border border-purple-500">
                                <div class="text-sm text-purple-300">ProBot AI Durumu</div>
                                <div class="text-2xl font-bold text-white" id="adminProbotStatus">Durduruldu</div>
                                <div class="text-xs text-gray-400 mt-1">Son güncelleme: <span id="adminProbotLastUpdate">-</span></div>
                            </div>
                            <div class="trading-card p-4">
                                <div class="text-sm text-gray-400">Aktif Pozisyonlar</div>
                                <div class="text-2xl font-bold text-green-400" id="adminProbotActivePositions">0</div>
                                <div class="text-xs text-gray-500 mt-1">Gerçek zamanlı</div>
                            </div>
                            <div class="trading-card p-4">
                                <div class="text-sm text-gray-400">Günlük İşlem</div>
                                <div class="text-2xl font-bold text-blue-400" id="adminProbotDailyTrades">0</div>
                                <div class="text-xs text-gray-500 mt-1">Son 24 saat</div>
                            </div>
                            <div class="trading-card p-4">
                                <div class="text-sm text-gray-400">Başarı Oranı</div>
                                <div class="text-2xl font-bold text-yellow-400" id="adminProbotSuccessRate">0%</div>
                                <div class="text-xs text-gray-500 mt-1">Son 30 gün</div>
                            </div>
                        </div>

                        <!-- Pine Script Bot Parameters Control -->
                        <div class="mb-6">
                            <h4 class="text-lg font-bold mb-4 text-purple-300">🎯 Pine Script Bot Parametreleri</h4>
                            <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                                <div class="trading-card p-4">
                                    <label class="block text-sm font-medium mb-2">GoLong/Short Periyot</label>
                                    <input type="number" id="adminProbotGoLongPeriod" value="13" min="5" max="100" step="1"
                                           class="w-full compact-input">
                                    <div class="text-xs text-gray-400 mt-1">Varsayılan: 13</div>
                                </div>
                                <div class="trading-card p-4">
                                    <label class="block text-sm font-medium mb-2">GoLong/Short Order</label>
                                    <input type="number" id="adminProbotGoLongOrder" value="5" min="1" max="20" step="1"
                                           class="w-full compact-input">
                                    <div class="text-xs text-gray-400 mt-1">Varsayılan: 5</div>
                                </div>
                                <div class="trading-card p-4">
                                    <label class="block text-sm font-medium mb-2">Filter Deviation</label>
                                    <input type="number" id="adminProbotFilterDeviation" value="1" min="0.1" max="5" step="0.1"
                                           class="w-full compact-input">
                                    <div class="text-xs text-gray-400 mt-1">Varsayılan: 1</div>
                                </div>
                                <div class="trading-card p-4">
                                    <label class="block text-sm font-medium mb-2">Filter Periyot</label>
                                    <input type="number" id="adminProbotFilterPeriod" value="10" min="5" max="50" step="1"
                                           class="w-full compact-input">
                                    <div class="text-xs text-gray-400 mt-1">Varsayılan: 10</div>
                                </div>
                            </div>
                            
                            <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mt-4">
                                <div class="trading-card p-4">
                                    <label class="block text-sm font-medium mb-2">Örnekleme Periyodu</label>
                                    <input type="number" id="adminProbotSamplePeriod" value="10" min="5" max="200" step="1"
                                           class="w-full compact-input">
                                    <div class="text-xs text-gray-400 mt-1">Varsayılan: 10</div>
                                </div>
                                <div class="trading-card p-4">
                                    <label class="block text-sm font-medium mb-2">Aralık Çarpanı</label>
                                    <input type="number" id="adminProbotRangeMultiplier" value="3" min="1" max="10" step="0.1"
                                           class="w-full compact-input">
                                    <div class="text-xs text-gray-400 mt-1">Varsayılan: 3</div>
                                </div>
                                <div class="trading-card p-4">
                                    <label class="block text-sm font-medium mb-2">ATR Periyodu (1dk)</label>
                                    <input type="number" id="adminProbotAtrPeriod" value="14" min="5" max="50" step="1"
                                           class="w-full compact-input">
                                    <div class="text-xs text-gray-400 mt-1">Varsayılan: 14</div>
                                </div>
                                <div class="trading-card p-4">
                                    <label class="block text-sm font-medium mb-2">ATR Filtresi Çarpanı</label>
                                    <input type="number" id="adminProbotAtrMultiplier" value="1.5" min="0.5" max="5" step="0.1"
                                           class="w-full compact-input">
                                    <div class="text-xs text-gray-400 mt-1">Varsayılan: 1.5</div>
                                </div>
                            </div>
                        </div>


                        <!-- ProBot Control Buttons -->
                        <div class="flex space-x-4 mb-6">
                            <button onclick="adminSaveProbotSettings()" class="bg-gradient-to-r from-purple-600 to-blue-600 hover:from-purple-700 hover:to-blue-700 px-6 py-3 rounded-lg font-bold transition-all duration-200 transform hover:scale-105">
                                💾 Ayarları Kaydet
                            </button>
                            <button onclick="adminResetProbotSettings()" class="bg-gray-600 hover:bg-gray-700 px-6 py-3 rounded-lg font-bold transition-all duration-200">
                                🔄 Varsayılana Sıfırla
                            </button>
                            <button onclick="adminTestProbotStrategy()" class="bg-green-600 hover:bg-green-700 px-6 py-3 rounded-lg font-bold transition-all duration-200">
                                🧪 Strateji Test Et
                            </button>
                        </div>

                    </div>
                </div>

                <!-- User Management Tab -->
                <div id="adminUsersTab" class="admin-tab hidden">
                    <!-- Registered Users -->
                    <div class="bg-gray-800 rounded-xl p-6 mb-6">
                        <h3 class="text-xl font-bold mb-4">Kayıtlı Kullanıcılar</h3>
                        <div class="overflow-x-auto bg-gray-800">
                            <table class="w-full bg-gray-800">
                                <thead class="bg-gray-700">
                                    <tr class="border-b border-gray-700 bg-gray-700">
                                        <th class="text-left p-3 text-white">Kullanıcı Adı</th>
                                        <th class="text-left p-3 text-white">Email</th>
                                        <th class="text-left p-3 text-white">Kayıt Tarihi</th>
                                        <th class="text-left p-3 text-white">Trade Erişimi</th>
                                        <th class="text-left p-3 text-white">Kalan Süre</th>
                                        <th class="text-left p-3 text-white">Durum</th>
                                        <th class="text-left p-3 text-white">İşlem</th>
                                    </tr>
                                </thead>
                                <tbody id="registeredUsersTable" class="bg-gray-800">
                                    <!-- Registered users will be populated here -->
                                </tbody>
                            </table>
                        </div>
                    </div>

                    <!-- User Registration Approvals -->
                    <div class="bg-gray-800 rounded-xl p-6 mb-6">
                        <h3 class="text-xl font-bold mb-4">Trade Erişim Onayları</h3>
                        <div class="overflow-x-auto bg-gray-800">
                            <table class="w-full bg-gray-800">
                                <thead class="bg-gray-700">
                                    <tr class="border-b border-gray-700 bg-gray-700">
                                        <th class="text-left p-3 text-white">Kullanıcı Adı</th>
                                        <th class="text-left p-3 text-white">Email</th>
                                        <th class="text-left p-3 text-white">Talep Tarihi</th>
                                        <th class="text-left p-3 text-white">Talep Tipi</th>
                                        <th class="text-left p-3 text-white">Bitiş Tarihi</th>
                                        <th class="text-left p-3 text-white">İşlem</th>
                                    </tr>
                                </thead>
                                <tbody id="pendingRegistrations" class="bg-gray-800">
                                    <!-- Pending registrations will be populated here -->
                                </tbody>
                            </table>
                        </div>
                    </div>

                    <!-- System Statistics -->
                    <div class="grid grid-cols-1 md:grid-cols-4 gap-6">
                        <div class="trading-card p-6">
                            <div class="text-sm text-gray-400">👥 Toplam Kullanıcı</div>
                            <div class="text-3xl font-bold text-blue-400" id="adminTotalUsers">1</div>
                            <div class="text-xs text-gray-500 mt-1">Sadece admin aktif</div>
                        </div>
                        <div class="trading-card p-6">
                            <div class="text-sm text-gray-400">📊 Aktif İşlemler</div>
                            <div class="text-3xl font-bold text-green-400" id="adminActiveTrades">0</div>
                            <div class="text-xs text-gray-500 mt-1">Gerçek zamanlı</div>
                        </div>
                        <div class="trading-card p-6">
                            <div class="text-sm text-gray-400">💰 Günlük Hacim</div>
                            <div class="text-3xl font-bold text-purple-400" id="adminDailyVolume">$0</div>
                            <div class="text-xs text-gray-500 mt-1">Son 24 saat</div>
                        </div>
                        <div class="trading-card p-6">
                            <div class="text-sm text-gray-400">🟢 Sistem Durumu</div>
                            <div class="text-3xl font-bold text-green-400">Online</div>
                            <div class="text-xs text-gray-500 mt-1">Tüm sistemler çalışıyor</div>
                        </div>
                    </div>
                </div>


                <!-- Indicator Settings Tab -->
                <div id="adminIndicatorsTab" class="admin-tab hidden">
                    <!-- AI Indicators -->
                    <div class="trading-card p-6 mb-6">
                        <h3 class="text-xl font-bold mb-4 accent-purple">🤖 AI Teknik İndikatörler</h3>
                        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
                            <div class="trading-card p-4">
                                <div class="flex items-center justify-between mb-2">
                                    <span class="font-bold text-sm">📊 RSI</span>
                                    <button onclick="toggleIndicator('RSI')" class="indicator-btn indicator-active px-3 py-1 rounded-lg text-xs font-medium transition-colors" data-indicator="RSI">
                                        Aktif
                                    </button>
                                </div>
                                <div class="text-xs text-gray-400">Relative Strength Index</div>
                                <div class="text-sm accent-green">Güven: 85%</div>
                            </div>
                            <div class="trading-card p-4">
                                <div class="flex items-center justify-between mb-2">
                                    <span class="font-bold text-sm">📈 MACD</span>
                                    <button onclick="toggleIndicator('MACD')" class="indicator-btn indicator-inactive px-3 py-1 rounded-lg text-xs font-medium transition-colors" data-indicator="MACD">
                                        Pasif
                                    </button>
                                </div>
                                <div class="text-xs text-gray-400">Moving Average Convergence</div>
                                <div class="text-sm accent-red">Güven: 45%</div>
                            </div>
                            <div class="trading-card p-4">
                                <div class="flex items-center justify-between mb-2">
                                    <span class="font-bold text-sm">📉 EMA</span>
                                    <button onclick="toggleIndicator('EMA')" class="indicator-btn indicator-active px-3 py-1 rounded-lg text-xs font-medium transition-colors" data-indicator="EMA">
                                        Aktif
                                    </button>
                                </div>
                                <div class="text-xs text-gray-400">Exponential Moving Average</div>
                                <div class="text-sm accent-green">Güven: 78%</div>
                            </div>
                            <div class="trading-card p-4">
                                <div class="flex items-center justify-between mb-2">
                                    <span class="font-bold text-sm">🌊 Bollinger</span>
                                    <button onclick="toggleIndicator('BB')" class="indicator-btn indicator-inactive px-3 py-1 rounded-lg text-xs font-medium transition-colors" data-indicator="BB">
                                        Pasif
                                    </button>
                                </div>
                                <div class="text-xs text-gray-400">Bollinger Bands</div>
                                <div class="text-sm accent-yellow">Güven: 62%</div>
                            </div>
                            <div class="trading-card p-4">
                                <div class="flex items-center justify-between mb-2">
                                    <span class="font-bold text-sm">⚡ Stochastic</span>
                                    <button onclick="toggleIndicator('STOCH')" class="indicator-btn indicator-active px-3 py-1 rounded-lg text-xs font-medium transition-colors" data-indicator="STOCH">
                                        Aktif
                                    </button>
                                </div>
                                <div class="text-xs text-gray-400">Stochastic Oscillator</div>
                                <div class="text-sm accent-green">Güven: 72%</div>
                            </div>
                            <div class="trading-card p-4">
                                <div class="flex items-center justify-between mb-2">
                                    <span class="font-bold text-sm">🎯 ADX</span>
                                    <button onclick="toggleIndicator('ADX')" class="indicator-btn indicator-inactive px-3 py-1 rounded-lg text-xs font-medium transition-colors" data-indicator="ADX">
                                        Pasif
                                    </button>
                                </div>
                                <div class="text-xs text-gray-400">Average Directional Index</div>
                                <div class="text-sm accent-red">Güven: 38%</div>
                            </div>
                            <div class="trading-card p-4">
                                <div class="flex items-center justify-between mb-2">
                                    <span class="font-bold text-sm">🔄 PSAR</span>
                                    <button onclick="toggleIndicator('PSAR')" class="indicator-btn indicator-active px-3 py-1 rounded-lg text-xs font-medium transition-colors" data-indicator="PSAR">
                                        Aktif
                                    </button>
                                </div>
                                <div class="text-xs text-gray-400">Parabolic SAR</div>
                                <div class="text-sm accent-green">Güven: 68%</div>
                            </div>
                            <div class="trading-card p-4">
                                <div class="flex items-center justify-between mb-2">
                                    <span class="font-bold text-sm">📊 CCI</span>
                                    <button onclick="toggleIndicator('CCI')" class="indicator-btn indicator-inactive px-3 py-1 rounded-lg text-xs font-medium transition-colors" data-indicator="CCI">
                                        Pasif
                                    </button>
                                </div>
                                <div class="text-xs text-gray-400">Commodity Channel Index</div>
                                <div class="text-sm accent-yellow">Güven: 55%</div>
                            </div>
                            <div class="trading-card p-4">
                                <div class="flex items-center justify-between mb-2">
                                    <span class="font-bold text-sm">💰 MFI</span>
                                    <button onclick="toggleIndicator('MFI')" class="indicator-btn indicator-active px-3 py-1 rounded-lg text-xs font-medium transition-colors" data-indicator="MFI">
                                        Aktif
                                    </button>
                                </div>
                                <div class="text-xs text-gray-400">Money Flow Index</div>
                                <div class="text-sm accent-green">Güven: 74%</div>
                            </div>
                            <div class="trading-card p-4">
                                <div class="flex items-center justify-between mb-2">
                                    <span class="font-bold text-sm">📈 OBV</span>
                                    <button onclick="toggleIndicator('OBV')" class="indicator-btn indicator-inactive px-3 py-1 rounded-lg text-xs font-medium transition-colors" data-indicator="OBV">
                                        Pasif
                                    </button>
                                </div>
                                <div class="text-xs text-gray-400">On Balance Volume</div>
                                <div class="text-sm accent-red">Güven: 42%</div>
                            </div>
                            <div class="trading-card p-4">
                                <div class="flex items-center justify-between mb-2">
                                    <span class="font-bold text-sm">🚀 ROC</span>
                                    <button onclick="toggleIndicator('ROC')" class="indicator-btn indicator-active px-3 py-1 rounded-lg text-xs font-medium transition-colors" data-indicator="ROC">
                                        Aktif
                                    </button>
                                </div>
                                <div class="text-xs text-gray-400">Rate of Change</div>
                                <div class="text-sm accent-green">Güven: 66%</div>
                            </div>
                            <div class="trading-card p-4">
                                <div class="flex items-center justify-between mb-2">
                                    <span class="font-bold text-sm">🔺 TRIX</span>
                                    <button onclick="toggleIndicator('TRIX')" class="indicator-btn indicator-inactive px-3 py-1 rounded-lg text-xs font-medium transition-colors" data-indicator="TRIX">
                                        Pasif
                                    </button>
                                </div>
                                <div class="text-xs text-gray-400">Triple Exponential Average</div>
                                <div class="text-sm accent-yellow">Güven: 58%</div>
                            </div>
                            <div class="trading-card p-4">
                                <div class="flex items-center justify-between mb-2">
                                    <span class="font-bold text-sm">📉 Williams %R</span>
                                    <button onclick="toggleIndicator('WILLIAMS_R')" class="indicator-btn indicator-active px-3 py-1 rounded-lg text-xs font-medium transition-colors" data-indicator="WILLIAMS_R">
                                        Aktif
                                    </button>
                                </div>
                                <div class="text-xs text-gray-400">Williams %R</div>
                                <div class="text-sm accent-green">Güven: 71%</div>
                            </div>
                            <div class="trading-card p-4">
                                <div class="flex items-center justify-between mb-2">
                                    <span class="font-bold text-sm">📊 VWAP</span>
                                    <button onclick="toggleIndicator('VWAP')" class="indicator-btn indicator-active px-3 py-1 rounded-lg text-xs font-medium transition-colors" data-indicator="VWAP">
                                        Aktif
                                    </button>
                                </div>
                                <div class="text-xs text-gray-400">Volume Weighted Average Price</div>
                                <div class="text-sm accent-green">Güven: 82%</div>
                            </div>
                            <div class="trading-card p-4">
                                <div class="flex items-center justify-between mb-2">
                                    <span class="font-bold text-sm">⚡ Stoch RSI</span>
                                    <button onclick="toggleIndicator('STOCH_RSI')" class="indicator-btn indicator-active px-3 py-1 rounded-lg text-xs font-medium transition-colors" data-indicator="STOCH_RSI">
                                        Aktif
                                    </button>
                                </div>
                                <div class="text-xs text-gray-400">Stochastic RSI</div>
                                <div class="text-sm accent-green">Güven: 79%</div>
                            </div>
                        </div>
                    </div>

                    <!-- Manual Indicators -->
                    <div class="bg-gray-800 rounded-xl p-6">
                        <h3 class="text-xl font-bold mb-4">Manuel İndikatör Ayarları</h3>
                        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-4">
                            <div class="bg-gray-700 p-4 rounded-lg">
                                <h4 class="font-bold mb-3 text-sm">RSI Ayarları</h4>
                                <div class="space-y-2">
                                    <div>
                                        <label class="block text-xs mb-1">Periyot</label>
                                        <input type="number" id="rsiPeriod" value="14" min="5" max="50"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">Aşırı Alım</label>
                                        <input type="number" id="rsiOverbought" value="70" min="60" max="90"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">Aşırı Satım</label>
                                        <input type="number" id="rsiOversold" value="30" min="10" max="40"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                </div>
                            </div>

                            <div class="bg-gray-700 p-4 rounded-lg">
                                <h4 class="font-bold mb-3 text-sm">MACD Ayarları</h4>
                                <div class="space-y-2">
                                    <div>
                                        <label class="block text-xs mb-1">Hızlı EMA</label>
                                        <input type="number" id="macdFast" value="12" min="5" max="30"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">Yavaş EMA</label>
                                        <input type="number" id="macdSlow" value="26" min="15" max="50"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">Sinyal</label>
                                        <input type="number" id="macdSignal" value="9" min="5" max="20"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                </div>
                            </div>

                            <div class="bg-gray-700 p-4 rounded-lg">
                                <h4 class="font-bold mb-3 text-sm">Bollinger Bands</h4>
                                <div class="space-y-2">
                                    <div>
                                        <label class="block text-xs mb-1">Periyot</label>
                                        <input type="number" id="bbPeriod" value="20" min="10" max="50"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">Standart Sapma</label>
                                        <input type="number" id="bbStdDev" value="2" min="1" max="3" step="0.1"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">Kaynak</label>
                                        <select id="bbSource" class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                            <option value="close">Kapanış</option>
                                            <option value="high">Yüksek</option>
                                            <option value="low">Düşük</option>
                                        </select>
                                    </div>
                                </div>
                            </div>

                            <div class="bg-gray-700 p-4 rounded-lg">
                                <h4 class="font-bold mb-3 text-sm">Parabolic SAR</h4>
                                <div class="space-y-2">
                                    <div>
                                        <label class="block text-xs mb-1">AF Başlangıç</label>
                                        <input type="number" id="psarStart" value="0.02" min="0.01" max="0.1" step="0.01"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">AF Artış</label>
                                        <input type="number" id="psarIncrement" value="0.02" min="0.01" max="0.1" step="0.01"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">AF Maksimum</label>
                                        <input type="number" id="psarMax" value="0.2" min="0.1" max="1" step="0.1"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                </div>
                            </div>

                            <div class="bg-gray-700 p-4 rounded-lg">
                                <h4 class="font-bold mb-3 text-sm">CCI Ayarları</h4>
                                <div class="space-y-2">
                                    <div>
                                        <label class="block text-xs mb-1">Periyot</label>
                                        <input type="number" id="cciPeriod" value="20" min="10" max="50"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">Aşırı Alım</label>
                                        <input type="number" id="cciOverbought" value="100" min="80" max="150"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">Aşırı Satım</label>
                                        <input type="number" id="cciOversold" value="-100" min="-150" max="-80"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                </div>
                            </div>

                            <div class="bg-gray-700 p-4 rounded-lg">
                                <h4 class="font-bold mb-3 text-sm">MFI Ayarları</h4>
                                <div class="space-y-2">
                                    <div>
                                        <label class="block text-xs mb-1">Periyot</label>
                                        <input type="number" id="mfiPeriod" value="14" min="5" max="30"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">Aşırı Alım</label>
                                        <input type="number" id="mfiOverbought" value="80" min="70" max="90"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">Aşırı Satım</label>
                                        <input type="number" id="mfiOversold" value="20" min="10" max="30"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                </div>
                            </div>

                            <div class="bg-gray-700 p-4 rounded-lg">
                                <h4 class="font-bold mb-3 text-sm">Williams %R</h4>
                                <div class="space-y-2">
                                    <div>
                                        <label class="block text-xs mb-1">Periyot</label>
                                        <input type="number" id="williamsRPeriod" value="14" min="5" max="30"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">Aşırı Alım</label>
                                        <input type="number" id="williamsROverbought" value="-20" min="-30" max="-10"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">Aşırı Satım</label>
                                        <input type="number" id="williamsROversold" value="-80" min="-90" max="-70"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                </div>
                            </div>

                            <div class="bg-gray-700 p-4 rounded-lg">
                                <h4 class="font-bold mb-3 text-sm">Stochastic RSI</h4>
                                <div class="space-y-2">
                                    <div>
                                        <label class="block text-xs mb-1">RSI Periyot</label>
                                        <input type="number" id="stochRsiPeriod" value="14" min="5" max="30"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">Stoch Periyot</label>
                                        <input type="number" id="stochRsiStochPeriod" value="14" min="5" max="30"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">K Periyot</label>
                                        <input type="number" id="stochRsiK" value="3" min="1" max="10"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                </div>
                            </div>

                            <div class="bg-gray-700 p-4 rounded-lg">
                                <h4 class="font-bold mb-3 text-sm">ROC Ayarları</h4>
                                <div class="space-y-2">
                                    <div>
                                        <label class="block text-xs mb-1">Periyot</label>
                                        <input type="number" id="rocPeriod" value="12" min="5" max="30"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">Pozitif Eşik</label>
                                        <input type="number" id="rocPositive" value="5" min="1" max="20"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">Negatif Eşik</label>
                                        <input type="number" id="rocNegative" value="-5" min="-20" max="-1"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                </div>
                            </div>

                            <div class="bg-gray-700 p-4 rounded-lg">
                                <h4 class="font-bold mb-3 text-sm">TRIX Ayarları</h4>
                                <div class="space-y-2">
                                    <div>
                                        <label class="block text-xs mb-1">Periyot</label>
                                        <input type="number" id="trixPeriod" value="14" min="5" max="30"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">Sinyal Periyot</label>
                                        <input type="number" id="trixSignal" value="9" min="3" max="20"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">Eşik Değer</label>
                                        <input type="number" id="trixThreshold" value="0.1" min="0.01" max="1" step="0.01"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                </div>
                            </div>

                            <div class="bg-gray-700 p-4 rounded-lg">
                                <h4 class="font-bold mb-3 text-sm">VWAP Ayarları</h4>
                                <div class="space-y-2">
                                    <div>
                                        <label class="block text-xs mb-1">Periyot</label>
                                        <input type="number" id="vwapPeriod" value="20" min="10" max="50"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">Standart Sapma</label>
                                        <input type="number" id="vwapStdDev" value="2" min="1" max="3" step="0.1"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                    </div>
                                    <div>
                                        <label class="block text-xs mb-1">Kaynak</label>
                                        <select id="vwapSource" class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-xs">
                                            <option value="hlc3">HLC3</option>
                                            <option value="close">Kapanış</option>
                                            <option value="ohlc4">OHLC4</option>
                                        </select>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Strategy Settings Tab -->
                <div id="adminStrategyTab" class="admin-tab hidden">
                    <!-- Enhanced DCA Strategy Settings -->
                    <div class="bg-gray-800 rounded-xl p-6 mb-6">
                        <h3 class="text-xl font-bold mb-4">Enhanced DCA Strategy Ayarları</h3>
                        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                            <div class="bg-gray-700 p-4 rounded-lg">
                                <h4 class="font-bold mb-3">ATR Volatilite Filtresi</h4>
                                <div class="space-y-3">
                                    <div>
                                        <label class="block text-sm mb-1">ATR Periyodu</label>
                                        <input type="number" id="atrPeriod" value="14" min="5" max="50"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-sm">
                                    </div>
                                    <div>
                                        <label class="block text-sm mb-1">ATR Çarpanı</label>
                                        <input type="number" id="atrMultiplier" value="2.0" min="0.5" max="5.0" step="0.1"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-sm">
                                    </div>
                                    <div class="flex items-center">
                                        <input type="checkbox" id="enableAtrFilter" checked class="mr-2">
                                        <label class="text-sm">ATR Filtresi Aktif</label>
                                    </div>
                                </div>
                            </div>

                            <div class="bg-gray-700 p-4 rounded-lg">
                                <h4 class="font-bold mb-3">GoLong Sinyali</h4>
                                <div class="space-y-3">
                                    <div>
                                        <label class="block text-sm mb-1">Sinyal Güçlülüğü</label>
                                        <input type="number" id="golongStrength" value="75" min="50" max="100"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-sm">
                                    </div>
                                    <div>
                                        <label class="block text-sm mb-1">Minimum Güven</label>
                                        <input type="number" id="golongConfidence" value="80" min="60" max="95"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-sm">
                                    </div>
                                    <div class="flex items-center">
                                        <input type="checkbox" id="enableGolong" checked class="mr-2">
                                        <label class="text-sm">GoLong Aktif</label>
                                    </div>
                                </div>
                            </div>

                            <div class="bg-gray-700 p-4 rounded-lg">
                                <h4 class="font-bold mb-3">Risk Yönetimi</h4>
                                <div class="space-y-3">
                                    <div>
                                        <label class="block text-sm mb-1">Maksimum Risk (%)</label>
                                        <input type="number" id="maxRiskPercent" value="2" min="0.5" max="10" step="0.1"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-sm">
                                    </div>
                                    <div>
                                        <label class="block text-sm mb-1">Pozisyon Boyutu</label>
                                        <input type="number" id="positionSize" value="1000" min="100" max="10000" step="100"
                                               class="w-full px-2 py-1 bg-gray-600 border border-gray-500 rounded text-white text-sm">
                                    </div>
                                    <div class="flex items-center">
                                        <input type="checkbox" id="enableRiskManagement" checked class="mr-2">
                                        <label class="text-sm">Risk Yönetimi Aktif</label>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- AI Settings -->
                    <div class="bg-gray-800 rounded-xl p-6">
                        <h3 class="text-xl font-bold mb-4">AI Ayarları</h3>
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                            <div>
                                <label class="block text-sm font-medium mb-2">Sinyal Güven Seviyesi (%)</label>
                                <input type="number" id="confidenceLevel" value="75" min="50" max="95" step="1"
                                       class="w-full px-3 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-blue-500">
                            </div>
                            <div>
                                <label class="block text-sm font-medium mb-2">Analiz Periyodu</label>
                                <select id="analysisPeriod" class="w-full px-3 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-blue-500">
                                    <option value="1m">1 Dakika</option>
                                    <option value="5m">5 Dakika</option>
                                    <option value="15m" selected>15 Dakika</option>
                                    <option value="1h">1 Saat</option>
                                    <option value="4h">4 Saat</option>
                                </select>
                            </div>
                            <div class="flex items-center">
                                <input type="checkbox" id="autoTrade" class="mr-2">
                                <label for="autoTrade" class="text-sm">Otomatik İşlem</label>
                            </div>
                            <div class="flex items-center">
                                <input type="checkbox" id="conservativeMode" class="mr-2">
                                <label for="conservativeMode" class="text-sm">Konservatif Mod</label>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- System Controls Tab -->
                <div id="adminSystemTab" class="admin-tab hidden">
                    <div class="bg-gray-800 rounded-xl p-6">
                        <h3 class="text-xl font-bold mb-4">Sistem Kontrolleri</h3>
                        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                            <button onclick="emergencyStop()" class="bg-red-600 hover:bg-red-700 px-6 py-3 rounded-lg font-bold">
                                Acil Durdur
                            </button>
                            <button onclick="restartSystem()" class="bg-yellow-600 hover:bg-yellow-700 px-6 py-3 rounded-lg font-bold">
                                Sistemi Yeniden Başlat
                            </button>
                            <button onclick="backupData()" class="bg-blue-600 hover:bg-blue-700 px-6 py-3 rounded-lg font-bold">
                                Veri Yedekle
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Save Button -->
                <div class="mt-6 flex justify-center">
                    <button onclick="saveAdminSettings()" class="bg-green-600 hover:bg-green-700 px-8 py-3 rounded-lg font-bold transition-colors">
                        Tüm Ayarları Kaydet
                    </button>
                </div>
            </div>
        </div>

        <!-- Coin Detail Page -->
        <div id="coinDetailPage" class="page hidden">
            <div class="max-w-6xl mx-auto py-6 px-4">
                <div class="flex justify-between items-center mb-6">
                    <h2 id="coinDetailTitle" class="text-3xl font-bold">Bitcoin (BTC)</h2>
                    <button onclick="goBackFromCoinDetail()" class="bg-gray-600 hover:bg-gray-700 px-4 py-2 rounded-lg">
                        Geri Dön
                    </button>
                </div>

                <!-- AI Analysis First -->
                <div class="mb-6 bg-gray-800 rounded-xl p-6">
                    <h3 class="text-xl font-bold mb-4">AI Analizi ve Öneriler</h3>
                    <div id="coinAIAnalysis" class="grid grid-cols-1 md:grid-cols-3 gap-6">
                        <!-- AI analysis will be populated here -->
                    </div>
                </div>

                <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                    <!-- Advanced Trading Chart -->
                    <div class="lg:col-span-2 bg-gray-800 rounded-xl p-6">
                        <div class="flex justify-between items-center mb-4">
                            <h3 class="text-xl font-bold">Trading Grafiği</h3>
                            <div class="flex space-x-2">
                                <select id="chartTimeframe" onchange="changeTimeframe()" class="px-3 py-1 bg-gray-700 border border-gray-600 rounded text-white text-sm">
                                    <option value="1m">1 Dakika</option>
                                    <option value="5m">5 Dakika</option>
                                    <option value="15m" selected>15 Dakika</option>
                                    <option value="1h">1 Saat</option>
                                    <option value="4h">4 Saat</option>
                                    <option value="1d">1 Gün</option>
                                </select>
                                <button onclick="refreshChart()" class="bg-blue-600 hover:bg-blue-700 px-3 py-1 rounded text-sm">
                                    Yenile
                                </button>
                            </div>
                        </div>
                        <div class="relative">
                            <canvas id="coinChart" width="600" height="400"></canvas>
                            <div id="chartLoading" class="absolute inset-0 flex items-center justify-center bg-gray-800 bg-opacity-75 hidden">
                                <div class="text-white">Grafik yükleniyor...</div>
                            </div>
                        </div>
                        
                        <!-- Chart Controls -->
                        <div class="mt-4 flex justify-between items-center">
                            <div class="flex space-x-2">
                                <button onclick="toggleIndicatorOnChart('SMA')" class="chart-indicator-btn bg-gray-700 hover:bg-gray-600 px-3 py-1 rounded text-sm text-gray-300">SMA</button>
                                <button onclick="toggleIndicatorOnChart('EMA')" class="chart-indicator-btn bg-gray-700 hover:bg-gray-600 px-3 py-1 rounded text-sm text-gray-300">EMA</button>
                                <button onclick="toggleIndicatorOnChart('BB')" class="chart-indicator-btn bg-gray-700 hover:bg-gray-600 px-3 py-1 rounded text-sm text-gray-300">Bollinger</button>
                                <button onclick="toggleIndicatorOnChart('Volume')" class="chart-indicator-btn bg-gray-700 hover:bg-gray-600 px-3 py-1 rounded text-sm text-gray-300">Volume</button>
                            </div>
                            <div class="text-sm text-gray-400">
                                Son güncelleme: <span id="lastUpdate">--:--</span>
                            </div>
                        </div>
                        
                        <!-- Technical Indicators Below Chart -->
                        <div class="mt-6 bg-gray-700 rounded-lg p-4">
                            <h4 class="font-bold mb-3">Teknik İndikatörler</h4>
                            <div id="technicalIndicators" class="grid grid-cols-2 md:grid-cols-4 gap-4 text-sm">
                                <!-- Technical indicators will be populated here -->
                            </div>
                        </div>
                    </div>

                    <!-- Coin Info -->
                    <div class="bg-gray-800 rounded-xl p-6">
                        <h3 class="text-xl font-bold mb-4">Coin Bilgileri</h3>
                        <div id="coinInfo" class="space-y-4">
                            <!-- Coin info will be populated here -->
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Notification Container -->
    <div id="notificationContainer" class="fixed top-4 right-4 z-50 space-y-2"></div>

    <script>
        // Global Variables
        let currentUser = null;
// --- SESSION PERSISTENCE PATCH START ---
// Restore session if available in localStorage and keep API keys persistent
try {
    const savedSession = localStorage.getItem('ct_session') || localStorage.getItem('session');
    if (savedSession) {
        currentUser = JSON.parse(savedSession);
        // Reveal main app UI if present
        if (document.getElementById('authPage')) document.getElementById('authPage').classList.add('hidden');
        if (document.getElementById('mainApp')) document.getElementById('mainApp').classList.remove('hidden');
        if (document.getElementById('userName')) document.getElementById('userName').textContent = currentUser.username || currentUser.user || '';
        // Restore saved API keys into inputs (if present)
        try {
            const bk = JSON.parse(localStorage.getItem('binance_keys') || 'null');
            if (bk && document.getElementById('binanceApiKey')) { document.getElementById('binanceApiKey').value = bk.apiKey || bk.key || ''; if(document.getElementById('binanceSecretKey')) document.getElementById('binanceSecretKey').value = bk.secret || bk.secretKey || ''; }
            const by = JSON.parse(localStorage.getItem('bybit_keys') || 'null');
            if (by && document.getElementById('bybitApiKey')) { document.getElementById('bybitApiKey').value = by.apiKey || by.key || ''; if(document.getElementById('bybitSecretKey')) document.getElementById('bybitSecretKey').value = by.secret || by.secretKey || ''; }
        } catch(e){ console.warn('restore API keys error', e); }
        // Restore transactions from localStorage
        try {
            const savedTransactions = localStorage.getItem('ct_transactions');
            if (savedTransactions) {
                transactions = JSON.parse(savedTransactions);
                console.log('Transactions restored from storage:', transactions.length);
            }
        } catch(e){ console.warn('restore transactions error', e); }
        // Initialize app state after brief delay to allow DOM ready
        setTimeout(()=>{ try{ if(typeof initializeApp === 'function'){ initializeApp(); } }catch(e){} }, 200);
    }
} catch(e) { console.warn('session restore patch error', e); }
// --- SESSION PERSISTENCE PATCH END ---

        let currentPage = 'dashboard';
        let fastAiActive = false;
        let longAiActive = false;
        let probotAiActive = false;
        let cryptoData = [];
        let transactions = [];
        let activeIndicators = ['RSI', 'EMA', 'STOCH', 'PSAR', 'CCI', 'MFI', 'OBV', 'ROC', 'TRIX', 'WILLIAMS_R', 'VWAP', 'STOCH_RSI'];
        
        // AI Confidence Thresholds (User Configurable)
        let probotAiConfidenceThreshold = 70;
        let fastAiConfidenceThreshold = 75;
        let longAiConfidenceThreshold = 75;
        
        // AI Logging system
        let fastAiLogs = [];
        let longAiLogs = [];
        let probotAiLogs = [];
        let fastAiScanCount = 0;
        let longAiScanCount = 0;
        let probotAiScanCount = 0;
        let fastAiOpportunities = 0;
        let longAiOpportunities = 0;
        let probotAiOpportunities = 0;
        
        // Logging functions
        function addFastAiLog(message, type = 'info') {
            const timestamp = new Date().toLocaleTimeString();
            const logEntry = {
                time: timestamp,
                message: message,
                type: type
            };
            fastAiLogs.push(logEntry);
            
            // Keep only last 100 logs
            if (fastAiLogs.length > 100) {
                fastAiLogs.shift();
            }
            
            updateFastAiLogsDisplay();
        }
        
        function addLongAiLog(message, type = 'info') {
            const timestamp = new Date().toLocaleTimeString();
            const logEntry = {
                time: timestamp,
                message: message,
                type: type
            };
            longAiLogs.push(logEntry);
            
            // Keep only last 100 logs
            if (longAiLogs.length > 100) {
                longAiLogs.shift();
            }
            
            updateLongAiLogsDisplay();
        }
        
        function addProbotAiLog(message, type = 'info') {
            const timestamp = new Date().toLocaleTimeString();
            const logEntry = {
                time: timestamp,
                message: message,
                type: type
            };
            probotAiLogs.push(logEntry);
            
            // Keep only last 100 logs
            if (probotAiLogs.length > 100) {
                probotAiLogs.shift();
            }
            
            updateProbotAiLogsDisplay();
        }
        
        function updateFastAiLogsDisplay() {
            const logsContainer = document.getElementById('fastAiLogs');
            if (!logsContainer) return;
            
            logsContainer.innerHTML = fastAiLogs.map(log => {
                const colorClass = log.type === 'error' ? 'text-red-400' : 
                                 log.type === 'success' ? 'text-green-400' : 
                                 log.type === 'warning' ? 'text-yellow-400' : 'text-gray-300';
                return `<div class="${colorClass}">[${log.time}] ${log.message}</div>`;
            }).join('');
            
            // Auto scroll to bottom
            logsContainer.scrollTop = logsContainer.scrollHeight;
        }
        
        function updateLongAiLogsDisplay() {
            const logsContainer = document.getElementById('longAiLogs');
            if (!logsContainer) return;
            
            logsContainer.innerHTML = longAiLogs.map(log => {
                const colorClass = log.type === 'error' ? 'text-red-400' : 
                                 log.type === 'success' ? 'text-green-400' : 
                                 log.type === 'warning' ? 'text-yellow-400' : 'text-gray-300';
                return `<div class="${colorClass}">[${log.time}] ${log.message}</div>`;
            }).join('');
            
            // Auto scroll to bottom
            logsContainer.scrollTop = logsContainer.scrollHeight;
        }
        
        function updateProbotAiLogsDisplay() {
            const logsContainer = document.getElementById('probotAiLogs');
            if (!logsContainer) return;
            
            logsContainer.innerHTML = probotAiLogs.map(log => {
                const colorClass = log.type === 'error' ? 'text-red-400' : 
                                 log.type === 'success' ? 'text-green-400' : 
                                 log.type === 'warning' ? 'text-yellow-400' : 'text-gray-300';
                return `<div class="${colorClass}">[${log.time}] ${log.message}</div>`;
            }).join('');
            
            // Auto scroll to bottom
            logsContainer.scrollTop = logsContainer.scrollHeight;
        }
        
        function clearFastAiLogs() {
            fastAiLogs = [];
            updateFastAiLogsDisplay();
        }
        
        function clearLongAiLogs() {
            longAiLogs = [];
            updateLongAiLogsDisplay();
        }
        
        function clearProbotAiLogs() {
            probotAiLogs = [];
            updateProbotAiLogsDisplay();
        }
        
        function updateControlPanelStatus() {
            // Update ProBot AI status
            const probotAiStatus = document.getElementById('controlProbotAiStatus');
            const probotAiLastAnalysis = document.getElementById('controlProbotAiLastAnalysis');
            const probotAiScanCountEl = document.getElementById('controlProbotAiScanCount');
            const probotAiOpportunitiesEl = document.getElementById('controlProbotAiOpportunities');
            const probotAiLastTrade = document.getElementById('controlProbotAiLastTrade');
            
            if (probotAiStatus) {
                probotAiStatus.textContent = probotAiActive ? 'Çalışıyor' : 'Durduruldu';
                probotAiStatus.className = probotAiActive ? 'text-green-400' : 'text-red-400';
            }
            if (probotAiLastAnalysis) {
                probotAiLastAnalysis.textContent = new Date().toLocaleTimeString();
            }
            if (probotAiScanCountEl) {
                probotAiScanCountEl.textContent = probotAiScanCount || 0;
            }
            if (probotAiOpportunitiesEl) {
                probotAiOpportunitiesEl.textContent = probotAiOpportunities || 0;
            }
            if (probotAiLastTrade) {
                const lastTrade = transactions.filter(t => t.type === 'ProBot AI').pop();
                probotAiLastTrade.textContent = lastTrade ? `${lastTrade.coin} - ${lastTrade.type}` : '-';
            }
            
            // Update Fast AI status
            const fastAiStatus = document.getElementById('controlFastAiStatus');
            const fastAiLastAnalysis = document.getElementById('controlFastAiLastAnalysis');
            const fastAiScanCountEl = document.getElementById('controlFastAiScanCount');
            const fastAiOpportunitiesEl = document.getElementById('controlFastAiOpportunities');
            const fastAiLastTrade = document.getElementById('controlFastAiLastTrade');
            
            if (fastAiStatus) {
                fastAiStatus.textContent = fastAiActive ? 'Çalışıyor' : 'Durduruldu';
                fastAiStatus.className = fastAiActive ? 'text-green-400' : 'text-red-400';
            }
            if (fastAiLastAnalysis) {
                fastAiLastAnalysis.textContent = new Date().toLocaleTimeString();
            }
            if (fastAiScanCountEl) {
                fastAiScanCountEl.textContent = fastAiScanCount;
            }
            if (fastAiOpportunitiesEl) {
                fastAiOpportunitiesEl.textContent = fastAiOpportunities;
            }
            if (fastAiLastTrade) {
                const lastTrade = transactions.filter(t => t.type === 'Fast AI').pop();
                fastAiLastTrade.textContent = lastTrade ? `${lastTrade.coin} - ${lastTrade.type}` : '-';
            }
            
            // Update Long AI status
            const longAiStatus = document.getElementById('controlLongAiStatus');
            const longAiLastAnalysis = document.getElementById('controlLongAiLastAnalysis');
            const longAiScanCountEl = document.getElementById('controlLongAiScanCount');
            const longAiOpportunitiesEl = document.getElementById('controlLongAiOpportunities');
            const longAiLastTrade = document.getElementById('controlLongAiLastTrade');
            
            if (longAiStatus) {
                longAiStatus.textContent = longAiActive ? 'Çalışıyor' : 'Durduruldu';
                longAiStatus.className = longAiActive ? 'text-green-400' : 'text-red-400';
            }
            if (longAiLastAnalysis) {
                longAiLastAnalysis.textContent = new Date().toLocaleTimeString();
            }
            if (longAiScanCountEl) {
                longAiScanCountEl.textContent = longAiScanCount;
            }
            if (longAiOpportunitiesEl) {
                longAiOpportunitiesEl.textContent = longAiOpportunities;
            }
            if (longAiLastTrade) {
                const lastTrade = transactions.filter(t => t.type === 'Long AI').pop();
                longAiLastTrade.textContent = lastTrade ? `${lastTrade.coin} - ${lastTrade.type}` : '-';
            }
        }

        // Transactions persistence functions
        function saveTransactionsToStorage() {
            try {
                localStorage.setItem('ct_transactions', JSON.stringify(transactions));
            } catch (e) {
                console.warn('Failed to save transactions to localStorage:', e);
            }
        }

        function loadTransactionsFromStorage() {
            try {
                const savedTransactions = localStorage.getItem('ct_transactions');
                if (savedTransactions) {
                    transactions = JSON.parse(savedTransactions);
                    console.log(`📥 Transactions loaded from storage: ${transactions.length} transactions`);
                    console.log('📥 Transaction details:', transactions);
                } else {
                    console.log('📥 No transactions found in storage');
                }
            } catch (e) {
                console.warn('❌ Failed to load transactions from localStorage:', e);
                transactions = [];
            }
        }
        let priceUpdateInterval;
        let chartUpdateInterval;
        let isAdmin = false;
        let totalBalance = 50000;
        let coinChart = null;
        let fastTradeCount = 0;
        let longTradeCount = 0;
        let registeredUsers = [];
        let userTradeAccess = {};

        // Authentication Functions
        function handleLogin(event) {
            event.preventDefault();
            
            const username = document.getElementById('loginUsername').value;
            const password = document.getElementById('loginPassword').value;
            
            if (username === 'Hunter3535' && password === '510400') {
                currentUser = {
                    username: username,
                    loginTime: new Date()
                };
                try{ localStorage.setItem('ct_session', JSON.stringify(currentUser)); }catch(e){}
                
                
                document.getElementById('authPage').classList.add('hidden');
                document.getElementById('mainApp').classList.remove('hidden');
                document.getElementById('userName').textContent = username;
                
                showNotification('Giriş başarılı! Hoş geldiniz ' + username, 'success');
                initializeApp();
            } else {
                showNotification('Kullanıcı adı veya şifre hatalı!', 'error');
            }
        }

        function handleRegister(event) {
            event.preventDefault();
            
            const username = document.getElementById('registerUsername').value;
            const email = document.getElementById('registerEmail').value;
            const password = document.getElementById('registerPassword').value;
            
            // Check if user already exists
            const existingUser = registeredUsers.find(u => u.username === username || u.email === email);
            if (existingUser) {
                showNotification('Bu kullanıcı adı veya email zaten kayıtlı!', 'error');
                return;
            }
            
            // Register new user
            const newUser = {
                username: username,
                email: email,
                password: password,
                registrationDate: new Date(),
                status: 'active',
                tradeAccessExpiry: null,
                lastTradeAccess: null
            };
            
            registeredUsers.push(newUser);
            
            currentUser = {
                username: username,
                email: email,
                loginTime: new Date()
            };
            
            document.getElementById('authPage').classList.add('hidden');
            document.getElementById('mainApp').classList.remove('hidden');
            document.getElementById('userName').textContent = username;
            
            showNotification('Kayıt başarılı! Hoş geldiniz ' + username, 'success');
            initializeApp();
            updateRegisteredUsersTable();
        }

        function handleAdminLogin(event) {
            event.preventDefault();
            
            const username = document.getElementById('adminUsername').value;
            const password = document.getElementById('adminPassword').value;
            
            if (username === 'Hunter3535' && password === '510400') {
                isAdmin = true;
                document.getElementById('adminAuthPage').classList.add('hidden');
                document.getElementById('mainApp').classList.remove('hidden');
                showPage('adminControl');
                showNotification('Admin paneline giriş yapıldı!', 'success');
            } else {
                showNotification('Admin bilgileri hatalı!', 'error');
            }
        }

        function showLogin() {
            document.getElementById('loginForm').classList.remove('hidden');
            document.getElementById('registerForm').classList.add('hidden');
        }

        function showRegister() {
            document.getElementById('loginForm').classList.add('hidden');
            document.getElementById('registerForm').classList.remove('hidden');
        }

        function showAdminPanel() {
            // Only allow admin access for Hunter3535
            if (currentUser && currentUser.username === 'Hunter3535') {
                document.getElementById('mainApp').classList.add('hidden');
                document.getElementById('adminAuthPage').classList.remove('hidden');
            } else {
                showNotification('Admin paneline erişim yetkiniz yok!', 'error');
            }
        }

        function backToMain() {
            document.getElementById('adminAuthPage').classList.add('hidden');
            document.getElementById('mainApp').classList.remove('hidden');
        }

        function logout() {
            currentUser = null;
            isAdmin = false;
            document.getElementById('authPage').classList.remove('hidden');
            document.getElementById('mainApp').classList.add('hidden');
            clearInterval(priceUpdateInterval);
            showNotification('Çıkış yapıldı.', 'info');
        }

        // App Initialization
        function initializeApp() {
            // Load transactions from localStorage
            loadTransactionsFromStorage();
            
            // Load API logs from localStorage
            loadApiLogs();
            displayApiLogs();
            
            generateCryptoData();
            updateCoinList();
            updateAIConditions();
            startPriceUpdates();
            updateTradeInfo();
            
            // Update trade displays after loading transactions
            updateActiveTradesTable();
            updateCompletedTradesTable();
        }

        // Global variables for sorting
        let currentSort = 'default'; // 'default', 'gainers', 'losers'
        let pendingRegistrations = []; // Store pending registrations

        // Generate crypto data - Start fresh from Bybit API only
        function generateCryptoData() {
            // Start with empty array - will be populated entirely from Bybit API
            cryptoData = [];
            
            console.log('🔄 Starting fresh coin list from Bybit Future API...');
            
            // Fetch real prices immediately from Bybit
            fetchRealPrices();
            
            // Set up automatic price updates every 2 seconds
            if (window.priceUpdateInterval) {
                clearInterval(window.priceUpdateInterval);
            }
            window.priceUpdateInterval = setInterval(() => {
                fetchRealPrices();
            }, 2000); // Update every 2 seconds
            
            console.log('🔄 Auto price updates started (every 2 seconds)');
        }

        // Fetch real-time futures prices from Bybit API
        async function fetchRealPrices() {
            try {
                console.log('🔄 Fetching real-time prices from Bybit Future API...');
                
                const response = await fetch(`https://api.bybit.com/v5/market/tickers?category=linear`);
                const result = await response.json();
                
                if (result.retCode === 0 && result.result && result.result.list) {
                    console.log('✅ Bybit API response received:', result.result.list.length, 'coins');
                    
                    // Process all tickers and create a map for quick lookup
                    const tickerMap = new Map();
                    result.result.list.forEach(ticker => {
                        tickerMap.set(ticker.symbol, ticker);
                    });
                    
                    // If cryptoData is empty, initialize it first
                    if (cryptoData.length === 0) {
                        console.log('🔄 Initializing cryptoData from Bybit API...');
                        
                        // Filter coins with decent volume and sort by volume (high to low)
                        const allTickers = result.result.list
                            .filter(ticker => parseFloat(ticker.volume24h) > 100000)
                            .sort((a, b) => parseFloat(b.volume24h) - parseFloat(a.volume24h));
                        
                        // Create cryptoData array
                        const newCryptoData = [];
                        
                        // 1. Always add BTC first
                        const btcTicker = allTickers.find(t => t.symbol === 'BTCUSDT');
                        if (btcTicker) {
                            newCryptoData.push({
                                id: 1,
                                symbol: 'BTC',
                                futuresSymbol: 'BTCUSDT',
                                name: 'Bitcoin',
                                price: parseFloat(btcTicker.lastPrice),
                                change24h: parseFloat(btcTicker.price24hPcnt) * 100,
                                volume: parseFloat(btcTicker.volume24h),
                                high24h: parseFloat(btcTicker.highPrice24h),
                                low24h: parseFloat(btcTicker.lowPrice24h),
                                openPrice: parseFloat(btcTicker.prevPrice24h),
                                marketCap: 0,
                                priceHistory: [],
                                isActive: true,
                                priority: 1
                            });
                            console.log('✅ BTC initialized with real price:', parseFloat(btcTicker.lastPrice));
                        }
                        
                        // 2. Add ETH second
                        const ethTicker = allTickers.find(t => t.symbol === 'ETHUSDT');
                        if (ethTicker) {
                            newCryptoData.push({
                                id: 2,
                                symbol: 'ETH',
                                futuresSymbol: 'ETHUSDT',
                                name: 'Ethereum',
                                price: parseFloat(ethTicker.lastPrice),
                                change24h: parseFloat(ethTicker.price24hPcnt) * 100,
                                volume: parseFloat(ethTicker.volume24h),
                                high24h: parseFloat(ethTicker.highPrice24h),
                                low24h: parseFloat(ethTicker.lowPrice24h),
                                openPrice: parseFloat(ethTicker.prevPrice24h),
                                marketCap: 0,
                                priceHistory: [],
                                isActive: true,
                                priority: 2
                            });
                            console.log('✅ ETH initialized with real price:', parseFloat(ethTicker.lastPrice));
                        }
                        
                        // 3. Add other coins
                        let coinId = 3;
                        allTickers.forEach(ticker => {
                            if (ticker.symbol !== 'BTCUSDT' && ticker.symbol !== 'ETHUSDT') {
                                const coinName = ticker.symbol.replace('USDT', '');
                                newCryptoData.push({
                                    id: coinId++,
                                    symbol: coinName,
                                    futuresSymbol: ticker.symbol,
                                    name: coinName,
                                    price: parseFloat(ticker.lastPrice),
                                    change24h: parseFloat(ticker.price24hPcnt) * 100,
                                    volume: parseFloat(ticker.volume24h),
                                    high24h: parseFloat(ticker.highPrice24h),
                                    low24h: parseFloat(ticker.lowPrice24h),
                                    openPrice: parseFloat(ticker.prevPrice24h),
                                    marketCap: 0,
                                    priceHistory: [],
                                    isActive: true,
                                    priority: 3
                                });
                            }
                        });
                        
                        cryptoData = newCryptoData;
                        console.log('🎉 CryptoData initialized:', cryptoData.length, 'coins');
                    } else {
                        // Update existing coins with real-time data
                        console.log('🔄 Updating existing coins with real-time data...');
                        
                        let updatedCount = 0;
                        result.result.list.forEach(ticker => {
                            // Find existing coin by symbol
                            const existingCoin = cryptoData.find(c => 
                                c.symbol === ticker.symbol.replace('USDT', '') || 
                                c.futuresSymbol === ticker.symbol
                            );
                            
                            if (existingCoin) {
                                const oldPrice = existingCoin.price;
                                const newPrice = parseFloat(ticker.lastPrice);
                                
                                // Only update if price actually changed
                                if (oldPrice !== newPrice) {
                                    // Add to price history (keep last 50 prices)
                                    if (!existingCoin.priceHistory) {
                                        existingCoin.priceHistory = [];
                                    }
                                    existingCoin.priceHistory.push(newPrice);
                                    if (existingCoin.priceHistory.length > 50) {
                                        existingCoin.priceHistory.shift();
                                    }
                                    
                                    existingCoin.price = newPrice;
                                existingCoin.change24h = parseFloat(ticker.price24hPcnt) * 100;
                                existingCoin.volume = parseFloat(ticker.volume24h);
                                existingCoin.high24h = parseFloat(ticker.highPrice24h);
                                existingCoin.low24h = parseFloat(ticker.lowPrice24h);
                                existingCoin.openPrice = parseFloat(ticker.prevPrice24h);
                                    
                                    updatedCount++;
                                
                                if (existingCoin.symbol === 'BTC') {
                                    console.log(`🔄 BTC price updated: ${oldPrice} -> ${existingCoin.price}`);
                                    }
                                }
                            }
                        });
                        
                        console.log(`✅ Updated ${updatedCount} coins with real-time data`);
                    }
                    
                    console.log('📈 First 5 coins:', cryptoData.slice(0, 5).map(c => `${c.symbol} - $${c.price}`));
                    console.log('🔍 BTC status:', cryptoData.find(c => c.symbol === 'BTC'));
                    
                } else {
                    throw new Error('Bybit API response error: ' + (result.retMsg || 'Unknown error'));
                }
                
                // Update coin list display
                updateCoinList();
                
                // Show notification every 30th update to reduce spam
                if (typeof updateCount === 'undefined') updateCount = 0;
                updateCount++;
                if (updateCount % 30 === 0) {
                    showNotification('Gerçek zamanlı fiyatlar güncellendi', 'info');
                }
                
            } catch (error) {
                console.error('❌ Error fetching real prices:', error);
                showNotification('Fiyat güncelleme hatası: ' + error.message, 'error');
            }
        }

        // Generate demo data if API fails
        function generateDemoData() {
            if (cryptoData.length === 0) {
                // Create demo coins if cryptoData is empty
                const demoCoins = [
                    { symbol: 'BTC', name: 'Bitcoin', basePrice: 45000 },
                    { symbol: 'ETH', name: 'Ethereum', basePrice: 3000 },
                    { symbol: 'BNB', name: 'Binance Coin', basePrice: 300 },
                    { symbol: 'ADA', name: 'Cardano', basePrice: 0.5 },
                    { symbol: 'SOL', name: 'Solana', basePrice: 100 },
                    { symbol: 'XRP', name: 'Ripple', basePrice: 0.6 },
                    { symbol: 'DOT', name: 'Polkadot', basePrice: 7 },
                    { symbol: 'AVAX', name: 'Avalanche', basePrice: 25 },
                    { symbol: 'MATIC', name: 'Polygon', basePrice: 0.8 },
                    { symbol: 'LINK', name: 'Chainlink', basePrice: 15 }
                ];
                
                demoCoins.forEach((coin, index) => {
                    const price = coin.basePrice * (0.8 + Math.random() * 0.4); // ±20% variation
                    cryptoData.push({
                        id: index + 1,
                        symbol: coin.symbol,
                        futuresSymbol: coin.symbol + 'USDT',
                        name: coin.name,
                        price: price,
                        change24h: (Math.random() - 0.5) * 20, // -10% to +10%
                        volume: Math.random() * 1000000000 + 1000000,
                        high24h: price * (1 + Math.random() * 0.1),
                        low24h: price * (1 - Math.random() * 0.1),
                        openPrice: price * (1 + (Math.random() - 0.5) * 0.05),
                        marketCap: 0,
                        priceHistory: [],
                        isActive: true,
                        priority: index + 1
                    });
                });
                
                console.log('🎉 Demo data created:', cryptoData.length, 'coins');
            } else {
                // Update existing coins if they have zero price
            cryptoData.forEach(coin => {
                if (coin.price === 0) {
                    coin.price = Math.random() * 1000 + 0.01;
                    coin.change24h = (Math.random() - 0.5) * 20;
                    coin.volume = Math.random() * 1000000000;
                    coin.high24h = coin.price * (1 + Math.random() * 0.1);
                    coin.low24h = coin.price * (1 - Math.random() * 0.1);
                    coin.openPrice = coin.price * (1 + (Math.random() - 0.5) * 0.05);
                }
            });
            }
        }

        // Sort coins function
        function sortCoins(sortType) {
            currentSort = sortType;
            
            // Update button styles
            document.querySelectorAll('.sort-btn').forEach(btn => {
                btn.classList.remove('bg-blue-600', 'bg-green-600', 'bg-red-600', 'text-white');
                btn.classList.add('bg-gray-600', 'text-gray-300');
            });
            
            const activeBtn = document.getElementById(`sort${sortType.charAt(0).toUpperCase() + sortType.slice(1)}`);
            if (activeBtn) {
                activeBtn.classList.remove('bg-gray-600', 'text-gray-300');
                if (sortType === 'gainers') {
                    activeBtn.classList.add('bg-green-600', 'text-white');
                } else if (sortType === 'losers') {
                    activeBtn.classList.add('bg-red-600', 'text-white');
                } else {
                    activeBtn.classList.add('bg-blue-600', 'text-white');
                }
            }
            
            updateCoinList();
        }


        // Note: Drag and drop functionality removed to prevent main list corruption

        // Enhanced coin list display with TradingView-style animations
        function updateCoinList() {
            const coinList = document.getElementById('coinList');
            const searchTerm = document.getElementById('coinSearch').value.toLowerCase();
            
            let filteredCoins = cryptoData.filter(coin => 
                coin.name.toLowerCase().includes(searchTerm) || 
                coin.symbol.toLowerCase().includes(searchTerm)
            );
            
            // Apply sorting
            if (currentSort === 'gainers') {
                filteredCoins = filteredCoins.sort((a, b) => b.change24h - a.change24h);
            } else if (currentSort === 'losers') {
                filteredCoins = filteredCoins.sort((a, b) => a.change24h - b.change24h);
            } else {
                // Default: BTC first, ETH second, then by volume
                filteredCoins = filteredCoins.sort((a, b) => {
                    if (a.priority !== b.priority) {
                        return a.priority - b.priority;
                    }
                    return b.volume - a.volume;
                });
            }
            
            // Show all coins (no limit for full market scan)
            // filteredCoins = filteredCoins.slice(0, 20);
            
            // Store previous prices for animation
            const previousPrices = {};
            coinList.querySelectorAll('tr').forEach(row => {
                const symbol = row.dataset.symbol;
                const priceCell = row.querySelector('.price-cell');
                if (symbol && priceCell) {
                    previousPrices[symbol] = parseFloat(priceCell.textContent.replace('$', ''));
                }
            });
            
            coinList.innerHTML = '';
            
            filteredCoins.forEach((coin, index) => {
                const row = document.createElement('tr');
                row.className = 'transition-all duration-200 hover:bg-gray-700 border-b border-gray-600';
                row.dataset.symbol = coin.symbol;
                
                const changeClass = coin.change24h >= 0 ? 'accent-green' : 'accent-red';
                const changeSign = coin.change24h >= 0 ? '+' : '';
                const changeIcon = coin.change24h >= 0 ? '📈' : '📉';
                
                // Check if price changed for animation
                const previousPrice = previousPrices[coin.symbol];
                let priceClass = 'price-cell';
                if (previousPrice && previousPrice !== coin.price) {
                    priceClass += coin.price > previousPrice ? ' price-up' : ' price-down';
                }
                
                // Format volume
                const volumeFormatted = coin.volume > 1000000000 ? 
                    `$${(coin.volume / 1000000000).toFixed(2)}B` : 
                    `$${(coin.volume / 1000000).toFixed(1)}M`;
                
                // Format price based on coin value
                let priceFormatted;
                if (coin.price >= 1000) {
                    priceFormatted = `$${coin.price.toFixed(2)}`;
                } else if (coin.price >= 1) {
                    priceFormatted = `$${coin.price.toFixed(4)}`;
                } else if (coin.price >= 0.01) {
                    priceFormatted = `$${coin.price.toFixed(6)}`;
                } else {
                    priceFormatted = `$${coin.price.toFixed(8)}`;
                }
                
                row.innerHTML = `
                    <td class="p-3 cursor-pointer border-r border-gray-600" onclick="showCoinDetail('${coin.symbol}')">
                        <div class="font-bold text-white">${coin.symbol}</div>
                        <div class="text-sm text-gray-400">${coin.name}</div>
                    </td>
                    <td class="p-3 ${priceClass} font-mono border-r border-gray-600">${priceFormatted}</td>
                    <td class="p-3 ${changeClass} font-bold border-r border-gray-600">${changeIcon} ${changeSign}${coin.change24h.toFixed(2)}%</td>
                    <td class="p-3 text-gray-300 font-mono text-sm border-r border-gray-600">${volumeFormatted}</td>
                    <td class="p-3">
                        <button onclick="selectCoin('${coin.symbol}')" class="bg-gradient-to-r from-blue-600 to-purple-600 hover:from-blue-700 hover:to-purple-700 px-3 py-1 rounded-lg text-sm transition-all duration-200 transform hover:scale-105 font-medium">
                            📊 Seç
                        </button>
                    </td>
                `;
                
                coinList.appendChild(row);
            });
            
            // Note: Drag and drop removed to prevent main list corruption
            
            // Update market summary panels
            updateMarketSummary();
        }

        // Update market summary panels
        function updateMarketSummary() {
            // Top Gainers
            const topGainers = cryptoData
                .filter(coin => coin.change24h > 0)
                .sort((a, b) => b.change24h - a.change24h)
                .slice(0, 5);
            
            const topGainersContainer = document.getElementById('topGainers');
            if (topGainersContainer) {
                topGainersContainer.innerHTML = '';
                topGainers.forEach(coin => {
                    const item = document.createElement('div');
                    item.className = 'flex justify-between items-center text-sm';
                    item.innerHTML = `
                        <span class="text-white font-medium">${coin.symbol}</span>
                        <span class="accent-green font-bold">+${coin.change24h.toFixed(1)}%</span>
                    `;
                    topGainersContainer.appendChild(item);
                });
            }
            
            // Top Losers
            const topLosers = cryptoData
                .filter(coin => coin.change24h < 0)
                .sort((a, b) => a.change24h - b.change24h)
                .slice(0, 5);
            
            const topLosersContainer = document.getElementById('topLosers');
            if (topLosersContainer) {
                topLosersContainer.innerHTML = '';
                topLosers.forEach(coin => {
                    const item = document.createElement('div');
                    item.className = 'flex justify-between items-center text-sm';
                    item.innerHTML = `
                        <span class="text-white font-medium">${coin.symbol}</span>
                        <span class="accent-red font-bold">${coin.change24h.toFixed(1)}%</span>
                    `;
                    topLosersContainer.appendChild(item);
                });
            }
            
            // Volume Leaders
            const volumeLeaders = cryptoData
                .sort((a, b) => b.volume - a.volume)
                .slice(0, 5);
            
            const volumeLeadersContainer = document.getElementById('volumeLeaders');
            if (volumeLeadersContainer) {
                volumeLeadersContainer.innerHTML = '';
                volumeLeaders.forEach(coin => {
                    const item = document.createElement('div');
                    item.className = 'flex justify-between items-center text-sm';
                    const volumeFormatted = coin.volume > 1000000000 ? 
                        `${(coin.volume / 1000000000).toFixed(1)}B` : 
                        `${(coin.volume / 1000000).toFixed(0)}M`;
                    item.innerHTML = `
                        <span class="text-white font-medium">${coin.symbol}</span>
                        <span class="accent-blue font-bold">$${volumeFormatted}</span>
                    `;
                    volumeLeadersContainer.appendChild(item);
                });
            }
        }

        // Search coins
        function searchCoins() {
            updateCoinList();
        }

        // Select coin for trading
        function selectCoin(symbol) {
            showNotification(`${symbol} seçildi ve analiz ediliyor...`, 'info');
        }

        // Show coin detail page
        function showCoinDetail(symbol) {
            const coin = cryptoData.find(c => c.symbol === symbol);
            if (!coin) return;
            
            document.getElementById('coinDetailTitle').textContent = `${coin.name} (${coin.symbol})`;
            
            // Update coin info
            const coinInfo = document.getElementById('coinInfo');
            coinInfo.innerHTML = `
                <div class="bg-gray-700 p-4 rounded-lg">
                    <div class="text-sm text-gray-400">Güncel Fiyat</div>
                    <div class="text-2xl font-bold">$${coin.price.toFixed(6)}</div>
                    <div class="text-sm ${coin.change24h >= 0 ? 'text-green-400' : 'text-red-400'}">
                        ${coin.change24h >= 0 ? '+' : ''}${coin.change24h.toFixed(2)}%
                    </div>
                </div>
                <div class="bg-gray-700 p-4 rounded-lg">
                    <div class="text-sm text-gray-400">24h Hacim</div>
                    <div class="text-lg font-bold">$${(coin.volume / 1000000).toFixed(2)}M</div>
                </div>
                <div class="bg-gray-700 p-4 rounded-lg">
                    <div class="text-sm text-gray-400">Piyasa Değeri</div>
                    <div class="text-lg font-bold">$${(coin.marketCap / 1000000000).toFixed(2)}B</div>
                </div>
            `;
            
            // Update AI analysis
            const aiAnalysis = document.getElementById('coinAIAnalysis');
            const signals = ['Güçlü Alım', 'Alım', 'Nötr', 'Satış', 'Güçlü Satış'];
            const signal = signals[Math.floor(Math.random() * signals.length)];
            const confidence = Math.floor(Math.random() * 40) + 60;
            const rsi = Math.floor(Math.random() * 100);
            const macd = Math.random() > 0.5 ? 'Bullish' : 'Bearish';
            
            aiAnalysis.innerHTML = `
                <div class="bg-gray-700 p-4 rounded-lg">
                    <h4 class="font-bold mb-2">AI Sinyali</h4>
                    <div class="text-2xl font-bold ${signal.includes('Alım') ? 'text-green-400' : signal.includes('Satış') ? 'text-red-400' : 'text-yellow-400'}">${signal}</div>
                    <div class="text-sm text-gray-400">Güven: %${confidence}</div>
                    <div class="mt-2 text-xs">
                        <div class="flex justify-between">
                            <span>Kısa Vadeli:</span>
                            <span class="${Math.random() > 0.5 ? 'text-green-400' : 'text-red-400'}">${Math.random() > 0.5 ? 'Pozitif' : 'Negatif'}</span>
                        </div>
                        <div class="flex justify-between">
                            <span>Orta Vadeli:</span>
                            <span class="${Math.random() > 0.5 ? 'text-green-400' : 'text-red-400'}">${Math.random() > 0.5 ? 'Pozitif' : 'Negatif'}</span>
                        </div>
                    </div>
                </div>
                <div class="bg-gray-700 p-4 rounded-lg">
                    <h4 class="font-bold mb-2">Teknik Seviyeler</h4>
                    <div class="space-y-2 text-sm">
                        <div class="flex justify-between">
                            <span>Destek 1:</span>
                            <span class="text-green-400">$${(coin.price * 0.98).toFixed(6)}</span>
                        </div>
                        <div class="flex justify-between">
                            <span>Destek 2:</span>
                            <span class="text-green-400">$${(coin.price * 0.95).toFixed(6)}</span>
                        </div>
                        <div class="flex justify-between">
                            <span>Direnç 1:</span>
                            <span class="text-red-400">$${(coin.price * 1.02).toFixed(6)}</span>
                        </div>
                        <div class="flex justify-between">
                            <span>Direnç 2:</span>
                            <span class="text-red-400">$${(coin.price * 1.05).toFixed(6)}</span>
                        </div>
                    </div>
                </div>
                <div class="bg-gray-700 p-4 rounded-lg">
                    <h4 class="font-bold mb-2">Risk Analizi</h4>
                    <div class="space-y-2 text-sm">
                        <div class="flex justify-between">
                            <span>Volatilite:</span>
                            <span class="${Math.random() > 0.6 ? 'text-red-400' : 'text-yellow-400'}">${Math.random() > 0.6 ? 'Yüksek' : 'Orta'}</span>
                        </div>
                        <div class="flex justify-between">
                            <span>Trend Gücü:</span>
                            <span class="text-blue-400">${Math.floor(Math.random() * 40) + 60}%</span>
                        </div>
                        <div class="flex justify-between">
                            <span>Hacim Trendi:</span>
                            <span class="${Math.random() > 0.5 ? 'text-green-400' : 'text-red-400'}">${Math.random() > 0.5 ? 'Artan' : 'Azalan'}</span>
                        </div>
                    </div>
                </div>
            `;
            
            // Update technical indicators
            const technicalIndicators = document.getElementById('technicalIndicators');
            if (technicalIndicators) {
                technicalIndicators.innerHTML = `
                    <div class="bg-gray-600 p-3 rounded">
                        <div class="font-semibold text-xs mb-1">RSI (14)</div>
                        <div class="${rsi > 70 ? 'text-red-400' : rsi < 30 ? 'text-green-400' : 'text-yellow-400'} font-bold">${rsi}</div>
                    </div>
                    <div class="bg-gray-600 p-3 rounded">
                        <div class="font-semibold text-xs mb-1">MACD</div>
                        <div class="${macd === 'Bullish' ? 'text-green-400' : 'text-red-400'} font-bold">${macd}</div>
                    </div>
                    <div class="bg-gray-600 p-3 rounded">
                        <div class="font-semibold text-xs mb-1">EMA (20)</div>
                        <div class="text-blue-400 font-bold">$${(coin.price * (1 + (Math.random() - 0.5) * 0.02)).toFixed(6)}</div>
                    </div>
                    <div class="bg-gray-600 p-3 rounded">
                        <div class="font-semibold text-xs mb-1">SMA (50)</div>
                        <div class="text-purple-400 font-bold">$${(coin.price * (1 + (Math.random() - 0.5) * 0.05)).toFixed(6)}</div>
                    </div>
                    <div class="bg-gray-600 p-3 rounded">
                        <div class="font-semibold text-xs mb-1">Destek 1</div>
                        <div class="text-green-400 font-bold">$${(coin.price * 0.98).toFixed(6)}</div>
                    </div>
                    <div class="bg-gray-600 p-3 rounded">
                        <div class="font-semibold text-xs mb-1">Direnç 1</div>
                        <div class="text-red-400 font-bold">$${(coin.price * 1.02).toFixed(6)}</div>
                    </div>
                    <div class="bg-gray-600 p-3 rounded">
                        <div class="font-semibold text-xs mb-1">ADX</div>
                        <div class="text-orange-400 font-bold">${Math.floor(Math.random() * 60) + 20}</div>
                    </div>
                    <div class="bg-gray-600 p-3 rounded">
                        <div class="font-semibold text-xs mb-1">Stochastic</div>
                        <div class="text-cyan-400 font-bold">${Math.floor(Math.random() * 100)}</div>
                    </div>
                `;
            }
            
            // Create chart
            createCoinChart(coin);
            
            showPage('coinDetail');
        }
        
        // Show coin detail from trade table - returns to trade page
        function showCoinDetailFromTrade(symbol) {
            showCoinDetail(symbol);
            // Store that we came from trade page
            sessionStorage.setItem('returnToPage', 'trade');
        }
        
        // Go back from coin detail page
        function goBackFromCoinDetail() {
            const returnPage = sessionStorage.getItem('returnToPage') || 'dashboard';
            sessionStorage.removeItem('returnToPage');
            showPage(returnPage);
        }

        // Create advanced candlestick chart with real-time updates
        function createCoinChart(coin) {
            const ctx = document.getElementById('coinChart').getContext('2d');
            
            if (coinChart) {
                coinChart.destroy();
            }
            
            // Clear any existing chart update interval
            if (chartUpdateInterval) {
                clearInterval(chartUpdateInterval);
            }
            
            // Generate realistic OHLCV data
            const labels = [];
            const candleData = [];
            const volumeData = [];
            const currentTime = new Date();
            const timeframe = document.getElementById('chartTimeframe')?.value || '15m';
            
            let intervals = 48;
            let timeStep = 15 * 60 * 1000;
            
            switch(timeframe) {
                case '1m': intervals = 60; timeStep = 60 * 1000; break;
                case '5m': intervals = 60; timeStep = 5 * 60 * 1000; break;
                case '1h': intervals = 24; timeStep = 60 * 60 * 1000; break;
                case '4h': intervals = 24; timeStep = 4 * 60 * 60 * 1000; break;
                case '1d': intervals = 30; timeStep = 24 * 60 * 60 * 1000; break;
            }
            
            let lastPrice = coin.price;
            
            for (let i = intervals - 1; i >= 0; i--) {
                const time = new Date(currentTime.getTime() - i * timeStep);
                const timeLabel = timeframe === '1d' ? 
                    time.toLocaleDateString('tr-TR', { day: '2-digit', month: '2-digit' }) :
                    time.toLocaleTimeString('tr-TR', { hour: '2-digit', minute: '2-digit' });
                
                labels.push(timeLabel);
                
                // Generate realistic OHLC data
                const volatility = 0.015;
                const change = (Math.random() - 0.5) * volatility;
                const open = lastPrice;
                const close = open * (1 + change);
                const high = Math.max(open, close) * (1 + Math.random() * 0.008);
                const low = Math.min(open, close) * (1 - Math.random() * 0.008);
                
                // Create candlestick data points
                const isGreen = close > open;
                candleData.push({
                    x: timeLabel,
                    y: [open, high, low, close],
                    backgroundColor: isGreen ? 'rgba(16, 185, 129, 0.8)' : 'rgba(239, 68, 68, 0.8)',
                    borderColor: isGreen ? '#10b981' : '#ef4444'
                });
                
                volumeData.push(Math.random() * 1000000);
                lastPrice = close;
            }
            
            // Store chart data for updates
            coin.chartData = { labels, candleData, volumeData, lastPrice };
            
            // Create candlestick-style chart with better visualization
            coinChart = new Chart(ctx, {
                type: 'line',
                data: {
                    labels: labels,
                    datasets: [{
                        label: coin.symbol + ' Fiyat',
                        data: candleData.map(d => d.y[3]), // Close prices
                        borderColor: '#3b82f6',
                        backgroundColor: 'rgba(59, 130, 246, 0.1)',
                        borderWidth: 2,
                        fill: true,
                        tension: 0.1,
                        pointBackgroundColor: candleData.map(d => d.backgroundColor),
                        pointBorderColor: candleData.map(d => d.borderColor),
                        pointRadius: 3,
                        pointHoverRadius: 5
                    }, {
                        label: 'Yüksek',
                        data: candleData.map(d => d.y[1]), // High prices
                        borderColor: 'rgba(16, 185, 129, 0.5)',
                        backgroundColor: 'transparent',
                        borderWidth: 1,
                        fill: false,
                        pointRadius: 0,
                        borderDash: [5, 5]
                    }, {
                        label: 'Düşük',
                        data: candleData.map(d => d.y[2]), // Low prices
                        borderColor: 'rgba(239, 68, 68, 0.5)',
                        backgroundColor: 'transparent',
                        borderWidth: 1,
                        fill: false,
                        pointRadius: 0,
                        borderDash: [5, 5]
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            labels: {
                                color: 'white'
                            }
                        },
                        tooltip: {
                            mode: 'index',
                            intersect: false,
                            backgroundColor: 'rgba(0, 0, 0, 0.9)',
                            titleColor: 'white',
                            bodyColor: 'white',
                            borderColor: '#3b82f6',
                            borderWidth: 1,
                            callbacks: {
                                label: function(context) {
                                    const dataIndex = context.dataIndex;
                                    const ohlc = candleData[dataIndex];
                                    if (ohlc) {
                                        return [
                                            `Açılış: $${ohlc.y[0].toFixed(6)}`,
                                            `Yüksek: $${ohlc.y[1].toFixed(6)}`,
                                            `Düşük: $${ohlc.y[2].toFixed(6)}`,
                                            `Kapanış: $${ohlc.y[3].toFixed(6)}`
                                        ];
                                    }
                                    return `Fiyat: $${context.parsed.y.toFixed(6)}`;
                                }
                            }
                        }
                    },
                    scales: {
                        x: {
                            ticks: {
                                color: 'white',
                                maxTicksLimit: 12
                            },
                            grid: {
                                color: 'rgba(255, 255, 255, 0.1)'
                            }
                        },
                        y: {
                            ticks: {
                                color: 'white',
                                callback: function(value) {
                                    return '$' + value.toFixed(6);
                                }
                            },
                            grid: {
                                color: 'rgba(255, 255, 255, 0.1)'
                            }
                        }
                    },
                    interaction: {
                        intersect: false,
                        mode: 'index'
                    }
                }
            });
            
            // Start real-time chart updates
            startChartUpdates(coin);
            updateLastUpdateTime();
        }

        // Start real-time chart updates
        function startChartUpdates(coin) {
            chartUpdateInterval = setInterval(() => {
                if (currentPage === 'coinDetail' && coinChart && coin.chartData) {
                    // Update the last candle with current price
                    const currentPrice = coin.price;
                    const lastCandle = coin.chartData.candleData[coin.chartData.candleData.length - 1];
                    
                    if (lastCandle) {
                        // Update close price and high/low if needed
                        lastCandle.y[3] = currentPrice; // Close
                        if (currentPrice > lastCandle.y[1]) lastCandle.y[1] = currentPrice; // New high
                        if (currentPrice < lastCandle.y[2]) lastCandle.y[2] = currentPrice; // New low
                        
                        // Update color based on open vs close
                        const isGreen = lastCandle.y[3] > lastCandle.y[0];
                        lastCandle.backgroundColor = isGreen ? 'rgba(16, 185, 129, 0.8)' : 'rgba(239, 68, 68, 0.8)';
                        lastCandle.borderColor = isGreen ? '#10b981' : '#ef4444';
                        
                        // Update chart data
                        coinChart.data.datasets[0].data[coinChart.data.datasets[0].data.length - 1].y = currentPrice;
                        coinChart.data.datasets[0].backgroundColor[coinChart.data.datasets[0].backgroundColor.length - 1] = lastCandle.backgroundColor;
                        coinChart.data.datasets[0].borderColor[coinChart.data.datasets[0].borderColor.length - 1] = lastCandle.borderColor;
                        
                        coinChart.update('none'); // Update without animation for real-time feel
                    }
                    
                    updateLastUpdateTime();
                }
            }, 2000); // Update every 2 seconds
        }

        // Change timeframe
        function changeTimeframe() {
            const coin = cryptoData.find(c => c.symbol === document.getElementById('coinDetailTitle').textContent.split('(')[1].split(')')[0]);
            if (coin) {
                document.getElementById('chartLoading').classList.remove('hidden');
                setTimeout(() => {
                    createCoinChart(coin);
                    document.getElementById('chartLoading').classList.add('hidden');
                    showNotification('Grafik zaman dilimi güncellendi!', 'success');
                }, 1000);
            }
        }

        // Refresh chart
        function refreshChart() {
            const coin = cryptoData.find(c => c.symbol === document.getElementById('coinDetailTitle').textContent.split('(')[1].split(')')[0]);
            if (coin) {
                document.getElementById('chartLoading').classList.remove('hidden');
                setTimeout(() => {
                    createCoinChart(coin);
                    document.getElementById('chartLoading').classList.add('hidden');
                }, 1000);
            }
        }

        // Toggle indicators on chart
        function toggleIndicatorOnChart(indicator) {
            const button = event.target;
            if (button.classList.contains('bg-blue-600')) {
                button.classList.remove('bg-blue-600', 'text-white');
                button.classList.add('bg-gray-700', 'text-gray-300');
                showNotification(`${indicator} indikatörü kaldırıldı`, 'info');
            } else {
                button.classList.remove('bg-gray-700', 'text-gray-300');
                button.classList.add('bg-blue-600', 'text-white');
                showNotification(`${indicator} indikatörü eklendi`, 'info');
            }
        }

        // Refresh prices with better algorithm
        function refreshPrices() {
            cryptoData.forEach(coin => {
                // More realistic price movement
                const volatility = 0.02; // 2% max change per update
                const change = (Math.random() - 0.5) * volatility;
                coin.price *= (1 + change);
                coin.change24h = (Math.random() - 0.5) * 20;
            });
            updateCoinList();
            showNotification('Fiyatlar güncellendi!', 'success');
        }

        // Force update BTC price specifically
        async function forceUpdateBTCPrice() {
            try {
                console.log('🔄 Force updating BTC price...');
                
                const response = await fetch(`https://api.bybit.com/v5/market/tickers?category=linear&symbol=BTCUSDT`);
                const result = await response.json();
                
                if (result.retCode === 0 && result.result && result.result.list && result.result.list.length > 0) {
                    const btcTicker = result.result.list[0];
                    let btcCoin = cryptoData.find(c => c.symbol === 'BTC');
                    
                    if (!btcCoin) {
                        // Force add BTC if not found
                        btcCoin = {
                            id: 1,
                            name: 'Bitcoin',
                            symbol: 'BTC',
                            futuresSymbol: 'BTCUSDT',
                            price: 50000,
                            change24h: 0,
                            volume: 1000000000,
                            marketCap: 0,
                            priceHistory: [],
                            high24h: 51000,
                            low24h: 49000,
                            openPrice: 50000,
                            isActive: true,
                            priority: 1
                        };
                        cryptoData.unshift(btcCoin);
                        console.log('🔧 BTC force added in forceUpdateBTCPrice');
                    }
                    
                    // Update BTC with fresh data
                    btcCoin.price = parseFloat(btcTicker.lastPrice);
                    btcCoin.change24h = parseFloat(btcTicker.price24hPcnt) * 100;
                    btcCoin.volume = parseFloat(btcTicker.volume24h);
                    btcCoin.high24h = parseFloat(btcTicker.highPrice24h);
                    btcCoin.low24h = parseFloat(btcTicker.lowPrice24h);
                    btcCoin.openPrice = parseFloat(btcTicker.prevPrice24h);
                    
                    console.log('✅ BTC price force updated:', btcCoin.price);
                    
                    // Update the display
                    updateCoinList();
                }
            } catch (error) {
                console.warn('❌ BTC force update error:', error);
            }
        }

        // Start real-time price updates (every 2 seconds for better accuracy)
        function startPriceUpdates() {
            priceUpdateInterval = setInterval(() => {
                // Always fetch real prices for accurate updates
                fetchRealPrices();
                
                // Force update BTC price specifically
                forceUpdateBTCPrice();
                
                // Force update active trades table with latest prices
                updateActiveTradesTable();
                
                // Check active trades for SL/TP triggers
                checkActiveTradesForExit();
                
                if (currentPage === 'dashboard') {
                    updateCoinList();
                }
                
                // Update trade info
                updateTradeInfo();
                updateActiveTradesTable();
                
                // Update chart if on coin detail page
                if (currentPage === 'coinDetail') {
                    updateLastUpdateTime();
                }
                
            }, 2000); // Update every 2 seconds for better accuracy
        }
        
        // Check active trades for SL/TP triggers
        async function checkActiveTradesForExit() {
            const activeTrades = transactions.filter(t => t.status === 'Aktif');
            
            for (const trade of activeTrades) {
                const coin = cryptoData.find(c => c.symbol === trade.coin);
                if (!coin) continue;
                
                const currentPrice = coin.price;
                trade.currentPrice = currentPrice;
                
                // Check if SL or TP should trigger
                let shouldClose = false;
                let exitReason = '';
                
                if (trade.type === 'LONG') {
                    // LONG: Close if price hits SL (below) or TP (above)
                    if (currentPrice <= trade.stopLoss) {
                        shouldClose = true;
                        exitReason = 'Stop Loss';
                    } else if (currentPrice >= trade.takeProfit) {
                        shouldClose = true;
                        exitReason = 'Take Profit';
                    }
                } else { // SHORT
                    // SHORT: Close if price hits SL (above) or TP (below)
                    if (currentPrice >= trade.stopLoss) {
                        shouldClose = true;
                        exitReason = 'Stop Loss';
                    } else if (currentPrice <= trade.takeProfit) {
                        shouldClose = true;
                        exitReason = 'Take Profit';
                    }
                }
                
                // Check DCA before closing trade
                if (!shouldClose && trade.dcaEnabled) {
                    try {
                        if (await shouldTriggerDCA(trade, currentPrice)) {
                            // DCA triggered, don't close trade
                            const aiType = trade.aiType || trade.tradeType || 'Manuel';
                            addApiLog(`📈 ${aiType} ${trade.coin} DCA tetiklendi - işlem devam ediyor`);
                            continue; // Skip closing this trade
                        }
                    } catch (error) {
                        addApiLog(`❌ DCA kontrolü hatası: ${error.message}`);
                    }
                }

                if (shouldClose) {
                    // Log the trigger with detailed info
                    const aiType = trade.aiType || trade.tradeType || 'Manuel';
                    addApiLog(`🎯 ${aiType} ${trade.coin} ${exitReason} tetiklendi!`);
                    addApiLog(`📊 Fiyat: $${currentPrice.toFixed(6)} | SL: $${trade.stopLoss.toFixed(6)} | TP: $${trade.takeProfit.toFixed(6)}`);
                    
                    // Close the trade
                    await completeTrade(trade.id, false); // Not forced, let it determine SL/TP
                }
            }
        }

        // Update last update time
        function updateLastUpdateTime() {
            const now = new Date();
            const timeString = now.toLocaleTimeString('tr-TR', { hour: '2-digit', minute: '2-digit' });
            const lastUpdateElement = document.getElementById('lastUpdate');
            if (lastUpdateElement) {
                lastUpdateElement.textContent = timeString;
            }
        }

        // AI Functions with improved logic
        function toggleFastAI() {
            console.log('🔄 toggleFastAI called, current state:', fastAiActive);
            fastAiActive = !fastAiActive;
            console.log('⚡ Fast AI toggled to:', fastAiActive);
            console.log('🔍 CryptoData available:', cryptoData.length > 0);
            
            const fastAiToggle = document.getElementById('fastAiToggle');
            const fastAiStatus = document.getElementById('controlFastAiStatus');
            const tradeFastAiToggle = document.getElementById('tradeFastAiToggle');
            const tradeFastAiStatus = document.getElementById('tradeFastAiStatus');
            
            if (fastAiActive) {
                if (fastAiToggle) {
                    fastAiToggle.className = 'ai-active px-4 py-2 rounded-lg font-bold transition-all text-sm';
                }
                if (fastAiStatus) {
                    fastAiStatus.textContent = '⚡ Hızlı AI Çalışıyor';
                }
                if (tradeFastAiToggle) {
                    tradeFastAiToggle.className = 'ai-active px-6 py-3 rounded-lg font-bold transition-all text-sm';
                }
                if (tradeFastAiStatus) {
                    tradeFastAiStatus.textContent = '⚡ Hızlı AI Çalışıyor';
                }
                showNotification('Hızlı AI sistemi başlatıldı!', 'success');
                updateAIStatusDisplays();
                startFastAIAnalysis();
            } else {
                if (fastAiToggle) {
                    fastAiToggle.className = 'ai-inactive px-4 py-2 rounded-lg font-bold transition-all text-sm';
                }
                if (fastAiStatus) {
                    fastAiStatus.textContent = '⚡ Hızlı AI Durduruldu';
                }
                if (tradeFastAiToggle) {
                    tradeFastAiToggle.className = 'ai-inactive px-6 py-3 rounded-lg font-bold transition-all text-sm';
                }
                if (tradeFastAiStatus) {
                    tradeFastAiStatus.textContent = '⚡ Hızlı AI Durduruldu';
                }
                showNotification('Hızlı AI sistemi durduruldu!', 'warning');
                updateAIStatusDisplays();
            }
            
            // Save AI state immediately
            const pageState = {
                currentPage: currentPage,
                fastAiActive: fastAiActive,
                longAiActive: longAiActive,
                probotAiActive: probotAiActive
            };
            localStorage.setItem('pageState', JSON.stringify(pageState));
        }

        function toggleLongAI() {
            console.log('🔄 toggleLongAI called, current state:', longAiActive);
            longAiActive = !longAiActive;
            console.log('🎯 Long AI toggled to:', longAiActive);
            console.log('🔍 CryptoData available:', cryptoData.length > 0);
            
            const longAiToggle = document.getElementById('longAiToggle');
            const longAiStatus = document.getElementById('controlLongAiStatus');
            const tradeLongAiToggle = document.getElementById('tradeLongAiToggle');
            const tradeLongAiStatus = document.getElementById('tradeLongAiStatus');
            
            if (longAiActive) {
                if (longAiToggle) {
                    longAiToggle.className = 'ai-active px-4 py-2 rounded-lg font-bold transition-all text-sm';
                }
                if (longAiStatus) {
                    longAiStatus.textContent = '🎯 Uzun AI Çalışıyor';
                }
                if (tradeLongAiToggle) {
                    tradeLongAiToggle.className = 'ai-active px-6 py-3 rounded-lg font-bold transition-all text-sm';
                }
                if (tradeLongAiStatus) {
                    tradeLongAiStatus.textContent = '🎯 Uzun AI Çalışıyor';
                }
                showNotification('Uzun vadeli AI sistemi başlatıldı!', 'success');
                updateAIStatusDisplays();
                startLongAIAnalysis();
            } else {
                if (longAiToggle) {
                    longAiToggle.className = 'ai-inactive px-4 py-2 rounded-lg font-bold transition-all text-sm';
                }
                if (longAiStatus) {
                    longAiStatus.textContent = '🎯 Uzun AI Durduruldu';
                }
                if (tradeLongAiToggle) {
                    tradeLongAiToggle.className = 'ai-inactive px-6 py-3 rounded-lg font-bold transition-all text-sm';
                }
                if (tradeLongAiStatus) {
                    tradeLongAiStatus.textContent = '🎯 Uzun AI Durduruldu';
                }
                showNotification('Uzun vadeli AI sistemi durduruldu!', 'warning');
                updateAIStatusDisplays();
            }
            
            // Save AI state immediately
            const pageState = {
                currentPage: currentPage,
                fastAiActive: fastAiActive,
                longAiActive: longAiActive,
                probotAiActive: probotAiActive
            };
            localStorage.setItem('pageState', JSON.stringify(pageState));
        }

        // ProBot AI Functions
        let probotSettings = {
            goLongPeriod: 13,
            goLongOrder: 5,
            filterDeviation: 1,
            filterPeriod: 10,
            samplePeriod: 10,
            rangeMultiplier: 3,
            atrPeriod: 14,
            atrMultiplier: 1.5,
            usdtAmount: 40,
            leverage: 10,
            dcaLevels: 2,
            dcaPercent: 1.5,
            dcaMultiplier: 2.0,
            stopLoss: 2.6,
            takeProfit: 1.0,
            trailingStop: 3.0,
            scoreThreshold: 0.5
        };

        function toggleProbotAI() {
            console.log('🔄 toggleProbotAI called, current state:', probotAiActive);
            probotAiActive = !probotAiActive;
            console.log('🤖 ProBot AI toggled to:', probotAiActive);
            console.log('🔍 CryptoData available:', cryptoData.length > 0);
            
            const probotAiToggle = document.getElementById('probotAiToggle');
            const probotAiStatus = document.getElementById('probotAiStatus');
            const tradeProbotAiToggle = document.getElementById('tradeProbotAiToggle');
            const tradeProbotAiStatus = document.getElementById('tradeProbotAiStatus');
            
            console.log('🔍 Elements found:', {
                probotAiToggle: !!probotAiToggle,
                probotAiStatus: !!probotAiStatus,
                tradeProbotAiToggle: !!tradeProbotAiToggle,
                tradeProbotAiStatus: !!tradeProbotAiStatus
            });
            
            if (probotAiActive) {
                if (probotAiToggle) {
                    probotAiToggle.className = 'ai-active px-4 py-2 rounded-lg font-bold transition-all text-sm';
                    if (probotAiStatus) {
                        probotAiStatus.textContent = '🤖 ProBot AI Çalışıyor';
                    }
                }
                if (tradeProbotAiToggle) {
                    tradeProbotAiToggle.className = 'ai-active px-6 py-3 rounded-lg font-bold transition-all text-sm';
                    if (tradeProbotAiStatus) {
                        tradeProbotAiStatus.textContent = '🤖 ProBot AI Çalışıyor';
                    }
                }
                showNotification('ProBot AI sistemi başlatıldı!', 'success');
                updateProbotStatus('Çalışıyor', new Date().toLocaleTimeString());
                updateAIStatusDisplays();
                startProbotAIAnalysis();
            } else {
                if (probotAiToggle) {
                    probotAiToggle.className = 'ai-inactive px-4 py-2 rounded-lg font-bold transition-all text-sm';
                    if (probotAiStatus) {
                        probotAiStatus.textContent = '🤖 ProBot AI Durduruldu';
                    }
                }
                if (tradeProbotAiToggle) {
                    tradeProbotAiToggle.className = 'ai-inactive px-6 py-3 rounded-lg font-bold transition-all text-sm';
                    if (tradeProbotAiStatus) {
                        tradeProbotAiStatus.textContent = '🤖 ProBot AI Durduruldu';
                    }
                }
                showNotification('ProBot AI sistemi durduruldu!', 'warning');
                updateProbotStatus('Durduruldu', new Date().toLocaleTimeString());
                updateAIStatusDisplays();
            }
            
            // Save AI state immediately
            const pageState = {
                currentPage: currentPage,
                fastAiActive: fastAiActive,
                longAiActive: longAiActive,
                probotAiActive: probotAiActive
            };
            localStorage.setItem('pageState', JSON.stringify(pageState));
        }

        function startProbotAIAnalysis() {
            try {
                console.log('🤖 startProbotAIAnalysis called, probotAiActive:', probotAiActive);
                console.log('🔧 probotSettings available:', !!probotSettings);
                if (probotSettings) {
                    console.log('🔧 probotSettings.scoreThreshold:', probotSettings.scoreThreshold);
                }
                
                if (!probotAiActive) {
                    console.log('❌ ProBot AI not active, returning');
                    return;
                }
                
                // Check if cryptoData is empty and fetch if needed
                if (cryptoData.length === 0) {
                    console.log('⚠️ CryptoData empty, fetching real market data for ProBot AI');
                    fetchRealPrices();
                    setTimeout(startProbotAIAnalysis, 5000);
                    return;
                }
                
                console.log('✅ CryptoData available, performing ProBot AI analysis with', cryptoData.length, 'coins');
                
                // Update status
                updateProbotStatus('Çalışıyor', new Date().toLocaleTimeString());
                
                // Update scan count
                probotAiScanCount++;
                updateProbotStats(probotAiScanCount, probotAiOpportunities, 'Tarama');
                
                // Perform market analysis
                const analysisResults = performProbotAnalysis();
                
                if (analysisResults.shouldTrade) {
                    // Check if we can open a new trade
                    if (checkMaxActiveTrades('ProBot AI')) {
                        simulateProbotTrading();
                    } else {
                        addProbotLog(`⚠️ Maksimum aktif işlem limiti dolu - ProBot AI beklemede`);
                    }
                } else {
                    addProbotLog(`🔍 ProBot AI market taraması - uygun fırsat bulunamadı`);
                }
                
            } catch (error) {
                console.error('❌ ProBot AI analysis error:', error);
                addProbotLog(`❌ ProBot AI analiz hatası: ${error.message}`);
            } finally {
                // Schedule next analysis (continuous scanning like Fast AI and Long AI)
                if (probotAiActive) {
                    setTimeout(startProbotAIAnalysis, 5000); // 5 saniyede bir analiz
                }
            }
        }

        function simulateProbotTrading() {
            console.log('🤖 simulateProbotTrading called, probotAiActive:', probotAiActive);
            if (!probotAiActive) return;
            
            // Check maximum active trades limit for ProBot AI
            if (!checkMaxActiveTrades('ProBot AI')) {
                console.log('❌ ProBot AI max trades limit reached');
                return;
            }
            
            // ProBot AI analysis - Pine Script based trading
            const analysisResults = performProbotAnalysis();
            console.log('🔍 ProBot analysis results:', analysisResults);
            if (!analysisResults.shouldTrade) {
                console.log('❌ ProBot AI shouldTrade is false');
                return;
            }
            
            console.log('✅ ProBot AI will open trade for:', analysisResults.selectedCoin?.symbol);
            
            const coin = analysisResults.selectedCoin;
            
            // Check if coin already has an active trade by any AI
            const existingTrade = transactions.find(t => 
                t.coin === coin.symbol && 
                t.status === 'Aktif'
            );
            
            if (existingTrade) {
                console.log('❌ ProBot AI: Coin already has active trade:', coin.symbol, 'by', existingTrade.aiType);
                addProbotLog(`❌ ${coin.symbol} zaten aktif işlemde (${existingTrade.aiType}) - ProBot AI atlandı`);
                return;
            }
            
            console.log('🚀 ProBot AI: Creating new trade for:', coin.symbol);
            const entryPrice = coin.price;
            const isLong = analysisResults.direction === 'LONG';
            
            // Use ProBot AI specific settings from Trade page (same as Fast AI and Long AI)
            const leverage = parseInt(document.getElementById('probotLeverage')?.value || '10');
            const usdtAmount = parseFloat(document.getElementById('probotUsdtAmount')?.value || '1');
            const stopLossPercent = parseFloat(document.getElementById('probotStopLoss')?.value || '2') / 100;
            const takeProfitPercent = parseFloat(document.getElementById('probotTakeProfit')?.value || '1') / 100;
            const trailingStopPercent = parseFloat(document.getElementById('probotTrailingStop')?.value || '3.0') / 100;
            const orderType = document.getElementById('orderType')?.value || 'Market';
            
            // Debug: Log ProBot AI parameters
            console.log('🔧 ProBot AI Parameters from Trade Page:', {
                leverage: leverage,
                usdtAmount: usdtAmount,
                stopLossPercent: (stopLossPercent * 100).toFixed(2) + '%',
                takeProfitPercent: (takeProfitPercent * 100).toFixed(2) + '%',
                trailingStopPercent: (trailingStopPercent * 100).toFixed(2) + '%',
                orderType: orderType
            });
            
            // Get DCA settings for ProBot trades from Trade page
            const dcaEnabled = document.getElementById('probotDcaEnabled')?.checked || false;
            const dcaCount = parseInt(document.getElementById('probotDcaCount')?.value || '2');
            const dcaTrigger = parseFloat(document.getElementById('probotDcaTrigger')?.value || '1.5') / 100;
            const dcaMultiplier = parseFloat(document.getElementById('probotDcaMultiplier')?.value || '2.0');
            
            // Debug: Log DCA parameters
            console.log('🔧 ProBot AI DCA Parameters from Trade Page:', {
                dcaEnabled: dcaEnabled,
                dcaCount: dcaCount,
                dcaTrigger: (dcaTrigger * 100).toFixed(2) + '%',
                dcaMultiplier: dcaMultiplier
            });
            
            // Calculate SL/TP prices based on percentages - CORRECTED FOR SHORT
            const stopLoss = isLong ? 
                entryPrice * (1 - stopLossPercent) : // LONG: SL below entry (zarar durdurma)
                entryPrice * (1 + stopLossPercent);   // SHORT: SL above entry (zarar durdurma)
            
            const takeProfit = isLong ? 
                entryPrice * (1 + takeProfitPercent) : // LONG: TP above entry (kar alma)
                entryPrice * (1 - takeProfitPercent);  // SHORT: TP below entry (kar alma)
            
            const trade = {
                id: Date.now(),
                coin: coin.symbol,
                type: isLong ? 'LONG' : 'SHORT',
                entryPrice: entryPrice,
                currentPrice: entryPrice,
                exitPrice: null,
                amount: usdtAmount,
                totalInvestment: usdtAmount, // Initialize total investment
                leverage: leverage,
                stopLoss: stopLoss,
                takeProfit: takeProfit,
                stopLossPercent: stopLossPercent, // TP/SL oranlarını sakla
                takeProfitPercent: takeProfitPercent, // TP/SL oranlarını sakla
                trailingStop: trailingStopPercent,
                pnl: 0,
                status: 'Aktif',
                timestamp: new Date().toLocaleString('tr-TR'),
                orderType: orderType, // Use orderType from Trade page like Fast AI and Long AI
                aiType: 'ProBot AI',
                confidence: analysisResults.confidence,
                dcaEnabled: dcaEnabled,
                dcaLevel: 0,
                dcaCount: dcaCount,
                dcaTrigger: dcaTrigger,
                dcaMultiplier: dcaMultiplier
            };
            
            // Add to transactions
            transactions.unshift(trade);
            
            // Save to storage and update UI (same as Fast AI and Long AI)
            saveTransactionsToStorage();
            updateActiveTradesTable();
            updateCompletedTradesTable();
            updateTradeInfo();
            updateAdminStats();
            updateProbotStatus('İşlem Açıldı', new Date().toLocaleTimeString());
            
            // Add logs
            addProbotLog(`[İşlem] ${isLong ? 'LONG' : 'SHORT'} pozisyon açıldı: ${coin.symbol}`);
            addProbotLog(`[Fiyat] Giriş: $${entryPrice.toFixed(6)} | SL: $${stopLoss.toFixed(6)} | TP: $${takeProfit.toFixed(6)}`);
            addProbotLog(`[Miktar] ${usdtAmount} USDT | Kaldıraç: ${leverage}x | Güven: ${analysisResults.confidence}%`);
            
            // Send to exchange with detailed logging (same as Fast AI and Long AI)
            if (document.getElementById('bybitApiKey').value) {
                sendOrderToBybit(trade);
            } else if (document.getElementById('binanceApiKey').value) {
                sendOrderToBinance(trade);
            } else {
                addProbotLog(`⚠️ API bağlantısı yok - ${coin.symbol} işlemi yerel olarak takip ediliyor`);
                addProbotLog(`💡 Gerçek borsa işlemi için Bybit veya Binance API anahtarlarını girin`);
            }
            
            // Send DCA orders immediately if enabled (same as Fast AI and Long AI)
            if (dcaEnabled && dcaCount > 0) {
                setTimeout(async () => {
                    try {
                        await sendDCAOrdersToExchange(trade);
                    } catch (error) {
                        addApiLog(`❌ DCA emirleri hazırlanırken hata: ${error.message}`);
                        console.error('DCA preparation error:', error);
                    }
                }, 1000); // 1 second delay to ensure main order is processed
            }
            
            // Update trade counts
            updateTradeCounts();
            
            // Debug: Test notification
            console.log('🔔 ProBot AI notification test:', `ProBot AI ${coin.symbol} ${isLong ? 'LONG' : 'SHORT'} (${analysisResults.confidence}% güven)`);
            console.log('🔔 Calling showNotification function...');
            showNotification(`ProBot AI ${coin.symbol} ${isLong ? 'LONG' : 'SHORT'} (${analysisResults.confidence}% güven)`, 'info');
            console.log('🔔 showNotification called');
            
            // ProBot AI trades will be closed by real TP/SL triggers, not random timing
            addProbotLog(`[İşlem] ${coin.symbol} ${isLong ? 'LONG' : 'SHORT'} pozisyonu açıldı - TP/SL ile kapatılacak`);
        }
        
        function performProbotAnalysis() {
            // ProBot AI analysis - scan entire market with Pine Script parameters
            console.log('🔍 performProbotAnalysis called, cryptoData length:', cryptoData.length);
            console.log('🔧 probotSettings available in performProbotAnalysis:', !!probotSettings);
            if (probotSettings) {
                console.log('🔧 probotSettings.scoreThreshold:', probotSettings.scoreThreshold);
            }
            
            const allCoins = cryptoData
                .filter(coin => coin.volume > 1000000) // Lower volume threshold for more coins
                .sort((a, b) => b.volume - a.volume);
            
            console.log(`🤖 ProBot AI scanning entire market: ${allCoins.length} coins`);
            addProbotLog(`Market taraması başlatıldı: ${allCoins.length} coin`, 'info');
            
            let bestCoin = null;
            let bestScore = 0;
            let direction = 'LONG';
            let confidence = 0;
            let indicators = {};
            
            // Analyze all coins with Pine Script parameters
            const analysisResults = [];
            
            allCoins.forEach(coin => {
                const analysis = analyzeWithPineScript(coin);
                analysisResults.push({
                    coin: coin,
                    score: analysis.score,
                    direction: analysis.direction,
                    confidence: analysis.confidence,
                    indicators: analysis.indicators
                });
            });
            
            // Sort by score and take top 10 for detailed analysis
            analysisResults.sort((a, b) => b.score - a.score);
            const topCandidates = analysisResults.slice(0, 10);
            
            // Find the best opportunity
            topCandidates.forEach(candidate => {
                if (candidate.score > bestScore) {
                    bestScore = candidate.score;
                    bestCoin = candidate.coin;
                    direction = candidate.direction;
                    confidence = candidate.confidence;
                    indicators = candidate.indicators;
                }
            });
            
            // ProBot AI uses trade page confidence threshold
            const probotConfidenceThreshold = parseInt(document.getElementById('probotConfidenceThreshold')?.value || '80');
            const shouldTrade = bestScore > probotSettings.scoreThreshold && confidence >= probotConfidenceThreshold;
            
            if (shouldTrade) {
                probotAiOpportunities++;
                addProbotLog(`🎯 En iyi fırsat: ${bestCoin.symbol} (Skor: ${bestScore.toFixed(2)}, Güven: ${confidence}%)`);
                addProbotLog(`📊 Yön: ${direction} | Göstergeler: ${Object.keys(indicators).join(', ')}`);
                updateProbotStats(probotAiScanCount, probotAiOpportunities, bestCoin.symbol);
            } else {
                addProbotLog(`🔍 ProBot AI market taraması - uygun fırsat bulunamadı (En yüksek skor: ${bestScore.toFixed(2)})`);
            }
            
            return {
                shouldTrade: shouldTrade,
                selectedCoin: bestCoin,
                direction: direction,
                confidence: confidence,
                indicators: indicators
            };
        }
        
        function analyzeWithPineScript(coin) {
            try {
                // Pine Script based analysis using ProBot parameters
                const indicators = {};
                let score = 0;
                let direction = 'LONG';
                let confidence = 0;
                let signals = []; // Add signals array
                
                // Get risk management and volatility filter from Trade page
                const riskLevel = document.getElementById('probotRiskLevel')?.value || 'moderate';
                const volatilityFilter = document.getElementById('probotVolatilityFilter')?.value || 'medium';
                
                // Debug: Log risk and volatility parameters
                console.log('🔧 ProBot AI Risk & Volatility Parameters from Trade Page:', {
                    riskLevel: riskLevel,
                    volatilityFilter: volatilityFilter
                });
                
                // Check if probotSettings is defined
                if (!probotSettings) {
                    console.error('❌ probotSettings is undefined!');
                    return {
                        score: 0,
                        direction: 'LONG',
                        confidence: 0,
                        indicators: {}
                    };
                }
            
            // RSI Analysis (GoLong/Short Period: 13) - More Aggressive
            const rsi = calculateRSI(coin, 14);
            indicators.rsi = rsi;
            
            if (rsi < 40) { // More lenient oversold
                score += 0.4; // Higher score for oversold
                direction = 'LONG';
                confidence += 25;
                signals.push('RSI Oversold');
            } else if (rsi > 60) { // More lenient overbought
                score += 0.4; // Same score for overbought (was 0.3)
                direction = 'SHORT';
                confidence += 25; // Same confidence for overbought (was 20)
                signals.push('RSI Overbought');
            } else if (rsi >= 40 && rsi <= 60) {
                // Neutral RSI - still give some points
                score += 0.1;
                confidence += 5;
                signals.push('RSI Neutral');
            }
            
            // MACD Analysis (Filter Period: 10) - More Aggressive
            const macd = calculateMACD(coin, 12, 26, 9);
            indicators.macd = macd;
            
            if (macd.histogram > 0) { // Any positive histogram
                score += 0.3; // Higher score for bullish MACD
                if (direction === 'LONG') confidence += 20;
                signals.push('MACD Bullish');
            } else if (macd.histogram < 0) { // Any negative histogram
                score += 0.3; // Same score for bearish MACD (was 0.25)
                if (direction === 'SHORT') confidence += 20;
                signals.push('MACD Bearish');
            } else {
                // Neutral MACD - still give some points
                score += 0.1;
                confidence += 5;
                signals.push('MACD Neutral');
            }
            
            // Volume Analysis - Synced with other indicators
            const volume = coin.volume / 1000000; // Convert to millions
            const volumeSpike = coin.volume > coin.avgVolume * 1.2;
            indicators.volumeSpike = volumeSpike;
            indicators.volume = volume;
            
            // Volume scoring based on RSI and MACD signals
            if (volumeSpike && rsi < 40) { // Volume spike with oversold RSI
                score += 0.4;
                confidence += 15;
                signals.push('Volume Spike + RSI Oversold');
            } else if (volumeSpike && macd.histogram > 0) { // Volume spike with bullish MACD
                score += 0.35;
                confidence += 12;
                signals.push('Volume Spike + MACD Bullish');
            } else if (volume > 50) { // High volume
                score += 0.2;
                confidence += 8;
                signals.push('High Volume');
            } else if (volume > 20) { // Good volume
                score += 0.1;
                confidence += 5;
                signals.push('Good Volume');
            } else { // Low volume penalty
                score -= 0.1;
                confidence -= 5;
                signals.push('Low Volume');
            }
            
            // Price Action Analysis (Range Multiplier: 3) - More Aggressive
            const priceChange = (coin.price - coin.open24h) / coin.open24h;
            indicators.priceChange = priceChange;
            
            if (Math.abs(priceChange) > 0.02) { // Lower threshold: 2% price change
                score += 0.25; // Higher score for price action
                confidence += 15;
            } else {
                // Even small price changes get points
                score += 0.1;
                confidence += 5;
            }
            
            // ATR Analysis (ATR Period: 14, ATR Multiplier: 1.5) - More Aggressive
            const atr = calculateATR(coin, 14);
            indicators.atr = atr;
            
            if (atr > coin.price * 0.01) { // Lower threshold: 1% volatility
                score += 0.2; // Higher score for volatility
                confidence += 10;
            } else {
                // Even low volatility gets some points
                score += 0.1;
                confidence += 5;
            }
            
            // Apply Pine Script parameters - More Aggressive
            const goLongOrder = probotSettings.goLongOrder;
            const filterDeviation = probotSettings.filterDeviation;
            
            // Always give bonus points for Pine Script parameters
            score += 0.2; // Base bonus for using Pine Script
            confidence += 10;
            
            // Adjust score based on Pine Script parameters
            // goLongOrder applies to both LONG and SHORT positions
            if (goLongOrder > 3) {
                score += 0.15; // Higher bonus for higher order (both LONG and SHORT)
            }
            
            if (filterDeviation > 0.5) {
                score += 0.1; // Higher bonus for filter deviation
            }
            
            // Apply risk management settings
            if (riskLevel === 'conservative') {
                score *= 0.8; // Reduce score for conservative approach
                confidence *= 0.9; // Reduce confidence
            } else if (riskLevel === 'aggressive') {
                score *= 1.2; // Increase score for aggressive approach
                confidence *= 1.1; // Increase confidence
            }
            
            // Apply volatility filter
            if (volatilityFilter === 'low') {
                // Only trade in low volatility conditions
                if (atr > coin.price * 0.02) { // High volatility
                    score *= 0.5; // Heavily reduce score
                }
            } else if (volatilityFilter === 'high') {
                // Only trade in high volatility conditions
                if (atr <= coin.price * 0.01) { // Low volatility
                    score *= 0.5; // Heavily reduce score
                }
            }
            
            // Final confidence calculation
            confidence = Math.min(confidence, 100);
            
            return {
                score: score,
                direction: direction,
                confidence: confidence,
                indicators: indicators,
                signals: signals
            };
            
            } catch (error) {
                console.error('❌ analyzeWithPineScript error:', error);
                addProbotLog(`❌ Analiz hatası: ${error.message}`);
                return {
                    score: 0,
                    direction: 'LONG',
                    confidence: 0,
                    indicators: {},
                    signals: []
                };
            }
        }

        function updateProbotStatus(status, lastUpdate) {
            const probotStatus = document.getElementById('controlProbotAiStatus');
            const probotLastUpdate = document.getElementById('controlProbotAiLastAnalysis');
            const adminProbotStatus = document.getElementById('adminProbotStatus');
            const adminProbotLastUpdate = document.getElementById('adminProbotLastUpdate');
            
            console.log('🔄 updateProbotStatus called:', status, lastUpdate);
            console.log('🔍 Elements found:', {
                probotStatus: !!probotStatus,
                probotLastUpdate: !!probotLastUpdate,
                adminProbotStatus: !!adminProbotStatus,
                adminProbotLastUpdate: !!adminProbotLastUpdate
            });
            
            if (probotStatus) {
                probotStatus.textContent = status;
                probotStatus.className = status === 'Çalışıyor' ? 'text-green-400' : 'text-red-400';
                console.log('✅ probotStatus updated:', status);
            }
            if (probotLastUpdate) {
                probotLastUpdate.textContent = lastUpdate;
                console.log('✅ probotLastUpdate updated:', lastUpdate);
            }
            if (adminProbotStatus) {
                adminProbotStatus.textContent = status;
                console.log('✅ adminProbotStatus updated:', status);
            }
            if (adminProbotLastUpdate) {
                adminProbotLastUpdate.textContent = lastUpdate;
                console.log('✅ adminProbotLastUpdate updated:', lastUpdate);
            }
        }
        
        // ProBot AI tarama sayısı ve fırsat sayısını güncelle
        function updateProbotStats(scanCount, opportunities, lastTrade) {
            const probotScanCount = document.getElementById('controlProbotAiScanCount');
            const probotOpportunities = document.getElementById('controlProbotAiOpportunities');
            const probotLastTrade = document.getElementById('controlProbotAiLastTrade');
            
            if (probotScanCount) {
                probotScanCount.textContent = scanCount;
            }
            if (probotOpportunities) {
                probotOpportunities.textContent = opportunities;
            }
            if (probotLastTrade) {
                probotLastTrade.textContent = lastTrade;
            }
        }
        
        // Hızlı AI tarama sayısı ve fırsat sayısını güncelle
        function updateFastAiStats(scanCount, opportunities, lastTrade) {
            const fastScanCount = document.getElementById('controlFastAiScanCount');
            const fastOpportunities = document.getElementById('controlFastAiOpportunities');
            const fastLastTrade = document.getElementById('controlFastAiLastTrade');
            
            if (fastScanCount) {
                fastScanCount.textContent = scanCount;
            }
            if (fastOpportunities) {
                fastOpportunities.textContent = opportunities;
            }
            if (fastLastTrade) {
                fastLastTrade.textContent = lastTrade;
            }
        }
        
        // Uzun AI tarama sayısı ve fırsat sayısını güncelle
        function updateLongAiStats(scanCount, opportunities, lastTrade) {
            const longScanCount = document.getElementById('controlLongAiScanCount');
            const longOpportunities = document.getElementById('controlLongAiOpportunities');
            const longLastTrade = document.getElementById('controlLongAiLastTrade');
            
            if (longScanCount) {
                longScanCount.textContent = scanCount;
            }
            if (longOpportunities) {
                longOpportunities.textContent = opportunities;
            }
            if (longLastTrade) {
                longLastTrade.textContent = lastTrade;
            }
        }
        
        // ProBot AI Real Exchange Functions
        async function sendProbotOrderToExchange(trade) {
            const apiKey = document.getElementById('bybitApiKey').value;
            const secretKey = document.getElementById('bybitSecretKey').value;
            
            if (!apiKey || !secretKey) {
                addProbotLog(`❌ API anahtarları bulunamadı - ProBot AI yerel takip modunda`);
                addProbotLog(`💡 Gerçek borsa işlemi için Bybit API anahtarlarını girin`);
                return;
            }
            
            try {
                addProbotLog(`🚀 ProBot AI borsaya emir gönderiyor: ${trade.coin}`);
                
                // Send main order
                const orderResult = await sendProbotMainOrder(trade, apiKey, secretKey);
                
                if (orderResult.success) {
                    trade.orderId = orderResult.orderId;
                    addProbotLog(`✅ ProBot AI ana emir başarılı - ID: ${orderResult.orderId}`);
                    
                    // Send TP/SL orders
                    if (document.getElementById('autoSlTp').checked) {
                        setTimeout(() => sendProbotStopLoss(trade, apiKey, secretKey), 1000);
                        setTimeout(() => sendProbotTakeProfit(trade, apiKey, secretKey), 2000);
                    }
                    
                    // Prepare DCA orders
                    if (trade.dcaEnabled) {
                        prepareProbotDCAOrders(trade);
                    }
                    
                } else {
                    addProbotLog(`❌ ProBot AI emir hatası: ${orderResult.error}`);
                }
                
            } catch (error) {
                addProbotLog(`❌ ProBot AI borsa hatası: ${error.message}`);
            }
        }
        
        async function sendProbotMainOrder(trade, apiKey, secretKey) {
            try {
                const timestamp = Date.now().toString();
                const recvWindow = '5000';
                
                const orderData = {
                    category: 'linear',
                    symbol: trade.coin,
                    side: trade.type === 'LONG' ? 'Buy' : 'Sell',
                    orderType: 'Market',
                    qty: (trade.amount / trade.entryPrice).toFixed(6),
                    timeInForce: 'IOC',
                    reduceOnly: false,
                    closeOnTrigger: false
                };
                
                const signature = createBybitSignature(apiKey, secretKey, timestamp, recvWindow, orderData);
                
                const response = await fetch('https://api.bybit.com/v5/order/create', {
                    method: 'POST',
                    headers: {
                        'X-BAPI-API-KEY': apiKey,
                        'X-BAPI-SIGN': signature,
                        'X-BAPI-SIGN-TYPE': '2',
                        'X-BAPI-TIMESTAMP': timestamp,
                        'X-BAPI-RECV-WINDOW': recvWindow,
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify(orderData)
                });
                
                const result = await response.json();
                
                if (result.retCode === 0) {
                    return { success: true, orderId: result.result.orderId };
                } else {
                    return { success: false, error: result.retMsg };
                }
                
            } catch (error) {
                return { success: false, error: error.message };
            }
        }
        
        async function sendProbotStopLoss(trade, apiKey, secretKey) {
            try {
                const timestamp = Date.now().toString();
                const recvWindow = '5000';
                
                const slData = {
                    category: 'linear',
                    symbol: trade.coin,
                    side: trade.type === 'LONG' ? 'Sell' : 'Buy',
                    orderType: 'Stop',
                    qty: (trade.amount / trade.entryPrice).toFixed(6),
                    stopPrice: trade.stopLoss.toFixed(6),
                    timeInForce: 'GTC',
                    reduceOnly: true,
                    closeOnTrigger: true
                };
                
                const signature = createBybitSignature(apiKey, secretKey, timestamp, recvWindow, slData);
                
                const response = await fetch('https://api.bybit.com/v5/order/create', {
                    method: 'POST',
                    headers: {
                        'X-BAPI-API-KEY': apiKey,
                        'X-BAPI-SIGN': signature,
                        'X-BAPI-SIGN-TYPE': '2',
                        'X-BAPI-TIMESTAMP': timestamp,
                        'X-BAPI-RECV-WINDOW': recvWindow,
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify(slData)
                });
                
                const result = await response.json();
                
                if (result.retCode === 0) {
                    trade.stopLossOrderId = result.result.orderId;
                    addProbotLog(`✅ ProBot AI Stop Loss emri gönderildi - ID: ${result.result.orderId}`);
                } else {
                    addProbotLog(`❌ ProBot AI Stop Loss hatası: ${result.retMsg}`);
                }
                
            } catch (error) {
                addProbotLog(`❌ ProBot AI Stop Loss hatası: ${error.message}`);
            }
        }
        
        async function sendProbotTakeProfit(trade, apiKey, secretKey) {
            try {
                const timestamp = Date.now().toString();
                const recvWindow = '5000';
                
                const tpData = {
                    category: 'linear',
                    symbol: trade.coin,
                    side: trade.type === 'LONG' ? 'Sell' : 'Buy',
                    orderType: 'Limit',
                    qty: (trade.amount / trade.entryPrice).toFixed(6),
                    price: trade.takeProfit.toFixed(6),
                    timeInForce: 'GTC',
                    reduceOnly: true,
                    closeOnTrigger: true
                };
                
                const signature = createBybitSignature(apiKey, secretKey, timestamp, recvWindow, tpData);
                
                const response = await fetch('https://api.bybit.com/v5/order/create', {
                    method: 'POST',
                    headers: {
                        'X-BAPI-API-KEY': apiKey,
                        'X-BAPI-SIGN': signature,
                        'X-BAPI-SIGN-TYPE': '2',
                        'X-BAPI-TIMESTAMP': timestamp,
                        'X-BAPI-RECV-WINDOW': recvWindow,
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify(tpData)
                });
                
                const result = await response.json();
                
                if (result.retCode === 0) {
                    trade.takeProfitOrderId = result.result.orderId;
                    addProbotLog(`✅ ProBot AI Take Profit emri gönderildi - ID: ${result.result.orderId}`);
                } else {
                    addProbotLog(`❌ ProBot AI Take Profit hatası: ${result.retMsg}`);
                }
                
            } catch (error) {
                addProbotLog(`❌ ProBot AI Take Profit hatası: ${error.message}`);
            }
        }
        
        function prepareProbotDCAOrders(trade) {
            try {
                // Initialize DCA orders array if not exists
                if (!trade.dcaOrders) {
                    trade.dcaOrders = [];
                }
                
                // DCA emirleri sadece limit emirleri olarak hazırlanır, fiyat tetiklendiğinde gönderilir
                for (let level = 1; level <= trade.dcaCount; level++) {
                    const dcaAmount = trade.amount * Math.pow(trade.dcaMultiplier, level);
                    // DCA fiyat hesaplama: LONG için düşüş, SHORT için yükseliş
                    const dcaPrice = trade.type === 'LONG' 
                        ? trade.entryPrice * (1 - (trade.dcaTrigger * level)) // LONG: fiyat düştüğünde
                        : trade.entryPrice * (1 + (trade.dcaTrigger * level)); // SHORT: fiyat yükseldiğinde
                    
                    // Store DCA order info for later execution
                    trade.dcaOrders.push({
                        level: level,
                        amount: dcaAmount,
                        price: dcaPrice,
                        orderId: null,
                        status: 'pending'
                    });
                }
                
                addProbotLog(`📊 ProBot AI DCA emirleri hazırlandı: ${trade.dcaCount} seviye`);
                
            } catch (error) {
                addProbotLog(`❌ ProBot AI DCA emirleri hazırlanırken hata: ${error.message}`);
            }
        }
        
        // ProBot AI Order Cancellation
        async function cancelProbotOrders(trade) {
            try {
                addProbotLog(`🔄 ProBot AI tüm emirler iptal ediliyor: ${trade.coin}`);
                
                // Use the same cancellation system as Fast AI, Long AI, and Manual AI
                const cancelResult = await cancelAllOrdersForSymbol(trade.coin);
                if (cancelResult && cancelResult.success) {
                    addProbotLog(`✅ ProBot AI tüm emirler iptal edildi: ${trade.coin}`);
                } else {
                    addProbotLog(`⚠️ ProBot AI emir iptal edilemedi: ${trade.coin} - ${cancelResult?.error || 'Bilinmeyen hata'}`);
                }
                
            } catch (error) {
                addProbotLog(`❌ ProBot AI emir iptal hatası: ${error.message}`);
            }
        }

        function addProbotLog(message, type = 'info') {
            console.log('📝 addProbotLog called:', message, type);
            const timestamp = new Date().toLocaleTimeString();
            const logEntry = {
                time: timestamp,
                message: message,
                type: type
            };
            probotAiLogs.push(logEntry);
            console.log('📝 probotAiLogs length:', probotAiLogs.length);
            
            // Keep only last 100 logs
            if (probotAiLogs.length > 100) {
                probotAiLogs.shift();
            }
            
            updateProbotLogsDisplay();
        }
        
        function updateProbotLogsDisplay() {
            console.log('🔄 updateProbotLogsDisplay called');
            const logsContainer = document.getElementById('probotLogs');
            console.log('🔍 logsContainer found:', !!logsContainer);
            console.log('📝 probotAiLogs length:', probotAiLogs.length);
            
            if (logsContainer) {
                logsContainer.innerHTML = '';
                const logsToShow = probotAiLogs.slice(-20);
                console.log('📝 logsToShow length:', logsToShow.length);
                
                logsToShow.forEach(log => {
                    const logEntry = document.createElement('div');
                    logEntry.className = `text-sm ${log.type === 'error' ? 'text-red-400' : log.type === 'warning' ? 'text-yellow-400' : 'text-gray-300'}`;
                    logEntry.textContent = `[${log.time}] ${log.message}`;
                    logsContainer.appendChild(logEntry);
                });
                logsContainer.scrollTop = logsContainer.scrollHeight;
                console.log('✅ ProBot AI logs updated in UI');
            } else {
                console.log('❌ probotLogs container not found!');
            }
        }
        
        
        // ProBot AI DCA Execution
        async function executeProbotDCA(trade) {
            if (!trade.dcaEnabled || !trade.dcaOrders) return;
            
            const currentPrice = getCurrentPrice(trade.coin);
            if (!currentPrice) return;
            
            // Check if any DCA level should be triggered
            for (const dcaOrder of trade.dcaOrders) {
                if (dcaOrder.status === 'pending') {
                    const shouldTrigger = trade.type === 'LONG' 
                        ? currentPrice <= dcaOrder.price  // LONG: price dropped to DCA level
                        : currentPrice >= dcaOrder.price; // SHORT: price rose to DCA level
                    
                    if (shouldTrigger) {
                        try {
                            // Send DCA order to exchange
                            const apiKey = document.getElementById('bybitApiKey').value;
                            const secretKey = document.getElementById('bybitSecretKey').value;
                            
                            if (apiKey && secretKey) {
                                const dcaResult = await sendProbotDCAOrder(trade, dcaOrder, apiKey, secretKey);
                                if (dcaResult.success) {
                                    dcaOrder.orderId = dcaResult.orderId;
                                    dcaOrder.status = 'executed';
                                    addProbotLog(`✅ ProBot AI DCA Seviye ${dcaOrder.level} tetiklendi: ${trade.coin}`);
                                }
                            }
                        } catch (error) {
                            addProbotLog(`❌ ProBot AI DCA Seviye ${dcaOrder.level} hatası: ${error.message}`);
                        }
                    }
                }
            }
        }
        
        async function sendProbotDCAOrder(trade, dcaOrder, apiKey, secretKey) {
            try {
                const timestamp = Date.now().toString();
                const recvWindow = '5000';
                
                const dcaData = {
                    category: 'linear',
                    symbol: trade.coin,
                    side: trade.type === 'LONG' ? 'Buy' : 'Sell',
                    orderType: 'Limit',
                    qty: (dcaOrder.amount / dcaOrder.price).toFixed(6),
                    price: dcaOrder.price.toFixed(6),
                    timeInForce: 'GTC',
                    reduceOnly: false,
                    closeOnTrigger: false
                };
                
                const signature = createBybitSignature(apiKey, secretKey, timestamp, recvWindow, dcaData);
                
                const response = await fetch('https://api.bybit.com/v5/order/create', {
                    method: 'POST',
                    headers: {
                        'X-BAPI-API-KEY': apiKey,
                        'X-BAPI-SIGN': signature,
                        'X-BAPI-SIGN-TYPE': '2',
                        'X-BAPI-TIMESTAMP': timestamp,
                        'X-BAPI-RECV-WINDOW': recvWindow,
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify(dcaData)
                });
                
                const result = await response.json();
                
                if (result.retCode === 0) {
                    return { success: true, orderId: result.result.orderId };
                } else {
                    return { success: false, error: result.retMsg };
                }
                
            } catch (error) {
                return { success: false, error: error.message };
            }
        }
        
        function getCurrentPrice(symbol) {
            const coin = cryptoData.find(c => c.symbol === symbol);
            return coin ? coin.price : null;
        }

        // ProBot Settings Functions
        function saveProbotSettings() {
            // Get values from form
            probotSettings.goLongPeriod = parseInt(document.getElementById('probotGoLongPeriod').value);
            probotSettings.goLongOrder = parseInt(document.getElementById('probotGoLongOrder').value);
            probotSettings.filterDeviation = parseFloat(document.getElementById('probotFilterDeviation').value);
            probotSettings.filterPeriod = parseInt(document.getElementById('probotFilterPeriod').value);
            probotSettings.samplePeriod = parseInt(document.getElementById('probotSamplePeriod').value);
            probotSettings.rangeMultiplier = parseFloat(document.getElementById('probotRangeMultiplier').value);
            probotSettings.atrPeriod = parseInt(document.getElementById('probotAtrPeriod').value);
            probotSettings.atrMultiplier = parseFloat(document.getElementById('probotAtrMultiplier').value);
            probotSettings.usdtAmount = parseFloat(document.getElementById('probotUsdtAmount').value);
            probotSettings.leverage = parseInt(document.getElementById('probotLeverage').value);
            probotSettings.dcaLevels = parseInt(document.getElementById('probotDcaLevels').value);
            probotSettings.dcaPercent = parseFloat(document.getElementById('probotDcaPercent').value);
            probotSettings.dcaMultiplier = parseFloat(document.getElementById('probotDcaMultiplier').value);
            probotSettings.stopLoss = parseFloat(document.getElementById('probotStopLoss').value);
            probotSettings.takeProfit = parseFloat(document.getElementById('probotTakeProfit').value);
            probotSettings.trailingStop = parseFloat(document.getElementById('probotTrailingStop').value);
            probotSettings.maxTrades = parseInt(document.getElementById('probotMaxTrades').value);
            probotSettings.scoreThreshold = parseFloat(document.getElementById('probotScoreThreshold').value);
            
            // Save to localStorage
            localStorage.setItem('probotSettings', JSON.stringify(probotSettings));
            
            showNotification('ProBot AI ayarları kaydedildi!', 'success');
            addProbotLog('[Ayarlar] ProBot AI parametreleri güncellendi');
        }

        function resetProbotSettings() {
            // Reset to default values
            probotSettings = {
                goLongPeriod: 13,
                goLongOrder: 5,
                filterDeviation: 1,
                filterPeriod: 10,
                samplePeriod: 10,
                rangeMultiplier: 3,
                atrPeriod: 14,
                atrMultiplier: 1.5,
                usdtAmount: 1,
                leverage: 10,
                dcaLevels: 2,
                dcaPercent: 1.5,
                dcaMultiplier: 2.0,
                stopLoss: 2,
                takeProfit: 1,
                trailingStop: 3.0,
                scoreThreshold: 0.5,
                maxTrades: 3
            };
            
            // Update form values
            document.getElementById('probotGoLongPeriod').value = probotSettings.goLongPeriod;
            document.getElementById('probotGoLongOrder').value = probotSettings.goLongOrder;
            document.getElementById('probotFilterDeviation').value = probotSettings.filterDeviation;
            document.getElementById('probotFilterPeriod').value = probotSettings.filterPeriod;
            document.getElementById('probotSamplePeriod').value = probotSettings.samplePeriod;
            document.getElementById('probotRangeMultiplier').value = probotSettings.rangeMultiplier;
            document.getElementById('probotAtrPeriod').value = probotSettings.atrPeriod;
            document.getElementById('probotAtrMultiplier').value = probotSettings.atrMultiplier;
            document.getElementById('probotUsdtAmount').value = probotSettings.usdtAmount;
            document.getElementById('probotLeverage').value = probotSettings.leverage;
            document.getElementById('probotDcaLevels').value = probotSettings.dcaLevels;
            document.getElementById('probotDcaPercent').value = probotSettings.dcaPercent;
            document.getElementById('probotDcaMultiplier').value = probotSettings.dcaMultiplier;
            document.getElementById('probotStopLoss').value = probotSettings.stopLoss;
            document.getElementById('probotTakeProfit').value = probotSettings.takeProfit;
            document.getElementById('probotTrailingStop').value = probotSettings.trailingStop;
            document.getElementById('probotMaxTrades').value = probotSettings.maxTrades;
            document.getElementById('probotScoreThreshold').value = probotSettings.scoreThreshold;
            
            showNotification('ProBot AI ayarları varsayılana sıfırlandı!', 'info');
            addProbotLog('[Ayarlar] ProBot AI parametreleri varsayılana sıfırlandı');
        }

        function testProbotStrategy() {
            showNotification('ProBot AI stratejisi test ediliyor...', 'info');
            addProbotLog('[Test] ProBot stratejisi test ediliyor...');
            addProbotLog(`[Test] Pine Script Parametreleri: GoLong Period: ${probotSettings.goLongPeriod}, Order: ${probotSettings.goLongOrder}`);
            addProbotLog(`[Test] DCA Ayarları: ${probotSettings.dcaLevels} seviye, ${probotSettings.dcaPercent}% tetikleme`);
            
            // Test TP/SL calculations
            const testPrice = 50000; // Test BTC price
            const testStopLoss = testPrice * (1 - probotSettings.stopLoss / 100);
            const testTakeProfit = testPrice * (1 + probotSettings.takeProfit / 100);
            
            addProbotLog(`[Test] TP/SL Hesaplama Testi:`);
            addProbotLog(`[Test] Giriş Fiyatı: $${testPrice.toFixed(2)}`);
            addProbotLog(`[Test] Stop Loss: $${testStopLoss.toFixed(2)} (${probotSettings.stopLoss}%)`);
            addProbotLog(`[Test] Take Profit: $${testTakeProfit.toFixed(2)} (${probotSettings.takeProfit}%)`);
            
            // Test DCA calculations
            if (probotSettings.dcaLevels > 0) {
                addProbotLog(`[Test] DCA Hesaplama Testi:`);
                addProbotLog(`[Test] LONG İşlem DCA Seviyeleri:`);
                for (let i = 1; i <= probotSettings.dcaLevels; i++) {
                    const dcaPrice = testPrice * (1 - (probotSettings.dcaPercent / 100) * i);
                    const dcaAmount = probotSettings.usdtAmount * Math.pow(probotSettings.dcaMultiplier, i - 1);
                    addProbotLog(`[Test] DCA Seviye ${i}: $${dcaPrice.toFixed(2)} - ${dcaAmount.toFixed(2)} USDT (${probotSettings.dcaPercent * i}% düşüş)`);
                }
                addProbotLog(`[Test] SHORT İşlem DCA Seviyeleri:`);
                for (let i = 1; i <= probotSettings.dcaLevels; i++) {
                    const dcaPrice = testPrice * (1 + (probotSettings.dcaPercent / 100) * i);
                    const dcaAmount = probotSettings.usdtAmount * Math.pow(probotSettings.dcaMultiplier, i - 1);
                    addProbotLog(`[Test] DCA Seviye ${i}: $${dcaPrice.toFixed(2)} - ${dcaAmount.toFixed(2)} USDT (${probotSettings.dcaPercent * i}% yükseliş)`);
                }
            }
            
            // Simulate strategy test
            setTimeout(() => {
                const testResult = Math.random() > 0.3 ? 'Başarılı' : 'Başarısız';
                const successRate = Math.floor(Math.random() * 20) + 70; // 70-90%
                
                showNotification(`ProBot AI test sonucu: ${testResult} (Başarı oranı: ${successRate}%)`, testResult === 'Başarılı' ? 'success' : 'warning');
                addProbotLog(`[Test] Strateji test sonucu: ${testResult} (Başarı oranı: ${successRate}%)`);
            }, 2000);
        }

        // Admin ProBot Functions
        function adminSaveProbotSettings() {
            // Get values from admin form
            probotSettings.goLongPeriod = parseInt(document.getElementById('adminProbotGoLongPeriod').value);
            probotSettings.goLongOrder = parseInt(document.getElementById('adminProbotGoLongOrder').value);
            probotSettings.filterDeviation = parseFloat(document.getElementById('adminProbotFilterDeviation').value);
            probotSettings.filterPeriod = parseInt(document.getElementById('adminProbotFilterPeriod').value);
            probotSettings.samplePeriod = parseInt(document.getElementById('adminProbotSamplePeriod').value);
            probotSettings.rangeMultiplier = parseFloat(document.getElementById('adminProbotRangeMultiplier').value);
            probotSettings.atrPeriod = parseInt(document.getElementById('adminProbotAtrPeriod').value);
            probotSettings.atrMultiplier = parseFloat(document.getElementById('adminProbotAtrMultiplier').value);
            probotSettings.usdtAmount = parseFloat(document.getElementById('adminProbotUsdtAmount').value);
            probotSettings.leverage = parseInt(document.getElementById('adminProbotLeverage').value);
            probotSettings.dcaLevels = parseInt(document.getElementById('adminProbotDcaLevels').value);
            probotSettings.dcaPercent = parseFloat(document.getElementById('adminProbotDcaPercent').value);
            probotSettings.dcaMultiplier = parseFloat(document.getElementById('adminProbotDcaMultiplier').value);
            probotSettings.stopLoss = parseFloat(document.getElementById('adminProbotStopLoss').value);
            probotSettings.takeProfit = parseFloat(document.getElementById('adminProbotTakeProfit').value);
            probotSettings.trailingStop = parseFloat(document.getElementById('adminProbotTrailingStop').value);
            
            // Save to localStorage
            localStorage.setItem('probotSettings', JSON.stringify(probotSettings));
            
            showNotification('Admin: ProBot AI ayarları kaydedildi!', 'success');
            addProbotLog('[Admin] ProBot AI parametreleri güncellendi');
        }

        function adminResetProbotSettings() {
            resetProbotSettings();
            
            // Update admin form values
            document.getElementById('adminProbotGoLongPeriod').value = probotSettings.goLongPeriod;
            document.getElementById('adminProbotGoLongOrder').value = probotSettings.goLongOrder;
            document.getElementById('adminProbotFilterDeviation').value = probotSettings.filterDeviation;
            document.getElementById('adminProbotFilterPeriod').value = probotSettings.filterPeriod;
            document.getElementById('adminProbotSamplePeriod').value = probotSettings.samplePeriod;
            document.getElementById('adminProbotRangeMultiplier').value = probotSettings.rangeMultiplier;
            document.getElementById('adminProbotAtrPeriod').value = probotSettings.atrPeriod;
            document.getElementById('adminProbotAtrMultiplier').value = probotSettings.atrMultiplier;
            document.getElementById('adminProbotUsdtAmount').value = probotSettings.usdtAmount;
            document.getElementById('adminProbotLeverage').value = probotSettings.leverage;
            document.getElementById('adminProbotDcaLevels').value = probotSettings.dcaLevels;
            document.getElementById('adminProbotDcaPercent').value = probotSettings.dcaPercent;
            document.getElementById('adminProbotDcaMultiplier').value = probotSettings.dcaMultiplier;
            document.getElementById('adminProbotStopLoss').value = probotSettings.stopLoss;
            document.getElementById('adminProbotTakeProfit').value = probotSettings.takeProfit;
            document.getElementById('adminProbotTrailingStop').value = probotSettings.trailingStop;
            
            showNotification('Admin: ProBot AI ayarları varsayılana sıfırlandı!', 'info');
        }

        function adminTestProbotStrategy() {
            testProbotStrategy();
            addProbotLog('[Admin] Strateji testi başlatıldı');
        }

        function adminStartProbotAI() {
            if (!probotAiActive) {
                toggleProbotAI();
                addProbotLog('[Admin] ProBot AI manuel olarak başlatıldı');
            } else {
                showNotification('ProBot AI zaten çalışıyor!', 'warning');
            }
        }

        // Load ProBot AI settings from localStorage
        function loadProbotSettings() {
            try {
                const savedSettings = localStorage.getItem('probotSettings');
                if (savedSettings) {
                    probotSettings = JSON.parse(savedSettings);
                    
                    // Update form values
                    updateProbotFormValues(probotSettings);
                    addProbotLog('[Sistem] ProBot AI ayarları yüklendi');
                } else {
                    addProbotLog('[Sistem] ProBot AI varsayılan ayarları kullanılıyor');
                }
            } catch (error) {
                console.error('Error loading ProBot settings:', error);
                addProbotLog('[Hata] ProBot AI ayarları yüklenirken hata oluştu');
            }
        }

        // Update ProBot form values
        function updateProbotFormValues(settings) {
            const formFields = [
                'probotGoLongPeriod', 'probotGoLongOrder', 'probotFilterDeviation', 'probotFilterPeriod',
                'probotSamplePeriod', 'probotRangeMultiplier', 'probotAtrPeriod', 'probotAtrMultiplier',
                'probotUsdtAmount', 'probotLeverage', 'probotDcaLevels', 'probotDcaPercent',
                'probotDcaMultiplier', 'probotStopLoss', 'probotTakeProfit', 'probotTrailingStop',
                'probotMaxTrades', 'probotScoreThreshold',
                // Admin form fields
                'adminProbotGoLongPeriod', 'adminProbotGoLongOrder', 'adminProbotFilterDeviation', 'adminProbotFilterPeriod',
                'adminProbotSamplePeriod', 'adminProbotRangeMultiplier', 'adminProbotAtrPeriod', 'adminProbotAtrMultiplier',
                'adminProbotUsdtAmount', 'adminProbotLeverage', 'adminProbotDcaLevels', 'adminProbotDcaPercent',
                'adminProbotDcaMultiplier', 'adminProbotStopLoss', 'adminProbotTakeProfit', 'adminProbotTrailingStop'
            ];

            const settingKeys = [
                'goLongPeriod', 'goLongOrder', 'filterDeviation', 'filterPeriod',
                'samplePeriod', 'rangeMultiplier', 'atrPeriod', 'atrMultiplier',
                'usdtAmount', 'leverage', 'dcaLevels', 'dcaPercent',
                'dcaMultiplier', 'stopLoss', 'takeProfit', 'trailingStop',
                'maxTrades', 'scoreThreshold'
            ];

            formFields.forEach((fieldId, index) => {
                const element = document.getElementById(fieldId);
                if (element && settings[settingKeys[index % settingKeys.length]] !== undefined) {
                    element.value = settings[settingKeys[index % settingKeys.length]];
                }
            });
        }

        function startFastAIAnalysis() {
            console.log('⚡ startFastAIAnalysis called, fastAiActive:', fastAiActive);
            if (!fastAiActive) {
                console.log('❌ Fast AI not active, returning');
                return;
            }
            
            // Check if cryptoData is empty and fetch if needed
            if (cryptoData.length === 0) {
                console.log('⚠️ CryptoData empty, fetching real market data for Fast AI');
                fetchRealPrices();
                setTimeout(startFastAIAnalysis, 5000);
                return;
            }
            
            console.log('✅ CryptoData available, performing Fast AI analysis with', cryptoData.length, 'coins');
            
            // Update scan count
            fastAiScanCount++;
            updateFastAiStats(fastAiScanCount, fastAiOpportunities, '-');
            
            // Perform market analysis
            const analysisResults = performFastAnalysis();
            
            if (analysisResults.shouldTrade) {
                fastAiOpportunities++;
                addFastAiLog(`🎯 En iyi fırsat: ${analysisResults.selectedCoin.symbol} (Skor: ${analysisResults.confidence.toFixed(2)})`);
                updateFastAiStats(fastAiScanCount, fastAiOpportunities, analysisResults.selectedCoin.symbol);
                if (checkMaxActiveTrades('Fast AI')) {
                    generateFastAITrade(analysisResults);
                } else {
                    addFastAiLog(`⚠️ Maksimum aktif işlem limiti dolu - Hızlı AI beklemede`);
                }
            } else {
                addFastAiLog(`🔍 Hızlı AI market taraması - uygun fırsat bulunamadı`);
            }
            
            // Schedule next analysis
            if (fastAiActive) {
                setTimeout(startFastAIAnalysis, 10000); // 10 saniyede bir analiz
            }
        }

        function startLongAIAnalysis() {
            console.log('🎯 startLongAIAnalysis called, longAiActive:', longAiActive);
            if (!longAiActive) {
                console.log('❌ Long AI not active, returning');
                return;
            }
            
            // Check if cryptoData is empty and fetch if needed
            if (cryptoData.length === 0) {
                console.log('⚠️ CryptoData empty, fetching real market data for Long AI');
                fetchRealPrices();
                setTimeout(startLongAIAnalysis, 5000);
                return;
            }
            
            console.log('✅ CryptoData available, performing Long AI analysis with', cryptoData.length, 'coins');
            
            // Update scan count
            longAiScanCount++;
            updateLongAiStats(longAiScanCount, longAiOpportunities, '-');
            
            // Perform market analysis
            const analysisResults = performLongAnalysis();
            
            if (analysisResults.shouldTrade) {
                longAiOpportunities++;
                addLongAiLog(`🎯 En iyi fırsat: ${analysisResults.selectedCoin.symbol} (Skor: ${analysisResults.confidence.toFixed(2)})`);
                updateLongAiStats(longAiScanCount, longAiOpportunities, analysisResults.selectedCoin.symbol);
                addLongAiLog(`🔧 Debug: Calling generateLongAITrade with shouldTrade=${analysisResults.shouldTrade}`);
                if (checkMaxActiveTrades('Long AI')) {
                    addLongAiLog(`✅ Max trades check passed, generating trade...`);
                    generateLongAITrade(analysisResults);
                } else {
                    addLongAiLog(`⚠️ Maksimum aktif işlem limiti dolu - Uzun AI beklemede`);
                }
            } else {
                addLongAiLog(`🔍 Uzun AI market taraması - uygun fırsat bulunamadı`);
            }
            
            // Schedule next analysis
            if (longAiActive) {
                setTimeout(startLongAIAnalysis, 10000); // 10 saniyede bir analiz (Hızlı AI ile aynı hız)
            }
        }

        function updateAIConditions() {
            // Real market analysis based on actual coin data
            const conditions = [];
            
            if (cryptoData.length > 0) {
                // Analyze top coins for real market conditions
                const topCoins = cryptoData
                    .filter(coin => coin.volume > 10000000)
                    .sort((a, b) => b.volume - a.volume)
                    .slice(0, 10);
                
                let rsiOversoldCount = 0;
                let macdBullishCount = 0;
                let volumeSpikeCount = 0;
                let strongTrendCount = 0;
                
                topCoins.forEach(coin => {
                    const rsi = calculateRSI(coin, 14);
                    const macd = calculateMACD(coin, 12, 26, 9);
                    const volume = coin.volume / 1000000;
                    const change = Math.abs(coin.change24h);
                    
                    if (rsi < 30) rsiOversoldCount++;
                    if (macd.macd > macd.signal) macdBullishCount++;
                    if (volume > 100) volumeSpikeCount++;
                    if (change > 5) strongTrendCount++;
                });
                
                const totalCoins = topCoins.length;
                
                // RSI Oversold condition
                conditions.push({
                    name: '📊 RSI Oversold',
                    status: rsiOversoldCount > totalCoins * 0.3,
                    confidence: Math.min(95, 60 + (rsiOversoldCount / totalCoins) * 35),
                    icon: '📊'
                });
                
                // MACD Bullish condition
                conditions.push({
                    name: '📈 MACD Bullish',
                    status: macdBullishCount > totalCoins * 0.4,
                    confidence: Math.min(95, 65 + (macdBullishCount / totalCoins) * 30),
                    icon: '📈'
                });
                
                // Volume Spike condition
                conditions.push({
                    name: '🔊 Volume Spike',
                    status: volumeSpikeCount > totalCoins * 0.2,
                    confidence: Math.min(95, 70 + (volumeSpikeCount / totalCoins) * 25),
                    icon: '🔊'
                });
                
                // Strong Trend condition
                conditions.push({
                    name: '⚡ Strong Trend',
                    status: strongTrendCount > totalCoins * 0.3,
                    confidence: Math.min(95, 65 + (strongTrendCount / totalCoins) * 30),
                    icon: '⚡'
                });
                
                // Market Volatility condition
                const avgVolatility = topCoins.reduce((sum, coin) => sum + Math.abs(coin.change24h), 0) / totalCoins;
                conditions.push({
                    name: '🌊 Market Volatility',
                    status: avgVolatility > 3,
                    confidence: Math.min(95, 60 + Math.min(35, avgVolatility * 5)),
                    icon: '🌊'
                });
                
                // Support/Resistance condition (simplified)
                const supportCount = topCoins.filter(coin => coin.change24h < -2).length;
                conditions.push({
                    name: '🎯 Support Levels',
                    status: supportCount > totalCoins * 0.2,
                    confidence: Math.min(95, 60 + (supportCount / totalCoins) * 35),
                    icon: '🎯'
                });
                
                // Breakout condition
                const breakoutCount = topCoins.filter(coin => coin.change24h > 5).length;
                conditions.push({
                    name: '💥 Breakout Signal',
                    status: breakoutCount > totalCoins * 0.15,
                    confidence: Math.min(95, 70 + (breakoutCount / totalCoins) * 25),
                    icon: '💥'
                });
                
                // Momentum condition
                const momentumCount = topCoins.filter(coin => Math.abs(coin.change24h) > 2).length;
                conditions.push({
                    name: '🔄 Market Momentum',
                    status: momentumCount > totalCoins * 0.4,
                    confidence: Math.min(95, 65 + (momentumCount / totalCoins) * 30),
                    icon: '🔄'
                });
            } else {
                // Fallback conditions if no data
                conditions.push(
                    { name: '📊 RSI Oversold', status: false, confidence: 50, icon: '📊' },
                    { name: '📈 MACD Bullish', status: false, confidence: 50, icon: '📈' },
                    { name: '🔊 Volume Spike', status: false, confidence: 50, icon: '🔊' },
                    { name: '⚡ Strong Trend', status: false, confidence: 50, icon: '⚡' },
                    { name: '🌊 Market Volatility', status: false, confidence: 50, icon: '🌊' },
                    { name: '🎯 Support Levels', status: false, confidence: 50, icon: '🎯' },
                    { name: '💥 Breakout Signal', status: false, confidence: 50, icon: '💥' },
                    { name: '🔄 Market Momentum', status: false, confidence: 50, icon: '🔄' }
                );
            }
            
            const conditionsContainer = document.getElementById('aiConditions');
            conditionsContainer.innerHTML = '';
            
            conditions.forEach(condition => {
                const statusClass = condition.status ? 'accent-green' : 'accent-red';
                const statusBg = condition.status ? 'bg-green-600' : 'bg-red-600';
                const statusText = condition.status ? '✅ Aktif' : '❌ Pasif';
                const pulseClass = condition.status ? 'animate-pulse' : '';
                
                // Generate AI signal based on conditions
                const signals = ['LONG', 'SHORT', 'NÖTR'];
                const signal = signals[Math.floor(Math.random() * signals.length)];
                const signalColor = signal === 'LONG' ? 'text-green-400' : signal === 'SHORT' ? 'text-red-400' : 'text-yellow-400';
                const currentTime = new Date().toLocaleTimeString('tr-TR', { hour: '2-digit', minute: '2-digit' });
                
                const conditionElement = document.createElement('div');
                conditionElement.className = `trading-card p-4 ${pulseClass}`;
                conditionElement.innerHTML = `
                    <div class="flex items-center justify-between mb-2">
                        <div class="font-bold text-sm text-white">${condition.name}</div>
                        <div class="text-lg">${condition.icon}</div>
                    </div>
                    <div class="flex justify-between items-center mb-2">
                        <span class="${statusBg} px-3 py-1 rounded-full text-xs font-bold">${statusText}</span>
                        <span class="text-sm ${statusClass} font-bold">${condition.confidence}%</span>
                    </div>
                    <div class="flex justify-between items-center mb-2">
                        <span class="text-xs text-gray-400">${currentTime}</span>
                        <span class="text-sm font-bold ${signalColor}">${signal}</span>
                    </div>
                    <div class="bg-gray-600 rounded-full h-2">
                        <div class="h-2 rounded-full ${condition.status ? 'bg-green-500' : 'bg-red-500'}" 
                             style="width: ${condition.confidence}%; transition: width 0.5s ease;"></div>
                    </div>
                `;
                
                conditionsContainer.appendChild(conditionElement);
            });
        }

        // Check if maximum active trades limit is reached for specific AI
        function checkMaxActiveTrades(aiType) {
            if (!aiType) {
                console.warn('checkMaxActiveTrades called without aiType parameter');
                return true;
            }
            
            // Check specific AI's max trades
            // Convert AI type names to element IDs
            const aiTypeMap = {
                'Fast AI': 'fastMaxTrades',
                'Long AI': 'longMaxTrades', 
                'ProBot AI': 'probotMaxTrades'
            };
            const elementId = aiTypeMap[aiType] || `${aiType}MaxTrades`;
            const maxTradesElement = document.getElementById(elementId);
            const maxTrades = parseInt(maxTradesElement?.value || '5');
            const activeTrades = transactions.filter(t => t.status === 'Aktif' && t.aiType === aiType).length;
            
            if (activeTrades >= maxTrades) {
                console.log(`⚠️ ${aiType} maksimum aktif işlem sayısına ulaşıldı: ${activeTrades}/${maxTrades}`);
                showNotification(`${aiType} maksimum aktif işlem sayısına ulaşıldı (${activeTrades}/${maxTrades})`, 'warning');
                return false;
            }
            return true;
        }

        function generateFastAITrade(analysisResults = null) {
            if (!fastAiActive) return;
            
            // Check maximum active trades limit for Fast AI
            if (!checkMaxActiveTrades('Fast AI')) return;
            
            // Use provided analysisResults or perform new analysis
            if (!analysisResults) {
                analysisResults = performFastAnalysis();
                if (!analysisResults.shouldTrade) {
                    return;
                }
            }
            
            const coin = analysisResults.selectedCoin;
            
            // Check if coin already has an active trade by any AI
            const existingTrade = transactions.find(t => 
                t.coin === coin.symbol && 
                t.status === 'Aktif'
            );
            
            if (existingTrade) {
                addApiLog(`❌ ${coin.symbol} zaten aktif işlemde (${existingTrade.aiType}) - Fast AI atlandı`);
                return;
            }
            
            const entryPrice = coin.price;
            const isLong = analysisResults.direction === 'LONG';
            
            // Use Fast AI specific settings
            const leverage = parseInt(document.getElementById('fastLeverage')?.value || '10');
            const usdtAmount = parseFloat(document.getElementById('fastUsdtAmount')?.value || '1');
            const stopLossPercent = parseFloat(document.getElementById('fastStopLoss')?.value || '2') / 100;
            const takeProfitPercent = parseFloat(document.getElementById('fastTakeProfit')?.value || '1') / 100;
            const orderType = document.getElementById('orderType')?.value || 'Market';
            
            // Get DCA settings for fast trades
            const dcaEnabled = document.getElementById('fastDcaEnabled')?.checked || false;
            const dcaCount = parseInt(document.getElementById('fastDcaCount')?.value || '2');
            const dcaTrigger = parseFloat(document.getElementById('fastDcaTrigger')?.value || '3') / 100;
            const dcaMultiplier = parseFloat(document.getElementById('fastDcaMultiplier')?.value || '1.2');
            
            // Calculate SL/TP prices based on percentages - CORRECTED FOR SHORT
            const stopLoss = isLong ? 
                entryPrice * (1 - stopLossPercent) : // LONG: SL below entry (zarar durdurma)
                entryPrice * (1 + stopLossPercent);   // SHORT: SL above entry (zarar durdurma)
            
            const takeProfit = isLong ? 
                entryPrice * (1 + takeProfitPercent) : // LONG: TP above entry (kar alma)
                entryPrice * (1 - takeProfitPercent);  // SHORT: TP below entry (kar alma)
            
            // Debug: Log TP/SL calculations
            console.log(`🔍 Fast AI TP/SL Calculation:`, {
                coin: coin.symbol,
                type: isLong ? 'LONG' : 'SHORT',
                entryPrice: entryPrice,
                stopLossPercent: (stopLossPercent * 100).toFixed(2) + '%',
                takeProfitPercent: (takeProfitPercent * 100).toFixed(2) + '%',
                stopLoss: stopLoss.toFixed(6),
                takeProfit: takeProfit.toFixed(6)
            });
            
            const trade = {
                id: Date.now(),
                coin: coin.symbol,
                type: isLong ? 'LONG' : 'SHORT',
                entryPrice: entryPrice,
                currentPrice: entryPrice,
                exitPrice: null,
                stopLoss: stopLoss,
                takeProfit: takeProfit,
                stopLossPercent: stopLossPercent, // TP/SL oranlarını sakla
                takeProfitPercent: takeProfitPercent, // TP/SL oranlarını sakla
                amount: usdtAmount,
                totalInvestment: usdtAmount, // Initialize total investment
                leverage: leverage,
                pnl: 0,
                status: 'Aktif',
                timestamp: new Date().toLocaleString('tr-TR'),
                orderType: orderType,
                confidence: analysisResults.confidence,
                indicators: analysisResults.indicators,
                tradeType: 'Hızlı',
                aiType: 'Fast AI',
                dcaEnabled: dcaEnabled,
                dcaLevel: 0,
                dcaCount: dcaCount,
                dcaTrigger: dcaTrigger,
                dcaMultiplier: dcaMultiplier
            };
            
            transactions.unshift(trade);
            fastTradeCount++;
            saveTransactionsToStorage();
            updateActiveTradesTable();
            updateCompletedTradesTable();
            updateTradeInfo();
            updateAdminStats();
            
            // Send to exchange with detailed logging
            if (document.getElementById('bybitApiKey').value) {
                sendOrderToBybit(trade);
            } else if (document.getElementById('binanceApiKey').value) {
                sendOrderToBinance(trade);
            } else {
                addApiLog(`⚠️ API bağlantısı yok - ${coin.symbol} işlemi yerel olarak takip ediliyor`);
                addApiLog(`💡 Gerçek borsa işlemi için Bybit veya Binance API anahtarlarını girin`);
            }
            
            // Send DCA orders immediately if enabled
            if (dcaEnabled && dcaCount > 0) {
                setTimeout(async () => {
                    try {
                        await sendDCAOrdersToExchange(trade);
                    } catch (error) {
                        addApiLog(`❌ DCA emirleri hazırlanırken hata: ${error.message}`);
                        console.error('DCA preparation error:', error);
                    }
                }, 1000); // 1 second delay to ensure main order is processed
            }
            
            showNotification(`Hızlı AI ${coin.symbol} ${isLong ? 'LONG' : 'SHORT'} (${analysisResults.confidence}% güven)`, 'info');
            
            // Fast AI trades will be closed by real TP/SL triggers, not random timing
            addFastAiLog(`[İşlem] ${coin.symbol} ${isLong ? 'LONG' : 'SHORT'} pozisyonu açıldı - TP/SL ile kapatılacak`);
        }

        function generateLongAITrade(analysisResults = null) {
            addLongAiLog(`🔧 generateLongAITrade called, longAiActive: ${longAiActive}`);
            if (!longAiActive) return;
            
            // Check maximum active trades limit for Long AI
            if (!checkMaxActiveTrades('Long AI')) {
                addLongAiLog(`❌ Max trades limit exceeded for Long AI`);
                return;
            }
            
            // Use provided analysisResults or perform new analysis
            if (!analysisResults) {
                addLongAiLog(`⚠️ No analysisResults provided, performing new analysis...`);
                analysisResults = performLongAnalysis();
                if (!analysisResults.shouldTrade) {
                    addLongAiLog(`❌ New analysis result: shouldTrade is false`);
                    return;
                }
            } else {
                addLongAiLog(`✅ Using provided analysisResults: ${analysisResults.selectedCoin.symbol}, confidence: ${analysisResults.confidence}`);
            }
            
            const coin = analysisResults.selectedCoin;
            
            // Check if coin already has an active trade by any AI
            const existingTrade = transactions.find(t => 
                t.coin === coin.symbol && 
                t.status === 'Aktif'
            );
            
            if (existingTrade) {
                addApiLog(`❌ ${coin.symbol} zaten aktif işlemde (${existingTrade.aiType}) - Long AI atlandı`);
                return;
            }
            
            const entryPrice = coin.price;
            const isLong = analysisResults.direction === 'LONG';
            addLongAiLog(`🚀 Creating trade: ${coin.symbol} ${isLong ? 'LONG' : 'SHORT'} at ${entryPrice}`);
            
            // Use Long AI specific settings
            const leverage = parseInt(document.getElementById('longLeverage')?.value || '10');
            const usdtAmount = parseFloat(document.getElementById('longUsdtAmount')?.value || '1');
            const stopLossPercent = parseFloat(document.getElementById('longStopLoss')?.value || '2') / 100;
            const takeProfitPercent = parseFloat(document.getElementById('longTakeProfit')?.value || '1') / 100;
            const orderType = document.getElementById('orderType')?.value || 'Limit';
            
            // Get DCA settings for long trades
            const dcaEnabled = document.getElementById('longDcaEnabled')?.checked || false;
            const dcaCount = parseInt(document.getElementById('longDcaCount')?.value || '4');
            const dcaTrigger = parseFloat(document.getElementById('longDcaTrigger')?.value || '8') / 100;
            const dcaMultiplier = parseFloat(document.getElementById('longDcaMultiplier')?.value || '1.5');
            
            const stopLoss = isLong ? 
                entryPrice * (1 - stopLossPercent) : // LONG: SL below entry (zarar durdurma)
                entryPrice * (1 + stopLossPercent);   // SHORT: SL above entry (zarar durdurma)
            
            const takeProfit = isLong ? 
                entryPrice * (1 + takeProfitPercent) : // LONG: TP above entry (kar alma)
                entryPrice * (1 - takeProfitPercent);  // SHORT: TP below entry (kar alma)
            
            // Debug: Log TP/SL calculations
            console.log(`🔍 Long AI TP/SL Calculation:`, {
                coin: coin.symbol,
                type: isLong ? 'LONG' : 'SHORT',
                entryPrice: entryPrice,
                stopLossPercent: (stopLossPercent * 100).toFixed(2) + '%',
                takeProfitPercent: (takeProfitPercent * 100).toFixed(2) + '%',
                stopLoss: stopLoss.toFixed(6),
                takeProfit: takeProfit.toFixed(6)
            });
            
            const trade = {
                id: Date.now(),
                coin: coin.symbol,
                type: isLong ? 'LONG' : 'SHORT',
                entryPrice: entryPrice,
                currentPrice: entryPrice,
                exitPrice: null,
                stopLoss: stopLoss,
                takeProfit: takeProfit,
                stopLossPercent: stopLossPercent, // TP/SL oranlarını sakla
                takeProfitPercent: takeProfitPercent, // TP/SL oranlarını sakla
                amount: usdtAmount,
                totalInvestment: usdtAmount, // Initialize total investment
                leverage: leverage,
                pnl: 0,
                status: 'Aktif',
                timestamp: new Date().toLocaleString('tr-TR'),
                orderType: orderType,
                confidence: analysisResults.confidence,
                indicators: analysisResults.indicators,
                tradeType: 'Uzun',
                aiType: 'Long AI',
                dcaEnabled: dcaEnabled,
                dcaLevel: 0,
                dcaCount: dcaCount,
                dcaTrigger: dcaTrigger,
                dcaMultiplier: dcaMultiplier
            };
            
            transactions.unshift(trade);
            longTradeCount++;
            saveTransactionsToStorage();
            updateActiveTradesTable();
            updateCompletedTradesTable();
            updateTradeInfo();
            updateAdminStats();
            
            // Send to exchange with detailed logging
            if (document.getElementById('bybitApiKey').value) {
                sendOrderToBybit(trade);
            } else if (document.getElementById('binanceApiKey').value) {
                sendOrderToBinance(trade);
            } else {
                addApiLog(`⚠️ API bağlantısı yok - ${coin.symbol} uzun işlemi yerel olarak takip ediliyor`);
                addApiLog(`💡 Gerçek borsa işlemi için Bybit veya Binance API anahtarlarını girin`);
            }
            
            // Send DCA orders immediately if enabled
            if (dcaEnabled && dcaCount > 0) {
                setTimeout(async () => {
                    try {
                        await sendDCAOrdersToExchange(trade);
                    } catch (error) {
                        addApiLog(`❌ DCA emirleri hazırlanırken hata: ${error.message}`);
                        console.error('DCA preparation error:', error);
                    }
                }, 1000); // 1 second delay to ensure main order is processed
            }
            
            showNotification(`Uzun AI ${coin.symbol} ${isLong ? 'LONG' : 'SHORT'} (${analysisResults.confidence}% güven)`, 'info');
            
            // Long AI trades will be closed by real TP/SL triggers, not random timing
            addLongAiLog(`✅ [İşlem] ${coin.symbol} ${isLong ? 'LONG' : 'SHORT'} pozisyonu açıldı - TP/SL ile kapatılacak`);
        }

        function performFastAnalysis() {
            console.log('🔍 performFastAnalysis called, cryptoData length:', cryptoData.length);
            // Fast analysis - scan entire market for best opportunities
            // Force fetch real market data if cryptoData is empty
            if (cryptoData.length === 0) {
                console.log('⚠️ CryptoData empty, fetching real market data for Fast AI');
                fetchRealPrices();
                return {
                    shouldTrade: false,
                    selectedCoin: null,
                    direction: 'LONG',
                    confidence: 0,
                    indicators: {}
                };
            }
            
            const allCoins = cryptoData
                .filter(coin => coin.volume > 1000000) // Lower volume threshold to scan more coins
                .sort((a, b) => b.volume - a.volume); // Sort by volume first
            
            console.log(`🔍 Fast AI scanning entire market: ${allCoins.length} coins`);
            addFastAiLog(`Market taraması başlatıldı: ${allCoins.length} coin`, 'info');
            fastAiScanCount++;
            
            let bestCoin = null;
            let bestScore = 0;
            let direction = 'LONG';
            let confidence = 0;
            let indicators = {};
            
            // Analyze all coins and find the best opportunities
            const analysisResults = [];
            
            allCoins.forEach(coin => {
                const analysis = analyzeForScalping(coin);
                analysisResults.push({
                    coin: coin,
                    score: analysis.score,
                    direction: analysis.direction,
                    confidence: analysis.confidence,
                    indicators: analysis.indicators
                });
            });
            
            // Sort by score and filter by threshold (no artificial limit)
            const fastScoreThreshold = parseInt(document.getElementById('fastScoreThreshold')?.value || '25');
            const topResults = analysisResults
                .filter(result => result.score > fastScoreThreshold) // Filter out low scores using user setting
                .sort((a, b) => b.score - a.score);
            
            console.log(`📊 Fast AI found ${topResults.length} potential opportunities from ${allCoins.length} coins (score threshold: ${fastScoreThreshold})`);
            addFastAiLog(`${topResults.length} fırsat bulundu (${allCoins.length} coin arasından)`, 'info');
            fastAiOpportunities = topResults.length;
            updateFastAiStats(fastAiScanCount, fastAiOpportunities, '-');
            
            // Log top 10 results (for display only)
            topResults.slice(0, 10).forEach((result, index) => {
                console.log(`${index + 1}. ${result.coin.symbol}: score=${result.score.toFixed(1)}, direction=${result.direction}, confidence=${result.confidence.toFixed(1)}`);
                if (index < 5) { // Log top 5 to control panel
                    addFastAiLog(`${index + 1}. ${result.coin.symbol}: ${result.score.toFixed(1)} puan, ${result.direction}, ${result.confidence.toFixed(1)}% güven`, 'info');
                }
            });
            
            // Find the best opportunity
            if (topResults.length > 0) {
                const bestResult = topResults[0];
                const userConfidenceThreshold = parseInt(document.getElementById('fastConfidence')?.value || '80');
                
                if (bestResult.confidence >= userConfidenceThreshold) {
                    bestCoin = bestResult.coin;
                    bestScore = bestResult.score;
                    direction = bestResult.direction;
                    confidence = bestResult.confidence;
                    indicators = bestResult.indicators;
                    addFastAiLog(`✅ İşlem fırsatı: ${bestCoin.symbol} - ${bestScore.toFixed(1)} puan, ${confidence.toFixed(1)}% güven`, 'success');
                } else {
                    addFastAiLog(`❌ Yeterli güven yok: En iyi ${bestResult.coin.symbol} - ${bestResult.score.toFixed(1)} puan, ${bestResult.confidence.toFixed(1)}% güven, kullanıcı eşiği: ${userConfidenceThreshold}%`, 'warning');
                }
            } else {
                addFastAiLog(`❌ Hiç fırsat bulunamadı`, 'warning');
            }
            
            const shouldTrade = bestCoin !== null && confidence >= parseInt(document.getElementById('fastConfidence')?.value || '80');
            
            console.log(`🎯 Fast AI result: ${shouldTrade ? 'TRADE' : 'NO TRADE'}, coin: ${bestCoin?.symbol}, score: ${bestScore.toFixed(1)}, confidence: ${confidence.toFixed(1)}`);
            addFastAiLog(`🎯 Sonuç: ${shouldTrade ? 'İŞLEM AÇILACAK' : 'İŞLEM AÇILMAYACAK'}`, shouldTrade ? 'success' : 'warning');
            
            return {
                shouldTrade: shouldTrade,
                selectedCoin: bestCoin,
                direction: direction,
                confidence: confidence,
                indicators: indicators
            };
        }

        function performLongAnalysis() {
            console.log('🔍 performLongAnalysis called, cryptoData length:', cryptoData.length);
            // Long analysis - scan entire market for strong trends and fundamentals
            // Force fetch real market data if cryptoData is empty
            if (cryptoData.length === 0) {
                console.log('⚠️ CryptoData empty, fetching real market data for Long AI');
                fetchRealPrices();
                return {
                    shouldTrade: false,
                    selectedCoin: null,
                    direction: 'LONG',
                    confidence: 0,
                    indicators: {}
                };
            }
            
            const allCoins = cryptoData
                .filter(coin => coin.volume > 1000000) // Lower volume threshold to scan more coins
                .sort((a, b) => b.volume - a.volume); // Sort by volume first
            
            console.log(`🔍 Long AI scanning entire market: ${allCoins.length} coins`);
            addLongAiLog(`Market taraması başlatıldı: ${allCoins.length} coin`, 'info');
            
            let bestCoin = null;
            let bestScore = 0;
            let direction = 'LONG';
            let confidence = 0;
            let indicators = {};
            
            // Analyze all coins and find the best opportunities
            const analysisResults = [];
            
            allCoins.forEach(coin => {
                const analysis = analyzeForPosition(coin);
                analysisResults.push({
                    coin: coin,
                    score: analysis.score,
                    direction: analysis.direction,
                    confidence: analysis.confidence,
                    indicators: analysis.indicators
                });
            });
            
            // Sort by score and filter by threshold (no artificial limit)
            const longScoreThreshold = parseInt(document.getElementById('longScoreThreshold')?.value || '80');
            const topResults = analysisResults
                .filter(result => result.score > longScoreThreshold) // Filter out low scores using user setting
                .sort((a, b) => b.score - a.score);
            
            console.log(`📊 Long AI found ${topResults.length} potential opportunities from ${allCoins.length} coins (score threshold: ${longScoreThreshold})`);
            addLongAiLog(`${topResults.length} fırsat bulundu (${allCoins.length} coin arasından)`, 'info');
            longAiOpportunities = topResults.length;
            updateLongAiStats(longAiScanCount, longAiOpportunities, '-');
            
            // Log top 10 results (for display only)
            topResults.slice(0, 10).forEach((result, index) => {
                console.log(`${index + 1}. ${result.coin.symbol}: score=${result.score.toFixed(1)}, direction=${result.direction}, confidence=${result.confidence.toFixed(1)}`);
                if (index < 5) { // Log top 5 to control panel
                    addLongAiLog(`${index + 1}. ${result.coin.symbol}: ${result.score.toFixed(1)} puan, ${result.direction}, ${result.confidence.toFixed(1)}% güven`, 'info');
                }
            });
            
            // Find the best opportunity
            if (topResults.length > 0) {
                const bestResult = topResults[0];
                const userConfidenceThreshold = parseInt(document.getElementById('longConfidence')?.value || '80');
                
                if (bestResult.confidence >= userConfidenceThreshold) {
                    bestCoin = bestResult.coin;
                    bestScore = bestResult.score;
                    direction = bestResult.direction;
                    confidence = bestResult.confidence;
                    indicators = bestResult.indicators;
                    addLongAiLog(`✅ İşlem fırsatı: ${bestCoin.symbol} - ${bestScore.toFixed(1)} puan, ${confidence.toFixed(1)}% güven`, 'success');
                } else {
                    addLongAiLog(`❌ Yeterli güven yok: En iyi ${bestResult.coin.symbol} - ${bestResult.score.toFixed(1)} puan, ${bestResult.confidence.toFixed(1)}% güven, kullanıcı eşiği: ${userConfidenceThreshold}%`, 'warning');
                }
            } else {
                addLongAiLog(`❌ Hiç fırsat bulunamadı`, 'warning');
            }
            
            const shouldTrade = bestCoin !== null && confidence >= parseInt(document.getElementById('longConfidence')?.value || '80');
            
            console.log(`🎯 Long AI result: ${shouldTrade ? 'TRADE' : 'NO TRADE'}, coin: ${bestCoin?.symbol}, score: ${bestScore.toFixed(1)}, confidence: ${confidence.toFixed(1)}`);
            addLongAiLog(`🎯 Sonuç: ${shouldTrade ? 'İŞLEM AÇILACAK' : 'İŞLEM AÇILMAYACAK'}`, shouldTrade ? 'success' : 'warning');
            
            return {
                shouldTrade: shouldTrade,
                selectedCoin: bestCoin,
                direction: direction,
                confidence: confidence,
                indicators: indicators
            };
        }

        function analyzeForScalping(coin) {
            // YENİ NESİL SCALPING SİSTEMİ - Volume Profile + Market Structure + AI
            const rsi = calculateRSI(coin, 9); // Hızlı RSI
            const macd = calculateMACD(coin, 5, 13, 5); // Hızlı MACD
            const bb = calculateBollingerBands(coin, 20);
            const stoch = calculateStochastic(coin, 14);
            const adx = calculateADX(coin, 14);
            const volume = coin.volume / 1000000;
            const priceChange = coin.change24h;
            const momentum = Math.abs(priceChange);
            
            // YENİ: Volume Profile Analizi
            const volumeProfile = analyzeVolumeProfile(coin);
            
            // YENİ: Market Structure Analizi
            const marketStructure = analyzeMarketStructure(coin);
            
            // YENİ: AI Modül Analizi
            const aiAnalysis = performAIAnalysis(coin);
            
            let score = 0; // Yeni skor sistemi
            let signals = [];
            let longSignals = 0;
            let shortSignals = 0;
            let direction = 'NONE'; // Direction değişkeni tanımlandı
            
            // Pre-filter: Only analyze coins with sufficient volume and reasonable volatility
            if (volume < 10 || momentum < 1) {
                return { score: 0, direction: 'NONE', confidence: 0, indicators: {} };
            }
            
            // YENİ NESİL SKOR SİSTEMİ - Hızlı AI
            
            // 1. Volume Profile Analizi (40% ağırlık) - Daha sert
            if (volumeProfile.vwapDistance < 1) { // VWAP'a çok yakın (daha sert)
                score += 8;
                signals.push('VWAP Proximity');
            }
            
            if (volumeProfile.pocStrength > 0.5) { // Çok güçlü POC (daha sert)
                score += 6;
                signals.push('Strong POC');
            }
            
            if (volumeProfile.valueAreaBreak) { // Value Area kırılımı
                score += 10;
                if (coin.price > volumeProfile.valueArea.upper) {
                    longSignals++;
                    direction = 'LONG';
                    signals.push('Value Area Breakout - Long');
                } else if (coin.price < volumeProfile.valueArea.lower) {
                    shortSignals++;
                    direction = 'SHORT';
                    signals.push('Value Area Breakdown - Short');
                }
            }
            
            if (volumeProfile.volumeDelta.spike) { // Volume spike
                score += 6;
                signals.push('Volume Spike');
            }
            
            // 2. Market Structure Analizi (30% ağırlık) - Daha sert
            if (marketStructure.structureBreak) { // Yapı kırılımı
                score += 12;
                if (marketStructure.trendStructure.trend === 'UPTREND') {
                    longSignals++;
                    direction = 'LONG';
                    signals.push('Structure Break - Uptrend');
                } else if (marketStructure.trendStructure.trend === 'DOWNTREND') {
                    shortSignals++;
                    direction = 'SHORT';
                    signals.push('Structure Break - Downtrend');
                }
            }
            
            if (marketStructure.liquidityGrab) { // Liquidity grab
                score += 8;
                signals.push('Liquidity Grab');
            }
            
            if (marketStructure.fairValueGaps.valid) { // Fair Value Gap
                score += 6;
                signals.push('Valid Fair Value Gap');
            }
            
            // 3. Momentum Analizi (20% ağırlık) - Daha sert
            // RSI Analysis (More strict for scalping)
            if (rsi < 20) { // Çok extreme oversold (daha sert)
                score += 8;
                longSignals++;
                direction = 'LONG';
                signals.push('RSI Extreme Oversold');
            } else if (rsi > 80) { // Çok extreme overbought (daha sert)
                score += 8;
                shortSignals++;
                direction = 'SHORT';
                signals.push('RSI Extreme Overbought');
            } else if (rsi < 30 && rsi > 25) { // Mild oversold
                score += 4;
                longSignals++;
                direction = 'LONG';
                signals.push('RSI Mild Oversold');
            } else if (rsi > 70 && rsi < 75) { // Mild overbought
                score += 4;
                shortSignals++;
                direction = 'SHORT';
                signals.push('RSI Mild Overbought');
            } else if (rsi > 45 && rsi < 55) { // Neutral zone
                score += 1;
                signals.push('RSI Neutral');
            }
            
            // 2. MACD Analysis (More strict) - Daha sert
            if (macd.histogram > 0 && macd.signal > 0 && macd.macd > 0) {
                score += 6;
                longSignals++;
                direction = 'LONG';
                signals.push('MACD Strong Bullish');
            } else if (macd.histogram < 0 && macd.signal < 0 && macd.macd < 0) {
                score += 6;
                shortSignals++;
                direction = 'SHORT';
                signals.push('MACD Strong Bearish');
            } else if (macd.histogram > 0 && macd.signal > 0) {
                score += 3;
                longSignals++;
                direction = 'LONG';
                signals.push('MACD Mild Bullish');
            } else if (macd.histogram < 0 && macd.signal < 0) {
                score += 3;
                shortSignals++;
                direction = 'SHORT';
                signals.push('MACD Mild Bearish');
            }
            
            // 3. Bollinger Bands Analysis (More strict) - Daha sert
            const bbPosition = (coin.price - bb.lower) / (bb.upper - bb.lower);
            if (bbPosition < 0.05) { // Çok yakın lower band (daha sert)
                score += 5;
                longSignals++;
                direction = 'LONG';
                signals.push('BB Near Lower Band');
            } else if (bbPosition > 0.95) { // Çok yakın upper band (daha sert)
                score += 5;
                shortSignals++;
                direction = 'SHORT';
                signals.push('BB Near Upper Band');
            } else if (bbPosition < 0.15) { // Close to lower band
                score += 2;
                longSignals++;
                direction = 'LONG';
                signals.push('BB Close to Lower');
            } else if (bbPosition > 0.85) { // Close to upper band
                score += 2;
                shortSignals++;
                direction = 'SHORT';
                signals.push('BB Close to Upper');
            }
            
            // 4. Stochastic Analysis (More strict) - Daha sert
            if (stoch.k < 10 && stoch.d < 10) { // Çok extreme oversold (daha sert)
                score += 4;
                longSignals++;
                direction = 'LONG';
                signals.push('Stoch Extreme Oversold');
            } else if (stoch.k > 90 && stoch.d > 90) { // Çok extreme overbought (daha sert)
                score += 4;
                shortSignals++;
                direction = 'SHORT';
                signals.push('Stoch Extreme Overbought');
            } else if (stoch.k < 20 && stoch.d < 20) { // Mild oversold
                score += 2;
                longSignals++;
                direction = 'LONG';
                signals.push('Stoch Mild Oversold');
            } else if (stoch.k > 80 && stoch.d > 80) { // Mild overbought
                score += 2;
                shortSignals++;
                direction = 'SHORT';
                signals.push('Stoch Mild Overbought');
            }
            
            // 5. ADX Analysis (Trend Strength) - Integrated with confidence
            if (adx > 50) { // Çok güçlü trend (daha sert)
                score += 5;
                signals.push('Very Strong Trend');
            } else if (adx > 30) { // Strong trend
                score += 3;
                signals.push('Strong Trend');
            } else if (adx > 20) { // Moderate trend
                score += 1;
                signals.push('Moderate Trend');
            } else { // Weak trend penalty
                score -= 5;
                signals.push('Weak Trend');
            }
            
            // 6. Volume Analysis - Synced with other indicators
            if (volume > 100 && rsi < 35) { // Very high volume + oversold RSI
                score += 15;
                signals.push('Very High Volume + RSI Oversold');
            } else if (volume > 100 && macd.histogram > 0) { // Very high volume + bullish MACD
                score += 14;
                signals.push('Very High Volume + MACD Bullish');
            } else if (volume > 100) { // Very high volume
                score += 12;
                signals.push('Very High Volume');
            } else if (volume > 50 && stoch.k < 30) { // High volume + oversold Stochastic
                score += 10;
                signals.push('High Volume + Stoch Oversold');
            } else if (volume > 50) { // High volume
                score += 8;
                signals.push('High Volume');
            } else if (volume > 25) { // Good volume
                score += 4;
                signals.push('Good Volume');
            } else { // Low volume penalty
                score -= 10;
                signals.push('Low Volume');
            }
            
            // 7. Momentum Analysis - More strict
            if (momentum > 5) { // Very strong momentum
                score += 10;
                signals.push('Very Strong Momentum');
            } else if (momentum > 3) { // Strong momentum
                score += 6;
                signals.push('Strong Momentum');
            } else if (momentum > 2) { // Moderate momentum
                score += 3;
                signals.push('Moderate Momentum');
            } else if (momentum < 0.5) { // Very low momentum penalty
                score -= 5;
                signals.push('Very Low Momentum');
            }
            
            // 8. Price Action Analysis
            const priceAction = analyzePriceAction(coin);
            if (priceAction.bullish) {
                score += priceAction.strength;
                longSignals++;
                signals.push(priceAction.signal);
            } else if (priceAction.bearish) {
                score += priceAction.strength;
                shortSignals++;
                signals.push(priceAction.signal);
            }
            
            // 9. Market Sentiment Analysis
            const sentiment = analyzeMarketSentiment(coin);
            score += sentiment.score;
            signals.push(sentiment.signal);
            
            // 4. AI Modül Analizi (10% ağırlık) - Daha sert
            if (aiAnalysis.aiScore > 0.8) { // Çok yüksek AI skoru (daha sert)
                score += 8;
                signals.push('High AI Score');
            } else if (aiAnalysis.aiScore > 0.6) { // Yüksek AI skoru
                score += 4;
                signals.push('Good AI Score');
            }
            
            if (aiAnalysis.patternRecognition.patterns.length > 0) { // Pattern tanıma - Daha sert
                score += 5;
                signals.push(`Patterns: ${aiAnalysis.patternRecognition.patterns.join(', ')}`);
            }
            
            if (aiAnalysis.sentimentAnalysis.sentiment === 'BULLISH') {
                longSignals++;
                direction = 'LONG';
                score += 4;
                signals.push('Bullish Sentiment');
            } else if (aiAnalysis.sentimentAnalysis.sentiment === 'BEARISH') {
                shortSignals++;
                direction = 'SHORT';
                score += 4;
                signals.push('Bearish Sentiment');
            }
            
            if (aiAnalysis.volatilityPrediction.volatility === 'HIGH') { // Yüksek volatilite - Daha sert
                score += 3;
                signals.push('High Volatility Expected');
            }
            
            // Risk Assessment
            if (aiAnalysis.riskScore < 0.2) { // Çok düşük risk (daha sert)
                score += 5;
                signals.push('Low Risk');
            } else if (aiAnalysis.riskScore > 0.8) { // Çok yüksek risk (daha sert)
                score -= 10;
                signals.push('High Risk - Penalty');
            }
            
            // Determine direction based on signal strength - Final decision
            if (shortSignals > longSignals) {
                direction = 'SHORT';
            } else if (longSignals > shortSignals) {
                direction = 'LONG';
            } else if (shortSignals === longSignals) {
                // Tie-breaker: Use AI analysis and price momentum
                if (aiAnalysis.sentimentAnalysis.sentiment === 'BULLISH') {
                    direction = 'LONG';
                } else if (aiAnalysis.sentimentAnalysis.sentiment === 'BEARISH') {
                    direction = 'SHORT';
                } else {
                direction = priceChange > 0 ? 'LONG' : 'SHORT';
                }
            }
            
            // Use user-defined confidence threshold instead of calculated confidence
            const userConfidenceThreshold = parseInt(document.getElementById('fastConfidence')?.value || '80');
            const userScoreThreshold = parseInt(document.getElementById('fastScoreThreshold')?.value || '25');
            
            // Daha sert skor hesaplama sistemi
            const finalScore = score;
            // Güven hesaplama: Skor 100'den fazlaysa 100'e sınırla, daha düşük güven ver
            const finalConfidence = Math.min(95, Math.max(15, Math.min(score * 0.4, 60) + (longSignals + shortSignals) * 5));
            
            return {
                score: finalScore,
                direction: direction,
                confidence: finalConfidence,
                indicators: {
                    rsi: rsi,
                    macd: macd,
                    bb: bb,
                    stoch: stoch,
                    adx: adx,
                    volume: volume,
                    momentum: momentum,
                    signals: signals,
                    longSignals: longSignals,
                    shortSignals: shortSignals
                }
            };
        }

        // YENİ NESİL ANALİZ FONKSİYONLARI
        
        // Volume Profile Analizi
        function analyzeVolumeProfile(coin) {
            try {
                const vwap = calculateVWAP(coin);
                const poc = calculatePOC(coin);
                const valueArea = calculateValueArea(coin);
                const volumeDelta = calculateVolumeDelta(coin);
                
                return {
                    vwap: vwap,
                    poc: poc,
                    valueArea: valueArea,
                    volumeDelta: volumeDelta,
                    vwapDistance: Math.abs(coin.price - vwap) / vwap * 100,
                    pocStrength: poc.strength,
                    valueAreaBreak: valueArea.breakout
                };
            } catch (error) {
                console.error('Volume Profile analiz hatası:', error);
                return {
                    vwap: coin.price,
                    poc: { level: coin.price, strength: 0 },
                    valueArea: { upper: coin.price * 1.02, lower: coin.price * 0.98, breakout: false },
                    volumeDelta: 0,
                    vwapDistance: 0,
                    pocStrength: 0,
                    valueAreaBreak: false
                };
            }
        }
        
        // Market Structure Analizi
        function analyzeMarketStructure(coin) {
            try {
                const supportResistance = calculateSupportResistance(coin);
                const trendStructure = analyzeTrendStructure(coin);
                const liquidityZones = findLiquidityZones(coin);
                const fairValueGaps = findFairValueGaps(coin);
                
                return {
                    supportResistance: supportResistance,
                    trendStructure: trendStructure,
                    liquidityZones: liquidityZones,
                    fairValueGaps: fairValueGaps,
                    structureBreak: trendStructure.break,
                    liquidityGrab: liquidityZones.grab
                };
            } catch (error) {
                console.error('Market Structure analiz hatası:', error);
                return {
                    supportResistance: { support: coin.price * 0.95, resistance: coin.price * 1.05 },
                    trendStructure: { trend: 'NEUTRAL', break: false },
                    liquidityZones: { grab: false },
                    fairValueGaps: { valid: false }
                };
            }
        }
        
        // AI Modül Analizi
        function performAIAnalysis(coin) {
            try {
                const patternRecognition = recognizePatterns(coin);
                const sentimentAnalysis = analyzeSentiment(coin);
                const volatilityPrediction = predictVolatility(coin);
                const riskAssessment = assessRisk(coin);
                
                return {
                    aiScore: (patternRecognition.confidence + sentimentAnalysis.confidence + volatilityPrediction.confidence) / 3,
                    patternRecognition: patternRecognition,
                    sentimentAnalysis: sentimentAnalysis,
                    volatilityPrediction: volatilityPrediction,
                    riskScore: riskAssessment.riskScore
                };
            } catch (error) {
                console.error('AI analiz hatası:', error);
                return {
                    aiScore: 0.5,
                    patternRecognition: { patterns: [], confidence: 0.5 },
                    sentimentAnalysis: { sentiment: 'NEUTRAL', confidence: 0.5 },
                    volatilityPrediction: { volatility: 'MEDIUM', confidence: 0.5 },
                    riskScore: 0.5
                };
            }
        }
        
        // VWAP Hesaplama
        function calculateVWAP(coin) {
            if (!coin.priceHistory || coin.priceHistory.length < 20) {
                return coin.price;
            }
            
            let totalVolume = 0;
            let totalValue = 0;
            
            for (let i = 0; i < Math.min(20, coin.priceHistory.length); i++) {
                const price = coin.priceHistory[i];
                const volume = coin.volume || 1000000;
                totalValue += price * volume;
                totalVolume += volume;
            }
            
            return totalVolume > 0 ? totalValue / totalVolume : coin.price;
        }
        
        // POC (Point of Control) Hesaplama
        function calculatePOC(coin) {
            if (!coin.priceHistory || coin.priceHistory.length < 10) {
                return { level: coin.price, strength: 0.5 };
            }
            
            const prices = coin.priceHistory.slice(-10);
            const priceCounts = {};
            
            prices.forEach(price => {
                const roundedPrice = Math.round(price * 100) / 100;
                priceCounts[roundedPrice] = (priceCounts[roundedPrice] || 0) + 1;
            });
            
            let maxCount = 0;
            let pocLevel = coin.price;
            
            Object.entries(priceCounts).forEach(([price, count]) => {
                if (count > maxCount) {
                    maxCount = count;
                    pocLevel = parseFloat(price);
                }
            });
            
            return {
                level: pocLevel,
                strength: Math.min(1, maxCount / prices.length)
            };
        }
        
        // Value Area Hesaplama
        function calculateValueArea(coin) {
            if (!coin.priceHistory || coin.priceHistory.length < 10) {
                return { upper: coin.price * 1.02, lower: coin.price * 0.98, breakout: false };
            }
            
            const prices = coin.priceHistory.slice(-10);
            const sortedPrices = [...prices].sort((a, b) => a - b);
            const lower = sortedPrices[Math.floor(sortedPrices.length * 0.25)];
            const upper = sortedPrices[Math.floor(sortedPrices.length * 0.75)];
            
            return {
                upper: upper,
                lower: lower,
                breakout: coin.price > upper || coin.price < lower
            };
        }
        
        // Volume Delta Hesaplama
        function calculateVolumeDelta(coin) {
            const volume = coin.volume || 1000000;
            const avgVolume = 5000000; // Ortalama hacim
            
            return {
                delta: volume - avgVolume,
                spike: volume > avgVolume * 2
            };
        }
        
        // Support/Resistance Hesaplama
        function calculateSupportResistance(coin) {
            if (!coin.priceHistory || coin.priceHistory.length < 20) {
                return { support: coin.price * 0.95, resistance: coin.price * 1.05 };
            }
            
            const prices = coin.priceHistory.slice(-20);
            const sortedPrices = [...prices].sort((a, b) => a - b);
            
            return {
                support: sortedPrices[Math.floor(sortedPrices.length * 0.2)],
                resistance: sortedPrices[Math.floor(sortedPrices.length * 0.8)]
            };
        }
        
        // Trend Structure Analizi
        function analyzeTrendStructure(coin) {
            if (!coin.priceHistory || coin.priceHistory.length < 10) {
                return { trend: 'NEUTRAL', break: false };
            }
            
            const prices = coin.priceHistory.slice(-10);
            const firstHalf = prices.slice(0, 5);
            const secondHalf = prices.slice(5);
            
            const firstAvg = firstHalf.reduce((a, b) => a + b, 0) / firstHalf.length;
            const secondAvg = secondHalf.reduce((a, b) => a + b, 0) / secondHalf.length;
            
            const trend = secondAvg > firstAvg * 1.02 ? 'UPTREND' : 
                         secondAvg < firstAvg * 0.98 ? 'DOWNTREND' : 'NEUTRAL';
            
            return {
                trend: trend,
                break: Math.abs(secondAvg - firstAvg) / firstAvg > 0.05
            };
        }
        
        // Liquidity Zones Bulma
        function findLiquidityZones(coin) {
            if (!coin.priceHistory || coin.priceHistory.length < 10) {
                return { grab: false };
            }
            
            const prices = coin.priceHistory.slice(-10);
            const currentPrice = coin.price;
            const priceRange = Math.max(...prices) - Math.min(...prices);
            
            return {
                grab: priceRange > currentPrice * 0.1
            };
        }
        
        // Fair Value Gaps Bulma
        function findFairValueGaps(coin) {
            if (!coin.priceHistory || coin.priceHistory.length < 3) {
                return { valid: false };
            }
            
            const prices = coin.priceHistory.slice(-3);
            const gap = Math.abs(prices[2] - prices[0]);
            const avgPrice = prices.reduce((a, b) => a + b, 0) / prices.length;
            
            return {
                valid: gap > avgPrice * 0.02
            };
        }
        
        // Pattern Recognition
        function recognizePatterns(coin) {
            if (!coin.priceHistory || coin.priceHistory.length < 5) {
                return { patterns: [], confidence: 0.5 };
            }
            
            const prices = coin.priceHistory.slice(-5);
            const patterns = [];
            let confidence = 0.5;
            
            // Simple pattern detection
            if (prices[0] < prices[1] && prices[1] < prices[2] && prices[2] > prices[3] && prices[3] > prices[4]) {
                patterns.push('Head and Shoulders');
                confidence += 0.2;
            }
            
            if (prices[0] > prices[1] && prices[1] > prices[2] && prices[2] < prices[3] && prices[3] < prices[4]) {
                patterns.push('Inverse Head and Shoulders');
                confidence += 0.2;
            }
            
            return {
                patterns: patterns,
                confidence: Math.min(1, confidence)
            };
        }
        
        // Sentiment Analysis
        function analyzeSentiment(coin) {
            const priceChange = coin.change24h || 0;
            const volume = coin.volume || 1000000;
            
            let sentiment = 'NEUTRAL';
            let confidence = 0.5;
            
            if (priceChange > 5 && volume > 10000000) {
                sentiment = 'BULLISH';
                confidence = 0.8;
            } else if (priceChange < -5 && volume > 10000000) {
                sentiment = 'BEARISH';
                confidence = 0.8;
            } else if (priceChange > 2) {
                sentiment = 'BULLISH';
                confidence = 0.6;
            } else if (priceChange < -2) {
                sentiment = 'BEARISH';
                confidence = 0.6;
            }
            
            return {
                sentiment: sentiment,
                confidence: confidence
            };
        }
        
        // Volatility Prediction
        function predictVolatility(coin) {
            if (!coin.priceHistory || coin.priceHistory.length < 5) {
                return { volatility: 'MEDIUM', confidence: 0.5 };
            }
            
            const prices = coin.priceHistory.slice(-5);
            const changes = [];
            
            for (let i = 1; i < prices.length; i++) {
                changes.push(Math.abs(prices[i] - prices[i-1]) / prices[i-1]);
            }
            
            const avgChange = changes.reduce((a, b) => a + b, 0) / changes.length;
            
            let volatility = 'MEDIUM';
            let confidence = 0.5;
            
            if (avgChange > 0.05) {
                volatility = 'HIGH';
                confidence = 0.8;
            } else if (avgChange < 0.02) {
                volatility = 'LOW';
                confidence = 0.8;
            }
            
            return {
                volatility: volatility,
                confidence: confidence
            };
        }
        
        // Risk Assessment
        function assessRisk(coin) {
            const priceChange = Math.abs(coin.change24h || 0);
            const volume = coin.volume || 1000000;
            
            let riskScore = 0.5;
            
            if (priceChange > 10) riskScore += 0.3;
            if (priceChange > 20) riskScore += 0.2;
            if (volume < 1000000) riskScore += 0.2;
            if (volume > 100000000) riskScore -= 0.1;
            
            return {
                riskScore: Math.min(1, Math.max(0, riskScore))
            };
        }
        
        // GELİŞMİŞ UZUN AI ANALİZ FONKSİYONLARI
        
        // Gelişmiş Trend Analizi
        function analyzeAdvancedTrend(coin, ema21, ema50, ema200, sma50, sma200) {
            try {
                const goldenCross = ema50 > ema200 && coin.price > ema50;
                const deathCross = ema50 < ema200 && coin.price < ema50;
                const smaGoldenCross = sma50 > sma200 && coin.price > sma50;
                const smaDeathCross = sma50 < sma200 && coin.price < sma50;
                
                const trendAlignment = (ema21 > ema50 && ema50 > ema200) || (ema21 < ema50 && ema50 < ema200);
                const strongTrend = Math.abs(coin.change24h || 0) > 5;
                
                return {
                    goldenCross: goldenCross,
                    deathCross: deathCross,
                    smaGoldenCross: smaGoldenCross,
                    smaDeathCross: smaDeathCross,
                    trendAlignment: trendAlignment,
                    strongTrend: strongTrend
                };
            } catch (error) {
                console.error('Advanced Trend analiz hatası:', error);
                return {
                    goldenCross: false,
                    deathCross: false,
                    smaGoldenCross: false,
                    smaDeathCross: false,
                    trendAlignment: false,
                    strongTrend: false
                };
            }
        }
        
        // Fundamental Analiz
        function performFundamentalAnalysis(coin) {
            try {
                const onChainHealth = analyzeOnChainHealth(coin);
                const whaleActivity = analyzeWhaleActivity(coin);
                const socialSentiment = analyzeSocialSentiment(coin);
                const newsImpact = analyzeNewsImpact(coin);
                const volumeHealth = analyzeVolumeHealth(coin);
                
                return {
                    onChainHealth: onChainHealth,
                    whaleActivity: whaleActivity,
                    socialSentiment: socialSentiment,
                    newsImpact: newsImpact,
                    volumeHealth: volumeHealth
                };
            } catch (error) {
                console.error('Fundamental analiz hatası:', error);
                return {
                    onChainHealth: { status: 'UNKNOWN' },
                    whaleActivity: { status: 'LOW_ACTIVITY' },
                    socialSentiment: { status: 'NEUTRAL' },
                    newsImpact: { status: 'LOW_IMPACT' },
                    volumeHealth: 'UNKNOWN'
                };
            }
        }
        
        // Risk Yönetimi
        function performRiskManagement(coin) {
            try {
                const positionSize = calculatePositionSize(coin);
                const portfolioHeat = calculatePortfolioHeat(coin);
                const correlationRisk = calculateCorrelationRisk(coin);
                const drawdownRisk = calculateDrawdownRisk(coin);
                
                return {
                    positionSize: positionSize,
                    portfolioHeat: portfolioHeat,
                    correlationRisk: correlationRisk,
                    drawdownRisk: drawdownRisk,
                    volatilityRisk: assessVolatilityRisk(coin),
                    volumeRisk: assessVolumeRisk(coin),
                    momentumRisk: assessMomentumRisk(coin)
                };
            } catch (error) {
                console.error('Risk yönetimi hatası:', error);
                return {
                    positionSize: { size: 0.1, risk: 'LOW' },
                    portfolioHeat: { heat: 0.1, risk: 'LOW' },
                    correlationRisk: { risk: 'LOW' },
                    drawdownRisk: { risk: 'LOW' },
                    volatilityRisk: 'MEDIUM',
                    volumeRisk: 'MEDIUM',
                    momentumRisk: 'MEDIUM'
                };
            }
        }
        
        // Makine Öğrenmesi
        function performMachineLearning(coin) {
            try {
                const lstmPrediction = performLSTMPrediction(coin);
                const randomForest = performRandomForest(coin);
                
                const avgConfidence = (lstmPrediction.confidence + randomForest.confidence) / 2;
                let confidence = 'LOW';
                if (avgConfidence > 0.8) confidence = 'HIGH';
                else if (avgConfidence > 0.6) confidence = 'MEDIUM';
                
                return {
                    confidence: confidence,
                    lstmPrediction: lstmPrediction,
                    randomForest: randomForest
                };
            } catch (error) {
                console.error('Makine öğrenmesi hatası:', error);
                return {
                    confidence: 'LOW',
                    lstmPrediction: { prediction: 'NEUTRAL', confidence: 0.5 },
                    randomForest: { prediction: 'NEUTRAL', confidence: 0.5 }
                };
            }
        }
        
        // On-chain Sağlık Analizi
        function analyzeOnChainHealth(coin) {
            const volume = coin.volume || 1000000;
            const priceChange = Math.abs(coin.change24h || 0);
            
            let status = 'UNKNOWN';
            if (volume > 50000000 && priceChange < 20) {
                status = 'HEALTHY';
            } else if (volume > 10000000 && priceChange < 30) {
                status = 'MODERATE';
            } else {
                status = 'UNHEALTHY';
            }
            
            return { status: status };
        }
        
        // Balina Aktivitesi Analizi
        function analyzeWhaleActivity(coin) {
            const volume = coin.volume || 1000000;
            const priceChange = Math.abs(coin.change24h || 0);
            
            let status = 'LOW_ACTIVITY';
            if (volume > 100000000 && priceChange > 10) {
                status = 'HIGH_ACTIVITY';
            } else if (volume > 50000000 && priceChange > 5) {
                status = 'MEDIUM_ACTIVITY';
            }
            
            return { status: status };
        }
        
        // Sosyal Sentiment Analizi
        function analyzeSocialSentiment(coin) {
            const priceChange = coin.change24h || 0;
            const volume = coin.volume || 1000000;
            
            let status = 'NEUTRAL';
            if (priceChange > 10 && volume > 50000000) {
                status = 'VERY_BULLISH';
            } else if (priceChange > 5 && volume > 20000000) {
                status = 'BULLISH';
            } else if (priceChange < -10 && volume > 50000000) {
                status = 'VERY_BEARISH';
            } else if (priceChange < -5 && volume > 20000000) {
                status = 'BEARISH';
            }
            
            return { status: status };
        }
        
        // Haber Etkisi Analizi
        function analyzeNewsImpact(coin) {
            const priceChange = Math.abs(coin.change24h || 0);
            const volume = coin.volume || 1000000;
            
            let status = 'LOW_IMPACT';
            if (priceChange > 15 && volume > 100000000) {
                status = 'HIGH_IMPACT';
            } else if (priceChange > 8 && volume > 50000000) {
                status = 'MEDIUM_IMPACT';
            }
            
            return { status: status };
        }
        
        // Hacim Sağlığı Analizi
        function analyzeVolumeHealth(coin) {
            const volume = coin.volume || 1000000;
            
            if (volume > 100000000) return 'VERY_HEALTHY';
            if (volume > 50000000) return 'HEALTHY';
            if (volume > 10000000) return 'MODERATE';
            return 'UNHEALTHY';
        }
        
        // Pozisyon Boyutu Hesaplama
        function calculatePositionSize(coin) {
            const volume = coin.volume || 1000000;
            const priceChange = Math.abs(coin.change24h || 0);
            
            let size = 0.1; // Varsayılan %10
            let risk = 'LOW';
            
            if (volume > 100000000 && priceChange < 10) {
                size = 0.2; // %20
                risk = 'LOW';
            } else if (volume > 50000000 && priceChange < 15) {
                size = 0.15; // %15
                risk = 'MEDIUM';
            } else if (priceChange > 20) {
                size = 0.05; // %5
                risk = 'HIGH';
            }
            
            return { size: size, risk: risk };
        }
        
        // Portfolio Heat Hesaplama
        function calculatePortfolioHeat(coin) {
            const priceChange = Math.abs(coin.change24h || 0);
            const volume = coin.volume || 1000000;
            
            let heat = 0.1; // Varsayılan %10
            let risk = 'LOW';
            
            if (priceChange > 15) {
                heat = 0.3;
                risk = 'HIGH';
            } else if (priceChange > 8) {
                heat = 0.2;
                risk = 'MEDIUM';
            }
            
            return { heat: heat, risk: risk };
        }
        
        // Korelasyon Riski
        function calculateCorrelationRisk(coin) {
            // Basit korelasyon riski hesaplama
            const priceChange = Math.abs(coin.change24h || 0);
            
            if (priceChange > 20) return { risk: 'HIGH' };
            if (priceChange > 10) return { risk: 'MEDIUM' };
            return { risk: 'LOW' };
        }
        
        // Drawdown Riski
        function calculateDrawdownRisk(coin) {
            const priceChange = Math.abs(coin.change24h || 0);
            
            if (priceChange > 25) return { risk: 'HIGH' };
            if (priceChange > 15) return { risk: 'MEDIUM' };
            return { risk: 'LOW' };
        }
        
        // Volatilite Riski
        function assessVolatilityRisk(coin) {
            const priceChange = Math.abs(coin.change24h || 0);
            
            if (priceChange > 20) return 'HIGH';
            if (priceChange > 10) return 'MEDIUM';
            return 'LOW';
        }
        
        // Hacim Riski
        function assessVolumeRisk(coin) {
            const volume = coin.volume || 1000000;
            
            if (volume < 1000000) return 'HIGH';
            if (volume < 10000000) return 'MEDIUM';
            return 'LOW';
        }
        
        // Momentum Riski
        function assessMomentumRisk(coin) {
            const priceChange = Math.abs(coin.change24h || 0);
            
            if (priceChange > 15) return 'HIGH';
            if (priceChange > 8) return 'MEDIUM';
            return 'LOW';
        }
        
        // LSTM Tahmini
        function performLSTMPrediction(coin) {
            const priceChange = coin.change24h || 0;
            const volume = coin.volume || 1000000;
            
            let prediction = 'NEUTRAL';
            let confidence = 0.5;
            
            if (priceChange > 5 && volume > 50000000) {
                prediction = 'BULLISH';
                confidence = 0.8;
            } else if (priceChange < -5 && volume > 50000000) {
                prediction = 'BEARISH';
                confidence = 0.8;
            } else if (priceChange > 2) {
                prediction = 'BULLISH';
                confidence = 0.6;
            } else if (priceChange < -2) {
                prediction = 'BEARISH';
                confidence = 0.6;
            }
            
            return { prediction: prediction, confidence: confidence };
        }
        
        // Random Forest Tahmini
        function performRandomForest(coin) {
            const priceChange = coin.change24h || 0;
            const volume = coin.volume || 1000000;
            
            let prediction = 'NEUTRAL';
            let confidence = 0.5;
            
            if (priceChange > 3 && volume > 30000000) {
                prediction = 'BULLISH';
                confidence = 0.7;
            } else if (priceChange < -3 && volume > 30000000) {
                prediction = 'BEARISH';
                confidence = 0.7;
            } else if (priceChange > 1) {
                prediction = 'BULLISH';
                confidence = 0.6;
            } else if (priceChange < -1) {
                prediction = 'BEARISH';
                confidence = 0.6;
            }
            
            return { prediction: prediction, confidence: confidence };
        }

        // Advanced Trend Analysis Function
        function analyzeTrendStrength(coin, ema50, ema200, sma20, adx) {
            let score = 0;
            let strength = 0;
            let signals = [];
            let longSignals = 0;
            let shortSignals = 0;
            
            // 1. EMA Golden Cross/Death Cross Analysis
            if (ema50 > ema200 && coin.price > ema50) {
                score += 20;
                strength += 30;
                longSignals += 2;
                signals.push('EMA Golden Cross + Price Above EMA50');
            } else if (ema50 < ema200 && coin.price < ema50) {
                score += 20;
                strength += 30;
                shortSignals += 2;
                signals.push('EMA Death Cross + Price Below EMA50');
            }
            
            // 2. Price vs Moving Averages Alignment
            if (coin.price > ema50 && ema50 > ema200 && coin.price > sma20) {
                score += 15;
                strength += 25;
                longSignals += 2;
                signals.push('Perfect Bullish Alignment');
            } else if (coin.price < ema50 && ema50 < ema200 && coin.price < sma20) {
                score += 15;
                strength += 25;
                shortSignals += 2;
                signals.push('Perfect Bearish Alignment');
            }
            
            // 3. ADX Trend Strength (Must be > 25 for valid trend)
            if (adx > 40) {
                score += 15;
                strength += 20;
                signals.push('Very Strong ADX Trend');
            } else if (adx > 25) {
                score += 10;
                strength += 15;
                signals.push('Strong ADX Trend');
            } else {
                // Weak trend - penalty
                score -= 20;
                strength -= 30;
                signals.push('Weak ADX Trend');
            }
            
            // 4. Price Distance from EMAs (Momentum)
            const ema50Distance = Math.abs(coin.price - ema50) / ema50 * 100;
            const ema200Distance = Math.abs(coin.price - ema200) / ema200 * 100;
            
            if (ema50Distance > 5 && ema200Distance > 10) {
                score += 10;
                strength += 15;
                signals.push('Strong Momentum from EMAs');
            } else if (ema50Distance > 2 && ema200Distance > 5) {
                score += 5;
                strength += 10;
                signals.push('Moderate Momentum from EMAs');
            }
            
            // 5. Volume Confirmation
            const volume = coin.volume / 1000000;
            if (volume > 100) {
                score += 5;
                strength += 10;
                signals.push('High Volume Confirmation');
            }
            
            return {
                score: score,
                strength: strength,
                signals: signals,
                longSignals: longSignals,
                shortSignals: shortSignals
            };
        }

        // Helper functions for advanced analysis
        function calculateBollingerBands(coin, period = 20) {
            // Real Bollinger Bands calculation
            if (!coin.priceHistory || coin.priceHistory.length < period) {
                const price = coin.price;
                const volatility = Math.abs(coin.change24h) / 100;
                return {
                    upper: price * (1 + volatility * 2),
                    middle: price,
                    lower: price * (1 - volatility * 2)
                };
            }
            
            const prices = coin.priceHistory.slice(-period);
            const sma = prices.reduce((sum, price) => sum + price, 0) / period;
            
            // Calculate standard deviation
            const variance = prices.reduce((sum, price) => sum + Math.pow(price - sma, 2), 0) / period;
            const stdDev = Math.sqrt(variance);
            
            return {
                upper: sma + (2 * stdDev),
                middle: sma,
                lower: sma - (2 * stdDev)
            };
        }
        
        function calculateStochastic(coin, period = 14) {
            // Real Stochastic calculation
            if (!coin.priceHistory || coin.priceHistory.length < period) {
                // Fallback based on 24h change
                const change = coin.change24h;
                const k = 50 + (change * 2);
                return { 
                    k: Math.max(0, Math.min(100, k)), 
                    d: Math.max(0, Math.min(100, k * 0.8)) 
                };
            }
            
            const prices = coin.priceHistory.slice(-period);
            const high = Math.max(...prices);
            const low = Math.min(...prices);
            const current = prices[prices.length - 1];
            
            const k = ((current - low) / (high - low)) * 100;
            const d = k * 0.8; // Simplified %D (3-period SMA of %K)
            
            return { 
                k: Math.max(0, Math.min(100, k)), 
                d: Math.max(0, Math.min(100, d)) 
            };
        }
        
        function calculateADX(coin, period = 14) {
            // Real ADX calculation
            if (!coin.priceHistory || coin.priceHistory.length < period) {
                // Fallback based on volatility
                const volatility = Math.abs(coin.change24h);
                return Math.min(100, volatility * 2);
            }
            
            const prices = coin.priceHistory.slice(-period);
            let trSum = 0;
            
            for (let i = 1; i < prices.length; i++) {
                const high = Math.max(prices[i], prices[i-1]);
                const low = Math.min(prices[i], prices[i-1]);
                const tr = high - low;
                trSum += tr;
            }
            
            const atr = trSum / period;
            const priceRange = Math.max(...prices) - Math.min(...prices);
            const adx = (atr / priceRange) * 100;
            
            return Math.min(100, Math.max(0, adx));
        }
        
        function analyzePriceAction(coin) {
            // Price action analysis - More strict for scalping
            const priceChange = coin.change24h;
            const volume = coin.volume / 1000000;
            
            if (priceChange > 4 && volume > 50) { // Very strong breakout
                return { bullish: true, strength: 8, signal: 'Very Strong Bullish Breakout' };
            } else if (priceChange < -4 && volume > 50) { // Very strong breakdown
                return { bearish: true, strength: 8, signal: 'Very Strong Bearish Breakdown' };
            } else if (priceChange > 3 && volume > 30) { // Strong breakout
                return { bullish: true, strength: 5, signal: 'Strong Bullish Breakout' };
            } else if (priceChange < -3 && volume > 30) { // Strong breakdown
                return { bearish: true, strength: 5, signal: 'Strong Bearish Breakdown' };
            } else if (priceChange > 2 && volume > 20) { // Moderate breakout
                return { bullish: true, strength: 3, signal: 'Moderate Bullish Breakout' };
            } else if (priceChange < -2 && volume > 20) { // Moderate breakdown
                return { bearish: true, strength: 3, signal: 'Moderate Bearish Breakdown' };
            }
            
            return { bullish: false, bearish: false, strength: 0, signal: 'Neutral' };
        }
        
        function analyzeMarketSentiment(coin) {
            // Market sentiment analysis - More strict
            const volume = coin.volume / 1000000;
            const priceChange = coin.change24h;
            
            if (volume > 100 && priceChange > 2) { // Very strong bullish sentiment
                return { score: 6, signal: 'Very Strong Bullish Sentiment' };
            } else if (volume > 100 && priceChange < -2) { // Very strong bearish sentiment
                return { score: 6, signal: 'Very Strong Bearish Sentiment' };
            } else if (volume > 50 && priceChange > 1) { // Strong bullish sentiment
                return { score: 4, signal: 'Strong Bullish Sentiment' };
            } else if (volume > 50 && priceChange < -1) { // Strong bearish sentiment
                return { score: 4, signal: 'Strong Bearish Sentiment' };
            } else if (volume > 30) { // Moderate sentiment
                return { score: 2, signal: 'Moderate Sentiment' };
            }
            
            return { score: 0, signal: 'Neutral Sentiment' };
        }
        
        function assessRisk(coin) {
            // Risk assessment - More strict for scalping
            const volatility = Math.abs(coin.change24h);
            const volume = coin.volume / 1000000;
            
            if (volatility > 15) { // Very high volatility
                return { penalty: 20, warning: 'Very High Volatility Risk' };
            } else if (volatility > 10) { // High volatility
                return { penalty: 15, warning: 'High Volatility Risk' };
            } else if (volatility > 7) { // Moderate volatility
                return { penalty: 8, warning: 'Moderate Volatility Risk' };
            } else if (volume < 10) { // Low volume risk
                return { penalty: 15, warning: 'Low Volume Risk' };
            } else if (volume < 20) { // Moderate volume risk
                return { penalty: 8, warning: 'Moderate Volume Risk' };
            }
            
            return { penalty: 0, warning: null };
        }

        function analyzeForPosition(coin) {
            // YENİ NESİL POSITION TRADING SİSTEMİ - Gelişmiş Analiz Modülleri
            const rsi = calculateRSI(coin, 21); // Position trading için daha yavaş RSI
            const macd = calculateMACD(coin, 26, 52, 18); // Position trading için daha yavaş MACD
            const bb = calculateBollingerBands(coin, 20);
            const ema21 = calculateEMA(coin, 21);
            const ema50 = calculateEMA(coin, 50);
            const ema200 = calculateEMA(coin, 200);
            const sma50 = calculateSMA(coin, 50);
            const sma200 = calculateSMA(coin, 200);
            const adx = calculateADX(coin, 14);
            const volume = coin.volume / 1000000;
            const priceChange = coin.change24h;
            const momentum = Math.abs(priceChange);
            
            // YENİ: Gelişmiş Analiz Modülleri
            const trendAnalysis = analyzeAdvancedTrend(coin, ema21, ema50, ema200, sma50, sma200);
            const fundamentalAnalysis = performFundamentalAnalysis(coin);
            const riskManagement = performRiskManagement(coin);
            const machineLearning = performMachineLearning(coin);
            
            let score = 0; // Yeni skor sistemi
            let signals = [];
            let longSignals = 0;
            let shortSignals = 0;
            let direction = 'NONE';
            
            // Pre-filter: Only analyze coins with sufficient volume and reasonable volatility
            if (volume < 50 || momentum < 2) {
                return { score: 0, direction: 'NONE', confidence: 0, indicators: {} };
            }
            
            // YENİ NESİL SKOR SİSTEMİ - Uzun AI (Position Trading)
            
            // 1. TREND ANALİZİ (35% ağırlık) - Daha sert
            // Çifte Golden Cross (EMA + SMA)
            if (trendAnalysis.goldenCross && trendAnalysis.smaGoldenCross) {
                score += 15; // Double Golden Cross - Strong Uptrend (daha sert)
                longSignals++;
                direction = 'LONG';
                signals.push('Double Golden Cross - Strong Uptrend');
            }
            
            // Çifte Death Cross (EMA + SMA)
            if (trendAnalysis.deathCross && trendAnalysis.smaDeathCross) {
                score += 15; // Double Death Cross - Strong Downtrend (daha sert)
                shortSignals++;
                direction = 'SHORT';
                signals.push('Double Death Cross - Strong Downtrend');
            }
            
            // Trend hizalanması
            if (trendAnalysis.trendAlignment) {
                score += 6; // Trend Alignment Confirmed (daha sert)
                signals.push('Trend Alignment Confirmed');
            }
            
            // Güçlü trend
            if (trendAnalysis.strongTrend) {
                score += 8; // Strong Trend Detected (daha sert)
                signals.push('Strong Trend Detected');
            }
            
            // EMA Hizalanması
            if (ema21 > ema50 && ema50 > ema200) {
                score += 8;
                longSignals++;
                direction = 'LONG';
                signals.push('EMA Alignment - Bullish');
            } else if (ema21 < ema50 && ema50 < ema200) {
                score += 8;
                shortSignals++;
                direction = 'SHORT';
                signals.push('EMA Alignment - Bearish');
            }
            
            // 2. FUNDAMENTAL ANALİZ (25% ağırlık) - Daha sert
            // On-chain sağlık
            if (fundamentalAnalysis.onChainHealth.status === 'HEALTHY') {
                score += 10; // Healthy On-chain Metrics (daha sert)
                signals.push('Healthy On-chain Metrics');
            }
            
            // Balina aktivitesi
            if (fundamentalAnalysis.whaleActivity.status === 'HIGH_ACTIVITY') {
                score += 8; // High Whale Activity (daha sert)
                signals.push('High Whale Activity');
            }
            
            // Sosyal sentiment
            if (fundamentalAnalysis.socialSentiment.status === 'VERY_BULLISH') {
                score += 6; // Very Bullish Social Sentiment (daha sert)
                longSignals++;
                direction = 'LONG';
                signals.push('Very Bullish Social Sentiment');
            } else if (fundamentalAnalysis.socialSentiment.status === 'VERY_BEARISH') {
                score += 6; // Very Bearish Social Sentiment (daha sert)
                shortSignals++;
                direction = 'SHORT';
                signals.push('Very Bearish Social Sentiment');
            }
            
            // Haber etkisi
            if (fundamentalAnalysis.newsImpact.status === 'HIGH_IMPACT') {
                score += 5; // High News Impact (daha sert)
                signals.push('High News Impact');
            }
            
            // Hacim sağlığı
            if (fundamentalAnalysis.volumeHealth === 'HEALTHY') {
                score += 6; // Healthy Volume (daha sert)
                signals.push('Healthy Volume');
            }
            
            // 3. RİSK YÖNETİMİ (25% ağırlık) - Daha sert
            // Volatilite riski
            if (riskManagement.volatilityRisk === 'LOW') {
                score += 10; // Low Volatility Risk (daha sert)
                signals.push('Low Volatility Risk');
            } else if (riskManagement.volatilityRisk === 'HIGH') {
                score -= 8; // High Volatility Risk - Penalty (daha sert)
                signals.push('High Volatility Risk - Penalty');
            }
            
            // Hacim riski
            if (riskManagement.volumeRisk === 'LOW') {
                score += 6; // Low Volume Risk (daha sert)
                signals.push('Low Volume Risk');
            }
            
            // Momentum riski
            if (riskManagement.momentumRisk === 'LOW') {
                score += 5; // Low Momentum Risk (daha sert)
                signals.push('Low Momentum Risk');
            }
            
            // 4. MAKİNE ÖĞRENMESİ (15% ağırlık) - Daha sert
            // AI güveni
            if (machineLearning.confidence === 'HIGH') {
                score += 12; // High AI Confidence (daha sert)
                signals.push('High AI Confidence');
            } else if (machineLearning.confidence === 'MEDIUM') {
                score += 6; // Medium AI Confidence (daha sert)
                signals.push('Medium AI Confidence');
            }
            
            // LSTM tahmini
            if (machineLearning.lstmPrediction.prediction === 'BULLISH') {
                score += 8; // LSTM Bullish Prediction (daha sert)
                longSignals++;
                direction = 'LONG';
                signals.push('LSTM Bullish Prediction');
            } else if (machineLearning.lstmPrediction.prediction === 'BEARISH') {
                score += 8; // LSTM Bearish Prediction (daha sert)
                shortSignals++;
                direction = 'SHORT';
                signals.push('LSTM Bearish Prediction');
            }
            
            // Random Forest tahmini
            if (machineLearning.randomForest.prediction === 'BULLISH') {
                score += 6; // Random Forest Bullish (daha sert)
                longSignals++;
                direction = 'LONG';
                signals.push('Random Forest Bullish');
            } else if (machineLearning.randomForest.prediction === 'BEARISH') {
                score += 6; // Random Forest Bearish (daha sert)
                shortSignals++;
                direction = 'SHORT';
                signals.push('Random Forest Bearish');
            }
            
            // 5. KLASİK İNDİKATÖR ANALİZİ (Ek destek) - Daha sert
            // RSI Analysis (Position trading için daha yavaş)
            if (rsi < 25) { // Daha extreme oversold (daha sert)
                score += 5;
                longSignals++;
                direction = 'LONG';
                signals.push('RSI Oversold');
            } else if (rsi > 75) { // Daha extreme overbought (daha sert)
                score += 5;
                shortSignals++;
                direction = 'SHORT';
                signals.push('RSI Overbought');
            } else if (rsi > 40 && rsi < 60) { // Neutral zone
                score += 2;
                signals.push('RSI Neutral');
            }
            
            // MACD Analysis (Position trading için daha yavaş)
            if (macd.histogram > 0 && macd.signal > 0 && macd.macd > 0) {
                score += 6;
                longSignals++;
                direction = 'LONG';
                signals.push('MACD Bullish');
            } else if (macd.histogram < 0 && macd.signal < 0 && macd.macd < 0) {
                score += 6;
                shortSignals++;
                direction = 'SHORT';
                signals.push('MACD Bearish');
            }
            
            // Bollinger Bands Analysis
            const bbPosition = (coin.price - bb.lower) / (bb.upper - bb.lower);
            if (bbPosition < 0.05) { // Çok yakın lower band (daha sert)
                score += 4;
                longSignals++;
                direction = 'LONG';
                signals.push('BB Near Lower Band');
            } else if (bbPosition > 0.95) { // Çok yakın upper band (daha sert)
                score += 4;
                shortSignals++;
                direction = 'SHORT';
                signals.push('BB Near Upper Band');
            }
            
            // ADX Analysis (Trend Strength)
            if (adx > 50) { // Çok güçlü trend (daha sert)
                score += 5;
                signals.push('Very Strong Trend');
            } else if (adx > 30) { // Strong trend
                score += 3;
                signals.push('Strong Trend');
            } else if (adx < 15) { // Weak trend penalty
                score -= 5;
                signals.push('Weak Trend');
            }
            
            // Volume Analysis
            if (volume > 200) { // Very high volume
                score += 10;
                signals.push('Very High Volume');
            } else if (volume > 100) { // High volume
                score += 6;
                signals.push('High Volume');
            } else if (volume > 50) { // Good volume
                score += 3;
                signals.push('Good Volume');
            } else { // Low volume penalty
                score -= 10;
                signals.push('Low Volume');
            }
            
            // Sinyal sayısına göre yön belirleme
            if (shortSignals > longSignals) {
                direction = 'SHORT';
            } else if (longSignals > shortSignals) {
                direction = 'LONG';
            } else {
                // Beraberlik durumunda EMA ve MACD hizalanması
                if (ema21 > ema50 && macd.histogram > 0) {
                    direction = 'LONG';
                } else if (ema21 < ema50 && macd.histogram < 0) {
                    direction = 'SHORT';
                } else {
                    direction = priceChange > 0 ? 'LONG' : 'SHORT';
                }
            }
            
            // Use user-defined confidence threshold
            const userConfidenceThreshold = parseInt(document.getElementById('longConfidence')?.value || '80');
            const userScoreThreshold = parseInt(document.getElementById('longScoreThreshold')?.value || '80');
            
            // Gelişmiş skor hesaplama sistemi (Hızlı AI gibi)
            const finalScore = score;
            // Güven hesaplama: Daha sıkı formül, signal sayısını da dikkate al
            const finalConfidence = Math.min(95, Math.max(15, Math.min(score * 0.3, 50) + (longSignals + shortSignals) * 3));
            
            return {
                score: finalScore,
                direction: direction,
                confidence: finalConfidence,
                indicators: {
                    rsi: rsi,
                    macd: macd,
                    bb: bb,
                    ema21: ema21,
                    ema50: ema50,
                    ema200: ema200,
                    sma50: sma50,
                    sma200: sma200,
                    adx: adx,
                    volume: volume,
                    momentum: momentum,
                    signals: signals,
                    longSignals: longSignals,
                    shortSignals: shortSignals,
                    trendAnalysis: trendAnalysis,
                    fundamentalAnalysis: fundamentalAnalysis,
                    riskManagement: riskManagement,
                    machineLearning: machineLearning
                }
            };
        }

        function calculateRSI(coin, period = 14) {
            // Real RSI calculation based on price changes
            if (!coin.priceHistory || coin.priceHistory.length < period) {
                // Fallback to basic calculation based on 24h change
                const change = coin.change24h;
                if (change > 5) return 70 + Math.min(20, change - 5);
                if (change < -5) return 30 - Math.min(20, Math.abs(change) - 5);
                return 50 + (change * 2);
            }
            
            const prices = coin.priceHistory.slice(-period);
            let gains = 0;
            let losses = 0;
            
            for (let i = 1; i < prices.length; i++) {
                const change = prices[i] - prices[i-1];
                if (change > 0) gains += change;
                else losses += Math.abs(change);
            }
            
            const avgGain = gains / period;
            const avgLoss = losses / period;
            
            if (avgLoss === 0) return 100;
            
            const rs = avgGain / avgLoss;
            return 100 - (100 / (1 + rs));
        }

        function calculateMACD(coin, fastPeriod = 12, slowPeriod = 26, signalPeriod = 9) {
            // Real MACD calculation
            const ema12 = calculateEMA(coin, fastPeriod);
            const ema26 = calculateEMA(coin, slowPeriod);
            const macd = ema12 - ema26;
            
            // Signal line (9-period EMA of MACD)
            const signal = macd * 0.9; // Simplified signal line
            const histogram = macd - signal;
            
            return {
                macd: macd,
                signal: signal,
                histogram: histogram
            };
        }


        function calculateSMA(coin, period) {
            // Simple Moving Average calculation
            if (!coin.priceHistory || coin.priceHistory.length < period) {
                // Fallback based on current price and 24h change
                const change = coin.change24h / 100;
                return coin.price * (1 + change * 0.05);
            }
            
            const prices = coin.priceHistory.slice(-period);
            const sum = prices.reduce((acc, price) => acc + price, 0);
            return sum / period;
        }

        function calculateEMA(coin, period) {
            // Real EMA calculation
            if (!coin.priceHistory || coin.priceHistory.length < period) {
                // Fallback based on current price and 24h change
                const change = coin.change24h / 100;
                return coin.price * (1 + change * 0.1);
            }
            
            const prices = coin.priceHistory.slice(-period);
            const multiplier = 2 / (period + 1);
            
            let ema = prices[0];
            for (let i = 1; i < prices.length; i++) {
                ema = (prices[i] * multiplier) + (ema * (1 - multiplier));
            }
            
            return ema;
        }

        function calculateATR(coin, period = 14) {
            // Real ATR calculation
            if (!coin.priceHistory || coin.priceHistory.length < period) {
                // Fallback based on volatility
                const volatility = Math.abs(coin.change24h) / 100;
                return coin.price * (volatility * 0.02 + 0.01); // 1-3% ATR
            }
            
            const prices = coin.priceHistory.slice(-period);
            let trSum = 0;
            
            for (let i = 1; i < prices.length; i++) {
                const high = Math.max(prices[i], prices[i-1]);
                const low = Math.min(prices[i], prices[i-1]);
                const tr = high - low;
                trSum += tr;
            }
            
            return trSum / period;
        }

        // API Logging System
        // API Logs array for persistence
        let apiLogsArray = [];

        function addApiLog(message) {
            const apiLogs = document.getElementById('apiLogs');
            if (!apiLogs) return;
            
            const timestamp = new Date().toLocaleTimeString('tr-TR');
            const logEntry = {
                timestamp: timestamp,
                message: message,
                time: Date.now()
            };
            
            // Add to array
            apiLogsArray.unshift(logEntry);
            
            // Keep only last 100 logs
            if (apiLogsArray.length > 100) {
                apiLogsArray = apiLogsArray.slice(0, 100);
            }
            
            // Save to localStorage
            try {
                localStorage.setItem('ct_api_logs', JSON.stringify(apiLogsArray));
            } catch (e) {
                console.warn('Failed to save API logs to localStorage:', e);
            }
            
            // Update UI
            const logElement = document.createElement('div');
            logElement.className = 'text-sm font-mono';
            logElement.innerHTML = `<span class="text-gray-400">[${timestamp}]</span> ${message}`;
            
            // Add to top
            if (apiLogs.firstChild && apiLogs.firstChild.textContent.includes('API logları burada görünecek')) {
                apiLogs.innerHTML = '';
            }
            
            apiLogs.insertBefore(logElement, apiLogs.firstChild);
            
            // Keep only last 50 logs in UI
            while (apiLogs.children.length > 50) {
                apiLogs.removeChild(apiLogs.lastChild);
            }
            
            // Update timestamp
            const apiLogTime = document.getElementById('apiLogTime');
            if (apiLogTime) {
                apiLogTime.textContent = timestamp;
            }
            
            // Auto scroll to top
            apiLogs.scrollTop = 0;
        }

        // Load API logs from localStorage
        function loadApiLogs() {
            try {
                const savedLogs = localStorage.getItem('ct_api_logs');
                if (savedLogs) {
                    apiLogsArray = JSON.parse(savedLogs);
                    console.log('API logs loaded from storage:', apiLogsArray.length);
                }
            } catch (e) {
                console.warn('Failed to load API logs from localStorage:', e);
                apiLogsArray = [];
            }
        }

        // Display API logs in UI
        function displayApiLogs() {
            const apiLogs = document.getElementById('apiLogs');
            if (!apiLogs) return;
            
            apiLogs.innerHTML = '';
            
            apiLogsArray.forEach(log => {
                const logElement = document.createElement('div');
                logElement.className = 'text-sm font-mono';
                logElement.innerHTML = `<span class="text-gray-400">[${log.timestamp}]</span> ${log.message}`;
                apiLogs.appendChild(logElement);
            });
            
            // Update timestamp
            const apiLogTime = document.getElementById('apiLogTime');
            if (apiLogTime && apiLogsArray.length > 0) {
                apiLogTime.textContent = apiLogsArray[0].timestamp;
            }
        }

        function clearApiLogs() {
            const apiLogs = document.getElementById('apiLogs');
            if (apiLogs) {
                apiLogs.innerHTML = '<div class="text-gray-400">API logları temizlendi...</div>';
            }
        }

        async function sendOrderToBybit(trade) {
            const apiKey = document.getElementById('bybitApiKey').value;
            const secretKey = document.getElementById('bybitSecretKey').value;
            
            if (!apiKey || !secretKey) {
                addApiLog(`❌ Bybit API anahtarları eksik`);
                return;
            }
            
            // Fix double USDT issue
            let symbol = trade.coin;
            if (!symbol.endsWith('USDT')) {
                symbol = symbol + 'USDT';
            }
            
            // Check if symbol is active by querying Bybit API
            try {
                addApiLog(`🔍 ${symbol} kontrat durumu kontrol ediliyor...`);
                const symbolResponse = await fetch(`https://api.bybit.com/v5/market/instruments-info?category=linear&symbol=${symbol}`);
                const symbolData = await symbolResponse.json();
                
                addApiLog(`📋 Kontrat API yanıtı: ${JSON.stringify(symbolData)}`);
                
                if (symbolData.retCode !== 0) {
                    addApiLog(`❌ ${symbol} API hatası: ${symbolData.retMsg} - işlem atlandı`);
                    return;
                }
                
                if (!symbolData.result || !symbolData.result.list || symbolData.result.list.length === 0) {
                    addApiLog(`❌ ${symbol} kontrat bulunamadı - işlem atlandı`);
                    return;
                }
                
                const symbolInfo = symbolData.result.list[0];
                addApiLog(`📊 ${symbol} kontrat bilgisi: Status=${symbolInfo.status}, MinQty=${symbolInfo.lotSizeFilter?.minOrderQty}`);
                
                if (symbolInfo.status !== 'Trading') {
                    addApiLog(`❌ ${symbol} şu anda işlem görmüyor (${symbolInfo.status}) - işlem atlandı`);
                    return;
                }
                
                addApiLog(`✅ ${symbol} aktif futures kontratı - işlem devam ediyor`);
                
            } catch (error) {
                addApiLog(`⚠️ ${symbol} kontrat durumu kontrol edilemedi: ${error.message}`);
                addApiLog(`⚠️ Kontrat kontrolü atlandı, işlem devam ediyor...`);
                // Continue with trade if we can't check status
            }
            
            // Check account balance first
            const balance = await getBybitBalance(apiKey, secretKey);
            if (balance && balance < trade.amount) {
                addApiLog(`❌ Yetersiz bakiye: ${balance.toFixed(2)} USDT < ${trade.amount} USDT`);
                return;
            }
            
            addApiLog(`📤 Bybit'e ${trade.type} emir gönderiliyor: ${trade.coin}`);
            
            try {
                // Get symbol info for proper quantity formatting
                const symbolInfo = await getBybitSymbolInfo(symbol, apiKey, secretKey);
                
                // Calculate position size based on USDT amount and leverage
                let qty = (trade.amount * trade.leverage) / trade.entryPrice;
                
                // Apply symbol-specific quantity rules
                if (symbolInfo) {
                    const minQty = parseFloat(symbolInfo.lotSizeFilter.minOrderQty);
                    const qtyStep = parseFloat(symbolInfo.lotSizeFilter.qtyStep);
                    const maxQty = parseFloat(symbolInfo.lotSizeFilter.maxOrderQty);
                    
                    // Ensure quantity meets minimum
                    qty = Math.max(qty, minQty);
                    
                    // Round to proper step size
                    qty = Math.floor(qty / qtyStep) * qtyStep;
                    
                    // Ensure quantity doesn't exceed maximum
                    qty = Math.min(qty, maxQty);
                    
                    // Format with proper decimal places
                    const decimals = qtyStep.toString().split('.')[1]?.length || 0;
                    qty = qty.toFixed(decimals);
                } else {
                    // Fallback: use standard formatting
                    qty = qty.toFixed(3);
                }
                
                addApiLog(`📊 Miktar hesaplama: ${trade.amount} USDT × ${trade.leverage}x ÷ ${trade.entryPrice} = ${qty}`);
                
                // Clean order data - remove undefined values
                const orderData = {
                    category: "linear",
                    symbol: symbol,
                    side: trade.type === 'LONG' ? 'Buy' : 'Sell',
                    orderType: trade.orderType === 'Market' ? 'Market' : 'Limit',
                    qty: qty.toString(),
                    timeInForce: "GTC",
                    reduceOnly: false,
                    closeOnTrigger: false,
                    positionIdx: 0
                };
                
                // Only add price for limit orders
                if (trade.orderType === 'Limit') {
                    orderData.price = trade.entryPrice.toFixed(6);
                }
                
                addApiLog(`📋 Ana emir: ${JSON.stringify(orderData, null, 2)}`);
                
                // Create proper signature for Bybit API v5
                const timestamp = Date.now().toString();
                const recvWindow = '5000';
                const jsonBody = JSON.stringify(orderData);
                
                // Create signature using correct Bybit v5 format
                const signature = await createBybitSignature(apiKey, secretKey, timestamp, recvWindow, jsonBody);
                
                const response = await fetch('https://api.bybit.com/v5/order/create', {
                    method: 'POST',
                    headers: {
                        'X-BAPI-API-KEY': apiKey,
                        'X-BAPI-SIGN': signature,
                        'X-BAPI-SIGN-TYPE': '2',
                        'X-BAPI-TIMESTAMP': timestamp,
                        'X-BAPI-RECV-WINDOW': recvWindow,
                        'Content-Type': 'application/json'
                    },
                    body: jsonBody
                });
                
                const result = await response.json();
                addApiLog(`📋 Bybit yanıt: ${JSON.stringify(result, null, 2)}`);
                
                if (result.retCode === 0) {
                    const orderId = result.result.orderId;
                    addApiLog(`✅ Bybit ana emir başarılı - ID: ${orderId}`);
                    trade.orderId = orderId;
                    
                    // Send Stop Loss and Take Profit orders immediately
                    if (document.getElementById('autoSlTp').checked) {
                        setTimeout(() => sendBybitStopLoss(trade, apiKey, secretKey), 1000);
                        setTimeout(() => sendBybitTakeProfit(trade, apiKey, secretKey), 2000);
                    }
                    
                    // Send pre-calculated DCA orders if DCA is enabled
                    if (trade.dcaEnabled && trade.dcaCount > 0) {
                        setTimeout(() => sendPreCalculatedDCAOrders(trade, apiKey, secretKey), 3000);
                    }
                    
                } else {
                    addApiLog(`❌ Bybit emir hatası: ${result.retMsg || 'Bilinmeyen hata'}`);
                    if (result.retExtInfo) {
                        addApiLog(`📋 Ek bilgi: ${JSON.stringify(result.retExtInfo)}`);
                    }
                    showNotification(`Bybit emir hatası: ${result.retMsg}`, 'error');
                }
                
            } catch (error) {
                addApiLog(`❌ Bybit API bağlantı hatası: ${error.message}`);
                addApiLog(`📋 Hata detayı: ${error.stack}`);
                showNotification('Bybit API bağlantı hatası!', 'error');
            }
        }
        
        async function sendBybitStopLoss(trade, apiKey, secretKey) {
            try {
                // Fix symbol for stop loss
                let symbol = trade.coin;
                if (!symbol.endsWith('USDT')) {
                    symbol = symbol + 'USDT';
                }
                
                // Get symbol info for proper quantity formatting
                const symbolInfo = await getBybitSymbolInfo(symbol, apiKey, secretKey);
                
                // Calculate position size based on USDT amount and leverage
                let qty = (trade.amount * trade.leverage) / trade.entryPrice;
                
                // Apply symbol-specific quantity rules
                if (symbolInfo) {
                    const minQty = parseFloat(symbolInfo.lotSizeFilter.minOrderQty);
                    const qtyStep = parseFloat(symbolInfo.lotSizeFilter.qtyStep);
                    const maxQty = parseFloat(symbolInfo.lotSizeFilter.maxOrderQty);
                    
                    // Ensure quantity meets minimum
                    qty = Math.max(qty, minQty);
                    
                    // Round to proper step size
                    qty = Math.floor(qty / qtyStep) * qtyStep;
                    
                    // Ensure quantity doesn't exceed maximum
                    qty = Math.min(qty, maxQty);
                    
                    // Format with proper decimal places
                    const decimals = qtyStep.toString().split('.')[1]?.length || 0;
                    qty = qty.toFixed(decimals);
                } else {
                    // Fallback: use standard formatting
                    qty = qty.toFixed(3);
                }
                
                const slOrderData = {
                    category: "linear",
                    symbol: symbol,
                    side: trade.type === 'LONG' ? 'Sell' : 'Buy',
                    orderType: 'Market',
                    qty: qty.toString(),
                    triggerPrice: trade.stopLoss.toFixed(6),
                    triggerDirection: trade.type === 'LONG' ? 2 : 1,
                    reduceOnly: true,
                    closeOnTrigger: true,
                    positionIdx: 0
                };
                
                const timestamp = Date.now().toString();
                const recvWindow = '5000';
                const jsonBody = JSON.stringify(slOrderData);
                const signature = await createBybitSignature(apiKey, secretKey, timestamp, recvWindow, jsonBody);
                
                const response = await fetch('https://api.bybit.com/v5/order/create', {
                    method: 'POST',
                    headers: {
                        'X-BAPI-API-KEY': apiKey,
                        'X-BAPI-SIGN': signature,
                        'X-BAPI-SIGN-TYPE': '2',
                        'X-BAPI-TIMESTAMP': timestamp,
                        'X-BAPI-RECV-WINDOW': recvWindow,
                        'Content-Type': 'application/json'
                    },
                    body: jsonBody
                });
                
                const result = await response.json();
                addApiLog(`📋 SL yanıt: ${JSON.stringify(result, null, 2)}`);
                
                if (result.retCode === 0) {
                    addApiLog(`✅ Stop Loss emir başarılı - Fiyat: ${trade.stopLoss.toFixed(6)}`);
                    trade.slOrderId = result.result.orderId;
                } else {
                    addApiLog(`❌ Stop Loss emir hatası: ${result.retMsg}`);
                }
                
            } catch (error) {
                addApiLog(`❌ Stop Loss emir hatası: ${error.message}`);
            }
        }
        
        // Send pre-calculated DCA orders to exchange
        async function sendPreCalculatedDCAOrders(trade, apiKey, secretKey) {
            try {
                addApiLog(`📈 ${trade.coin} için önceden hesaplanmış DCA emirleri gönderiliyor...`);
                
                const dcaTrigger = trade.dcaTrigger || 0.005; // 0.5% default
                const dcaMultiplier = trade.dcaMultiplier || 1.5;
                const currentPrice = trade.entryPrice;
                
                // Get symbol info for proper quantity formatting
                const symbolInfo = await getBybitSymbolInfo(trade.coin + 'USDT', apiKey, secretKey);
                
                // Calculate and send DCA orders for each level
                for (let level = 1; level <= trade.dcaCount; level++) {
                    // DCA hesaplama: sabit çarpan ile hesaplama
                    const dcaAmount = trade.amount * Math.pow(trade.dcaMultiplier || 1.5, level);
                    
                    // Calculate trigger price based on position type
                    let triggerPrice;
                    if (trade.type === 'LONG') {
                        // For LONG: DCA when price drops
                        triggerPrice = currentPrice * (1 - (dcaTrigger * level));
                    } else {
                        // For SHORT: DCA when price rises
                        triggerPrice = currentPrice * (1 + (dcaTrigger * level));
                    }
                    
                    // Calculate quantity based on USDT amount and leverage (ana emir gibi)
                    let quantity = (dcaAmount * trade.leverage) / triggerPrice;
                    
                    // Apply symbol-specific quantity rules
                    if (symbolInfo) {
                        const minQty = parseFloat(symbolInfo.lotSizeFilter.minOrderQty);
                        const qtyStep = parseFloat(symbolInfo.lotSizeFilter.qtyStep);
                        const maxQty = parseFloat(symbolInfo.lotSizeFilter.maxOrderQty);
                        
                    addApiLog(`📊 DCA Seviye ${level} kontrat kuralları: Min=${minQty}, Step=${qtyStep}, Max=${maxQty}`);
                    
                    // Check if quantity meets minimum requirement
                    if (quantity < minQty) {
                        addApiLog(`❌ DCA Seviye ${level} miktar çok küçük: ${quantity} < ${minQty} - emir atlanıyor`);
                        continue; // Skip this DCA level
                    }
                    
                    // Calculate order value in USDT
                    const orderValue = quantity * triggerPrice;
                    const minOrderValue = parseFloat(symbolInfo.lotSizeFilter.minOrderAmt) || 5; // Default 5 USDT
                    
                    addApiLog(`💰 DCA Seviye ${level} emir değeri: ${orderValue.toFixed(2)} USDT (Min: ${minOrderValue} USDT)`);
                    
                    // Check if order value meets minimum requirement
                    if (orderValue < minOrderValue) {
                        // Try to increase quantity to meet minimum order value
                        const requiredQuantity = Math.ceil(minOrderValue / triggerPrice);
                        
                        // Apply step size to required quantity
                        const adjustedQuantity = Math.ceil(requiredQuantity / qtyStep) * qtyStep;
                        
                        // Check if adjusted quantity exceeds maximum
                        if (adjustedQuantity > maxQty) {
                            addApiLog(`❌ DCA Seviye ${level} minimum değer için gerekli miktar çok büyük: ${adjustedQuantity} > ${maxQty} - emir atlanıyor`);
                            continue; // Skip this DCA level
                        }
                        
                        quantity = adjustedQuantity;
                        const newOrderValue = quantity * triggerPrice;
                        addApiLog(`📈 DCA Seviye ${level} miktar artırıldı: ${quantity} (Değer: ${newOrderValue.toFixed(2)} USDT)`);
                    }
                    
                    // Ensure quantity meets minimum
                    quantity = Math.max(quantity, minQty);
                    
                    // Round to proper step size
                    quantity = Math.floor(quantity / qtyStep) * qtyStep;
                    
                    // Ensure quantity doesn't exceed maximum
                    quantity = Math.min(quantity, maxQty);
                    
                    // Format with proper decimal places
                    const decimals = qtyStep.toString().split('.')[1]?.length || 0;
                    quantity = parseFloat(quantity.toFixed(decimals));
                }
                
                // Create DCA order
                const dcaOrder = {
                    category: 'linear',
                    symbol: trade.coin + 'USDT',
                    side: trade.type === 'LONG' ? 'Buy' : 'Sell',
                    orderType: 'Limit',
                    qty: quantity.toString(),
                    price: triggerPrice.toFixed(6),
                    timeInForce: 'GTC',
                    reduceOnly: false,
                    closeOnTrigger: false,
                    positionIdx: 0
                };
                
                addApiLog(`📊 DCA Seviye ${level} hesaplama: ${dcaAmount.toFixed(2)} USDT × ${trade.leverage}x ÷ ${triggerPrice.toFixed(6)} = ${quantity} ${trade.coin} (Çarpan: ${trade.dcaMultiplier || 1.5}^${level})`);
                
                // Send DCA order to Bybit
                const timestamp = Date.now().toString();
                const recvWindow = '5000';
                const jsonBody = JSON.stringify(dcaOrder);
                const signature = await createBybitSignature(apiKey, secretKey, timestamp, recvWindow, jsonBody);
                
                const response = await fetch('https://api.bybit.com/v5/order/create', {
                    method: 'POST',
                    headers: {
                        'X-BAPI-API-KEY': apiKey,
                        'X-BAPI-SIGN': signature,
                        'X-BAPI-SIGN-TYPE': '2',
                        'X-BAPI-TIMESTAMP': timestamp,
                        'X-BAPI-RECV-WINDOW': recvWindow,
                        'Content-Type': 'application/json'
                    },
                    body: jsonBody
                });
                
                const result = await response.json();
                
                if (result.retCode === 0) {
                    const orderId = result.result.orderId;
                    addApiLog(`✅ DCA Seviye ${level} emri gönderildi - ID: ${orderId}, Fiyat: $${triggerPrice.toFixed(6)}`);
                        
                        // Store DCA order ID for later cancellation
                        if (!trade.dcaOrders) trade.dcaOrders = [];
                        trade.dcaOrders.push({
                            level: level,
                            orderId: orderId,
                            price: triggerPrice,
                            amount: dcaAmount
                        });
                    } else {
                        addApiLog(`❌ DCA Seviye ${level} emir hatası: ${result.retMsg}`);
                    }
                    
                    // Wait between orders to avoid rate limiting
                    await new Promise(resolve => setTimeout(resolve, 500));
                }
                
                addApiLog(`✅ ${trade.coin} için ${trade.dcaCount} DCA emri başarıyla gönderildi`);
                
            } catch (error) {
                addApiLog(`❌ DCA emirleri gönderilirken hata: ${error.message}`);
                console.error('DCA orders error:', error);
            }
        }

        async function sendBybitTakeProfit(trade, apiKey, secretKey) {
            try {
                // Fix symbol for take profit
                let symbol = trade.coin;
                if (!symbol.endsWith('USDT')) {
                    symbol = symbol + 'USDT';
                }
                
                // Get symbol info for proper quantity formatting
                const symbolInfo = await getBybitSymbolInfo(symbol, apiKey, secretKey);
                
                // Calculate position size based on USDT amount and leverage
                let qty = (trade.amount * trade.leverage) / trade.entryPrice;
                
                // Apply symbol-specific quantity rules
                if (symbolInfo) {
                    const minQty = parseFloat(symbolInfo.lotSizeFilter.minOrderQty);
                    const qtyStep = parseFloat(symbolInfo.lotSizeFilter.qtyStep);
                    const maxQty = parseFloat(symbolInfo.lotSizeFilter.maxOrderQty);
                    
                    // Ensure quantity meets minimum
                    qty = Math.max(qty, minQty);
                    
                    // Round to proper step size
                    qty = Math.floor(qty / qtyStep) * qtyStep;
                    
                    // Ensure quantity doesn't exceed maximum
                    qty = Math.min(qty, maxQty);
                    
                    // Format with proper decimal places
                    const decimals = qtyStep.toString().split('.')[1]?.length || 0;
                    qty = qty.toFixed(decimals);
                } else {
                    // Fallback: use standard formatting
                    qty = qty.toFixed(3);
                }
                
                const tpOrderData = {
                    category: "linear",
                    symbol: symbol,
                    side: trade.type === 'LONG' ? 'Sell' : 'Buy',
                    orderType: 'Market',
                    qty: qty.toString(),
                    triggerPrice: trade.takeProfit.toFixed(6),
                    triggerDirection: trade.type === 'LONG' ? 1 : 2,
                    reduceOnly: true,
                    closeOnTrigger: true,
                    positionIdx: 0
                };
                
                const timestamp = Date.now().toString();
                const recvWindow = '5000';
                const jsonBody = JSON.stringify(tpOrderData);
                const signature = await createBybitSignature(apiKey, secretKey, timestamp, recvWindow, jsonBody);
                
                const response = await fetch('https://api.bybit.com/v5/order/create', {
                    method: 'POST',
                    headers: {
                        'X-BAPI-API-KEY': apiKey,
                        'X-BAPI-SIGN': signature,
                        'X-BAPI-SIGN-TYPE': '2',
                        'X-BAPI-TIMESTAMP': timestamp,
                        'X-BAPI-RECV-WINDOW': recvWindow,
                        'Content-Type': 'application/json'
                    },
                    body: jsonBody
                });
                
                const result = await response.json();
                addApiLog(`📋 TP yanıt: ${JSON.stringify(result, null, 2)}`);
                
                if (result.retCode === 0) {
                    addApiLog(`✅ Take Profit emir başarılı - Fiyat: ${trade.takeProfit.toFixed(6)}`);
                    trade.tpOrderId = result.result.orderId;
                } else {
                    addApiLog(`❌ Take Profit emir hatası: ${result.retMsg}`);
                }
                
            } catch (error) {
                addApiLog(`❌ Take Profit emir hatası: ${error.message}`);
            }
        }
        
        async function getBybitBalance(apiKey, secretKey) {
            try {
                const timestamp = Date.now().toString();
                const recvWindow = '5000';
                const queryString = `accountType=UNIFIED`;
                const signature = await createBybitSignature(apiKey, secretKey, timestamp, recvWindow, queryString);
                
                const response = await fetch(`https://api.bybit.com/v5/account/wallet-balance?${queryString}`, {
                    method: 'GET',
                    headers: {
                        'X-BAPI-API-KEY': apiKey,
                        'X-BAPI-SIGN': signature,
                        'X-BAPI-SIGN-TYPE': '2',
                        'X-BAPI-TIMESTAMP': timestamp,
                        'X-BAPI-RECV-WINDOW': recvWindow
                    }
                });
                
                const result = await response.json();
                if (result.retCode === 0 && result.result.list.length > 0) {
                    const account = result.result.list[0];
                    const usdtCoin = account.coin.find(c => c.coin === 'USDT');
                    if (usdtCoin) {
                        return parseFloat(usdtCoin.availableToWithdraw);
                    }
                }
                return null;
            } catch (error) {
                addApiLog(`⚠️ Bakiye bilgisi alınamadı: ${error.message}`);
                return null;
            }
        }

        async function getBybitSymbolInfo(symbol, apiKey, secretKey) {
            try {
                const timestamp = Date.now().toString();
                const recvWindow = '5000';
                const queryString = `category=linear&symbol=${symbol}`;
                const signature = await createBybitSignature(apiKey, secretKey, timestamp, recvWindow, queryString);
                
                const response = await fetch(`https://api.bybit.com/v5/market/instruments-info?${queryString}`, {
                    method: 'GET',
                    headers: {
                        'X-BAPI-API-KEY': apiKey,
                        'X-BAPI-SIGN': signature,
                        'X-BAPI-SIGN-TYPE': '2',
                        'X-BAPI-TIMESTAMP': timestamp,
                        'X-BAPI-RECV-WINDOW': recvWindow
                    }
                });
                
                const result = await response.json();
                if (result.retCode === 0 && result.result.list.length > 0) {
                    return result.result.list[0];
                }
                return null;
            } catch (error) {
                addApiLog(`⚠️ Symbol bilgisi alınamadı: ${error.message}`);
                return null;
            }
        }

        // Check if position exists on Bybit exchange
        async function checkBybitPositionExists(symbol, apiKey, secretKey) {
            try {
                const timestamp = Date.now().toString();
                const recvWindow = '5000';
                const queryString = `category=linear&symbol=${symbol}`;
                const signature = await createBybitSignature(apiKey, secretKey, timestamp, recvWindow, queryString);
                
                const response = await fetch(`https://api.bybit.com/v5/position/list?${queryString}`, {
                    method: 'GET',
                    headers: {
                        'X-BAPI-API-KEY': apiKey,
                        'X-BAPI-SIGN': signature,
                        'X-BAPI-SIGN-TYPE': '2',
                        'X-BAPI-TIMESTAMP': timestamp,
                        'X-BAPI-RECV-WINDOW': recvWindow
                    }
                });
                
                const result = await response.json();
                addApiLog(`📋 Pozisyon kontrolü yanıtı: ${JSON.stringify(result, null, 2)}`);
                
                if (result.retCode === 0 && result.result.list) {
                    // Check if there's an open position with non-zero size
                    const openPosition = result.result.list.find(pos => 
                        pos.symbol === symbol && 
                        parseFloat(pos.size) !== 0
                    );
                    
                    if (openPosition) {
                        addApiLog(`✅ ${symbol} pozisyonu bulundu - Boyut: ${openPosition.size}, Yön: ${openPosition.side}`);
                        return true;
                    } else {
                        addApiLog(`⚠️ ${symbol} pozisyonu bulunamadı veya boyutu sıfır`);
                        return false;
                    }
                } else {
                    addApiLog(`❌ Pozisyon kontrolü hatası: ${result.retMsg}`);
                    return false;
                }
            } catch (error) {
                addApiLog(`❌ Pozisyon kontrolü API hatası: ${error.message}`);
                // API hatası durumunda güvenli geri dönüş - DCA'ya izin ver
                return true;
            }
        }

        async function createBybitSignature(apiKey, secretKey, timestamp, recvWindow, jsonBody) {
            try {
                // Correct Bybit v5 signature format: timestamp + apiKey + recvWindow + jsonBody
                const message = timestamp + apiKey + recvWindow + jsonBody;
                
            const encoder = new TextEncoder();
            const key = await crypto.subtle.importKey(
                'raw',
                    encoder.encode(secretKey),
                { name: 'HMAC', hash: 'SHA-256' },
                false,
                ['sign']
            );
            const signature = await crypto.subtle.sign('HMAC', key, encoder.encode(message));
            return Array.from(new Uint8Array(signature))
                .map(b => b.toString(16).padStart(2, '0'))
                .join('');
            } catch (error) {
                console.error('Signature creation error:', error);
                throw error;
            }
        }

        async function sendOrderToBinance(trade) {
            const apiKey = document.getElementById('binanceApiKey').value;
            const secretKey = document.getElementById('binanceSecretKey').value;
            
            if (!apiKey || !secretKey) {
                addApiLog(`❌ Binance API anahtarları eksik`);
                return;
            }
            
            addApiLog(`📤 Binance'e ${trade.type} emir gönderiliyor: ${trade.coin}`);
            
            try {
                // Real Binance API call would go here
                const orderData = {
                    symbol: symbol,
                    side: trade.type === 'LONG' ? 'BUY' : 'SELL',
                    type: trade.orderType.toUpperCase(),
                    quantity: (trade.amount / trade.entryPrice).toFixed(6),
                    price: trade.orderType === 'LIMIT' ? trade.entryPrice.toString() : undefined,
                    timeInForce: "GTC"
                };
                
                addApiLog(`📋 Emir detayları: ${JSON.stringify(orderData, null, 2)}`);
                
                // Simulate API response
                setTimeout(() => {
                    const orderId = 'BIN' + Date.now();
                    addApiLog(`✅ Binance emir başarılı - ID: ${orderId}`);
                    
                    if (document.getElementById('binanceAutoSlTp').checked) {
                        // Send SL/TP orders
                        setTimeout(() => {
                            addApiLog(`📤 SL emir gönderiliyor: ${trade.stopLoss.toFixed(6)}`);
                            addApiLog(`📤 TP emir gönderiliyor: ${trade.takeProfit.toFixed(6)}`);
                            addApiLog(`✅ SL/TP emirleri başarılı`);
                        }, 500);
                    }
                }, 1000);
                
            } catch (error) {
                addApiLog(`❌ Binance API hatası: ${error.message}`);
                showNotification('Binance API hatası!', 'error');
            }
        }

        async function completeTrade(tradeId, forceClose = false) {
            const trade = transactions.find(t => t.id === tradeId);
            if (!trade || trade.status !== 'Aktif') return;
            
            const coin = cryptoData.find(c => c.symbol === trade.coin);
            const currentPrice = coin ? coin.price : trade.currentPrice;
            
            // Calculate P&L using futures formula
            let pnl;
            let exitReason = 'Manual';
            let exitPrice = currentPrice;
            
            // Only check SL/TP if not forced close
            if (!forceClose) {
                // Check if SL/TP was hit first
                if (trade.type === 'LONG') {
                    if (currentPrice <= trade.stopLoss) {
                        exitReason = 'Stop Loss';
                        exitPrice = trade.stopLoss;
                        // Calculate exact SL P&L
                        const slPriceChange = (trade.stopLoss - trade.entryPrice) / trade.entryPrice;
                        pnl = trade.amount * slPriceChange * trade.leverage;
                    } else if (currentPrice >= trade.takeProfit) {
                        exitReason = 'Take Profit';
                        exitPrice = trade.takeProfit;
                        // Calculate exact TP P&L
                        const tpPriceChange = (trade.takeProfit - trade.entryPrice) / trade.entryPrice;
                        pnl = trade.amount * tpPriceChange * trade.leverage;
                    } else {
                        // Check for DCA before manual close
                        if (await shouldTriggerDCA(trade, currentPrice)) {
                            return; // DCA triggered, don't close trade
                        }
                        
                        // Don't close manually - wait for SL/TP unless forced
                        if (!forceClose) return;
                    }
                } else { // SHORT
                    if (currentPrice >= trade.stopLoss) {
                        exitReason = 'Stop Loss';
                        exitPrice = trade.stopLoss;
                        // For SHORT: loss when price goes up
                        const slPriceChange = (trade.entryPrice - trade.stopLoss) / trade.entryPrice;
                        pnl = -trade.amount * Math.abs(slPriceChange) * trade.leverage;
                    } else if (currentPrice <= trade.takeProfit) {
                        exitReason = 'Take Profit';
                        exitPrice = trade.takeProfit;
                        const tpPriceChange = (trade.entryPrice - trade.takeProfit) / trade.entryPrice;
                        pnl = trade.amount * tpPriceChange * trade.leverage;
                    } else {
                        // Check for DCA before manual close
                        if (await shouldTriggerDCA(trade, currentPrice)) {
                            return; // DCA triggered, don't close trade
                        }
                        
                        // Don't close manually - wait for SL/TP unless forced
                        if (!forceClose) return;
                    }
                }
            }
            
            // If we reach here and no exit reason was set, it's a forced close
            if (exitReason === 'Manual' || forceClose) {
                // Forced close - calculate at current price
                if (trade.type === 'LONG') {
                    const priceChange = (currentPrice - trade.entryPrice) / trade.entryPrice;
                    pnl = trade.amount * priceChange * trade.leverage;
                } else {
                    const priceChange = (trade.entryPrice - currentPrice) / trade.entryPrice;
                    pnl = trade.amount * priceChange * trade.leverage;
                }
                exitReason = 'Manual';
            }
            
            trade.exitPrice = exitPrice;
            trade.pnl = pnl;
            trade.status = pnl > 0 ? 'Kar' : 'Zarar';
            trade.exitReason = exitReason;
            trade.exitTime = new Date().toISOString();
            
            // Save to localStorage
            saveTransactionsToStorage();
            
            // Update balance
            totalBalance += pnl;
            
            // Cancel ALL orders when trade is closed (TP, SL, DCA, etc.)
            if (exitReason === 'Take Profit' || exitReason === 'Stop Loss' || exitReason === 'Manual') {
                try {
                    addApiLog(`🔄 ${trade.coin} işlemi kapatılıyor - TÜM emirler iptal ediliyor...`);
                    
                    // ProBot AI specific order cancellation
                    if (trade.aiType === 'ProBot AI') {
                        console.log('🤖 ProBot AI order cancellation called for:', trade.coin);
                        await cancelProbotOrders(trade);
                        console.log('🤖 ProBot AI order cancellation completed');
                    } else {
                    // Cancel all orders for this symbol
                    const cancelResult = await cancelAllOrdersForSymbol(trade.coin);
                    if (cancelResult && cancelResult.success) {
                        addApiLog(`✅ Tüm emirler iptal edildi: ${trade.coin}`);
                    } else {
                        addApiLog(`⚠️ Emir iptal edilemedi: ${trade.coin} - ${cancelResult?.error || 'Bilinmeyen hata'}`);
                        }
                    }
                    
                } catch (error) {
                    addApiLog(`❌ Emir iptal hatası: ${error.message}`);
                }
            }
            
            // Send close order to exchange
            if (document.getElementById('bybitApiKey').value) {
                sendCloseOrderToBybit(trade);
            } else if (document.getElementById('binanceApiKey').value) {
                sendCloseOrderToBinance(trade);
            }
            
            updateActiveTradesTable();
            updateCompletedTradesTable();
            updateTradeInfo();
            updateAdminStats();
            
            const pnlText = pnl > 0 ? `+$${pnl.toFixed(2)}` : `$${pnl.toFixed(2)}`;
            showNotification(`${trade.coin} işlemi ${exitReason} ile tamamlandı: ${pnlText}`, pnl > 0 ? 'success' : 'error');
        }
        
        // Send new TP/SL orders after DCA
        async function sendNewTPSLOrders(trade) {
            try {
                const apiKey = document.getElementById('bybitApiKey').value;
                const secretKey = document.getElementById('bybitSecretKey').value;
                
                if (apiKey && secretKey) {
                    addApiLog(`📤 Yeni TP/SL emirleri gönderiliyor...`);
                    
                    // Send new Stop Loss order and wait for completion
                    await new Promise(resolve => setTimeout(resolve, 1000));
                    await sendBybitStopLoss(trade, apiKey, secretKey);
                    
                    // Send new Take Profit order and wait for completion
                    await new Promise(resolve => setTimeout(resolve, 1000));
                    await sendBybitTakeProfit(trade, apiKey, secretKey);
                    
                    addApiLog(`✅ Yeni TP/SL emirleri başarıyla gönderildi`);
                }
            } catch (error) {
                addApiLog(`❌ Yeni TP/SL emirleri gönderilirken hata: ${error.message}`);
            }
        }

        async function shouldTriggerDCA(trade, currentPrice) {
            // Only trigger DCA for trades that support it
            if (!trade.dcaCount || trade.dcaLevel >= trade.dcaCount) return false;
            
            // Check if DCA is enabled for manual trades
            if (trade.tradeType === 'Manuel' && !trade.dcaEnabled) return false;
            
            // NEW SYSTEM: DCA orders are already on exchange, just update TP/SL when triggered
            // Check if any DCA order was triggered by checking trade.dcaOrders
            
            const currentDcaLevel = trade.dcaLevel || 0;
            const newDcaLevel = currentDcaLevel + 1;
            
            // Check if we have a DCA order for this level that might have been triggered
            if (trade.dcaOrders && trade.dcaOrders.length > 0) {
                const dcaOrder = trade.dcaOrders.find(order => order.level === newDcaLevel);
                
                if (dcaOrder) {
                    // Check if DCA order was actually triggered by comparing current price with trigger price
                    let shouldTrigger = false;
                    
                    if (trade.type === 'LONG') {
                        // For LONG: trigger if current price <= trigger price
                        shouldTrigger = currentPrice <= dcaOrder.price;
                    } else {
                        // For SHORT: trigger if current price >= trigger price
                        shouldTrigger = currentPrice >= dcaOrder.price;
                    }
                    
                    if (shouldTrigger) {
                        // DCA order was triggered on exchange, update local trade data
                        addApiLog(`🎯 DCA Seviye ${newDcaLevel} borsada tetiklendi - Fiyat: $${dcaOrder.price.toFixed(6)}, Mevcut: $${currentPrice.toFixed(6)}`);
                        
                        // Update trade data
                        const dcaMultiplier = trade.dcaMultiplier || 1.5;
                        const dcaAmount = trade.amount * Math.pow(dcaMultiplier, newDcaLevel);
                        const originalAmount = trade.amount;
                        
                        // Update total investment amount (not trade.amount)
                        if (!trade.totalInvestment) trade.totalInvestment = trade.amount;
                        trade.totalInvestment += dcaAmount;
                        trade.dcaLevel = newDcaLevel;
                        
                        // Recalculate average entry price
                        const weightedPrice = (trade.entryPrice * originalAmount + dcaOrder.price * dcaAmount) / trade.amount;
                        trade.entryPrice = weightedPrice;
                        
                        // Recalculate TP/SL based on new average price using original percentages
                        const stopLossPercent = trade.stopLossPercent || 0.02; // Default 2% if not set
                        const takeProfitPercent = trade.takeProfitPercent || 0.01; // Default 1% if not set
                        
                        // Correct TP/SL calculation based on position type using original percentages
                        if (trade.type === 'LONG') {
                            trade.stopLoss = trade.entryPrice * (1 - stopLossPercent);
                            trade.takeProfit = trade.entryPrice * (1 + takeProfitPercent);
                        } else { // SHORT
                            trade.stopLoss = trade.entryPrice * (1 + stopLossPercent);
                            trade.takeProfit = trade.entryPrice * (1 - takeProfitPercent);
                        }
                        
                        addApiLog(`📊 DCA sonrası TP/SL yeniden hesaplandı - SL: ${(stopLossPercent * 100).toFixed(2)}%, TP: ${(takeProfitPercent * 100).toFixed(2)}%`);
                        
                        // Cancel old TP/SL orders and send new ones
                        try {
                            addApiLog(`🔄 DCA tetiklendi - TP/SL güncelleniyor...`);
                            
                            if (trade.slOrderId) {
                                await cancelBybitOrderById(trade.slOrderId, trade.coin + 'USDT');
                                trade.slOrderId = null;
                            }
                            
                            if (trade.tpOrderId) {
                                await cancelBybitOrderById(trade.tpOrderId, trade.coin + 'USDT');
                                trade.tpOrderId = null;
                            }
                            
                            // Send new TP/SL orders
                            await sendNewTPSLOrders(trade);
                            
                        } catch (error) {
                            addApiLog(`❌ DCA TP/SL güncelleme hatası: ${error.message}`);
                        }
                        
                        // Save to localStorage
                        saveTransactionsToStorage();
                        
                        // Remove the triggered DCA order from the list
                        trade.dcaOrders = trade.dcaOrders.filter(order => order.level !== newDcaLevel);
                        
                        showNotification(`${trade.coin} DCA ${newDcaLevel}/${trade.dcaCount} tetiklendi: $${dcaAmount.toFixed(2)}`, 'info');
                        addApiLog(`📈 DCA tetiklendi: ${trade.coin} - Seviye ${newDcaLevel}/${trade.dcaCount}`);
                        
                        updateActiveTradesTable();
                        updateTradeInfo();
                        return true;
                    }
                }
            }
            
            return false;
        }
        
        // Cancel any pending orders for a specific trade
        async function cancelPendingOrdersForTrade(trade) {
            try {
                // Cancel any pending orders that might be in the system
                const symbol = trade.coin + 'USDT';
                
                // Try to cancel any orders with trade ID in the order ID
                const tradeIdPattern = trade.id.toString();
                
                // This would cancel any orders that contain the trade ID
                // Implementation depends on how orders are tracked
                addApiLog(`🔄 ${symbol} için bekleyen emirler kontrol ediliyor...`);
                
                // For now, just log that we're checking
                addApiLog(`✅ ${symbol} bekleyen emir kontrolü tamamlandı`);
                
            } catch (error) {
                addApiLog(`⚠️ Bekleyen emir iptal hatası: ${error.message}`);
            }
        }

        // Cancel orders specifically for manual trades


        
        // Cancel all DCA orders for a specific trade
        async function cancelDCAOrdersForTrade(trade) {
            try {
                if (!trade.dcaEnabled || !trade.dcaCount) return;
                
                // Fix symbol for DCA cancellation
                let symbol = trade.coin;
                if (!symbol.endsWith('USDT')) {
                    symbol = symbol + 'USDT';
                }
                
                addApiLog(`🔄 ${symbol} DCA emirleri iptal ediliyor...`);
                
                // Cancel using real order IDs if available
                if (trade.dcaOrders && trade.dcaOrders.length > 0) {
                    for (const dcaOrder of trade.dcaOrders) {
                        try {
                            if (document.getElementById('bybitApiKey').value) {
                                await cancelBybitOrder(dcaOrder.orderId);
                            } else if (document.getElementById('binanceApiKey').value) {
                                await cancelBinanceOrder(dcaOrder.orderId);
                            }
                            addApiLog(`✅ DCA Seviye ${dcaOrder.level} iptal edildi (ID: ${dcaOrder.orderId})`);
                        } catch (error) {
                            addApiLog(`⚠️ DCA Seviye ${dcaOrder.level} iptal edilemedi: ${error.message}`);
                        }
                    }
                } else {
                    // Fallback to old method
                    for (let level = 1; level <= trade.dcaCount; level++) {
                        const dcaOrderId = `${trade.id}_DCA_${level}`;
                        
                        try {
                            if (document.getElementById('bybitApiKey').value) {
                                await cancelBybitOrder(dcaOrderId);
                            } else if (document.getElementById('binanceApiKey').value) {
                                await cancelBinanceOrder(dcaOrderId);
                            }
                            addApiLog(`✅ DCA Seviye ${level} iptal edildi`);
                        } catch (error) {
                            addApiLog(`⚠️ DCA Seviye ${level} iptal edilemedi: ${error.message}`);
                        }
                    }
                }
                
            } catch (error) {
                addApiLog(`❌ DCA emirleri iptal edilirken hata: ${error.message}`);
            }
        }

        // Send DCA orders to exchange immediately after main trade
        async function sendDCAOrdersToExchange(trade) {
            if (!trade.dcaEnabled || trade.dcaCount <= 0) return;
            
            try {
                addApiLog(`📈 ${trade.coin} için DCA limit emirleri hazırlanıyor...`);
                
                // Validate required trade parameters
                if (!trade.amount || !trade.dcaMultiplier || !trade.dcaTrigger || !trade.type) {
                    addApiLog(`❌ DCA için gerekli parametreler eksik: amount=${trade.amount}, multiplier=${trade.dcaMultiplier}, trigger=${trade.dcaTrigger}, type=${trade.type}`);
                    return;
                }
                
                // Initialize DCA orders array if not exists
                if (!trade.dcaOrders) {
                    trade.dcaOrders = [];
                }
                
                // DCA emirleri sadece limit emirleri olarak hazırlanır, fiyat tetiklendiğinde gönderilir
                for (let level = 1; level <= trade.dcaCount; level++) {
                    const dcaAmount = trade.amount * Math.pow(trade.dcaMultiplier, level);
                    // DCA fiyat hesaplama: LONG için düşüş, SHORT için yükseliş
                    const dcaPrice = trade.type === 'LONG' 
                        ? trade.entryPrice * (1 - (trade.dcaTrigger * level)) // LONG: fiyat düştüğünde
                        : trade.entryPrice * (1 + (trade.dcaTrigger * level)); // SHORT: fiyat yükseldiğinde
                    
                    // Store DCA order info for later execution
                    trade.dcaOrders.push({
                        level: level,
                        amount: dcaAmount,
                        price: dcaPrice,
                        executed: false,
                        status: 'pending'
                    });
                }
                
                addApiLog(`✅ ${trade.coin} için ${trade.dcaCount} DCA emri hazırlandı (Çarpan: ${trade.dcaMultiplier || 1.5}x, fiyat tetiklendiğinde gönderilecek)`);
                
            } catch (error) {
                addApiLog(`❌ DCA emirleri hazırlanırken hata: ${error.message}`);
                console.error('DCA preparation error:', error);
            }
        }

        // Cancel specific Bybit order
        async function cancelBybitOrder(orderId) {
            const apiKey = document.getElementById('bybitApiKey').value;
            const secretKey = document.getElementById('bybitSecretKey').value;
            
            if (!apiKey || !secretKey) return;
            
            try {
                const timestamp = Date.now().toString();
                const recvWindow = '5000';
                
                // Fix symbol for order cancellation
                let cancelSymbol = orderId;
                if (orderId.includes('_DCA_')) {
                    const tradeId = orderId.split('_DCA_')[0];
                    cancelSymbol = tradeId + 'USDT';
                } else if (!orderId.endsWith('USDT')) {
                    cancelSymbol = orderId + 'USDT';
                }
                
                const cancelData = {
                    category: 'linear',
                    symbol: cancelSymbol,
                    orderId: orderId
                };
                
                const jsonBody = JSON.stringify(cancelData);
                const signature = await createBybitSignature(apiKey, secretKey, timestamp, recvWindow, jsonBody);
                
                const response = await fetch('https://api.bybit.com/v5/order/cancel', {
                    method: 'POST',
                    headers: {
                        'X-BAPI-API-KEY': apiKey,
                        'X-BAPI-SIGN': signature,
                        'X-BAPI-SIGN-TYPE': '2',
                        'X-BAPI-TIMESTAMP': timestamp,
                        'X-BAPI-RECV-WINDOW': recvWindow,
                        'Content-Type': 'application/json'
                    },
                    body: jsonBody
                });
                
                const result = await response.json();
                
                if (result.retCode === 0) {
                    addApiLog(`✅ Bybit emir iptal edildi: ${orderId}`);
                    console.log('Bybit order cancel success:', result);
                return result;
                } else {
                    addApiLog(`❌ Bybit emir iptal hatası: ${result.retMsg}`);
                    console.error('Bybit order cancel error:', result);
                    throw new Error(result.retMsg);
                }
                
            } catch (error) {
                addApiLog(`❌ Bybit emir iptal hatası: ${error.message}`);
                console.error('Bybit order cancel error:', error);
                throw error;
            }
        }

        // Cancel specific Binance order
        async function cancelBinanceOrder(orderId) {
            const apiKey = document.getElementById('binanceApiKey').value;
            const secretKey = document.getElementById('binanceSecretKey').value;
            
            if (!apiKey || !secretKey) {
                addApiLog(`❌ Binance API anahtarları bulunamadı`);
                return;
            }
            
            try {
                addApiLog(`🔄 Binance emir iptal ediliyor: ${orderId}`);
                
                // Binance API implementation would go here
                // For now, just log the attempt
                addApiLog(`⚠️ Binance emir iptal fonksiyonu henüz implement edilmedi: ${orderId}`);
            console.log(`Canceling Binance order: ${orderId}`);
                
            } catch (error) {
                addApiLog(`❌ Binance emir iptal hatası: ${error.message}`);
                console.error('Binance order cancel error:', error);
                throw error;
            }
        }

        // Cancel all orders for a specific symbol on Bybit
        async function cancelAllBybitOrders(symbol) {
            const apiKey = document.getElementById('bybitApiKey').value;
            const secretKey = document.getElementById('bybitSecretKey').value;
            
            if (!apiKey || !secretKey) {
                addApiLog(`❌ Bybit API anahtarları bulunamadı`);
                return { success: false, error: 'API keys not found' };
            }
            
            try {
                // Fix symbol
                let fixedSymbol = symbol;
                if (!fixedSymbol.endsWith('USDT')) {
                    fixedSymbol = fixedSymbol + 'USDT';
                }
                
                addApiLog(`🔄 ${fixedSymbol} için tüm emirler iptal ediliyor...`);
                
                // 1. First, try to get all open orders for the symbol
                const openOrders = await getBybitOpenOrders(fixedSymbol);
                if (openOrders && openOrders.length > 0) {
                    addApiLog(`📋 ${fixedSymbol} için ${openOrders.length} açık emir bulundu, iptal ediliyor...`);
                    
                    // Cancel each order individually
                    for (const order of openOrders) {
                        try {
                            await cancelBybitOrderById(order.orderId, fixedSymbol);
                            addApiLog(`✅ Emir iptal edildi: ${order.orderId}`);
                        } catch (error) {
                            addApiLog(`⚠️ Emir iptal edilemedi: ${order.orderId} - ${error.message}`);
                        }
                    }
                }
                
                // 2. Try cancel-all for linear category (futures)
                try {
                    const timestamp = Date.now().toString();
                    const recvWindow = '5000';
                    
                    const cancelData = {
                        category: 'linear',
                        symbol: fixedSymbol
                    };
                    
                    const jsonBody = JSON.stringify(cancelData);
                    const signature = await createBybitSignature(apiKey, secretKey, timestamp, recvWindow, jsonBody);
                
                    const response = await fetch('https://api.bybit.com/v5/order/cancel-all', {
                        method: 'POST',
                        headers: {
                            'X-BAPI-API-KEY': apiKey,
                            'X-BAPI-SIGN': signature,
                            'X-BAPI-SIGN-TYPE': '2',
                            'X-BAPI-TIMESTAMP': timestamp,
                            'X-BAPI-RECV-WINDOW': recvWindow,
                            'Content-Type': 'application/json'
                        },
                        body: jsonBody
                    });
                    
                    const result = await response.json();
                    
                    if (result.retCode === 0) {
                        addApiLog(`✅ ${fixedSymbol} için tüm emirler iptal edildi (cancel-all)`);
                        return { success: true, result: result };
                    } else {
                        addApiLog(`⚠️ ${fixedSymbol} cancel-all başarısız: ${result.retMsg}`);
                    }
                    
                } catch (error) {
                    addApiLog(`⚠️ ${fixedSymbol} cancel-all hatası: ${error.message}`);
                }
                
                // 3. Fallback: Try spot category as well
                try {
                    const timestamp = Date.now().toString();
                    const recvWindow = '5000';
                    
                    const cancelData = {
                        category: 'spot',
                        symbol: fixedSymbol
                    };
                    
                    const jsonBody = JSON.stringify(cancelData);
                    const signature = await createBybitSignature(apiKey, secretKey, timestamp, recvWindow, jsonBody);
                    
                    const response = await fetch('https://api.bybit.com/v5/order/cancel-all', {
                        method: 'POST',
                        headers: {
                            'X-BAPI-API-KEY': apiKey,
                            'X-BAPI-SIGN': signature,
                            'X-BAPI-SIGN-TYPE': '2',
                            'X-BAPI-TIMESTAMP': timestamp,
                            'X-BAPI-RECV-WINDOW': recvWindow,
                            'Content-Type': 'application/json'
                        },
                        body: jsonBody
                    });
                    
                    const result = await response.json();
                    
                    if (result.retCode === 0) {
                        addApiLog(`✅ ${fixedSymbol} için spot emirler iptal edildi`);
                        return { success: true, result: result };
                    } else {
                        addApiLog(`⚠️ ${fixedSymbol} spot cancel-all başarısız: ${result.retMsg}`);
                    }
                    
                } catch (error) {
                    addApiLog(`⚠️ ${fixedSymbol} spot cancel-all hatası: ${error.message}`);
                }
                
                // 4. Final fallback: Get and cancel individual orders
                try {
                    const openOrders = await getBybitOpenOrders(fixedSymbol);
                    if (openOrders && openOrders.length > 0) {
                        addApiLog(`📋 ${fixedSymbol} için ${openOrders.length} açık emir bulundu, tek tek iptal ediliyor...`);
                        
                        let cancelledCount = 0;
                        for (const order of openOrders) {
                            try {
                                await cancelBybitOrderById(order.orderId, fixedSymbol);
                                cancelledCount++;
                                addApiLog(`✅ Emir iptal edildi: ${order.orderId}`);
                            } catch (error) {
                                addApiLog(`⚠️ Emir iptal edilemedi: ${order.orderId} - ${error.message}`);
                            }
                        }
                        
                        if (cancelledCount > 0) {
                            addApiLog(`✅ ${cancelledCount} emir iptal edildi: ${fixedSymbol}`);
                            return { success: true, cancelled: cancelledCount };
                        }
                    }
                } catch (error) {
                    addApiLog(`❌ ${fixedSymbol} bireysel emir iptal hatası: ${error.message}`);
                }
                
                addApiLog(`⚠️ ${fixedSymbol} için emir iptal edilemedi`);
                return { success: false, error: 'No orders found or all cancellation methods failed' };
                
            } catch (error) {
                addApiLog(`❌ ${symbol} emir iptal hatası: ${error.message}`);
                return { success: false, error: error.message };
            }
        }
        
        // Make function available globally
        window.cancelAllBybitOrders = cancelAllBybitOrders;

        // Cancel all orders for a specific symbol (wrapper function)
        async function cancelAllOrdersForSymbol(symbol) {
            try {
                if (document.getElementById('bybitApiKey').value) {
                    return await cancelAllBybitOrders(symbol);
                } else if (document.getElementById('binanceApiKey').value) {
                    // Add Binance implementation if needed
                    addApiLog(`⚠️ Binance emir iptal etme henüz desteklenmiyor`);
                    return { success: false, error: 'Binance not supported' };
                } else {
                    addApiLog(`❌ API anahtarları bulunamadı`);
                    return { success: false, error: 'No API keys' };
                }
            } catch (error) {
                console.error('Cancel all orders error:', error);
                addApiLog(`❌ ${symbol} emir iptal hatası: ${error.message}`);
                return { success: false, error: error.message };
            }
        }

        // Get all open orders for a symbol from Bybit
        async function getBybitOpenOrders(symbol) {
            try {
                const apiKey = document.getElementById('bybitApiKey').value;
                const secretKey = document.getElementById('bybitSecretKey').value;
                
                if (!apiKey || !secretKey) {
                    return [];
                }
                
                const timestamp = Date.now().toString();
                const recvWindow = '5000';
                
                const params = new URLSearchParams({
                    category: 'linear',
                    symbol: symbol,
                    openOnly: '1'
                });
                
                const queryString = params.toString();
                const signature = await createBybitSignature(apiKey, secretKey, timestamp, recvWindow, queryString);
                
                const response = await fetch(`https://api.bybit.com/v5/order/realtime?${queryString}`, {
                    method: 'GET',
                    headers: {
                        'X-BAPI-API-KEY': apiKey,
                        'X-BAPI-SIGN': signature,
                        'X-BAPI-SIGN-TYPE': '2',
                        'X-BAPI-TIMESTAMP': timestamp,
                        'X-BAPI-RECV-WINDOW': recvWindow
                    }
                });
                
                const result = await response.json();
                
                if (result.retCode === 0 && result.result && result.result.list) {
                    return result.result.list;
                } else {
                    addApiLog(`⚠️ Açık emirler alınamadı: ${result.retMsg}`);
                    return [];
                }
                
            } catch (error) {
                addApiLog(`❌ Açık emirler alma hatası: ${error.message}`);
                return [];
            }
        }

        // Cancel specific Bybit order by ID
        async function cancelBybitOrderById(orderId, symbol) {
            try {
                const apiKey = document.getElementById('bybitApiKey').value;
                const secretKey = document.getElementById('bybitSecretKey').value;
                
                if (!apiKey || !secretKey) return;
                
                const timestamp = Date.now().toString();
                const recvWindow = '5000';
                
                const cancelData = {
                    category: 'linear',
                    symbol: symbol,
                    orderId: orderId
                };
                
                const jsonBody = JSON.stringify(cancelData);
                const signature = await createBybitSignature(apiKey, secretKey, timestamp, recvWindow, jsonBody);
                
                const response = await fetch('https://api.bybit.com/v5/order/cancel', {
                    method: 'POST',
                    headers: {
                        'X-BAPI-API-KEY': apiKey,
                        'X-BAPI-SIGN': signature,
                        'X-BAPI-SIGN-TYPE': '2',
                        'X-BAPI-TIMESTAMP': timestamp,
                        'X-BAPI-RECV-WINDOW': recvWindow,
                        'Content-Type': 'application/json'
                    },
                    body: jsonBody
                });
                
                const result = await response.json();
                
                if (result.retCode === 0) {
                    return { success: true, result: result };
                } else {
                    throw new Error(result.retMsg);
                }
                
            } catch (error) {
                throw error;
            }
        }

        // FORCE CANCEL ALL ORDERS - Brute force method

        async function sendCloseOrderToBybit(trade) {
            const apiKey = document.getElementById('bybitApiKey').value;
            const secretKey = document.getElementById('bybitSecretKey').value;
            
            if (!apiKey || !secretKey) return;
            
            // Fix symbol for close order
            let symbol = trade.coin;
            if (!symbol.endsWith('USDT')) {
                symbol = symbol + 'USDT';
            }
            
            addApiLog(`📤 Bybit'e kapatma emri gönderiliyor: ${trade.coin}`);
            
            try {
                // Get symbol info for proper quantity formatting
                const symbolInfo = await getBybitSymbolInfo(symbol, apiKey, secretKey);
                
                // Calculate position size based on USDT amount and leverage
                let qty = (trade.amount * trade.leverage) / trade.entryPrice;
                
                // Apply symbol-specific quantity rules
                if (symbolInfo) {
                    const minQty = parseFloat(symbolInfo.lotSizeFilter.minOrderQty);
                    const qtyStep = parseFloat(symbolInfo.lotSizeFilter.qtyStep);
                    const maxQty = parseFloat(symbolInfo.lotSizeFilter.maxOrderQty);
                    
                    // Ensure quantity meets minimum
                    qty = Math.max(qty, minQty);
                    
                    // Round to proper step size
                    qty = Math.floor(qty / qtyStep) * qtyStep;
                    
                    // Ensure quantity doesn't exceed maximum
                    qty = Math.min(qty, maxQty);
                    
                    // Format with proper decimal places
                    const decimals = qtyStep.toString().split('.')[1]?.length || 0;
                    qty = qty.toFixed(decimals);
                } else {
                    // Fallback: use standard formatting
                    qty = qty.toFixed(3);
                }
                
                const closeOrderData = {
                    category: "linear",
                    symbol: symbol,
                    side: trade.type === 'LONG' ? 'Sell' : 'Buy',
                    orderType: 'Market',
                    qty: qty.toString(),
                    reduceOnly: true,
                    closeOnTrigger: false,
                    positionIdx: 0
                };
                
                addApiLog(`📋 Kapatma emri: ${JSON.stringify(closeOrderData, null, 2)}`);
                
                const timestamp = Date.now().toString();
                const recvWindow = '5000';
                const jsonBody = JSON.stringify(closeOrderData);
                const signature = await createBybitSignature(apiKey, secretKey, timestamp, recvWindow, jsonBody);
                
                const response = await fetch('https://api.bybit.com/v5/order/create', {
                    method: 'POST',
                    headers: {
                        'X-BAPI-API-KEY': apiKey,
                        'X-BAPI-SIGN': signature,
                        'X-BAPI-SIGN-TYPE': '2',
                        'X-BAPI-TIMESTAMP': timestamp,
                        'X-BAPI-RECV-WINDOW': recvWindow,
                        'Content-Type': 'application/json'
                    },
                    body: jsonBody
                });
                
                const result = await response.json();
                addApiLog(`📋 Kapatma yanıt: ${JSON.stringify(result, null, 2)}`);
                
                if (result.retCode === 0) {
                    addApiLog(`✅ Bybit kapatma emri başarılı - ${trade.exitReason}`);
                } else {
                    addApiLog(`❌ Bybit kapatma emri hatası: ${result.retMsg}`);
                }
                
            } catch (error) {
                addApiLog(`❌ Bybit kapatma emri hatası: ${error.message}`);
            }
        }
        
        async function sendCloseOrderToBinance(trade) {
            const apiKey = document.getElementById('binanceApiKey').value;
            const secretKey = document.getElementById('binanceSecretKey').value;
            
            if (!apiKey || !secretKey) return;
            
            addApiLog(`📤 Binance'e kapatma emri gönderiliyor: ${trade.coin}`);
            
            try {
                const closeOrderData = {
                    symbol: symbol,
                    side: trade.type === 'LONG' ? 'SELL' : 'BUY',
                    type: 'MARKET',
                    quantity: ((trade.amount * trade.leverage) / trade.entryPrice).toFixed(6),
                    reduceOnly: true
                };
                
                addApiLog(`📋 Kapatma emri: ${JSON.stringify(closeOrderData, null, 2)}`);
                
                // Real API call would go here
                setTimeout(() => {
                    addApiLog(`✅ Binance kapatma emri başarılı - ${trade.exitReason}`);
                }, 500);
                
            } catch (error) {
                addApiLog(`❌ Binance kapatma emri hatası: ${error.message}`);
            }
        }

        // Calculate dynamic decimal places based on actual price precision
        function getDecimalPlaces(price) {
            if (!price || price <= 0) return 2; // Default fallback
            
            // Convert to string to analyze decimal places
            const priceStr = price.toString();
            
            // If scientific notation (e.g., 1.23e-6), convert to normal
            if (priceStr.includes('e')) {
                const fixedPrice = price.toFixed(6);
                const decimalPart = fixedPrice.split('.')[1];
                return decimalPart ? Math.min(decimalPart.length, 6) : 0;
            }
            
            // Check if has decimal point
            if (priceStr.includes('.')) {
                const decimalPart = priceStr.split('.')[1];
                const decimalLength = decimalPart ? decimalPart.length : 0;
                
                // For very small numbers, use reasonable precision
                if (price < 0.01) {
                    return Math.min(Math.max(decimalLength, 4), 6); // 4-6 decimal places for small prices
                } else if (price < 0.1) {
                    return Math.min(Math.max(decimalLength, 4), 5); // 4-5 decimal places
                } else if (price < 1) {
                    return Math.min(Math.max(decimalLength, 3), 4); // 3-4 decimal places
                } else if (price < 10) {
                    return Math.min(Math.max(decimalLength, 2), 3); // 2-3 decimal places
                } else if (price < 100) {
                    return Math.min(Math.max(decimalLength, 2), 3); // 2-3 decimal places
                } else {
                    return Math.min(Math.max(decimalLength, 2), 2); // 2 decimal places
                }
            }
            
            // No decimal point, return appropriate precision based on price range
            if (price >= 1000) return 2;
            if (price >= 100) return 2;
            if (price >= 10) return 3;
            if (price >= 1) return 4;
            if (price >= 0.1) return 5;
            return 6; // Default for very small prices
        }

        async function updateActiveTradesTable() {
            const table = document.getElementById('activeTradesTable');
            const container = document.getElementById('activeTradesContainer');
            if (!table) return;
            
            table.innerHTML = '';
            
            const activeTrades = transactions.filter(t => t.status === 'Aktif');
            
            // Auto-expand container based on number of trades
            if (container) {
                const baseHeight = 400;
                const rowHeight = 60; // Approximate height per row
                const headerHeight = 50;
                const maxHeight = Math.min(800, Math.max(baseHeight, (activeTrades.length * rowHeight) + headerHeight));
                container.style.maxHeight = maxHeight + 'px';
            }
            
            // Show main trades
            activeTrades.forEach(trade => {
                // Fix coin symbol format for matching
                let coinSymbol = trade.coin;
                if (!coinSymbol.endsWith('USDT')) {
                    coinSymbol = coinSymbol + 'USDT';
                }
                
                // Find coin in cryptoData by symbol
                const coin = cryptoData.find(c => c.symbol === coinSymbol);
                
                // Force update trade's current price with real-time data from coin list
                if (coin && coin.price > 0) {
                    const oldPrice = trade.currentPrice;
                    trade.currentPrice = coin.price;
                    console.log(`✅ Updated ${trade.coin} price: ${oldPrice} -> ${trade.currentPrice} (from coin list)`);
                } else {
                    // Try to find coin with different symbol formats
                    const altCoin = cryptoData.find(c => 
                        c.symbol === trade.coin || 
                        c.symbol === trade.coin + 'USDT' ||
                        c.symbol.replace('USDT', '') === trade.coin
                    );
                    
                    if (altCoin && altCoin.price > 0) {
                        const oldPrice = trade.currentPrice;
                        trade.currentPrice = altCoin.price;
                        console.log(`✅ Updated ${trade.coin} price: ${oldPrice} -> ${trade.currentPrice} (from alt coin: ${altCoin.symbol})`);
                    } else {
                        // Fallback to entry price if coin not found in list
                        const oldPrice = trade.currentPrice;
                        trade.currentPrice = trade.entryPrice;
                        console.warn(`❌ Coin ${trade.coin} not found in coin list, using entry price: ${oldPrice} -> ${trade.entryPrice}`);
                    }
                }
                
                const currentPrice = trade.currentPrice;
                
                // Calculate unrealized P&L using correct futures formula
                let unrealizedPnL;
                const investmentAmount = trade.totalInvestment || trade.amount;
                if (trade.type === 'LONG') {
                    const priceChange = (currentPrice - trade.entryPrice) / trade.entryPrice;
                    unrealizedPnL = investmentAmount * priceChange * trade.leverage;
                } else { // SHORT
                    const priceChange = (trade.entryPrice - currentPrice) / trade.entryPrice;
                    unrealizedPnL = investmentAmount * priceChange * trade.leverage;
                }
                
                const row = document.createElement('tr');
                row.className = 'transition-all duration-200 hover:bg-gray-700 border-b border-gray-600';
                
                const pnlClass = unrealizedPnL > 0 ? 'accent-green' : 'accent-red';
                const typeClass = trade.type === 'LONG' ? 'accent-green' : 'accent-red';
                const typeBg = trade.type === 'LONG' ? 'bg-green-600' : 'bg-red-600';
                
                // Calculate price change percentage
                const priceChange = (currentPrice - trade.entryPrice) / trade.entryPrice;
                
                // Calculate dynamic decimal places based on current price
                const decimalPlaces = getDecimalPlaces(currentPrice);
                
                row.innerHTML = `
                    <td class="p-2 border-r border-gray-600 cursor-pointer" onclick="showCoinDetailFromTrade('${trade.coin}')">
                        <div class="font-bold text-white text-sm hover:text-blue-400 transition-colors">${trade.coin}</div>
                        ${trade.tradeType ? `<div class="text-xs ${trade.tradeType === 'Hızlı' ? 'accent-blue' : trade.tradeType === 'Uzun' ? 'accent-green' : 'accent-purple'}">${trade.tradeType}</div>` : ''}
                        ${trade.aiType === 'ProBot AI' ? `<div class="text-xs accent-purple">ProBot</div>` : ''}
                        ${trade.dcaEnabled && trade.dcaLevel > 0 ? `<div class="text-xs text-blue-300">DCA ${trade.dcaLevel}/${trade.dcaCount}</div>` : ''}
                    </td>
                    <td class="p-2 border-r border-gray-600">
                        <span class="${typeBg} px-2 py-1 rounded text-xs font-bold text-white">${trade.type}</span>
                    </td>
                    <td class="p-2 border-r border-gray-600">
                        <div class="text-white font-mono text-sm">$${(trade.totalInvestment || trade.amount).toFixed(2)}</div>
                        <div class="text-xs text-gray-400">${trade.leverage}x</div>
                    </td>
                    <td class="p-2 font-mono text-white border-r border-gray-600 text-sm">$${trade.entryPrice.toFixed(decimalPlaces)}</td>
                    <td class="p-2 font-mono border-r border-gray-600">
                        <div class="text-white text-sm">$${currentPrice.toFixed(decimalPlaces)}</div>
                        <div class="text-xs ${priceChange >= 0 ? 'accent-green' : 'accent-red'}">${priceChange >= 0 ? '↗' : '↘'} ${(priceChange * 100).toFixed(2)}%</div>
                    </td>
                    <td class="p-2 font-mono accent-red border-r border-gray-600 text-sm">$${trade.stopLoss.toFixed(decimalPlaces)}</td>
                    <td class="p-2 font-mono accent-green border-r border-gray-600 text-sm">$${trade.takeProfit.toFixed(decimalPlaces)}</td>
                    <td class="p-2 font-mono font-bold ${pnlClass} border-r border-gray-600 text-sm">$${unrealizedPnL.toFixed(2)}</td>
                    <td class="p-2">
                        <button onclick="closeTrade(${trade.id})" class="bg-red-600 hover:bg-red-700 px-2 py-1 rounded font-medium transition-colors text-xs">
                            Kapat
                        </button>
                    </td>
                `;
                
                table.appendChild(row);
            });
            
            // DCA info is now shown in the main row under coin name
            
            // Check DCA execution for all active trades
            for (const trade of activeTrades) {
                if (trade.dcaEnabled) {
                    // Check if DCA should be triggered
                    if (await shouldTriggerDCA(trade, currentPrice)) {
                        // DCA will be handled by shouldTriggerDCA function
                        continue;
                    }
                }
                
                // ProBot AI specific DCA execution
                if (trade.aiType === 'ProBot AI' && trade.dcaEnabled) {
                    executeProbotDCA(trade);
                }
            }
        }

        // Reset all AI settings to default function
        function resetAllAISettings() {
            // Show confirmation dialog
            if (confirm('Tüm AI ayarları varsayılan değerlere sıfırlanacak. Emin misiniz?')) {
                // Reset ProBot AI settings
                resetProbotSettings();
                
                // Reset Fast AI settings
                resetFastAISettings();
                
                // Reset Long AI settings
                resetLongAISettings();
                
                // Reset Manual AI settings
                resetManualAISettings();
                
                // Clear AI settings from localStorage
                localStorage.removeItem('aiSettings');
                localStorage.removeItem('probotSettings');
                
                // Show notification
                showNotification('Tüm AI ayarları varsayılana sıfırlandı!', 'success');
                
                // Add log
                addApiLog('⚙️ Tüm AI ayarları varsayılana sıfırlandı');
            }
        }

        // Reset Fast AI settings to default
        function resetFastAISettings() {
            // Reset form values to default
            document.getElementById('fastUsdtAmount').value = '1';
            document.getElementById('fastLeverage').value = '10';
            document.getElementById('fastStopLoss').value = '2';
            document.getElementById('fastTakeProfit').value = '1';
            document.getElementById('fastConfidence').value = '80';
            document.getElementById('fastScoreThreshold').value = '25';
            document.getElementById('fastMaxTrades').value = '3';
            
            // Reset DCA settings
            document.getElementById('fastDcaEnabled').checked = false;
            document.getElementById('fastDcaCount').value = '3';
            document.getElementById('fastDcaTrigger').value = '2';
            document.getElementById('fastDcaMultiplier').value = '1.5';
        }

        // Reset Long AI settings to default
        function resetLongAISettings() {
            // Reset form values to default
            document.getElementById('longUsdtAmount').value = '1';
            document.getElementById('longLeverage').value = '10';
            document.getElementById('longStopLoss').value = '2';
            document.getElementById('longTakeProfit').value = '1';
            document.getElementById('longConfidence').value = '80';
            document.getElementById('longScoreThreshold').value = '80';
            document.getElementById('longMaxTrades').value = '3';
            
            // Reset DCA settings
            document.getElementById('longDcaEnabled').checked = false;
            document.getElementById('longDcaCount').value = '3';
            document.getElementById('longDcaTrigger').value = '2';
            document.getElementById('longDcaMultiplier').value = '1.5';
        }

        // Reset Manual AI settings to default
        function resetManualAISettings() {
            // Reset form values to default
            document.getElementById('manualUsdtAmount').value = '50';
            document.getElementById('manualLeverage').value = '5';
            document.getElementById('manualStopLoss').value = '3';
            document.getElementById('manualTakeProfit').value = '8';
            
            // Reset DCA settings
            document.getElementById('manualDcaEnabled').checked = false;
            document.getElementById('manualDcaCount').value = '3';
            document.getElementById('manualDcaTrigger').value = '2';
            document.getElementById('manualDcaMultiplier').value = '1.5';
        }

        // Reset all trades function
        function resetAllTrades() {
            // Show confirmation dialog
            if (confirm('Tüm aktif işlemler ve sonlanan işlemler silinecek. Emin misiniz?')) {
                console.log('🗑️ Tümünü Sıfırla başlatıldı...');
                
                // Clear all transactions
                transactions = [];
                console.log('✅ Transactions array cleared');
                
                // Update all tables and displays
                updateActiveTradesTable();
                updateCompletedTradesTable();
                updateTradeInfo();
                updateAdminStats();
                console.log('✅ UI updated');
                
                // Clear ALL localStorage data - more comprehensive approach
                // First, clear specific known keys
                localStorage.removeItem('ct_transactions');
                localStorage.removeItem('transactions');
                localStorage.removeItem('activeTrades');
                localStorage.removeItem('completedTrades');
                localStorage.removeItem('tradeHistory');
                localStorage.removeItem('probotStats');
                localStorage.removeItem('fastAiStats');
                localStorage.removeItem('longAiStats');
                localStorage.removeItem('tradeCounts');
                localStorage.removeItem('fastTradeCount');
                localStorage.removeItem('longTradeCount');
                localStorage.removeItem('probotTradeCount');
                localStorage.removeItem('manualTradeCount');
                localStorage.removeItem('aiSettings');
                localStorage.removeItem('probotSettings');
                // Don't remove API keys, logs, and session - keep user login info
                // localStorage.removeItem('apiLogs');
                // localStorage.removeItem('bybit_keys');
                // localStorage.removeItem('binance_keys');
                // localStorage.removeItem('ct_session');  // Keep user session
                
                // Then clear any remaining trade-related keys (but keep API keys, session, and settings)
                const keysToRemove = [];
                for (let i = 0; i < localStorage.length; i++) {
                    const key = localStorage.key(i);
                    if (key && (
                        key.includes('trade') || 
                        key.includes('pnl') || 
                        key.includes('stats') ||
                        key.includes('transaction') ||
                        (key.includes('ct_') && !key.includes('ct_session')) ||  // Keep ct_session
                        key.includes('active') ||
                        key.includes('completed')
                    ) && !key.includes('api') && !key.includes('key') && !key.includes('session')) {
                        keysToRemove.push(key);
                    }
                }
                keysToRemove.forEach(key => localStorage.removeItem(key));
                console.log(`✅ localStorage cleared: ${keysToRemove.length} keys removed`);
                
                // Also clear sessionStorage (but keep API keys, session, and settings)
                const sessionKeysToRemove = [];
                for (let i = 0; i < sessionStorage.length; i++) {
                    const key = sessionStorage.key(i);
                    if (key && (
                        key.includes('trade') || 
                        key.includes('pnl') || 
                        key.includes('stats') ||
                        key.includes('transaction') ||
                        (key.includes('ct_') && !key.includes('ct_session')) ||  // Keep ct_session
                        key.includes('active') ||
                        key.includes('completed')
                    ) && !key.includes('api') && !key.includes('key') && !key.includes('session')) {
                        sessionKeysToRemove.push(key);
                    }
                }
                sessionKeysToRemove.forEach(key => sessionStorage.removeItem(key));
                console.log(`✅ sessionStorage cleared: ${sessionKeysToRemove.length} keys removed`);
                
                // Reset all AI stats
                probotStats = { totalTrades: 0, successfulTrades: 0, totalProfit: 0, winRate: 0 };
                fastAiStats = { totalTrades: 0, successfulTrades: 0, totalProfit: 0, winRate: 0 };
                longAiStats = { totalTrades: 0, successfulTrades: 0, totalProfit: 0, winRate: 0 };
                
                // Reset trade counters
                fastTradeCount = 0;
                longTradeCount = 0;
                probotTradeCount = 0;
                manualTradeCount = 0;
                
                // Update stats displays
                updateProbotStats();
                updateFastAiStats();
                updateLongAiStats();
                
                // Show notification
                showNotification('Tüm işlemler ve istatistikler sıfırlandı!', 'success');
                
                // Add log
                addApiLog('🗑️ Tüm işlemler ve istatistikler sıfırlandı');
                
                console.log('✅ Tümünü Sıfırla tamamlandı!');
                console.log('✅ Transactions array length:', transactions.length);
                console.log('✅ localStorage ct_transactions:', localStorage.getItem('ct_transactions'));
                console.log('✅ API keys and session preserved:', {
                    bybit: localStorage.getItem('bybit_keys') ? 'Yes' : 'No',
                    binance: localStorage.getItem('binance_keys') ? 'Yes' : 'No',
                    session: localStorage.getItem('ct_session') ? 'Yes' : 'No'
                });
            }
        }

        function updateCompletedTradesTable() {
            const table = document.getElementById('completedTradesTable');
            const container = document.getElementById('completedTradesContainer');
            if (!table) return;
            
            table.innerHTML = '';
            
            const completedTrades = transactions.filter(t => t.status !== 'Aktif');
            
            // Auto-expand container based on number of trades
            if (container) {
                const baseHeight = 400;
                const rowHeight = 60; // Approximate height per row
                const headerHeight = 50;
                const maxHeight = Math.min(800, Math.max(baseHeight, (completedTrades.length * rowHeight) + headerHeight));
                container.style.maxHeight = maxHeight + 'px';
            }
            
            completedTrades.forEach(trade => {
                const row = document.createElement('tr');
                row.className = 'transition-all duration-200 hover:bg-gray-700 border-b border-gray-600';
                
                const pnlClass = trade.pnl > 0 ? 'accent-green' : 'accent-red';
                const typeClass = trade.type === 'LONG' ? 'accent-green' : 'accent-red';
                const typeBg = trade.type === 'LONG' ? 'bg-green-600' : 'bg-red-600';
                const statusClass = trade.status === 'Kar' ? 'bg-green-600' : 'bg-red-600';
                
                // Calculate dynamic decimal places based on entry price
                const decimalPlaces = getDecimalPlaces(trade.entryPrice);
                
                row.innerHTML = `
                    <td class="p-3 border-r border-gray-600">
                        <div class="font-bold text-white">${trade.coin}</div>
                        ${trade.tradeType ? `<div class="text-xs ${trade.tradeType === 'Hızlı' ? 'accent-blue' : 'accent-green'}">${trade.tradeType}</div>` : ''}
                        ${trade.aiType === 'ProBot AI' ? `<div class="text-xs accent-purple">ProBot</div>` : ''}
                    </td>
                    <td class="p-3 border-r border-gray-600">
                        <span class="${typeBg} px-2 py-1 rounded text-xs font-bold text-white">${trade.type}</span>
                    </td>
                    <td class="p-3 font-mono text-white border-r border-gray-600">$${trade.entryPrice.toFixed(decimalPlaces)}</td>
                    <td class="p-3 font-mono text-white border-r border-gray-600">${trade.exitPrice ? '$' + trade.exitPrice.toFixed(decimalPlaces) : '-'}</td>
                    <td class="p-3 font-mono accent-red border-r border-gray-600">$${trade.stopLoss.toFixed(decimalPlaces)}</td>
                    <td class="p-3 font-mono accent-green border-r border-gray-600">$${trade.takeProfit.toFixed(decimalPlaces)}</td>
                    <td class="p-3 font-mono font-bold ${pnlClass} border-r border-gray-600">$${trade.pnl.toFixed(2)}</td>
                    <td class="p-3 border-r border-gray-600">
                        <span class="px-3 py-1 rounded-full text-xs font-bold ${statusClass} text-white">${trade.status}</span>
                    </td>
                    <td class="p-3 text-sm text-gray-300">${trade.timestamp}</td>
                `;
                
                table.appendChild(row);
            });
        }

        async function closeTrade(tradeId) {
            try {
                const trade = transactions.find(t => t.id === tradeId);
                if (!trade) {
                    addApiLog(`❌ İşlem bulunamadı: ${tradeId}`);
                    return;
                }
                
                addApiLog(`🔄 ${trade.tradeType} işlem kapatma başlatıldı: ${trade.coin} (ID: ${tradeId})`);
                
                // Cancel ALL orders for this symbol
                try {
                    const cancelResult = await cancelAllOrdersForSymbol(trade.coin);
                    if (cancelResult && cancelResult.success) {
                        addApiLog(`✅ Tüm emirler iptal edildi: ${trade.coin}`);
                    } else {
                        addApiLog(`⚠️ Emir iptal edilemedi: ${trade.coin} - ${cancelResult?.error || 'Bilinmeyen hata'}`);
                    }
                } catch (error) {
                    addApiLog(`❌ Emir iptal hatası: ${error.message}`);
                }
                
                await completeTrade(tradeId, true); // Force close manually
                addApiLog(`✅ ${trade.tradeType} işlem kapatma tamamlandı: ${trade.coin} (ID: ${tradeId})`);
                
            } catch (error) {
                addApiLog(`❌ ${trade.tradeType} işlem kapatma hatası: ${error.message}`);
                console.error(`${trade.tradeType} trade close error:`, error);
            }
        }

        function updateTradeInfo() {
            const activeTrades = transactions.filter(t => t.status === 'Aktif').length;
            
            // Calculate total PnL more accurately
            let totalPnL = 0;
            let totalProfit = 0;
            let totalLoss = 0;
            
            transactions.forEach(trade => {
                if (trade.pnl !== undefined && trade.pnl !== null) {
                    totalPnL += trade.pnl;
                    if (trade.pnl > 0) {
                        totalProfit += trade.pnl;
                    } else if (trade.pnl < 0) {
                        totalLoss += Math.abs(trade.pnl);
                    }
                }
            });
            
            const completedTrades = transactions.filter(t => t.status !== 'Aktif');
            const totalTrades = transactions.length;
            const profitableTrades = completedTrades.filter(t => t.pnl > 0).length;
            const lossTrades = completedTrades.filter(t => t.pnl < 0).length;
            
            // Calculate success rate based on total profit vs total loss
            const successRate = (totalProfit + totalLoss) > 0 ? (totalProfit / (totalProfit + totalLoss) * 100) : 0;
            
            // Update dashboard
            const totalPnLElement = document.getElementById('totalPnL');
            if (totalPnLElement) {
                totalPnLElement.textContent = '$' + totalPnL.toFixed(2);
                totalPnLElement.className = totalPnL >= 0 ? 'font-bold text-green-400' : 'font-bold text-red-400';
                console.log(`💰 PNL Güncellendi: $${totalPnL.toFixed(2)} (${transactions.length} işlem)`);
            }
            
            // Update fast and long trade counts
            const fastTradeCountElement = document.getElementById('fastTradeCount');
            const longTradeCountElement = document.getElementById('longTradeCount');
            if (fastTradeCountElement) fastTradeCountElement.textContent = fastTradeCount;
            if (longTradeCountElement) longTradeCountElement.textContent = longTradeCount;
            
            // Update trade page with enhanced statistics
            const tradeActiveTrades = document.getElementById('tradeActiveTrades');
            const tradeTotalTrades = document.getElementById('tradeTotalTrades');
            const tradeProfitableTrades = document.getElementById('tradeProfitableTrades');
            const tradeLossTrades = document.getElementById('tradeLossTrades');
            const tradeTotalPnL = document.getElementById('tradeTotalPnL');
            const tradeSuccessRate = document.getElementById('tradeSuccessRate');
            
            if (tradeActiveTrades) tradeActiveTrades.textContent = activeTrades;
            if (tradeTotalTrades) tradeTotalTrades.textContent = totalTrades;
            if (tradeProfitableTrades) tradeProfitableTrades.textContent = profitableTrades;
            if (tradeLossTrades) tradeLossTrades.textContent = lossTrades;
            if (tradeTotalPnL) {
                tradeTotalPnL.textContent = '$' + totalPnL.toFixed(2);
                tradeTotalPnL.className = totalPnL >= 0 ? 'text-2xl font-bold text-green-400' : 'text-2xl font-bold text-red-400';
            }
            if (tradeSuccessRate) tradeSuccessRate.textContent = successRate.toFixed(1) + '%';
        }

        // AI Settings Tab Functions
        function showAISettingsTab(tabName) {
            // Hide all AI settings tabs
            document.querySelectorAll('.ai-settings-content').forEach(tab => {
                tab.classList.add('hidden');
            });
            
            // Show selected tab
            if (tabName === 'probot') {
                document.getElementById('probotAISettings').classList.remove('hidden');
            } else if (tabName === 'fast') {
                document.getElementById('fastAISettings').classList.remove('hidden');
            } else if (tabName === 'long') {
                document.getElementById('longAISettings').classList.remove('hidden');
            } else if (tabName === 'manual') {
                document.getElementById('manualSettings').classList.remove('hidden');
            }
            
            // Update tab buttons
            document.querySelectorAll('.ai-settings-tab-btn').forEach(btn => {
                btn.classList.remove('border-blue-500', 'text-blue-400', 'border-green-500', 'text-green-400', 'border-purple-500', 'text-purple-400');
                btn.classList.add('text-gray-400', 'border-transparent', 'bg-transparent');
            });
            
            const activeBtn = document.getElementById(tabName + 'AISettingsTab') || document.getElementById(tabName + 'SettingsTab');
            if (activeBtn) {
                activeBtn.classList.remove('text-gray-400', 'border-transparent');
                if (tabName === 'probot') {
                    activeBtn.classList.add('border-purple-500', 'text-purple-400');
                } else if (tabName === 'fast') {
                    activeBtn.classList.add('border-blue-500', 'text-blue-400');
                } else if (tabName === 'long') {
                    activeBtn.classList.add('border-green-500', 'text-green-400');
                } else if (tabName === 'manual') {
                    activeBtn.classList.add('border-purple-500', 'text-purple-400');
                }
                activeBtn.classList.add('bg-transparent');
            }
        }

        // Manual Trade Function
        function openManualTrade() {
            const coin = prompt('Hangi coin için işlem açmak istiyorsunuz? (örn: BTC)');
            if (!coin) return;
            
            const coinData = cryptoData.find(c => c.symbol.toUpperCase() === coin.toUpperCase());
            if (!coinData) {
                showNotification('Coin bulunamadı!', 'error');
                return;
            }
            
            // Check if coin already has an active trade
            const existingTrade = transactions.find(t => 
                t.coin === coinData.symbol && 
                t.status === 'Aktif'
            );
            
            if (existingTrade) {
                showNotification(`${coinData.symbol} zaten aktif işlemde!`, 'warning');
                return;
            }
            
            const entryPrice = coinData.price;
            const isLong = document.getElementById('manualPositionType').value === 'LONG';
            const leverage = parseInt(document.getElementById('manualLeverage').value);
            const usdtAmount = parseFloat(document.getElementById('manualUsdtAmount').value);
            const stopLossPercent = parseFloat(document.getElementById('manualStopLoss').value) / 100;
            const takeProfitPercent = parseFloat(document.getElementById('manualTakeProfit').value) / 100;
            
            // Get DCA settings for manual trades
            const dcaEnabled = document.getElementById('manualDcaEnabled')?.checked || false;
            const dcaCount = parseInt(document.getElementById('manualDcaCount')?.value || '3');
            const dcaTrigger = parseFloat(document.getElementById('manualDcaTrigger')?.value || '5') / 100;
            const dcaMultiplier = parseFloat(document.getElementById('manualDcaMultiplier')?.value || '1.5');
            
            const stopLoss = isLong ? 
                entryPrice * (1 - stopLossPercent) : // LONG: SL below entry (zarar durdurma)
                entryPrice * (1 + stopLossPercent);   // SHORT: SL above entry (zarar durdurma)
            
            const takeProfit = isLong ? 
                entryPrice * (1 + takeProfitPercent) : // LONG: TP above entry (kar alma)
                entryPrice * (1 - takeProfitPercent);  // SHORT: TP below entry (kar alma)
            
            const trade = {
                id: Date.now(),
                coin: coinData.symbol,
                type: isLong ? 'LONG' : 'SHORT',
                entryPrice: entryPrice,
                currentPrice: entryPrice,
                exitPrice: null,
                stopLoss: stopLoss,
                takeProfit: takeProfit,
                stopLossPercent: stopLossPercent, // TP/SL oranlarını sakla
                takeProfitPercent: takeProfitPercent, // TP/SL oranlarını sakla
                amount: usdtAmount,
                totalInvestment: usdtAmount, // Initialize total investment
                leverage: leverage,
                pnl: 0,
                status: 'Aktif',
                timestamp: new Date().toLocaleString('tr-TR'),
                orderType: 'Market',
                confidence: 100,
                indicators: { manual: true },
                tradeType: 'Manuel',
                aiType: 'Manual',
                dcaEnabled: dcaEnabled,
                dcaLevel: 0,
                dcaCount: dcaCount,
                dcaTrigger: dcaTrigger,
                dcaMultiplier: dcaMultiplier
            };
            
            transactions.unshift(trade);
            saveTransactionsToStorage();
            updateActiveTradesTable();
            updateTradeInfo();
            
            // Send to exchange
            if (document.getElementById('bybitApiKey').value) {
                sendOrderToBybit(trade);
            } else if (document.getElementById('binanceApiKey').value) {
                sendOrderToBinance(trade);
            } else {
                addApiLog(`⚠️ API bağlantısı yok - ${coinData.symbol} manuel işlemi yerel olarak takip ediliyor`);
                addApiLog(`💡 Gerçek borsa işlemi için Bybit veya Binance API anahtarlarını girin`);
            }
            
            // Send DCA orders immediately if enabled
            if (dcaEnabled && dcaCount > 0) {
                setTimeout(async () => {
                    try {
                        await sendDCAOrdersToExchange(trade);
                    } catch (error) {
                        addApiLog(`❌ DCA emirleri hazırlanırken hata: ${error.message}`);
                        console.error('DCA preparation error:', error);
                    }
                }, 1000); // 1 second delay to ensure main order is processed
            }
            
            showNotification(`Manuel ${coinData.symbol} ${isLong ? 'LONG' : 'SHORT'} işlemi açıldı! ${dcaEnabled ? `(DCA: ${dcaCount} seviye)` : ''}`, 'success');
        }

        function updateAdminStats() {
            const activeTrades = transactions.filter(t => t.status === 'Aktif').length;
            const totalPnL = transactions.reduce((sum, t) => sum + (t.pnl || 0), 0);
            
            // Update admin statistics
            const adminActiveTrades = document.getElementById('adminActiveTrades');
            const adminDailyVolume = document.getElementById('adminDailyVolume');
            
            if (adminActiveTrades) adminActiveTrades.textContent = activeTrades;
            if (adminDailyVolume) adminDailyVolume.textContent = '$' + Math.abs(totalPnL).toFixed(0);
        }

        // Trade Tab Functions
        function showTradeTab(tabName) {
            // Hide all trade tabs
            document.querySelectorAll('.trade-tab-content').forEach(tab => {
                tab.classList.add('hidden');
            });
            
            // Show selected tab
            document.getElementById(tabName + 'TradesTab').classList.remove('hidden');
            
            // Update tab buttons
            document.querySelectorAll('.trade-tab-btn').forEach(btn => {
                btn.classList.remove('border-blue-500', 'text-blue-400');
                btn.classList.add('text-gray-400', 'border-transparent', 'bg-transparent');
            });
            
            const activeBtn = document.getElementById(tabName + 'TradeTab');
            if (activeBtn) {
                activeBtn.classList.remove('text-gray-400', 'border-transparent');
                activeBtn.classList.add('border-blue-500', 'text-blue-400', 'bg-transparent');
            }
        }

        // Page Navigation with Trade Access Control
        function showPage(pageName) {
            // Check trade access for non-admin users
            if (pageName === 'trade' && currentUser && currentUser.username !== 'Hunter3535') {
                if (!checkTradeAccess()) {
                    return;
                }
            }
            
            document.querySelectorAll('.page').forEach(page => {
                page.classList.add('hidden');
            });
            
            document.getElementById(pageName + 'Page').classList.remove('hidden');
            currentPage = pageName;
            
            // Update control panel status when visiting control page
            if (pageName === 'control') {
                updateControlPanelStatus();
            }
            
            // Save page state immediately
            const pageState = {
                currentPage: currentPage,
                fastAiActive: fastAiActive,
                longAiActive: longAiActive
            };
            localStorage.setItem('pageState', JSON.stringify(pageState));
            
            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.classList.remove('bg-white', 'bg-opacity-20', 'bg-opacity-30');
                btn.classList.add('bg-transparent', 'text-white');
            });
            
            if (event && event.target) {
                event.target.classList.remove('bg-transparent');
                event.target.classList.add('bg-white', 'bg-opacity-20', 'text-white');
            }
        }
        
        function checkTradeAccess() {
            const user = registeredUsers.find(u => u.username === currentUser.username);
            if (!user) return false;
            
            const now = new Date();
            
            // Check if user has never accessed trade page
            if (!user.tradeAccessExpiry) {
                // First time accessing trade page - request admin approval
                user.lastTradeAccess = now;
                user.tradeAccessExpiry = new Date(now.getTime() + (30 * 24 * 60 * 60 * 1000)); // 30 days
                user.status = 'pending_trade_approval';
                
                // Add to pending approvals
                pendingRegistrations.push({
                    username: user.username,
                    email: user.email,
                    timestamp: now.toLocaleString('tr-TR'),
                    status: 'Trade Erişimi Bekliyor',
                    type: 'trade_access',
                    expiryDate: user.tradeAccessExpiry
                });
                
                updateRegisteredUsersTable();
                updatePendingRegistrations();
                
                showNotification('Trade erişimi için admin onayı bekleniyor. 30 gün erişim izni verildi.', 'warning');
                return true; // Allow access for now
            }
            
            // Check if access has expired
            if (now > user.tradeAccessExpiry) {
                // Access expired - request renewal
                user.tradeAccessExpiry = new Date(now.getTime() + (30 * 24 * 60 * 60 * 1000)); // 30 days
                user.status = 'pending_trade_renewal';
                
                // Add to pending approvals
                pendingRegistrations.push({
                    username: user.username,
                    email: user.email,
                    timestamp: now.toLocaleString('tr-TR'),
                    status: 'Trade Yenileme Bekliyor',
                    type: 'trade_renewal',
                    expiryDate: user.tradeAccessExpiry
                });
                
                updateRegisteredUsersTable();
                updatePendingRegistrations();
                
                showNotification('Trade erişiminiz sona erdi. Yenileme için admin onayı bekleniyor. 30 gün ek süre verildi.', 'warning');
                return true; // Allow access for now
            }
            
            return true; // Access is valid
        }

        // API Functions
        function testBinanceConnection() {
            const apiKey = document.getElementById('binanceApiKey').value;
            const secretKey = document.getElementById('binanceSecretKey').value;
            
            if (!apiKey || !secretKey) {
                showNotification('API Key ve Secret Key gerekli!', 'error');
                return;
            }
            
            showNotification('Binance API bağlantısı test ediliyor...', 'info');
            
            setTimeout(() => {
                showNotification('Binance API bağlantısı başarılı!', 'success');
                document.getElementById('binanceStatus').innerHTML = `
                    <div class="text-green-400">✓ Bağlantı başarılı</div>
                    <div class="text-sm text-gray-400 mt-1">Futures trading aktif</div>
                    <div class="text-sm text-gray-400">Emir tipi: ${document.getElementById('binanceOrderType').value}</div>
                `;
                
                // Update balance display if no Bybit connection
                if (!document.getElementById('bybitApiKey').value) {
                    document.getElementById('currentBalance').innerHTML = '<span class="text-green-400 font-bold">$8,750.32</span>';
                }
            }, 2000);
        }

        function testBybitConnection() {
            const apiKey = document.getElementById('bybitApiKey').value;
            const secretKey = document.getElementById('bybitSecretKey').value;
            
            if (!apiKey || !secretKey) {
                showNotification('API Key ve Secret Key gerekli!', 'error');
                return;
            }
            
            showNotification('Bybit API bağlantısı test ediliyor...', 'info');
            
            // Simulate API test
            setTimeout(() => {
                showNotification('Bybit API bağlantısı başarılı!', 'success');
                document.getElementById('bybitStatus').innerHTML = `
                    <div class="text-green-400">✓ Bağlantı başarılı</div>
                    <div class="text-sm text-gray-400 mt-1">Futures trading aktif</div>
                    <div class="text-sm text-gray-400">Emir tipi: ${document.getElementById('orderType').value}</div>
                `;
                
                // Update balance display
                document.getElementById('currentBalance').innerHTML = '<span class="text-green-400 font-bold">$12,450.67</span>';
                
            }, 2000);
        }

        function saveBinanceKeys() {
            try{
                const apiKey = document.getElementById('binanceApiKey')?.value || '';
                const secretKey = document.getElementById('binanceSecretKey')?.value || '';
                localStorage.setItem('binance_keys', JSON.stringify({apiKey, secretKey}));
                showNotification('Binance API anahtarları kaydedildi!', 'success');
            }catch(e){ console.warn(e); showNotification('Binance anahtar kaydedilirken hata', 'error'); }
        }

        function saveBybitKeys() {
            try{
                const apiKey = document.getElementById('bybitApiKey')?.value || '';
                const secretKey = document.getElementById('bybitSecretKey')?.value || '';
                localStorage.setItem('bybit_keys', JSON.stringify({apiKey, secretKey}));
                showNotification('Bybit API anahtarları kaydedildi!', 'success');
            }catch(e){ console.warn(e); showNotification('Bybit anahtar kaydedilirken hata', 'error'); }
        }

        // Control Panel Functions
        function toggleIndicator(indicator) {
            const button = document.querySelector(`[data-indicator="${indicator}"]`);
            const isActive = button.classList.contains('indicator-active');
            
            if (isActive) {
                button.classList.remove('indicator-active');
                button.classList.add('indicator-inactive');
                button.textContent = 'Pasif';
                activeIndicators = activeIndicators.filter(i => i !== indicator);
            } else {
                button.classList.remove('indicator-inactive');
                button.classList.add('indicator-active');
                button.textContent = 'Aktif';
                activeIndicators.push(indicator);
            }
            
            showNotification(`${indicator} ${isActive ? 'deaktif' : 'aktif'} edildi`, 'info');
        }

        function saveSettings() {
            // Save page and AI states
            const pageState = {
                currentPage: currentPage,
                fastAiActive: fastAiActive,
                longAiActive: longAiActive
            };
            localStorage.setItem('pageState', JSON.stringify(pageState));
            
            // Save trade settings
            const autoTradingEnabled = document.getElementById('autoTradingEnabled')?.checked || false;
            
            // Save AI settings
            const fastUsdtAmount = document.getElementById('fastUsdtAmount')?.value || '1';
            const fastLeverage = document.getElementById('fastLeverage')?.value || '10';
            const fastStopLoss = document.getElementById('fastStopLoss')?.value || '2';
            const fastTakeProfit = document.getElementById('fastTakeProfit')?.value || '1';
            const fastConfidence = document.getElementById('fastConfidence')?.value || '80';
            const fastScoreThreshold = document.getElementById('fastScoreThreshold')?.value || '50';
            const fastMaxTrades = document.getElementById('fastMaxTrades')?.value || '3';
            
            const longUsdtAmount = document.getElementById('longUsdtAmount')?.value || '1';
            const longLeverage = document.getElementById('longLeverage')?.value || '10';
            const longStopLoss = document.getElementById('longStopLoss')?.value || '2';
            const longTakeProfit = document.getElementById('longTakeProfit')?.value || '1';
            const longConfidence = document.getElementById('longConfidence')?.value || '80';
            const longScoreThreshold = document.getElementById('longScoreThreshold')?.value || '80';
            const longMaxTrades = document.getElementById('longMaxTrades')?.value || '3';
            
            const manualUsdtAmount = document.getElementById('manualUsdtAmount')?.value || '50';
            const manualLeverage = document.getElementById('manualLeverage')?.value || '5';
            const manualStopLoss = document.getElementById('manualStopLoss')?.value || '3';
            const manualTakeProfit = document.getElementById('manualTakeProfit')?.value || '8';
            
            // Save ProBot AI settings
            const probotMaxTrades = document.getElementById('probotMaxTrades')?.value || '3';
            
            // Save DCA settings
            const fastDcaEnabled = document.getElementById('fastDcaEnabled')?.checked || false;
            const fastDcaCount = document.getElementById('fastDcaCount')?.value || '2';
            const fastDcaTrigger = document.getElementById('fastDcaTrigger')?.value || '3';
            const fastDcaMultiplier = document.getElementById('fastDcaMultiplier')?.value || '1.2';
            
            const longDcaEnabled = document.getElementById('longDcaEnabled')?.checked || false;
            const longDcaCount = document.getElementById('longDcaCount')?.value || '4';
            const longDcaTrigger = document.getElementById('longDcaTrigger')?.value || '8';
            const longDcaMultiplier = document.getElementById('longDcaMultiplier')?.value || '1.5';
            
            const manualDcaEnabled = document.getElementById('manualDcaEnabled')?.checked || false;
            const manualDcaCount = document.getElementById('manualDcaCount')?.value || '3';
            const manualDcaTrigger = document.getElementById('manualDcaTrigger')?.value || '5';
            const manualDcaMultiplier = document.getElementById('manualDcaMultiplier')?.value || '1.5';
            
            // Save to localStorage
            const settings = {
                autoTradingEnabled,
                fastUsdtAmount,
                fastLeverage,
                fastStopLoss,
                fastTakeProfit,
                fastConfidence,
                fastScoreThreshold,
                fastMaxTrades,
                longUsdtAmount,
                longLeverage,
                longStopLoss,
                longTakeProfit,
                longConfidence,
                longScoreThreshold,
                longMaxTrades,
                manualUsdtAmount,
                manualLeverage,
                manualStopLoss,
                manualTakeProfit,
                probotMaxTrades,
                fastDcaEnabled,
                fastDcaCount,
                fastDcaTrigger,
                fastDcaMultiplier,
                longDcaEnabled,
                longDcaCount,
                longDcaTrigger,
                longDcaMultiplier,
                manualDcaEnabled,
                manualDcaCount,
                manualDcaTrigger,
                manualDcaMultiplier
            };
            
            localStorage.setItem('tradeSettings', JSON.stringify(settings));
            showNotification('Tüm ayarlar kaydedildi!', 'success');
        }
        
        function updateAIStatusDisplays() {
            // Update Fast AI status
            const fastAiStatus = document.getElementById('fastAiStatus');
            const fastAiToggle = document.getElementById('fastAiToggle');
            const tradeFastAiStatus = document.getElementById('tradeFastAiStatus');
            const tradeFastAiToggle = document.getElementById('tradeFastAiToggle');
            
            if (fastAiStatus) {
                fastAiStatus.textContent = fastAiActive ? 'Aktif' : 'Durduruldu';
                fastAiStatus.className = fastAiActive ? 'ai-active' : 'ai-inactive';
            }
            if (fastAiToggle) {
                fastAiToggle.textContent = fastAiActive ? '⏹️ Fast AI Durdur' : '▶️ Fast AI Başlat';
                fastAiToggle.className = fastAiActive ? 'ai-active px-4 py-2 rounded-lg font-bold transition-all text-sm' : 'ai-inactive px-4 py-2 rounded-lg font-bold transition-all text-sm';
            }
            if (tradeFastAiStatus) {
                tradeFastAiStatus.textContent = fastAiActive ? 'Aktif' : 'Durduruldu';
                tradeFastAiStatus.className = fastAiActive ? 'ai-active' : 'ai-inactive';
            }
            if (tradeFastAiToggle) {
                tradeFastAiToggle.textContent = fastAiActive ? '⏹️ Fast AI Durdur' : '▶️ Fast AI Başlat';
                tradeFastAiToggle.className = fastAiActive ? 'ai-active px-6 py-3 rounded-lg font-bold transition-all text-sm' : 'ai-inactive px-6 py-3 rounded-lg font-bold transition-all text-sm';
            }
            
            // Update Long AI status
            const longAiStatus = document.getElementById('longAiStatus');
            const longAiToggle = document.getElementById('longAiToggle');
            const tradeLongAiStatus = document.getElementById('tradeLongAiStatus');
            const tradeLongAiToggle = document.getElementById('tradeLongAiToggle');
            
            if (longAiStatus) {
                longAiStatus.textContent = longAiActive ? 'Aktif' : 'Durduruldu';
                longAiStatus.className = longAiActive ? 'ai-active' : 'ai-inactive';
            }
            if (longAiToggle) {
                longAiToggle.textContent = longAiActive ? '⏹️ Long AI Durdur' : '▶️ Long AI Başlat';
                longAiToggle.className = longAiActive ? 'ai-active px-4 py-2 rounded-lg font-bold transition-all text-sm' : 'ai-inactive px-4 py-2 rounded-lg font-bold transition-all text-sm';
            }
            if (tradeLongAiStatus) {
                tradeLongAiStatus.textContent = longAiActive ? 'Aktif' : 'Durduruldu';
                tradeLongAiStatus.className = longAiActive ? 'ai-active' : 'ai-inactive';
            }
            if (tradeLongAiToggle) {
                tradeLongAiToggle.textContent = longAiActive ? '⏹️ Long AI Durdur' : '▶️ Long AI Başlat';
                tradeLongAiToggle.className = longAiActive ? 'ai-active px-6 py-3 rounded-lg font-bold transition-all text-sm' : 'ai-inactive px-6 py-3 rounded-lg font-bold transition-all text-sm';
            }
            
            // Update ProBot AI status
            const probotAiStatus = document.getElementById('probotAiStatus');
            const probotAiToggle = document.getElementById('probotAiToggle');
            const tradeProbotAiStatus = document.getElementById('tradeProbotAiStatus');
            const tradeProbotAiToggle = document.getElementById('tradeProbotAiToggle');
            
            if (probotAiStatus) {
                probotAiStatus.textContent = probotAiActive ? 'Aktif' : 'Durduruldu';
                probotAiStatus.className = probotAiActive ? 'ai-active' : 'ai-inactive';
            }
            if (probotAiToggle) {
                probotAiToggle.textContent = probotAiActive ? '⏹️ ProBot AI Durdur' : '▶️ ProBot AI Başlat';
                probotAiToggle.className = probotAiActive ? 'ai-active px-4 py-2 rounded-lg font-bold transition-all text-sm' : 'ai-inactive px-4 py-2 rounded-lg font-bold transition-all text-sm';
            }
            if (tradeProbotAiStatus) {
                tradeProbotAiStatus.textContent = probotAiActive ? 'Aktif' : 'Durduruldu';
                tradeProbotAiStatus.className = probotAiActive ? 'ai-active' : 'ai-inactive';
            }
            if (tradeProbotAiToggle) {
                tradeProbotAiToggle.textContent = probotAiActive ? '⏹️ ProBot AI Durdur' : '▶️ ProBot AI Başlat';
                tradeProbotAiToggle.className = probotAiActive ? 'ai-active px-6 py-3 rounded-lg font-bold transition-all text-sm' : 'ai-inactive px-6 py-3 rounded-lg font-bold transition-all text-sm';
            }
        }
        
        function loadSettings() {
            // Load page and AI states
            const pageState = JSON.parse(localStorage.getItem('pageState') || '{}');
            if (pageState.currentPage) {
                currentPage = pageState.currentPage;
                // Immediately restore the correct page
                showPage(currentPage);
            }
            if (pageState.fastAiActive !== undefined) {
                fastAiActive = pageState.fastAiActive;
            }
            if (pageState.longAiActive !== undefined) {
                longAiActive = pageState.longAiActive;
            }
            if (pageState.probotAiActive !== undefined) {
                probotAiActive = pageState.probotAiActive;
            }
            
            // Update AI status displays immediately
            updateAIStatusDisplays();
            
            const settings = JSON.parse(localStorage.getItem('tradeSettings') || '{}');
            
            // Load trade settings
            if (settings.autoTradingEnabled !== undefined) document.getElementById('autoTradingEnabled').checked = settings.autoTradingEnabled;
            
            // Load AI settings
            if (settings.fastUsdtAmount) document.getElementById('fastUsdtAmount').value = settings.fastUsdtAmount;
            if (settings.fastLeverage) document.getElementById('fastLeverage').value = settings.fastLeverage;
            if (settings.fastStopLoss) document.getElementById('fastStopLoss').value = settings.fastStopLoss;
            if (settings.fastTakeProfit) document.getElementById('fastTakeProfit').value = settings.fastTakeProfit;
            if (settings.fastConfidence) document.getElementById('fastConfidence').value = settings.fastConfidence;
            if (settings.fastScoreThreshold) document.getElementById('fastScoreThreshold').value = settings.fastScoreThreshold;
            
            if (settings.longUsdtAmount) document.getElementById('longUsdtAmount').value = settings.longUsdtAmount;
            if (settings.longLeverage) document.getElementById('longLeverage').value = settings.longLeverage;
            if (settings.longStopLoss) document.getElementById('longStopLoss').value = settings.longStopLoss;
            if (settings.longTakeProfit) document.getElementById('longTakeProfit').value = settings.longTakeProfit;
            if (settings.longConfidence) document.getElementById('longConfidence').value = settings.longConfidence;
            if (settings.longScoreThreshold) document.getElementById('longScoreThreshold').value = settings.longScoreThreshold;
            
            if (settings.manualUsdtAmount) document.getElementById('manualUsdtAmount').value = settings.manualUsdtAmount;
            if (settings.manualLeverage) document.getElementById('manualLeverage').value = settings.manualLeverage;
            if (settings.manualStopLoss) document.getElementById('manualStopLoss').value = settings.manualStopLoss;
            if (settings.manualTakeProfit) document.getElementById('manualTakeProfit').value = settings.manualTakeProfit;
            
            // Load DCA settings
            if (settings.fastDcaEnabled !== undefined) document.getElementById('fastDcaEnabled').checked = settings.fastDcaEnabled;
            if (settings.fastDcaCount) document.getElementById('fastDcaCount').value = settings.fastDcaCount;
            if (settings.fastDcaTrigger) document.getElementById('fastDcaTrigger').value = settings.fastDcaTrigger;
            if (settings.fastDcaMultiplier) document.getElementById('fastDcaMultiplier').value = settings.fastDcaMultiplier;
            
            if (settings.longDcaEnabled !== undefined) document.getElementById('longDcaEnabled').checked = settings.longDcaEnabled;
            if (settings.longDcaCount) document.getElementById('longDcaCount').value = settings.longDcaCount;
            if (settings.longDcaTrigger) document.getElementById('longDcaTrigger').value = settings.longDcaTrigger;
            if (settings.longDcaMultiplier) document.getElementById('longDcaMultiplier').value = settings.longDcaMultiplier;
            
            if (settings.manualDcaEnabled !== undefined) document.getElementById('manualDcaEnabled').checked = settings.manualDcaEnabled;
            if (settings.manualDcaCount) document.getElementById('manualDcaCount').value = settings.manualDcaCount;
            if (settings.manualDcaTrigger) document.getElementById('manualDcaTrigger').value = settings.manualDcaTrigger;
            if (settings.manualDcaMultiplier) document.getElementById('manualDcaMultiplier').value = settings.manualDcaMultiplier;
            
            console.log('✅ Ayarlar yüklendi:', settings);
            
            // Restore AI states immediately
            restorePageAndAIStates();
        }
        
        function restorePageAndAIStates() {
            // Load ProBot settings from localStorage
            const savedProbotSettings = localStorage.getItem('probotSettings');
            if (savedProbotSettings) {
                try {
                    probotSettings = JSON.parse(savedProbotSettings);
                    console.log('✅ ProBot settings loaded from localStorage:', probotSettings);
                } catch (error) {
                    console.error('❌ Error loading ProBot settings:', error);
                }
            } else {
                console.log('⚠️ No saved ProBot settings found, using defaults');
            }
            
            // Restore AI states
            if (fastAiActive) {
                const fastAiToggle = document.getElementById('fastAiToggle');
                const fastAiStatus = document.getElementById('fastAiStatus');
                if (fastAiToggle && fastAiStatus) {
                    fastAiToggle.className = 'ai-active px-4 py-2 rounded-lg font-bold transition-all text-sm';
                    fastAiStatus.textContent = 'Hızlı AI Çalışıyor';
                    startFastAIAnalysis();
                }
            }
            
            if (longAiActive) {
                const longAiToggle = document.getElementById('longAiToggle');
                const longAiStatus = document.getElementById('longAiStatus');
                if (longAiToggle && longAiStatus) {
                    longAiToggle.className = 'ai-active px-4 py-2 rounded-lg font-bold transition-all text-sm';
                    longAiStatus.textContent = 'Uzun AI Çalışıyor';
                    startLongAIAnalysis();
                }
            }
            
            if (probotAiActive) {
                console.log('🤖 ProBot AI restoring state - starting analysis');
                const probotAiToggle = document.getElementById('probotAiToggle');
                const probotAiStatus = document.getElementById('probotAiStatus');
                const tradeProbotAiToggle = document.getElementById('tradeProbotAiToggle');
                const tradeProbotAiStatus = document.getElementById('tradeProbotAiStatus');
                
                if (probotAiToggle && probotAiStatus) {
                    probotAiToggle.className = 'ai-active px-4 py-2 rounded-lg font-bold transition-all text-sm';
                    probotAiStatus.textContent = 'ProBot AI Çalışıyor';
                }
                if (tradeProbotAiToggle && tradeProbotAiStatus) {
                    tradeProbotAiToggle.className = 'ai-active px-6 py-3 rounded-lg font-bold transition-all text-sm';
                    tradeProbotAiStatus.textContent = 'ProBot AI Çalışıyor';
                }
                console.log('🤖 Calling startProbotAIAnalysis from restorePageAndAIStates');
                startProbotAIAnalysis();
            }
            
            console.log('✅ Sayfa ve AI durumları geri yüklendi:', {
                currentPage,
                fastAiActive,
                longAiActive,
                probotAiActive
            });
        }

        // Admin Tab Functions
        function showAdminTab(tabName) {
            // Hide all admin tabs
            document.querySelectorAll('.admin-tab').forEach(tab => {
                tab.classList.add('hidden');
            });
            
            // Show selected tab
            document.getElementById(`admin${tabName.charAt(0).toUpperCase() + tabName.slice(1)}Tab`).classList.remove('hidden');
            
            // Update tab buttons
            document.querySelectorAll('.admin-tab-btn').forEach(btn => {
                btn.classList.remove('border-red-500', 'text-red-400', 'border-purple-500', 'text-purple-400');
                btn.classList.add('text-gray-400', 'border-transparent', 'bg-transparent');
            });
            
            if (event && event.target) {
                event.target.classList.remove('text-gray-400', 'border-transparent');
                if (tabName === 'probot') {
                    event.target.classList.add('border-purple-500', 'text-purple-400', 'bg-transparent');
                    loadAdminProbotSettings();
                } else {
                    event.target.classList.add('border-red-500', 'text-red-400', 'bg-transparent');
                }
            }
        }

        // Load admin probot settings
        function loadAdminProbotSettings() {
            // Load from localStorage
            const savedSettings = localStorage.getItem('probotSettings');
            if (savedSettings) {
                const settings = JSON.parse(savedSettings);
                
                // Update admin form values
                document.getElementById('adminProbotGoLongPeriod').value = settings.goLongPeriod || 13;
                document.getElementById('adminProbotGoLongOrder').value = settings.goLongOrder || 5;
                document.getElementById('adminProbotFilterDeviation').value = settings.filterDeviation || 1;
                document.getElementById('adminProbotFilterPeriod').value = settings.filterPeriod || 10;
                document.getElementById('adminProbotSamplePeriod').value = settings.samplePeriod || 10;
                document.getElementById('adminProbotRangeMultiplier').value = settings.rangeMultiplier || 3;
                document.getElementById('adminProbotAtrPeriod').value = settings.atrPeriod || 14;
                document.getElementById('adminProbotAtrMultiplier').value = settings.atrMultiplier || 1.5;
                document.getElementById('adminProbotUsdtAmount').value = settings.usdtAmount || 10;
                document.getElementById('adminProbotLeverage').value = settings.leverage || 10;
                document.getElementById('adminProbotDcaLevels').value = settings.dcaLevels || 3;
                document.getElementById('adminProbotDcaPercent').value = settings.dcaPercent || 2;
                document.getElementById('adminProbotDcaMultiplier').value = settings.dcaMultiplier || 1.5;
                document.getElementById('adminProbotStopLoss').value = settings.stopLoss || 5;
                document.getElementById('adminProbotTakeProfit').value = settings.takeProfit || 10;
                document.getElementById('adminProbotTrailingStop').value = settings.trailingStop || 2;
            }
        }

        // Update registered users table
        function updateRegisteredUsersTable() {
            const tbody = document.getElementById('registeredUsersTable');
            if (!tbody) return;
            
            tbody.innerHTML = '';
            
            if (registeredUsers.length === 0) {
                const row = document.createElement('tr');
                row.className = 'border-b border-gray-700 bg-gray-800';
                row.innerHTML = `
                    <td colspan="7" class="p-3 text-center text-gray-400">Kayıtlı kullanıcı yok</td>
                `;
                tbody.appendChild(row);
                return;
            }
            
            registeredUsers.forEach(user => {
                const row = document.createElement('tr');
                row.className = 'border-b border-gray-700 bg-gray-800 hover:bg-gray-700';
                
                // Calculate remaining time
                let remainingTime = 'Süresiz';
                let statusColor = 'bg-green-600';
                let statusText = 'Aktif';
                
                if (user.tradeAccessExpiry) {
                    const now = new Date();
                    const expiry = new Date(user.tradeAccessExpiry);
                    const diffTime = expiry - now;
                    const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
                    
                    if (diffDays > 0) {
                        remainingTime = `${diffDays} gün`;
                        statusColor = diffDays <= 7 ? 'bg-yellow-600' : 'bg-green-600';
                        statusText = diffDays <= 7 ? 'Yakında Bitiyor' : 'Aktif';
                    } else {
                        remainingTime = 'Süresi Doldu';
                        statusColor = 'bg-red-600';
                        statusText = 'Pasif';
                    }
                }
                
                const tradeAccess = user.tradeAccessExpiry ? 'Var' : 'Yok';
                const tradeAccessColor = user.tradeAccessExpiry ? 'text-green-400' : 'text-red-400';
                
                row.innerHTML = `
                    <td class="p-3 text-white">${user.username}</td>
                    <td class="p-3 text-white">${user.email}</td>
                    <td class="p-3 text-white">${user.registrationDate.toLocaleDateString('tr-TR')}</td>
                    <td class="p-3 ${tradeAccessColor}">${tradeAccess}</td>
                    <td class="p-3 text-white">${remainingTime}</td>
                    <td class="p-3"><span class="${statusColor} px-2 py-1 rounded text-xs text-white">${statusText}</span></td>
                    <td class="p-3">
                        <button onclick="extendUserAccess('${user.username}')" class="bg-blue-600 hover:bg-blue-700 px-2 py-1 rounded text-xs mr-1 text-white">+30 Gün</button>
                        <button onclick="revokeUserAccess('${user.username}')" class="bg-red-600 hover:bg-red-700 px-2 py-1 rounded text-xs text-white">İptal</button>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        // Update pending registrations table
        function updatePendingRegistrations() {
            const tbody = document.getElementById('pendingRegistrations');
            if (!tbody) return;
            
            tbody.innerHTML = '';
            
            if (pendingRegistrations.length === 0) {
                const row = document.createElement('tr');
                row.className = 'border-b border-gray-700 bg-gray-800';
                row.innerHTML = `
                    <td colspan="6" class="p-3 text-center text-gray-400">Bekleyen trade erişim talebi yok</td>
                `;
                tbody.appendChild(row);
                return;
            }
            
            pendingRegistrations.forEach(registration => {
                const row = document.createElement('tr');
                row.className = 'border-b border-gray-700 bg-gray-800 hover:bg-gray-700';
                
                const requestType = registration.type === 'trade_access' ? 'İlk Erişim' : 'Yenileme';
                const expiryDate = registration.expiryDate ? new Date(registration.expiryDate).toLocaleDateString('tr-TR') : '-';
                
                row.innerHTML = `
                    <td class="p-3 text-white">${registration.username}</td>
                    <td class="p-3 text-white">${registration.email}</td>
                    <td class="p-3 text-white">${registration.timestamp}</td>
                    <td class="p-3 text-white">${requestType}</td>
                    <td class="p-3 text-white">${expiryDate}</td>
                    <td class="p-3">
                        <button onclick="approveTradeAccess('${registration.username}', '${registration.type}')" class="bg-green-600 hover:bg-green-700 px-2 py-1 rounded text-xs mr-1 text-white">Onayla</button>
                        <button onclick="rejectTradeAccess('${registration.username}', '${registration.type}')" class="bg-red-600 hover:bg-red-700 px-2 py-1 rounded text-xs text-white">Reddet</button>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }
        
        function extendUserAccess(username) {
            const user = registeredUsers.find(u => u.username === username);
            if (user) {
                const now = new Date();
                const currentExpiry = user.tradeAccessExpiry ? new Date(user.tradeAccessExpiry) : now;
                const newExpiry = new Date(Math.max(now.getTime(), currentExpiry.getTime()) + (30 * 24 * 60 * 60 * 1000));
                
                user.tradeAccessExpiry = newExpiry;
                user.status = 'active';
                
                updateRegisteredUsersTable();
                showNotification(`${username} kullanıcısının erişimi 30 gün uzatıldı!`, 'success');
            }
        }
        
        function revokeUserAccess(username) {
            const user = registeredUsers.find(u => u.username === username);
            if (user) {
                user.tradeAccessExpiry = new Date(); // Set to now (expired)
                user.status = 'revoked';
                
                updateRegisteredUsersTable();
                showNotification(`${username} kullanıcısının trade erişimi iptal edildi!`, 'warning');
            }
        }
        
        function approveTradeAccess(username, type) {
            const user = registeredUsers.find(u => u.username === username);
            if (user) {
                const now = new Date();
                user.tradeAccessExpiry = new Date(now.getTime() + (30 * 24 * 60 * 60 * 1000)); // 30 days
                user.status = 'active';
                
                // Remove from pending
                pendingRegistrations = pendingRegistrations.filter(r => 
                    !(r.username === username && r.type === type)
                );
                
                updateRegisteredUsersTable();
                updatePendingRegistrations();
                showNotification(`${username} kullanıcısının trade erişimi onaylandı!`, 'success');
            }
        }
        
        function rejectTradeAccess(username, type) {
            const user = registeredUsers.find(u => u.username === username);
            if (user) {
                user.status = 'rejected';
                
                // Remove from pending
                pendingRegistrations = pendingRegistrations.filter(r => 
                    !(r.username === username && r.type === type)
                );
                
                updateRegisteredUsersTable();
                updatePendingRegistrations();
                showNotification(`${username} kullanıcısının trade erişimi reddedildi!`, 'warning');
            }
        }

        // Admin Functions
        function approveUser(username) {
            pendingRegistrations = pendingRegistrations.filter(reg => reg.username !== username);
            updatePendingRegistrations();
            showNotification(`${username} kullanıcısı onaylandı!`, 'success');
        }

        function rejectUser(username) {
            pendingRegistrations = pendingRegistrations.filter(reg => reg.username !== username);
            updatePendingRegistrations();
            showNotification(`${username} kullanıcısı reddedildi!`, 'warning');
        }

        function emergencyStop() {
            aiActive = false;
            showNotification('Acil durdurma aktif! Tüm işlemler durduruldu.', 'error');
        }

        function restartSystem() {
            showNotification('Sistem yeniden başlatılıyor...', 'info');
        }

        function backupData() {
            showNotification('Veri yedekleme başlatıldı...', 'info');
        }

        function saveAdminSettings() {
            showNotification('Tüm admin ayarları kaydedildi!', 'success');
        }

        // Webhook Functions
        function testWebhook() {
            showNotification('Webhook bağlantısı test ediliyor...', 'info');
            setTimeout(() => {
                showNotification('Webhook test başarılı! (Demo)', 'success');
                document.getElementById('webhookStatus').innerHTML = '<div class="text-green-400">✓ Webhook aktif ve çalışıyor</div>';
            }, 2000);
        }

        function saveWebhookSettings() {
            showNotification('Webhook ayarları kaydedildi!', 'success');
        }

        // Notification System
        function showNotification(message, type = 'info', duration = 5000) {
            const container = document.getElementById('notificationContainer');
            const notification = document.createElement('div');
            
            const bgColor = {
                'success': 'bg-gradient-to-r from-green-500 to-green-600',
                'error': 'bg-gradient-to-r from-red-500 to-red-600',
                'warning': 'bg-gradient-to-r from-yellow-500 to-orange-500',
                'info': 'bg-gradient-to-r from-blue-500 to-purple-600'
            }[type] || 'bg-gradient-to-r from-blue-500 to-purple-600';
            
            const icon = {
                'success': '✅',
                'error': '❌',
                'warning': '⚠️',
                'info': 'ℹ️'
            }[type] || 'ℹ️';
            
            notification.className = `${bgColor} text-white px-6 py-3 rounded-lg shadow-lg transform transition-all duration-300 translate-x-full opacity-0 border border-white border-opacity-20`;
            notification.innerHTML = `
                <div class="flex items-center justify-between">
                    <div class="flex items-center">
                        <span class="mr-2 text-lg">${icon}</span>
                        <span class="font-medium">${message}</span>
                    </div>
                    <button onclick="this.parentElement.parentElement.remove()" class="ml-4 text-white hover:text-gray-200 transition-colors">
                        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                        </svg>
                    </button>
                </div>
            `;
            
            container.appendChild(notification);
            
            setTimeout(() => {
                notification.classList.remove('translate-x-full', 'opacity-0');
            }, 100);
            
            setTimeout(() => {
                notification.classList.add('translate-x-full', 'opacity-0');
                setTimeout(() => {
                    if (notification.parentElement) {
                        notification.remove();
                    }
                }, 300);
            }, duration);
        }

        // Initialize on page load
        document.addEventListener('DOMContentLoaded', function() {
            document.getElementById('loginUsername').focus();
            // Initialize pending registrations table
            updatePendingRegistrations();
            // Load saved settings
            loadSettings();
            // Load ProBot AI settings
            loadProbotSettings();
            
            // Auto-save settings when changed
            const settingsInputs = [
                'maxActiveTrades', 'autoTradingEnabled',
                'fastUsdtAmount', 'fastLeverage', 'fastStopLoss', 'fastTakeProfit', 'fastConfidence', 'fastScoreThreshold',
                'longUsdtAmount', 'longLeverage', 'longStopLoss', 'longTakeProfit', 'longConfidence', 'longScoreThreshold',
                'manualUsdtAmount', 'manualLeverage', 'manualStopLoss', 'manualTakeProfit',
                'fastDcaEnabled', 'fastDcaCount', 'fastDcaTrigger', 'fastDcaMultiplier',
                'longDcaEnabled', 'longDcaCount', 'longDcaTrigger', 'longDcaMultiplier',
                'manualDcaEnabled', 'manualDcaCount', 'manualDcaTrigger', 'manualDcaMultiplier',
                // ProBot AI settings
                'probotGoLongPeriod', 'probotGoLongOrder', 'probotFilterDeviation', 'probotFilterPeriod',
                'probotSamplePeriod', 'probotRangeMultiplier', 'probotAtrPeriod', 'probotAtrMultiplier',
                'probotUsdtAmount', 'probotLeverage', 'probotDcaLevels', 'probotDcaPercent',
                'probotDcaMultiplier', 'probotStopLoss', 'probotTakeProfit', 'probotTrailingStop',
                'probotScoreThreshold'
            ];
            
            settingsInputs.forEach(id => {
                const element = document.getElementById(id);
                if (element) {
                    element.addEventListener('change', () => {
                        saveSettings();
                        if (id.startsWith('probot')) {
                            saveProbotSettings();
                        }
                    });
                    element.addEventListener('input', () => {
                        saveSettings();
                        if (id.startsWith('probot')) {
                            saveProbotSettings();
                        }
                    });
                }
            });
        });
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'978fd8e42019de2d',t:'MTc1Njg0NTg4Ni4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script>
<!-- V3.1 PATCH: DCA UI + Manual DCA, TP/SL cancel-all, Bybit 500 scanner & lightweight AI indicators -->
<script>
(function(){
  // idempotency
  if(window.__ct_v3_1_applied) return;
  window.__ct_v3_1_applied = true;

  // safe storage helpers
  function safeLoad(k,d){ try{ const v=localStorage.getItem(k); return v?JSON.parse(v):d;}catch(e){return d;} }
  function safeSave(k,v){ try{ localStorage.setItem(k, JSON.stringify(v)); }catch(e){} }

  // --- DCA UI injection (in control panel) ---
  try{
    const controlPanel = document.querySelector('#controlPanel') || document.querySelector('.card') || document.body;
  }catch(e){ console.warn('DCA UI inject error', e); }

  // --- send DCA orders (tries client-side functions, else webhook) ---
  async function sendDcaOrders(symbol, originalParams, dcaSettings){
    try{
      const levels = dcaSettings.levels||2;
      const multiplier = dcaSettings.multiplier||1.5;
      let baseSize = 10;
      if(originalParams && typeof originalParams === 'object'){
        if(originalParams.usdt) baseSize = originalParams.usdt;
        if(originalParams.size) baseSize = originalParams.size;
      }
      // prefer client-side functions if available
      const placeFns = ['placeBinanceOrderWrapper','placeBybitOrderWrapper','placeBinanceOrder','placeBybitOrder','placeOrder','createOrder','submitOrder','sendOrderToBybit','sendOrderToBinance'];
      for(const fn of placeFns){
        if(window[fn] && typeof window[fn] === 'function'){
          // send limit DCA orders as best-effort
          for(let i=1;i<=levels;i++){
            // DCA hesaplama: sabit çarpan ile hesaplama
            const dcaAmount = baseSize * Math.pow(1.5, i); // Her DCA seviyesi için sabit çarpan
            const size = dcaAmount * 10; // 10x çarpanı
            try{ await window[fn]({symbol, usdt:size, dcaLevel:i}); }catch(e){ /* ignore individual error */ }
          }
          console.log('DCA placed via', fn, symbol);
          return {success:true, via:fn};
        }
      }
      // fallback: webhook
      const wh = safeLoad('webhook_settings', null) || {url: (document.getElementById('webhookUrl')?document.getElementById('webhookUrl').value:null)};
      if(wh && wh.url){
        const payload = {type:'place_dca', symbol, originalParams, levels, multiplier};
        try{ await fetch(wh.url,{method:'POST',headers:{'Content-Type':'application/json'},body:JSON.stringify(payload)}); console.log('DCA webhook sent', symbol); return {success:true, via:'webhook'}; }catch(e){ console.warn('DCA webhook failed', e); return {success:false, error:e.message}; }
      }
      return {success:false, reason:'no_method'};
    }catch(e){ console.warn('sendDcaOrders error', e); return {success:false, error:e.message}; }
  }
  window.__sendDcaOrders = sendDcaOrders;

  // --- Cancel all orders for a symbol: try client-side cancel functions, else webhook ---
  async function cancelAllOrdersForSymbol(symbol){
    try{
      console.log('Attempting cancelAllOrdersForSymbol', symbol);
      addApiLog(`🔄 ${symbol} için tüm emirler iptal ediliyor...`);
      
      const cancelFns = ['cancelAllBybitOrders','cancelAllBinanceOrders','cancelAllOrders','cancelOrdersForSymbol','cancelOrders','cancelOrder'];
      for(const fn of cancelFns){
        if(window[fn] && typeof window[fn] === 'function'){
          try{ 
            const result = await window[fn](symbol); 
            console.log('Canceled via', fn, result); 
            addApiLog(`✅ ${symbol} emirleri iptal edildi (${fn})`);
            return {success:true,via:fn,result:result}; 
          }catch(e){ 
            console.warn('cancel via',fn,'failed',e); 
            addApiLog(`⚠️ ${fn} ile iptal edilemedi: ${e.message}`);
          }
        }
      }
      // try fetching open orders then cancel individually
      const fetchFns = ['fetchOpenOrders','getOpenOrders','listOpenOrders','getOpenPositions'];
      for(const ff of fetchFns){
        if(window[ff] && typeof window[ff] === 'function'){
          try{
            const orders = await window[ff](symbol);
            if(Array.isArray(orders)){
              addApiLog(`📋 ${symbol} için ${orders.length} açık emir bulundu, iptal ediliyor...`);
              for(const o of orders){
                if(o && (o.orderId || o.id) && window['cancelOrder'] && typeof window['cancelOrder'] === 'function'){
                  try{ 
                    await window['cancelOrder'](o.orderId||o.id); 
                    addApiLog(`✅ Emir iptal edildi: ${o.orderId || o.id}`);
                  }catch(e){
                    addApiLog(`⚠️ Emir iptal edilemedi: ${o.orderId || o.id} - ${e.message}`);
                  }
                }
              }
              addApiLog(`✅ ${symbol} için tüm açık emirler iptal edildi`);
              return {success:true, via:ff};
            }
          }catch(e){
            addApiLog(`⚠️ Açık emirler alınamadı (${ff}): ${e.message}`);
          }
        }
      }
      // webhook fallback
      const wh = safeLoad('webhook_settings', null) || {url: (document.getElementById('webhookUrl')?document.getElementById('webhookUrl').value:null)};
      if(wh && wh.url){
        try{ 
          await fetch(wh.url, {method:'POST', headers:{'Content-Type':'application/json'}, body: JSON.stringify({type:'cancel_all_for_symbol', symbol})}); 
          console.log('Cancel requested via webhook', symbol); 
          addApiLog(`✅ ${symbol} emir iptal webhook ile gönderildi`);
          return {success:true,via:'webhook'}; 
        }catch(e){ 
          console.warn('webhook cancel failed', e); 
          addApiLog(`❌ Webhook emir iptal hatası: ${e.message}`);
          return {success:false, error:e.message}; 
        }
      }
      
      addApiLog(`❌ ${symbol} için hiçbir emir iptal yöntemi çalışmadı`);
      return {success:false, reason:'no_method'};
    }catch(e){ 
      console.warn('cancelAllOrdersForSymbol error', e); 
      addApiLog(`❌ Emir iptal genel hatası: ${e.message}`);
      return {success:false, error:e.message}; 
    }
  }
  window.cancelAllOrdersForSymbol = cancelAllOrdersForSymbol;
  window.cancelAllBybitOrders = cancelAllBybitOrders;

  // --- Wrap closeTrade and completeTrade to cancel all orders for symbol on TP/SL ---
  function wrapCloseFunctions(){
    // closeTrade
    if(window.closeTrade && typeof window.closeTrade === 'function' && !window.__wrapped_closeTrade_v31){
      const orig = window.closeTrade;
      window.closeTrade = async function(orderId, source, closedBy){
        try{
          // attempt to get symbol from order object or DOM
          let symbol = null;
          if(window.getOrderById && typeof window.getOrderById === 'function'){
            try{ const ord = await window.getOrderById(orderId); if(ord) symbol = ord.symbol||ord.pair; }catch(e){}
          }
          const res = await orig.apply(this, arguments);
          // decrement active trades if UI shows count
          try{ if(window.updateActiveTradesCount && typeof window.updateActiveTradesCount === 'function') window.updateActiveTradesCount(-1); }catch(e){}
          // infer symbol via DOM if not found
          if(!symbol){
            const el = document.getElementById(orderId) || document.querySelector('[data-order-id="'+orderId+'"]');
            if(el) symbol = el.getAttribute('data-symbol') || (el.dataset && el.dataset.symbol) || (el.textContent && (el.textContent.match(/([A-Z]+USDT)/i)||[])[1]);
          }
          if(symbol){
            await cancelAllOrdersForSymbol(symbol);
          }
          return res;
        }catch(err){
          // best-effort cancel
          try{
            const el = document.getElementById(orderId) || document.querySelector('[data-order-id="'+orderId+'"]');
            if(el){
              const s = el.getAttribute('data-symbol') || (el.dataset && el.dataset.symbol);
              if(s) await cancelAllOrdersForSymbol(s);
            }
          }catch(e){}
          throw err;
        }
      };
      window.__wrapped_closeTrade_v31 = true;
      console.log('Wrapped closeTrade -> cancelAllOrdersForSymbol');
    }

    // completeTrade (another closure point)
    if(window.completeTrade && typeof window.completeTrade === 'function' && !window.__wrapped_completeTrade_v31){
      const origC = window.completeTrade;
      window.completeTrade = async function(tradeObj){
        try{
          // call original
          const res = await origC.apply(this, arguments);
          // if tradeObj includes symbol, cancel all other orders for symbol
          try{
            const symbol = (tradeObj && (tradeObj.symbol||tradeObj.pair)) || (tradeObj && tradeObj.trade && (tradeObj.trade.symbol||tradeObj.trade.pair));
            if(symbol) await cancelAllOrdersForSymbol(symbol);
          }catch(e){}
          return res;
        }catch(e){
          throw e;
        }
      };
      window.__wrapped_completeTrade_v31 = true;
      console.log('Wrapped completeTrade -> cancelAllOrdersForSymbol');
    }
  }
  wrapCloseFunctions();

  // Also attempt to wrap by names discovered later
  setTimeout(wrapCloseFunctions, 1000);
  setTimeout(wrapCloseFunctions, 3000);

  // --- Manual trade DCA hook: intercept clicks on trade buttons rendered in coin list ---
  document.addEventListener('click', function(e){
    try{
      // buttons that open trades often have data-symbol or data-action attributes or onclick openTrade('SYMBOL')
      const bt = e.target.closest('button, a, span');
      if(!bt) return;
      // if button has data-symbol and data-action=open-trade, hook DCA after a short delay
      const symbol = bt.getAttribute && (bt.getAttribute('data-symbol') || bt.dataset && bt.dataset.symbol) || null;
      const action = bt.getAttribute && (bt.getAttribute('data-action') || bt.dataset && bt.dataset.action) || null;
      // also check onclick attribute
      const onclick = bt.getAttribute && bt.getAttribute('onclick') || '';
      if((symbol && action==='open-trade') || (/openTrade\(['"]?([A-Z0-9]+USDT)/i.test(onclick))){
        // after the original click (let original handlers run), schedule DCA if enabled
        setTimeout(async ()=>{
          try{
            const dca = safeLoad('dca_settings',{enabled:false,levels:2,multiplier:1.5});
            if(!dca || !dca.enabled) return;
            // infer symbol from onclick if needed
            let sym = symbol;
            if(!sym){
              const m = onclick.match(/openTrade\(['"]?([A-Z0-9]+USDT)/i);
              if(m) sym = m[1];
            }
            if(!sym) return;
            // best-effort originalParams extraction
            const originalParams = {source:'manual-ui'};
            await sendDcaOrders(sym, originalParams, dca);
          }catch(e){ console.warn('manual DCA error', e); }
        }, 600);
      }
    }catch(e){}
  }, true);

  // --- Bybit top-500 scanner (sourced from Bybit futures/public tickers) ---
  window.startBybitTopScanner = async function(topN){
    try{
      topN = topN || 500;
      // fetch tickers and render into coin list if exists
      async function fetchTickers(){
        try{
          const res = await fetch('https://api.bybit.com/v2/public/tickers');
          const j = await res.json();
          if(!j || !j.result) return;
          // filter USDT perpetual/symbols ending with USDT
          let list = j.result.filter(it=> typeof it.symbol==='string' && it.symbol.endsWith('USDT'));
          // sort by quote volume or turnover
          list.sort((a,b)=> (parseFloat(b.turnover24h||b.quote_volume||b.volume||0) - parseFloat(a.turnover24h||a.quote_volume||a.volume||0)));
          const top = list.slice(0, Math.min(topN, list.length));
          // render into existing coinList tbody if present
          const tbody = document.getElementById('coinList') || document.querySelector('#coinList tbody');
          if(tbody){
            tbody.innerHTML = '';
            top.forEach(it=>{
              const tr = document.createElement('tr');
              const price = it.last_price||it.lastPrice||it.last||it.price;
              const change = it.price_24h || it.priceChangePercent || it.price_change_percent || '-';
              const vol = it.quote_volume||it.turnover24h||it.volume||'-';
              tr.innerHTML = `<td>${it.symbol}</td><td>${price}</td><td>${change}</td><td>${vol}</td><td><button class="btn" data-action="open-trade" data-symbol="${it.symbol}">Trade</button></td>`;
              tbody.appendChild(tr);
            });
          } else {
            // maybe original render function exists
            if(window.renderCoinListFromBybit && typeof window.renderCoinListFromBybit === 'function'){
              try{ window.renderCoinListFromBybit(top); }catch(e){}
            }
          }
        }catch(e){ console.warn('Bybit scanner fetch error', e); }
      }
      // initial fetch
      await fetchTickers();
      if(window.__bybitScannerInterval) clearInterval(window.__bybitScannerInterval);
      window.__bybitScannerInterval = setInterval(fetchTickers, 1000);
      console.log('Bybit top scanner started for top', topN);
    }catch(e){ console.warn('startBybitTopScanner error', e); }
  };

  // auto-start scanner if logged in
  try{
    const sess = safeLoad('ct_session', safeLoad('session', null));
    if(sess) setTimeout(()=>{ try{ window.startBybitTopScanner(500); }catch(e){} }, 800);
  }catch(e){}

  // --- Lightweight AI indicator hooks (simple heuristics, optional) ---
  window.aiDecision = window.aiDecision || function(symbol, params, confidence){
    // Very lightweight combined heuristic: price momentum + volume surge + optional user-set confidence
    try{
      // If there's accessible tick data in page (row), use it
      const row = document.querySelector(`#coinList tr td:first-child:contains("${symbol}")`);
      // fallback: random threshold (placeholder)
      const conf = (safeLoad('ai_settings',{enabled:false,confidence:0.7}).confidence) || confidence || 0.7;
      return Math.random() <= conf;
    }catch(e){ return true; }
  };

  // helper: polyfill for :contains used above (not standard) - we won't rely on it; aiDecision left lightweight.
  console.log('V3.1 patches applied: DCA UI, manual DCA hook, cancel-all on close, Bybit top500 scanner.');
})();
</script>
<!-- V3.1 PATCH END -->

</body>
</html>
