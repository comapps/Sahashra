<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Multi TV Channel - Neon Design</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link
    rel="stylesheet"
    href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap"
  />
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css"
  />
  <style>
    body {
      font-family: "Roboto", sans-serif;
      background: #0f0f18;
      color: #0ff;
      overflow-x: hidden;
    }
    h1 {
      text-shadow:
        0 0 5px #0ff,
        0 0 10px #0ff,
        0 0 20px #0ff,
        0 0 40px #0ff;
    }
    .tv-frame-container {
      position: relative;
      width: 100%;
      max-width: 900px;
      margin: auto;
      padding-top: 56.25%; /* 16:9 Aspect Ratio */
      border-radius: 25px;
      box-shadow:
        0 0 10px #0ff,
        0 0 20px #0ff,
        0 0 40px #0ff,
        inset 0 0 30px #0ff;
      background: #000;
      overflow: hidden;
    }
    .tv-frame {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      border-radius: 25px;
      box-shadow:
        0 0 15px #0ff,
        inset 0 0 20px #0ff;
      outline: 2px solid #0ff;
      outline-offset: -6px;
      background: black;
    }
    /* Neon glow for channel logos */
    .channel-logo {
      filter: drop-shadow(0 0 5px #0ff);
      transition: filter 0.3s ease, transform 0.3s ease;
      border: 2px solid transparent;
    }
    .channel-logo:hover,
    .channel-logo:focus {
      filter:
        drop-shadow(0 0 10px #0ff)
        drop-shadow(0 0 20px #0ff)
        drop-shadow(0 0 30px #0ff);
      transform: scale(1.15);
      border-color: #0ff;
      outline: none;
      cursor: pointer;
      z-index: 10;
      position: relative;
    }
    /* Neon button */
    .btn-neon {
      background: transparent;
      border: 2px solid #0ff;
      color: #0ff;
      padding: 0.5rem 1.25rem;
      border-radius: 9999px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.1em;
      box-shadow:
        0 0 5px #0ff,
        0 0 10px #0ff,
        0 0 20px #0ff;
      transition: background-color 0.3s ease, color 0.3s ease;
      user-select: none;
    }
    .btn-neon:hover,
    .btn-neon:focus {
      background-color: #0ff;
      color: #000;
      outline: none;
      box-shadow:
        0 0 10px #0ff,
        0 0 20px #0ff,
        0 0 40px #0ff;
      cursor: pointer;
    }
    /* Dropdown container */
    .dropdown {
      position: relative;
      display: inline-block;
      max-width: 100%;
      margin: 1.5rem auto 0 auto;
      width: 90vw;
      max-width: 900px;
      text-align: left;
      user-select: none;
    }
    /* Dropdown button */
    .dropdown-button {
      width: 100%;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0.75rem 1rem;
      font-size: 1.125rem;
      border-radius: 12px;
      border: 2px solid #0ff;
      background: transparent;
      color: #0ff;
      box-shadow:
        0 0 5px #0ff,
        0 0 10px #0ff;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    .dropdown-button:hover,
    .dropdown-button:focus {
      background-color: #0ff;
      color: #000;
      outline: none;
      box-shadow:
        0 0 10px #0ff,
        0 0 20px #0ff;
    }
    /* Dropdown content */
    .dropdown-content {
      max-height: 0;
      overflow: hidden;
      transition: max-height 0.5s ease, opacity 0.5s ease;
      opacity: 0;
      background: #11121a;
      border: 2px solid #0ff;
      border-top: none;
      border-radius: 0 0 12px 12px;
      box-shadow:
        0 0 10px #0ff,
        0 0 20px #0ff;
      margin-top: -2px;
      z-index: 20;
      position: relative;
    }
    .dropdown-content.open {
      max-height: 600px;
      opacity: 1;
      overflow-y: auto;
    }
    /* Scrollbar for dropdown */
    .dropdown-content::-webkit-scrollbar {
      width: 8px;
    }
    .dropdown-content::-webkit-scrollbar-track {
      background: #0f0f18;
    }
    .dropdown-content::-webkit-scrollbar-thumb {
      background: #0ff;
      border-radius: 4px;
    }
    /* Channel list inside dropdown */
    .dropdown-channel-list {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(70px, 1fr));
      gap: 1rem;
      padding: 1rem;
    }
    /* TV player controls container */
    .tv-controls {
      max-width: 900px;
      margin: 1.5rem auto 3rem auto;
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1rem;
      user-select: none;
    }
    .tv-controls button,
    .tv-controls input[type="range"] {
      background: transparent;
      border: 2px solid #0ff;
      color: #0ff;
      padding: 0.5rem 1rem;
      border-radius: 9999px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.1em;
      box-shadow:
        0 0 5px #0ff,
        0 0 10px #0ff;
      transition: background-color 0.3s ease, color 0.3s ease;
      cursor: pointer;
    }
    .tv-controls button:hover,
    .tv-controls button:focus,
    .tv-controls input[type="range"]:hover,
    .tv-controls input[type="range"]:focus {
      background-color: #0ff;
      color: #000;
      outline: none;
      box-shadow:
        0 0 10px #0ff,
        0 0 20px #0ff;
    }
    .tv-controls input[type="range"] {
      -webkit-appearance: none;
      width: 150px;
      cursor: pointer;
      background: transparent;
    }
    .tv-controls input[type="range"]::-webkit-slider-runnable-track {
      height: 6px;
      background: #0ff;
      border-radius: 3px;
    }
    .tv-controls input[type="range"]::-webkit-slider-thumb {
      -webkit-appearance: none;
      width: 18px;
      height: 18px;
      background: #0ff;
      border-radius: 50%;
      margin-top: -6px;
      box-shadow:
        0 0 8px #0ff;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    .tv-controls input[type="range"]:focus::-webkit-slider-thumb {
      background-color: #00ffff;
      box-shadow:
        0 0 12px #00ffff;
      outline: none;
    }
    /* Responsive adjustments */
    @media (max-width: 640px) {
      .tv-controls {
        flex-direction: column;
        gap: 0.75rem;
      }
      .tv-controls input[type="range"] {
        width: 100%;
        max-width: 300px;
      }
    }
  </style>
</head>
<body>
  <header class="text-center pt-6">
    <h1>SAHASHRA TV PORTAL</h1>
  </header>

  <main class="flex flex-col items-center px-4">
    <div class="tv-frame-container mt-6" aria-label="TV player container">
      <iframe
        id="tvFrame"
        class="tv-frame"
        src="https://www.livereacting.com/tools/hls-player-embed?url=https://cdn3.wowza.com/1/QmVNUVhTNTZSS3Uz/YWQ0aHpi/hls/live/playlist.m3u8"
        allowfullscreen
        title="Live TV Player"
        allow="autoplay; fullscreen"
      ></iframe>
    </div>

    <div class="tv-controls" role="region" aria-label="TV player controls">
      <button id="playPauseBtn" aria-label="Play/Pause TV player" class="btn-neon">
        <i class="fas fa-play"></i> Play
      </button>
      <button id="muteBtn" aria-label="Mute/Unmute TV player" class="btn-neon">
        <i class="fas fa-volume-up"></i> Mute
      </button>
      <label for="volumeRange" class="sr-only">Volume control</label>
      <input
        type="range"
        id="volumeRange"
        min="0"
        max="1"
        step="0.05"
        value="1"
        aria-valuemin="0"
        aria-valuemax="1"
        aria-valuenow="1"
        aria-label="Volume slider"
      />
      <button id="fullscreenBtn" aria-label="Toggle fullscreen" class="btn-neon">
        <i class="fas fa-expand"></i> Fullscreen
      </button>
    </div>

    <div class="dropdown" id="channelDropdown">
      <button
        class="dropdown-button"
        id="dropdownBtn"
        aria-haspopup="true"
        aria-expanded="false"
        aria-controls="dropdownMenu"
      >
        Select Channel
        <i class="fas fa-chevron-down transition-transform duration-300" id="dropdownIcon"></i>
      </button>
      <div
        class="dropdown-content"
        id="dropdownMenu"
        role="menu"
        aria-labelledby="dropdownBtn"
        tabindex="-1"
      >
        <div class="dropdown-channel-list" role="list">
          <img
            role="listitem"
            tabindex="0"
            alt="Logo of TV 1 channel, a blue and white stylized number 1 with a globe"
            class="channel-logo rounded-full mx-auto w-20 h-20 object-contain"
            data-url="https://ndevslk.github.io/iptv/hlsplayer.html?url=gc2R2P4U3Mt5CMwAjN5UjYfR3cpx2auVHaj9Cbp12cuETMxYHd6wWatN3LkNXMz5WYyR3L0Vmbu4GZjBHc1lnLlZXasJ2bt9yL6MHc0RHa"
            src="https://www.seekpng.com/png/full/72-723646_2016-tv-1-logo-png.png"
            width="70"
            height="70"
          />
          <img
            role="listitem"
            tabindex="0"
            alt="Logo of TV DERANA channel, red and white text with a red circle"
            class="channel-logo rounded-full mx-auto w-20 h-20 object-contain"
            data-url="https://ndevslk.github.io/iptv/hlsplayer.html?url=Indk9DO1NTbuADMwYTO1I2X0NXastmb1h2YvwWatNnL0Ajd0VGZ6wWatN3LyQGaz5WYyR3L0Vmbu4GZjBHc1lnLlZXasJ2bt9yL6MHc0RHa"
            src="https://upload.wikimedia.org/wikipedia/commons/9/94/Logo_TV_Derana.jpg"
            width="70"
            height="70"
          />
          <img
            role="listitem"
            tabindex="0"
            alt="Logo of CHARANA TV channel, black and red text with a red circle"
            class="channel-logo rounded-full mx-auto w-20 h-20 object-contain"
            data-url="https://ndevslk.github.io/iptv/hlsplayer.html?url=Indk9DO1NTbuADMwYTO1I2X0NXastmb1h2YvwWatNnL1Ajd0h2Y6wWatN3LyQGaz5WYyR3L0Vmbu4GZjBHc1lnLlZXasJ2bt9yL6MHc0RHa"
            src="https://i0.wp.com/www.charanatv.lk/wp-content/uploads/2021/08/CHARANA-LOGO.png?fit=271%2C300&ssl=1"
            width="70"
            height="70"
          />
          <img
            role="listitem"
            tabindex="0"
            alt="Logo of SWARNAWAHINI channel, yellow and red text with a sun icon"
            class="channel-logo rounded-full mx-auto w-20 h-20 object-contain"
            data-url="https://ndevslk.github.io/iptv/hlsplayer.html?url=Indk9DO1NTbuADMwYTO1I2X0NXastmb1h2YvwWatNnL2ATauF2dzpDbp12cvQ2cz5WYyR3L0Vmbu4GZjBHc1lnLlZXasJ2bt9yL6MHc0RHa"
            src="https://sri-lanka.mom-gmr.org/uploads/tx_lfrogmom/media/13515-1360_import.png"
            width="70"
            height="70"
          />
          <img
            role="listitem"
            tabindex="0"
            alt="Logo of VASANTHAM TV channel, red and white text with a stylized V"
            class="channel-logo rounded-full mx-auto w-20 h-20 object-contain"
            data-url="https://ndevslk.github.io/iptv/hlsplayer.html?url=Indk9DO1NTbuADMwYTO1I2X0NXastmb1h2YvwWatNnL3Ajd0Fmd6wWatN3LkNXMz5WYyR3L0Vmbu4GZjBHc1lnLlZXasJ2bt9yL6MHc0RHa"
            src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSpcGcR56pXITyrFOxdUNH9z-uZG0Tp-WbhBg&s"
            width="70"
            height="70"
          />
          <img
            role="listitem"
            tabindex="0"
            alt="Logo of SIYATHA TV channel, red and white text with a stylized S"
            class="channel-logo rounded-full mx-auto w-20 h-20 object-contain"
            data-url="https://ndevslk.github.io/iptv/hlsplayer.html?url=yZHZ/gTdz0mLwADM2kTNi9FdzlGbr5WdoN2LslWbz5COwYHd5l2c6wWatN3LyQGaz5WYyR3L0Vmbu4GZjBHc1lnLlZXasJ2bt9yL6MHc0RHa"
            src="https://sri-lanka.mom-gmr.org/uploads/tx_lfrogmom/media/13521-1360_import.png"
            width="70"
            height="70"
          />
          <img
            role="listitem"
            tabindex="0"
            alt="Logo of SIRASA TV channel, red and white text with a stylized S"
            class="channel-logo rounded-full mx-auto w-20 h-20 object-contain"
            data-url="https://ndevslk.github.io/iptv/hlsplayer.html?url=Indk9DO1NTbuADMwYTO1I2X0NXastmb1h2YvwWatNnL5Ajd0JXazpDbp12cvQ2cz5WYyR3L0Vmbu4GZjBHc1lnLlZXasJ2bt9yL6MHc0RHa"
            src="https://sri-lanka.mom-gmr.org/uploads/tx_lfrogmom/media/13514-1360_import.png"
            width="70"
            height="70"
          />
          <img
            role="listitem"
            tabindex="0"
            alt="Logo of SAKTHI TV channel, red and white text with Tamil script"
            class="channel-logo rounded-full mx-auto w-20 h-20 object-contain"
            data-url="https://ndevslk.github.io/iptv/hlsplayer.html?url=Indk9DO1NTbuADMwYTO1I2X0NXastmb1h2YvwWatNnLwEjd0tWYzpDbp12cvQ2cz5WYyR3L0Vmbu4GZjBHc1lnLlZXasJ2bt9yL6MHc0RHa"
            src="https://shakthitv.lk/wp-content/uploads/2021/08/topbanner-250x200.png"
            width="70"
            height="70"
          />
          <img
            role="listitem"
            tabindex="0"
            alt="Logo of TNL channel, red and white text with a stylized T"
            class="channel-logo rounded-full mx-auto w-20 h-20 object-contain"
            data-url="https://www.itn.lk/stream/itntv/"
            src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQoumgpMxEVwKZgQC2dxO54zKdRlv7zQQc1en7hb-61KSifStvS7eCXpjkNFrJzu-WP83Y&usqp=CAU"
            width="70"
            height="70"
          />
          <img
            role="listitem"
            tabindex="0"
            alt="Logo of NETHRA TV channel, red and white text with a stylized N"
            class="channel-logo rounded-full mx-auto w-20 h-20 object-contain"
            data-url="https://ndevslk.github.io/iptv/hlsplayer.html?url=yZHZ/gTdz0mLwADM2kTNi9FdzlGbr5WdoN2LslWbz5SNxYHd0Vmb6wWatN3LkNXMz5WYyR3L0Vmbu4GZjBHc1lnLlZXasJ2bt9yL6MHc0RHa"
            src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSE5FkQ0lWpk5yq0CJP8_GU-skYKlzam9W2RA&s"
            width="70"
            height="70"
          />
          <img
            role="listitem"
            tabindex="0"
            alt="Logo of HIRU TV channel, red and white text with a stylized H"
            class="channel-logo rounded-full mx-auto w-20 h-20 object-contain"
            data-url="https://ndevslk.github.io/iptv/hlsplayer.html?url=Indk9DO1NTbuADMwYTO1I2X0NXastmb1h2YvwWatNnL3Ejd0lGa6wWatN3LyQGaz5WYyR3L0Vmbu4GZjBHc1lnLlZXasJ2bt9yL6MHc0RHa"
            src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRI5HXSlL2_GkA5pTPQHe5NU9Irsp2wmgAvvg&s"
            width="70"
            height="70"
          />
          <img
            role="listitem"
            tabindex="0"
            alt="Logo of STAR TAMIL channel, red and white text with a star icon"
            class="channel-logo rounded-full mx-auto w-20 h-20 object-contain"
            data-url="https://ndevslk.github.io/iptv/hlsplayer.html?url=gc2R2P4U3Mt5CMwAjN5UjYfR3cpx2auVHaj9Cbp12cukTMs1GdyR3c6wWatN3LkNXMz5WYyR3L0Vmbu4GZjBHc1lnLlZXasJ2bt9yL6MHc0RHa"
            src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSKtOGKmITNfhqt2EbtC1nxUkWqCpE42L95qA&s"
            width="70"
            height="70"
          />
          <img
            role="listitem"
            tabindex="0"
            alt="Logo of RUPAWAHINI channel, red and white text with a stylized R"
            class="channel-logo rounded-full mx-auto w-20 h-20 object-contain"
            data-url="https://ndevslk.github.io/iptv/hlsplayer.html?url=gc2R2P4U3Mt5CMwAjN5UjYfR3cpx2auVHaj9Cbp12cuEDMp5WdypDbp12cvQ2cz5WYyR3L0Vmbu4GZjBHc1lnLlZXasJ2bt9yL6MHc0RHa"
            src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTWE5yS6CHKwEywoSBgv0f7tl0hOvjJ82oOlA&s"
            width="70"
            height="70"
          />
          <img
            role="listitem"
            tabindex="0"
            alt="Logo of ITN channel, red and white text with a stylized I"
            class="channel-logo rounded-full mx-auto w-20 h-20 object-contain"
            data-url="https://www.itn.lk/stream/itntv/"
            src="https://upload.wikimedia.org/wikipedia/commons/a/aa/ITN_Television_Logo_of_Sri_lanka.png"
            width="70"
            height="70"
          />
          <img
            role="listitem"
            tabindex="0"
            alt="Logo of MUSIC PLUS channel, red and white text with a musical note"
            class="channel-logo rounded-full mx-auto w-20 h-20 object-contain"
            data-url="https://ndevslk.github.io/iptv/hlsplayer.html?url=yZHZ/gTdz0mLwADM2kTNi9FdzlGbr5WdoN2LslWbz5CNxYHdwVXb6wWatN3LkNXMz5WYyR3L0Vmbu4GZjBHc1lnLlZXasJ2bt9yL6MHc0RHa"
            src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQHOG_QUaRlyNl5BXx-pr-RGphOqRuiFFTKBw&s"
            width="70"
            height="70"
          />
          <img
            role="listitem"
            tabindex="0"
            alt="Logo of verbumtv channel, blue and white text with a globe"
            class="channel-logo rounded-full mx-auto w-20 h-20 object-contain"
            data-url="https://verbumtv.livebox.co.in/verbumtvhls/live.m3u8"
            src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTTcl3ooFM--xqwPLpZljDfEtHsn1PVV5Eukw&s"
            width="70"
            height="70"
          />
        </div>
      </div>
    </div>
  </main>

  <footer class="text-center py-6 text-gray-400 text-sm select-none">
    © 2025 SAHASHRA TV PORTAL EDITED BY ANURADHA BANDARANYAKA
  </footer>

  <script>
    (() => {
      const dropdownBtn = document.getElementById("dropdownBtn");
      const dropdownContent = document.getElementById("dropdownMenu");
      const dropdownIcon = document.getElementById("dropdownIcon");
      const tvFrame = document.getElementById("tvFrame");
      const channelLogos = dropdownContent.querySelectorAll(".channel-logo");

      // TV player controls
      const playPauseBtn = document.getElementById("playPauseBtn");
      const muteBtn = document.getElementById("muteBtn");
      const volumeRange = document.getElementById("volumeRange");
      const fullscreenBtn = document.getElementById("fullscreenBtn");

      // State for play/pause (iframe video can't be controlled directly, so we reload src to simulate)
      let isPlaying = true;
      let currentSrc = tvFrame.src;
      let isMuted = false;

      // Toggle dropdown open/close
      function toggleDropdown() {
        const isOpen = dropdownContent.classList.contains("open");
        if (isOpen) {
          dropdownContent.classList.remove("open");
          dropdownBtn.setAttribute("aria-expanded", "false");
          dropdownIcon.style.transform = "rotate(0deg)";
        } else {
          dropdownContent.classList.add("open");
          dropdownBtn.setAttribute("aria-expanded", "true");
          dropdownIcon.style.transform = "rotate(180deg)";
          dropdownContent.focus();
        }
      }

      dropdownBtn.addEventListener("click", toggleDropdown);

      // Close dropdown if clicked outside
      document.addEventListener("click", (e) => {
        if (
          !dropdownBtn.contains(e.target) &&
          !dropdownContent.contains(e.target)
        ) {
          dropdownContent.classList.remove("open");
          dropdownBtn.setAttribute("aria-expanded", "false");
          dropdownIcon.style.transform = "rotate(0deg)";
        }
      });

      // Keyboard accessibility for dropdown button
      dropdownBtn.addEventListener("keydown", (e) => {
        if (e.key === "ArrowDown" || e.key === "Enter" || e.key === " ") {
          e.preventDefault();
          if (!dropdownContent.classList.contains("open")) {
            toggleDropdown();
          }
          // Focus first channel logo
          const firstLogo = dropdownContent.querySelector(".channel-logo");
          if (firstLogo) firstLogo.focus();
        }
      });

      // Keyboard navigation inside dropdown channel list
      dropdownContent.addEventListener("keydown", (e) => {
        const focusable = Array.from(
          dropdownContent.querySelectorAll(".channel-logo")
        );
        const index = focusable.indexOf(document.activeElement);
        if (e.key === "ArrowDown") {
          e.preventDefault();
          const nextIndex = (index + 1) % focusable.length;
          focusable[nextIndex].focus();
        } else if (e.key === "ArrowUp") {
          e.preventDefault();
          const prevIndex = (index - 1 + focusable.length) % focusable.length;
          focusable[prevIndex].focus();
        } else if (e.key === "Escape") {
          dropdownContent.classList.remove("open");
          dropdownBtn.setAttribute("aria-expanded", "false");
          dropdownIcon.style.transform = "rotate(0deg)";
          dropdownBtn.focus();
        } else if (e.key === "Enter" || e.key === " ") {
          e.preventDefault();
          if (document.activeElement.classList.contains("channel-logo")) {
            const url = document.activeElement.getAttribute("data-url");
            changeChannel(url);
            dropdownContent.classList.remove("open");
            dropdownBtn.setAttribute("aria-expanded", "false");
            dropdownIcon.style.transform = "rotate(0deg)";
            dropdownBtn.focus();
          }
        }
      });

      // Change channel function
      function changeChannel(url) {
        if (!url) return;
        currentSrc = url;
        tvFrame.src = url;
        isPlaying = true;
        playPauseBtn.innerHTML = '<i class="fas fa-pause"></i> Pause';
        // Reset mute and volume controls
        isMuted = false;
        muteBtn.innerHTML = '<i class="fas fa-volume-up"></i> Mute';
        volumeRange.value = 1;
      }

      // Click on channel logos changes channel
      channelLogos.forEach((logo) => {
        logo.addEventListener("click", () => {
          const url = logo.getAttribute("data-url");
          changeChannel(url);
        });
        logo.addEventListener("keydown", (e) => {
          if (e.key === "Enter" || e.key === " ") {
            e.preventDefault();
            const url = logo.getAttribute("data-url");
            changeChannel(url);
          }
        });
      });

      // Play/Pause button simulates by reloading iframe or blanking src
      playPauseBtn.addEventListener("click", () => {
        if (isPlaying) {
          // Pause: blank src to stop stream
          tvFrame.src = "about:blank";
          playPauseBtn.innerHTML = '<i class="fas fa-play"></i> Play';
          isPlaying = false;
        } else {
          // Play: reload current src
          tvFrame.src = currentSrc;
          playPauseBtn.innerHTML = '<i class="fas fa-pause"></i> Pause';
          isPlaying = true;
        }
      });

      // Mute button toggles volume slider and icon
      muteBtn.addEventListener("click", () => {
        if (isMuted) {
          volumeRange.value = 1;
          muteBtn.innerHTML = '<i class="fas fa-volume-up"></i> Mute';
          isMuted = false;
          // Reload iframe with volume param if possible (not really controllable)
          // No direct volume control on iframe, so just UI effect
        } else {
          volumeRange.value = 0;
          muteBtn.innerHTML = '<i class="fas fa-volume-mute"></i> Unmute';
          isMuted = true;
        }
      });

      // Volume slider changes mute state and icon
      volumeRange.addEventListener("input", () => {
        const vol = parseFloat(volumeRange.value);
        if (vol === 0) {
          muteBtn.innerHTML = '<i class="fas fa-volume-mute"></i> Unmute';
          isMuted = true;
        } else {
          muteBtn.innerHTML = '<i class="fas fa-volume-up"></i> Mute';
          isMuted = false;
        }
        // No direct volume control on iframe video, so this is UI only
      });

      // Fullscreen toggle for iframe container
      fullscreenBtn.addEventListener("click", () => {
        const container = document.querySelector(".tv-frame-container");
        if (!document.fullscreenElement) {
          if (container.requestFullscreen) {
            container.requestFullscreen();
          } else if (container.webkitRequestFullscreen) {
            container.webkitRequestFullscreen();
          } else if (container.msRequestFullscreen) {
            container.msRequestFullscreen();
          }
          fullscreenBtn.innerHTML = '<i class="fas fa-compress"></i> Exit Fullscreen';
        } else {
          if (document.exitFullscreen) {
            document.exitFullscreen();
          } else if (document.webkitExitFullscreen) {
            document.webkitExitFullscreen();
          } else if (document.msExitFullscreen) {
            document.msExitFullscreen();
          }
          fullscreenBtn.innerHTML = '<i class="fas fa-expand"></i> Fullscreen';
        }
      });

      // Listen for fullscreen change to update button text
      document.addEventListener("fullscreenchange", () => {
        if (!document.fullscreenElement) {
          fullscreenBtn.innerHTML = '<i class="fas fa-expand"></i> Fullscreen';
        } else {
          fullscreenBtn.innerHTML = '<i class="fas fa-compress"></i> Exit Fullscreen';
        }
      });
    })();
  </script>

  <!--Start of Tawk.to Script-->
  <script type="text/javascript">
    var Tawk_API = Tawk_API || {},
      Tawk_LoadStart = new Date();
    (function () {
      var s1 = document.createElement("script"),
        s0 = document.getElementsByTagName("script")[0];
      s1.async = true;
      s1.src = "https://embed.tawk.to/64c7514bcc26a871b02c4442/1ioaju2dp";
      s1.charset = "UTF-8";
      s1.setAttribute("crossorigin", "*");
      s0.parentNode.insertBefore(s1, s0);
    })();
  </script>
  <!--End of Tawk.to Script-->
</body>
</html>

