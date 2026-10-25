# YoutubeStylus
copia desde linea 3 a 120 y pegalo como un nuevo estilo de stylus para youtube

html {
  background: url("https://raw.githubusercontent.com/XDertZX/Pictures/refs/heads/main/kafkitadefrente.jpg")
    center / cover no-repeat fixed !important;
}

html::before {
  content: "" !important;
  position: fixed !important;
  inset: 0 !important;
  z-index: 0 !important;
  backdrop-filter: blur(2px) !important;
  background: rgba(0, 0, 0, 0.35) !important;
  pointer-events: none !important;
}

body, ytd-app {
  position: relative !important;
  z-index: 1 !important;
  background: transparent !important;
}

body *:not(#player-container):not(#player-container *):not(.html5-video-player):not(.html5-video-player *):not(video) {
  background-color: transparent !important;
  background-image: none !important;
  box-shadow: none !important;
  border-color: rgba(255,255,255,0.08) !important;
  text-shadow: none !important;
  color: #e8e8e8 !important;
}

#masthead-container, ytd-masthead {
  background-color: rgba(0, 0, 0, 0.35) !important;
  backdrop-filter: blur(3px) !important;
}

ytd-guide-renderer, #guide-content, tp-yt-app-drawer {
  background-color: rgba(0, 0, 0, 0.20) !important;
  backdrop-filter: blur(2px) !important;
}

#below, #meta, #description, ytd-video-primary-info-renderer,
ytd-video-secondary-info-renderer, iron-selector#chips {
  background-color: rgba(0, 0, 0, 0.20) !important;
  backdrop-filter: blur(2px) !important;
  border-radius: 12px !important;
}

ytd-comments, ytd-comment-thread-renderer, #comments {
  background-color: rgba(0, 0, 0, 0.20) !important;
  backdrop-filter: blur(2px) !important;
  border-radius: 12px !important;
}

#related, ytd-watch-next-secondary-results-renderer, ytd-compact-video-renderer {
  background-color: rgba(0, 0, 0, 0.15) !important;
  backdrop-filter: blur(2px) !important;
}

ytd-rich-item-renderer, ytd-video-renderer, ytd-grid-video-renderer {
  background-color: rgba(0, 0, 0, 0.12) !important;
  border-radius: 10px !important;
}
ytd-thumbnail, ytd-thumbnail img, yt-image img, #thumbnail img {
  background-color: transparent !important;
  background-image: revert !important;
}

tp-yt-iron-dropdown, ytd-popup-container, [role="menu"], [role="dialog"], tp-yt-paper-dialog {
  background-color: rgba(10, 10, 10, 0.55) !important;
  backdrop-filter: blur(4px) !important;
  border: 0.5px solid rgba(255,255,255,0.20) !important;
}

yt-button-shape button, tp-yt-paper-button, ytd-button-renderer {
  background-color: rgba(255,255,255,0.06) !important;
  border: 0.5px solid rgba(255,255,255,0.12) !important;
}

#search, #search-form, ytd-searchbox {
  background-color: rgba(255,255,255,0.06) !important;
  backdrop-filter: blur(2px) !important;
}

a { color: #7ab7ff !important; }

* { scrollbar-color: rgba(255,255,255,0.2) transparent !important; }
::-webkit-scrollbar { width: 6px; }
::-webkit-scrollbar-track { background: transparent !important; }
::-webkit-scrollbar-thumb {
  background-color: rgba(255,255,255,0.2) !important;
  border-radius: 4px;
}

::selection, ::-moz-selection {
  background: rgba(255,255,255,0.15) !important;
}

.ytp-play-progress,
.ytp-play-progress.ytp-swatch-background-color {
  background: linear-gradient(to right, #9b6dff 20%, #ffd2b8 60%) !important;
}
.ytp-scrubber-button.ytp-swatch-background-color {
  background: url("https://raw.githubusercontent.com/XDertZX/Pictures/refs/heads/main/kafkachiquitareal.gif")
    no-repeat !important;
  background-size: contain !important;
  box-shadow: none !important;
  border: none !important;
  width: 28px !important;
  height: 28px !important;
  margin-left: -8px !important;
  margin-top: -16px !important;
}
.ytp-scrubber-button.ytp-swatch-background-color:hover {
  background: url("https://raw.githubusercontent.com/XDertZX/Pictures/refs/heads/main/kafkachiquitareal.gif")
    no-repeat !important;
  background-size: contain !important;
}
