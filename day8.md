<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Environmental Health Analyzer</title>
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Chart.js -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.0/dist/chart.umd.min.js"></script>
    
    <!-- Lucide Icons -->
    <script src="https://cdn.jsdelivr.net/npm/lucide@latest"></script>
    
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        :root {
            --primary: #1e7e34;
            --primary-light: #22c55e;
            --primary-dark: #15803d;
            --secondary: #0f172a;
            --accent: #f59e0b;
            --success: #10b981;
            --warning: #f97316;
            --danger: #ef4444;
        }
        
        html {
            scroll-behavior: smooth;
        }
        
        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
            transition: background-color 0.3s ease, color 0.3s ease;
        }
        
        body.light-mode {
            background-color: #f8fafc;
            color: #1e293b;
        }
        
        body.dark-mode {
            background-color: #0f172a;
            color: #e2e8f0;
        }
        
        .card {
            border-radius: 12px;
            transition: all 0.3s ease;
            backdrop-filter: blur(8px);
        }
        
        .card:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
        }
        
        .light-mode .card {
            background: white;
            border: 1px solid rgba(30, 126, 52, 0.1);
        }
        
        .dark-mode .card {
            background: rgba(15, 23, 42, 0.8);
            border: 1px solid rgba(34, 197, 94, 0.2);
        }
        
        .metric-card {
            position: relative;
            overflow: hidden;
        }
        
        .metric-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, var(--primary), var(--primary-light));
        }
        
        .risk-indicator {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            display: inline-block;
            animation: pulse 2s infinite;
        }
        
        .risk-safe {
            background-color: var(--success);
        }
        
        .risk-moderate {
            background-color: var(--warning);
        }
        
        .risk-hazardous {
            background-color: var(--danger);
        }
        
        @keyframes pulse {
            0%, 100% {
                opacity: 1;
            }
            50% {
                opacity: 0.7;
            }
        }
        
        .filter-btn {
            transition: all 0.3s ease;
            cursor: pointer;
        }
        
        .filter-btn.active {
            background: linear-gradient(135deg, var(--primary), var(--primary-light));
            color: white;
            box-shadow: 0 4px 12px rgba(30, 126, 52, 0.3);
        }
        
        .light-mode .filter-btn {
            background: #f1f5f9;
            color: #1e293b;
            border: 1px solid #cbd5e1;
        }
        
        .dark-mode .filter-btn {
            background: #1e293b;
            color: #e2e8f0;
            border: 1px solid #334155;
        }
        
        .sidebar {
            transition: all 0.3s ease;
        }
        
        .light-mode .sidebar {
            background: linear-gradient(135deg, #ffffff 0%, #f0fdf4 100%);
            border-right: 1px solid rgba(30, 126, 52, 0.1);
        }
        
        .dark-mode .sidebar {
            background: linear-gradient(135deg, #1e293b 0%, #0f172a 100%);
            border-right: 1px solid rgba(34, 197, 94, 0.1);
        }
        
        .mode-toggle {
            cursor: pointer;
            transition: transform 0.3s ease;
        }
        
        .mode-toggle:hover {
            transform: rotate(20deg);
        }
        
        .header-gradient {
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-light) 100%);
        }
        
        .chart-container {
            position: relative;
            height: 300px;
            margin-bottom: 20px;
        }
        
        .load-animation {
            animation: slideInUp 0.6s ease-out;
        }
        
        @keyframes slideInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        .stagger-item {
            animation: slideInUp 0.6s ease-out;
        }
        
        .stagger-item:nth-child(1) { animation-delay: 0.1s; }
        .stagger-item:nth-child(2) { animation-delay: 0.2s; }
        .stagger-item:nth-child(3) { animation-delay: 0.3s; }
        .stagger-item:nth-child(4) { animation-delay: 0.4s; }
        
        .stat-label {
            font-size: 0.875rem;
            opacity: 0.8;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }
        
        .stat-value {
            font-size: 2rem;
            font-weight: 700;
            line-height: 1;
            margin: 0.5rem 0;
        }
        
        .scroll-bar {
            scrollbar-width: thin;
        }
        
        .scroll-bar::-webkit-scrollbar {
            width: 6px;
        }
        
        .scroll-bar::-webkit-scrollbar-track {
            background: transparent;
        }
        
        .scroll-bar::-webkit-scrollbar-thumb {
            background: rgba(34, 197, 94, 0.3);
            border-radius: 3px;
        }
        
        .scroll-bar::-webkit-scrollbar-thumb:hover {
            background: rgba(34, 197, 94, 0.5);
        }
    </style>
