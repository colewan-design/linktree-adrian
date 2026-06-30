<template>
  <main class="page">
    <div class="container">

      <!-- Profile -->
      <section class="profile">
        <div class="avatar-ring">
          <div class="avatar">
            <img src="/profile-bg.jpg" alt="Adrian Benig" class="avatar-img" />
          </div>
        </div>
        <h1 class="username">@adrianbenig</h1>

        <!-- Quick social icons -->
        <div class="social-icons">
          <a href="https://www.instagram.com/adrianbenig" target="_blank" rel="noopener" class="icon-btn" aria-label="Instagram">
            <IconInstagram />
          </a>
          <a href="https://www.tiktok.com/@adrianbenig" target="_blank" rel="noopener" class="icon-btn" aria-label="TikTok">
            <IconTikTok />
          </a>
          <a href="https://www.facebook.com/adrianbenig" target="_blank" rel="noopener" class="icon-btn" aria-label="Facebook">
            <IconFacebook />
          </a>
        </div>
      </section>

      <!-- Featured banner -->
      <section class="banner">
        <div class="banner-bg" />
        <div class="banner-content">
          <div class="banner-text">
            <p class="banner-name">Adrian Benig</p>
            <p class="banner-sub">Guitarist · Content Creator</p>
          </div>
          <span class="banner-tag">links</span>
        </div>
      </section>

      <!-- Links section -->
      <section class="links-section">
        <h2 class="section-label">SOCIAL MEDIA</h2>

        <div class="links-list">
          <a
            v-for="link in links"
            :key="link.id"
            :href="link.url"
            target="_blank"
            rel="noopener"
            class="link-card"
          >
            <div class="link-icon">
              <component :is="link.icon" />
            </div>
            <span class="link-label">{{ link.label }}</span>
            <div class="link-arrow">
              <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M9 18l6-6-6-6" />
              </svg>
            </div>
          </a>
        </div>
      </section>

      <footer class="footer">
        <p>© {{ new Date().getFullYear() }} Adrian Benig</p>
      </footer>

    </div>
  </main>
</template>

<script setup lang="ts">
import { defineComponent, h } from 'vue'

const IconInstagram = defineComponent({
  render: () =>
    h('svg', { width: 20, height: 20, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor', 'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round' }, [
      h('rect', { x: 2, y: 2, width: 20, height: 20, rx: 5, ry: 5 }),
      h('path', { d: 'M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z' }),
      h('line', { x1: 17.5, y1: 6.5, x2: 17.51, y2: 6.5 }),
    ]),
})

const IconTikTok = defineComponent({
  render: () =>
    h('svg', { width: 20, height: 20, viewBox: '0 0 24 24', fill: 'currentColor' }, [
      h('path', { d: 'M19.59 6.69a4.83 4.83 0 0 1-3.77-4.25V2h-3.45v13.67a2.89 2.89 0 0 1-2.88 2.5 2.89 2.89 0 0 1-2.89-2.89 2.89 2.89 0 0 1 2.89-2.89c.28 0 .54.04.79.1V9.01a6.32 6.32 0 0 0-.79-.05 6.34 6.34 0 0 0-6.34 6.34 6.34 6.34 0 0 0 6.34 6.34 6.34 6.34 0 0 0 6.33-6.34V8.69a8.17 8.17 0 0 0 4.78 1.52V6.75a4.85 4.85 0 0 1-1.01-.06z' }),
    ]),
})

const IconFacebook = defineComponent({
  render: () =>
    h('svg', { width: 20, height: 20, viewBox: '0 0 24 24', fill: 'none', stroke: 'currentColor', 'stroke-width': 2, 'stroke-linecap': 'round', 'stroke-linejoin': 'round' }, [
      h('path', { d: 'M18 2h-3a5 5 0 0 0-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 0 1 1-1h3z' }),
    ]),
})

const links = [
  { id: 'instagram', label: 'instagram',  url: 'https://www.instagram.com/adrianbenig', icon: IconInstagram },
  { id: 'tiktok',    label: 'tiktok',     url: 'https://www.tiktok.com/@adrianbenig',  icon: IconTikTok },
  { id: 'facebook',  label: 'facebook',   url: 'https://www.facebook.com/adrianbenig', icon: IconFacebook },
]
</script>

<style scoped>
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

.page {
  min-height: 100vh;
  background: #0d0d0d;
  color: #ffffff;
  font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
  display: flex;
  justify-content: center;
  padding: 48px 16px 32px;
}

.container {
  width: 100%;
  max-width: 440px;
  display: flex;
  flex-direction: column;
  gap: 28px;
}

/* ── profile ── */
.profile {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
}

.avatar-ring {
  padding: 3px;
  border-radius: 50%;
  background: linear-gradient(135deg, #444 0%, #1a1a1a 100%);
}

.avatar {
  width: 88px;
  height: 88px;
  border-radius: 50%;
  border: 3px solid #0d0d0d;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #111;
}

.avatar-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center top;
}

.username {
  font-size: 1rem;
  font-weight: 500;
  color: #e0e0e0;
  letter-spacing: 0.5px;
}

/* ── quick social icons ── */
.social-icons {
  display: flex;
  gap: 16px;
  margin-top: 4px;
}

.icon-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background: #1a1a1a;
  color: #ccc;
  text-decoration: none;
  transition: background 0.2s, color 0.2s;
}

.icon-btn:hover {
  background: #2a2a2a;
  color: #fff;
}

/* ── featured banner ── */
.banner {
  border-radius: 14px;
  overflow: hidden;
  position: relative;
  height: 140px;
  border: 1px solid #222;
}

.banner-bg {
  position: absolute;
  inset: 0;
  background-image: url('/profile-bg.jpg');
  background-size: cover;
  background-position: center 20%;
  filter: brightness(0.35);
}

.banner-content {
  position: relative;
  z-index: 1;
  height: 100%;
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  padding: 16px 20px;
}

.banner-name {
  font-size: 1.4rem;
  font-weight: 800;
  letter-spacing: -0.5px;
  color: #fff;
  font-style: italic;
}

.banner-sub {
  font-size: 0.72rem;
  color: #aaa;
  margin-top: 3px;
  letter-spacing: 0.3px;
}

.banner-tag {
  font-size: 0.62rem;
  text-transform: uppercase;
  letter-spacing: 2px;
  color: #888;
  border: 1px solid #444;
  padding: 4px 10px;
  border-radius: 20px;
  align-self: flex-start;
  margin-top: 16px;
}

/* ── links section ── */
.section-label {
  font-size: 0.62rem;
  letter-spacing: 3px;
  color: #555;
  font-weight: 600;
  text-align: center;
  margin-bottom: 12px;
}

.links-list {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.link-card {
  display: flex;
  align-items: center;
  gap: 14px;
  background: #161616;
  border: 1px solid #222;
  border-radius: 12px;
  padding: 14px 16px;
  text-decoration: none;
  color: #d0d0d0;
  transition: background 0.2s, border-color 0.2s, transform 0.15s;
}

.link-card:hover {
  background: #1e1e1e;
  border-color: #333;
  transform: translateY(-1px);
  color: #fff;
}

.link-card:active {
  transform: translateY(0);
}

.link-icon {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background: #222;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  color: #bbb;
}

.link-label {
  flex: 1;
  font-size: 0.9rem;
  font-weight: 500;
  letter-spacing: 0.5px;
  text-align: center;
}

.link-arrow {
  color: #444;
  flex-shrink: 0;
}

/* ── footer ── */
.footer {
  text-align: center;
  color: #333;
  font-size: 0.7rem;
  letter-spacing: 1px;
  padding-top: 8px;
}
</style>
