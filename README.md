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
            --font-body: 'Lexend Deca', sans-serif;
            
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
                    // Restore P
                    P = data.P || {};
                    
                    // Restore UI
                    if(P.lifestyle) document.querySelector(`input[name="lifestyle"][value="${P.lifestyle}"]`).checked = true;
                    if(P.budget) document.getElementById('budget').value = P.budget;
                    if(P.industry) document.getElementById('industry').value = P.industry;
                    if(P.workmode) document.querySelector(`input[name="workmode"][value="${P.workmode}"]`).checked = true;

                    // Show banner
                    document.getElementById('savedBanner').style.display = 'block';
                    
                    // Jump to last step if data exists (optional, here we stay at 1 but prefill)
                    // Or jump to step 2 if step 1 is full
                    if(P.lifestyle && P.budget) {
                        // Could auto-advance, but let's keep it manual for clarity
                    }
                } catch (e) {
                    console.error("Failed to load session", e);
                }
            }
        }

        function saveSession() {
            // Collect current DOM state into P
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
            
            // Update Accent Color
            document.documentElement.style.setProperty('--accent', PATH_COLORS[stepIndex]);
        }

        function validateStep(stepNum) {
            let isValid = true;
            const wrapper = document.getElementById(`step-${stepNum}`);
            
            // Step 1 Validation
            if (stepNum === 1) {
                const lifestyle = document.querySelector('input[name="lifestyle"]:checked');
                const budget = document.getElementById('budget').value;
                
                const wrapLive = document.getElementById('wrap-lifestyle');
                const wrapBud = document.getElementById('wrap-budget');

                if (!lifestyle) {
                    wrapLive.classList.add('err');
                    isValid = false;
                } else {
                    wrapLive.classList.remove('err');
                }

                if (!budget || budget <= 0) {
                    wrapBud.classList.add('err');
                    isValid = false;
                } else {
                    wrapBud.classList.remove('err');
                }
            }

            // Step 2 Validation
            if (stepNum === 2) {
                const industry = document.getElementById('industry').value;
                const workmode = document.querySelector('input[name="workmode"]:checked');

                const wrapInd = document.getElementById('wrap-industry');
                const wrapMode = document.getElementById('wrap-workmode');

                if (!industry) {
                    wrapInd.classList.add('err');
                    isValid = false;
                } else {
                    wrapInd.classList.remove('err');
                }

                if (!workmode) {
                    wrapMode.classList.add('err');
                    isValid = false;
                } else {
                    wrapMode.classList.remove('err');
                }
            }

            return isValid;
        }

        function nextStep(currentStep) {
            if (!validateStep(currentStep)) return;

            saveSession(); // Save before moving

            // Hide current
            document.getElementById(`step-${currentStep}`).classList.remove('active');
            
            // Show next
            const next = currentStep + 1;
            if (next <= TOTAL_STEPS) {
                document.getElementById(`step-${next}`).classList.add('active');
                updateProgress(next);
                
                // If last step, generate results
                if (next === 3) {
                    generateResults();
                }
            }
        }

        function prevStep(currentStep) {
            document.getElementById(`step-${currentStep}`).classList.remove('active');
            const prev = currentStep - 1;
            document.getElementById(`step-${prev}`).classList.add('active');
            updateProgress(prev);
        }

        // --- Logic & Results ---
        function generateResults() {
            const container = document.getElementById('results-container');
            
            // Mock Logic: In a real scenario, this would filter a JSON dataset
            // Here we simulate based on inputs
            let recommendations = [];
            
            if (P.industry === 'tech') {
                recommendations.push({ city: "Manchester", reason: "Booming tech hub, lower rent than London.", match: 92 });
                recommendations.push({ city: "Bristol", reason: "Creative tech scene, high quality of life.", match: 88 });
            } else if (P.industry === 'creative') {
                recommendations.push({ city: "Leeds", reason: "Thriving arts district, affordable studios.", match: 90 });
                recommendations.push({ city: "Glasgow", reason: "Strong cultural funding, vibrant scene.", match: 85 });
            } else {
                recommendations.push({ city: "London", reason: "Global hub for all industries.", match: 75 });
                recommendations.push({ city: "Edinburgh", reason: "Growing sector, historic charm.", match: 80 });
            }

            // Add user constraints to summary
            let html = `<div style="background:var(--surface); padding:var(--space-md); border-radius:var(--radius); margin-bottom:var(--space-sm);">
                <strong>Your Criteria:</strong> ${P.lifestyle} lifestyle, £${P.budget} budget, ${P.industry} sector.
            </div>`;

            recommendations.forEach((rec, i) => {
                html += `
                <div style="border-left: 3px solid var(--accent); background:var(--surface); padding:var(--space-sm); margin-bottom:var(--space-sm); border-radius:0 var(--radius) var(--radius) 0;">
                    <h3 style="color:var(--accent); margin-bottom:0.25rem;">${rec.city}</h3>
                    <p style="font-size:0.9rem; color:var(--text-muted);">${rec.reason}</p>
                    <small>Match Score: ${rec.match}%</small>
                </div>`;
            });

            container.innerHTML = html;
        }

        // --- Export Logic (Placeholder for PDF) ---
        async function downloadSnapshot() {
            // In a real implementation, we would load jsPDF from CDN here
            // For now, we simulate the "Commitment Filter"
            
            const btn = document.getElementById('btn-download');
            const originalText = btn.innerText;
            
            btn.innerText = "Generating...";
            btn.disabled = true;

            // Simulate processing time
            await new Promise(r => setTimeout(r, 1500));

            // Create a shareable URL (Base64 encoded data)
            const shareData = btoa(JSON.stringify(P));
            const shareUrl = `${window.location.origin}${window.location.pathname}?data=${shareData}`;

            alert(`Snapshot Generated!\n\nYour data is ready. In a full version, this would download a PDF.\n\nShareable Link (simulated):\n${shareUrl}`);
            
            // Clear session after successful "commitment"
            clearSession();
            
            btn.innerText = "Downloaded";
            btn.style.background = "#4CAF50";
            btn.style.color = "#fff";
        }

        // --- URL Parameter Handling (For Shared Links) ---
        window.onload = function() {
            const urlParams = new URLSearchParams(window.location.search);
            const dataParam = urlParams.get('data');
            
            if (dataParam) {
                try {
                    const decoded = JSON.parse(atob(dataParam));
                    // Pre-fill form for read-only view or edit
                    // (Implementation omitted for brevity, but follows same logic as loadSession)
                    document.getElementById('savedBanner').innerHTML = "Loaded from shared link. Edit to refine.";
                    document.getElementById('savedBanner').style.display = 'block';
                } catch(e) {
                    console.error("Invalid shared data");
                }
            }
        };
    </script>
</body>
</html># daam.github.io
UKL
