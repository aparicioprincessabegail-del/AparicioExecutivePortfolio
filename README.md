<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Abby Aparicio - Portfolio Dashboard</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        navy: {
                            50: '#F4F7FA',
                            100: '#E1E9F0',
                            200: '#C2D2E1',
                            300: '#9BB8D0',
                            400: '#6E96BA',
                            500: '#4D7AA3',
                            600: '#345E85',
                            700: '#1B3B5C',
                            800: '#0E243A',
                            900: '#06101B'
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif']
                    }
                }
            }
        };
    </script>
    <!-- Google Fonts (Inter) -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght=300;400;500;600;700;800&display=swap" rel="stylesheet">
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #F8FAFC;
        }
        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #F1F5F9;
        }
        ::-webkit-scrollbar-thumb {
            background: #1B3B5C;
            border-radius: 3px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #0E243A;
        }
        
        /* Premium View Mode Controls */
        body:not(.edit-mode) .editor-only {
            display: none !important;
        }
        body.edit-mode .view-only {
            display: none !important;
        }

        /* Folder Tabs Navigation styling */
        .no-scrollbar::-webkit-scrollbar {
            display: none;
        }
        .no-scrollbar {
            -ms-overflow-style: none;
            scrollbar-width: none;
        }
        
        .folder-tab {
            transition: all 0.2s ease-in-out;
            border-top-left-radius: 0.75rem;
            border-top-right-radius: 0.75rem;
        }
    </style>
</head>
<body class="text-navy-900 overflow-x-hidden antialiased">

<script>
    // Premium starting data setup
    const defaultData = {
        hero: {
            name: "Abby Aparicio",
            headline: "Marketing & Events Manager",
            welcomeMessage: "I don't believe in creating work that simply gets done. I believe in creating work that gets remembered.\n\nAs a marketing strategist, content creator, and project manager, I specialize in turning ideas into experiences that connect, engage, and leave a lasting impact. From social media campaigns and brand storytelling to large-scale events and project execution, I bring together creativity, organization, and relentless attention to detail to make things happen.\n\nOver time, I've earned a reputation among clients, colleagues, and friends: if Abby worked on it, expect excellence. Not because perfection is the goal—but because I care deeply about delivering work that reflects the highest standard possible.\n\nI bring ideas to life. Then I make them impossible to ignore."
        },
        profile: {
            fullName: "Princess Abegail Aparicio",
            nickname: "Abby",
            address: "Cebu, Philippines",
            phone: "09271515517",
            email: "aparicioprincessabegail@gmail.com",
            linkedin: "https://www.linkedin.com/in/abbyaparicio/",
            skills: ["Events Management", "Project Management", "Execution & Strategy", "Content Strategy", "Graphics Editing", "Creative Direction", "Sales", "Insurance"],
            tools: ["MS Office", "Canva Pro", "CapCut", "Trello", "Meta Business Suite", "ChatGPT", "Gemini", "Zoom", "Outlook"],
            disc: {
                title: "DISC Personality Assessment",
                description: "Your unique sequence of scores characterizes you in a specific way. The positive impact you are likely to make on people is:\n\nYou have strong inner motivation to influence people and circumstances. You thrive on competitive situations and challenging assignments. The stresses and pressures of everyday work and life are unlikely to reduce your effectiveness and enthusiasm.",
                img: ""
            },
            iq: {
                title: "IQ Cognitive Evaluation - Score: 135",
                description: "Highly Gifted / Superior Intelligence. An IQ of 135 ranks in the top 1% of the global population. This indicates exceptional capacity for logical analysis, complex reasoning, structural problem-solving, and superior strategic blueprint design.",
                img: ""
            },
            english: {
                title: "English Level Proficiency (EF SET)",
                description: "C2 Proficient (Advanced/Mastery). Highly sophisticated writing fluency, bilingual communication adaptation, and mastery of dynamic strategic presentation contexts.",
                img: ""
            },
            mbti: {
                title: "MBTI Personality Profile - INFJ (The Advocate)",
                description: "Yep, im an introvert. But everyone would always argue because I never show that I am. I can be the life of the party when I need to.",
                img: ""
            }
        },
        education: [
            { level: "Elementary", school: "St. Catherine Academy", years: "2008 - 2014", field: "General Basic Education" },
            { level: "Junior High School", school: "Sisters of Mary Schools", years: "2014 - 2018", field: "High School Academic Track" },
            { level: "Senior High School", school: "National High School", years: "2018 - 2020", field: "Accountancy, Business, and Management (ABM)" },
            { level: "Bachelor's Degree", school: "State University of the Philippines", years: "2020 - 2024", field: "Bachelor of Science in Business Administration Major in Marketing Management" }
        ],
        work: {
            marketing: [
                { id: "wm_1", company: "Aura Creative Agency", position: "Lead Marketing Associate", startYear: "2024", endYear: "Present", details: "Spearheaded digital marketing campaigns for high-profile retail clients. Managed cross-functional design and copywriting teams, achieving an average 25% increase in lead generation and customer conversion rates." },
                { id: "wm_2", company: "OmniCorp Group", position: "Marketing Intern", startYear: "2023", endYear: "2024", details: "Coordinated local promotional events and assisted in generating monthly market research briefs." }
            ],
            socialMedia: {
                link: "https://www.linkedin.com/in/abbyaparicio/",
                industries: ["E-Commerce", "B2B SaaS", "Luxury Fashion", "Health & Wellness", "Real Estate"]
            },
            events: "Highly organized Events Specialist with hands-on experience orchestrating product launches, corporative seminars, and large-scale community initiatives. Known for impeccable timeline management, meticulous vendor coordination, and seamless real-time execution. I believe that an event is more than a gathering—it is a live, dynamic expression of a brand's narrative."
        },
        leadership: [
            { id: "lead_1", organization: "Junior Marketing Association", position: "Vice President for Internal Affairs", startYear: "2023", endYear: "2024" },
            { id: "lead_2", organization: "Youth Leaders Network", position: "Community Mobilizer", startYear: "2021", endYear: "2023" }
        ],
        honors: [
            { id: "hon_1", honor: "Magna Cum Laude", school: "State University of the Philippines", startYear: "2020", endYear: "2024" },
            { id: "hon_2", honor: "President's List Recipient", school: "State University of the Philippines", startYear: "2021", endYear: "2023" }
        ],
        awards: [
            { id: "aw_1", title: "National Marketing Pitch Winner", competition: "Inter-University Business Challenge", year: "2023" },
            { id: "aw_2", title: "Outstanding Youth Leader Award", competition: "Local Government Academic Awards", year: "2022" }
        ]
    };

    // Load data or safely fall back
    let state = JSON.parse(localStorage.getItem('princess_portfolio_data')) || defaultData;

    // Save and sync data
    function saveData() {
        localStorage.setItem('princess_portfolio_data', JSON.stringify(state));
    }
</script>

