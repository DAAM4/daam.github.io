<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UK Relocation Snapshot | Wireframe Physical</title>
    
    <!-- Fonts: Fraunces (Editorial Headings) & Lexend Deca (Readable Body) -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,300;400;600&family=Lexend+Deca:wght@300;400;500&display=swap" rel="stylesheet">

    <style>
        :root {
            /* Palette */
            --bg: #121212;
            --surface: #1E1E1E;
            --text-main: #E0E0E0;
            --text-muted: #A0A0A0;
            
            /* Dynamic Accent (Set by JS based on path) */
            --accent: #00E5FF; 
            --accent-dim: rgba(0, 229, 255, 0.1);
            
            /* Typography */
            --font-head: 'Fraunces', serif;
            --font-body: 'Lexend+Deca', sans-serif;
            
            /* Spacing & Layout */
            --space-xs: 0.5rem;
            --space-sm: 1rem;
            --space-md: 2rem;
            --space-lg: 4rem;
            --radius: 8px;
            --max-w: 680px;
            
            /* Transitions */
            --ease: cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }

        /* Reset & Base */
        * { box-sizing: border-box; margin: 0; padding: 0; }
        
        body {
            background-color: var(--bg);
            color: var(--text-main);
            font-family: var(--font-body);
            line-height: 1.6;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: var(--space-md);
        }

        /* Header & Branding */
        header {
            width: 100%;
            max-width: var(--max-w);
            margin-bottom: var(--space-lg);
            border-bottom: 1px solid var(--surface);
            padding-bottom: var(--space-sm);
        }

        h1 {
            font-family: var(--font-head);
            font-weight: 400;
            font-size: 2.5rem;
            letter-spacing: -0.02em;
            margin-bottom: var(--space-xs);
        }

        .tagline {
            color: var(--text-muted);
            font-size: 0.9rem;
        }

        /* Progress Bar */
        .progress-container {
            width: 100%;
            max-width: var(--max-w);
            height: 4px;
            background: var(--surface);
            margin-bottom: var(--space-lg);
            border-radius: 2px;
            overflow: hidden;
        }

        .progress-bar {
            height: 100%;
            background: var(--accent);
            width: 0%;
            transition: width 0.4s var(--ease);
        }

        /* Main Form Area */
        main {
            width: 100%;
            max-width: var(--max-w);
            position: relative;
        }

        .step {
            display: none;
            animation: fadeIn 0.4s var(--ease);
        }

        .step.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        h2 {
            font-family: var(--font-head);
            font-size: 1.8rem;
            margin-bottom: var(--space-md);
            color: var(--accent);
        }

        p.desc {
            color: var(--text-muted);
            margin-bottom: var(--space-md);
            font-size: 1rem;
        }

        /* Input Groups */
        .group {
            margin-bottom: var(--space-md);
        }

        label.field-label {
            display: block;
            margin-bottom: var(--space-xs);
            font-weight: 500;
            font-size: 0.9rem;
        }

        /* Custom Radio Cards (Hidden Input) */
        .radio-group {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: var(--space-sm);
        }

        .radio-card input {
            display: none;
        }

        .radio-card label {
            display: block;
            background: var(--surface);
            padding: var(--space-md);
            border: 1px solid transparent;
            border-radius: var(--radius);
            cursor: pointer;
            transition: all 0.2s var(--ease);
            text-align: center;
        }

        .radio-card label:hover {
            border-color: var(--text-muted);
        }

        .radio-card input:checked + label {
            background: var(--accent-dim);
            border-color: var(--accent);
            color: var(--accent);
            font-weight: 600;
        }

        /* Text Inputs */
        input[type="text"], input[type="number"], select {
            width: 100%;
            background: var(--surface);
            border: 1px solid #333;
            color: var(--text-main);
            padding: var(--space-sm);
            border-radius: var(--radius);
            font-family: var(--font-body);
            font-size: 1rem;
            transition: border-color 0.2s;
        }

        input:focus, select:focus {
            outline: none;
            border-color: var(--accent);
        }

        /* Error States */
        .field-wrapper.err input, 
        .field-wrapper.err select {
            border-color: #FF5252;
        }

        .error-msg {
            color: #FF5252;
            font-size: 0.85rem;
            margin-top: 0.25rem;
            display: none;
        }

        .field-wrapper.err .error-msg {
            display: block;
        }

        /* Navigation Buttons */
        .nav-actions {
            display: flex;
            justify-content: space-between;
            margin-top: var(--space-lg);
        }

        button {
            background: transparent;
            border: 1px solid var(--text-muted);
            color: var(--text-main);
            padding: 0.75rem 1.5rem;
            border-radius: var(--radius);
            cursor: pointer;
            font-family: var(--font-body);
            font-weight: 500;
            transition: all 0.2s;
        }

        button:hover {
            border-color: var(--text-main);
            background: var(--surface);
        }

        button.primary {
            background: var(--accent);
            color: var(--bg);
            border: none;
            font-weight: 600;
        }

        button.primary:hover {
            background: #fff;
            color: var(--bg);
        }

        /* Saved Banner */
        .saved-banner {
            background: var(--accent-dim);
            border-left: 3px solid var(--accent);
            padding: var(--space-sm);
            margin-bottom: var(--space-md);
            font-size: 0.9rem;
            display: none;
        }

        /* Footer */
        footer {
            margin-top: auto;
            padding-top: var(--space-lg);
            color: var(--text-muted);
            font-size: 0.8rem;
            text-align: center;
            width: 100%;
            max-width: var(--max-w);
        }

        /* Responsive */
        @media (max-width: 600px) {
            .radio-group { grid-template-columns: 1fr; }
            h1 { font-size: 2rem; }
        }
    </style>