</head>
<body class="light-mode scroll-bar">
    <div class="flex h-screen">
        <!-- Sidebar -->
        <aside class="sidebar w-72 border-r p-6 overflow-y-auto hidden md:flex md:flex-col">
            <div class="flex items-center justify-between mb-8">
                <div class="flex items-center gap-3">
                    <div class="w-10 h-10 bg-gradient-to-br from-green-400 to-green-600 rounded-lg flex items-center justify-center">
                        <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"></path>
                        </svg>
                    </div>
                    <div>
                        <h1 class="font-bold text-lg">EcoHealth</h1>
                        <p class="text-xs opacity-60">Analytics</p>
                    </div>
                </div>
                <button id="modeToggle" class="mode-toggle p-2 hover:bg-green-100 dark-mode:hover:bg-slate-700 rounded-lg transition">
                    <svg id="sunIcon" class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24" style="display: none;">
                        <circle cx="12" cy="12" r="5"/><line x1="12" y1="1" x2="12" y2="3"/><line x1="12" y1="21" x2="12" y2="23"/><line x1="4.22" y1="4.22" x2="5.64" y2="5.64"/><line x1="18.36" y1="18.36" x2="19.78" y2="19.78"/><line x1="1" y1="12" x2="3" y2="12"/><line x1="21" y1="12" x2="23" y2="12"/><line x1="4.22" y1="19.78" x2="5.64" y2="18.36"/><line x1="18.36" y1="5.64" x2="19.78" y2="4.22"/>
                    </svg>
                    <svg id="moonIcon" class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                        <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/>
                    </svg>
                </button>
            </div>
            
            <!-- Filters Section -->
            <div class="space-y-6">
                <div>
                    <label class="text-sm font-semibold opacity-70 uppercase tracking-wide">Region</label>
                    <div class="mt-3 space-y-2">
                        <button class="filter-btn w-full py-2 px-3 rounded-lg text-sm font-medium active" data-filter="region" data-value="all">All Regions</button>
                        <button class="filter-btn w-full py-2 px-3 rounded-lg text-sm font-medium" data-filter="region" data-value="north">North</button>
                        <button class="filter-btn w-full py-2 px-3 rounded-lg text-sm font-medium" data-filter="region" data-value="south">South</button>
                        <button class="filter-btn w-full py-2 px-3 rounded-lg text-sm font-medium" data-filter="region" data-value="east">East</button>
                        <button class="filter-btn w-full py-2 px-3 rounded-lg text-sm font-medium" data-filter="region" data-value="west">West</button>
                        <button class="filter-btn w-full py-2 px-3 rounded-lg text-sm font-medium" data-filter="region" data-value="urban">Urban</button>
                        <button class="filter-btn w-full py-2 px-3 rounded-lg text-sm font-medium" data-filter="region" data-value="rural">Rural</button>
                    </div>
                </div>
                
                <div class="h-px opacity-20"></div>
                
                <div>
                    <label class="text-sm font-semibold opacity-70 uppercase tracking-wide">Pollutant Type</label>
                    <div class="mt-3 space-y-2">
                        <button class="filter-btn w-full py-2 px-3 rounded-lg text-sm font-medium active" data-filter="pollutant" data-value="all">All Pollutants</button>
                        <button class="filter-btn w-full py-2 px-3 rounded-lg text-sm font-medium" data-filter="pollutant" data-value="PM2.5">PM2.5</button>
                        <button class="filter-btn w-full py-2 px-3 rounded-lg text-sm font-medium" data-filter="pollutant" data-value="NO2">NO₂</button>
                        <button class="filter-btn w-full py-2 px-3 rounded-lg text-sm font-medium" data-filter="pollutant" data-value="Lead">Lead</button>
                        <button class="filter-btn w-full py-2 px-3 rounded-lg text-sm font-medium" data-filter="pollutant" data-value="WaterContaminants">Water Contaminants</button>
                    </div>
                </div>
                
                <div class="h-px opacity-20"></div>
                
                <div>
                    <label class="text-sm font-semibold opacity-70 uppercase tracking-wide">Year</label>
                    <div class="mt-3">
                        <select id="yearFilter" class="w-full py-2 px-3 rounded-lg text-sm font-medium filter-btn border focus:outline-none focus:ring-2 focus:ring-green-500">
                            <option value="all">All Years</option>
                            <option value="2021">2021</option>
                            <option value="2022">2022</option>
                            <option value="2023">2023</option>
                            <option value="2024">2024</option>
                        </select>
                    </div>
                </div>
                
                <button id="resetFilters" class="w-full mt-8 py-2 px-4 bg-gradient-to-r from-green-500 to-green-600 text-white rounded-lg font-medium text-sm hover:from-green-600 hover:to-green-700 transition transform hover:scale-105">
                    Reset Filters
                </button>
            </div>
        </aside>
        
        <!-- Mobile Header -->
        <div class="md:hidden fixed top-0 left-0 right-0 h-16 header-gradient text-white flex items-center justify-between px-4 z-50">
            <div class="flex items-center gap-2">
                <div class="w-8 h-8 bg-white rounded-lg flex items-center justify-center">
                    <svg class="w-5 h-5 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"></path>
                    </svg>
                </div>
                <h1 class="font-bold">EcoHealth Analytics</h1>
            </div>
            <button id="mobileToggleMode" class="mode-toggle p-2">
                <svg id="mobileIcon" class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                    <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/>
                </svg>
            </button>
        </div>
        
        <!-- Main Content -->
        <main class="flex-1 overflow-y-auto scroll-bar pt-20 md:pt-0">
            <div class="p-4 md:p-8 max-w-7xl">
                <!-- Page Header -->
                <div class="mb-8 stagger-item">
                    <h2 class="text-3xl font-bold mb-2">Environmental Health Dashboard</h2>
                    <p class="opacity-60">Real-time monitoring and analysis of environmental health metrics across regions</p>
                </div>
                
                <!-- KPI Cards -->
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4 mb-8">
                    <div class="card metric-card p-6 stagger-item">
                        <div class="flex items-start justify-between mb-4">
                            <div class="stat-label">Average AQI</div>
                            <div class="risk-indicator risk-moderate"></div>
                        </div>
                        <div class="stat-value text-warning" id="avgAQI">0</div>
                        <p class="text-xs opacity-60">Moderate air quality</p>
                    </div>
                    
                    <div class="card metric-card p-6 stagger-item">
                        <div class="flex items-start justify-between mb-4">
                            <div class="stat-label">Water Safety</div>
                            <div class="risk-indicator risk-safe"></div>
                        </div>
                        <div class="stat-value text-success" id="waterSafety">0%</div>
                        <p class="text-xs opacity-60">Tested locations</p>
                    </div>
                    
                    <div class="card metric-card p-6 stagger-item">
                        <div class="flex items-start justify-between mb-4">
                            <div class="stat-label">Health Alerts</div>
                            <div class="risk-indicator risk-hazardous"></div>
                        </div>
                        <div class="stat-value text-danger" id="healthAlerts">0</div>
                        <p class="text-xs opacity-60">Active warnings</p>
                    </div>
                    
                    <div class="card metric-card p-6 stagger-item">
                        <div class="flex items-start justify-between mb-4">
                            <div class="stat-label">Affected Population</div>
                            <span class="text-xs bg-accent bg-opacity-20 text-accent px-2 py-1 rounded">HIGH</span>
                        </div>
                        <div class="stat-value text-accent" id="affectedPop">0</div>
                        <p class="text-xs opacity-60">Estimated people</p>
                    </div>
                </div>
                
                <!-- Charts Grid -->
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-6 mb-8">
                    <!-- AQI Trends Chart -->
                    <div class="card p-6 stagger-item">
                        <h3 class="text-lg font-semibold mb-4">AQI Trends Over Time</h3>
                        <div class="chart-container">
                            <canvas id="aqiChart"></canvas>
                        </div>
                    </div>
                    
                    <!-- Pollutant Comparison Chart -->
                    <div class="card p-6 stagger-item">
                        <h3 class="text-lg font-semibold mb-4">Pollutant Levels by Region</h3>
                        <div class="chart-container">
                            <canvas id="pollutantChart"></canvas>
                        </div>
                    </div>
                </div>
                
                <!-- Bottom Row Charts -->
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-6 mb-8">
                    <!-- Health Risk Distribution -->
                    <div class="card p-6 stagger-item">
                        <h3 class="text-lg font-semibold mb-4">Health Risk Distribution</h3>
                        <div class="chart-container">
                            <canvas id="healthRiskChart"></canvas>
                        </div>
                    </div>
                    
                    <!-- Regional Comparison -->
                    <div class="card p-6 stagger-item">
                        <h3 class="text-lg font-semibold mb-4">Regional Air Quality Index</h3>
                        <div class="chart-container">
                            <canvas id="regionalAQIChart"></canvas>
                        </div>
                    </div>
                </div>
                
                <!-- Data Table -->
                <div class="card p-6 stagger-item">
                    <h3 class="text-lg font-semibold mb-4">Recent Measurements</h3>
                    <div class="overflow-x-auto">
                        <table class="w-full text-sm">
                            <thead>
                                <tr class="border-b opacity-50">
                                    <th class="text-left py-3 px-4 font-semibold">Location</th>
                                    <th class="text-left py-3 px-4 font-semibold">Pollutant</th>
                                    <th class="text-left py-3 px-4 font-semibold">Level (μg/m³)</th>
                                    <th class="text-left py-3 px-4 font-semibold">AQI</th>
                                    <th class="text-left py-3 px-4 font-semibold">Status</th>
                                </tr>
                            </thead>
                            <tbody id="dataTable">
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </main>
    </div>
    
    <script>
        // ============================================
        // MOCK DATA
        // ============================================
        const mockData = {
            regions: ['north', 'south', 'east', 'west', 'urban', 'rural'],
            pollutants: ['PM2.5', 'NO2', 'Lead', 'WaterContaminants'],
            years: [2021, 2022, 2023, 2024],
            
            // Time series data for AQI trends
            aqiTrends: {
                labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
                data: {
                    all: [85, 78, 72, 65, 58, 52, 48, 51, 62, 71, 82, 88],
                    north: [92, 85, 78, 70, 62, 56, 52, 55, 68, 78, 88, 95],
                    south: [75, 68, 62, 55, 48, 42, 38, 41, 52, 62, 75, 82],
                    east: [88, 82, 75, 68, 60, 54, 50, 53, 65, 75, 85, 92],
                    west: [78, 72, 65, 58, 50, 44, 40, 43, 55, 65, 78, 85],
                    urban: [95, 88, 82, 75, 68, 62, 58, 61, 72, 82, 92, 98],
                    rural: [65, 58, 52, 45, 38, 32, 28, 31, 42, 52, 65, 72]
                }
            },
            
            // Pollutant levels by region
            pollutantLevels: {
                north: { 'PM2.5': 85, 'NO2': 72, 'Lead': 25, 'WaterContaminants': 35 },
                south: { 'PM2.5': 55, 'NO2': 42, 'Lead': 15, 'WaterContaminants': 20 },
      