<div class="min-h-screen flex flex-col justify-between">
    <!-- Premium Top Nav -->
    <header class="bg-white border-b border-slate-200 sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex flex-col sm:flex-row items-center justify-between gap-4 py-4 sm:py-0">
            <!-- Branding -->
            <div class="flex items-center">
                <div>
                    <h1 class="text-lg font-bold tracking-tight text-navy-800" id="brand-name">Abby Aparicio</h1>
                    <p class="text-xs text-navy-500 font-semibold tracking-wider uppercase">Executive Interactive Portfolio</p>
                </div>
            </div>

            <!-- Mode Selector Slider -->
            <div class="flex items-center space-x-2 bg-slate-100 p-1.5 rounded-full border border-slate-200">
                <button onclick="setMode('view')" id="btn-view" class="px-4 py-1.5 rounded-full text-xs font-semibold tracking-wide transition-all flex items-center space-x-2">
                    <i class="fa-solid fa-eye text-xs"></i>
                    <span>Recruiter View</span>
                </button>
                <button onclick="setMode('edit')" id="btn-edit" class="px-4 py-1.5 rounded-full text-xs font-semibold tracking-wide transition-all flex items-center space-x-2">
                    <i class="fa-solid fa-pen-to-square text-xs"></i>
                    <span>Editor Mode</span>
                </button>
            </div>

            <!-- Global Actions -->
            <div class="flex items-center space-x-3">
                <button onclick="openShareModal()" class="bg-navy-800 hover:bg-navy-900 text-white text-xs font-bold uppercase tracking-wider px-4 py-2.5 rounded-lg transition-all flex items-center space-x-2 shadow-sm">
                    <i class="fa-solid fa-share-nodes"></i>
                    <span>Share Portfolio</span>
                </button>
            </div>
        </div>
    </header>

    <!-- Brand Hero Header Segment -->
    <section class="bg-gradient-to-b from-white to-slate-50/50 py-16 px-4 border-b border-slate-100 relative overflow-hidden">
        <div class="absolute inset-0 pointer-events-none opacity-20">
            <div class="absolute top-10 left-10 w-64 h-64 rounded-full border border-navy-200"></div>
            <div class="absolute bottom-10 right-10 w-96 h-96 rounded-full border border-navy-100"></div>
        </div>

        <div class="max-w-4xl mx-auto text-center relative z-10 space-y-6">
            <span class="text-xs font-bold text-navy-600 uppercase tracking-widest bg-navy-50 px-3.5 py-1.5 rounded-full">Executive Portfolio</span>
            
            <div class="space-y-2">
                <!-- Name Field -->
                <div>
                    <h2 class="text-4xl md:text-5xl lg:text-6xl font-black tracking-tight text-navy-800 view-only" id="hero-display-name">Abby Aparicio</h2>
                    <div class="editor-only max-w-md mx-auto">
                        <label class="block text-[10px] uppercase font-bold text-slate-400 mb-1">Name</label>
                        <input type="text" id="hero-input-name" oninput="updateHero('name', this.value)" class="w-full text-center px-3 py-2 border border-slate-200 rounded-lg text-sm font-semibold text-navy-800 bg-white">
                    </div>
                </div>

                <!-- Position Field -->
                <div>
                    <p class="text-lg md:text-xl font-light text-navy-500 tracking-wide italic max-w-2xl mx-auto view-only" id="hero-display-headline">Marketing & Events Manager</p>
                    <div class="editor-only max-w-md mx-auto mt-2">
                        <label class="block text-[10px] uppercase font-bold text-slate-400 mb-1">Position / Title</label>
                        <input type="text" id="hero-input-headline" oninput="updateHero('headline', this.value)" class="w-full text-center px-3 py-2 border border-slate-200 rounded-lg text-sm bg-white">
                    </div>
                </div>
            </div>

            <!-- Welcome Message Manifesto Container -->
            <div class="max-w-3xl mx-auto space-y-2 bg-white/70 backdrop-blur-md p-6 sm:p-8 rounded-2xl border border-slate-100 shadow-sm">
                <div class="view-only">
                    <p id="hero-display-welcome" class="text-slate-600 leading-relaxed font-normal text-sm sm:text-base text-justify whitespace-pre-line"></p>
                </div>
                <div class="editor-only text-left">
                    <label class="block text-[10px] uppercase font-bold text-slate-400 mb-2">Introduction Manifesto</label>
                    <textarea id="hero-input-welcome" rows="7" oninput="updateHero('welcomeMessage', this.value)" class="w-full px-3 py-2 border border-slate-200 rounded-lg text-sm bg-white focus:outline-none focus:ring-1 focus:ring-navy-600"></textarea>
                </div>
            </div>

            <!-- Location and Quick contacts Row -->
            <div class="flex flex-wrap justify-center gap-4 text-xs font-medium text-navy-500 pt-2">
                <span class="flex items-center gap-1.5"><i class="fa-solid fa-location-dot text-navy-400"></i> <span id="quick-address">Cebu, Philippines</span></span>
                <span class="h-4 w-px bg-slate-200 hidden sm:inline-block"></span>
                <span class="flex items-center gap-1.5"><i class="fa-solid fa-phone text-navy-400"></i> <span id="quick-phone">09271515517</span></span>
                <span class="h-4 w-px bg-slate-200 hidden sm:inline-block"></span>
                <span class="flex items-center gap-1.5"><i class="fa-solid fa-envelope text-navy-400"></i> <span id="quick-email">aparicioprincessabegail@gmail.com</span></span>
            </div>
        </div>
    </section>

    <!-- Main Content Panel Area -->
    <main class="flex-grow max-w-5xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-10">
        <!-- Dashboard Top Control Header -->
        <div class="flex flex-col sm:flex-row items-start sm:items-center justify-between mb-4 gap-2 px-1">
            <div class="flex items-center space-x-2">
                <span class="text-[10px] font-black uppercase tracking-widest bg-navy-800 text-white px-2.5 py-1 rounded">INDEX</span>
                <span class="text-xs text-navy-500 font-semibold">Select an index folder to inspect files</span>
            </div>
            <!-- Live Auto Indicator -->
            <div class="flex items-center space-x-2 bg-emerald-50 text-emerald-800 px-3 py-1 rounded-full border border-emerald-100 text-[10px] font-bold uppercase tracking-wider">
                <span class="w-1.5 h-1.5 bg-emerald-500 rounded-full animate-pulse"></span>
                <i class="fa-solid fa-cloud mr-0.5"></i> Autosaved Session
            </div>
        </div>

        <!-- Horizontal Folder tabs bar -->
        <div class="relative z-10 flex items-end overflow-x-auto no-scrollbar gap-1.5 px-2 -mb-[1px]" id="folder-tab-bar">
            <!-- Dynamic Folder Tabs populated by JavaScript -->
        </div>

        <!-- Unified Premium Content Card -->
        <div class="bg-white rounded-b-2xl rounded-tr-2xl border border-slate-200 p-6 sm:p-8 min-h-[520px] shadow-sm relative z-0">
            <!-- Active Tab Context Header -->
            <div class="flex items-center justify-between border-b border-slate-100 pb-4 mb-6">
                <div class="flex items-center space-x-3">
                    <div class="p-2 bg-navy-800 text-white rounded-lg" id="tab-meta-icon">
                        <i class="fa-solid fa-user"></i>
                    </div>
                    <h3 class="text-xl font-bold text-navy-800 animate-fade-in" id="tab-meta-title">Personal Profile</h3>
                </div>
                <div class="text-xs text-navy-500 font-bold uppercase tracking-wider bg-slate-50 px-3 py-1 rounded">
                    Folder Document: <span id="tab-meta-number">1</span>/6
                </div>
            </div>

            <!-- TAB CONTAINER WRAPPERS -->

            <!-- PANEL 1: PERSONAL PROFILE -->
            <div id="panel-content-1" class="panel-view space-y-8 hidden">
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                    <!-- Left Column: Contact and Skills -->
                    <div class="space-y-6">
                        <h4 class="text-xs font-bold uppercase tracking-wider text-navy-500 border-b pb-2">Primary Credentials</h4>
                        
                        <!-- Contact Fields Grid -->
                        <div class="space-y-3.5">
                            <!-- Full name -->
                            <div class="flex flex-col">
                                <span class="text-[10px] uppercase font-bold text-slate-400">Full Name</span>
                                <span class="text-sm font-semibold text-navy-800 view-only" id="prof-display-fullName"></span>
                                <input type="text" id="prof-input-fullName" oninput="updateProfile('fullName', this.value)" class="editor-only mt-1 px-3 py-1.5 text-xs border border-slate-200 rounded-lg bg-white">
                            </div>
                            <!-- Nickname -->
                            <div class="flex flex-col">
                                <span class="text-[10px] uppercase font-bold text-slate-400">Nickname</span>
                                <span class="text-sm font-semibold text-navy-800 view-only" id="prof-display-nickname"></span>
                                <input type="text" id="prof-input-nickname" oninput="updateProfile('nickname', this.value)" class="editor-only mt-1 px-3 py-1.5 text-xs border border-slate-200 rounded-lg bg-white">
                            </div>
                            <!-- Address -->
                            <div class="flex flex-col">
                                <span class="text-[10px] uppercase font-bold text-slate-400">Address Location</span>
                                <span class="text-sm font-semibold text-navy-800 view-only" id="prof-display-address"></span>
                                <input type="text" id="prof-input-address" oninput="updateProfile('address', this.value)" class="editor-only mt-1 px-3 py-1.5 text-xs border border-slate-200 rounded-lg bg-white">
                            </div>
                            <!-- Phone -->
                            <div class="flex flex-col">
                                <span class="text-[10px] uppercase font-bold text-slate-400">Phone Number</span>
                                <span class="text-sm font-semibold text-navy-800 view-only" id="prof-display-phone"></span>
                                <input type="text" id="prof-input-phone" oninput="updateProfile('phone', this.value)" class="editor-only mt-1 px-3 py-1.5 text-xs border border-slate-200 rounded-lg bg-white">
                            </div>
                            <!-- Email -->
                            <div class="flex flex-col">
                                <span class="text-[10px] uppercase font-bold text-slate-400">Email Address</span>
                                <span class="text-sm font-semibold text-navy-800 view-only" id="prof-display-email"></span>
                                <input type="email" id="prof-input-email" oninput="updateProfile('email', this.value)" class="editor-only mt-1 px-3 py-1.5 text-xs border border-slate-200 rounded-lg bg-white">
                            </div>
                            <!-- LinkedIn Linked Button -->
                            <div class="pt-2 flex flex-col gap-1.5">
                                <span class="text-[10px] uppercase font-bold text-slate-400">LinkedIn Profile Link</span>
                                <input type="text" id="prof-input-linkedin" oninput="updateProfile('linkedin', this.value)" class="editor-only px-3 py-1.5 text-xs border border-slate-200 rounded-lg bg-white mb-2">
                                <div>
                                    <a id="prof-display-linkedin" href="" target="_blank" class="inline-flex items-center space-x-2 bg-navy-800 hover:bg-navy-900 text-white text-xs font-bold uppercase tracking-wider px-4 py-2.5 rounded-lg shadow-sm transition-all">
                                        <i class="fa-brands fa-linkedin text-sm"></i>
                                        <span>Connect with me</span>
                                    </a>
                                </div>
                            </div>
                        </div>

                        <!-- Core Skills list dynamic block -->
                        <div class="pt-4 border-t border-slate-100 space-y-3">
                            <div class="flex items-center justify-between">
                                <span class="text-[10px] uppercase font-bold text-slate-400">Core Skillsets</span>
                                <button onclick="addSkill()" class="editor-only text-xs text-navy-700 font-bold hover:text-navy-900"><i class="fa-solid fa-plus mr-1"></i> Add Skill</button>
                            </div>
                            <div id="skills-list" class="flex flex-wrap gap-2">
                                <!-- Populated dynamically -->
                            </div>
                        </div>

                        <!-- Tools Proficiency dynamic block -->
                        <div class="pt-4 border-t border-slate-100 space-y-3">
                            <div class="flex items-center justify-between">
                                <span class="text-[10px] uppercase font-bold text-slate-400">Tools Proficiency</span>
                                <button onclick="addTool()" class="editor-only text-xs text-navy-700 font-bold hover:text-navy-900"><i class="fa-solid fa-plus mr-1"></i> Add Tool</button>
                            </div>
                            <div id="tools-list" class="flex flex-wrap gap-2">
                                <!-- Populated dynamically -->
                            </div>
                        </div>
                    </div>

                    <!-- Right Column: Professional Evaluation Scores -->
                    <div class="space-y-6">
                        <h4 class="text-xs font-bold uppercase tracking-wider text-navy-500 border-b pb-2">Cognitive & Personality Credentials</h4>
                        
                        <!-- Dynamic Evaluation Cards Grid -->
                        <div class="space-y-5">
                            
                            <!-- DISC -->
                            <div class="border border-slate-200 p-4 rounded-xl bg-white space-y-3">
                                <div class="flex items-center justify-between">
                                    <span class="text-xs font-bold text-navy-800 flex items-center gap-2">
                                        <i class="fa-solid fa-chart-pie text-navy-500"></i> DISC Personality Assessment
                                    </span>
                                    <div class="editor-only">
                                        <label class="cursor-pointer bg-slate-100 hover:bg-slate-200 px-2 py-1 rounded text-[10px] font-semibold text-navy-700">
                                            Upload Certificate
                                            <input type="file" accept="image/*" class="hidden" onchange="uploadImage('disc', this)">
                                        </label>
                                    </div>
                                </div>
                                <p id="disc-display-desc" class="text-xs text-slate-600 leading-relaxed text-justify whitespace-pre-line view-only"></p>
                                <textarea id="disc-input-desc" oninput="updateAssessment('disc', this.value)" class="editor-only w-full text-xs p-2 border border-slate-200 rounded" rows="3"></textarea>
                                
                                <!-- Optional image container -->
                                <div class="relative rounded-lg overflow-hidden border border-slate-100 bg-slate-50 min-h-[40px] flex items-center justify-center">
                                    <img id="disc-preview" class="max-h-48 w-full object-contain hidden" alt="DISC Result Certificate">
                                    <span id="disc-empty" class="text-[10px] text-slate-400 italic py-2">No certificate uploaded yet</span>
                                </div>
                            </div>

                            <!-- IQ -->
                            <div class="border border-slate-200 p-4 rounded-xl bg-white space-y-3">
                                <div class="flex items-center justify-between">
                                    <span class="text-xs font-bold text-navy-800 flex items-center gap-2">
                                        <i class="fa-solid fa-brain text-navy-500"></i> IQ Cognitive Evaluation
                                    </span>
                                    <div class="editor-only">
                                        <label class="cursor-pointer bg-slate-100 hover:bg-slate-200 px-2 py-1 rounded text-[10px] font-semibold text-navy-700">
                                            Upload Certificate
                                            <input type="file" accept="image/*" class="hidden" onchange="uploadImage('iq', this)">
                                        </label>
                                    </div>
                                </div>
                                <p id="iq-display-desc" class="text-xs text-slate-600 leading-relaxed text-justify whitespace-pre-line view-only"></p>
                                <textarea id="iq-input-desc" oninput="updateAssessment('iq', this.value)" class="editor-only w-full text-xs p-2 border border-slate-200 rounded" rows="3"></textarea>
                                
                                <div class="relative rounded-lg overflow-hidden border border-slate-100 bg-slate-50 min-h-[40px] flex items-center justify-center">
                                    <img id="iq-preview" class="max-h-48 w-full object-contain hidden" alt="IQ Score certificate">
                                    <span id="iq-empty" class="text-[10px] text-slate-400 italic py-2">No certificate uploaded yet</span>
                                </div>
                            </div>

                            <!-- English Level -->
                            <div class="border border-slate-200 p-4 rounded-xl bg-white space-y-3">
                                <div class="flex items-center justify-between">
                                    <span class="text-xs font-bold text-navy-800 flex items-center gap-2">
                                        <i class="fa-solid fa-language text-navy-500"></i> English Level Proficiency (EF SET)
                                    </span>
                                    <div class="editor-only">
                                        <label class="cursor-pointer bg-slate-100 hover:bg-slate-200 px-2 py-1 rounded text-[10px] font-semibold text-navy-700">
                                            Upload Certificate
                                            <input type="file" accept="image/*" class="hidden" onchange="uploadImage('english', this)">
                                        </label>
                                    </div>
                                </div>
                                <p id="english-display-desc" class="text-xs text-slate-600 leading-relaxed text-justify whitespace-pre-line view-only"></p>
                                <textarea id="english-input-desc" oninput="updateAssessment('english', this.value)" class="editor-only w-full text-xs p-2 border border-slate-200 rounded" rows="3"></textarea>
                                
                                <div class="relative rounded-lg overflow-hidden border border-slate-100 bg-slate-50 min-h-[40px] flex items-center justify-center">
                                    <img id="english-preview" class="max-h-48 w-full object-contain hidden" alt="English test certificate">
                                    <span id="english-empty" class="text-[10px] text-slate-400 italic py-2">No certificate uploaded yet</span>
                                </div>
                            </div>

                            <!-- MBTI Personality -->
                            <div class="border border-slate-200 p-4 rounded-xl bg-white space-y-3">
                                <div class="flex items-center justify-between">
                                    <span class="text-xs font-bold text-navy-800 flex items-center gap-2">
                                        <i class="fa-solid fa-mask text-navy-500"></i> MBTI Personality Profile - INFJ (The Advocate)
                                    </span>
                                    <div class="editor-only">
                                        <label class="cursor-pointer bg-slate-100 hover:bg-slate-200 px-2 py-1 rounded text-[10px] font-semibold text-navy-700">
                                            Upload Certificate
                                            <input type="file" accept="image/*" class="hidden" onchange="uploadImage('mbti', this)">
                                        </label>
                                    </div>
                                </div>
                                <p id="mbti-display-desc" class="text-xs text-slate-600 leading-relaxed text-justify whitespace-pre-line view-only"></p>
                                <textarea id="mbti-input-desc" oninput="updateAssessment('mbti', this.value)" class="editor-only w-full text-xs p-2 border border-slate-200 rounded" rows="3"></textarea>
                                
                                <div class="relative rounded-lg overflow-hidden border border-slate-100 bg-slate-50 min-h-[40px] flex items-center justify-center">
                                    <img id="mbti-preview" class="max-h-48 w-full object-contain hidden" alt="MBTI personality certificate">
                                    <span id="mbti-empty" class="text-[10px] text-slate-400 italic py-2">No certificate uploaded yet</span>
                                </div>
                            </div>

                        </div>
                    </div>
                </div>
            </div>

            <!-- PANEL 2: EDUCATION (LOCKED TO EXACTLY 4 HIGH-FIDELITY ITEMS) -->
            <div id="panel-content-2" class="panel-view space-y-8 hidden">
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6" id="education-render-grid">
                    <!-- Dynamic education blocks -->
                </div>
            </div>

            <!-- PANEL 3: WORK EXPERIENCES -->
            <div id="panel-content-3" class="panel-view space-y-8 hidden">
                
                <!-- Section 3A: Marketing & Sales -->
                <div class="space-y-4">
                    <div class="flex items-center justify-between border-b border-slate-100 pb-2">
                        <h4 class="text-sm font-bold uppercase tracking-wider text-navy-800 flex items-center gap-2">
                            <i class="fa-solid fa-chart-line text-navy-500"></i>
                            <span>Marketing & Sales Experiences</span>
                        </h4>
                        <button onclick="addMarketingWork()" class="editor-only bg-navy-800 text-white text-xs font-bold px-3 py-1.5 rounded-lg hover:bg-navy-900 transition-all">
                            <i class="fa-solid fa-plus mr-1"></i> Add Entry
                        </button>
                    </div>

                    <div id="work-marketing-container" class="space-y-4">
                        <!-- Dynamic sorted lists appear here -->
                    </div>
                </div>

                <!-- Section 3B: Social Media Management -->
                <div class="space-y-4 pt-6 border-t border-slate-100">
                    <h4 class="text-sm font-bold uppercase tracking-wider text-navy-800 flex items-center gap-2">
                        <i class="fa-solid fa-hashtag text-navy-500"></i>
                        <span>Social Media Management</span>
                    </h4>

                    <div class="bg-slate-50/50 border border-slate-200 p-6 rounded-xl space-y-4">
                        <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4">
                            <div>
                                <span class="text-[10px] uppercase font-bold text-slate-400">Campaign Showreel Portal</span>
                                <p class="text-xs text-slate-500 mt-0.5">Click the portfolio link to review client analytics, visual layouts, and content portfolios.</p>
                            </div>
                            <div class="flex flex-col gap-1.5">
                                <input type="text" id="sm-input-link" oninput="updateSMLink(this.value)" class="editor-only px-3 py-1.5 text-xs border border-slate-200 rounded-lg bg-white w-64" placeholder="Destination link">
                                <a id="sm-display-link" href="" target="_blank" class="inline-flex items-center space-x-2 bg-navy-800 hover:bg-navy-900 text-white text-xs font-bold uppercase tracking-wider px-5 py-2.5 rounded-lg shadow-sm">
                                    <i class="fa-solid fa-arrow-up-right-from-square"></i>
                                    <span>Launch Campaign Portfolio</span>
                                </a>
                            </div>
                        </div>

                        <!-- Industry Badges -->
                        <div class="space-y-2 pt-2">
                            <div class="flex items-center justify-between border-b pb-1.5">
                                <span class="text-[10px] uppercase font-bold text-slate-400">Industries Covered</span>
                                <div class="editor-only flex gap-1 items-center">
                                    <input type="text" id="sm-input-industry" class="px-2 py-1 text-xs border border-slate-200 rounded" placeholder="E.g. Logistics">
                                    <button onclick="addSMIndustry()" class="text-xs text-navy-700 font-bold hover:text-navy-900"><i class="fa-solid fa-plus"></i></button>
                                </div>
                            </div>
                            <div id="sm-industries-box" class="flex flex-wrap gap-2 pt-1">
                                <!-- Floating tags only - non clickable -->
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Section 3C: Events Management (Essay Format) -->
                <div class="space-y-4 pt-6 border-t border-slate-100">
                    <h4 class="text-sm font-bold uppercase tracking-wider text-navy-800 flex items-center gap-2">
                        <i class="fa-solid fa-calendar-check text-navy-500"></i>
                        <span>Events Management</span>
                    </h4>

                    <div class="bg-white border border-slate-200 p-6 rounded-xl">
                        <div class="view-only">
                            <p id="events-display-essay" class="text-slate-600 leading-relaxed font-normal text-sm sm:text-base text-justify whitespace-pre-line"></p>
                        </div>
                        <div class="editor-only space-y-2">
                            <label class="block text-[10px] uppercase font-bold text-slate-400">Narrative Essay Statement</label>
                            <textarea id="events-input-essay" rows="6" oninput="updateEventsEssay(this.value)" class="w-full p-3 text-xs border border-slate-200 rounded-lg bg-white focus:outline-none focus:ring-1 focus:ring-navy-600"></textarea>
                        </div>
                    </div>
                </div>

            </div>

            <!-- PANEL 4: LEADERSHIP EXPERIENCES -->
            <div id="panel-content-4" class="panel-view space-y-8 hidden">
                <div class="flex items-center justify-between border-b border-slate-100 pb-2">
                    <h4 class="text-sm font-bold uppercase tracking-wider text-navy-800 flex items-center gap-2">
                        <i class="fa-solid fa-handshake-angle text-navy-500"></i>
                        <span>Executive & Community Leadership History</span>
                    </h4>
                    <button onclick="addLeadership()" class="editor-only bg-navy-800 text-white text-xs font-bold px-3 py-1.5 rounded-lg hover:bg-navy-900 transition-all">
                        <i class="fa-solid fa-plus mr-1"></i> Add Entry
                    </button>
                </div>

                <div id="leadership-container" class="space-y-4">
                    <!-- Dynamic sorted items -->
                </div>
            </div>

            <!-- PANEL 5: ACADEMIC HONORS -->
            <div id="panel-content-5" class="panel-view space-y-8 hidden">
                <div class="flex items-center justify-between border-b border-slate-100 pb-2">
                    <h4 class="text-sm font-bold uppercase tracking-wider text-navy-800 flex items-center gap-2">
                        <i class="fa-solid fa-award text-navy-500"></i>
                        <span>Scholastic Distinctions & Academic Honors</span>
                    </h4>
                    <button onclick="addHonor()" class="editor-only bg-navy-800 text-white text-xs font-bold px-3 py-1.5 rounded-lg hover:bg-navy-900 transition-all">
                        <i class="fa-solid fa-plus mr-1"></i> Add Entry
                    </button>
                </div>

                <div id="honors-container" class="space-y-4">
                    <!-- Dynamic sorted items -->
                </div>
            </div>

            <!-- PANEL 6: AWARDS -->
            <div id="panel-content-6" class="panel-view space-y-8 hidden">
                <div class="flex items-center justify-between border-b border-slate-100 pb-2">
                    <h4 class="text-sm font-bold uppercase tracking-wider text-navy-800 flex items-center gap-2">
                        <i class="fa-solid fa-trophy text-navy-500"></i>
                        <span>Industry Competitions & Academic Awards</span>
                    </h4>
                    <button onclick="addAward()" class="editor-only bg-navy-800 text-white text-xs font-bold px-3 py-1.5 rounded-lg hover:bg-navy-900 transition-all">
                        <i class="fa-solid fa-plus mr-1"></i> Add Entry
                    </button>
                </div>

                <div id="awards-container" class="space-y-4">
                    <!-- Dynamic sorted items -->
                </div>
            </div>

        </div>
    </main>

    <!-- Brand Footer -->
    <footer class="bg-navy-900 text-slate-400 py-10 mt-16 border-t border-navy-800">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col md:flex-row items-center justify-between gap-6 text-center md:text-left">
            <div>
                <p class="text-white text-sm font-bold tracking-wide">Abby Aparicio</p>
                <p class="text-xs text-slate-500 mt-1">Marketing & Events Manager. All portfolios cached locally.</p>
            </div>
            <div class="text-xs text-slate-500">
                You may email me directly so we can discuss my services in detail.
            </div>
        </div>
    </footer>