</head>
<body>

    <header>
        <h1>Relocation Snapshot</h1>
        <div class="tagline">We don't hold profiles. You do. Define your future, download your plan.</div>
    </header>

    <div class="progress-container">
        <div class="progress-bar" id="progressBar"></div>
    </div>

    <main>
        <div id="savedBanner" class="saved-banner">
            Your progress was saved locally. You can resume where you left off.
        </div>

        <!-- Step 1: Living Preferences -->
        <div class="step active" id="step-1" data-step="1">
            <h2>The Living Standard</h2>
            <p class="desc">Where do you want to wake up? This defines your daily rhythm.</p>

            <div class="group field-wrapper" id="wrap-lifestyle">
                <label class="field-label">Lifestyle Vibe</label>
                <div class="radio-group">
                    <div class="radio-card">
                        <input type="radio" name="lifestyle" value="urban" id="live-urban">
                        <label for="live-urban">Urban Pulse<br><span style="font-size:0.8em; color:var(--text-muted)">Fast-paced, culture, nightlife</span></label>
                    </div>
                    <div class="radio-card">
                        <input type="radio" name="lifestyle" value="coastal" id="live-coastal">
                        <label for="live-coastal">Coastal Calm<br><span style="font-size:0.8em; color:var(--text-muted)">Sea views, slower pace, fresh air</span></label>
                    </div>
                    <div class="radio-card">
                        <input type="radio" name="lifestyle" value="rural" id="live-rural">
                        <label for="live-rural">Rural Quiet<br><span style="font-size:0.8em; color:var(--text-muted)">Nature, space, community</span></label>
                    </div>
                    <div class="radio-card">
                        <input type="radio" name="lifestyle" value="industrial" id="live-industrial">
                        <label for="live-industrial">Industrial Edge<br><span style="font-size:0.8em; color:var(--text-muted)">Gritty, creative, affordable</span></label>
                    </div>
                </div>
                <div class="error-msg">Please select a lifestyle preference.</div>
            </div>

            <div class="group field-wrapper" id="wrap-budget">
                <label class="field-label">Max Monthly Rent (£)</label>
                <input type="number" id="budget" placeholder="e.g. 1200">
                <div class="error-msg">Please enter a valid budget.</div>
            </div>

            <div class="nav-actions">
                <button disabled>Back</button>
                <button class="primary" onclick="nextStep(1)">Next: Career Engine</button>
            </div>
        </div>

        <!-- Step 2: Working Preferences -->
        <div class="step" id="step-2" data-step="2">
            <h2>The Career Engine</h2>
            <p class="desc">What fuels your ambition? We match industry hubs to your goals.</p>

            <div class="group field-wrapper" id="wrap-industry">
                <label class="field-label">Primary Industry</label>
                <select id="industry">
                    <option value="">Select an industry...</option>
                    <option value="tech">Technology & Software</option>
                    <option value="creative">Creative & Design</option>
                    <option value="finance">Finance & Business</option>
                    <option value="healthcare">Healthcare & Science</option>
                    <option value="trades">Trades & Construction</option>
                    <option value="education">Education & Research</option>
                </select>
                <div class="error-msg">Please select an industry.</div>
            </div>

            <div class="group field-wrapper" id="wrap-workmode">
                <label class="field-label">Work Mode Preference</label>
                <div class="radio-group">
                    <div class="radio-card">
                        <input type="radio" name="workmode" value="remote" id="work-remote">
                        <label for="work-remote">Fully Remote</label>
                    </div>
                    <div class="radio-card">
                        <input type="radio" name="workmode" value="hybrid" id="work-hybrid">
                        <label for="work-hybrid">Hybrid (2-3 days office)</label>
                    </div>
                    <div class="radio-card">
                        <input type="radio" name="workmode" value="onsite" id="work-onsite">
                        <label for="work-onsite">On-Site Only</label>
                    </div>
                </div>
                <div class="error-msg">Please select a work mode.</div>
            </div>

            <div class="nav-actions">
                <button onclick="prevStep(2)">Back</button>
                <button class="primary" onclick="nextStep(2)">Next: Generate Snapshot</button>
            </div>
        </div>

        <!-- Step 3: Results & Export -->
        <div class="step" id="step-3" data-step="3">
            <h2>Your Snapshot</h2>
            <p class="desc">Based on your inputs, here are your top matches. This data lives in your browser until you download it.</p>
            
            <div id="results-container" style="margin-bottom: var(--space-lg);">
                <!-- Results injected here via JS -->
                <div style="background:var(--surface); padding:var(--space-md); border-radius:var(--radius);">
                    <strong>Analysis:</strong> Calculating optimal matches...
                </div>
            </div>

            <div class="nav-actions">
                <button onclick="prevStep(3)">Back</button>
                <button class="primary" id="btn-download" onclick="downloadSnapshot()">Download PDF Snapshot</button>
            </div>
        </div>
    </main>

    <footer>
        <p>We don't hold profiles — you do. <br>Your snapshot travels with you.</p>
    </footer>

    <!-- Scripts -->
    <script>
        // --- REAL UK CITY DATASET ---
        // Salaries are approximate averages for mid-level roles (£)
        // Rents are approximate 1-bed city centre (£)
        // Vibe scores (0-100) indicate how strongly the city fits the category
        const UK_CITIES = [
            {
                name: "London",
                region: "South East",
                rent: 2100,
                salaries: { tech: 65000, creative: 45000, finance: 75000, healthcare: 42000, trades: 38000, education: 35000 },
                vibes: { urban: 100, coastal: 20, rural: 10, industrial: 60 },
                notes: "Global hub. Unbeatable culture, but high cost of living."
            },
            {
                name: "Manchester",
                region: "North West",
                rent: 950,
                salaries: { tech: 48000, creative: 38000, finance: 52000, healthcare: 38000, trades: 32000, education: 34000 },
                vibes: { urban: 85, coastal: 10, rural: 20, industrial: 90 },
                notes: "Booming tech scene, gritty industrial heritage, very affordable."
            },
            {
                name: "Bristol",
                region: "South West",
                rent: 1150,
                salaries: { tech: 46000, creative: 42000, finance: 48000, healthcare: 39000, trades: 34000, education: 36000 },
                vibes: { urban: 75, coastal: 60, rural: 40, industrial: 50 },
                notes: "Creative capital, high quality of life, slightly higher rents."
            },
            {
                name: "Leeds",
                region: "Yorkshire",
                rent: 850,
                salaries: { tech: 44000, creative: 36000, finance: 55000, healthcare: 37000, trades: 31000, education: 33000 },
                vibes: { urban: 80, coastal: 0, rural: 30, industrial: 70 },
                notes: "Financial powerhouse, thriving arts, very affordable."
            },
            {
                name: "Edinburgh",
                region: "Scotland",
                rent: 1050,
                salaries: { tech: 47000, creative: 40000, finance: 58000, healthcare: 40000, trades: 33000, education: 38000 },
                vibes: { urban: 70, coastal: 40, rural: 50, industrial: 30 },
                notes: "Historic charm, strong finance/tech, beautiful surroundings."
            },
            {
                name: "Glasgow",
                region: "Scotland",
                rent: 800,
                salaries: { tech: 42000, creative: 38000, finance: 45000, healthcare: 38000, trades: 32000, education: 35000 },
                vibes: { urban: 75, coastal: 30, rural: 20, industrial: 85 },
                notes: "Friendly, cultural, affordable, strong industrial roots."
            },
            {
                name: "Brighton",
                region: "South Coast",
                rent: 1300,
                salaries: { tech: 45000, creative: 44000, finance: 40000, healthcare: 38000, trades: 33000, education: 35000 },
                vibes: { urban: 60, coastal: 100, rural: 20, industrial: 20 },
                notes: "Beach life, tech hub, creative, expensive for the south coast."
            },
            {
                name: "Birmingham",
                region: "Midlands",
                rent: 900,
                salaries: { tech: 43000, creative: 37000, finance: 48000, healthcare: 37000, trades: 32000, education: 33000 },
                vibes: { urban: 85, coastal: 0, rural: 10, industrial: 80 },
                notes: "Central location, massive regeneration, diverse economy."
            },
            {
                name: "Newcastle",
                region: "North East",
                rent: 750,
                salaries: { tech: 40000, creative: 35000, finance: 42000, healthcare: 36000, trades: 30000, education: 32000 },
                vibes: { urban: 70, coastal: 50, rural: 30, industrial: 75 },
                notes: "Great nightlife, very affordable, close to countryside."
            },
            {
                name: "Cambridge",
                region: "East of England",
                rent: 1400,
                salaries: { tech: 60000, creative: 38000, finance: 50000, healthcare: 42000, trades: 35000, education: 45000 },
                vibes: { urban: 50, coastal: 0, rural: 80, industrial: 40 },
                notes: "World-class science/tech, historic, expensive, quieter."
            },
            {
                name: "Oxford",
                region: "South East",
                rent: 1350,
                salaries: { tech: 58000, creative: 39000, finance: 52000, healthcare: 41000, trades: 34000, education: 44000 },
                vibes: { urban: 45, coastal: 0, rural: 85, industrial: 30 },
                notes: "Academic hub, high salaries, high cost of living."
            },
            {
                name: "Bath",
                region: "South West",
                rent: 1100,
                salaries: { tech: 42000, creative: 40000, finance: 45000, healthcare: 38000, trades: 33000, education: 36000 },
                vibes: { urban: 40, coastal: 30, rural: 90, industrial: 20 },
                notes: "Beautiful Georgian architecture, relaxed, tourist-heavy."
            }
        ];

        // --- Configuration & State ---
        const STEPS = ['step-1', 'step-2', 'step-3'];
        const TOTAL_STEPS = STEPS.length;
        
        // Data Object P - holds all user inputs
        let P = {
            lifestyle: null,
            budget: null,
            industry: null,
            workmode: null
        };

        // Path Colors (Living = Blue/Teal, Work = Amber, Result = Purple)
        const PATH_COLORS = {
            1: '#00E5FF', // Living
            2: '#FFB74D', // Work
            3: '#BA68C8'  // Result
        };

        // --- Initialization ---
        document.addEventListener('DOMContentLoaded', () => {
            loadSession();
            updateProgress(1);
        });

        // --- Session Storage Logic ---
        function loadSession() {
            const saved = sessionStorage.getItem('uk_reloc_snapshot');
            if (saved) {
                try {
                    const data = JSON.parse(saved);
                    P = data.P || {};
                    
                    if(P.lifestyle) document.querySelector(`input[name="lifestyle"][value="${P.lifestyle}"]`).checked = true;
                    if(P.budget) document.getElementById('budget').value = P.budget;
                    if(P.industry) document.getElementById('industry').value = P.industry;
                    if(P.workmode) document.querySelector(`input[name="workmode"][value="${P.workmode}"]`).checked = true;

                    document.getElementById('savedBanner').style.display = 'block';
                } catch (e) {
                    console.error("Failed to load session", e);
                }
            }
        }

        function saveSession() {
            P.lifestyle = document.querySelector('input[name="lifestyle"]:checked')?.value;
            P.budget = document.getElementById('budget').value;
            P.industry = document.getElementById('industry').value;
            P.workmode = document.querySelector('input[name="workmode"]:checked')?.value;
            sessionStorage.setItem('uk_reloc_snapshot', JSON.stringify({ P }));
        }

        function clearSession() {
            sessionStorage.removeItem('uk_reloc_snapshot');
            document.getElementById('savedBanner').style.display = 'none';
        }

        // --- Navigation & Validation ---
        function updateProgress(stepIndex) {
            const pct = ((stepIndex - 1) / (TOTAL_STEPS - 1)) * 100;
            document.getElementById('progressBar').style.width = `${pct}%`;
            document.documentElement.style.setProperty('--accent', PATH_COLORS[stepIndex]);
        }

        function validateStep(stepNum) {
            let isValid = true;
            
            if (stepNum === 1) {
                const lifestyle = document.querySelector('input[name="lifestyle"]:checked');
                const budget = document.getElementById('budget').value;
                const wrapLive = document.getElementById('wrap-lifestyle');
                const wrapBud = document.getElementById('wrap-budget');

                if (!lifestyle) { wrapLive.classList.add('err'); isValid = false; } else { wrapLive.classList.remove('err'); }
                if (!budget || budget <= 0) { wrapBud.classList.add('err'); isValid = false; } else { wrapBud.classList.remove('err'); }
            }

            if (stepNum === 2) {
                const industry = document.getElementById('industry').value;
                const workmode = document.querySelector('input[name="workmode"]:checked');
                const wrapInd = document.getElementById('wrap-industry');
                const wrapMode = document.getElementById('wrap-workmode');

                if (!industry) { wrapInd.classList.add('err'); isValid = false; } else { wrapInd.classList.remove('err'); }
                if (!workmode) { wrapMode.classList.add('err'); isValid = false; } else { wrapMode.classList.remove('err'); }
            }

            return isValid;
        }

        function nextStep(currentStep) {
            if (!validateStep(currentStep)) return;
            saveSession();
            document.getElementById(`step-${currentStep}`).classList.remove('active');
            const next = currentStep + 1;
            if (next <= TOTAL_STEPS) {
                document.getElementById(`step-${next}`).classList.add('active');
                updateProgress(next);
                if (next === 3) generateResults();
            }
        }

        function prevStep(currentStep) {
            document.getElementById(`step-${currentStep}`).classList.remove('active');
            const prev = currentStep - 1;
            document.getElementById(`step-${prev}`).classList.add('active');
            updateProgress(prev);
        }

        // --- REAL FILTERING LOGIC ---
        function generateResults() {
            const container = document.getElementById('results-container');
            const userBudget = parseInt(P.budget);
            const userIndustry = P.industry;
            const userLifestyle = P.lifestyle;

            // Calculate scores for each city
            const scoredCities = UK_CITIES.map(city => {
                let score = 0;
                let reasons = [];

                // 1. Budget Check (Hard Filter + Soft Score)
                if (city.rent > userBudget * 1.2) {
                    // If rent is > 20% over budget, heavily penalize but don't exclude completely (maybe they can stretch)
                    score -= 50;
                    reasons.push("Rent significantly over budget");
                } else if (city.rent <= userBudget) {
                    score += 40; // Good fit
                    reasons.push("Fits budget comfortably");
                } else {
                    score += 20; // Slightly over but manageable
                    reasons.push("Slightly over budget");
                }

                // 2. Industry Match (Salary Potential)
                const avgSalary = city.salaries[userIndustry] || 0;
                // Normalize salary score (assuming 40k is baseline, 70k is high)
                const salaryScore = Math.min((avgSalary / 70000) * 30, 30);
                score += salaryScore;
                
                if (avgSalary > 50000) reasons.push(`Strong ${userIndustry} salaries (£${avgSalary.toLocaleString()})`);
                else if (avgSalary > 35000) reasons.push(`Decent ${userIndustry} salaries (£${avgSalary.toLocaleString()})`);
                else reasons.push(`${userIndustry} market is smaller here`);

                // 3. Lifestyle Match (Vibe Score)
                const vibeScore = city.vibes[userLifestyle];
                score += (vibeScore * 0.3); // Max 30 points from vibe
                
                if (vibeScore > 80) reasons.push("Perfect match for your lifestyle");
                else if (vibeScore > 50) reasons.push("Good lifestyle fit");

                // Cap score at 100
                score = Math.min(Math.max(score, 0), 100);

                return {
                    ...city,
                    matchScore: Math.round(score),
                    reasons: reasons
                };
            });

            // Sort by score descending
            scoredCities.sort((a, b) => b.matchScore - a.matchScore);

            // Take top 3
            const topMatches = scoredCities.slice(0, 3);

            // Render HTML
            let html = `<div style="background:var(--surface); padding:var(--space-md); border-radius:var(--radius); margin-bottom:var(--space-sm);">
                <strong>Your Criteria:</strong> ${P.lifestyle} lifestyle, £${P.budget} budget, ${P.industry} sector.
            </div>`;

            topMatches.forEach(city => {
                let reasonText = city.reasons.join(", ");
                html += `
                <div style="border-left: 3px solid var(--accent); background:var(--surface); padding:var(--space-md); margin-bottom:var(--space-sm); border-radius:0 var(--radius) var(--radius) 0;">
                    <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:0.5rem;">
                        <h3 style="color:var(--accent); margin:0;">${city.name}</h3>
                        <span style="background:var(--accent-dim); color:var(--accent); padding:0.2rem 0.6rem; border-radius:4px; font-weight:bold;">${city.matchScore}% Match</span>
                    </div>
                    <p style="font-size:0.9rem; color:var(--text-muted); margin-bottom:0.5rem;">${city.notes}</p>
                    <div style="font-size:0.85rem; color:#ccc; border-top:1px solid #333; padding-top:0.5rem;">
                        <strong>Why?</strong> ${reasonText}
                    </div>
                    <div style="margin-top:0.5rem; font-size:0.85rem; color:#aaa;">
                        Est. Rent: £${city.rent} | Avg ${userIndustry} Salary: £${city.salaries[userIndustry].toLocaleString()}
                    </div>
                </div>`;
            });

            container.innerHTML = html;
        }

        // --- Export Logic ---
        async function downloadSnapshot() {
            const btn = document.getElementById('btn-download');
            btn.innerText = "Generating...";
            btn.disabled = true;

            await new Promise(r => setTimeout(r, 1500));

            const shareData = btoa(JSON.stringify(P));
            const shareUrl = `${window.location.origin}${window.location.pathname}?data=${shareData}`;

            alert(`Snapshot Generated!\n\nYour data is ready. In a full version, this would download a PDF.\n\nShareable Link (simulated):\n${shareUrl}`);
            
            clearSession();
            btn.innerText = "Downloaded";
            btn.style.background = "#4CAF50";
            btn.style.color = "#fff";
        }

        // --- URL Parameter Handling ---
        window.onload = function() {
            const urlParams = new URLSearchParams(window.location.search);
            const dataParam = urlParams.get('data');
            if (dataParam) {
                try {
                    const decoded = JSON.parse(atob(dataParam));
                    document.getElementById('savedBanner').innerHTML = "Loaded from shared link. Edit to refine.";
                    document.getElementById('savedBanner').style.display = 'block';
                } catch(e) { console.error("Invalid shared data"); }
            }
        };
    </script>
</body>
</html>
