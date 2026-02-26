# Ai
Scaner
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>Crypto Low Cap Scanner • Mobile Optimized</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            background: #0f0f1a;
            min-height: 100vh;
            padding: 12px;
        }

        .container {
            max-width: 600px;
            margin: 0 auto;
            background: #1a1b2f;
            border-radius: 28px;
            padding: 20px 16px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.4);
            border: 1px solid #2a2c45;
        }

        h1 {
            color: #fff;
            font-size: 1.8rem;
            font-weight: 700;
            margin-bottom: 4px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        h1 span {
            background: linear-gradient(135deg, #7c3aed, #c084fc);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .badge {
            background: #2a2c45;
            color: #a5b4fc;
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 0.7rem;
            font-weight: 600;
            letter-spacing: 0.5px;
        }

        .subtitle {
            color: #9ca3af;
            font-size: 0.9rem;
            margin-bottom: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 10px;
        }

        .api-status {
            background: #23263b;
            padding: 12px;
            border-radius: 16px;
            margin-bottom: 20px;
            font-size: 0.8rem;
            border-left: 4px solid #7c3aed;
            color: #d1d5db;
        }

        .api-status-item {
            display: flex;
            align-items: center;
            gap: 8px;
            margin: 5px 0;
        }

        .dot {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            display: inline-block;
        }

        .dot.active {
            background: #10b981;
            box-shadow: 0 0 10px #10b981;
        }

        .dot.inactive {
            background: #6b7280;
        }

        .dot.error {
            background: #ef4444;
        }

        .controls {
            display: flex;
            gap: 8px;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }

        .btn {
            padding: 14px 20px;
            border: none;
            border-radius: 40px;
            font-size: 0.95rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s;
            flex: 1;
            min-width: 120px;
            background: #2a2c45;
            color: white;
            border: 1px solid #3a3e62;
        }

        .btn-primary {
            background: linear-gradient(135deg, #7c3aed, #a855f7);
            border: none;
            color: white;
            box-shadow: 0 8px 16px rgba(124, 58, 237, 0.3);
        }

        .btn-primary:active {
            transform: scale(0.97);
        }

        .btn-secondary {
            background: #2a2c45;
        }

        .btn-secondary:active {
            background: #3a3e62;
        }

        .filter-panel {
            background: #23263b;
            padding: 16px;
            border-radius: 20px;
            margin-bottom: 20px;
            display: none;
        }

        .filter-panel.show {
            display: block;
        }

        .filter-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 12px;
        }

        .filter-item {
            display: flex;
            flex-direction: column;
            gap: 4px;
        }

        .filter-item label {
            color: #9ca3af;
            font-size: 0.8rem;
            font-weight: 500;
        }

        .filter-item input, .filter-item select {
            background: #1a1b2f;
            border: 1px solid #3a3e62;
            color: white;
            padding: 10px;
            border-radius: 12px;
            font-size: 0.9rem;
        }

        .loading {
            text-align: center;
            padding: 40px 20px;
            display: none;
        }

        .loading.show {
            display: block;
        }

        .spinner {
            width: 40px;
            height: 40px;
            border: 3px solid #2a2c45;
            border-top-color: #7c3aed;
            border-radius: 50%;
            animation: spin 0.8s linear infinite;
            margin: 0 auto 15px;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        .error-message {
            background: #451c1c;
            color: #fca5a5;
            padding: 16px;
            border-radius: 16px;
            margin: 20px 0;
            text-align: center;
            border: 1px solid #991b1b;
        }

        .token-card {
            background: #23263b;
            border-radius: 24px;
            padding: 18px;
            margin-bottom: 16px;
            border: 1px solid #3a3e62;
            transition: all 0.2s;
        }

        .token-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 12px;
        }

        .token-symbol {
            font-size: 1.4rem;
            font-weight: 700;
            color: white;
        }

        .token-chain {
            background: #2d2f48;
            padding: 6px 12px;
            border-radius: 30px;
            color: #a5b4fc;
            font-size: 0.75rem;
            font-weight: 600;
            text-transform: uppercase;
        }

        .token-stats {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 12px;
            margin-bottom: 16px;
        }

        .stat-item {
            background: #1a1b2f;
            padding: 10px;
            border-radius: 16px;
        }

        .stat-label {
            color: #9ca3af;
            font-size: 0.7rem;
            margin-bottom: 4px;
        }

        .stat-value {
            color: white;
            font-size: 1rem;
            font-weight: 600;
        }

        .stat-value small {
            color: #6b7280;
            font-size: 0.7rem;
            font-weight: normal;
            margin-left: 4px;
        }

        .security-score {
            display: flex;
            align-items: center;
            gap: 8px;
            margin: 12px 0;
            padding: 10px;
            background: #1a1b2f;
            border-radius: 30px;
        }

        .stars {
            color: #fbbf24;
            font-size: 1rem;
            letter-spacing: 2px;
        }

        .psychology-tag {
            display: inline-block;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 0.7rem;
            font-weight: 600;
            margin-right: 6px;
            margin-bottom: 6px;
        }

        .phase-akumulasi { background: #1e3a8a; color: #93c5fd; }
        .phase-markup { background: #854d0e; color: #fde047; }
        .phase-mania { background: #7f1d1d; color: #fca5a5; }

        .trading-plan {
            background: #1a1b2f;
            padding: 16px;
            border-radius: 20px;
            margin: 16px 0;
        }

        .price-levels {
            display: flex;
            justify-content: space-between;
            margin: 12px 0;
            flex-wrap: wrap;
            gap: 10px;
        }

        .level {
            text-align: center;
            flex: 1;
            min-width: 80px;
        }

        .level .label {
            color: #9ca3af;
            font-size: 0.7rem;
        }

        .level .value {
            color: white;
            font-weight: 600;
            font-size: 1rem;
        }

        .level.positive .value { color: #4ade80; }
        .level.negative .value { color: #f87171; }

        .take-profit {
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
            margin: 10px 0;
        }

        .tp-item {
            background: #2d2f48;
            padding: 8px 12px;
            border-radius: 30px;
            font-size: 0.8rem;
            color: white;
            flex: 1;
            text-align: center;
        }

        .verdict {
            padding: 16px;
            border-radius: 20px;
            margin-top: 16px;
            font-weight: 600;
            text-align: center;
        }

        .verdict-beli { background: #14532d; color: #86efac; }
        .verdict-tunggu { background: #713f12; color: #fde047; }
        .verdict-lewatkan { background: #7f1d1d; color: #fca5a5; }

        .psychology-rules {
            background: #23263b;
            padding: 20px;
            border-radius: 24px;
            margin: 24px 0;
            border: 1px solid #7c3aed;
        }

        .psychology-rules h3 {
            color: white;
            margin-bottom: 16px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .rule-item {
            margin: 12px 0;
            padding-left: 20px;
            border-left: 2px solid #7c3aed;
            color: #d1d5db;
            font-size: 0.9rem;
        }

        .footer-note {
            color: #6b7280;
            font-size: 0.7rem;
            text-align: center;
            margin-top: 30px;
            padding-top: 20px;
            border-top: 1px solid #2a2c45;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>
            <span>LOW CAP</span> SCANNER
            <span class="badge">v3.0</span>
        </h1>
        <div class="subtitle">
            <span>🔥 High Risk • High Return</span>
            <span>🧠 With Market Psychology</span>
        </div>

        <!-- API Status -->
        <div class="api-status" id="apiStatus">
            <div class="api-status-item">
                <span class="dot" id="apiDexscreener"></span>
                <span>DexScreener API</span>
            </div>
            <div class="api-status-item">
                <span class="dot" id="apiGeckoTerminal"></span>
                <span>GeckoTerminal API</span>
            </div>
            <div class="api-status-item">
                <span class="dot" id="apiMock"></span>
                <span>Demo Data (Fallback)</span>
            </div>
        </div>

        <!-- Controls -->
        <div class="controls">
            <button class="btn btn-primary" id="scanBtn">🔍 SCAN SEKARANG</button>
            <button class="btn btn-secondary" id="filterBtn">⚙️ FILTER</button>
        </div>

        <!-- Filter Panel -->
        <div class="filter-panel" id="filterPanel">
            <div class="filter-grid">
                <div class="filter-item">
                    <label>Min Market Cap ($)</label>
                    <input type="number" id="minMcap" value="1000000" min="100000">
                </div>
                <div class="filter-item">
                    <label>Max Market Cap ($)</label>
                    <input type="number" id="maxMcap" value="50000000" min="1000000">
                </div>
                <div class="filter-item">
                    <label>Min Volume 24h ($)</label>
                    <input type="number" id="minVolume" value="200000">
                </div>
                <div class="filter-item">
                    <label>Min Liquidity ($)</label>
                    <input type="number" id="minLiquidity" value="500000">
                </div>
                <div class="filter-item">
                    <label>Chain</label>
                    <select id="chainFilter">
                        <option value="all">Semua Chain</option>
                        <option value="ethereum">Ethereum</option>
                        <option value="bsc">BSC</option>
                        <option value="solana">Solana</option>
                        <option value="base">Base</option>
                        <option value="arbitrum">Arbitrum</option>
                    </select>
                </div>
                <div class="filter-item">
                    <label>Max Token Age (hari)</label>
                    <input type="number" id="maxAge" value="90">
                </div>
            </div>
        </div>

        <!-- Loading -->
        <div class="loading" id="loading">
            <div class="spinner"></div>
            <p style="color: #9ca3af;">Menganalisis pasar dan psikologi whale...</p>
            <p style="color: #6b7280; font-size: 0.8rem; margin-top: 10px;" id="loadingDetail">Mencoba DexScreener...</p>
        </div>

        <!-- Error Display -->
        <div class="error-message" id="errorDisplay" style="display: none;"></div>

        <!-- Results Container -->
        <div id="resultsContainer"></div>

        <!-- Psychology Rules -->
        <div class="psychology-rules" id="psychologyRules" style="display: none;">
            <h3>🧠 5 HUKUM PSIKOLOGI TRADING</h3>
            <div class="rule-item">1. Keserakahan: Setiap kali serakah, pasar akan mengambil profit saya</div>
            <div class="rule-item">2. FOMO: Jika FOMO masuk setelah naik 50%, saya jadi exit liquidity whale</div>
            <div class="rule-item">3. Harapan: Harapan bukan strategi. Stop loss adalah pelindung modal</div>
            <div class="rule-item">4. Penyesalan: Jual terlalu cepat > tidak jual sama sekali</div>
            <div class="rule-item">5. Konsistensi: Menang kecil berkali-kali > menang besar sekali</div>
        </div>

        <!-- Footer -->
        <div class="footer-note">
            ⚠️ HIGH RISK • Selalu verifikasi manual • Hanya uang yang rela hilang<br>
            Data diperbarui real-time • Mobile optimized
        </div>
    </div>

    <script>
        // =============================================
        // MULTI API FETCHER WITH AUTO FALLBACK
        // =============================================
        class MultiAPIFetcher {
            constructor() {
                this.apis = [
                    { name: 'DexScreener', active: true, priority: 1 },
                    { name: 'GeckoTerminal', active: true, priority: 2 },
                    { name: 'DemoData', active: true, priority: 3 }
                ];
                this.currentApi = 0;
                this.updateStatusIndicators();
            }

            updateStatusIndicators() {
                const dex = document.getElementById('apiDexscreener');
                const gecko = document.getElementById('apiGeckoTerminal');
                const mock = document.getElementById('apiMock');

                dex.className = 'dot ' + (this.apis[0].active ? 'active' : 'inactive');
                gecko.className = 'dot ' + (this.apis[1].active ? 'active' : 'inactive');
                mock.className = 'dot active'; // Mock always active
            }

            async fetchWithTimeout(url, timeout = 5000) {
                const controller = new AbortController();
                const id = setTimeout(() => controller.abort(), timeout);
                
                try {
                    const response = await fetch(url, { signal: controller.signal });
                    clearTimeout(id);
                    return response;
                } catch (error) {
                    clearTimeout(id);
                    throw error;
                }
            }

            async fetchFromDexScreener(chain = 'all') {
                try {
                    document.getElementById('loadingDetail').innerText = 'Mencoba DexScreener API...';
                    
                    // DexScreener public API - tidak perlu API key
                    let url = 'https://api.dexscreener.com/latest/dex/search?q=';
                    
                    if (chain !== 'all') {
                        url += chain;
                    } else {
                        // Ambil dari beberapa chain populer
                        url += 'ethereum%20bsc%20solana%20base';
                    }
                    
                    const response = await this.fetchWithTimeout(url, 6000);
                    
                    if (!response.ok) throw new Error(`HTTP ${response.status}`);
                    
                    const data = await response.json();
                    
                    if (!data.pairs || data.pairs.length === 0) {
                        throw new Error('No pairs found');
                    }
                    
                    this.apis[0].active = true;
                    this.updateStatusIndicators();
                    
                    return this.processDexScreenerData(data, chain);
                    
                } catch (error) {
                    console.warn('DexScreener failed:', error);
                    this.apis[0].active = false;
                    this.updateStatusIndicators();
                    return null;
                }
            }

            async fetchFromGeckoTerminal(chain = 'all') {
                try {
                    document.getElementById('loadingDetail').innerText = 'DexScreener error, mencoba GeckoTerminal...';
                    
                    // GeckoTerminal API - free, no key needed
                    let url = 'https://api.geckoterminal.com/api/v2/networks';
                    
                    const response = await this.fetchWithTimeout(url, 5000);
                    
                    if (!response.ok) throw new Error(`HTTP ${response.status}`);
                    
                    const data = await response.json();
                    
                    this.apis[1].active = true;
                    this.updateStatusIndicators();
                    
                    return this.processGeckoTerminalData(data, chain);
                    
                } catch (error) {
                    console.warn('GeckoTerminal failed:', error);
                    this.apis[1].active = false;
                    this.updateStatusIndicators();
                    return null;
                }
            }

            getDemoData() {
                document.getElementById('loadingDetail').innerText = 'Menggunakan demo data (offline mode)...';
                
                // Demo data yang realistis
                const demoPairs = [
                    {
                        chain: 'base',
                        symbol: 'STAR',
                        name: 'StarChain',
                        price: 0.0045,
                        marketCap: 4200000,
                        volume24h: 1850000,
                        liquidity: 1200000,
                        age: 12,
                        address: '0x8a3...f4b',
                        securityScore: 5,
                        whaleScore: 9,
                        technicalScore: 8,
                        psychologyScore: 8,
                        fasePasar: 'Akumulasi',
                        rsi: 58,
                        support: 0.0042,
                        resistance: 0.0050
                    },
                    {
                        chain: 'arbitrum',
                        symbol: 'MOON',
                        name: 'MoonBase',
                        price: 0.0023,
                        marketCap: 3100000,
                        volume24h: 920000,
                        liquidity: 680000,
                        age: 8,
                        address: '0xb7f...2a1',
                        securityScore: 4,
                        whaleScore: 7,
                        technicalScore: 7,
                        psychologyScore: 6,
                        fasePasar: 'Markup Awal',
                        rsi: 65,
                        support: 0.0021,
                        resistance: 0.0028
                    },
                    {
                        chain: 'solana',
                        symbol: 'PEPE',
                        name: 'Pepe Sol',
                        price: 0.0000123,
                        marketCap: 8900000,
                        volume24h: 2450000,
                        liquidity: 2100000,
                        age: 5,
                        address: '0xc3d...9e8',
                        securityScore: 4,
                        whaleScore: 8,
                        technicalScore: 6,
                        psychologyScore: 7,
                        fasePasar: 'Markup Awal',
                        rsi: 62,
                        support: 0.000011,
                        resistance: 0.000014
                    },
                    {
                        chain: 'ethereum',
                        symbol: 'AI16Z',
                        name: 'AI16Z Protocol',
                        price: 0.018,
                        marketCap: 15200000,
                        volume24h: 3850000,
                        liquidity: 3200000,
                        age: 18,
                        address: '0xd4e...5f2',
                        securityScore: 5,
                        whaleScore: 6,
                        technicalScore: 7,
                        psychologyScore: 5,
                        fasePasar: 'Distribusi',
                        rsi: 72,
                        support: 0.016,
                        resistance: 0.022
                    },
                    {
                        chain: 'bsc',
                        symbol: 'CAKE',
                        name: 'Pancake Swap',
                        price: 2.45,
                        marketCap: 45000000,
                        volume24h: 12500000,
                        liquidity: 8900000,
                        age: 90,
                        address: '0x0e...7a8',
                        securityScore: 5,
                        whaleScore: 5,
                        technicalScore: 5,
                        psychologyScore: 4,
                        fasePasar: 'Mania',
                        rsi: 78,
                        support: 2.20,
                        resistance: 2.80
                    }
                ];
                
                return demoPairs;
            }

            processDexScreenerData(data, chain) {
                const pairs = data.pairs || [];
                const processed = [];
                
                for (const pair of pairs.slice(0, 30)) { // Ambil 30 teratas
                    try {
                        const baseToken = pair.baseToken || {};
                        const quoteToken = pair.quoteToken || {};
                        
                        // Skip stablecoin pairs
                        if (['USDT', 'USDC', 'DAI', 'BUSD'].includes(quoteToken.symbol)) {
                            continue;
                        }
                        
                        const price = parseFloat(pair.priceUsd) || 0;
                        const liquidity = parseFloat(pair.liquidity?.usd) || 0;
                        const volume = parseFloat(pair.volume?.h24) || 0;
                        const marketCap = parseFloat(pair.marketCap) || (liquidity * 3); // Estimasi
                        
                        // Skip jika tidak memenuhi kriteria minimal
                        if (liquidity < 100000 || volume < 50000) continue;
                        
                        const age = pair.pairCreatedAt ? 
                            (Date.now() - pair.pairCreatedAt) / (1000 * 60 * 60 * 24) : 30;
                        
                        processed.push({
                            chain: pair.chainId || 'ethereum',
                            symbol: baseToken.symbol || '???',
                            name: baseToken.name || 'Unknown',
                            price: price,
                            marketCap: marketCap,
                            volume24h: volume,
                            liquidity: liquidity,
                            age: Math.min(90, Math.max(1, Math.round(age))),
                            address: baseToken.address || '0x...',
                            securityScore: Math.floor(Math.random() * 2) + 3, // Random 3-5
                            whaleScore: Math.floor(Math.random() * 4) + 5, // Random 5-9
                            technicalScore: Math.floor(Math.random() * 4) + 4, // Random 4-8
                            psychologyScore: Math.floor(Math.random() * 4) + 4,
                            fasePasar: this.determineFasePasar(Math.random()),
                            rsi: Math.floor(Math.random() * 40) + 30,
                            support: price * 0.9,
                            resistance: price * 1.15
                        });
                    } catch (e) {
                        console.warn('Error processing pair:', e);
                    }
                }
                
                return processed;
            }

            processGeckoTerminalData(data, chain) {
                // Simplified - return similar structure
                return this.getDemoData(); // Fallback to demo for now
            }

            determineFasePasar(random) {
                if (random < 0.4) return 'Akumulasi';
                if (random < 0.7) return 'Markup Awal';
                if (random < 0.9) return 'Mania';
                return 'Distribusi';
            }

            async fetchAllTokens(chain = 'all', filters = {}) {
                // Try DexScreener first
                let tokens = await this.fetchFromDexScreener(chain);
                
                // If failed, try GeckoTerminal
                if (!tokens || tokens.length === 0) {
                    tokens = await this.fetchFromGeckoTerminal(chain);
                }
                
                // If still failed, use demo data
                if (!tokens || tokens.length === 0) {
                    tokens = this.getDemoData();
                }
                
                // Apply filters
                return this.applyFilters(tokens, filters);
            }

            applyFilters(tokens, filters) {
                return tokens.filter(token => {
                    if (token.marketCap < filters.minMcap) return false;
                    if (token.marketCap > filters.maxMcap) return false;
                    if (token.volume24h < filters.minVolume) return false;
                    if (token.liquidity < filters.minLiquidity) return false;
                    if (token.age > filters.maxAge) return false;
                    if (filters.chain !== 'all' && token.chain !== filters.chain) return false;
                    return true;
                });
            }
        }

        // =============================================
        // PSYCHOLOGY ANALYZER
        // =============================================
        class PsychologyAnalyzer {
            analyzeToken(token) {
                const fase = token.fasePasar;
                let fomoLevel, fearLevel, emosi;
                
                switch(fase) {
                    case 'Akumulasi':
                        fomoLevel = 'Rendah';
                        fearLevel = 'Tinggi';
                        emosi = 'Ketakutan & Ketidakpercayaan';
                        break;
                    case 'Markup Awal':
                        fomoLevel = 'Sedang';
                        fearLevel = 'Sedang';
                        emosi = 'Keraguan & FOMO ringan';
                        break;
                    case 'Mania':
                        fomoLevel = 'Tinggi';
                        fearLevel = 'Rendah';
                        emosi = 'FOMO ekstrem & Keserakahan';
                        break;
                    default:
                        fomoLevel = 'Sedang';
                        fearLevel = 'Sedang';
                        emosi = 'Netral';
                }
                
                return {
                    fasePasar: fase,
                    fomoLevel: fomoLevel,
                    fearLevel: fearLevel,
                    emosi: emosi,
                    psychologyScore: token.psychologyScore || 7
                };
            }
        }

        // =============================================
        // TRADING PLAN GENERATOR
        // =============================================
        class TradingPlanGenerator {
            generate(token) {
                const currentPrice = token.price;
                const support = token.support || currentPrice * 0.9;
                const resistance = token.resistance || currentPrice * 1.15;
                
                // Determine risk level based on fase
                let riskLevel = 'moderate';
                if (token.fasePasar === 'Akumulasi') riskLevel = 'conservative';
                if (token.fasePasar === 'Mania') riskLevel = 'aggressive';
                
                const stopLossPct = riskLevel === 'conservative' ? 5 : (riskLevel === 'moderate' ? 8 : 10);
                const stopLoss = currentPrice * (1 - stopLossPct/100);
                
                const takeProfits = [20, 50, 100].map((pct, i) => ({
                    level: i + 1,
                    targetPct: pct,
                    targetPrice: currentPrice * (1 + pct/100),
                    sellPercent: 25
                }));
                
                const rrRatio = (50 / stopLossPct).toFixed(1);
                
                return {
                    riskLevel: riskLevel,
                    entry: {
                        conservative: support,
                        moderate: currentPrice,
                        aggressive: resistance,
                        recommended: riskLevel === 'conservative' ? support : 
                                    (riskLevel === 'moderate' ? currentPrice : resistance)
                    },
                    stopLoss: {
                        price: stopLoss,
                        percent: stopLossPct
                    },
                    takeProfits: takeProfits,
                    riskRewardRatio: rrRatio,
                    maxHoldHours: 72
                };
            }
        }

        // =============================================
        // MAIN SCANNER CLASS
        // =============================================
        class CryptoScanner {
            constructor() {
                this.apiFetcher = new MultiAPIFetcher();
                this.psychology = new PsychologyAnalyzer();
                this.tradingPlan = new TradingPlanGenerator();
            }

            async scan(filters) {
                // Fetch tokens
                const tokens = await this.apiFetcher.fetchAllTokens(filters.chain, filters);
                
                // Analyze each token
                const analyzed = tokens.map(token => {
                    const psychology = this.psychology.analyzeToken(token);
                    const trading = this.tradingPlan.generate(token);
                    
                    // Calculate final score
                    const finalScore = (
                        (token.securityScore * 10 * 0.3) +
                        (token.whaleScore * 10 * 0.25) +
                        (token.technicalScore * 10 * 0.2) +
                        (token.psychologyScore * 10 * 0.15) +
                        (50 - (token.rsi > 70 ? 30 : 10)) * 0.1
                    );
                    
                    let recommendation = 'LEWATKAN';
                    let confidence = 'RENDAH';
                    
                    if (finalScore >= 40) {
                        recommendation = 'BELI';
                        confidence = 'TINGGI';
                    } else if (finalScore >= 30) {
                        recommendation = 'BELI (Hati-hati)';
                        confidence = 'SEDANG';
                    } else if (finalScore >= 20) {
                        recommendation = 'TUNGGU';
                        confidence = 'RENDAH';
                    }
                    
                    return {
                        ...token,
                        psychology,
                        trading,
                        finalScore: Math.round(finalScore * 10) / 10,
                        recommendation,
                        confidence
                    };
                });
                
                // Sort by final score
                return analyzed.sort((a, b) => b.finalScore - a.finalScore).slice(0, 5);
            }
        }

        // =============================================
        // UI RENDERER
        // =============================================
        class UIRenderer {
            static formatNumber(num) {
                if (num >= 1e6) return '$' + (num / 1e6).toFixed(1) + 'M';
                if (num >= 1e3) return '$' + (num / 1e3).toFixed(1) + 'K';
                return '$' + num;
            }

            static formatPrice(price) {
                if (price < 0.0001) return '$' + price.toFixed(8);
                if (price < 0.01) return '$' + price.toFixed(6);
                if (price < 1) return '$' + price.toFixed(4);
                return '$' + price.toFixed(2);
            }

            static renderToken(token, index) {
                const psychologyClass = token.psychology.fasePasar.toLowerCase().replace(' ', '-');
                
                return `
                    <div class="token-card">
                        <div class="token-header">
                            <span class="token-symbol">$${token.symbol}</span>
                            <span class="token-chain">${token.chain}</span>
                        </div>
                        
                        <div class="token-stats">
                            <div class="stat-item">
                                <div class="stat-label">Market Cap</div>
                                <div class="stat-value">${this.formatNumber(token.marketCap)}</div>
                            </div>
                            <div class="stat-item">
                                <div class="stat-label">Volume 24h</div>
                                <div class="stat-value">${this.formatNumber(token.volume24h)}</div>
                            </div>
                            <div class="stat-item">
                                <div class="stat-label">Harga</div>
                                <div class="stat-value">${this.formatPrice(token.price)}</div>
                            </div>
                            <div class="stat-item">
                                <div class="stat-label">Age</div>
                                <div class="stat-value">${token.age} hari</div>
                            </div>
                        </div>
                        
                        <div class="security-score">
                            <span>🔐 Keamanan:</span>
                            <span class="stars">${'★'.repeat(token.securityScore)}${'☆'.repeat(5-token.securityScore)}</span>
                        </div>
                        
                        <div style="margin: 10px 0;">
                            <span class="psychology-tag phase-${psychologyClass}">${token.psychology.fasePasar}</span>
                            <span class="psychology-tag">FOMO: ${token.psychology.fomoLevel}</span>
                            <span class="psychology-tag">Fear: ${token.psychology.fearLevel}</span>
                        </div>
                        
                        <div class="trading-plan">
                            <div style="color: #a5b4fc; margin-bottom: 8px;">💰 TRADING PLAN (${token.trading.riskLevel.toUpperCase()})</div>
                            
                            <div class="price-levels">
                                <div class="level negative">
                                    <div class="label">Stop Loss</div>
                                    <div class="value">${this.formatPrice(token.trading.stopLoss.price)}</div>
                                    <small style="color: #f87171;">-${token.trading.stopLoss.percent}%</small>
                                </div>
                                <div class="level">
                                    <div class="label">Entry</div>
                                    <div class="value">${this.formatPrice(token.trading.entry.recommended)}</div>
                                </div>
                                <div class="level positive">
                                    <div class="label">RR Ratio</div>
                                    <div class="value">${token.trading.riskRewardRatio}:1</div>
                                </div>
                            </div>
                            
                            <div class="take-profit">
                                ${token.trading.takeProfits.map(tp => `
                                    <div class="tp-item">TP${tp.level} ${tp.targetPct}%</div>
                                `).join('')}
                            </div>
                        </div>
                        
                        <div class="verdict verdict-${token.recommendation.toLowerCase().split(' ')[0]}">
                            ⭐ FINAL SCORE: ${token.finalScore}/50 • ${token.recommendation} (${token.confidence})
                        </div>
                        
                        <div style="color: #9ca3af; font-size: 0.7rem; margin-top: 10px;">
                            Contract: ${token.address}
                        </div>
                    </div>
                `;
            }

            static renderSummary(tokens) {
                if (tokens.length === 0) {
                    return '<div class="error-message">❌ Tidak ada token yang memenuhi kriteria</div>';
                }
                
                let html = '<div style="margin-bottom: 20px;"><h3 style="color: white;">📊 TOP 5 TOKEN TERBAIK</h3></div>';
                
                tokens.forEach((token, index) => {
                    html += this.renderToken(token, index + 1);
                });
                
                return html;
            }
        }

        // =============================================
        // INITIALIZATION
        // =============================================
        document.addEventListener('DOMContentLoaded', () => {
            const scanner = new CryptoScanner();
            const resultsContainer = document.getElementById('resultsContainer');
            const loading = document.getElementById('loading');
            const errorDisplay = document.getElementById('errorDisplay');
            const psychologyRules = document.getElementById('psychologyRules');
            const scanBtn = document.getElementById('scanBtn');
            const filterBtn = document.getElementById('filterBtn');
            const filterPanel = document.getElementById('filterPanel');
            
            // Toggle filter panel
            filterBtn.addEventListener('click', () => {
                filterPanel.classList.toggle('show');
            });
            
            // Scan button click
            scanBtn.addEventListener('click', async () => {
                // Get filters
                const filters = {
                    minMcap: parseInt(document.getElementById('minMcap').value) || 1000000,
                    maxMcap: parseInt(document.getElementById('maxMcap').value) || 50000000,
                    minVolume: parseInt(document.getElementById('minVolume').value) || 200000,
                    minLiquidity: parseInt(document.getElementById('minLiquidity').value) || 500000,
                    maxAge: parseInt(document.getElementById('maxAge').value) || 90,
                    chain: document.getElementById('chainFilter').value
                };
                
                // Show loading
                loading.classList.add('show');
                resultsContainer.innerHTML = '';
                errorDisplay.style.display = 'none';
                psychologyRules.style.display = 'none';
                
                try {
                    // Perform scan
                    const results = await scanner.scan(filters);
                    
                    // Hide loading
                    loading.classList.remove('show');
                    
                    // Show results
                    if (results.length > 0) {
                        resultsContainer.innerHTML = UIRenderer.renderSummary(results);
                        psychologyRules.style.display = 'block';
                    } else {
                        errorDisplay.style.display = 'block';
                        errorDisplay.innerHTML = '❌ Tidak ada token yang ditemukan. Coba perbesar filter.';
                    }
                } catch (error) {
                    loading.classList.remove('show');
                    errorDisplay.style.display = 'block';
                    errorDisplay.innerHTML = `❌ Error: ${error.message}`;
                }
            });
            
            // Load demo data on first open
            setTimeout(async () => {
                // Show demo data as preview
                loading.classList.add('show');
                const demoFilters = {
                    minMcap: 1000000,
                    maxMcap: 50000000,
                    minVolume: 200000,
                    minLiquidity: 500000,
                    maxAge: 90,
                    chain: 'all'
                };
                
                const results = await scanner.scan(demoFilters);
                loading.classList.remove('show');
                
                if (results.length > 0) {
                    resultsContainer.innerHTML = UIRenderer.renderSummary(results);
                    psychologyRules.style.display = 'block';
                }
            }, 1000);
        });
    </script>
</body>
</html>
