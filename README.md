<html lang="es" class="dark scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fundamentos de la Ciberseguridad | CBTis N° 166 - DGETI 2026</title>
    <!-- Tailwind CSS via CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        cyber: {
                            black: '#0b0f19',
                            dark: '#121824',
                            card: '#1a2234',
                            border: '#2a354f',
                            cyan: '#00f2fe',
                            blue: '#4facfe',
                            green: '#00ff87',
                            purple: '#7928ca',
                            red: '#ff4b5c'
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        mono: ['JetBrains Mono', 'monospace']
                    }
                }
            }
        }
    </script>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=JetBrains+Mono:wght@400;500;700&display=swap" rel="stylesheet">
    <!-- FontAwesome CDN para Iconos -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        .code-font {
            font-family: 'JetBrains Mono', monospace;
        }
        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #0b0f19;
        }
        ::-webkit-scrollbar-thumb {
            background: #2a354f;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #00f2fe;
        }
        /* Glow effects */
        .neon-glow-cyan {
            box-shadow: 0 0 15px rgba(0, 242, 254, 0.3);
        }
        .neon-glow-green {
            box-shadow: 0 0 15px rgba(0, 255, 135, 0.3);
        }
        .neon-border {
            border-color: rgba(0, 242, 254, 0.4);
        }
        .neon-border:hover {
            border-color: rgba(0, 242, 254, 1);
            box-shadow: 0 0 12px rgba(0, 242, 254, 0.4);
        }

        /* Light mode adjustments */
        html:not(.dark) body {
            background-color: #f8fafc;
            color: #0f172a;
        }
        html:not(.dark) .bg-cyber-dark {
            background-color: #ffffff;
            border-color: #e2e8f0;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05);
        }
        html:not(.dark) .bg-cyber-card {
            background-color: #f1f5f9;
            border-color: #cbd5e1;
        }
        html:not(.dark) .bg-cyber-black {
            background-color: #e2e8f0;
            border-color: #cbd5e1;
            color: #0f172a;
        }
        html:not(.dark) .text-slate-300, html:not(.dark) .text-slate-400 {
            color: #334155;
        }
        html:not(.dark) .text-white {
            color: #0f172a;
        }
        html:not(.dark) header {
            background-color: rgba(255, 255, 255, 0.9);
            border-color: #e2e8f0;
        }
    </style>
