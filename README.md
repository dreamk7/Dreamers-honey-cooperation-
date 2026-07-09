<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover, user-scalable=yes">
  <title>Bloom & Hive | Artisanal Beekeeping & Honey</title>
  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;400;500;600;700;800;900&family=Playfair+Display:ital,wght@0,500;0,600;0,700;0,800;0,900;1,500;1,600;1,700&display=swap" rel="stylesheet">
  <!-- Font Awesome 6 -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    /* ===== CSS VARIABLES ===== */
    :root {
      --primary-green: #0d3b2a;
      --secondary-green: #1a5a3a;
      --dark-green: #0e4a2f;
      --header-bg: #1F3B2C;
      --gold: #E9A23B;
      --gold-light: #FFD966;
      --text-light: #f0e8d0;
      --text-muted: #ddd0b0;
      --card-bg: rgba(255, 255, 255, 0.98);
      --shadow: 0 8px 20px rgba(0,0,0,0.08);
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      font-family: 'Inter', 'Segoe UI', Roboto, sans-serif;
      background: linear-gradient(135deg, #0a1a0f 0%, #0d2d1a 20%, #1a3d2a 40%, #2d4a2a 55%, #1a3d2a 70%, #0d2d1a 85%, #0a1a0f 100%);
      color: #ffffff;
      padding-top: 67px;
      overflow-x: hidden;
      position: relative;
      min-height: 100vh;
    }

    body::before {
      content: '';
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: 
        radial-gradient(ellipse at 25% 20%, rgba(233, 162, 59, 0.15) 0%, transparent 50%),
        radial-gradient(ellipse at 75% 80%, rgba(233, 162, 59, 0.10) 0%, transparent 45%),
        radial-gradient(ellipse at 50% 50%, rgba(255, 217, 102, 0.06) 0%, transparent 60%),
        radial-gradient(ellipse at 10% 60%, rgba(233, 162, 59, 0.05) 0%, transparent 30%),
        radial-gradient(ellipse at 90% 30%, rgba(233, 162, 59, 0.05) 0%, transparent 30%);
      pointer-events: none;
      z-index: 0;
    }

    body::after {
      content: '🐝';
      position: fixed;
      bottom: 30px;
      right: 30px;
      font-size: 4rem;
      opacity: 0.04;
      z-index: 0;
      pointer-events: none;
      animation: floatHoney 12s ease-in-out infinite;
    }

    @keyframes floatHoney {
      0%, 100% { transform: translateY(0) rotate(0deg) scale(1); }
      33% { transform: translateY(-15px) rotate(5deg) scale(1.05); }
      66% { transform: translateY(10px) rotate(-3deg) scale(0.95); }
    }

    ::-webkit-scrollbar { width: 8px; }
    ::-webkit-scrollbar-track { background: #1a4a2a; border-radius: 10px; }
    ::-webkit-scrollbar-thumb { background: var(--gold); border-radius: 10px; }

    .container {
      max-width: 1300px;
      margin: 0 auto;
      padding: 0 30px;
      position: relative;
      z-index: 1;
    }

    #backToTop {
      position: fixed;
      bottom: 30px;
      right: 30px;
      z-index: 999;
      background: var(--gold);
      color: #1a3a2a;
      border: none;
      width: 50px;
      height: 50px;
      border-radius: 50%;
      font-size: 1.3rem;
      cursor: pointer;
      box-shadow: 0 4px 20px rgba(233, 162, 59, 0.4);
      transition: all 0.3s ease;
      opacity: 0;
      visibility: hidden;
      transform: translateY(20px);
    }
    #backToTop.show {
      opacity: 1;
      visibility: visible;
      transform: translateY(0);
    }
    #backToTop:hover {
      background: #c07d1a;
      transform: scale(1.1);
      box-shadow: 0 6px 30px rgba(233, 162, 59, 0.6);
    }

    .main-header {
      background: rgba(31, 59, 44, 0.95);
      padding: 12px 0;
      border-bottom: 1px solid rgba(47, 84, 62, 0.5);
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      z-index: 200;
      transition: transform 0.3s ease-in-out, background 0.3s ease;
      transform: translateY(0);
      backdrop-filter: blur(10px);
    }
    .main-header.hide {
      transform: translateY(-100%);
    }

    .header-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: nowrap;
      gap: 16px;
    }

    .menu-toggle-wrapper {
      display: flex;
      align-items: center;
      flex-shrink: 0;
    }
    .menu-toggle {
      background: var(--gold-light);
      border: none;
      font-size: 1.4rem;
      font-weight: bold;
      cursor: pointer;
      padding: 6px 14px;
      border-radius: 40px;
      color: var(--header-bg);
      transition: 0.2s;
      font-family: inherit;
    }
    .menu-toggle:hover {
      background: #e6c04e;
      transform: scale(0.97);
    }

    .logo-section {
      text-align: center;
      line-height: 1.1;
      flex-shrink: 0;
    }
    .logo-img {
      display: block;
      margin: 0 auto;
      max-width: 50px;
      height: auto;
      border-radius: 50%;
    }
    .company-name {
      font-family: 'Georgia', serif;
      font-size: 1rem;
      font-weight: 700;
      color: var(--gold-light);
      margin-top: 4px;
      letter-spacing: 0.3px;
    }

    .search-bar {
      flex: 1;
      max-width: 380px;
      min-width: 180px;
      position: relative;
    }
    .search-bar form {
      display: flex;
      width: 100%;
    }
    .search-bar input {
      width: 100%;
      padding: 8px 16px;
      border: none;
      border-radius: 40px 0 0 40px;
      font-size: 0.85rem;
      outline: none;
      font-family: inherit;
      background: rgba(255,255,255,0.9);
    }
    .search-bar button {
      background: var(--gold-light);
      border: none;
      padding: 0 18px;
      border-radius: 0 40px 40px 0;
      font-weight: 700;
      cursor: pointer;
      color: var(--header-bg);
      font-size: 0.9rem;
      transition: 0.2s;
    }
    .search-bar button:hover {
      background: #e6c04e;
    }

    .search-suggestions {
      position: absolute;
      top: 100%;
      left: 0;
      right: 0;
      background: white;
      border-radius: 0 0 20px 20px;
      box-shadow: 0 8px 25px rgba(0,0,0,0.2);
      max-height: 300px;
      overflow-y: auto;
      display: none;
      z-index: 300;
      margin-top: 4px;
    }
    .search-suggestions.show {
      display: block;
    }
    .search-suggestion-item {
      padding: 10px 18px;
      color: #1a2c1e;
      cursor: pointer;
      transition: 0.2s;
      font-size: 0.85rem;
      border-bottom: 1px solid #f0f0f0;
    }
    .search-suggestion-item:hover {
      background: #f5f0e0;
    }
    .search-suggestion-item:last-child {
      border-bottom: none;
    }

    .right-links {
      display: flex;
      align-items: center;
      justify-content: flex-end;
      gap: 12px;
      flex-shrink: 0;
      flex-wrap: nowrap;
    }

    .animated-link {
      background: transparent;
      border: none;
      cursor: pointer;
      font-size: 0.85rem;
      font-weight: 500;
      display: flex;
      align-items: center;
      gap: 5px;
      font-family: inherit;
      text-decoration: none;
      position: relative;
      padding: 4px 6px;
      overflow: hidden;
      transition: transform 0.2s ease;
      white-space: nowrap;
    }

    .animated-link span {
      color: white;
      font-size: 0.85rem;
      letter-spacing: 0.2px;
      display: inline-block;
      opacity: 0;
      animation: dissolveInText 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94) forwards;
    }

    .signin-icon span { animation-delay: 0.05s; }
    .cart-link span { animation-delay: 0.15s; }
    .about-link span { animation-delay: 0.25s; }
    .trending-link span { animation-delay: 0.35s; }

    @keyframes dissolveInText {
      0% { opacity: 0; transform: translateY(4px); filter: blur(2px); }
      40% { opacity: 0.6; }
      100% { opacity: 1; transform: translateY(0); filter: blur(0); }
    }

    @keyframes sparklingSweep {
      0% { left: -100%; opacity: 0; }
      20% { opacity: 0.8; }
      60% { opacity: 0.9; }
      100% { left: 150%; opacity: 0; }
    }

    .animated-link::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 70%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(255, 217, 102, 0.7), rgba(255, 245, 180, 0.9), transparent);
      transform: skewX(-20deg);
      animation: sparklingSweep 2.4s ease-in-out infinite;
      pointer-events: none;
      z-index: 1;
    }

    .signin-icon::before { animation-delay: 0s; }
    .cart-link::before { animation-delay: 0.4s; }
    .about-link::before { animation-delay: 0.8s; }
    .trending-link::before { animation-delay: 1.2s; }

    .animated-link .link-icon {
      font-size: 1rem;
      opacity: 0;
      animation: dissolveInText 0.4s forwards;
    }
    .signin-icon .link-icon { animation-delay: 0s; }
    .cart-link .link-icon { animation-delay: 0.1s; }
    .about-link .link-icon { animation-delay: 0.2s; }
    .trending-link .link-icon { animation-delay: 0.3s; }

    .animated-link:hover {
      transform: scale(1.02);
    }
    .animated-link:hover span {
      text-shadow: 0 0 4px rgba(255, 217, 102, 0.6);
    }

    .nav-wrapper {
      background: rgba(31, 59, 44, 0.95);
      position: fixed;
      top: 67px;
      left: 0;
      right: 0;
      z-index: 199;
      transition: transform 0.3s ease-in-out;
      transform: translateY(0);
      backdrop-filter: blur(10px);
    }
    .nav-wrapper.hide {
      transform: translateY(-100%);
    }
    .nav-menu {
      max-height: 0;
      overflow: hidden;
      transition: max-height 0.4s ease-out;
    }
    .nav-menu.open {
      max-height: 280px;
      transition: max-height 0.5s ease-in;
    }
    .nav-links {
      display: flex;
      flex-wrap: wrap;
      gap: 24px;
      list-style: none;
      padding: 16px 0 20px 0;
      border-top: 1px solid rgba(59, 94, 72, 0.5);
    }
    .nav-links a {
      color: #F5F0E0;
      text-decoration: none;
      font-weight: 600;
      font-size: 0.9rem;
      letter-spacing: 0.3px;
      padding: 4px 0;
      white-space: nowrap;
      transition: 0.2s;
      cursor: pointer;
    }
    .nav-links a:hover {
      color: var(--gold-light);
    }

    @media (max-width: 950px) {
      .header-row {
        flex-wrap: wrap;
        gap: 12px;
      }
      .search-bar {
        order: 3;
        width: 100%;
        max-width: 100%;
        margin-top: 6px;
      }
      .logo-section {
        order: 2;
        margin-left: auto;
        margin-right: auto;
      }
      .menu-toggle-wrapper {
        order: 1;
      }
      .right-links {
        order: 4;
        width: 100%;
        justify-content: center;
        margin-top: 8px;
        gap: 16px;
        flex-wrap: wrap;
      }
      .animated-link span {
        font-size: 0.8rem;
      }
      .nav-links {
        flex-direction: column;
        gap: 12px;
      }
      .nav-links a {
        white-space: normal;
      }
      .nav-wrapper {
        top: 67px;
      }
      .animated-link::before {
        display: none !important;
      }
    }

    @media (max-width: 550px) {
      .container {
        padding: 0 16px;
      }
      .right-links {
        gap: 10px;
      }
      .animated-link span {
        font-size: 0.7rem;
      }
      .animated-link .link-icon {
        font-size: 0.85rem;
      }
      .logo-img {
        max-width: 40px;
      }
      body::after {
        font-size: 2.5rem;
        bottom: 15px;
        right: 15px;
      }
    }

    .modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.6);
      justify-content: center;
      align-items: center;
      z-index: 1000;
      backdrop-filter: blur(5px);
    }
    .modal-content {
      background: linear-gradient(135deg, #1a4a2a, #0d3b2a);
      padding: 32px;
      border-radius: 28px;
      width: 340px;
      max-width: 90%;
      text-align: center;
      box-shadow: 0 20px 60px rgba(0,0,0,0.5);
      color: #ffffff;
      border: 1px solid rgba(233, 162, 59, 0.2);
    }
    .modal-content h3 {
      margin-bottom: 16px;
      color: var(--gold-light);
      font-family: 'Playfair Display', serif;
    }
    .modal-content input {
      width: 100%;
      padding: 12px 16px;
      margin: 10px 0;
      border: 1px solid rgba(255,255,255,0.1);
      border-radius: 60px;
      font-size: 0.9rem;
      background: rgba(255,255,255,0.05);
      color: #fff;
    }
    .modal-content input::placeholder {
      color: rgba(255,255,255,0.4);
    }
    .modal-content input:focus {
      outline: none;
      border-color: var(--gold);
    }
    .modal-content button {
      background: var(--gold);
      border: none;
      padding: 12px 20px;
      border-radius: 60px;
      font-weight: bold;
      cursor: pointer;
      width: 100%;
      margin-top: 6px;
      color: #1a3a2a;
      transition: 0.2s;
    }
    .modal-content button:hover {
      background: #c07d1a;
      transform: scale(1.02);
    }
    .close-modal {
      margin-top: 10px;
      background: rgba(255,255,255,0.1) !important;
      color: #fff !important;
    }
    .close-modal:hover {
      background: rgba(255,255,255,0.2) !important;
    }

    .hero {
      position: relative;
      width: 100%;
      min-height: 100vh;
      background: var(--primary-green);
      overflow: hidden;
      margin-top: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 0;
    }

    .hero-background {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 0;
    }
    .hero-background img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      display: block;
      transition: opacity 0.8s ease-in-out;
      opacity: 1;
    }

    .hero-overlay {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, rgba(0,0,0,0.6) 0%, rgba(0,0,0,0.3) 50%, rgba(0,0,0,0.6) 100%);
      z-index: 1;
    }

    .hero-content {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 2;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 40px 30px;
    }

    .hero-badge {
      display: inline-block;
      background: rgba(233, 162, 59, 0.2);
      border: 1px solid rgba(233, 162, 59, 0.3);
      padding: 14px 36px;
      border-radius: 60px;
      font-size: 1.2rem;
      color: var(--gold-light);
      margin-bottom: 30px;
      backdrop-filter: blur(4px);
      letter-spacing: 3px;
      text-transform: uppercase;
      font-weight: 900;
      opacity: 0;
      box-shadow: 0 4px 20px rgba(0,0,0,0.3);
      transition: opacity 0.5s ease;
    }
    .hero-badge.show {
      opacity: 1;
      animation: fadeInDown 0.5s ease forwards;
    }

    .hero-title {
      font-family: 'Playfair Display', serif;
      font-size: 6.5rem;
      font-weight: 900;
      line-height: 1.1;
      margin-bottom: 28px;
      text-shadow: 0 4px 40px rgba(0,0,0,0.5);
      color: #ffffff;
      letter-spacing: 2px;
      opacity: 0;
      transition: opacity 0.5s ease;
    }
    .hero-title.show {
      opacity: 1;
      animation: fadeInUp 0.6s ease forwards;
    }
    .hero-title .gold {
      color: var(--gold-light);
      position: relative;
      display: inline-block;
      text-shadow: 0 0 40px rgba(233, 162, 59, 0.2);
      letter-spacing: 2.5px;
      font-weight: 900;
    }

    .hero-description {
      font-size: 1.8rem;
      color: #f5f0e8;
      text-shadow: 0 2px 30px rgba(0,0,0,0.5);
      max-width: 800px;
      line-height: 2.5;
      letter-spacing: 1.5px;
      word-spacing: 4px;
      opacity: 0;
      transition: opacity 0.5s ease;
      font-weight: 700;
    }
    .hero-description.show {
      opacity: 1;
    }
    .hero-description .dissolve-word {
      display: inline-block;
      opacity: 0;
      animation: dissolveWord 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94) forwards;
      letter-spacing: 1px;
      padding: 0 2px;
      font-weight: 700;
    }
    .hero-description .dissolve-word:nth-child(1) { animation-delay: 0.20s; }
    .hero-description .dissolve-word:nth-child(2) { animation-delay: 0.30s; }
    .hero-description .dissolve-word:nth-child(3) { animation-delay: 0.40s; }
    .hero-description .dissolve-word:nth-child(4) { animation-delay: 0.50s; }
    .hero-description .dissolve-word:nth-child(5) { animation-delay: 0.60s; }
    .hero-description .dissolve-word:nth-child(6) { animation-delay: 0.70s; }
    .hero-description .dissolve-word:nth-child(7) { animation-delay: 0.80s; }
    .hero-description .dissolve-word:nth-child(8) { animation-delay: 0.90s; }
    .hero-description .dissolve-word:nth-child(9) { animation-delay: 1.00s; }
    .hero-description .dissolve-word:nth-child(10) { animation-delay: 1.10s; }
    .hero-description .dissolve-word:nth-child(11) { animation-delay: 1.20s; }
    .hero-description .dissolve-word:nth-child(12) { animation-delay: 1.30s; }
    .hero-description .dissolve-word:nth-child(13) { animation-delay: 1.40s; }
    .hero-description .dissolve-word:nth-child(14) { animation-delay: 1.50s; }
    .hero-description .dissolve-word:nth-child(15) { animation-delay: 1.60s; }
    .hero-description .dissolve-word:nth-child(16) { animation-delay: 1.70s; }
    .hero-description .dissolve-word:nth-child(17) { animation-delay: 1.80s; }
    .hero-description .dissolve-word:nth-child(18) { animation-delay: 1.90s; }
    .hero-description .dissolve-word:nth-child(19) { animation-delay: 2.00s; }
    .hero-description .dissolve-word:nth-child(20) { animation-delay: 2.10s; }
    .hero-description .dissolve-word:nth-child(21) { animation-delay: 2.20s; }
    .hero-description .dissolve-word:nth-child(22) { animation-delay: 2.30s; }
    .hero-description .dissolve-word:nth-child(23) { animation-delay: 2.40s; }
    .hero-description .dissolve-word:nth-child(24) { animation-delay: 2.50s; }

    @keyframes dissolveWord {
      0% { opacity: 0; transform: translateY(8px); filter: blur(3px); }
      40% { opacity: 0.4; }
      100% { opacity: 1; transform: translateY(0); filter: blur(0); }
    }

    @keyframes fadeInUp {
      0% { opacity: 0; transform: translateY(25px); }
      100% { opacity: 1; transform: translateY(0); }
    }

    @keyframes fadeInDown {
      0% { opacity: 0; transform: translateY(-15px); }
      100% { opacity: 1; transform: translateY(0); }
    }

    @media (min-width: 1400px) {
      .hero-title { font-size: 8rem; letter-spacing: 3px; }
      .hero-description { font-size: 2.2rem; max-width: 900px; letter-spacing: 2px; word-spacing: 5px; line-height: 2.8; }
      .hero-badge { font-size: 1.4rem; padding: 16px 40px; letter-spacing: 4px; }
    }

    @media (max-width: 1399px) and (min-width: 1025px) {
      .hero-title { font-size: 6.5rem; letter-spacing: 2px; }
      .hero-description { font-size: 1.8rem; max-width: 750px; letter-spacing: 1.5px; word-spacing: 4px; line-height: 2.5; }
      .hero-badge { font-size: 1.2rem; padding: 14px 34px; letter-spacing: 3px; }
    }

    @media (max-width: 1024px) and (min-width: 769px) {
      .hero-title { font-size: 5rem; letter-spacing: 2px; }
      .hero-description { font-size: 1.5rem; max-width: 650px; line-height: 2.3; letter-spacing: 1.2px; word-spacing: 3px; }
      .hero-badge { font-size: 1rem; padding: 12px 28px; margin-bottom: 24px; letter-spacing: 2.5px; }
    }

    @media (max-width: 768px) and (min-width: 481px) {
      .hero-title { font-size: 3.8rem; margin-bottom: 20px; letter-spacing: 1.5px; }
      .hero-description { font-size: 1.2rem; max-width: 100%; line-height: 2.2; letter-spacing: 1px; word-spacing: 3px; }
      .hero-badge { font-size: 0.9rem; padding: 10px 24px; margin-bottom: 20px; letter-spacing: 2px; }
      .hero-content { 