</div>

<!-- EDITOR AUTHENTICATION MODAL -->
<div id="password-modal" class="hidden fixed inset-0 z-50 bg-navy-900/60 backdrop-blur-sm flex items-center justify-center p-4">
    <div class="bg-white rounded-2xl max-w-sm w-full p-6 shadow-xl border border-slate-200 space-y-4">
        <div class="flex items-center justify-between border-b pb-3">
            <h4 class="text-base font-bold text-navy-800 flex items-center gap-2">
                <i class="fa-solid fa-lock text-navy-500"></i>
                <span>Editor Authentication</span>
            </h4>
            <button onclick="closePasswordModal()" class="text-slate-400 hover:text-slate-600"><i class="fa-solid fa-circle-xmark text-lg"></i></button>
        </div>
        <p class="text-xs text-slate-500 leading-relaxed">Please enter your password to unlock the editor and update your records.</p>
        <div class="space-y-2">
            <input type="password" id="editor-password-input" class="w-full px-3 py-2 border border-slate-200 rounded-lg text-sm bg-white focus:outline-none focus:ring-1 focus:ring-navy-600" placeholder="••••••••••••" onkeydown="if(event.key === 'Enter') submitPassword()">
            <p id="password-error" class="text-[10px] text-rose-500 hidden font-semibold">Incorrect password. Access denied.</p>
        </div>
        <div class="flex items-center justify-end gap-2 pt-2">
            <button onclick="closePasswordModal()" class="px-4 py-2 border border-slate-200 hover:bg-slate-50 text-slate-500 text-xs font-semibold rounded-lg transition-all">Cancel</button>
            <button onclick="submitPassword()" class="bg-navy-800 hover:bg-navy-900 text-white text-xs font-bold uppercase tracking-wider px-5 py-2 rounded-lg transition-all shadow-sm">Unlock</button>
        </div>
    </div>
