[middleman_portfolio.html](https://github.com/user-attachments/files/32578230/middleman_portfolio.html)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Middleman_12345 — Roblox Bug Finder</title>
  
  <!-- Fonts & Tailwind CSS CDN -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
  <script src="https://cdn.tailwindcss.com"></script>

  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            brand: {
              bg: '#08090c',
              card: '#111319',
              cardHover: '#171a22',
              border: '#1e222d',
              accent: '#facc15', // Cheese yellow accent
              accentGlow: 'rgba(250, 204, 21, 0.15)',
              pinkAura: '#ff7eb6',
              pinkGlow: 'rgba(255, 126, 182, 0.35)'
            }
          },
          fontFamily: {
            sans: ['"Plus Jakarta Sans"', 'sans-serif'],
            mono: ['"JetBrains Mono"', 'monospace'],
          }
        }
      }
    }
  </script>

  <style>
    body {
      background-color: #08090c;
      color: #f3f4f6;
      font-family: 'Plus Jakarta Sans', sans-serif;
      overflow-x: hidden;
    }

    /* Custom Scrollbar */
    ::-webkit-scrollbar {
      width: 8px;
    }
    ::-webkit-scrollbar-track {
      background: #08090c;
    }
    ::-webkit-scrollbar-thumb {
      background: #1e222d;
      border-radius: 4px;
    }
    ::-webkit-scrollbar-thumb:hover {
      background: #2e3545;
    }

    /* Glowing Pink Aura for Villager Avatar Frame */
    @keyframes auraPulse {
      0%, 100% {
        box-shadow: 0 0 20px 4px rgba(255, 126, 182, 0.4), inset 0 0 15px rgba(255, 126, 182, 0.2);
        border-color: rgba(255, 126, 182, 0.8);
      }
      50% {
        box-shadow: 0 0 35px 8px rgba(255, 126, 182, 0.65), inset 0 0 25px rgba(255, 126, 182, 0.4);
        border-color: rgba(255, 126, 182, 1);
      }
    }

    .pink-aura {
      animation: auraPulse 3s infinite ease-in-out;
    }

    /* Floating particles canvas overlay */
    #particles-canvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 0;
    }

    .glass-card {
      background: rgba(17, 19, 25, 0.85);
      backdrop-filter: blur(12px);
      border: 1px solid #1e222d;
    }

    .glass-card-hover {
      transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    }
    .glass-card-hover:hover {
      transform: translateY(-4px);
      border-color: rgba(250, 204, 21, 0.4);
      box-shadow: 0 12px 30px -10px rgba(0, 0, 0, 0.5), 0 0 20px rgba(250, 204, 21, 0.1);
    }

    /* Toast Notification */
    #toast {
      transform: translateY(100px);
      opacity: 0;
      transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    }
    #toast.show {
      transform: translateY(0);
      opacity: 1;
    }
  </style>
