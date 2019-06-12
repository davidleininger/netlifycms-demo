<template>
  <div class="layout">
    <header class="header">
      <strong>
        <g-link to="/">{{ $static.metaData.siteName }}</g-link>
      </strong>
      <nav class="nav">
        <g-link class="nav__link" to="/about">About</g-link>
      </nav>
    </header>
    <slot/>
    <footer>
      <p class="footer-links">
        <a href="https://gridsome.org/docs" target="_blank" rel="noopener">Gridsome Docs</a>
        <a href="https://github.com/davidleininger/gridsome-netlifycms-starter" target="_blank" rel="noopener">GitHub</a>
      </p>
    </footer>
  </div>
</template>

<static-query>
query {
  metaData {
    siteName
  }
}
</static-query>

<style>
:root {
  --black: #1B2B34;
  --teal: #5FB3B3;
  --teal-dark: #59A9A5;
  --grey: #D8DEE9;
  --grey-dark: #A4ACB9;
  --red-light: #ed6f7d;
  --red: #B3545E;
  --white: #fff;
}
::-webkit-input-placeholder {
  color: var(--grey-dark);
}
*{
  box-sizing: border-box;
}
.flex{
  display: flex;
}
.in-line{
  display: inline-block;
}

body {
  font-family: -apple-system,system-ui,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif;
  margin:0;
  padding:0;
  line-height: 1.5;
}

.layout {
  display: grid;
  grid-template-rows: auto 1fr auto;
  margin: 0 auto;
  max-width: 900px;
  min-height: 100vh;
  padding:24px;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
.logo {
  color: var(--black);
  font-size: 1.5rem;
  text-decoration: none;
  text-transform: uppercase;
  transition: all 0.2s;
}
.logo:hover {
  color: var(--teal);
}

.nav__link {
  color: var(--black);
  font-size: 1.125rem;
  margin-left: 20px;
  padding: 0 0.25rem;
  position: relative;
  text-decoration: none;
}
.nav__link:after {
  background: var(--teal);
  bottom: -4px;
  content: '';
  height: 2px;
  left: 0;
  margin: 0 auto;
  position: absolute;
  transform: scaleX(0);
  transition: transform 0.3s ease;
  width: 100%;
}
.nav__link:hover:after {
  content: '';
  transform: scaleX(1);
}
.nav__link:hover {
  color: var(--black);
}
</style>