</head>
<body class="bg-slate-50 text-slate-900 dark:bg-cyber-black dark:text-slate-100 transition-colors duration-300">

    <!-- Reading Progress Bar -->
    <div id="progress-bar" class="fixed top-0 left-0 h-1 bg-gradient-to-r from-cyber-cyan via-cyber-blue to-cyber-green z-[60] transition-all duration-150" style="width: 0%"></div>

    <!-- Header / Navbar (Modificado a relativo para Google Sites) -->
    <header class="relative z-50 w-full backdrop-blur-md bg-white/80 dark:bg-cyber-black/80 border-b border-slate-200 dark:border-cyber-border">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between">
            <!-- Logo -->
            <a href="#inicio" class="flex items-center gap-3 group">
                <div class="w-10 h-10 rounded-lg bg-gradient-to-br from-cyber-cyan to-cyber-blue flex items-center justify-center text-cyber-black font-bold text-xl neon-glow-cyan group-hover:scale-105 transition-transform">
                    <i class="fa-solid font-mono fa-shield-halved"></i>
                </div>
                <div>
                    <span class="text-lg font-bold bg-gradient-to-r from-cyber-cyan to-cyber-green bg-clip-text text-transparent">CIBERSEGURIDAD</span>
                    <span class="block text-xs text-slate-500 dark:text-slate-400 font-mono">DGETI | CBTis N° 166</span>
                </div>
            </a>

            <!-- Desktop Nav Links -->
            <nav class="hidden lg:flex items-center gap-6 text-sm font-medium">
                <a href="#inicio" class="hover:text-cyber-cyan transition-colors">Inicio</a>
                <a href="#tema1" class="hover:text-cyber-cyan transition-colors">T1: Origen</a>
                <a href="#tema2" class="hover:text-cyber-cyan transition-colors">T2: Amenazas</a>
                <a href="#tema3" class="hover:text-cyber-cyan transition-colors">T3: Escolar</a>
                <a href="#tema4" class="hover:text-cyber-cyan transition-colors">T4: Fraudes</a>
                <a href="#tema5" class="hover:text-cyber-cyan transition-colors">T5: Delitos</a>
                <a href="#faq" class="hover:text-cyber-green transition-colors text-cyber-green">FAQ Experto</a>
                
                <!-- Dropdown Laboratorio -->
                <div class="relative group">
                    <button class="hover:text-cyber-cyan transition-colors flex items-center gap-1 py-2">
                        Laboratorios <i class="fa-solid fa-chevron-down text-[10px] transition-transform group-hover:rotate-180"></i>
                    </button>
                    <div class="absolute left-0 top-full mt-0 w-52 bg-white dark:bg-cyber-card border border-slate-200 dark:border-cyber-border rounded-xl shadow-xl opacity-0 invisible group-hover:opacity-100 group-hover:visible transition-all duration-200 z-50 flex flex-col overflow-hidden">
                        <a href="#sim-tema1" class="px-4 py-3 text-xs hover:bg-slate-100 dark:hover:bg-cyber-cyan/10 hover:text-cyber-cyan border-b border-slate-100 dark:border-cyber-border/50 transition-colors">1. Miniquiz T1</a>
                        <a href="#sim-tema2" class="px-4 py-3 text-xs hover:bg-slate-100 dark:hover:bg-cyber-cyan/10 hover:text-cyber-cyan border-b border-slate-100 dark:border-cyber-border/50 transition-colors">2. Eval. Contraseñas</a>
                        <a href="#sim-tema3" class="px-4 py-3 text-xs hover:bg-slate-100 dark:hover:bg-cyber-cyan/10 hover:text-cyber-cyan border-b border-slate-100 dark:border-cyber-border/50 transition-colors">3. Auditoría T3</a>
                        <a href="#sim-tema4" class="px-4 py-3 text-xs hover:bg-slate-100 dark:hover:bg-cyber-cyan/10 hover:text-cyber-cyan border-b border-slate-100 dark:border-cyber-border/50 transition-colors">4. Simulador Phishing</a>
                        <a href="#sim-tema5" class="px-4 py-3 text-xs hover:bg-slate-100 dark:hover:bg-cyber-cyan/10 hover:text-cyber-cyan transition-colors">5. Casos Legales</a>
                    </div>
                </div>

                <a href="#fuentes" class="hover:text-cyber-cyan transition-colors">Fuentes</a>
            </nav>

            <!-- Actions & Theme Toggle -->
            <div class="flex items-center gap-3">
                <button id="theme-toggle" class="p-2.5 rounded-lg border border-slate-300 dark:border-cyber-border bg-slate-200 dark:bg-cyber-dark hover:border-cyber-cyan transition-colors" title="Cambiar Tema">
                    <i id="theme-toggle-dark-icon" class="fa-solid fa-moon text-cyber-cyan"></i>
                    <i id="theme-toggle-light-icon" class="fa-solid fa-sun text-amber-500 hidden"></i>
                </button>

                <a href="#autor" class="hidden sm:inline-flex items-center gap-2 px-4 py-2 rounded-lg bg-cyber-card border border-cyber-cyan text-cyber-cyan text-xs font-semibold uppercase tracking-wider hover:bg-cyber-cyan hover:text-cyber-black transition-all">
                    <i class="fa-solid fa-user-gear"></i> Autor
                </a>

                <!-- Mobile menu button -->
                <button id="mobile-menu-btn" class="lg:hidden p-2 rounded-lg border border-slate-300 dark:border-cyber-border text-slate-700 dark:text-slate-300">
                    <i class="fa-solid fa-bars text-xl"></i>
                </button>
            </div>
        </div>

        <!-- Mobile Nav Menu -->
        <div id="mobile-menu" class="hidden lg:hidden bg-slate-100 dark:bg-cyber-dark border-b border-slate-300 dark:border-cyber-border px-4 py-4 space-y-3 font-medium text-sm">
            <a href="#inicio" class="block hover:text-cyber-cyan">Inicio</a>
            <a href="#tema1" class="block hover:text-cyber-cyan">Tema 1: Historia & Pentágono</a>
            <a href="#tema2" class="block hover:text-cyber-cyan">Tema 2: Amenazas & 4 Pilares</a>
            <a href="#tema3" class="block hover:text-cyber-cyan">Tema 3: Ciberseguridad Escolar</a>
            <a href="#tema4" class="block hover:text-cyber-cyan">Tema 4: Fraude & Mal Uso</a>
            <a href="#tema5" class="block hover:text-cyber-cyan">Tema 5: Delitos & Normativa</a>
            <a href="#faq" class="block text-cyber-green font-bold">FAQ Experto (31 Preguntas)</a>
            
            <!-- Sub-menu de laboratorios en Móvil -->
            <div class="border-l-2 border-cyber-cyan pl-3 py-1 space-y-3 my-2 bg-slate-200/50 dark:bg-cyber-black/50 rounded-r-lg">
                <span class="block text-xs font-bold text-slate-500 dark:text-slate-400 uppercase tracking-wider">Laboratorios Interactivos:</span>
                <a href="#sim-tema1" class="block hover:text-cyber-cyan text-sm">1. Miniquiz (Tema 1)</a>
                <a href="#sim-tema2" class="block hover:text-cyber-cyan text-sm">2. Contraseñas (Tema 2)</a>
                <a href="#sim-tema3" class="block hover:text-cyber-cyan text-sm">3. Auditoría (Tema 3)</a>
                <a href="#sim-tema4" class="block hover:text-cyber-cyan text-sm">4. Phishing (Tema 4)</a>
                <a href="#sim-tema5" class="block hover:text-cyber-cyan text-sm">5. Casos Legales (Tema 5)</a>
            </div>

            <a href="#fuentes" class="block hover:text-cyber-cyan">Fuentes y Estándares</a>
            <a href="#autor" class="block hover:text-cyber-cyan">Acerca del Autor</a>
        </div>
    </header>

    <!-- Main Content Container -->
    <main class="space-y-24 pt-4 pb-8">

        <!-- HERO SECTION -->
        <section id="inicio" class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 pt-8 pb-12">
            <div class="absolute -top-20 right-10 w-96 h-96 bg-cyber-cyan/10 rounded-full blur-3xl -z-10"></div>
            <div class="absolute top-40 left-10 w-96 h-96 bg-cyber-purple/10 rounded-full blur-3xl -z-10"></div>

            <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
                <div class="lg:col-span-7 space-y-6">
                    <div class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full bg-cyber-card border border-cyber-green/40 text-cyber-green text-xs font-mono">
                        <span class="w-2 h-2 rounded-full bg-cyber-green animate-pulse"></span>
                        CURSO OFICIAL 2026 | DGETI & CBTis N° 166
                    </div>
                    <h1 class="text-4xl sm:text-5xl lg:text-6xl font-extrabold tracking-tight leading-none">
                        Fundamentos de la <br>
                        <span class="bg-gradient-to-r from-cyber-cyan via-cyber-blue to-cyber-green bg-clip-text text-transparent">Ciberseguridad</span>
                    </h1>
                    <p class="text-slate-300 text-lg leading-relaxed">
                        Plataforma interactiva de aprendizaje integral. Explora los 5 módulos teóricos, pon a prueba tus habilidades con simuladores en vivo y consulta el compendio exclusivo de 31 preguntas clave respondidas por expertos del área.
                    </p>

                    <div class="flex flex-wrap gap-4 pt-2">
                        <a href="#tema1" class="px-6 py-3.5 rounded-xl bg-gradient-to-r from-cyber-cyan to-cyber-blue text-cyber-black font-bold text-sm tracking-wide hover:shadow-lg hover:shadow-cyber-cyan/30 transition-all flex items-center gap-2">
                            <i class="fa-solid fa-rocket"></i> Iniciar Curso
                        </a>
                        <a href="#faq" class="px-6 py-3.5 rounded-xl bg-cyber-card border border-cyber-green text-cyber-green font-bold text-sm hover:bg-cyber-green hover:text-cyber-black transition-all flex items-center gap-2">
                            <i class="fa-solid fa-clipboard-question"></i> Entrevista Experto (FAQ)
                        </a>
                    </div>

                    <!-- Quick Metrics -->
                    <div class="grid grid-cols-3 gap-4 pt-6 border-t border-cyber-border text-center sm:text-left">
                        <div>
                            <span class="text-2xl sm:text-3xl font-extrabold text-cyber-cyan font-mono">5</span>
                            <span class="block text-xs text-slate-400 uppercase tracking-wider mt-1">Módulos Teóricos</span>
                        </div>
                        <div>
                            <span class="text-2xl sm:text-3xl font-extrabold text-cyber-green font-mono">31</span>
                            <span class="block text-xs text-slate-400 uppercase tracking-wider mt-1">FAQs de Experto</span>
                        </div>
                        <div>
                            <span class="text-2xl sm:text-3xl font-extrabold text-cyber-blue font-mono">4</span>
                            <span class="block text-xs text-slate-400 uppercase tracking-wider mt-1">Simuladores Vivos</span>
                        </div>
                    </div>
                </div>

                <!-- Hero Graphic Card -->
                <div class="lg:col-span-5">
                    <div class="relative bg-cyber-dark border border-cyber-border rounded-2xl p-6 shadow-2xl neon-glow-cyan overflow-hidden">
                        <div class="flex items-center justify-between pb-4 border-b border-cyber-border">
                            <div class="flex gap-2">
                                <span class="w-3 h-3 rounded-full bg-red-500"></span>
                                <span class="w-3 h-3 rounded-full bg-yellow-500"></span>
                                <span class="w-3 h-3 rounded-full bg-green-500"></span>
                            </div>
                            <span class="text-xs font-mono text-slate-400">sec-status: ActiveGuard 2.0</span>
                        </div>

                        <div class="py-6 space-y-4 font-mono text-xs">
                            <div class="p-3 bg-cyber-black rounded-lg border border-cyber-border flex items-center justify-between">
                                <span class="text-slate-400">&gt; Protocolo de Red:</span>
                                <span class="text-cyber-blue font-semibold">TLS 1.3 / WPA3</span>
                            </div>
                            <div class="p-3 bg-cyber-black rounded-lg border border-cyber-border flex items-center justify-between">
                                <span class="text-slate-400">&gt; Creador y Especialista:</span>
                                <span class="text-amber-400 font-semibold">Rodolfo Villa Noriega</span>
                            </div>
                        </div>

                        <div class="bg-gradient-to-r from-cyber-cyan/10 to-cyber-green/10 p-4 rounded-xl border border-cyber-cyan/30 text-center">
                            <i class="fa-solid fa-user-shield text-3xl text-cyber-cyan mb-2"></i>
                            <p class="text-xs text-slate-300">"El factor humano consciente y capacitado es el cortafuegos más potente de la era digital."</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- TEMA 1 SECTION -->
        <section id="tema1" class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 scroll-mt-24">
            <div class="bg-cyber-dark border border-cyber-border rounded-3xl p-6 sm:p-10 relative overflow-hidden">
                <div class="absolute top-0 right-0 px-6 py-2 bg-cyber-cyan/10 text-cyber-cyan font-mono text-xs rounded-bl-2xl border-l border-b border-cyber-cyan/30 uppercase tracking-widest font-bold">
                    Módulo 1
                </div>

                <div class="mb-8">
                    <span class="text-cyber-cyan text-sm font-mono uppercase tracking-wider font-semibold">Fundamentos Históricos & Principios Teóricos</span>
                    <h2 class="text-3xl sm:text-4xl font-bold mt-1">Tema 1: Introducción y Origen de Internet y la Ciberseguridad</h2>
                </div>

                <!-- Content Grid -->
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                    <!-- History Column -->
                    <div class="space-y-6">
                        <div class="bg-cyber-card p-6 rounded-2xl border border-cyber-border">
                            <h3 class="text-xl font-bold text-cyber-cyan flex items-center gap-2 mb-4">
                                <i class="fa-solid fa-timeline"></i> Historia y Evolución de la Red y las Amenazas
                            </h3>
                            <ul class="space-y-4 text-sm text-slate-300">
                                <li class="border-l-2 border-cyber-cyan pl-4">
                                    <strong class="text-white block font-mono">1960s - ARPANET y Conmutación de Paquetes</strong>
                                    Paul Baran (RAND Corporation) propone redes distribuidas de datos en 11 memorandos técnicos, y Donald Davies (NPL, Reino Unido) acuña el término <em>"packet switching"</em>. 
                                    <em class="text-slate-400 block text-xs mt-1">Mito vs. Realidad: Aunque popularmente se creía que ARPANET buscaba resistir ataques nucleares masivos, su objetivo primario documentado era optimizar el tiempo compartido de grandes supercomputadoras entre centros de investigación.</em>
                                </li>
                                <li class="border-l-2 border-cyber-cyan pl-4">
                                    <strong class="text-white block font-mono">29 de Octubre de 1969 - El Primer Mensaje ("LO")</strong>
                                    Transmisión entre el Interface Message Processor (IMP) de UCLA (supervisado por Leonard Kleinrock) y el IMP del Stanford Research Institute (SRI). Al intentar enviar la palabra "LOGIN", la red sufrió un colapso tras transmitir las letras "L" y "O".
                                </li>
                                <li class="border-l-2 border-cyber-cyan pl-4">
                                    <strong class="text-white block font-mono">1971 - Creeper vs. Reaper (El Primer Malware y Antivirus)</strong>
                                    Bob Thomas crea <em>Creeper</em> en la red ARPANET bajo el sistema operativo TENEX, mostrando la frase: <code>"I'm the creeper, catch me if you can!"</code>. En respuesta, Ray Tomlinson programa <em>Reaper</em>, diseñado para autorreplicarse, buscar las copias de Creeper y eliminarlas de los nodos infectados.
                                </li>
                                <li class="border-l-2 border-cyber-cyan pl-4">
                                    <strong class="text-white block font-mono">1 de Enero de 1983 - Flag Day & Protocolo TCP/IP</strong>
                                    Ocurre la transición histórica de NCP (Network Control Program) al conjunto de protocolos TCP (RFC 793) e IP (RFC 791) desarrollados por Vinton Cerf y Robert Kahn, marcando el nacimiento técnico de la Internet moderna.
                                </li>
                                <li class="border-l-2 border-cyber-cyan pl-4">
                                    <strong class="text-white block font-mono">1988 - El Morris Worm y el Origen de CERT/CC</strong>
                                    Robert Tappan Morris libera el primer gusano en afectar masivamente a computadoras conectadas a Internet (explotando fallas en <code>fingerd</code> y <code>sendmail</code>). Este hito histórico motiva la creación del primer Equipo de Respuesta ante Incidentes de Seguridad Informática (CERT/CC) en la Universidad Carnegie Mellon.
                                </li>
                                <li class="border-l-2 border-cyber-cyan pl-4">
                                    <strong class="text-white block font-mono">1989-1993 - La WWW y el Navegador Mosaic</strong>
                                    Tim Berners-Lee publica la propuesta de la World Wide Web en el CERN (creando HTML, HTTP y URL). En 1993, Marc Andreessen y Eric Bina lanzan NCSA Mosaic, democratizando la navegación gráfica a nivel global.
                                </li>
                            </ul>
                        </div>
                    </div>

                    <!-- Security Pentagon & Frameworks -->
                    <div class="space-y-6">
                        <!-- Pentagon -->
                        <div class="bg-cyber-card p-6 rounded-2xl border border-cyber-border">
                            <h3 class="text-xl font-bold text-cyber-green flex items-center gap-2 mb-4">
                                <i class="fa-solid fa-shapes"></i> El Pentágono de la Seguridad de la Información
                            </h3>
                            <p class="text-xs text-slate-300 mb-4">
                                Extensión del modelo clásico CIA (Confidencialidad, Integridad, Disponibilidad) incorporando los principios de Autenticidad y Trazabilidad para la protección integral de activos de información.
                            </p>
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3 text-xs">
                                <div class="p-3 bg-cyber-black rounded-xl border border-cyber-border">
                                    <span class="text-cyber-cyan font-bold block mb-1">1. Confidencialidad</span>
                                    Garantiza que la información permanezca inaccesible para entidades no autorizadas mediante cifrado (AES-256) y RBAC.
                                </div>
                                <div class="p-3 bg-cyber-black rounded-xl border border-cyber-border">
                                    <span class="text-cyber-green font-bold block mb-1">2. Integridad</span>
                                    Asegura la exactitud y totalidad de los datos impidiendo modificaciones maliciosas mediante funciones hash (SHA-256) y HMAC.
                                </div>
                                <div class="p-3 bg-cyber-black rounded-xl border border-cyber-border">
                                    <span class="text-cyber-blue font-bold block mb-1">3. Disponibilidad</span>
                                    Garantiza el acceso oportuno a los datos mediante redundancia y mitigación de ataques DoS.
                                </div>
                                <div class="p-3 bg-cyber-black rounded-xl border border-cyber-border">
                                    <span class="text-purple-400 font-bold block mb-1">4. Autenticidad</span>
                                    Verifica la identidad declarada por el emisor mediante certificados X.509 y firma digital.
                                </div>
                                <div class="sm:col-span-2 p-3 bg-cyber-black rounded-xl border border-cyber-border">
                                    <span class="text-amber-400 font-bold block mb-1">5. Trazabilidad (No Repudio)</span>
                                    Permite rastrear cada acción a un usuario específico mediante auditorías inmutables de registros SYSLOG.
                                </div>
                            </div>
                        </div>

                        <!-- Paradigmas de Defensa y Estándares -->
                        <div class="bg-cyber-card p-6 rounded-2xl border border-cyber-border space-y-4">
                            <h3 class="text-lg font-bold text-white flex items-center gap-2">
                                <i class="fa-solid fa-layer-group"></i> Paradigmas Modernos y Marcos Internacionales
                            </h3>
                            <div class="space-y-3 text-xs text-slate-300">
                                <div class="p-3 bg-cyber-black rounded-xl">
                                    <strong class="text-cyber-cyan block mb-1">Defensa en Profundidad:</strong>
                                    Estrategia en capas superpuestas (perimetral, red, host, datos). Si una falla, la siguiente contiene la amenaza.
                                </div>
                                <div class="p-3 bg-cyber-black rounded-xl">
                                    <strong class="text-cyber-green block mb-1">Modelo Zero Trust (NIST SP 800-207):</strong>
                                    Principio rector: <em>"Nunca confíes, verifica siempre explícitamente"</em> antes de autorizar cualquier acceso.
                                </div>
                                <div class="p-3 bg-cyber-black rounded-xl border-l-2 border-amber-400">
                                    <strong class="text-amber-400 block mb-1">NIST CSF 2.0:</strong>
                                    Funciones clave: <strong>Gobernar, Identificar, Proteger, Detectar, Responder y Recuperar</strong>.
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- SIMULADOR INTERACTIVO TEMA 1: MINI CUESTIONARIO -->
                <div id="sim-tema1" class="mt-8 pt-8 border-t border-cyber-border scroll-mt-24">
                    <div class="bg-cyber-card p-6 rounded-2xl border border-cyber-cyan/40">
                        <div class="flex items-center justify-between mb-4">
                            <h3 class="text-lg font-bold text-cyber-cyan flex items-center gap-2">
                                <i class="fa-solid fa-list-check"></i> Simulador Tema 1: Mini Cuestionario de Evaluación (6 Preguntas)
                            </h3>
                            <span id="quiz-score-badge" class="px-3 py-1 bg-cyber-black border border-cyber-cyan text-cyber-cyan font-mono text-xs rounded-full font-bold">Puntaje: 0 / 6</span>
                        </div>
                        <p class="text-xs text-slate-300 mb-6">Demuestra tus conocimientos sobre la historia de Internet, el Pentágono de Seguridad y los marcos normativos.</p>

                        <div id="quiz-questions-container" class="space-y-6">
                            <!-- Dynamic questions populated by JS -->
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- TEMA 2 SECTION -->
        <section id="tema2" class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 scroll-mt-24">
            <div class="bg-cyber-dark border border-cyber-border rounded-3xl p-6 sm:p-10 relative overflow-hidden">
                <div class="absolute top-0 right-0 px-6 py-2 bg-cyber-green/10 text-cyber-green font-mono text-xs rounded-bl-2xl border-l border-b border-cyber-green/30 uppercase tracking-widest font-bold">
                    Módulo 2
                </div>

                <div class="mb-8">
                    <span class="text-cyber-green text-sm font-mono uppercase tracking-wider font-semibold">Amenazas Modernas & Higiene Cibernética Avanzada</span>
                    <h2 class="text-3xl sm:text-4xl font-bold mt-1">Tema 2: Internet y sus Principales Amenazas</h2>
                </div>

                <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                    <!-- Threat Taxonomy -->
                    <div class="space-y-6">
                        <div class="bg-cyber-card p-6 rounded-2xl border border-cyber-border">
                            <h3 class="text-xl font-bold text-cyber-red flex items-center gap-2 mb-3">
                                <i class="fa-solid fa-bug"></i> El Factor Humano e Ingeniería Social
                            </h3>
                            <p class="text-xs text-slate-300 mb-4 leading-relaxed">
                                Los atacantes explotan sesgos cognitivos primarios mediante las 6 reglas de la persuasión de Robert Cialdini: <strong>Reciprocidad, Escasez, Autoridad, Consistencia, Simpatía y Prueba Social</strong>.
                            </p>

                            <h4 class="text-sm font-bold text-white mb-3 border-b border-cyber-border pb-2">Taxonomía Completa de Amenazas</h4>
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3 text-xs">
                                <div class="p-3.5 bg-cyber-black rounded-xl border border-cyber-border">
                                    <strong class="text-cyber-cyan block mb-1">Phishing & Spearfishing con IA</strong>
                                    Correos engañosos generados por IA que eliminan errores ortográficos para hiperpersonalizar ataques.
                                </div>
                                <div class="p-3.5 bg-cyber-black rounded-xl border border-cyber-border">
                                    <strong class="text-cyber-red block mb-1">Ransomware de Extorsión Múltiple</strong>
                                    Cifrado de datos y amenaza de divulgación o ataques DDoS si no se realiza el pago del rescate.
                                </div>
                                <div class="p-3.5 bg-cyber-black rounded-xl border border-cyber-border">
                                    <strong class="text-amber-400 block mb-1">Troyanos & Drive-By Downloads</strong>
                                    Malware oculto en programas legítimos o infecciones al visitar sitios web vulnerables.
                                </div>
                                <div class="p-3.5 bg-cyber-black rounded-xl border border-cyber-border">
                                    <strong class="text-purple-400 block mb-1">Túnel DNS (RFC 1035 Abuse)</strong>
                                    Exfiltración encubierta de datos a través de peticiones de consulta DNS para evadir cortafuegos.
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- 4 Pillars of Cyber Hygiene -->
                    <div class="space-y-6">
                        <div class="bg-cyber-card p-6 rounded-2xl border border-cyber-border">
                            <h3 class="text-xl font-bold text-cyber-green flex items-center gap-2 mb-4">
                                <i class="fa-solid fa-kit-medical"></i> Kit de Supervivencia: Matriz de los 4 Pilares
                            </h3>
                            <div class="space-y-3 text-xs">
                                <div class="flex items-start gap-3 p-3.5 bg-cyber-black rounded-xl border-l-4 border-cyber-cyan">
                                    <div class="text-cyber-cyan text-lg mt-0.5"><i class="fa-solid fa-key"></i></div>
                                    <div>
                                        <strong class="text-white block text-sm">1. Candados de Titanio (MFA / 2FA & FIDO2)</strong>
                                        Autenticación multifactor con aplicaciones TOTP (Google/Microsoft Authenticator) o llaves hardware FIDO2.
                                    </div>
                                </div>
                                <div class="flex items-start gap-3 p-3.5 bg-cyber-black rounded-xl border-l-4 border-cyber-green">
                                    <div class="text-cyber-green text-lg mt-0.5"><i class="fa-solid fa-syringe"></i></div>
                                    <div>
                                        <strong class="text-white block text-sm">2. Vacunas Digitales (EDR & Parches)</strong>
                                        Antivirus heurístico EDR con parches automatizados de seguridad.
                                    </div>
                                </div>
                                <div class="flex items-start gap-3 p-3.5 bg-cyber-black rounded-xl border-l-4 border-cyber-blue">
                                    <div class="text-cyber-blue text-lg mt-0.5"><i class="fa-solid fa-user-lock"></i></div>
                                    <div>
                                        <strong class="text-white block text-sm">3. El Túnel Secreto (VPN en Redes Públicas)</strong>
                                        Navegación en redes Wi-Fi abiertas únicamente a través de VPN cifrada (AES-256).
                                    </div>
                                </div>
                                <div class="flex items-start gap-3 p-3.5 bg-cyber-black rounded-xl border-l-4 border-amber-400">
                                    <div class="text-amber-400 text-lg mt-0.5"><i class="fa-solid fa-fire"></i></div>
                                    <div>
                                        <strong class="text-white block text-sm">4. Tierra Quemada (Destrucción Segura)</strong>
                                        Sanitización de datos (NIST SP 800-88) y destrucción física de unidades inservibles.
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- SIMULADOR INTERACTIVO TEMA 2: EVALUADOR DE CONTRASEÑAS -->
                <div id="sim-tema2" class="mt-8 pt-8 border-t border-cyber-border scroll-mt-24">
                    <div class="bg-cyber-card p-6 rounded-2xl border border-cyber-cyan/40 shadow-xl space-y-4">
                        <h3 class="text-lg font-bold text-cyber-cyan flex items-center gap-2">
                            <i class="fa-solid fa-calculator"></i> Simulador Tema 2: Evaluador de Fortalecimiento de Contraseñas
                        </h3>
                        <p class="text-xs text-slate-300">Prueba la solidez de una clave en tiempo real (procesado únicamente en tu navegador sin enviar datos a la red).</p>

                        <div class="grid grid-cols-1 md:grid-cols-2 gap-6 items-center">
                            <div class="space-y-3">
                                <div>
                                    <label class="block text-xs font-mono text-slate-400 mb-1">Ingresa una contraseña simulada:</label>
                                    <input type="password" id="pass-input" placeholder="Ej: P@ssw0rd2026!Sec" class="w-full px-4 py-3 bg-cyber-black border border-cyber-border rounded-xl text-sm focus:outline-none focus:border-cyber-cyan font-mono text-white">
                                </div>

                                <div class="space-y-2 text-xs font-mono">
                                    <div class="flex justify-between">
                                        <span>Nivel de Fortaleza:</span>
                                        <span id="pass-strength-text" class="font-bold text-slate-400">Esperando entrada...</span>
                                    </div>
                                    <div class="w-full h-2 bg-cyber-black rounded-full overflow-hidden border border-cyber-border">
                                        <div id="pass-strength-bar" class="h-full w-0 bg-red-500 transition-all duration-300"></div>
                                    </div>
                                    <div id="pass-time" class="text-[11px] text-slate-400">Tiempo estimado para vulnerarla por fuerza bruta: --</div>
                                </div>
                            </div>

                            <div class="p-4 bg-cyber-black rounded-xl text-xs space-y-2 text-slate-300">
                                <strong class="text-cyber-green block mb-1">Requisitos de Seguridad Cumplidos:</strong>
                                <div id="req-length" class="flex items-center gap-2"><i class="fa-solid fa-circle text-[8px] text-slate-600"></i> Al menos 12-16 caracteres</div>
                                <div id="req-upper" class="flex items-center gap-2"><i class="fa-solid fa-circle text-[8px] text-slate-600"></i> Mayúsculas y minúsculas combinadas</div>
                                <div id="req-num" class="flex items-center gap-2"><i class="fa-solid fa-circle text-[8px] text-slate-600"></i> Números y Símbolos especiales (!@#$%^&*)</div>
                                <div id="req-dict" class="flex items-center gap-2"><i class="fa-solid fa-circle text-[8px] text-slate-600"></i> Sin palabras comunes ni secuencias sencillas</div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- TEMA 3 SECTION -->
        <section id="tema3" class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 scroll-mt-24">
            <div class="bg-cyber-dark border border-cyber-border rounded-3xl p-6 sm:p-10 relative overflow-hidden">
                <div class="absolute top-0 right-0 px-6 py-2 bg-cyber-blue/10 text-cyber-blue font-mono text-xs rounded-bl-2xl border-l border-b border-cyber-blue/30 uppercase tracking-widest font-bold">
                    Módulo 3
                </div>

                <div class="mb-8">
                    <span class="text-cyber-blue text-sm font-mono uppercase tracking-wider font-semibold">Entorno Académico Digital & Protección de Infraestructuras</span>
                    <h2 class="text-3xl sm:text-4xl font-bold mt-1">Tema 3: Ciberseguridad Escolar y el Campus Digital</h2>
                </div>

                <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                    <!-- School Cyber Ecosystem -->
                    <div class="space-y-6">
                        <div class="bg-cyber-card p-6 rounded-2xl border border-cyber-border">
                            <h3 class="text-xl font-bold text-cyber-cyan flex items-center gap-2 mb-4">
                                <i class="fa-solid fa-graduation-cap"></i> El Campus Invisible y sus Superficies de Ataque
                            </h3>
                            <p class="text-xs text-slate-300 mb-4 leading-relaxed">
                                La rápida digitalización educativa ha expandido la superficie de vulnerabilidad institucional hacia plataformas en la nube (LMS como Google Classroom, Moodle, Canvas), expedientes académicos digitales y APIs de consulta de calificaciones.
                            </p>
                            <div class="space-y-3 text-xs">
                                <div class="p-3.5 bg-cyber-black rounded-xl border border-cyber-border">
                                    <strong class="text-amber-400 block mb-1">Puntos Ciegos en la Infraestructura Tecnológica Escolar</strong>
                                    Errores de configuración por omisión en repositorios de almacenamiento público por defecto, servidores sin parchar e infiltración a través de proveedores externos en la cadena de suministro.
                                </div>
                                <div class="p-3.5 bg-cyber-black rounded-xl border border-cyber-border">
                                    <strong class="text-cyber-red block mb-1">Trampas en Tareas y Material Didáctico Infectado</strong>
                                    Distribución de malware mediante repositorios desregulados de tareas o archivos en formato "PDF trampa" infectados con scripts maliciosos.
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- School Defensive Arsenal -->
                    <div class="space-y-6">
                        <div class="bg-cyber-card p-6 rounded-2xl border border-cyber-border">
                            <h3 class="text-xl font-bold text-cyber-green flex items-center gap-2 mb-4">
                                <i class="fa-solid fa-shield-virus"></i> Estrategias Defensivas e Infraestructura Institucional
                            </h3>
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3 text-xs">
                                <div class="p-3.5 bg-cyber-black rounded-xl border border-cyber-border">
                                    <strong class="text-cyber-green block mb-1"><i class="fa-solid fa-copy"></i> Respaldos 3-2-1-1-0</strong>
                                    3 copias de datos, 2 medios distintos, 1 en la nube, 1 inmutable desconectada y 0 errores tras restauraciones de prueba.
                                </div>
                                <div class="p-3.5 bg-cyber-black rounded-xl border border-cyber-border">
                                    <strong class="text-cyber-cyan block mb-1"><i class="fa-solid fa-vault"></i> Cifrado de Bóveda (AES-256)</strong>
                                    Cifrado riguroso de expedientes estudiantiles en reposo y en tránsito (HTTPS/TLS 1.3).
                                </div>
                                <div class="p-3.5 bg-cyber-black rounded-xl border border-cyber-border">
                                    <strong class="text-cyber-blue block mb-1"><i class="fa-solid fa-network-wired"></i> Segmentación por VLANs</strong>
                                    Aislamiento de la red Wi-Fi de alumnos de las redes críticas de control administrativo.
                                </div>
                                <div class="p-3.5 bg-cyber-black rounded-xl border border-cyber-border">
                                    <strong class="text-amber-400 block mb-1"><i class="fa-solid fa-shield-cat"></i> Plan de Respuesta (NIST SP 800-61)</strong>
                                    Protocolo institucional formalizado para contención y recuperación efectiva de incidentes.
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- SIMULADOR INTERACTIVO TEMA 3: AUDITORÍA ESCOLAR -->
                <div id="sim-tema3" class="mt-8 pt-8 border-t border-cyber-border scroll-mt-24">
                    <div class="bg-cyber-card p-6 rounded-2xl border border-cyber-green/40">
                        <div class="flex items-center justify-between mb-3">
                            <h3 class="text-base font-bold text-cyber-green flex items-center gap-2">
                                <i class="fa-solid fa-list-check"></i> Simulador Tema 3: Auditoría de Higiene Digital Escolar
                            </h3>
                            <span id="audit-score-text" class="font-mono font-bold text-cyber-green text-lg">0% Resiliencia</span>
                        </div>
                        <p class="text-xs text-slate-300 mb-4">Evalúa los controles implementados en tu entorno educativo o personal seleccionando las casillas cumplidas:</p>
                        
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-3 text-xs font-mono" id="school-audit-checklist">
                            <label class="flex items-center gap-3 p-3 bg-cyber-black rounded-xl cursor-pointer hover:bg-cyber-border transition-colors">
                                <input type="checkbox" onchange="calcAuditScore()" class="audit-cb accent-cyber-green w-4 h-4">
                                <span>Respaldos automáticos 3-2-1 inmutables activos</span>
                            </label>
                            <label class="flex items-center gap-3 p-3 bg-cyber-black rounded-xl cursor-pointer hover:bg-cyber-border transition-colors">
                                <input type="checkbox" onchange="calcAuditScore()" class="audit-cb accent-cyber-green w-4 h-4">
                                <span>2FA / MFA obligatorio en cuentas docentes e institucionales</span>
                            </label>
                            <label class="flex items-center gap-3 p-3 bg-cyber-black rounded-xl cursor-pointer hover:bg-cyber-border transition-colors">
                                <input type="checkbox" onchange="calcAuditScore()" class="audit-cb accent-cyber-green w-4 h-4">
                                <span>Redes Wi-Fi aisladas mediante segmentación por VLANs</span>
                            </label>
                            <label class="flex items-center gap-3 p-3 bg-cyber-black rounded-xl cursor-pointer hover:bg-cyber-border transition-colors">
                                <input type="checkbox" onchange="calcAuditScore()" class="audit-cb accent-cyber-green w-4 h-4">
                                <span>Filtrado web activo e inspección de adjuntos (.exe, .scr, .vbs)</span>
                            </label>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- TEMA 4 SECTION -->
        <section id="tema4" class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 scroll-mt-24">
            <div class="bg-cyber-dark border border-cyber-border rounded-3xl p-6 sm:p-10 relative overflow-hidden">
                <div class="absolute top-0 right-0 px-6 py-2 bg-amber-400/10 text-amber-400 font-mono text-xs rounded-bl-2xl border-l border-b border-amber-400/30 uppercase tracking-widest font-bold">
                    Módulo 4
                </div>

                <div class="mb-8">
                    <span class="text-amber-400 text-sm font-mono uppercase tracking-wider font-semibold">Vulnerabilidades de Usuario & Estafas Digitales</span>
                    <h2 class="text-3xl sm:text-4xl font-bold mt-1">Tema 4: Mal Uso de Internet y Fraude Electrónico</h2>
                </div>

                <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                    <!-- Fraud Variants -->
                    <div class="space-y-6">
                        <div class="bg-cyber-card p-6 rounded-2xl border border-cyber-border">
                            <h3 class="text-xl font-bold text-amber-400 flex items-center gap-2 mb-4">
                                <i class="fa-solid fa-mask"></i> Anatomía de Correos Falsos y Vectores de Engaño
                            </h3>
                            <p class="text-xs text-slate-300 mb-4 leading-relaxed">
                                El análisis exhaustivo de cabeceras requiere verificar los mecanismos: <strong>SPF, DKIM y DMARC</strong>.
                            </p>
                            <div class="space-y-3 text-xs">
                                <div class="p-3.5 bg-cyber-black rounded-xl">
                                    <strong class="text-cyber-cyan block mb-1">Phishing, Smishing y Vishing con Clonación de Voz</strong>
                                    Ingeniería social mediante correos, SMS y llamadas telefónicas impulsadas por clonación de voz con Inteligencia Artificial.
                                </div>
                                <div class="p-3.5 bg-cyber-black rounded-xl">
                                    <strong class="text-amber-400 block mb-1">Compromiso de Correo Comercial (BEC / CEO Fraud)</strong>
                                    Suplantación de identidad de directivos para solicitar transferencias fraudulentas.
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="space-y-6">
                        <div class="bg-cyber-card p-6 rounded-2xl border border-cyber-border">
                            <h3 class="text-base font-bold text-slate-200 mb-2">Verificación Técnica HTTPS y SSL/TLS</h3>
                            <p class="text-xs text-slate-300 leading-relaxed">
                                Es vital revisar la Autoridad Certificadora (CA) y prevenir ataques de <em>Typosquatting</em> o alteración tipográfica de caracteres Unicode (Punycode).
                            </p>
                        </div>
                    </div>
                </div>

                <!-- SIMULADOR INTERACTIVO TEMA 4: PHISHING DETECTOR -->
                <div id="sim-tema4" class="mt-8 pt-8 border-t border-cyber-border scroll-mt-24">
                    <div class="bg-cyber-card p-6 rounded-2xl border border-cyber-cyan/40">
                        <div class="flex items-center justify-between mb-4">
                            <h3 class="text-lg font-bold text-cyber-cyan flex items-center gap-2">
                                <i class="fa-solid fa-envelope-open-text"></i> Simulador Tema 4: Detección de Phishing y Fraude (8 Casos Prácticos)
                            </h3>
                            <span id="phish-counter" class="text-xs font-mono text-slate-400">Caso 1 de 8</span>
                        </div>

                        <div id="phish-box" class="p-4 bg-cyber-black rounded-xl border border-cyber-border space-y-3 text-xs">
                            <!-- Dynamic content via JS -->
                        </div>

                        <div class="flex gap-3 mt-4">
                            <button onclick="evalPhish(true)" class="flex-1 py-3 rounded-xl bg-red-600/20 border border-red-500 text-red-400 font-bold text-xs hover:bg-red-500 hover:text-white transition-all">
                                <i class="fa-solid fa-triangle-exclamation"></i> ¡Es PHISHING!
                            </button>
                            <button onclick="evalPhish(false)" class="flex-1 py-3 rounded-xl bg-green-600/20 border border-green-500 text-green-400 font-bold text-xs hover:bg-green-500 hover:text-white transition-all">
                                <i class="fa-solid fa-circle-check"></i> Es LEGÍTIMO
                            </button>
                        </div>

                        <div id="phish-feedback" class="hidden mt-3 p-3 rounded-xl text-xs font-semibold text-center"></div>
                    </div>
                </div>
            </div>
        </section>

        <!-- TEMA 5 SECTION -->
        <section id="tema5" class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 scroll-mt-24">
            <div class="bg-cyber-dark border border-cyber-border rounded-3xl p-6 sm:p-10 relative overflow-hidden">
                <div class="absolute top-0 right-0 px-6 py-2 bg-cyber-red/10 text-cyber-red font-mono text-xs rounded-bl-2xl border-l border-b border-cyber-red/30 uppercase tracking-widest font-bold">
                    Módulo 5
                </div>

                <div class="mb-8">
                    <span class="text-cyber-red text-sm font-mono uppercase tracking-wider font-semibold">Marco Normativo, Delitos Digitales & Legislación Nacional</span>
                    <h2 class="text-3xl sm:text-4xl font-bold mt-1">Tema 5: Delitos Cibernéticos, Violencia Digital y Marco Normativo</h2>
                </div>

                <div class="grid grid-cols-1 lg:grid-cols-12 gap-8">
                    <!-- Glossary of Digital Crimes -->
                    <div class="lg:col-span-8 space-y-6">
                        <div class="bg-cyber-card p-6 rounded-2xl border border-cyber-border">
                            <h3 class="text-xl font-bold text-cyber-red flex items-center gap-2 mb-4">
                                <i class="fa-solid fa-gavel"></i> Anatomía y Glosario Extendido de Delitos Cibernéticos
                            </h3>
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3 text-xs">
                                <div class="p-3.5 bg-cyber-black rounded-xl border border-cyber-border">
                                    <span class="text-cyber-cyan font-bold block mb-1">Ley Olimpia (Código Penal Federal Art. 199 Octies)</span>
                                    Sanciona la violación a la intimidad sexual mediante la divulgación, compilación o comercialización no consentida de contenido íntimo.
                                </div>
                                <div class="p-3.5 bg-cyber-black rounded-xl border border-cyber-border">
                                    <span class="text-cyber-red font-bold block mb-1">Grooming & ESCNNA</span>
                                    Acoso deliberado de un adulto hacia menores mediante perfiles falsos con fines de explotación sexual (Art. 209 Bis).
                                </div>
                                <div class="p-3.5 bg-cyber-black rounded-xl border border-cyber-border">
                                    <span class="text-amber-400 font-bold block mb-1">Sextorsión & Doxing</span>
                                    Chantaje bajo amenaza de difundir imágenes íntimas y publicación no consentida de datos privados.
                                </div>
                                <div class="p-3.5 bg-cyber-black rounded-xl border border-cyber-border">
                                    <span class="text-purple-400 font-bold block mb-1">Cryptojacking & Usurpación de Identidad</span>
                                    Uso no autorizado del procesador para minar criptomonedas y suplantación de identidad (Art. 430).
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Action & Reporting Protocol -->
                    <div class="lg:col-span-4 space-y-6">
                        <div class="bg-cyber-card p-6 rounded-2xl border border-cyber-red/40 space-y-4">
                            <h3 class="text-lg font-bold text-cyber-red flex items-center gap-2">
                                <i class="fa-solid fa-phone-volume"></i> Denuncia y Protocolos Legales en México
                            </h3>
                            <p class="text-xs text-slate-300">
                                Canales oficiales institucionales para reporte de ciberdelictivos:
                            </p>
                            <div class="space-y-3 text-xs">
                                <div class="p-3.5 bg-cyber-black rounded-xl border border-cyber-border">
                                    <strong class="text-cyber-cyan block">Guardia Nacional - CERT-MX</strong>
                                    Línea directa 24/7: <span class="text-white font-mono">088</span> / cert-mx@gn.gob.mx
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- SIMULADOR INTERACTIVO TEMA 5: ANALIZADOR DE CASOS LEGALES -->
                <div id="sim-tema5" class="mt-8 pt-8 border-t border-cyber-border scroll-mt-24">
                    <div class="bg-cyber-card p-6 rounded-2xl border border-cyber-red/40">
                        <h3 class="text-lg font-bold text-cyber-red flex items-center gap-2 mb-3">
                            <i class="fa-solid fa-scale-balanced"></i> Simulador Tema 5: Analizador de Casos de Violencia Digital y Normativa
                        </h3>
                        <p class="text-xs text-slate-300 mb-4">Selecciona un caso ficticio para determinar el marco legal correspondiente y la autoridad ante la cual denunciar:</p>

                        <div class="grid grid-cols-1 md:grid-cols-3 gap-4 text-xs">
                            <div onclick="showLegalCase(1)" class="p-4 bg-cyber-black rounded-xl border border-cyber-border hover:border-cyber-red cursor-pointer transition-all">
                                <strong class="text-cyber-cyan block mb-1"><i class="fa-solid fa-image"></i> Caso A: Difusión no Consentida</strong>
                                Un alumno comparte fotografías íntimas de su expareja en un grupo de mensajería escolar.
                            </div>
                            <div onclick="showLegalCase(2)" class="p-4 bg-cyber-black rounded-xl border border-cyber-border hover:border-cyber-red cursor-pointer transition-all">
                                <strong class="text-amber-400 block mb-1"><i class="fa-solid fa-user-ninja"></i> Caso B: Perfil Falso y Acoso a Menor</strong>
                                Un usuario adulto crea una cuenta falsa para solicitar imágenes a estudiantes de bachillerato.
                            </div>
                            <div onclick="showLegalCase(3)" class="p-4 bg-cyber-black rounded-xl border border-cyber-border hover:border-cyber-red cursor-pointer transition-all">
                                <strong class="text-purple-400 block mb-1"><i class="fa-solid fa-address-card"></i> Caso C: Publicación de Datos Privados</strong>
                                Un atacante publica la dirección y teléfono de un docente amenazándolo en redes sociales.
                            </div>
                        </div>

                        <div id="legal-case-result" class="hidden mt-4 p-4 bg-cyber-black rounded-xl border border-cyber-red text-xs space-y-2">
                            <!-- Dynamic legal resolution details -->
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- SECTION: FAQ EXPERTO -->
        <section id="faq" class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 scroll-mt-24">
            <div class="bg-cyber-dark border border-cyber-border rounded-3xl p-6 sm:p-10 relative">
                <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 mb-8">
                    <div>
                        <span class="text-cyber-green text-sm font-mono uppercase tracking-wider font-semibold">Entrevista Exclusiva 2026</span>
                        <h2 class="text-3xl sm:text-4xl font-bold mt-1">Preguntas Frecuentes al Experto (FAQ)</h2>
                        <p class="text-xs text-slate-400 mt-1">31 respuestas fundamentales para la protección de la ciudadanía y la comunidad académica.</p>
                    </div>

                    <!-- Live Search Filter -->
                    <div class="relative w-full md:w-80">
                        <i class="fa-solid fa-magnifying-glass absolute left-3 top-3.5 text-slate-500 text-xs"></i>
                        <input type="text" id="faq-search" placeholder="Buscar en las 31 preguntas..." class="w-full pl-9 pr-4 py-2.5 bg-cyber-black border border-cyber-border rounded-xl text-xs text-white focus:outline-none focus:border-cyber-green font-mono">
                    </div>
                </div>

                <!-- FAQ Accordion Container -->
                <div id="faq-accordion-container" class="space-y-3">
                    <!-- Dynamic Accordions -->
                </div>
            </div>
        </section>

        <!-- FUENTES Y REFERENCIAS -->
        <section id="fuentes" class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 scroll-mt-24">
            <div class="bg-cyber-dark border border-cyber-border rounded-3xl p-6 sm:p-10">
                <div class="mb-6">
                    <span class="text-cyber-cyan text-sm font-mono uppercase tracking-wider font-semibold">Respaldo Académico & Estándares de la Industria</span>
                    <h2 class="text-3xl font-bold mt-1">Fuentes de Información y Referencias Consultadas</h2>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-6 text-xs text-slate-300">
                    <div class="bg-cyber-card p-5 rounded-2xl border border-cyber-border space-y-3">
                        <h3 class="text-sm font-bold text-cyber-cyan flex items-center gap-2">
                            <i class="fa-solid fa-book-bookmark"></i> Fuentes Principales del Curso y Literatura
                        </h3>
                        <ul class="space-y-2 list-disc pl-4">
                            <li>Curso <em>"Fundamentos de la Ciberseguridad"</em>, Dirección General de Educación Tecnológica Industrial y de Servicios (DGETI) / CBTis N° 166 "Pablo Torres Burgos", Impartido por Rodolfo Villa Noriega, México, 2026.</li>
                            <li>Materiales Didácticos de las Sesiones 1 a 5, Desarrollados por Rodolfo Villa Noriega (2026).</li>
                            <li>Entrevista Documental al Experto en Ciberseguridad (Compendio didáctico de 31 preguntas, 2026).</li>
                            <li>Stallings, W. (2018). <em>Computer Security: Principles and Practice</em>. Pearson.</li>
                            <li>Mitnick, K. D. (2002). <em>The Art of Deception: Controlling the Human Element of Security</em>. Wiley.</li>
                        </ul>
                    </div>

                    <div class="bg-cyber-card p-5 rounded-2xl border border-cyber-border space-y-3">
                        <h3 class="text-sm font-bold text-cyber-green flex items-center gap-2">
                            <i class="fa-solid fa-globe"></i> Marcos Internacionales, RFCs y Legislación
                        </h3>
                        <ul class="space-y-2 list-disc pl-4">
                            <li>National Institute of Standards and Technology (NIST). (2024). <em>NIST Cybersecurity Framework (CSF) 2.0</em>.</li>
                            <li>NIST SP 800-207. (2020). <em>Zero Trust Architecture</em>.</li>
                            <li>ISO/IEC 27001:2022. <em>Information security management systems — Requirements</em>.</li>
                            <li>OWASP Foundation. (2021). <em>OWASP Top 10 Web Application Security Risks</em>.</li>
                            <li>CISA. (2023). <em>StopRansomware Guide & Zero Trust Maturity Model 2.0</em>.</li>
                            <li>Cámara de Diputados. <em>Código Penal Federal (Ley Olimpia Arts. 199 Octies, 209 Bis, 430)</em>.</li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>

        <!-- ACERCA DEL AUTOR -->
        <section id="autor" class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 scroll-mt-24">
            <div class="bg-cyber-dark border border-cyber-cyan/40 rounded-3xl p-6 sm:p-10 relative overflow-hidden">
                <div class="flex items-center justify-between mb-6">
                    <div>
                        <span class="text-cyber-cyan text-sm font-mono uppercase tracking-wider font-semibold">Perfil Docente / Creador</span>
                        <h2 class="text-3xl font-bold mt-1">Acerca del Autor</h2>
                    </div>
                    <button onclick="openAuthorModal()" class="px-4 py-2 rounded-xl bg-cyber-card border border-cyber-cyan text-cyber-cyan text-xs font-bold hover:bg-cyber-cyan hover:text-cyber-black transition-all flex items-center gap-2">
                        <i class="fa-solid fa-pen-to-square"></i> Editar Mi Información
                    </button>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-12 gap-8 items-center">
                    <div class="md:col-span-4 text-center">
                        <div class="w-32 h-32 mx-auto rounded-full bg-gradient-to-tr from-cyber-cyan to-cyber-green p-1 neon-glow-cyan mb-4">
                            <div class="w-full h-full rounded-full bg-cyber-black flex items-center justify-center text-4xl text-cyber-cyan">
                                <i class="fa-solid fa-user-shield"></i>
                            </div>
                        </div>
                        <h3 id="display-author-name" class="text-xl font-bold text-white">Rodolfo Villa Noriega</h3>
                        <p id="display-author-role" class="text-xs text-cyber-cyan font-mono mt-1">Docente / Especialista en Cultura Digital y Ciberseguridad</p>
                        <p id="display-author-inst" class="text-xs text-slate-400 mt-1">CBTis N° 166 "Pablo Torres Burgos" / DGETI</p>
                    </div>

                    <div class="md:col-span-8 space-y-4 text-xs text-slate-300">
                        <div class="bg-cyber-card p-5 rounded-2xl border border-cyber-border space-y-2">
                            <h4 class="font-bold text-white text-sm">Biografía Profesional</h4>
                            <p id="display-author-bio" class="leading-relaxed">
                                Rodolfo Villa Noriega es docente e investigador comprometido con la educación tecnológica y el fortalecimiento de la cultura de seguridad en entornos digitales educativos. Especialista en arquitecturas de información, prevención de riesgos digitales e higiene cibernética.
                            </p>
                        </div>

                        <div class="bg-cyber-card p-4 rounded-2xl border border-cyber-border grid grid-cols-1 sm:grid-cols-3 gap-3 font-mono">
                            <div>
                                <span class="text-slate-500 block text-[10px]">Correo Electrónico:</span>
                                <span id="display-author-email" class="text-cyber-cyan">rodolfo.villa@cbtis166.edu.mx</span>
                            </div>
                            <div>
                                <span class="text-slate-500 block text-[10px]">Teléfono Institucional:</span>
                                <span id="display-author-phone" class="text-cyber-green">+52 (777) 123-4567</span>
                            </div>
                            <div>
                                <span class="text-slate-500 block text-[10px]">Perfil / Red:</span>
                                <span id="display-author-link" class="text-cyber-blue">linkedin.com/in/rodolfo-villa-noriega</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

    </main>

    <!-- FOOTER -->
    <footer class="border-t border-slate-200 dark:border-cyber-border bg-slate-100 dark:bg-cyber-black py-10 text-xs text-slate-500 font-mono">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col sm:flex-row items-center justify-between gap-4">
            <div class="flex items-center gap-2">
                <i class="fa-solid fa-shield-halved text-cyber-cyan"></i>
                <span>Fundamentos de la Ciberseguridad © 2026 | Rodolfo Villa Noriega — DGETI / CBTis N° 166</span>
            </div>
            <div>
                Cumple Estándares Accessibility WCAG 2.1 AA | NIST CSF 2.0
            </div>
        </div>
    </footer>

    <!-- AUTHOR EDIT MODAL -->
    <div id="author-modal" class="fixed inset-0 bg-black/80 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
        <div class="bg-cyber-dark border border-cyber-cyan rounded-2xl max-w-lg w-full p-6 space-y-4 relative">
            <h3 class="text-lg font-bold text-white flex items-center gap-2">
                <i class="fa-solid fa-user-pen text-cyber-cyan"></i> Editar Perfil del Autor
            </h3>
            <div class="space-y-3 text-xs">
                <div>
                    <label class="block text-slate-400 mb-1">Nombre Completo:</label>
                    <input type="text" id="input-author-name" class="w-full p-2.5 bg-cyber-black border border-cyber-border rounded-xl text-white">
                </div>
                <div>
                    <label class="block text-slate-400 mb-1">Cargo / Titulación:</label>
                    <input type="text" id="input-author-role" class="w-full p-2.5 bg-cyber-black border border-cyber-border rounded-xl text-white">
                </div>
                <div>
                    <label class="block text-slate-400 mb-1">Institución:</label>
                    <input type="text" id="input-author-inst" class="w-full p-2.5 bg-cyber-black border border-cyber-border rounded-xl text-white">
                </div>
                <div>
                    <label class="block text-slate-400 mb-1">Biografía Profesional:</label>
                    <textarea id="input-author-bio" rows="3" class="w-full p-2.5 bg-cyber-black border border-cyber-border rounded-xl text-white"></textarea>
                </div>
                <div class="grid grid-cols-2 gap-2">
                    <div>
                        <label class="block text-slate-400 mb-1">Correo Electrónico:</label>
                        <input type="text" id="input-author-email" class="w-full p-2.5 bg-cyber-black border border-cyber-border rounded-xl text-white">
                    </div>
                    <div>
                        <label class="block text-slate-400 mb-1">Teléfono:</label>
                        <input type="text" id="input-author-phone" class="w-full p-2.5 bg-cyber-black border border-cyber-border rounded-xl text-white">
                    </div>
                </div>
            </div>
            <div class="flex justify-end gap-2 pt-2">
                <button onclick="closeAuthorModal()" class="px-4 py-2 rounded-xl bg-cyber-black text-slate-400 hover:text-white">Cancelar</button>
                <button onclick="saveAuthorData()" class="px-4 py-2 rounded-xl bg-cyber-cyan text-cyber-black font-bold">Guardar Cambios</button>
            </div>
        </div>
    </div>

    <!-- JAVASCRIPT INTEGRAL -->
    <script>
        // -------------------------------------------------------------
        // 1. MINI CUESTIONARIO TEMA 1 (6 PREGUNTAS DETALLADAS)
        // -------------------------------------------------------------
        function toggleQuiz(id) {
            const el = document.getElementById(id);
            if (el) {
                el.classList.toggle('hidden');
            }
        }

        function checkQuizAnswer(qId, isCorrect) {
            const feedback = document.getElementById(`${qId}-feedback`);
            if (feedback) {
                feedback.classList.remove('hidden');
                if (isCorrect) {
                    feedback.className = "p-3 rounded-lg bg-green-900/40 text-green-400 border border-green-500 text-xs font-bold text-center";
                    feedback.innerText = "¡Correcto! La Trazabilidad (No Repudio) asegura que una acción no pueda ser negada por su autor.";
                } else {
                    feedback.className = "p-3 rounded-lg bg-red-900/40 text-red-400 border border-red-500 text-xs font-bold text-center";
                    feedback.innerText = "Incorrecto. La respuesta correcta es Trazabilidad (No Repudio).";
                }
            }
        }

        const quizQuestions = [
            {
                id: 1,
                question: "¿Cuál es el principio del Pentágono de Seguridad que garantiza que un usuario no pueda negar haber realizado una transacción digital?",
                options: ["Confidencialidad", "Disponibilidad", "Trazabilidad (No Repudio)", "Integridad"],
                correct: 2,
                explanation: "La Trazabilidad (No Repudio) garantiza la autoría innegable de una acción mediante registros SYSLOG y firma digital."
            },
            {
                id: 2,
                question: "¿Qué protocolo sustituyó a NCP el 1 de enero de 1983 (Flag Day), marcando el origen técnico de la Internet moderna?",
                options: ["HTTP / HTTPS", "TCP / IP", "DNS / BGP", "FTP / TELNET"],
                correct: 1,
                explanation: "El 1 de enero de 1983 (Flag Day), ARPANET adoptó formalmente la pila de protocolos TCP/IP (RFC 793 / 791)."
            },
            {
                id: 3,
                question: "¿Cuál es el estándar internacional supremo que certifica la implementación de un Sistema de Gestión de la Seguridad de la Información (SGSI)?",
                options: ["ISO/IEC 27001", "NIST SP 800-53", "OWASP Top 10", "PCI-DSS"],
                correct: 0,
                explanation: "ISO/IEC 27001 es la norma internacional auditable para implementar y certificar un SGSI."
            },
            {
                id: 4,
                question: "En la regla de respaldos 3-2-1-1-0, ¿qué representa la copia con valor '1' desconectada?",
                options: ["Copia en un disco duro USB local", "Copia inmutable fuera de línea (Offsite / Air-Gapped)", "Copia enviada por correo electrónico", "Impresión física en papel"],
                correct: 1,
                explanation: "Representa una copia inmutable o fuera de línea (Air-Gapped) inaccesible para malware como el Ransomware."
            },
            {
                id: 5,
                question: "¿Qué artículo del Código Penal Federal en México sanciona la violación a la intimidad sexual (Ley Olimpia)?",
                options: ["Artículo 199 Octies", "Artículo 209 Bis", "Artículo 430", "Artículo 108"],
                correct: 0,
                explanation: "El Artículo 199 Octies del Código Penal Federal sanciona la producción, almacenamiento y divulgación de contenido íntimo sin consentimiento."
            },
            {
                id: 6,
                question: "¿Cuál es la función principal de las aplicaciones de autenticación TOTP (RFC 6238) como Google o Microsoft Authenticator?",
                options: ["Cifrar el disco duro completo", "Generar códigos dinámicos temporales que cambian cada 30 segundos", "Reemplazar el antivirus", "Bloquear llamadas spam"],
                correct: 1,
                explanation: "Generan códigos temporales únicos basados en tiempo (TOTP) independientes de la red celular para añadir un factor MFA seguro."
            }
        ];

        let userQuizAnswers = {};

        function renderQuiz() {
            const container = document.getElementById('quiz-questions-container');
            container.innerHTML = '';

            quizQuestions.forEach((q, idx) => {
                const card = document.createElement('div');
                card.className = "p-4 bg-cyber-black rounded-xl border border-cyber-border space-y-3 text-xs";
                
                let optionsHtml = '';
                q.options.forEach((opt, optIdx) => {
                    optionsHtml += `
                        <button onclick="selectQuizAnswer(${q.id}, ${optIdx})" id="btn-q${q.id}-opt${optIdx}" class="w-full text-left p-3 rounded-lg bg-cyber-card border border-transparent hover:border-cyber-cyan transition-all text-slate-300">
                            <span class="font-bold text-cyber-cyan mr-2">${String.fromCharCode(65 + optIdx)})</span> ${opt}
                        </button>
                    `;
                });

                card.innerHTML = `
                    <p class="font-bold text-white text-sm"><span class="text-cyber-cyan font-mono">${idx + 1}.</span> ${q.question}</p>
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-2">${optionsHtml}</div>
                    <div id="quiz-explain-${q.id}" class="hidden p-3 rounded-lg text-xs font-semibold"></div>
                `;
                container.appendChild(card);
            });
        }

        function selectQuizAnswer(qId, selectedIdx) {
            const q = quizQuestions.find(item => item.id === qId);
            const explainBox = document.getElementById(`quiz-explain-${qId}`);
            explainBox.classList.remove('hidden');

            userQuizAnswers[qId] = (selectedIdx === q.correct);

            // Update option styles
            q.options.forEach((_, optIdx) => {
                const btn = document.getElementById(`btn-q${qId}-opt${optIdx}`);
                btn.disabled = true;
                if (optIdx === q.correct) {
                    btn.className = "w-full text-left p-3 rounded-lg bg-green-950/60 border border-green-500 text-green-300 font-bold";
                } else if (optIdx === selectedIdx) {
                    btn.className = "w-full text-left p-3 rounded-lg bg-red-950/60 border border-red-500 text-red-300";
                }
            });

            if (selectedIdx === q.correct) {
                explainBox.className = "p-3 rounded-lg bg-green-900/40 text-green-400 border border-green-500 text-xs";
                explainBox.innerText = "¡Correcto! " + q.explanation;
            } else {
                explainBox.className = "p-3 rounded-lg bg-red-900/40 text-red-400 border border-red-500 text-xs";
                explainBox.innerText = "Incorrecto. " + q.explanation;
            }

            // Update total score
            const score = Object.values(userQuizAnswers).filter(Boolean).length;
            document.getElementById('quiz-score-badge').innerText = `Puntaje: ${score} / ${quizQuestions.length}`;
        }

        // -------------------------------------------------------------
        // 2. SIMULADOR DE DETECCIÓN DE PHISHING (8 CASOS EXTENDIDOS)
        // -------------------------------------------------------------
        const phishScenarios = [
            {
                sender: "Soporte Técnico <seguridad-dgeti@verificacion-cuenta-escuela.com>",
                subject: "¡URGENTE! Tu correo institucional será dado de baja en 2 horas",
                body: "Estimado usuario, detectamos accesos sospechosos. Haz clic aquí para ingresar tus credenciales inmediatamente o perderás tus calificaciones.",
                link: "http://login-portal-cbtis.atwebpages.com/verificar",
                isPhishing: true,
                reason: "¡Phishing detectado! El dominio del remitente no es oficial y utiliza lenguaje alarmista forzando urgencia."
            },
            {
                sender: "Dirección Académica <servicios.escolares@cbtis166.edu.mx>",
                subject: "Calendario Oficial de Evaluaciones - Período 2026",
                body: "Estimada comunidad docente y estudiantil, adjunto encontrarán la circular informativa oficial en PDF para su consulta en el portal.",
                link: "https://cbtis166.edu.mx/circulares/2026-evaluaciones.pdf",
                isPhishing: false,
                reason: "¡Correo Legítimo! Utiliza el dominio institucional oficial (@cbtis166.edu.mx) y protocolo HTTPS verificado."
            },
            {
                sender: "Banco de Notificaciones <alertas@banc0-naci0nal-sec.net>",
                subject: "Transferencia retenida por $15,000 MXN",
                body: "Se ha detectado una compra no reconocida. Ingresa tu número de tarjeta y NIP para cancelar la operación.",
                link: "http://banc0-naci0nal-sec.net/cancelar",
                isPhishing: true,
                reason: "¡Phishing grave! Inconsistencias tipográficas en el dominio (banc0 con cero) y solicitud ilegal de NIP bancario."
            },
            {
                sender: "Dirección General DGETI <direccion.ejecutiva@dgeti-gob-soporte-oficial.com>",
                subject: "Aviso Urgente: Transferencia bancaria para compra de equipos",
                body: "Estimado administrativo, requiero que realice una transferencia bancaria inmediata de $45,000 MXN para pago de licencias. No responda por teléfono, estoy en reunión.",
                link: "http://dgeti-gob-soporte-oficial.com/autorizar",
                isPhishing: true,
                reason: "¡Ataque BEC (Business Email Compromise)! Suplantación de identidad del directivo con dominio falso para autorizar fondos ilícitos."
            },
            {
                sender: "Guardia Nacional CERT-MX <cert-mx@gn.gob.mx>",
                subject: "Boletín de Ciberseguridad: Alerta sobre Ransomware en instituciones escolares",
                body: "Se emite recomendación de actualización para sistemas Windows y filtrado de extensiones .exe. Consulte la guía técnica en la plataforma oficial.",
                link: "https://www.gob.mx/guardianacional/articulos/boletin-ciberseguridad-2026",
                isPhishing: false,
                reason: "¡Notificación Legítima! Proviene del dominio oficial gubernamental (.gob.mx) con fines preventivos."
            },
            {
                sender: "WhatsApp Notificaciones <alertas-whatsapp-verificar-id.com>",
                subject: "Su código de verificación de 6 dígitos ha sido solicitado",
                body: "Alguien intentó registrar su número en otro dispositivo. Haga clic en el enlace para enviar su código SMS y recuperar el control.",
                link: "http://alertas-whatsapp-verificar-id.com/codigo",
                isPhishing: true,
                reason: "¡Smishing / Phishing de Cuentas! Ningún servicio oficial solicitará que compartas códigos SMS de verificación."
            },
            {
                sender: "Tareas y Libros Gratis <admin@descargar-tareas-gratis-pdf.net>",
                subject: "Descarga la guía completa de examen resuelta en formato ejecutable",
                body: "Descarga nuestro archivo comprimido Guia2026_Resuelta.exe.msi para abrir el libro interactivo sin pagar nada.",
                link: "http://descargar-tareas-gratis-pdf.net/files/Guia2026_Resuelta.exe",
                isPhishing: true,
                reason: "¡Malware / Drive-by Download! Los documentos de estudio legítimos son PDFs o archivos de texto, jamás ejecutables (.exe/.msi)."
            },
            {
                sender: "Ventanilla Única Nacional <no-reply@gob.mx>",
                subject: "Confirmación de trámite de beca escolar",
                body: "Su solicitud de beca ha sido registrada exitosamente. Puede consultar el folio asignado en la plataforma oficial con sus credenciales habituales.",
                link: "https://www.gob.mx/becasbenitojuarez",
                isPhishing: false,
                reason: "¡Correo Legítimo! Dominio de gobierno oficial (@gob.mx) y enlace verificado."
            }
        ];

        let currentPhishIdx = 0;

        function loadPhishScenario() {
            const sc = phishScenarios[currentPhishIdx];
            document.getElementById('phish-counter').innerText = `Caso ${currentPhishIdx + 1} de ${phishScenarios.length}`;
            document.getElementById('phish-box').innerHTML = `
                <div><span class="text-slate-500">De:</span> <span class="text-amber-400 font-mono">${sc.sender}</span></div>
                <div><span class="text-slate-500">Asunto:</span> <strong class="text-white">${sc.subject}</strong></div>
                <div class="p-3 bg-cyber-card rounded-lg my-2 text-slate-300 leading-relaxed">${sc.body}</div>
                <div><span class="text-slate-500">Enlace incluido:</span> <span class="text-cyber-cyan underline font-mono">${sc.link}</span></div>
            `;
            const fb = document.getElementById('phish-feedback');
            fb.classList.add('hidden');
        }

        function evalPhish(userSaidPhish) {
            const sc = phishScenarios[currentPhishIdx];
            const fb = document.getElementById('phish-feedback');
            fb.classList.remove('hidden');

            if (userSaidPhish === sc.isPhishing) {
                fb.className = "mt-3 p-3 rounded-xl text-xs font-semibold text-center bg-green-900/40 text-green-400 border border-green-500";
                fb.innerText = "¡Correcto! " + sc.reason;
            } else {
                fb.className = "mt-3 p-3 rounded-xl text-xs font-semibold text-center bg-red-900/40 text-red-400 border border-red-500";
                fb.innerText = "Incorrecto. " + sc.reason;
            }

            setTimeout(() => {
                currentPhishIdx = (currentPhishIdx + 1) % phishScenarios.length;
                loadPhishScenario();
            }, 4000);
        }

        // -------------------------------------------------------------
        // 3. ANALIZADOR DE CASOS LEGALES (TEMA 5)
        // -------------------------------------------------------------
        function showLegalCase(caseId) {
            const res = document.getElementById('legal-case-result');
            res.classList.remove('hidden');

            if (caseId === 1) {
                res.innerHTML = `
                    <strong class="text-cyber-cyan block text-sm mb-1"><i class="fa-solid fa-gavel"></i> Resolución Legal - Caso A: Ley Olimpia</strong>
                    <p class="text-slate-300 leading-relaxed"><strong>Calificación Jurídica:</strong> Violación a la intimidad sexual (Código Penal Federal Art. 199 Octies).</p>
                    <p class="text-slate-300 leading-relaxed"><strong>Sanción Prevista:</strong> Pena de 3 a 6 años de prisión y multa de 500 a 1,000 UMAs.</p>
                    <p class="text-cyber-green leading-relaxed"><strong>Protocolo de Acción:</strong> 1) No revictimizar. 2) Preservar evidencia digital (capturas con cabeceras/hashes). 3) Denuncia formal ante la Fiscalía del Estado o Policía Cibernética (088).</p>
                `;
            } else if (caseId === 2) {
                res.innerHTML = `
                    <strong class="text-amber-400 block text-sm mb-1"><i class="fa-solid fa-shield-cat"></i> Resolución Legal - Caso B: Grooming y ESCNNA</strong>
                    <p class="text-slate-300 leading-relaxed"><strong>Calificación Jurídica:</strong> Grooming / Corrupción de Menores (Código Penal Federal Art. 209 Bis).</p>
                    <p class="text-slate-300 leading-relaxed"><strong>Sanción Prevista:</strong> Delito grave federal con pena de prisión sin derecho a fianza.</p>
                    <p class="text-cyber-green leading-relaxed"><strong>Protocolo de Acción:</strong> Reporte inmediato al CERT-MX de la Guardia Nacional (cert-mx@gn.gob.mx) y resguardo del menor.</p>
                `;
            } else if (caseId === 3) {
                res.innerHTML = `
                    <strong class="text-purple-400 block text-sm mb-1"><i class="fa-solid fa-user-shield"></i> Resolución Legal - Caso C: Doxing y Amenazas</strong>
                    <p class="text-slate-300 leading-relaxed"><strong>Calificación Jurídica:</strong> Doxing, Vulneración de Datos Personales (LGPDPPSO) y Amenazas.</p>
                    <p class="text-slate-300 leading-relaxed"><strong>Protocolo de Acción:</strong> Reportar la publicación en la red social para remoción urgente, solicitar medidas de protección institucionales y denuncia ante el Ministerio Público.</p>
                `;
            }
        }

        // -------------------------------------------------------------
        // 4. DATA COMPLETA DE PREGUNTAS FRECUENTES (31 PREGUNTAS DE EXPERTO)
        // -------------------------------------------------------------
        const faqData = [
            { id: 1, q: "¿Qué es la ciberseguridad?", a: "Es el conjunto de herramientas, políticas, conceptos de seguridad, salvaguardas, directrices y tecnologías utilizadas para proteger los sistemas, redes, dispositivos y datos de ataques cibernéticos, accesos no autorizados y daños digitales." },
            { id: 2, q: "¿Cuál es la definición de delito informático?", a: "Es toda acción ilegal, delictiva o no autorizada que utiliza las tecnologías de la información (Internet, computadoras, software) como medio o fin para vulnerar la confidencialidad, integridad o disponibilidad de sistemas y datos." },
            { id: 3, q: "Menciona un ejemplo de delito informático que afecte a la ciudadanía.", a: "El phishing bancario para el robo de credenciales, el secuestro de información mediante ransomware a particulares, y la violencia digital o sextorsión." },
            { id: 4, q: "¿Por qué es fundamental proteger nuestros dispositivos personales?", a: "Porque contienen nuestra identidad digital, información financiera, fotos y documentos privados, y además pueden ser utilizados por cibercriminales como puente para infectar a otros contactos o redes institucionales." },
            { id: 5, q: "¿Qué combinación de elementos hace que una contraseña sea considerada segura?", a: "Una longitud mínima de 12 a 16 caracteres, combinando letras mayúsculas, minúsculas, números y símbolos especiales, sin incluir palabras de diccionario ni datos personales." },
            { id: 6, q: "¿Cómo funciona la autenticación en dos pasos (2FA / MFA)?", a: "Solicita un segundo factor de verificación independiente (como un código generado por una app TOTP, token físico o biometría) además de la contraseña tradicional para autorizar el acceso." },
            { id: 7, q: "Menciona algunas técnicas que suelen utilizar los delincuentes en un ataque de phishing.", a: "La manipulación psicológica (urgencia o miedo), la clonación de imagen institucional de bancos o escuelas, el uso de enlaces a dominios falsificados y archivos adjuntos con código malicioso." },
            { id: 8, q: "¿Cuál es el beneficio directo de mantener el software y las aplicaciones actualizadas?", a: "Corregir vulnerabilidades y fallas de seguridad conocidas (parches de seguridad), cerrando las puertas de entrada a virus y exploits." },
            { id: 9, q: "¿Qué se entiende por protección de identidad en el contexto digital?", a: "El conjunto de prácticas enfocadas en salvaguardar la información personal, credenciales, imágenes y datos biométricos para evitar que terceros los usen sin consentimiento." },
            { id: 10, q: "¿Cuál es la función de un firewall (cortafuegos)?", a: "Actuar como una barrera entre una red interna segura y redes externas (como Internet), monitoreando y filtrando el tráfico entrante y saliente según reglas de seguridad preestablecidas." },
            { id: 11, q: "¿Qué acción se recomienda ante contenidos peligrosos o retos virales dañinos en redes sociales?", a: "No interactuar ni compartirlos, bloquear la fuente, reportar la publicación inmediatamente a la plataforma y alertar a docentes o autoridades correspondientes." },
            { id: 12, q: "¿Cuál herramienta ayuda específicamente a crear y guardar contraseñas robustas de forma organizada?", a: "Un gestor de contraseñas (Password Manager) cifrado." },
            { id: 13, q: "Menciona un riesgo directo de sufrir suplantación de identidad.", a: "Pérdida financiera por fraudes o préstamos solicitados a nombre de la víctima, daño a la reputación y problemas legales derivados de delitos cometidos usando su identidad." },
            { id: 14, q: "Antes de proporcionar información personal en un sitio web, ¿qué se debe verificar?", a: "Que el sitio cuente con protocolo HTTPS (candado de seguridad), que la URL sea oficial y exacta (sin errores tipográficos), y revisar las políticas de privacidad." },
            { id: 15, q: "¿Qué componente de la seguridad digital se encarga de detectar y eliminar malware presente en el equipo?", a: "El software antivirus / antimalware o soluciones EDR (Endpoint Detection and Response)." },
            { id: 16, q: "¿Cuáles son las características de los mensajes de phishing que buscan engañar al usuario para que no verifique la información?", a: "Utilizan lenguaje alarmista o de extrema urgencia ('su cuenta será suspendida en 1 hora'), promesas de premios irreales o amenazas de sanciones inmediatas." },
            { id: 17, q: "¿Cuánto contribuye la educación en ciberseguridad a la protección ciudadana?", a: "Es el pilar fundamental; convierte al usuario de ser el eslabón más débil a ser la primera línea de defensa activa contra el cibercrimen." },
            { id: 18, q: "¿Cuáles recomendaciones se sugieren evitar al crear una contraseña para que no sea fácilmente adivinada?", a: "Evitar nombres de familiares o mascotas, fechas de nacimiento, secuencias simples ('123456', 'qwerty'), palabras comunes como 'contraseña' o 'Profe123', y no reutilizar la misma clave en varios sitios." },
            { id: 19, q: "Menciona algunas estrategias para prevenir delitos informáticos.", a: "Habilitar autenticación multifactor, realizar respaldos periódicos, usar VPN en redes públicas, mantener sistemas actualizados y capacitarse en detección de engaños digitales." },
            { id: 20, q: "En la autenticación multifactor, además de las contraseñas, ¿cuáles son otros métodos de verificación válidos?", a: "Aplicaciones de autenticación (TOTP como Google/Microsoft Authenticator), tokens de seguridad hardware (YubiKey), verificación biométrica (huella dactilar, reconocimiento facial) y claves de seguridad FIDO2." },
            { id: 21, q: "Menciona algunos riesgos que se presentan a un ciudadano que sufre ciberacoso.", a: "Daño psicológico grave, aislamiento social, ansiedad, depresión, pérdida de privacidad y posible exposición a extorsión o agresiones físicas." },
            { id: 22, q: "¿Cuál es la función de los códigos enviados al celular en un esquema de seguridad digital?", a: "Verificar en tiempo real la posesión física del dispositivo registrado por el usuario legítimo durante el proceso de inicio de sesión." },
            { id: 23, q: "¿Cuál es la importancia de no compartir información personal en redes sociales con desconocidos?", a: "Evitar que ciberdelincuentes realicen ingeniería social, perfilar hábitos para robos, o recopilar insumos para grooming, doxing o suplantación." },
            { id: 24, q: "¿Cuál es el objetivo principal de los delincuentes al distribuir virus y malware?", a: "Obtener beneficios económicos (robo de dinero/datos, rescates), espionaje o reclutamiento de equipos para redes zombi (botnets)." },
            { id: 25, q: "Menciona acciones sencillas que puede realizar cualquier ciudadano para mantener sus equipos actualizados.", a: "Activar las actualizaciones automáticas en el sistema operativo y aplicaciones, reiniciar el equipo con regularidad y descargar software únicamente de tiendas o sitios oficiales." },
            { id: 26, q: "¿Cuál es la recomendación principal respecto a los enlaces recibidos en correos sospechosos?", a: "No hacer clic en ellos bajo ninguna circunstancia, no descargar archivos adjuntos y verificar el contenido contactando a la institución por sus canales oficiales." },
            { id: 27, q: "¿Qué papel juega la responsabilidad individual en la ciberseguridad?", a: "Un papel determinante; la tecnología no puede suplir las decisiones del usuario. La concienciación y el sentido común de cada persona constituyen la defensa definitiva." },
            { id: 28, q: "¿Cómo ayudan las aplicaciones de autenticación a proteger las cuentas bancarias y personales?", a: "Generan códigos temporales dinámicos (que cambian cada 30 segundos) sin viajar por la red telefónica, impidiendo el acceso aun si la contraseña ha sido filtrada." },
            { id: 29, q: "En el contexto de la identidad digital, ¿qué objetivo tiene cuidar las fotografías que compartimos?", a: "Prevenir la sobreexposición (oversharing), proteger la privacidad propia y familiar, e impedir el mal uso de la imagen para perfiles falsos, acoso o manipulación con IA." },
            { id: 30, q: "Menciona algunas consecuencias de no tener instalado un antivirus confiable.", a: "Infección silenciosa por espías (spyware/keyloggers), secuestro de datos por ransomware, ralentización del sistema y exposición masiva de cuentas bancarias y contraseñas." },
            { id: 31, q: "¿Qué sentimiento o reacción buscan provocar los delincuentes informáticos para que sus estafas tengan éxito?", a: "Buscan detonar miedo, pánico, urgencia desmedida, curiosidad o codicia, forzando a la víctima a actuar por impulso emocional sin razonar ni verificar." }
        ];

        // RENDER FAQ ACCORDIONS WITH SEARCH
        function renderFAQ(filterText = '') {
            const container = document.getElementById('faq-accordion-container');
            container.innerHTML = '';
            
            const filtered = faqData.filter(item => 
                item.q.toLowerCase().includes(filterText.toLowerCase()) || 
                item.a.toLowerCase().includes(filterText.toLowerCase())
            );

            if (filtered.length === 0) {
                container.innerHTML = `<div class="p-4 text-center text-xs text-slate-400">No se encontraron preguntas que coincidan con "${filterText}".</div>`;
                return;
            }

            filtered.forEach(item => {
                const accordion = document.createElement('div');
                accordion.className = 'bg-cyber-card border border-cyber-border rounded-xl overflow-hidden transition-all';
                accordion.innerHTML = `
                    <button onclick="toggleFAQ(${item.id})" class="w-full p-4 text-left flex justify-between items-center hover:bg-cyber-black/50 transition-colors">
                        <span class="font-semibold text-xs sm:text-sm text-slate-200 flex items-center gap-2">
                            <span class="text-cyber-green font-mono text-xs">P${item.id}.</span> ${item.q}
                        </span>
                        <i id="faq-icon-${item.id}" class="fa-solid fa-chevron-down text-slate-400 text-xs transition-transform duration-200"></i>
                    </button>
                    <div id="faq-body-${item.id}" class="hidden p-4 pt-0 text-xs text-slate-300 leading-relaxed border-t border-cyber-border/40 bg-cyber-black/30">
                        <strong class="text-cyber-cyan block mb-1">Respuesta del Experto:</strong>
                        ${item.a}
                    </div>
                `;
                container.appendChild(accordion);
            });
        }

        function toggleFAQ(id) {
            const body = document.getElementById(`faq-body-${id}`);
            const icon = document.getElementById(`faq-icon-${id}`);
            const isHidden = body.classList.contains('hidden');
            
            if (isHidden) {
                body.classList.remove('hidden');
                icon.style.transform = 'rotate(180deg)';
            } else {
                body.classList.add('hidden');
                icon.style.transform = 'rotate(0deg)';
            }
        }

        document.getElementById('faq-search').addEventListener('input', (e) => {
            renderFAQ(e.target.value);
        });

        // -------------------------------------------------------------
        // 5. EVALUADOR DE CONTRASEÑAS EN TIEMPO REAL
        // -------------------------------------------------------------
        document.getElementById('pass-input').addEventListener('input', (e) => {
            const val = e.target.value;
            let score = 0;

            const hasUpper = /[A-Z]/.test(val);
            const hasLower = /[a-z]/.test(val);
            const hasNum = /[0-9]/.test(val);
            const hasSym = /[^A-Za-z0-9]/.test(val);
            const isLong = val.length >= 12;

            document.getElementById('req-length').children[0].className = isLong ? "fa-solid fa-circle-check text-cyber-green text-[10px]" : "fa-solid fa-circle text-[8px] text-slate-600";
            document.getElementById('req-upper').children[0].className = (hasUpper && hasLower) ? "fa-solid fa-circle-check text-cyber-green text-[10px]" : "fa-solid fa-circle text-[8px] text-slate-600";
            document.getElementById('req-num').children[0].className = (hasNum && hasSym) ? "fa-solid fa-circle-check text-cyber-green text-[10px]" : "fa-solid fa-circle text-[8px] text-slate-600";

            if (val.length === 0) {
                document.getElementById('pass-strength-text').innerText = "Esperando entrada...";
                document.getElementById('pass-strength-text').className = "font-bold text-slate-400";
                document.getElementById('pass-strength-bar').style.width = "0%";
                document.getElementById('pass-time').innerText = "Tiempo estimado para vulnerarla: --";
                return;
            }

            if (val.length > 0) score += 10;
            if (val.length >= 8) score += 20;
            if (val.length >= 12) score += 25;
            if (hasUpper && hasLower) score += 15;
            if (hasNum) score += 15;
            if (hasSym) score += 15;

            const bar = document.getElementById('pass-strength-bar');
            const text = document.getElementById('pass-strength-text');
            const time = document.getElementById('pass-time');

            bar.style.width = `${score}%`;

            if (score < 40) {
                text.innerText = "MUY DÉBIL";
                text.className = "font-bold text-red-500";
                bar.className = "h-full bg-red-500 transition-all duration-300";
                time.innerText = "Tiempo estimado para vulnerarla: Segundos / Instantáneo";
            } else if (score < 75) {
                text.innerText = "ACEPTABLE";
                text.className = "font-bold text-amber-400";
                bar.className = "h-full bg-amber-400 transition-all duration-300";
                time.innerText = "Tiempo estimado para vulnerarla: 3 a 6 Meses";
            } else {
                text.innerText = "BLINDADA (ALTA SEGURIDAD)";
                text.className = "font-bold text-cyber-green";
                bar.className = "h-full bg-cyber-green transition-all duration-300";
                time.innerText = "Tiempo estimado para vulnerarla: +400 Años (Impenetrable)";
            }
        });

        // -------------------------------------------------------------
        // 6. AUDITORÍA ESCOLAR CHECKLIST SCORE
        // -------------------------------------------------------------
        function calcAuditScore() {
            const checkboxes = document.querySelectorAll('.audit-cb');
            let checked = 0;
            checkboxes.forEach(cb => { if (cb.checked) checked++; });
            const pct = Math.round((checked / checkboxes.length) * 100);
            document.getElementById('audit-score-text').innerText = `${pct}% Resiliencia`;
        }

        // -------------------------------------------------------------
        // 7. AUTHOR MODAL EDITING SYSTEM
        // -------------------------------------------------------------
        function openAuthorModal() {
            document.getElementById('input-author-name').value = document.getElementById('display-author-name').innerText;
            document.getElementById('input-author-role').value = document.getElementById('display-author-role').innerText;
            document.getElementById('input-author-inst').value = document.getElementById('display-author-inst').innerText;
            document.getElementById('input-author-bio').value = document.getElementById('display-author-bio').innerText;
            document.getElementById('input-author-email').value = document.getElementById('display-author-email').innerText;
            document.getElementById('input-author-phone').value = document.getElementById('display-author-phone').innerText;
            document.getElementById('author-modal').classList.remove('hidden');
        }

        function closeAuthorModal() {
            document.getElementById('author-modal').classList.add('hidden');
        }

        function saveAuthorData() {
            document.getElementById('display-author-name').innerText = document.getElementById('input-author-name').value;
            document.getElementById('display-author-role').innerText = document.getElementById('input-author-role').value;
            document.getElementById('display-author-inst').innerText = document.getElementById('input-author-inst').value;
            document.getElementById('display-author-bio').innerText = document.getElementById('input-author-bio').value;
            document.getElementById('display-author-email').innerText = document.getElementById('input-author-email').value;
            document.getElementById('display-author-phone').innerText = document.getElementById('input-author-phone').value;
            closeAuthorModal();
        }

        // -------------------------------------------------------------
        // 8. THEME TOGGLE & AUTO-CLOSE MOBILE MENU FIX
        // -------------------------------------------------------------
        const themeBtn = document.getElementById('theme-toggle');
        const darkIcon = document.getElementById('theme-toggle-dark-icon');
        const lightIcon = document.getElementById('theme-toggle-light-icon');

        themeBtn.addEventListener('click', () => {
            const isDark = document.documentElement.classList.toggle('dark');
            if (isDark) {
                darkIcon.classList.remove('hidden');
                lightIcon.classList.add('hidden');
            } else {
                darkIcon.classList.add('hidden');
                lightIcon.classList.remove('hidden');
            }
        });

        // Mobile Menu Toggle & Auto-Close on Item Click
        const mobileMenu = document.getElementById('mobile-menu');
        document.getElementById('mobile-menu-btn').addEventListener('click', () => {
            mobileMenu.classList.toggle('hidden');
        });

        // Scroll Progress Indicator
        window.addEventListener('scroll', () => {
            const winScroll = document.body.scrollTop || document.documentElement.scrollTop;
            const height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
            const scrolled = (winScroll / height) * 100;
            document.getElementById('progress-bar').style.width = scrolled + '%';
        });

        // Initialize Application
        window.onload = function() {
            renderQuiz();
            renderFAQ();
            loadPhishScenario();
        }
    </script>
</body>
</html>
