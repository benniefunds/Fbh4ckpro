<html lang="en">
 <head> 
  <meta charset="UTF-8"> 
  <meta name="viewport" content="width=device-width, initial-scale=1.0"> 
  <title>BennieTech FB Downloader | Bennie</title> 
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css"> 
  <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;700&amp;family=Orbitron:wght@500&amp;display=swap" rel="stylesheet"> 
  <style>
    :root {
      --primary: #00ffaa;
      --secondary: #00cc88;
      --dark: #0a192f;
      --darker: #020c1b;
      --light: #ccd6f6;
      --accent: #64ffda;
      --error: #ff4d4d;
      --warning: #ffcc00;
      --success: #00cc66;
      --terminal-bg: #011627;
      --terminal-text: #d6deeb;
      --terminal-border: #1d3b53;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: linear-gradient(135deg, var(--darker), var(--dark));
      color: var(--light);
      font-family: 'Fira Code', monospace;
      min-height: 100vh;
      line-height: 1.6;
      overflow-x: hidden;
      transition: all 0.5s ease;
    }

    body.light-mode {
      --dark: #f0f4f8;
      --darker: #d9e2ec;
      --light: #102a43;
      --terminal-bg: #ffffff;
      --terminal-text: #243B53;
      --terminal-border: #bcccdc;
      background: linear-gradient(135deg, #e6f0f8, #d1e0f0);
    }

    .container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 1.5rem;
    }

    /* ===== HEADER ===== */
    header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 1rem 0;
      margin-bottom: 1.5rem;
      border-bottom: 1px solid rgba(100, 255, 218, 0.2);
      animation: fadeInDown 0.8s ease;
    }

    .logo {
      display: flex;
      align-items: center;
      gap: 0.8rem;
      cursor: pointer;
    }

    .logo-icon {
      font-size: 2.2rem;
      color: var(--primary);
      animation: pulse 2s infinite;
    }

    .logo-text {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.8rem;
      font-weight: 700;
      background: linear-gradient(to right, var(--primary), var(--accent));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      letter-spacing: 1px;
    }

    .header-actions {
      display: flex;
      gap: 1rem;
      align-items: center;
    }

    .theme-toggle {
      background: none;
      border: none;
      color: var(--light);
      font-size: 1.3rem;
      cursor: pointer;
      transition: transform 0.3s;
    }

    .theme-toggle:hover {
      transform: rotate(30deg);
    }

    .telegram-btn {
      background: linear-gradient(to right, #0088cc, #00aced);
      color: white;
      padding: 0.6rem 1.2rem;
      border-radius: 50px;
      text-decoration: none;
      display: flex;
      align-items: center;
      gap: 0.5rem;
      font-weight: 600;
      transition: all 0.3s ease;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    }

    .telegram-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 12px rgba(0, 172, 237, 0.3);
    }

    /* ===== HERO SECTION ===== */
    .hero {
      text-align: center;
      padding: 2rem 0;
      animation: fadeIn 1s ease;
    }

    .hero h1 {
      font-size: 2.8rem;
      margin-bottom: 1.5rem;
      background: linear-gradient(to right, var(--primary), var(--accent));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      font-family: 'Orbitron', sans-serif;
      letter-spacing: 1px;
    }

    .typewriter {
      overflow: hidden;
      border-right: 3px solid var(--primary);
      white-space: nowrap;
      margin: 0 auto;
      letter-spacing: 2px;
      animation: typing 3.5s steps(40, end), blink-caret 0.75s step-end infinite;
      font-size: 1.2rem;
      max-width: 80%;
      color: var(--light);
      opacity: 0.9;
    }

    /* ===== DOWNLOAD BOX ===== */
    .download-box {
      background: rgba(10, 25, 47, 0.7);
      border: 1px solid rgba(100, 255, 218, 0.1);
      border-radius: 12px;
      padding: 2rem;
      backdrop-filter: blur(10px);
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
      max-width: 800px;
      margin: 2rem auto;
      transition: all 0.3s ease;
      animation: slideUp 0.8s ease;
    }

    .download-box:hover {
      border-color: rgba(100, 255, 218, 0.3);
      box-shadow: 0 15px 35px rgba(0, 0, 0, 0.4);
    }

    .input-group {
      position: relative;
      margin-bottom: 1.5rem;
    }

    .input-group i {
      position: absolute;
      left: 15px;
      top: 50%;
      transform: translateY(-50%);
      color: var(--primary);
      font-size: 1.2rem;
    }

    .url-input {
      width: 100%;
      padding: 15px 15px 15px 45px;
      background: rgba(2, 12, 27, 0.7);
      border: 1px solid rgba(100, 255, 218, 0.2);
      border-radius: 8px;
      color: var(--light);
      font-size: 1rem;
      transition: all 0.3s ease;
      font-family: 'Fira Code', monospace;
    }

    .url-input:focus {
      outline: none;
      border-color: var(--primary);
      box-shadow: 0 0 0 2px rgba(0, 255, 170, 0.2);
    }

    .download-btn {
      width: 100%;
      padding: 15px;
      background: linear-gradient(to right, var(--primary), var(--secondary));
      border: none;
      border-radius: 8px;
      color: var(--darker);
      font-size: 1.1rem;
      font-weight: 600;
      cursor: pointer;
      transition: all 0.3s ease;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.5rem;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    }

    .download-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 8px 15px rgba(0, 255, 170, 0.3);
    }

    .download-btn:active {
      transform: translateY(0);
    }

    /* ===== PROGRESS BAR ===== */
    .progress-container {
      width: 100%;
      height: 6px;
      background: rgba(2, 12, 27, 0.5);
      border-radius: 3px;
      margin-top: 1rem;
      overflow: hidden;
      display: none;
    }

    .progress-bar {
      height: 100%;
      background: linear-gradient(to right, var(--primary), var(--accent));
      width: 0%;
      transition: width 0.3s ease;
      border-radius: 3px;
    }

    /* ===== VIDEO CONTAINER ===== */
    .video-container {
      margin-top: 2rem;
      display: none;
      animation: fadeIn 0.8s ease;
    }

    .video-wrapper {
      background: rgba(2, 12, 27, 0.7);
      border-radius: 10px;
      padding: 1.5rem;
      margin-bottom: 1.5rem;
      border: 1px solid rgba(100, 255, 218, 0.1);
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
    }

    .video-wrapper h3 {
      color: var(--primary);
      margin-bottom: 1rem;
      display: flex;
      align-items: center;
      gap: 0.5rem;
      font-size: 1.3rem;
    }

    video {
      width: 100%;
      border-radius: 8px;
      border: 1px solid rgba(100, 255, 218, 0.2);
      background: #000;
    }

    .quality-btns {
      display: flex;
      gap: 1rem;
      margin-top: 1rem;
      flex-wrap: wrap;
    }

    .quality-btn {
      flex: 1;
      min-width: 120px;
      padding: 10px;
      background: rgba(2, 12, 27, 0.7);
      border: 1px solid var(--primary);
      border-radius: 5px;
      color: var(--primary);
      cursor: pointer;
      transition: all 0.3s ease;
      text-align: center;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.5rem;
      font-weight: 500;
    }

    .quality-btn:hover {
      background: rgba(0, 255, 170, 0.1);
      transform: translateY(-2px);
    }

    /* ===== LOADING SPINNER ===== */
    .loading {
      display: none;
      text-align: center;
      margin: 1.5rem 0;
      flex-direction: column;
      align-items: center;
      gap: 1rem;
    }

    .spinner {
      border: 4px solid rgba(0, 255, 170, 0.2);
      border-radius: 50%;
      border-top: 4px solid var(--primary);
      width: 50px;
      height: 50px;
      animation: spin 1s linear infinite;
    }

    .loading-text {
      color: var(--light);
      font-size: 1.1rem;
      opacity: 0.8;
    }

    /* ===== FEATURES SECTION ===== */
    .features {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 2rem;
      margin: 4rem 0;
    }

    .feature-card {
      background: rgba(10, 25, 47, 0.7);
      border: 1px solid rgba(100, 255, 218, 0.1);
      border-radius: 10px;
      padding: 2rem;
      transition: all 0.3s ease;
      animation: fadeIn 1s ease;
    }

    .feature-card:hover {
      transform: translateY(-5px);
      border-color: rgba(100, 255, 218, 0.3);
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
    }

    .feature-card i {
      font-size: 2.5rem;
      color: var(--primary);
      margin-bottom: 1.5rem;
    }

    .feature-card h3 {
      margin-bottom: 1rem;
      color: var(--light);
      font-size: 1.4rem;
    }

    .feature-card p {
      color: var(--light);
      opacity: 0.8;
      line-height: 1.6;
    }

    /* ===== HISTORY SECTION ===== */
    .history-section {
      margin: 3rem 0;
      animation: fadeIn 1s ease;
    }

    .history-title {
      display: flex;
      align-items: center;
      gap: 0.5rem;
      color: var(--light);
      margin-bottom: 1rem;
      font-size: 1.3rem;
    }

    .history-list {
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
    }

    .history-item {
      background: rgba(2, 12, 27, 0.5);
      padding: 0.8rem 1rem;
      border-radius: 6px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      transition: all 0.3s ease;
      cursor: pointer;
    }

    .history-item:hover {
      background: rgba(0, 255, 170, 0.1);
    }

    .history-item span {
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
      max-width: 80%;
    }

    .history-item i {
      color: var(--primary);
      cursor: pointer;
    }

    /* ===== FOOTER ===== */
    footer {
      text-align: center;
      padding: 2rem 0;
      margin-top: 3rem;
      border-top: 1px solid rgba(100, 255, 218, 0.2);
      color: var(--light);
      opacity: 0.7;
      animation: fadeIn 1s ease;
    }

    .footer-links {
      display: flex;
      justify-content: center;
      gap: 1.5rem;
      margin-bottom: 1rem;
    }

    .footer-link {
      color: var(--light);
      text-decoration: none;
      transition: color 0.3s;
      display: flex;
      align-items: center;
      gap: 0.3rem;
    }

    .footer-link:hover {
      color: var(--primary);
    }

    /* ===== TOOLTIP ===== */
    .tooltip {
      position: relative;
      display: inline-block;
      cursor: help;
    }

    .tooltip .tooltiptext {
      visibility: hidden;
      width: 200px;
      background-color: var(--dark);
      color: var(--light);
      text-align: center;
      border-radius: 6px;
      padding: 10px;
      position: absolute;
      z-index: 1;
      bottom: 125%;
      left: 50%;
      transform: translateX(-50%);
      opacity: 0;
      transition: opacity 0.3s;
      border: 1px solid var(--primary);
      font-size: 0.9rem;
    }

    .tooltip:hover .tooltiptext {
      visibility: visible;
      opacity: 1;
    }

    /* ===== TERMINAL STYLE NOTIFICATION ===== */
    .terminal-notification {
      position: fixed;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
      background: var(--terminal-bg);
      color: var(--terminal-text);
      border: 1px solid var(--terminal-border);
      border-radius: 6px;
      padding: 12px 20px;
      font-family: 'Fira Code', monospace;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
      z-index: 1000;
      display: flex;
      align-items: center;
      gap: 10px;
      max-width: 90%;
      animation: fadeInUp 0.5s ease;
    }

    .terminal-notification i {
      font-size: 1.2rem;
    }

    .terminal-notification.success i {
      color: var(--success);
    }

    .terminal-notification.error i {
      color: var(--error);
    }

    .terminal-notification.warning i {
      color: var(--warning);
    }

    /* ===== ANIMATIONS ===== */
    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    @keyframes typing {
      from { width: 0 }
      to { width: 100% }
    }

    @keyframes blink-caret {
      from, to { border-color: transparent }
      50% { border-color: var(--primary) }
    }

    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    @keyframes fadeInDown {
      from {
        opacity: 0;
        transform: translateY(-20px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @keyframes fadeInUp {
      from {
        opacity: 0;
        transform: translate(-50%, 20px);
      }
      to {
        opacity: 1;
        transform: translate(-50%, 0);
      }
    }

    @keyframes slideUp {
      from {
        opacity: 0;
        transform: translateY(30px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @keyframes pulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.1); }
      100% { transform: scale(1); }
    }

    /* ===== RESPONSIVE DESIGN ===== */
    @media (max-width: 768px) {
      .hero h1 {
        font-size: 2rem;
      }

      .typewriter {
        white-space: normal;
        border-right: none;
        animation: none;
        max-width: 100%;
      }

      .logo-text {
        font-size: 1.5rem;
      }

      .telegram-btn {
        padding: 0.5rem 1rem;
        font-size: 0.9rem;
      }

      .download-box {
        padding: 1.5rem;
      }

      .features {
        grid-template-columns: 1fr;
      }
    }

    @media (max-width: 480px) {
      .container {
        padding: 1rem;
      }

      header {
        flex-direction: column;
        gap: 1rem;
      }

      .header-actions {
        width: 100%;
        justify-content: space-between;
      }

      .hero h1 {
        font-size: 1.8rem;
      }

      .quality-btns {
        flex-direction: column;
      }
    }
  </style> 
 </head> 
 <body class=""> 
  <div class="container"> 
   <!-- HEADER --> 
   <header> 
    <div class="logo" onclick="window.location.reload()"> 
     <i class="fab fa-facebook logo-icon"></i> 
     <span class="logo-text">BennieTech FB Downloader</span> 
    </div> 
    <div class="header-actions"> 
     <button class="theme-toggle" id="themeToggle"><i class="fas fa-moon"></i></button> 
     <a href="https://whatsapp.com/channel/0029VbAaJpAHVvTQvBB8pw1h" class="telegram-btn" target="_blank"> <i class="fab fa-whatsapp"></i> <span>Join WhatsApp</span> </a> 
    </div> 
   </header> 
   <!-- HERO SECTION --> 
   <section class="hero"> 
    <h1>Facebook Video Downloader</h1> 
    <p class="typewriter">Powered by Bennie Tech - Download HD videos in one click!</p> 
    <!-- DOWNLOAD BOX --> 
    <div class="download-box"> 
     <div class="input-group"> 
      <i class="fas fa-link"></i> 
      <input type="text" id="urlInput" class="url-input" placeholder="Paste Facebook video URL here..." autocomplete="off"> 
     </div> 
     <button id="downloadBtn" class="download-btn" onclick="downloadVideo()"> <i class="fas fa-download"></i> Download Video </button> 
     <div class="progress-container" id="progressContainer"> 
      <div class="progress-bar" id="progressBar"></div> 
     </div> 
     <div id="loading" class="loading"> 
      <div class="spinner"></div> 
      <p class="loading-text">Processing your video...</p> 
     </div> 
    </div> 
    <!-- VIDEO CONTAINER --> 
    <div id="videoContainer" class="video-container"></div> 
    <!-- HISTORY SECTION --> 
    <div class="history-section" id="historySection"> 
     <h3 class="history-title"> <i class="fas fa-history"></i> Recent Downloads </h3> 
     <div class="history-list" id="historyList">
      <p style="opacity:0.7; font-size:0.9rem;">No recent downloads yet</p>
     </div> 
    </div> 
   </section> 
   <!-- FEATURES SECTION --> 
   <section class="features"> 
    <div class="feature-card"> 
     <i class="fas fa-bolt"></i> 
     <h3>Lightning Fast</h3> 
     <p>Our High Tech-powered backend processes videos at incredible speed with minimal latency.</p> 
    </div> 
    <div class="feature-card"> 
     <i class="fas fa-shield-alt"></i> 
     <h3>No Watermarks</h3> 
     <p>Download original quality videos without any annoying watermarks or ads.</p> 
    </div> 
   </section> 
   <!-- FOOTER --> 
   <footer> 
    <div class="footer-links"> 
     <a href="https://whatsapp.com/channel/0029VbAaJpAHVvTQvBB8pw1h" class="footer-link" target="_blank"> <i class="fab fa-whatsapp"></i> Whatsapp </a> 
     <a href="#" class="footer-link" id="aboutBtn"> <i class="fas fa-info-circle"></i> About </a> 
    </div> 
    <p>© 2025 Bennie Tech | <span class="tooltip">Powered by Bennie Tech<span class="tooltiptext">Join our WhatsApp for more awesome tools!</span></span></p> 
   </footer> 
  </div> 
  <script>
    // ===== GLOBAL VARIABLES =====
    const MAX_HISTORY_ITEMS = 5;
    let history = JSON.parse(localStorage.getItem('downloadHistory')) || [];

    // ===== DOM CONTENT LOADED =====
    document.addEventListener('DOMContentLoaded', function() {
      // Initialize theme
      initTheme();
      
      // Load history
      renderHistory();
      
      // Check for saved URL in localStorage
      const savedUrl = localStorage.getItem('lastFbUrl');
      if (savedUrl) {
        document.getElementById('urlInput').value = savedUrl;
      }
      
      // Add event listener for Enter key
      document.getElementById('urlInput').addEventListener('keypress', function(e) {
        if (e.key === 'Enter') {
          downloadVideo();
        }
      });
      
      // Auto-detect paste event
      document.getElementById('urlInput').addEventListener('paste', function(e) {
        setTimeout(() => {
          if (this.value.includes('facebook.com') || this.value.includes('fb.watch')) {
            downloadVideo();
          }
        }, 100);
      });
      
      // CLI Info Button
      document.getElementById('cliInfoBtn').addEventListener('click', function(e) {
        e.preventDefault();
        showTerminalNotification('info', 'Check our Telegram for Termux CLI version: /termux_command_store');
      });
      
      // About Button
      document.getElementById('aboutBtn').addEventListener('click', function(e) {
        e.preventDefault();
        showTerminalNotification('info', 'Termux FB Downloader v2.0 - Powered by Termux Command Store');
      });
    });

    // ===== THEME TOGGLE =====
    function initTheme() {
      const themeToggle = document.getElementById('themeToggle');
      const currentTheme = localStorage.getItem('theme') || 'dark';
      
      if (currentTheme === 'light') {
        document.body.classList.add('light-mode');
        themeToggle.innerHTML = '<i class="fas fa-sun"></i>';
      } else {
        themeToggle.innerHTML = '<i class="fas fa-moon"></i>';
      }
      
      themeToggle.addEventListener('click', function() {
        document.body.classList.toggle('light-mode');
        const isLight = document.body.classList.contains('light-mode');
        
        if (isLight) {
          localStorage.setItem('theme', 'light');
          themeToggle.innerHTML = '<i class="fas fa-sun"></i>';
        } else {
          localStorage.setItem('theme', 'dark');
          themeToggle.innerHTML = '<i class="fas fa-moon"></i>';
        }
      });
    }

    // ===== DOWNLOAD VIDEO FUNCTION =====
    async function downloadVideo() {
      const url = document.getElementById('urlInput').value.trim();
      if (!url) {
        showTerminalNotification('error', 'Please enter a Facebook video URL.');
        return;
      }
      
      // Validate URL
      if (!url.includes('facebook.com') && !url.includes('fb.watch')) {
        showTerminalNotification('error', 'Invalid URL - Must be from Facebook (facebook.com or fb.watch)');
        return;
      }
      
      // Save URL to localStorage
      localStorage.setItem('lastFbUrl', url);
      addToHistory(url);
      
      const videoContainer = document.getElementById('videoContainer');
      const loading = document.getElementById('loading');
      const progressContainer = document.getElementById('progressContainer');
      const progressBar = document.getElementById('progressBar');
      const downloadBtn = document.getElementById('downloadBtn');
      
      // Show loading state
      videoContainer.style.display = 'none';
      loading.style.display = 'flex';
      progressContainer.style.display = 'block';
      downloadBtn.disabled = true;
      downloadBtn.innerHTML = '<i class="fas fa-spinner fa-spin"></i> Processing...';
      
      // Simulate progress (real API would update this differently)
      let progress = 0;
      const progressInterval = setInterval(() => {
        progress += Math.random() * 10;
        if (progress > 90) clearInterval(progressInterval);
        progressBar.style.width = `${Math.min(progress, 90)}%`;
      }, 300);
      
      try {
        const apiURL = `https://tcs-demonic2.vercel.app/api/fbdownloader?url=${encodeURIComponent(url)}`;
        const response = await fetch(apiURL);
        
        // Complete progress bar
        progressBar.style.width = '100%';
        await new Promise(resolve => setTimeout(resolve, 500));
        
        const data = await response.json();
        
        if (data.success && data.data.success) {
          const { hdlink, sdlink } = data.data;
          let html = '';
          
          if (hdlink) {
            html += `
              <div class="video-wrapper">
                <h3><i class="fas fa-film"></i> HD Quality (720p/1080p)</h3>
                <video controls>
                  <source src="${hdlink}" type="video/mp4">
                  Your browser does not support the video tag.
                </video>
                <div class="quality-btns">
                  <a href="${hdlink}" class="quality-btn" download="facebook_hd_video.mp4">
                    <i class="fas fa-download"></i> Download HD
                  </a>
                  <button class="quality-btn" onclick="copyToClipboard('${hdlink}')">
                    <i class="fas fa-copy"></i> Copy Link
                  </button>
                </div>
              </div>
            `;
          }
          
          if (sdlink) {
            html += `
              <div class="video-wrapper">
                <h3><i class="fas fa-film"></i> SD Quality (480p)</h3>
                <video controls>
                  <source src="${sdlink}" type="video/mp4">
                  Your browser does not support the video tag.
                </video>
                <div class="quality-btns">
                  <a href="${sdlink}" class="quality-btn" download="facebook_sd_video.mp4">
                    <i class="fas fa-download"></i> Download SD
                  </a>
                  <button class="quality-btn" onclick="copyToClipboard('${sdlink}')">
                    <i class="fas fa-copy"></i> Copy Link
                  </button>
                </div>
              </div>
            `;
          }
          
          videoContainer.innerHTML = html;
          videoContainer.style.display = 'block';
          showTerminalNotification('success', 'Video loaded successfully!');
        } else {
          throw new Error(data.message || "Failed to fetch video links.");
        }
      } catch (error) {
        console.error(error);
        showTerminalNotification('error', error.message || "An error occurred. Please try again.");
      } finally {
        clearInterval(progressInterval);
        loading.style.display = 'none';
        progressContainer.style.display = 'none';
        progressBar.style.width = '0%';
        downloadBtn.disabled = false;
        downloadBtn.innerHTML = '<i class="fas fa-download"></i> Download Video';
      }
    }

    // ===== HISTORY FUNCTIONS =====
    function addToHistory(url) {
      // Remove if already exists
      history = history.filter(item => item.url !== url);
      
      // Add to beginning of array
      history.unshift({
        url: url,
        timestamp: new Date().toISOString()
      });
      
      // Keep only last 5 items
      if (history.length > MAX_HISTORY_ITEMS) {
        history = history.slice(0, MAX_HISTORY_ITEMS);
      }
      
      // Save to localStorage
      localStorage.setItem('downloadHistory', JSON.stringify(history));
      
      // Update UI
      renderHistory();
    }

    function renderHistory() {
      const historyList = document.getElementById('historyList');
      
      if (history.length === 0) {
        historyList.innerHTML = '<p style="opacity:0.7; font-size:0.9rem;">No recent downloads yet</p>';
        return;
      }
      
      historyList.innerHTML = history.map(item => `
        <div class="history-item" onclick="useHistoryItem('${item.url}')">
          <span>${item.url}</span>
          <i class="fas fa-times" onclick="removeHistoryItem('${item.url}', event)"></i>
        </div>
      `).join('');
    }

    function useHistoryItem(url) {
      document.getElementById('urlInput').value = url;
      downloadVideo();
    }

    function removeHistoryItem(url, event) {
      event.stopPropagation();
      history = history.filter(item => item.url !== url);
      localStorage.setItem('downloadHistory', JSON.stringify(history));
      renderHistory();
    }

    // ===== UTILITY FUNCTIONS =====
    function copyToClipboard(text) {
      navigator.clipboard.writeText(text)
        .then(() => {
          showTerminalNotification('success', 'Link copied to clipboard!');
        })
        .catch(err => {
          showTerminalNotification('error', 'Failed to copy link');
          console.error('Failed to copy: ', err);
        });
    }

    function showTerminalNotification(type, message) {
      const notification = document.createElement('div');
      notification.className = `terminal-notification ${type}`;
      
      let icon;
      switch(type) {
        case 'success':
          icon = '<i class="fas fa-check-circle"></i>';
          break;
        case 'error':
          icon = '<i class="fas fa-exclamation-circle"></i>';
          break;
        case 'warning':
          icon = '<i class="fas fa-exclamation-triangle"></i>';
          break;
        default:
          icon = '<i class="fas fa-info-circle"></i>';
      }
      
      notification.innerHTML = `${icon} <span>${message}</span>`;
      document.body.appendChild(notification);
      
      setTimeout(() => {
        notification.style.animation = 'fadeInUp 0.5s ease reverse';
        setTimeout(() => {
          document.body.removeChild(notification);
        }, 500);
      }, 3000);
    }
  </script> 
 </body>
</html>