</div>

<!-- SHARE MODAL DIALOG -->
<div id="share-modal" class="hidden fixed inset-0 z-50 bg-navy-900/60 backdrop-blur-sm flex items-center justify-center p-4">
    <div class="bg-white rounded-2xl max-w-md w-full p-6 shadow-xl border border-slate-200 space-y-4">
        <div class="flex items-center justify-between border-b pb-3">
            <h4 class="text-base font-bold text-navy-800 flex items-center gap-2">
                <i class="fa-solid fa-share-nodes text-navy-500"></i>
                <span>Share Interactive Portfolio</span>
            </h4>
            <button onclick="closeShareModal()" class="text-slate-400 hover:text-slate-600"><i class="fa-solid fa-circle-xmark text-lg"></i></button>
        </div>
        <p class="text-xs text-slate-500 leading-relaxed">Copy this unique direct view link to present the locked recruiter view directly to prospective hiring managers.</p>
        <div class="bg-slate-50 p-3 rounded-lg border border-slate-200 flex items-center justify-between">
            <span id="shareable-link" class="text-xs text-navy-700 font-semibold truncate mr-2 select-all">https://abby-aparicio.portfolio.io/recruiter-view</span>
            <button onclick="copyLink()" class="bg-navy-800 text-white text-xs font-bold px-3.5 py-1.5 rounded hover:bg-navy-900 transition-all flex items-center gap-1">
                <i class="fa-regular fa-copy"></i>
                <span id="btn-copy-label">Copy</span>
            </button>
        </div>
    </div>