</head>
<body class="relative min-h-screen">

  <canvas id="particles-canvas"></canvas>

  <!-- Notification Toast -->
  <div id="toast" class="fixed bottom-6 right-6 z-50 flex items-center gap-3 bg-brand-card border border-brand-accent/40 text-white px-5 py-3.5 rounded-xl shadow-2xl">
    <span class="text-brand-accent text-lg">✓</span>
    <span id="toast-text" class="text-sm font-medium">Copied to clipboard!</span>
  </div>

  <div class="relative z-10 max-w-5xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
    
    <header class="flex flex-col items-center text-center pt-8 pb-12">
      
      <!-- Avatar with Villager Picture & Pink Aura Frame -->
      <div class="relative mb-6 group cursor-pointer">
        <div class="relative w-32 h-32 rounded-full p-1 pink-aura border-2 transition-transform duration-500 group-hover:scale-105 overflow-hidden bg-[#1a1116] flex items-center justify-center">
          
          <!-- Villager Image -->
          <img 
            src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/items/poke-ball.png" 
            alt="Middleman_12345 Villager Avatar"
            class="w-full h-full object-cover object-top scale-110"
            onerror="this.onerror=null; this.src='https://images.wikidex.net/subidas/wikidex/4/4b/latest/20210430214828/Aldeano_JE2.png';"
          />

          <!-- Pink aura overlay blend -->
          <div class="absolute inset-0 bg-gradient-to-t from-brand-pinkAura/30 via-transparent to-transparent pointer-events-none"></div>
        </div>

        <!-- Red Status Indicator -->
        <div class="absolute bottom-1 right-1 w-7 h-7 bg-[#111319] rounded-full p-0.5 flex items-center justify-center border border-brand-border" title="Status: Active Bug Finding">
          <div class="w-full h-full bg-red-500 rounded-full flex items-center justify-center">
            <div class="w-3 h-0.5 bg-white rounded-full"></div>
          </div>
        </div>
      </div>

      <!-- Main Title and Subtext -->
      <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-brand-accentGlow border border-brand-accent/30 text-brand-accent text-xs font-semibold uppercase tracking-wider mb-3">
        <span class="w-2 h-2 rounded-full bg-brand-accent animate-ping"></span>
        Roblox Bug Finder
      </div>

      <h1 class="text-4xl sm:text-5xl font-extrabold tracking-tight text-white mb-2">
        Middleman_12345
      </h1>
      
      <p class="font-mono text-brand-accent font-medium text-sm sm:text-base mb-4">
        aka AdrianPro9222 <span class="text-gray-500">(Roblox)</span>
      </p>

      <!-- EXCLUSIVE ROLE BADGES -->
      <div class="flex flex-wrap justify-center gap-2 mb-6 max-w-lg">
        <span class="px-3.5 py-1.5 rounded-xl bg-brand-card border border-brand-border text-xs font-medium text-gray-300">🐛 Bug Finder</span>
        <span class="px-3.5 py-1.5 rounded-xl bg-brand-card border border-brand-border text-xs font-medium text-gray-300">⚡ Exploit Spotter</span>
        <span class="px-3.5 py-1.5 rounded-xl bg-brand-card border border-brand-border text-xs font-medium text-gray-300">🔍 Glitch Hunter</span>
      </div>

      <!-- Bio -->
      <p class="text-gray-400 text-base max-w-xl mb-8 leading-relaxed">
        Dedicated Roblox Bug Finder specializing in finding duplication exploits, game-breaking glitches, and performance bugs in high-traffic experiences before release.
      </p>

      <!-- Action Buttons -->
      <div class="flex flex-wrap justify-center items-center gap-4">
        <a href="#project" class="px-6 py-3 rounded-xl bg-brand-accent text-black font-bold text-sm hover:bg-yellow-400 transition-all shadow-lg shadow-brand-accent/20 flex items-center gap-2">
          <span>🧀 View Featured Project</span>
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path></svg>
        </a>
        <a href="#contact" class="px-6 py-3 rounded-xl bg-brand-card border border-brand-border text-white font-semibold text-sm hover:bg-brand-cardHover hover:border-gray-600 transition-all flex items-center gap-2">
          <span>💬 Contact Me</span>
        </a>
      </div>

      <!-- Current Status Banner -->
      <div class="mt-8 px-4 py-2 rounded-2xl bg-brand-card/90 border border-brand-border flex items-center gap-3 text-xs text-gray-400">
        <span class="flex h-2.5 w-2.5 relative">
          <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-emerald-400 opacity-75"></span>
          <span class="relative inline-flex rounded-full h-2.5 w-2.5 bg-emerald-500"></span>
        </span>
        <span>Active Bug Finder for: <strong class="text-white">Stream A Cheese Pull! (30K CCU)</strong></span>
      </div>
    </header>

    <section class="grid grid-cols-2 lg:grid-cols-4 gap-4 mb-16">
      <div class="glass-card glass-card-hover p-6 rounded-2xl text-center">
        <div class="text-3xl sm:text-4xl font-extrabold text-brand-accent font-mono mb-1">30,000+</div>
        <div class="text-xs font-medium text-gray-400 uppercase tracking-wider">Peak CCU</div>
      </div>
      <div class="glass-card glass-card-hover p-6 rounded-2xl text-center">
        <div class="text-3xl sm:text-4xl font-extrabold text-brand-accent font-mono mb-1">50+</div>
        <div class="text-xs font-medium text-gray-400 uppercase tracking-wider">Bugs Found</div>
      </div>
      <div class="glass-card glass-card-hover p-6 rounded-2xl text-center">
        <div class="text-3xl sm:text-4xl font-extrabold text-brand-accent font-mono mb-1">1</div>
        <div class="text-xs font-medium text-gray-400 uppercase tracking-wider">Dedicated Project</div>
      </div>
      <div class="glass-card glass-card-hover p-6 rounded-2xl text-center">
        <div class="text-3xl sm:text-4xl font-extrabold text-emerald-400 font-mono mb-1">OPEN</div>
        <div class="text-xs font-medium text-gray-400 uppercase tracking-wider">For Bug Finding</div>
      </div>
    </section>

    <section id="project" class="mb-16">
      <div class="flex items-center justify-between mb-8">
        <div>
          <h2 class="text-2xl font-bold text-white flex items-center gap-2">
            <span>Featured Project</span>
            <span class="text-brand-accent">✦</span>
          </h2>
          <p class="text-sm text-gray-400">Sole experience I currently test and hunt bugs for</p>
        </div>
      </div>

      <!-- Project Card -->
      <div class="glass-card rounded-3xl p-6 sm:p-8 border border-brand-border relative overflow-hidden group">
        <div class="absolute -right-20 -top-20 w-60 h-60 bg-brand-accent/10 rounded-full blur-3xl pointer-events-none"></div>

        <div class="flex flex-col md:flex-row items-start md:items-center justify-between gap-6 mb-8">
          <div class="flex items-center gap-4">
            <div class="w-16 h-16 rounded-2xl bg-amber-950/40 border border-brand-accent/30 flex items-center justify-center text-3xl shadow-inner">
              🧀
            </div>
            <div>
              <div class="flex items-center gap-2 mb-1">
                <h3 class="text-2xl font-bold text-white">Stream A Cheese Pull!</h3>
                <span class="px-2.5 py-0.5 rounded-md bg-emerald-500/10 text-emerald-400 border border-emerald-500/20 text-xs font-semibold">Bug Finder</span>
              </div>
              <p class="text-sm text-gray-400">Roblox Game Project</p>
            </div>
          </div>

          <div class="flex flex-wrap gap-2">
            <a href="https://www.roblox.com/games/124293095895786/Stream-A-Cheese-Pull" target="_blank" rel="noopener noreferrer" class="px-5 py-2.5 rounded-xl bg-brand-accent text-black font-bold text-xs hover:bg-yellow-400 transition-all flex items-center gap-1.5">
              <span>Play on Roblox</span>
              <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"></path></svg>
            </a>
          </div>
        </div>

        <p class="text-gray-300 text-sm sm:text-base leading-relaxed mb-8 bg-brand-bg/50 p-4 sm:p-5 rounded-2xl border border-brand-border/60">
          Working directly on <strong>Stream A Cheese Pull!</strong> to detect and report replication errors, UI glitches, physics breakages, and duplication exploits during high-traffic updates reaching up to <strong>30,000 Concurrent Players</strong>.
        </p>

        <!-- Project Metrics Grid -->
        <div class="grid grid-cols-2 sm:grid-cols-4 gap-4">
          <div class="bg-brand-bg/80 p-4 rounded-xl border border-brand-border/80">
            <span class="text-xs text-gray-500 uppercase tracking-wider block mb-1">Game Visits</span>
            <span class="text-lg font-bold text-white font-mono">27.8M+</span>
          </div>
          <div class="bg-brand-bg/80 p-4 rounded-xl border border-brand-border/80">
            <span class="text-xs text-gray-500 uppercase tracking-wider block mb-1">Peak CCU</span>
            <span class="text-lg font-bold text-brand-accent font-mono">30,000+</span>
          </div>
          <div class="bg-brand-bg/80 p-4 rounded-xl border border-brand-border/80">
            <span class="text-xs text-gray-500 uppercase tracking-wider block mb-1">Bugs Found</span>
            <span class="text-lg font-bold text-brand-accent font-mono">50+</span>
          </div>
          <div class="bg-brand-bg/80 p-4 rounded-xl border border-brand-border/80">
            <span class="text-xs text-gray-500 uppercase tracking-wider block mb-1">Role</span>
            <span class="text-lg font-bold text-emerald-400 font-mono">Bug Finder</span>
          </div>
        </div>
      </div>
    </section>

    <section class="mb-16">
      <h2 class="text-2xl font-bold text-white mb-2">What I Do</h2>
      <p class="text-sm text-gray-400 mb-8">Specialized strictly in bug finding and exploit discovery</p>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
        
        <div class="glass-card glass-card-hover p-6 rounded-2xl">
          <div class="w-12 h-12 rounded-xl bg-brand-accentGlow border border-brand-accent/20 flex items-center justify-center text-xl mb-4">
            🔍
          </div>
          <h3 class="text-lg font-bold text-white mb-2">Exploit & Dupe Spotting</h3>
          <p class="text-gray-400 text-sm leading-relaxed">
            Finding hidden duplication glitches, economy exploits, and remote event vulnerabilities before malicious players can abuse them.
          </p>
        </div>

        <div class="glass-card glass-card-hover p-6 rounded-2xl">
          <div class="w-12 h-12 rounded-xl bg-brand-accentGlow border border-brand-accent/20 flex items-center justify-center text-xl mb-4">
            🐛
          </div>
          <h3 class="text-lg font-bold text-white mb-2">Bug Replication & Logging</h3>
          <p class="text-gray-400 text-sm leading-relaxed">
            Isolating complex UI glitches and physics bugs with clear, step-by-step reproduction steps for developers to patch fast.
          </p>
        </div>

        <div class="glass-card glass-card-hover p-6 rounded-2xl">
          <div class="w-12 h-12 rounded-xl bg-brand-accentGlow border border-brand-accent/20 flex items-center justify-center text-xl mb-4">
            ⚡
          </div>
          <h3 class="text-lg font-bold text-white mb-2">Load Stress Bug Hunting</h3>
          <p class="text-gray-400 text-sm leading-relaxed">
            Hunting down server-side bugs and lag-inducing glitches while games are operating at peak load (30,000+ CCU).
          </p>
        </div>

      </div>
    </section>

    <section class="mb-16">
      <div class="glass-card rounded-3xl p-6 sm:p-8 border border-brand-border flex flex-col md:flex-row items-center gap-8">
        
        <div class="relative flex-shrink-0">
          <div class="w-28 h-28 rounded-full pink-aura border-2 p-1 flex items-center justify-center bg-[#1a1116] overflow-hidden">
            <img 
              src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/items/poke-ball.png" 
              alt="Middleman_12345 Avatar"
              class="w-full h-full object-cover object-top scale-110"
              onerror="this.onerror=null; this.src='https://images.wikidex.net/subidas/wikidex/4/4b/latest/20210430214828/Aldeano_JE2.png';"
            />
          </div>
        </div>

        <div>
          <h2 class="text-2xl font-bold text-white mb-3">About Middleman_12345</h2>
          <p class="text-gray-300 text-sm leading-relaxed mb-4">
            I am a dedicated Roblox Bug Finder known as <strong>Middleman_12345</strong> (Roblox: <code>AdrianPro9222</code>). I focus exclusively on finding critical bugs and exploits across games with massive player bases.
          </p>
          <p class="text-gray-400 text-sm leading-relaxed">
            Having found 50+ bugs on <i>Stream A Cheese Pull!</i> during 30,000 CCU updates, I help ensure games run smoothly and remain free of game-breaking glitches.
          </p>
        </div>

      </div>
    </section>

    <section id="contact" class="mb-12">
      <div class="glass-card rounded-3xl p-8 sm:p-10 border border-brand-border text-center relative overflow-hidden">
        
        <div class="max-w-xl mx-auto">
          <span class="text-brand-accent text-3xl mb-3 inline-block">💬</span>
          <h2 class="text-3xl font-extrabold text-white mb-3">Contact For Bug Finding</h2>
          <p class="text-gray-400 text-sm mb-8">
            Need a reliable Bug Finder for your Roblox game? Reach out via Discord or Roblox:
          </p>

          <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 text-left mb-8">
            
            <!-- Discord Copy Card -->
            <div class="bg-brand-bg/90 border border-brand-border p-4 rounded-2xl flex items-center justify-between group hover:border-indigo-500/50 transition-all">
              <div class="flex items-center gap-3">
                <div class="w-10 h-10 rounded-xl bg-indigo-500/10 border border-indigo-500/20 flex items-center justify-center text-indigo-400 font-bold text-sm">
                  DC
                </div>
                <div>
                  <div class="text-xs text-gray-400">Discord</div>
                  <div class="text-sm font-bold text-white font-mono">Middleman_12345</div>
                </div>
              </div>
              <button onclick="copyToClipboard('Middleman_12345', 'Discord Username')" class="px-3 py-1.5 rounded-lg bg-brand-card hover:bg-brand-cardHover border border-brand-border text-xs text-gray-300 hover:text-white transition-all">
                Copy
              </button>
            </div>

            <!-- Roblox Copy Card -->
            <div class="bg-brand-bg/90 border border-brand-border p-4 rounded-2xl flex items-center justify-between group hover:border-brand-accent/50 transition-all">
              <div class="flex items-center gap-3">
                <div class="w-10 h-10 rounded-xl bg-brand-accentGlow border border-brand-accent/20 flex items-center justify-center text-brand-accent font-bold text-sm">
                  RBX
                </div>
                <div>
                  <div class="text-xs text-gray-400">Roblox</div>
                  <div class="text-sm font-bold text-white font-mono">AdrianPro9222</div>
                </div>
              </div>
              <button onclick="copyToClipboard('AdrianPro9222', 'Roblox Username')" class="px-3 py-1.5 rounded-lg bg-brand-card hover:bg-brand-cardHover border border-brand-border text-xs text-gray-300 hover:text-white transition-all">
                Copy
              </button>
            </div>

          </div>

          <div class="inline-flex items-center gap-2 text-xs text-gray-500 bg-brand-bg/50 px-4 py-2 rounded-xl border border-brand-border">
            <span>⚡ Open for:</span>
            <strong class="text-gray-300">Roblox Bug Finding & Exploit Testing</strong>
          </div>

        </div>
      </div>
    </section>

    <footer class="text-center pt-8 border-t border-brand-border/50 text-xs text-gray-500">
      <p>© Middleman_12345 — Roblox Bug Finder</p>
      <p class="mt-1 text-gray-600">AdrianPro9222 Portfolio</p>
    </footer>

  </div>

  <script>
    // Particle background animation
    const canvas = document.getElementById('particles-canvas');
    const ctx = canvas.getContext('2d');

    let width = canvas.width = window.innerWidth;
    let height = canvas.height = window.innerHeight;

    window.addEventListener('resize', () => {
      width = canvas.width = window.innerWidth;
      height = canvas.height = window.innerHeight;
    });

    const particles = Array.from({ length: 45 }, () => ({
      x: Math.random() * width,
      y: Math.random() * height,
      size: Math.random() * 2 + 0.5,
      speedX: (Math.random() - 0.5) * 0.3,
      speedY: (Math.random() - 0.5) * 0.3,
      opacity: Math.random() * 0.4 + 0.1,
      color: Math.random() > 0.3 ? '#facc15' : '#ff7eb6'
    }));

    function animateParticles() {
      ctx.clearRect(0, 0, width, height);

      particles.forEach(p => {
        p.x += p.speedX;
        p.y += p.speedY;

        if (p.x < 0) p.x = width;
        if (p.x > width) p.x = 0;
        if (p.y < 0) p.y = height;
        if (p.y > height) p.y = 0;

        ctx.beginPath();
        ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
        ctx.fillStyle = p.color;
        ctx.globalAlpha = p.opacity;
        ctx.fill();
      });

      requestAnimationFrame(animateParticles);
    }

    animateParticles();

    // Copy to clipboard helper
    function copyToClipboard(text, label) {
      const textarea = document.createElement('textarea');
      textarea.value = text;
      document.body.appendChild(textarea);
      textarea.select();
      
      try {
        document.execCommand('copy');
        showToast(`Copied ${label} (${text})!`);
      } catch (err) {
        showToast(`Failed to copy.`);
      }
      
      document.body.removeChild(textarea);
    }

    // Toast Notification helper
    let toastTimeout;
    function showToast(message) {
      const toast = document.getElementById('toast');
      const toastText = document.getElementById('toast-text');
      
      toastText.textContent = message;
      toast.classList.add('show');

      clearTimeout(toastTimeout);
      toastTimeout = setTimeout(() => {
        toast.classList.remove('show');
      }, 3000);
    }
  </script>

</body>
</html>
