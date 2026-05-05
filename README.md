# -user-.github.io-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>RiskLens — Stock Risk Visualizer | Real-time Risk Intelligence</title>
    <!-- Google Fonts + modern reset -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,500;14..32,600;14..32,700;14..32,800&display=swap" rel="stylesheet">
    <!-- Font Awesome 6 (free icons) -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: radial-gradient(circle at 10% 20%, #f0f4ff, #e6edfa);
            color: #121826;
            line-height: 1.5;
            padding: 1.5rem 1rem;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
        }

        /* modern glassmorphism header */
        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 1rem;
            margin-bottom: 2.5rem;
            background: rgba(255, 255, 255, 0.6);
            backdrop-filter: blur(8px);
            padding: 0.8rem 2rem;
            border-radius: 3rem;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.02);
            border: 1px solid rgba(255,255,255,0.8);
        }

        .logo {
            font-size: 1.9rem;
            font-weight: 800;
            background: linear-gradient(135deg, #0f2b4d, #2c5282);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: -0.02em;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .logo i {
            background: none;
            -webkit-background-clip: unset;
            background-clip: unset;
            color: #2c5282;
            font-size: 1.8rem;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            font-weight: 500;
            align-items: center;
        }

        .nav-links a {
            text-decoration: none;
            color: #1e3a5f;
            transition: 0.2s;
            font-weight: 500;
        }

        .nav-links a:hover {
            color: #0b2b44;
        }

        .btn-outline {
            border: 1.5px solid #2c5282;
            padding: 0.5rem 1.2rem;
            border-radius: 2rem;
            background: white;
            font-weight: 600;
        }

        .btn-outline:hover {
            background: #2c5282;
            color: white;
            border-color: #2c5282;
        }

        /* hero section */
        .hero {
            text-align: center;
            margin-bottom: 3rem;
        }

        .badge {
            background: rgba(44, 82, 130, 0.12);
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 0.4rem 1rem;
            border-radius: 3rem;
            font-size: 0.8rem;
            font-weight: 600;
            margin-bottom: 1rem;
            color: #1f4973;
            backdrop-filter: blur(2px);
        }

        .hero h1 {
            font-size: 3.5rem;
            font-weight: 800;
            background: linear-gradient(145deg, #132c42, #2b5f8a);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom: 1rem;
            letter-spacing: -0.02em;
        }

        .hero p {
            font-size: 1.2rem;
            color: #2c3f5c;
            max-width: 680px;
            margin: 0 auto;
        }

        /* main interactive card */
        .demo-card {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 2.5rem;
            box-shadow: 0 25px 45px -12px rgba(0, 0, 0, 0.2), 0 1px 2px rgba(0,0,0,0.02);
            padding: 2rem 2rem 2rem 2rem;
            margin-bottom: 3rem;
            transition: all 0.2s ease;
            border: 1px solid rgba(255,255,255,0.7);
            backdrop-filter: blur(2px);
        }

        .demo-title {
            font-size: 1.8rem;
            font-weight: 700;
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 0.3rem;
        }

        .demo-sub {
            color: #4a617c;
            margin-bottom: 2rem;
            border-left: 4px solid #3a6ea5;
            padding-left: 1rem;
            font-size: 0.95rem;
        }

        .risk-input-area {
            display: flex;
            flex-wrap: wrap;
            gap: 1.2rem;
            align-items: flex-end;
            margin-bottom: 2rem;
        }

        .input-group {
            flex: 2;
            min-width: 200px;
        }

        .input-group label {
            display: block;
            font-weight: 600;
            margin-bottom: 0.4rem;
            font-size: 0.85rem;
            color: #1e3a5f;
            letter-spacing: -0.2px;
        }

        input, select {
            width: 100%;
            padding: 0.85rem 1rem;
            border-radius: 1.2rem;
            border: 1.5px solid #e2e8f2;
            font-family: inherit;
            font-size: 1rem;
            transition: all 0.2s;
            background: white;
        }

        input:focus, select:focus {
            outline: none;
            border-color: #3a6ea5;
            box-shadow: 0 0 0 3px rgba(58, 110, 165, 0.2);
        }

        button {
            background: linear-gradient(105deg, #1e3b5c, #2c5282);
            color: white;
            border: none;
            padding: 0.85rem 2rem;
            border-radius: 2rem;
            font-weight: 700;
            cursor: pointer;
            transition: 0.25s;
            font-size: 1rem;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.05);
        }

        button:hover {
            transform: translateY(-2px);
            background: linear-gradient(105deg, #143453, #23466e);
            box-shadow: 0 12px 20px -10px rgba(44,82,130,0.4);
        }

        /* result card dynamic */
        .risk-result {
            background: #fbfdff;
            border-radius: 1.8rem;
            padding: 1.8rem;
            margin-top: 1rem;
            border-left: 8px solid;
            transition: all 0.25s ease-in-out;
            box-shadow: 0 6px 14px rgba(0, 0, 0, 0.02);
        }

        .risk-score {
            font-size: 3.2rem;
            font-weight: 800;
            margin: 0.65rem 0 0.25rem;
            letter-spacing: -1px;
            line-height: 1.1;
        }

        .risk-label {
            font-weight: 700;
            font-size: 1.4rem;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .interpretation {
            margin-top: 1rem;
            color: #2a405e;
            background: #f0f4fa;
            padding: 0.9rem 1.2rem;
            border-radius: 1.2rem;
            font-size: 0.95rem;
        }

        .risk-meta {
            display: flex;
            justify-content: space-between;
            align-items: baseline;
            flex-wrap: wrap;
            margin-bottom: 6px;
        }

        .metric-badge {
            font-family: monospace;
            background: #eef2fa;
            padding: 0.2rem 0.7rem;
            border-radius: 2rem;
            font-size: 0.75rem;
        }

        hr {
            margin: 1.5rem 0;
            border: 0;
            height: 1px;
            background: radial-gradient(circle, #cbd5e6, transparent);
        }

        .features {
            display: flex;
            gap: 2rem;
            flex-wrap: wrap;
            justify-content: center;
            margin: 3rem 0 2rem;
        }

        .feature {
            flex: 1;
            min-width: 180px;
            background: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(4px);
            padding: 1.5rem;
            border-radius: 1.8rem;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.02);
            border: 1px solid rgba(255,255,255,0.7);
            transition: all 0.2s;
        }

        .feature i {
            font-size: 2rem;
            color: #2c5282;
            margin-bottom: 0.8rem;
        }

        .feature h3 {
            font-size: 1.2rem;
            margin-bottom: 0.5rem;
        }

        footer {
            text-align: center;
            margin-top: 2.5rem;
            padding-top: 1.5rem;
            border-top: 1px solid rgba(44,82,130,0.2);
            color: #4f6f94;
            font-size: 0.85rem;
        }

        /* additional loading + small animations */
        @keyframes fadeSlide {
            from { opacity: 0; transform: translateY(8px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .risk-result {
            animation: fadeSlide 0.35s ease-out;
        }

        .glow-text {
            font-weight: 500;
        }

        .inline-icon {
            margin-right: 6px;
        }

        @media (max-width: 750px) {
            .hero h1 { font-size: 2.3rem; }
            .navbar { padding: 0.8rem 1.2rem; }
            .demo-card { padding: 1.5rem; }
            .risk-score { font-size: 2.5rem; }
        }
    </style>
</head>
<body>
<div class="container">
    <div class="navbar">
        <div class="logo">
            <i class="fas fa-chart-line"></i> 
            <span>RiskLens</span>
        </div>
        <div class="nav-links">
            <a href="#"><i class="fas fa-tachometer-alt"></i> Dashboard</a>
            <a href="#"><i class="fas fa-microchip"></i> Research</a>
            <a href="#" class="btn-outline"><i class="fas fa-user-circle"></i> Sign in</a>
        </div>
    </div>

    <div class="hero">
        <div class="badge">
            <i class="fas fa-robot"></i> AI + FinTech · Real-time risk intelligence
        </div>
        <h1>See the hidden risk<br> before you buy.</h1>
        <p>Volatility · Sentiment · Options Skew → One smart score (0–100). Built for modern investors.</p>
    </div>

    <!-- ===== ENHANCED TOY DEMO APP with micro-interactions ===== -->
    <div class="demo-card">
        <div class="demo-title">
            <i class="fas fa-chart-simple" style="color:#2c5282"></i> 
            RiskLens Live Demo
        </div>
        <div class="demo-sub">
            "Dynamic risk engine" — real-time simulated risk using volatility proxy + market mood + sector DNA
        </div>

        <div class="risk-input-area">
            <div class="input-group">
                <label><i class="fas fa-tag"></i> Stock Ticker</label>
                <input type="text" id="ticker" placeholder="e.g., AAPL, TSLA, GME, NVDA, META" value="AAPL" autocomplete="off">
            </div>
            <div class="input-group">
                <label><i class="fas fa-chart-line"></i> Market Sentiment (simulated)</label>
                <select id="mood">
                    <option value="calm">🌿 Calm market (VIX low)</option>
                    <option value="neutral" selected>⚖️ Neutral / Mixed</option>
                    <option value="fear">⚠️ Fear / Panic (high VIX)</option>
                </select>
            </div>
            <button id="analyzeBtn">
                <i class="fas fa-eye"></i> Analyze Risk
            </button>
        </div>

        <div id="riskOutput" class="risk-result" style="border-left-color: #bdc4d4;">
            <div style="text-align: center; color: #5f7d9c;">
                <i class="fas fa-mouse-pointer"></i> Click "Analyze Risk" to see AI-driven risk analysis
            </div>
        </div>

        <hr>
        <div style="font-size: 0.8rem; color: #5f6f8a; text-align: center; display: flex; justify-content: center; gap: 1rem; flex-wrap: wrap;">
            <span><i class="fas fa-chart-line"></i> Simulated volatility proxy</span>
            <span><i class="fas fa-brain"></i> Sentiment-aware scoring</span>
            <span><i class="fas fa-shield-alt"></i> Educational demo — not financial advice</span>
        </div>
    </div>

    <div class="features">
        <div class="feature">
            <i class="fas fa-rocket"></i>
            <h3>10‑second risk scan</h3>
            <p>No complex Greeks. Instant visual clarity.</p>
        </div>
        <div class="feature">
            <i class="fas fa-microphone-alt"></i>
            <h3>AI insights (GPT-ready)</h3>
            <p>Plain English explanations of risk drivers.</p>
        </div>
        <div class="feature">
            <i class="fas fa-fire"></i>
            <h3>Portfolio heatmap</h3>
            <p>Visualize every position's hidden risk.</p>
        </div>
    </div>

    <footer>
        <i class="far fa-copyright"></i> 2026 RiskLens — simulated FinTech demo. Real version uses options flow, news NLP & on-chain data.
    </footer>
</div>

<script>
    // ------------------------------------------------------------
    // ENHANCED RISK ENGINE: Volatility proxy + dynamic mood + ticker personality
    // More realistic, deterministic & varied. Provides better UX.
    // ------------------------------------------------------------
    
    // Dictionary of sector-based risk offsets (realistic archetypes)
    const getTickerProfile = (symbol) => {
        const s = symbol.toUpperCase();
        // tech giants (lower base volatility)
        if (['AAPL', 'MSFT', 'GOOGL', 'GOOG', 'META', 'NVDA'].includes(s)) {
            return { baseVol: 0.22, name: 'Mega-cap Tech', momentumRisk: -0.03, specialNote: 'Liquidity strong, but sensitive to rates.' };
        }
        // growth & EV
        if (['TSLA', 'RIVN', 'LCID'].includes(s)) {
            return { baseVol: 0.58, name: 'High-growth EV', momentumRisk: 0.12, specialNote: 'Elastic to CEO tweets & delivery data.' };
        }
        // meme / retail favorites
        if (['GME', 'AMC', 'BB', 'KOSS'].includes(s)) {
            return { baseVol: 0.72, name: 'Meme stock', momentumRisk: 0.22, specialNote: 'High gamma & social sentiment driven.' };
        }
        // crypto-related
        if (['COIN', 'MSTR', 'RIOT', 'MARA'].includes(s)) {
            return { baseVol: 0.68, name: 'Crypto-correlated', momentumRisk: 0.18, specialNote: 'Extreme beta to BTC.' };
        }
        // financials & stable
        if (['JPM', 'BAC', 'WFC', 'GS', 'V', 'MA'].includes(s)) {
            return { baseVol: 0.28, name: 'Financial', momentumRisk: -0.02, specialNote: 'Sensitive to macro & Fed.' };
        }
        // healthcare defensive
        if (['JNJ', 'PFE', 'MRK', 'UNH', 'ABT'].includes(s)) {
            return { baseVol: 0.19, name: 'Healthcare', momentumRisk: -0.05, specialNote: 'Defensive profile, lower volatility.' };
        }
        // consumer cyclical
        if (['AMZN', 'NFLX', 'DIS', 'WMT'].includes(s)) {
            return { baseVol: 0.32, name: 'Consumer Cyclical', momentumRisk: 0.02, specialNote: 'Spending trends impact risk.' };
        }
        // default mid-cap / normal
        return { baseVol: 0.41, name: 'General equity', momentumRisk: 0.0, specialNote: 'Standard volatility profile.' };
    };

    // advanced deterministic but dynamic hash for ticker nuance
    function deterministicSeedMap(symbol) {
        let h = 0;
        for (let i = 0; i < symbol.length; i++) {
            h = ((h << 5) - h) + symbol.charCodeAt(i);
            h = h & h;
        }
        return Math.abs(h % 41) / 100; // 0..0.4 extra wiggle
    }
    
    function computeRiskScore(tickerSymbol, moodInput) {
        let tickerRaw = tickerSymbol.trim();
        if (tickerRaw === "") tickerRaw = "UNK";
        const upperTicker = tickerRaw.toUpperCase();
        const profile = getTickerProfile(upperTicker);
        
        // base volatility from profile (0.19 to 0.72)
        let baseVol = profile.baseVol;
        
        // additional pseudo-random but deterministic factor (makes each ticker unique)
        const extraRand = deterministicSeedMap(upperTicker);
        const totalVolRaw = baseVol + (extraRand * 0.18); // maximum extra 0.18
        
        // clamp realistic vol range
        let volatilityComponent = Math.min(0.85, Math.max(0.12, totalVolRaw));
        
        // Sentiment mood factor (expanded)
        let moodFactor = 0;
        let sentimentDesc = "";
        if (moodInput === 'calm') {
            moodFactor = -0.14;
            sentimentDesc = "Low VIX, risk appetite healthy";
        } else if (moodInput === 'neutral') {
            moodFactor = 0.0;
            sentimentDesc = "Mixed positioning, macro indecision";
        } else if (moodInput === 'fear') {
            moodFactor = 0.28;
            sentimentDesc = "Flight to safety, put skew widens";
        }
        
        // momentum risk adjustment from profile
        const momentumAdj = profile.momentumRisk;
        
        // additional ticker-specific "event risk" (e.g., earnings soon or high short interest)
        let specialEventRisk = 0;
        if (['GME','AMC','TSLA','BYND'].includes(upperTicker)) specialEventRisk = 0.05;
        if (upperTicker === 'NVDA') specialEventRisk = -0.02; // strong momentum but elevated expectations
        
        // FINAL raw risk between 0 and 1
        let rawRisk = volatilityComponent + moodFactor + momentumAdj + specialEventRisk;
        
        // apply boundary & scale to 0-100 confident
        rawRisk = Math.min(0.98, Math.max(0.02, rawRisk));
        let riskScore = Math.min(100, Math.max(0, Math.round(rawRisk * 100)));
        
        // Additional adjustment: if ticker is very short and "fear" mode extra amplification
        if (moodInput === 'fear' && (upperTicker === 'GME' || upperTicker === 'TSLA')) {
            riskScore = Math.min(100, riskScore + 6);
        }
        if (moodInput === 'calm' && profile.name === 'Healthcare') {
            riskScore = Math.max(8, riskScore - 4);
        }
        
        riskScore = Math.min(100, Math.max(0, riskScore));
        
        // Categorization + rich messages
        let label = "";
        let borderColor = "";
        let riskEmoji = "";
        let detailedInsight = "";
        
        if (riskScore <= 22) {
            label = "LOW RISK";
            borderColor = "#2b8c4a";
            riskEmoji = "🟢";
            detailedInsight = "Very stable profile. Low volatility & supportive sentiment. Good for capital preservation.";
        } else if (riskScore <= 48) {
            label = "MODERATE RISK";
            borderColor = "#e9b35f";
            riskEmoji = "🟡";
            detailedInsight = "Balanced risk-reward. Standard fluctuations expected. Consider diversifying.";
        } else if (riskScore <= 72) {
            label = "ELEVATED RISK";
            borderColor = "#f48c42";
            riskEmoji = "🟠";
            detailedInsight = "Heightened volatility or sentiment shifts. Use defined risk strategies.";
        } else {
            label = "SEVERE RISK";
            borderColor = "#dc4c2c";
            riskEmoji = "🔴";
            detailedInsight = "Extreme turbulence possible. Position sizing critical. Hedge recommended.";
        }
        
        // build dynamic interpretation based on profile + mood
        let sentimentPhrase = "";
        if (moodInput === 'fear') sentimentPhrase = "Fear premium is elevated — options skew suggests downside concerns.";
        else if (moodInput === 'calm') sentimentPhrase = "Calm regime supports risk assets, but complacency watch.";
        else sentimentPhrase = "Neutral sentiment → macro indicators mixed.";
        
        const finalMsg = `${profile.name} · ${sentimentDesc}. ${detailedInsight} ${profile.specialNote} ${sentimentPhrase}`;
        
        // Append ticker-specific nuanced note based on score extremes
        let extraInsight = "";
        if (riskScore >= 85 && moodInput === 'fear') extraInsight = " High short interest + panic could amplify moves.";
        if (riskScore <= 15 && moodInput === 'calm') extraInsight = " Ultra-low risk; typical range-bound trading.";
        if (upperTicker === 'TSLA') extraInsight += " (Elastic to sentiment & delivery metrics)";
        
        const finalInterpretation = finalMsg + extraInsight;
        
        return {
            score: riskScore,
            label: `${riskEmoji} ${label}`,
            borderColor,
            interpretation: finalInterpretation,
            ticker: upperTicker,
            moodRaw: moodInput,
            profileName: profile.name,
            sentimentDesc: sentimentDesc
        };
    }
    
    // UI update function with smooth loading feel
    function updateRiskUI() {
        const tickerInput = document.getElementById("ticker").value.trim();
        const ticker = tickerInput === "" ? "AAPL" : tickerInput;
        const mood = document.getElementById("mood").value;
        
        // Show subtle loading indicator
        const outputDiv = document.getElementById("riskOutput");
        outputDiv.style.opacity = "0.7";
        outputDiv.innerHTML = `<div style="text-align:center; padding:1rem;"><i class="fas fa-spinner fa-pulse"></i> Analyzing risk factors...</div>`;
        
        // simulate realistic micro delay (makes the "AI" feel more engaging)
        setTimeout(() => {
            const result = computeRiskScore(ticker, mood);
            outputDiv.style.opacity = "1";
            outputDiv.style.borderLeftColor = result.borderColor;
            
            // Create dynamic risk gauge visual
            const gaugeWidth = result.score;
            const gaugeColor = result.score <= 22 ? '#2b8c4a' : (result.score <= 48 ? '#e9b35f' : (result.score <= 72 ? '#f48c42' : '#dc4c2c'));
            
            outputDiv.innerHTML = `
                <div class="risk-meta">
                    <span class="risk-label">${result.label}</span>
                    <span class="metric-badge"><i class="fas fa-chart-line"></i> ${result.ticker} · ${result.profileName}</span>
                </div>
                <div class="risk-score">${result.score} <span style="font-size: 1.2rem;">/ 100</span></div>
                <div style="margin: 8px 0 12px 0; background: #e4e9f2; border-radius: 40px; height: 10px; width: 100%; overflow: hidden;">
                    <div style="width: ${result.score}%; background: ${gaugeColor}; height: 10px; border-radius: 40px; transition: width 0.4s ease;"></div>
                </div>
                <div class="interpretation">
                    <i class="fas fa-lightbulb" style="margin-right: 8px; color:#e9b35f"></i> 
                    ${result.interpretation}
                </div>
                <div style="margin-top: 14px; display: flex; flex-wrap: wrap; gap: 10px; justify-content: space-between; align-items: center;">
                    <div><i class="fas fa-chart-simple"></i> Sentiment: <strong>${result.sentimentDesc}</strong></div>
                    <div><i class="fas fa-microchip"></i> Model: vol proxy + option sentiment proxy</div>
                </div>
                <div style="margin-top: 12px; font-size: 0.75rem; background: #eef3fc; padding: 6px 12px; border-radius: 2rem; display: inline-block;">
                    <i class="fas fa-info-circle"></i> Real version: options flow, news NLP & on-chain data
                </div>
            `;
        }, 60);
    }
    
    // attach event listeners + default load, also listening to Enter key
    const analyzeBtn = document.getElementById("analyzeBtn");
    analyzeBtn.addEventListener("click", updateRiskUI);
    
    const tickerField = document.getElementById("ticker");
    tickerField.addEventListener("keypress", (e) => {
        if (e.key === "Enter") {
            e.preventDefault();
            updateRiskUI();
        }
    });
    
    // initial load
    window.addEventListener("DOMContentLoaded", updateRiskUI);
</script>
</body>
</html>