</div>

<!-- TOAST ALERTS SYSTEM -->
<div id="notification-toast" class="fixed bottom-6 right-6 z-50 transform translate-y-20 opacity-0 transition-all duration-300">
    <div class="bg-navy-900 text-white text-xs font-semibold px-4 py-3 rounded-xl shadow-lg border border-navy-800 flex items-center space-x-2.5">
        <span class="w-2 h-2 rounded-full bg-emerald-400"></span>
        <span id="notification-text">Saved to storage successfully</span>
    </div>
</div>

<!-- CORE APP ENGINE -->
<script>
    let activeTab = 1;
    let mode = 'view'; // default to recruiter presentation

    // Dynamic Tab Icons and metadata titles
    const tabData = {
        1: { icon: "fa-solid fa-user", title: "Personal Profile" },
        2: { icon: "fa-solid fa-graduation-cap", title: "Education (4 Levels)" },
        3: { icon: "fa-solid fa-briefcase", title: "Work Experience Categories" },
        4: { icon: "fa-solid fa-handshake-angle", title: "Leadership History" },
        5: { icon: "fa-solid fa-award", title: "Academic Honors" },
        6: { icon: "fa-solid fa-trophy", title: "Competition Awards" }
    };

    // Initialize systems on layout paint
    window.onload = function () {
        document.body.className = "bg-[#F8FAFC] text-navy-900 antialiased";
        renderTabsNav();
        hydrateView();
        applyMode('view'); // force display mode by default
    };

    // Mode Selector Controls
    function setMode(newMode) {
        if (newMode === 'edit') {
            openPasswordModal();
        } else {
            applyMode('view');
        }
    }

    function openPasswordModal() {
        document.getElementById('editor-password-input').value = '';
        document.getElementById('password-error').classList.add('hidden');
        document.getElementById('password-modal').classList.remove('hidden');
        setTimeout(() => {
            document.getElementById('editor-password-input').focus();
        }, 100);
    }

    function closePasswordModal() {
        document.getElementById('password-modal').classList.add('hidden');
    }

    function submitPassword() {
        const passwordInput = document.getElementById('editor-password-input').value;
        const errorText = document.getElementById('password-error');
        
        if (passwordInput === 'hiremeLord123!') {
            closePasswordModal();
            applyMode('edit');
        } else {
            errorText.classList.remove('hidden');
            document.getElementById('editor-password-input').value = '';
            showToast("Authentication failed. Incorrect password.");
        }
    }

    function applyMode(newMode) {
        mode = newMode;
        const bodyEl = document.body;
        const btnView = document.getElementById('btn-view');
        const btnEdit = document.getElementById('btn-edit');

        if (newMode === 'edit') {
            bodyEl.classList.add('edit-mode');
            btnEdit.className = "px-4 py-1.5 rounded-full text-xs font-bold tracking-wide bg-navy-800 text-white shadow-sm flex items-center space-x-2";
            btnView.className = "px-4 py-1.5 rounded-full text-xs font-bold tracking-wide text-slate-500 hover:text-navy-800 hover:bg-slate-200/50 flex items-center space-x-2";
            showToast("Editor Mode Active - Click to change details.");
        } else {
            bodyEl.classList.remove('edit-mode');
            btnView.className = "px-4 py-1.5 rounded-full text-xs font-bold tracking-wide bg-navy-800 text-white shadow-sm flex items-center space-x-2";
            btnEdit.className = "px-4 py-1.5 rounded-full text-xs font-bold tracking-wide text-slate-500 hover:text-navy-800 hover:bg-slate-200/50 flex items-center space-x-2";
            showToast("Recruiter Mode Active - Form inputs locked.");
        }
        renderActivePanel();
    }

    // Dynamic folder tab renderer
    function renderTabsNav() {
        const bar = document.getElementById('folder-tab-bar');
        bar.innerHTML = '';

        for (let i = 1; i <= 6; i++) {
            const tabMeta = tabData[i];
            const isActive = i === activeTab;
            
            const activeStyle = "bg-navy-800 text-white border-t border-l border-r border-navy-800 font-bold -mb-[1px] relative z-20 shadow-[0_-3px_8px_rgba(14,36,58,0.15)]";
            const inactiveStyle = "bg-slate-100 text-navy-700/80 hover:bg-slate-200/80 border-b border-slate-200 hover:translate-y-[-1px] transition-all";
            
            bar.innerHTML += `
                <button onclick="switchTab(${i})" class="folder-tab ${isActive ? activeStyle : inactiveStyle} px-4 py-3 sm:px-6 sm:py-3.5 text-xs sm:text-sm flex items-center space-x-2 focus:outline-none select-none flex-shrink-0">
                    <i class="${tabMeta.icon} text-xs"></i>
                    <span>${tabMeta.title.split(' ')[0]}</span>
                </button>
            `;
        }
    }

    function switchTab(index) {
        activeTab = index;
        renderTabsNav();
        renderActivePanel();
    }

    // Displays relevant card container elements
    function renderActivePanel() {
        // Toggle view blocks
        for (let i = 1; i <= 6; i++) {
            const panel = document.getElementById('panel-content-' + i);
            if (i === activeTab) {
                panel.classList.remove('hidden');
            } else {
                panel.classList.add('hidden');
            }
        }

        // Set top titles
        document.getElementById('tab-meta-title').innerText = tabData[activeTab].title;
        document.getElementById('tab-meta-icon').innerHTML = `<i class="${tabData[activeTab].icon}"></i>`;
        document.getElementById('tab-meta-number').innerText = activeTab;

        // Perform specific panel updates
        if (activeTab === 1) renderPersonalProfile();
        if (activeTab === 2) renderEducationPanel();
        if (activeTab === 3) renderWorkPanel();
        if (activeTab === 4) renderLeadershipPanel();
        if (activeTab === 5) renderHonorsPanel();
        if (activeTab === 6) renderAwardsPanel();
    }

    // Dynamic value mapping on open
    function hydrateView() {
        // Hero Inputs
        document.getElementById('hero-display-name').innerText = state.hero.name;
        document.getElementById('brand-name').innerText = state.hero.name;
        document.getElementById('hero-input-name').value = state.hero.name;

        document.getElementById('hero-display-headline').innerText = state.hero.headline;
        document.getElementById('hero-input-headline').value = state.hero.headline;

        document.getElementById('hero-display-welcome').innerText = state.hero.welcomeMessage;
        document.getElementById('hero-input-welcome').value = state.hero.welcomeMessage;

        // Profile quick details mapping
        document.getElementById('quick-address').innerText = state.profile.address;
        document.getElementById('quick-phone').innerText = state.profile.phone;
        document.getElementById('quick-email').innerText = state.profile.email;
    }

    // Hero key handlers
    function updateHero(key, val) {
        state.hero[key] = val;
        saveData();
        hydrateView();
    }

    // ----------------------------------------------------
    // TAB 1: PERSONAL PROFILE LOGIC
    // ----------------------------------------------------
    function renderPersonalProfile() {
        const prof = state.profile;

        // Input Sync (excluding linkedin from direct text replacement so the button text remains)
        const fields = ['fullName', 'nickname', 'address', 'phone', 'email'];
        fields.forEach(f => {
            document.getElementById(`prof-display-${f}`).innerText = prof[f] || '';
            document.getElementById(`prof-input-${f}`).value = prof[f] || '';
        });

        // Set input value for editor separate from button content
        document.getElementById('prof-input-linkedin').value = prof.linkedin || '';

        // Set Link URL only, preserving button's styled HTML children
        document.getElementById('prof-display-linkedin').href = prof.linkedin || 'https://linkedin.com';

        // Render skill tags
        const skillsBox = document.getElementById('skills-list');
        skillsBox.innerHTML = '';
        prof.skills.forEach((skill, idx) => {
            skillsBox.innerHTML += `
                <span class="inline-flex items-center bg-slate-100 text-navy-800 text-xs font-semibold px-3 py-1.5 rounded-full border border-slate-200">
                    <span>${skill}</span>
                    <button onclick="removeSkill(${idx})" class="editor-only ml-2 text-rose-500 hover:text-rose-700 transition-colors"><i class="fa-solid fa-circle-xmark"></i></button>
                </span>
            `;
        });

        // Render tools tags
        const toolsBox = document.getElementById('tools-list');
        toolsBox.innerHTML = '';
        prof.tools.forEach((tool, idx) => {
            toolsBox.innerHTML += `
                <span class="inline-flex items-center bg-slate-100 text-navy-800 text-xs font-semibold px-3 py-1.5 rounded-full border border-slate-200">
                    <span>${tool}</span>
                    <button onclick="removeTool(${idx})" class="editor-only ml-2 text-rose-500 hover:text-rose-700 transition-colors"><i class="fa-solid fa-circle-xmark"></i></button>
                </span>
            `;
        });

        // Sync Assessment Textareas & Scorecard images
        const scorecards = ['disc', 'iq', 'english', 'mbti'];
        scorecards.forEach(key => {
            const dataObj = prof[key];
            if (dataObj) {
                document.getElementById(`${key}-display-desc`).innerText = dataObj.description || '';
                document.getElementById(`${key}-input-desc`).value = dataObj.description || '';
                
                const imgPre = document.getElementById(`${key}-preview`);
                const emptyZone = document.getElementById(`${key}-empty`);
                if (dataObj.img) {
                    imgPre.src = dataObj.img;
                    imgPre.classList.remove('hidden');
                    emptyZone.classList.add('hidden');
                } else {
                    imgPre.classList.add('hidden');
                    emptyZone.classList.remove('hidden');
                }
            }
        });
    }

    function updateProfile(key, val) {
        state.profile[key] = val;
        saveData();
        hydrateView();
        
        // Live feedback for label fields (skipping text overwrite on the styled linkedin element)
        if (key !== 'linkedin') {
            const display = document.getElementById(`prof-display-${key}`);
            if (display) display.innerText = val;
        } else {
            document.getElementById('prof-display-linkedin').href = val || '#';
        }
    }

    function addSkill() {
        const name = prompt("Enter Skill name:");
        if (name && name.trim()) {
            state.profile.skills.push(name.trim());
            saveData();
            renderPersonalProfile();
            showToast("New core skill added!");
        }
    }

    function removeSkill(idx) {
        state.profile.skills.splice(idx, 1);
        saveData();
        renderPersonalProfile();
        showToast("Skill removed");
    }

    function addTool() {
        const tool = prompt("Enter platform/tool name:");
        if (tool && tool.trim()) {
            state.profile.tools.push(tool.trim());
            saveData();
            renderPersonalProfile();
            showToast("New tool asset listed!");
        }
    }

    function removeTool(idx) {
        state.profile.tools.splice(idx, 1);
        saveData();
        renderPersonalProfile();
        showToast("Tool removed");
    }

    function updateAssessment(key, textVal) {
        if (!state.profile[key]) state.profile[key] = { title: "", description: "", img: "" };
        state.profile[key].description = textVal;
        saveData();
        document.getElementById(`${key}-display-desc`).innerText = textVal;
    }

    // Direct Image upload zone to Base64
    function uploadImage(key, input) {
        if (input.files && input.files[0]) {
            const reader = new FileReader();
            reader.onload = function(e) {
                if (!state.profile[key]) state.profile[key] = { title: "", description: "", img: "" };
                state.profile[key].img = e.target.result;
                saveData();
                renderPersonalProfile();
                showToast(`Verification scorecard uploaded successfully!`);
            };
            reader.readAsDataURL(input.files[0]);
        }
    }

    // ----------------------------------------------------
    // TAB 2: EDUCATION (LOCKED CHRONOLOGY)
    // ----------------------------------------------------
    function renderEducationPanel() {
        const grid = document.getElementById('education-render-grid');
        grid.innerHTML = '';

        state.education.forEach((edu, idx) => {
            grid.innerHTML += `
                <div class="border border-slate-200 rounded-2xl p-5 bg-white shadow-[0_4px_12px_-4px_rgba(0,0,0,0.02)] space-y-4 hover:border-navy-200 transition-colors">
                    <div class="flex items-center justify-between">
                        <span class="text-[10px] font-black uppercase tracking-wider text-navy-600 bg-navy-50 px-2.5 py-1 rounded">
                            ${edu.level}
                        </span>
                        <span class="text-xs font-bold text-slate-300">Level Index 0${idx + 1}</span>
                    </div>

                    <div class="space-y-3">
                        <!-- School Field -->
                        <div>
                            <span class="block text-[9px] uppercase font-bold text-slate-400">Educational Institution</span>
                            <p class="text-sm sm:text-base font-bold text-navy-800 view-only">${edu.school || 'Unspecified'}</p>
                            <input type="text" value="${edu.school || ''}" oninput="updateEdu(${idx}, 'school', this.value)" class="editor-only mt-1 w-full px-3 py-1.5 text-xs border border-slate-200 rounded-lg bg-white">
                        </div>

                        <!-- Year Field -->
                        <div>
                            <span class="block text-[9px] uppercase font-bold text-slate-400">Duration Years</span>
                            <p class="text-xs font-semibold text-slate-500 view-only"><i class="fa-regular fa-calendar mr-1"></i> ${edu.years || 'Unspecified'}</p>
                            <input type="text" value="${edu.years || ''}" oninput="updateEdu(${idx}, 'years', this.value)" class="editor-only mt-1 w-full px-3 py-1.5 text-xs border border-slate-200 rounded-lg bg-white">
                        </div>

                        <!-- Field of study -->
                        <div>
                            <span class="block text-[9px] uppercase font-bold text-slate-400">Field of Study</span>
                            <p class="text-xs text-navy-800 font-medium leading-relaxed view-only">${edu.field || 'Unspecified'}</p>
                            <input type="text" value="${edu.field || ''}" oninput="updateEdu(${idx}, 'field', this.value)" class="editor-only mt-1 w-full px-3 py-1.5 text-xs border border-slate-200 rounded-lg bg-white">
                        </div>
                    </div>
                </div>
            `;
        });
    }

    function updateEdu(idx, key, val) {
        state.education[idx][key] = val;
        saveData();
    }

    // ----------------------------------------------------
    // TAB 3: WORK EXPERIENCES
    // ----------------------------------------------------
    function renderWorkPanel() {
        // Marketing Sorted Render (Descending start time period check)
        const sortedMarketing = [...state.work.marketing].sort((a, b) => {
            const parsedA = a.endYear.toLowerCase() === 'present' ? 9999 : (parseInt(a.endYear) || 0);
            const parsedB = b.endYear.toLowerCase() === 'present' ? 9999 : (parseInt(b.endYear) || 0);
            return parsedB - parsedA;
        });

        const container = document.getElementById('work-marketing-container');
        container.innerHTML = '';

        sortedMarketing.forEach(item => {
            container.innerHTML += `
                <div class="border border-slate-200 rounded-2xl p-5 bg-white relative hover:border-slate-300 transition-colors">
                    <div class="flex flex-col sm:flex-row sm:items-start justify-between gap-3">
                        <div class="space-y-1">
                            <!-- Job details view -->
                            <h5 class="text-sm sm:text-base font-bold text-navy-800 view-only">${item.position}</h5>
                            <input type="text" value="${item.position}" oninput="updateWorkItem('${item.id}', 'position', this.value)" class="editor-only px-3 py-1.5 text-xs border border-slate-200 rounded-lg bg-white w-full sm:w-80 font-bold mb-1.5">

                            <p class="text-xs font-bold text-navy-600 view-only">${item.company}</p>
                            <input type="text" value="${item.company}" oninput="updateWorkItem('${item.id}', 'company', this.value)" class="editor-only px-3 py-1.5 text-xs border border-slate-200 rounded-lg bg-white w-full sm:w-80 mb-1.5">
                        </div>

                        <!-- Time block -->
                        <div class="flex items-center space-x-2 text-xs font-semibold text-slate-500 bg-slate-50 border border-slate-100 px-3 py-1.5 rounded-lg w-max self-start">
                            <span class="view-only"><i class="fa-regular fa-clock mr-1"></i> ${item.startYear} - ${item.endYear}</span>
                            <div class="editor-only flex items-center space-x-1.5">
                                <input type="text" value="${item.startYear}" oninput="updateWorkItem('${item.id}', 'startYear', this.value)" class="w-16 px-1.5 py-0.5 border rounded text-[11px]" placeholder="Start">
                                <span class="text-slate-300">-</span>
                                <input type="text" value="${item.endYear}" oninput="updateWorkItem('${item.id}', 'endYear', this.value)" class="w-20 px-1.5 py-0.5 border rounded text-[11px]" placeholder="End / Present">
                            </div>
                        </div>
                    </div>

                    <!-- Work details essay -->
                    <div class="mt-4 pt-3 border-t border-slate-100 space-y-1.5">
                        <span class="block text-[9px] uppercase font-bold text-slate-400">Accomplishments & Contributions</span>
                        <p class="text-xs sm:text-sm text-slate-600 leading-relaxed text-justify whitespace-pre-line view-only">${item.details}</p>
                        <textarea oninput="updateWorkItem('${item.id}', 'details', this.value)" class="editor-only mt-1 w-full p-2 text-xs border border-slate-200 rounded-lg bg-white focus:outline-none" rows="3">${item.details}</textarea>
                    </div>

                    <!-- Action buttons -->
                    <button onclick="deleteMarketingWork('${item.id}')" class="editor-only absolute top-4 right-4 text-rose-500 hover:text-rose-700 font-bold text-xs">
                        <i class="fa-regular fa-trash-can mr-1"></i> Delete
                    </button>
                </div>
            `;
        });

        // Social Media Link mapping
        document.getElementById('sm-display-link').href = state.work.socialMedia.link || 'https://linkedin.com';
        document.getElementById('sm-input-link').value = state.work.socialMedia.link || '';

        // Industry Tags Cloud
        const box = document.getElementById('sm-industries-box');
        box.innerHTML = '';
        state.work.socialMedia.industries.forEach((ind, index) => {
            box.innerHTML += `
                <span class="inline-flex items-center bg-white border border-slate-200 shadow-sm text-navy-800 text-xs font-bold px-3 py-1.5 rounded-full select-none">
                    <span>${ind}</span>
                    <button onclick="removeSMIndustry(${index})" class="editor-only ml-2 text-rose-500 hover:text-rose-700 transition-colors"><i class="fa-solid fa-circle-xmark"></i></button>
                </span>
            `;
        });

        // Events Narrative essay
        document.getElementById('events-display-essay').innerText = state.work.events || '';
        document.getElementById('events-input-essay').value = state.work.events || '';
    }

    function addMarketingWork() {
        const id = "wm_" + Date.now();
        state.work.marketing.unshift({
            id: id,
            company: "New Company Group",
            position: "Marketing Associate",
            startYear: "2024",
            endYear: "Present",
            details: "Detail primary execution channels, conversions, budget controls, and analytics results."
        });
        saveData();
        renderWorkPanel();
        showToast("New marketing position listed!");
    }

    function updateWorkItem(id, key, val) {
        const target = state.work.marketing.find(x => x.id === id);
        if (target) {
            target[key] = val;
            saveData();
        }
    }

    function deleteMarketingWork(id) {
        state.work.marketing = state.work.marketing.filter(x => x.id !== id);
        saveData();
        renderWorkPanel();
        showToast("Marketing entry removed");
    }

    function updateSMLink(val) {
        state.work.socialMedia.link = val;
        saveData();
        document.getElementById('sm-display-link').href = val || '#';
    }

    function addSMIndustry() {
        const input = document.getElementById('sm-input-industry');
        const val = input.value.trim();
        if (val) {
            state.work.socialMedia.industries.push(val);
            input.value = '';
            saveData();
            renderWorkPanel();
            showToast("New industry added");
        }
    }

    function removeSMIndustry(idx) {
        state.work.socialMedia.industries.splice(idx, 1);
        saveData();
        renderWorkPanel();
        showToast("Industry removed");
    }

    function updateEventsEssay(val) {
        state.work.events = val;
        saveData();
        document.getElementById('events-display-essay').innerText = val;
    }

    // ----------------------------------------------------
    // TAB 4: LEADERSHIP HISTORY
    // ----------------------------------------------------
    function renderLeadershipPanel() {
        const sorted = [...state.leadership].sort((a, b) => {
            const valA = parseInt(a.startYear) || 0;
            const valB = parseInt(b.startYear) || 0;
            return valB - valA;
        });

        const container = document.getElementById('leadership-container');
        container.innerHTML = '';

        sorted.forEach(item => {
            container.innerHTML += `
                <div class="border border-slate-200 rounded-2xl p-5 bg-white relative hover:border-slate-300 transition-colors">
                    <div class="flex flex-col sm:flex-row sm:items-start justify-between gap-3">
                        <div class="space-y-1">
                            <h5 class="text-sm sm:text-base font-bold text-navy-800 view-only">${item.organization}</h5>
                            <input type="text" value="${item.organization}" oninput="updateLeadershipItem('${item.id}', 'organization', this.value)" class="editor-only px-3 py-1.5 text-xs border border-slate-200 rounded-lg bg-white w-full sm:w-80 font-bold mb-1">

                            <p class="text-xs font-semibold text-slate-500 view-only">${item.position}</p>
                            <input type="text" value="${item.position}" oninput="updateLeadershipItem('${item.id}', 'position', this.value)" class="editor-only px-3 py-1.5 text-xs border border-slate-200 rounded-lg bg-white w-full sm:w-80 mb-1">
                        </div>

                        <div class="flex items-center space-x-2 text-xs font-semibold text-slate-500 bg-slate-50 border border-slate-100 px-3 py-1.5 rounded-lg w-max self-start">
                            <span class="view-only"><i class="fa-regular fa-clock mr-1"></i> ${item.startYear} - ${item.endYear}</span>
                            <div class="editor-only flex items-center space-x-1.5">
                                <input type="text" value="${item.startYear}" oninput="updateLeadershipItem('${item.id}', 'startYear', this.value)" class="w-16 px-1.5 py-0.5 border rounded text-[11px]" placeholder="Start">
                                <span class="text-slate-300">-</span>
                                <input type="text" value="${item.endYear}" oninput="updateLeadershipItem('${item.id}', 'endYear', this.value)" class="w-16 px-1.5 py-0.5 border rounded text-[11px]" placeholder="End">
                            </div>
                        </div>
                    </div>

                    <!-- Delete button -->
                    <button onclick="deleteLeadership('${item.id}')" class="editor-only absolute top-4 right-4 text-rose-500 hover:text-rose-700 font-bold text-xs">
                        <i class="fa-regular fa-trash-can mr-1"></i> Delete
                    </button>
                </div>
            `;
        });
    }

    function addLeadership() {
        const id = "lead_" + Date.now();
        state.leadership.unshift({
            id: id,
            organization: "National Youth Committee",
            position: "Lead Organizer",
            startYear: "2024",
            endYear: "2025"
        });
        saveData();
        renderLeadershipPanel();
        showToast("New leadership entry created!");
    }

    function updateLeadershipItem(id, key, val) {
        const target = state.leadership.find(x => x.id === id);
        if (target) {
            target[key] = val;
            saveData();
        }
    }

    function deleteLeadership(id) {
        state.leadership = state.leadership.filter(x => x.id !== id);
        saveData();
        renderLeadershipPanel();
        showToast("Leadership entry deleted");
    }

    // ----------------------------------------------------
    // TAB 5: ACADEMIC HONORS
    // ----------------------------------------------------
    function renderHonorsPanel() {
        const sorted = [...state.honors].sort((a, b) => {
            const valA = parseInt(a.startYear) || 0;
            const valB = parseInt(b.startYear) || 0;
            return valB - valA;
        });

        const container = document.getElementById('honors-container');
        container.innerHTML = '';

        sorted.forEach(item => {
            container.innerHTML += `
                <div class="border border-slate-200 rounded-2xl p-5 bg-white relative hover:border-slate-300 transition-colors">
                    <div class="flex flex-col sm:flex-row sm:items-start justify-between gap-3">
                        <div class="space-y-1">
                            <h5 class="text-sm sm:text-base font-bold text-navy-800 view-only">${item.honor}</h5>
                            <input type="text" value="${item.honor}" oninput="updateHonorItem('${item.id}', 'honor', this.value)" class="editor-only px-3 py-1.5 text-xs border border-slate-200 rounded-lg bg-white w-full sm:w-80 font-bold mb-1">

                            <p class="text-xs font-semibold text-slate-500 view-only">${item.school || 'Unspecified'}</p>
                            <input type="text" value="${item.school || ''}" oninput="updateHonorItem('${item.id}', 'school', this.value)" class="editor-only px-3 py-1.5 text-xs border border-slate-200 rounded-lg bg-white w-full sm:w-80 mb-1" placeholder="School">
                        </div>

                        <div class="flex items-center space-x-2 text-xs font-semibold text-slate-500 bg-slate-50 border border-slate-100 px-3 py-1.5 rounded-lg w-max self-start">
                            <span class="view-only"><i class="fa-regular fa-clock mr-1"></i> ${item.startYear} - ${item.endYear}</span>
                            <div class="editor-only flex items-center space-x-1.5">
                                <input type="text" value="${item.startYear}" oninput="updateHonorItem('${item.id}', 'startYear', this.value)" class="w-16 px-1.5 py-0.5 border rounded text-[11px]" placeholder="Start">
                                <span class="text-slate-300">-</span>
                                <input type="text" value="${item.endYear}" oninput="updateHonorItem('${item.id}', 'endYear', this.value)" class="w-16 px-1.5 py-0.5 border rounded text-[11px]" placeholder="End">
                            </div>
                        </div>
                    </div>

                    <button onclick="deleteHonor('${item.id}')" class="editor-only absolute top-4 right-4 text-rose-500 hover:text-rose-700 font-bold text-xs">
                        <i class="fa-regular fa-trash-can mr-1"></i> Delete
                    </button>
                </div>
            `;
        });
    }

    function addHonor() {
        const id = "hon_" + Date.now();
        state.honors.unshift({
            id: id,
            honor: "Presidential Distinction",
            school: "State University",
            startYear: "2022",
            endYear: "2023"
        });
        saveData();
        renderHonorsPanel();
        showToast("New honor distinction added!");
    }

    function updateHonorItem(id, key, val) {
        const target = state.honors.find(x => x.id === id);
        if (target) {
            target[key] = val;
            saveData();
        }
    }

    function deleteHonor(id) {
        state.honors = state.honors.filter(x => x.id !== id);
        saveData();
        renderHonorsPanel();
        showToast("Honor removed");
    }

    // ----------------------------------------------------
    // TAB 6: COMPETITION AWARDS
    // ----------------------------------------------------
    function renderAwardsPanel() {
        const sorted = [...state.awards].sort((a, b) => {
            const valA = parseInt(a.year) || 0;
            const valB = parseInt(b.year) || 0;
            return valB - valA;
        });

        const container = document.getElementById('awards-container');
        container.innerHTML = '';

        sorted.forEach(item => {
            container.innerHTML += `
                <div class="border border-slate-200 rounded-2xl p-5 bg-white relative hover:border-slate-300 transition-colors">
                    <div class="flex flex-col sm:flex-row sm:items-start justify-between gap-3">
                        <div class="space-y-1">
                            <h5 class="text-sm sm:text-base font-bold text-navy-800 view-only">${item.title}</h5>
                            <input type="text" value="${item.title}" oninput="updateAwardItem('${item.id}', 'title', this.value)" class="editor-only px-3 py-1.5 text-xs border border-slate-200 rounded-lg bg-white w-full sm:w-80 font-bold mb-1">

                            <p class="text-xs font-semibold text-slate-500 view-only">${item.competition}</p>
                            <input type="text" value="${item.competition}" oninput="updateAwardItem('${item.id}', 'competition', this.value)" class="editor-only px-3 py-1.5 text-xs border border-slate-200 rounded-lg bg-white w-full sm:w-80 mb-1" placeholder="Competition">
                        </div>

                        <div class="flex items-center space-x-2 text-xs font-semibold text-slate-500 bg-slate-50 border border-slate-100 px-3 py-1.5 rounded-lg w-max self-start">
                            <span class="view-only"><i class="fa-solid fa-trophy mr-1 text-amber-500"></i> ${item.year}</span>
                            <div class="editor-only flex items-center space-x-1.5">
                                <input type="text" value="${item.year}" oninput="updateAwardItem('${item.id}', 'year', this.value)" class="w-20 px-1.5 py-0.5 border rounded text-[11px]" placeholder="Year">
                            </div>
                        </div>
                    </div>

                    <button onclick="deleteAward('${item.id}')" class="editor-only absolute top-4 right-4 text-rose-500 hover:text-rose-700 font-bold text-xs">
                        <i class="fa-regular fa-trash-can mr-1"></i> Delete
                    </button>
                </div>
            `;
        });
    }

    function addAward() {
        const id = "aw_" + Date.now();
        state.awards.unshift({
            id: id,
            title: "Outstanding Marketer Award",
            competition: "Regional Business League",
            year: "2024"
        });
        saveData();
        renderAwardsPanel();
        showToast("New competition award listed!");
    }

    // Dynamic key fields updates
    function updateAwardItem(id, key, val) {
        const target = state.awards.find(x => x.id === id);
        if (target) {
            target[key] = val;
            saveData();
        }
    }

    function deleteAward(id) {
        state.awards = state.awards.filter(x => x.id !== id);
        saveData();
        renderAwardsPanel();
        showToast("Award removed");
    }

    // ----------------------------------------------------
    // AUXILIARY UTILITIES (Toast alerts, Share Modal, etc.)
    // ----------------------------------------------------
    function showToast(msg) {
        const toast = document.getElementById('notification-toast');
        document.getElementById('notification-text').innerText = msg;
        toast.className = "fixed bottom-6 right-6 z-50 transform translate-y-0 opacity-100 transition-all duration-300";
        setTimeout(() => {
            toast.className = "fixed bottom-6 right-6 z-50 transform translate-y-20 opacity-0 transition-all duration-300";
        }, 3000);
    }

    function openShareModal() {
        document.getElementById('share-modal').classList.remove('hidden');
    }

    function closeShareModal() {
        document.getElementById('share-modal').classList.add('hidden');
    }

    function copyLink() {
        const copyText = document.getElementById('shareable-link').innerText;
        const tempInput = document.createElement("input");
        tempInput.value = copyText;
        document.body.appendChild(tempInput);
        tempInput.select();
        document.execCommand("copy");
        document.body.removeChild(tempInput);

        const btnLabel = document.getElementById('btn-copy-label');
        btnLabel.innerText = "Copied!";
        setTimeout(() => {
            btnLabel.innerText = "Copy";
        }, 1500);
        showToast("Link copied to clipboard successfully!");
    }
</script>

</body>
</html>
