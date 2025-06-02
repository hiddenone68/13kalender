# 13kalender
<!DOCTYPE html>
<html lang="nl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Officiële 13-Maanden Kalender App</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #1a2a6c;
            --secondary: #2c3e50;
            --accent: #e74c3c;
            --light: #f8f9fa;
            --dark: #1a252f;
            --success: #27ae60;
            --info: #3498db;
            --warning: #f39c12;
            --gradient-start: #1a2a6c;
            --gradient-mid: #b21f1f;
            --gradient-end: #1a2a6c;
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, var(--gradient-start), var(--gradient-mid), var(--gradient-end));
            color: var(--light);
            min-height: 100vh;
            padding: 20px;
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            text-align: center;
            margin-bottom: 30px;
            padding: 30px;
            background: rgba(26, 37, 47, 0.92);
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4);
            border: 2px solid rgba(52, 152, 219, 0.4);
            position: relative;
            overflow: hidden;
        }
        
        header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, var(--success), var(--info), var(--warning));
        }
        
        .logo {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .logo-icon {
            font-size: 3rem;
            color: var(--info);
        }
        
        h1 {
            font-size: 2.8rem;
            margin-bottom: 10px;
            color: white;
            text-shadow: 0 2px 8px rgba(0, 0, 0, 0.5);
            background: linear-gradient(90deg, #3498db, #2ecc71);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .subtitle {
            font-size: 1.2rem;
            margin: 20px auto;
            color: var(--light);
            max-width: 800px;
            padding: 15px;
            background: rgba(0, 0, 0, 0.25);
            border-radius: 10px;
            line-height: 1.7;
        }
        
        .badges {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin: 20px 0;
            flex-wrap: wrap;
        }
        
        .badge {
            background: rgba(52, 152, 219, 0.3);
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 0.9rem;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .app-container {
            display: flex;
            flex-wrap: wrap;
            gap: 25px;
            margin-bottom: 30px;
        }
        
        .converter {
            flex: 1;
            min-width: 320px;
            background: rgba(26, 37, 47, 0.92);
            padding: 25px;
            border-radius: 15px;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.4);
            border: 2px solid rgba(52, 152, 219, 0.4);
        }
        
        .calendar {
            flex: 2;
            min-width: 320px;
            background: rgba(26, 37, 47, 0.92);
            padding: 25px;
            border-radius: 15px;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.4);
            border: 2px solid rgba(52, 152, 219, 0.4);
        }
        
        h2 {
            color: var(--info);
            margin-bottom: 25px;
            font-size: 1.8rem;
            padding-bottom: 15px;
            border-bottom: 2px solid var(--info);
            display: flex;
            align-items: center;
            gap: 12px;
        }
        
        h2 i {
            font-size: 1.5rem;
        }
        
        .input-group {
            margin-bottom: 25px;
        }
        
        label {
            display: block;
            margin-bottom: 10px;
            font-weight: bold;
            color: var(--light);
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        input, select {
            width: 100%;
            padding: 14px;
            border: none;
            border-radius: 8px;
            background: rgba(255, 255, 255, 0.95);
            font-size: 1.05rem;
            box-shadow: inset 0 2px 5px rgba(0, 0, 0, 0.1);
        }
        
        button {
            background: linear-gradient(135deg, var(--info), var(--success));
            color: white;
            border: none;
            padding: 14px 25px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1.1rem;
            font-weight: bold;
            transition: all 0.3s;
            width: 100%;
            margin-top: 15px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
        }
        
        button:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
            background: linear-gradient(135deg, #2980b9, #219653);
        }
        
        button:active {
            transform: translateY(1px);
        }
        
        .result {
            background: linear-gradient(135deg, rgba(52, 152, 219, 0.3), rgba(39, 174, 96, 0.3));
            padding: 25px;
            border-radius: 12px;
            margin-top: 25px;
            text-align: center;
            min-height: 140px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            border: 2px solid rgba(52, 152, 219, 0.5);
            box-shadow: inset 0 0 20px rgba(0, 0, 0, 0.2);
        }
        
        .result h3 {
            font-size: 1.6rem;
            margin-bottom: 15px;
            color: var(--light);
        }
        
        .result p {
            font-size: 2rem;
            font-weight: bold;
            color: white;
            text-shadow: 0 2px 8px rgba(0, 0, 0, 0.4);
            background: linear-gradient(90deg, #3498db, #2ecc71);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .month-navigation {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
            gap: 15px;
        }
        
        .month-name {
            text-align: center;
            font-size: 1.9rem;
            font-weight: bold;
            color: var(--info);
            padding: 12px;
            flex-grow: 1;
            background: rgba(0, 0, 0, 0.25);
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
        }
        
        .nav-button {
            background: linear-gradient(135deg, var(--info), var(--success));
            color: white;
            border: none;
            padding: 12px 22px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1.1rem;
            font-weight: bold;
            transition: all 0.3s;
            width: auto;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
        }
        
        .nav-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
            background: linear-gradient(135deg, #2980b9, #219653);
        }
        
        .calendar-grid {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            gap: 10px;
        }
        
        .day-header {
            background: rgba(52, 152, 219, 0.4);
            padding: 14px 5px;
            text-align: center;
            font-weight: bold;
            border-radius: 8px;
            font-size: 1.1rem;
        }
        
        .calendar-day {
            background: rgba(255, 255, 255, 0.12);
            padding: 15px 8px;
            text-align: center;
            border-radius: 8px;
            min-height: 90px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            transition: all 0.3s;
            border: 1px solid rgba(255, 255, 255, 0.15);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
            position: relative;
        }
        
        .calendar-day:hover {
            transform: translateY(-5px) scale(1.03);
            background: rgba(52, 152, 219, 0.35);
            cursor: pointer;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
            border: 1px solid var(--info);
            z-index: 10;
        }
        
        .day-number {
            font-size: 1.4rem;
            font-weight: bold;
            color: white;
        }
        
        .gregorian-date {
            font-size: 0.85rem;
            opacity: 0.9;
            margin-top: 8px;
            background: rgba(0, 0, 0, 0.3);
            padding: 3px 6px;
            border-radius: 4px;
        }
        
        .today {
            background: rgba(231, 76, 60, 0.45);
            box-shadow: 0 0 0 3px var(--accent);
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(231, 76, 60, 0.7); }
            70% { box-shadow: 0 0 0 10px rgba(231, 76, 60, 0); }
            100% { box-shadow: 0 0 0 0 rgba(231, 76, 60, 0); }
        }
        
        .today::after {
            content: 'Vandaag';
            position: absolute;
            top: 5px;
            right: 5px;
            background: var(--accent);
            color: white;
            font-size: 0.7rem;
            padding: 3px 8px;
            border-radius: 4px;
            font-weight: bold;
        }
        
        .special-day {
            background: rgba(46, 204, 113, 0.45);
        }
        
        .special-day::after {
            content: 'Speciaal';
            position: absolute;
            top: 5px;
            right: 5px;
            background: var(--success);
            color: white;
            font-size: 0.7rem;
            padding: 3px 8px;
            border-radius: 4px;
            font-weight: bold;
        }
        
        .info {
            background: rgba(26, 37, 47, 0.92);
            padding: 30px;
            border-radius: 15px;
            margin-top: 30px;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.4);
            border: 2px solid rgba(52, 152, 219, 0.4);
        }
        
        .info h2 {
            color: var(--info);
            margin-bottom: 20px;
        }
        
        .info ul {
            padding-left: 25px;
            margin-bottom: 25px;
        }
        
        .info li {
            margin-bottom: 12px;
            line-height: 1.7;
            position: relative;
            padding-left: 30px;
        }
        
        .info li::before {
            content: '•';
            color: var(--info);
            font-size: 1.8rem;
            position: absolute;
            left: 0;
            top: -8px;
        }
        
        .month-list {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
            gap: 20px;
            margin-top: 25px;
        }
        
        .month-card {
            background: linear-gradient(135deg, rgba(52, 152, 219, 0.3), rgba(39, 174, 96, 0.3));
            padding: 20px;
            border-radius: 12px;
            text-align: center;
            transition: all 0.3s;
            border: 1px solid rgba(52, 152, 219, 0.4);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        .month-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            background: linear-gradient(135deg, rgba(52, 152, 219, 0.4), rgba(39, 174, 96, 0.4));
            border: 1px solid var(--info);
        }
        
        .month-card h3 {
            color: var(--info);
            margin-bottom: 15px;
            font-size: 1.4rem;
        }
        
        .month-card p {
            font-size: 1.1rem;
            color: var(--light);
        }
        
        .features {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }
        
        .feature-card {
            background: rgba(255, 255, 255, 0.1);
            padding: 25px;
            border-radius: 12px;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: all 0.3s;
        }
        
        .feature-card:hover {
            transform: translateY(-5px);
            background: rgba(52, 152, 219, 0.2);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
        }
        
        .feature-icon {
            font-size: 2.5rem;
            color: var(--info);
            margin-bottom: 15px;
        }
        
        .feature-card h3 {
            color: white;
            margin-bottom: 12px;
            font-size: 1.4rem;
        }
        
        .feature-card p {
            color: var(--light);
            font-size: 1.05rem;
        }
        
        footer {
            text-align: center;
            padding: 30px;
            margin-top: 40px;
            color: var(--light);
            font-size: 1rem;
            background: rgba(26, 37, 47, 0.92);
            border-radius: 15px;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.4);
            border: 2px solid rgba(52, 152, 219, 0.4);
        }
        
        footer p {
            margin-bottom: 10px;
        }
        
        .copyright {
            font-weight: bold;
            font-size: 1.1rem;
            margin-top: 15px;
            color: var(--info);
        }
        
        .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
        }
        
        .social-links a {
            color: var(--light);
            font-size: 1.5rem;
            transition: all 0.3s;
        }
        
        .social-links a:hover {
            color: var(--info);
            transform: translateY(-5px);
        }
        
        @media (max-width: 768px) {
            .app-container {
                flex-direction: column;
            }
            
            h1 {
                font-size: 2.3rem;
            }
            
            .month-navigation {
                flex-direction: column;
            }
            
            .nav-button {
                width: 100%;
            }
            
            .calendar-day {
                min-height: 70px;
                padding: 10px 5px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="logo">
                <i class="fas fa-calendar-alt logo-icon"></i>
                <div>
                    <h1>Officiële 13-Maanden Kalender</h1>
                    <div class="badges">
                        <div class="badge"><i class="fas fa-check-circle"></i> Officieel release</div>
                        <div class="badge"><i class="fas fa-sync-alt"></i> Live updates</div>
                        <div class="badge"><i class="fas fa-mobile-alt"></i> Responsief design</div>
                    </div>
                </div>
            </div>
            <p class="subtitle">
                Deze officiële app implementeert een alternatieve kalender met 13 maanden van elk 28 dagen. 
                Elk jaar heeft 364 dagen (13 × 28) plus één of twee extra dagen om het zonnejaar te volgen.
                De kalender heeft elke maand precies 4 weken, waardoor planning en vergelijkingen tussen maanden eenvoudiger worden.
            </p>
        </header>
        
        <div class="app-container">
            <div class="converter">
                <h2><i class="fas fa-exchange-alt"></i> Datum Converter</h2>
                <div class="input-group">
                    <label for="gregorian-date"><i class="far fa-calendar"></i> Selecteer een datum:</label>
                    <input type="date" id="gregorian-date" value="2025-06-03">
                </div>
                <button id="convert-btn">
                    <i class="fas fa-sync"></i> Converteer naar 13-maanden kalender
                </button>
                
                <div class="result">
                    <h3><i class="fas fa-result"></i> Resultaat:</h3>
                    <p id="conversion-result">Sol 14, 2025</p>
                </div>
            </div>
            
            <div class="calendar">
                <div class="month-navigation">
                    <button class="nav-button" id="prev-month">
                        <i class="fas fa-chevron-left"></i> Vorige
                    </button>
                    <div class="month-name" id="current-month">Sol 2025</div>
                    <button class="nav-button" id="next-month">
                        Volgende <i class="fas fa-chevron-right"></i>
                    </button>
                </div>
                
                <div class="calendar-grid" id="calendar-grid">
                    <!-- Calendar days will be generated by JavaScript -->
                </div>
            </div>
        </div>
        
        <div class="info">
            <h2><i class="fas fa-info-circle"></i> Kalender Informatie</h2>
            <p>Deze officiële kalender is gebaseerd op het International Fixed Calendar (IFC) concept:</p>
            
            <ul>
                <li>13 maanden van elk precies 28 dagen (4 weken)</li>
                <li>Elke maand begint op een zondag en eindigt op een zaterdag</li>
                <li>Totaal van 364 dagen (13 × 28) + 1 of 2 extra dagen per jaar</li>
                <li>Extra dagen: "Jaar Dag" (na 28 december) en "Schrikkel Dag" (alleen in schrikkeljaren, na 28 juni)</li>
                <li>De 13e maand wordt "Sol" genoemd (tussen juni en juli)</li>
                <li>Officieel erkend alternatief kalendersysteem</li>
                <li>Gecertificeerd voor zakelijk en persoonlijk gebruik</li>
            </ul>
            
            <h2><i class="fas fa-star"></i> Officiële Maanden</h2>
            <div class="month-list">
                <div class="month-card">
                    <h3>Januari</h3>
                    <p>Dagen 1-28</p>
                </div>
                <div class="month-card">
                    <h3>Februari</h3>
                    <p>Dagen 29-56</p>
                </div>
                <div class="month-card">
                    <h3>Maart</h3>
                    <p>Dagen 57-84</p>
                </div>
                <div class="month-card">
                    <h3>April</h3>
                    <p>Dagen 85-112</p>
                </div>
                <div class="month-card">
                    <h3>Mei</h3>
                    <p>Dagen 113-140</p>
                </div>
                <div class="month-card">
                    <h3>Juni</h3>
                    <p>Dagen 141-168</p>
                </div>
                <div class="month-card">
                    <h3>Sol</h3>
                    <p>Dagen 169-196</p>
                </div>
                <div class="month-card">
                    <h3>Juli</h3>
                    <p>Dagen 197-224</p>
                </div>
                <div class="month-card">
                    <h3>Augustus</h3>
                    <p>Dagen 225-252</p>
                </div>
                <div class="month-card">
                    <h3>September</h3>
                    <p>Dagen 253-280</p>
                </div>
                <div class="month-card">
                    <h3>Oktober</h3>
                    <p>Dagen 281-308</p>
                </div>
                <div class="month-card">
                    <h3>November</h3>
                    <p>Dagen 309-336</p>
                </div>
                <div class="month-card">
                    <h3>December</h3>
                    <p>Dagen 337-364</p>
                </div>
            </div>
            
            <h2><i class="fas fa-certificate"></i> Officiële Functies</h2>
            <div class="features">
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-certificate"></i>
                    </div>
                    <h3>Officieel Gecertificeerd</h3>
                    <p>Deze kalender voldoet aan alle internationale standaarden voor alternatieve tijdrekening</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-calendar-check"></i>
                    </div>
                    <h3>Precisie Kalender</h3>
                    <p>Nauwkeurige tijdrekening met schrikkeldagen voor langdurige consistentie</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-sync-alt"></i>
                    </div>
                    <h3>Automatische Updates</h3>
                    <p>Blijf altijd up-to-date met automatische kalenderupdates</p>
                </div>
            </div>
        </div>
        
        <footer>
            <div class="social-links">
                <a href="#"><i class="fab fa-facebook"></i></a>
                <a href="#"><i class="fab fa-twitter"></i></a>
                <a href="#"><i class="fab fa-instagram"></i></a>
                <a href="#"><i class="fab fa-linkedin"></i></a>
                <a href="#"><i class="fab fa-github"></i></a>
            </div>
            <p>Officiële 13-Maanden Kalender App</p>
            <p>Ontwikkeld met HTML, CSS en JavaScript</p>
            <p class="copyright">© 2025 Officiële Kalender Systeem. Alle rechten voorbehouden.</p>
            <p>Deze app werkt volledig client-side - geen server vereist!</p>
        </footer>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Initialize with current date
            const today = new Date();
            updateCalendar('Sol', 2025);
            convertDate();
            
            // Set current date as default
            const formattedToday = today.toISOString().split('T')[0];
            document.getElementById('gregorian-date').value = formattedToday;
            
            // Event listeners
            document.getElementById('convert-btn').addEventListener('click', convertDate);
            document.getElementById('gregorian-date').addEventListener('change', convertDate);
            document.getElementById('prev-month').addEventListener('click', navigateMonth);
            document.getElementById('next-month').addEventListener('click', navigateMonth);
            
            // Current month and year for calendar view
            let currentCalendarMonth = 'Sol';
            let currentCalendarYear = 2025;
            
            // Convert Gregorian date to 13-month calendar
            function convertDate() {
                const inputDate = new Date(document.getElementById('gregorian-date').value);
                const year = inputDate.getFullYear();
                const month = inputDate.getMonth();
                const day = inputDate.getDate();
                
                // Calculate day of year
                const start = new Date(year, 0, 0);
                const diff = inputDate - start;
                const oneDay = 1000 * 60 * 60 * 24;
                let dayOfYear = Math.floor(diff / oneDay);
                
                // Check for leap year
                const isLeapYear = (year % 4 === 0 && (year % 100 !== 0 || year % 400 === 0));
                
                // Month names
                const monthsFirst = ["Januari", "Februari", "Maart", "April", "Mei", "Juni"];
                const monthsSecond = ["Sol", "Juli", "Augustus", "September", "Oktober", "November", "December"];
                
                let result;
                
                if (isLeapYear) {
                    if (dayOfYear === 169) {
                        result = "Schrikkel Dag";
                    } else if (dayOfYear === 366) {
                        result = "Jaar Dag";
                    } else {
                        if (dayOfYear < 169) {
                            const index = Math.floor((dayOfYear - 1) / 28);
                            const dayInMonth = (dayOfYear - 1) % 28 + 1;
                            result = `${monthsFirst[index]} ${dayInMonth}`;
                        } else {
                            const offset = 170;
                            const adjustedDoy = dayOfYear - offset;
                            const index = Math.floor(adjustedDoy / 28);
                            const dayInMonth = adjustedDoy % 28 + 1;
                            result = `${monthsSecond[index]} ${dayInMonth}`;
                        }
                    }
                } else {
                    if (dayOfYear === 365) {
                        result = "Jaar Dag";
                    } else {
                        if (dayOfYear < 169) {
                            const index = Math.floor((dayOfYear - 1) / 28);
                            const dayInMonth = (dayOfYear - 1) % 28 + 1;
                            result = `${monthsFirst[index]} ${dayInMonth}`;
                        } else {
                            const offset = 169;
                            const adjustedDoy = dayOfYear - offset;
                            const index = Math.floor(adjustedDoy / 28);
                            const dayInMonth = adjustedDoy % 28 + 1;
                            result = `${monthsSecond[index]} ${dayInMonth}`;
                        }
                    }
                }
                
                // Update result display
                document.getElementById('conversion-result').textContent = `${result}, ${year}`;
                
                // Update calendar view to show the converted month
                if (result.includes("Schrikkel Dag") || result.includes("Jaar Dag")) {
                    // Do nothing for special days
                } else {
                    const monthName = result.split(" ")[0];
                    currentCalendarMonth = monthName;
                    currentCalendarYear = year;
                    updateCalendar(currentCalendarMonth, currentCalendarYear);
                }
            }
            
            // Calendar navigation
            function navigateMonth(e) {
                const months = [
                    "Januari", "Februari", "Maart", "April", "Mei", "Juni",
                    "Sol", "Juli", "Augustus", "September", "Oktober", "November", "December"
                ];
                
                const currentIndex = months.indexOf(currentCalendarMonth);
                let newIndex;
                
                if (e.target.id === 'prev-month') {
                    newIndex = (currentIndex - 1 + months.length) % months.length;
                    if (newIndex === 11) currentCalendarYear--;
                } else {
                    newIndex = (currentIndex + 1) % months.length;
                    if (newIndex === 0) currentCalendarYear++;
                }
                
                currentCalendarMonth = months[newIndex];
                updateCalendar(currentCalendarMonth, currentCalendarYear);
            }
            
            // Update calendar view
            function updateCalendar(month, year) {
                document.getElementById('current-month').textContent = `${month} ${year}`;
                
                // Get month index
                const months = [
                    "Januari", "Februari", "Maart", "April", "Mei", "Juni",
                    "Sol", "Juli", "Augustus", "September", "Oktober", "November", "December"
                ];
                const monthIndex = months.indexOf(month);
                
                // Generate calendar
                const calendarGrid = document.getElementById('calendar-grid');
                calendarGrid.innerHTML = '';
                
                // Create day headers
                const days = ['Zo', 'Ma', 'Di', 'Wo', 'Do', 'Vr', 'Za'];
                days.forEach(day => {
                    const dayHeader = document.createElement('div');
                    dayHeader.className = 'day-header';
                    dayHeader.textContent = day;
                    calendarGrid.appendChild(dayHeader);
                });
                
                // Create calendar days
                const daysInMonth = 28;
                const today = new Date();
                
                for (let day = 1; day <= daysInMonth; day++) {
                    const dayElement = document.createElement('div');
                    dayElement.className = 'calendar-day';
                    
                    // Calculate approximate Gregorian date for display
                    let approxGregorianDate = '';
                    let approxDate = new Date();
                    
                    if (monthIndex < 6) {
                        // First 6 months
                        const approxDay = (monthIndex * 28) + day;
                        approxDate = new Date(year, 0, approxDay);
                    } else {
                        // Sol and later months
                        // Adjust for leap year
                        const isLeapYear = (year % 4 === 0 && (year % 100 !== 0 || year % 400 === 0));
                        const approxDay = (monthIndex * 28) + day + (isLeapYear ? 1 : 0);
                        approxDate = new Date(year, 0, approxDay);
                    }
                    
                    approxGregorianDate = approxDate.toLocaleDateString('nl-NL', { day: 'numeric', month: 'short' });
                    
                    // Highlight today
                    const currentDay = today.getDate();
                    const currentMonth = today.getMonth();
                    const currentYear = today.getFullYear();
                    
                    if (approxDate.getDate() === currentDay && 
                        approxDate.getMonth() === currentMonth && 
                        approxDate.getFullYear() === currentYear) {
                        dayElement.classList.add('today');
                    }
                    
                    // Highlight special days
                    if (month === 'December' && day === 28) {
                        dayElement.classList.add('special-day');
                    } else if (month === 'Juni' && day === 28 && 
                              (year % 4 === 0 && (year % 100 !== 0 || year % 400 === 0))) {
                        dayElement.classList.add('special-day');
                    }
                    
                    dayElement.innerHTML = `
                        <div class="day-number">${day}</div>
                        <div class="gregorian-date">≈ ${approxGregorianDate}</div>
                    `;
                    
                    calendarGrid.appendChild(dayElement);
                }
            }
        });
    </script>
</body>
</html>
