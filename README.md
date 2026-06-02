# Benedita-Tech
HTML5 semântico, CSS com variáveis (:root), Flexbox, Grid, responsividade (media viewport), gradientes, animações (@keyframes), transições, sombras (box-shadow), bordas arredondadas, pseudo-elementos (::before/::after), estados hover/focus e design system (botões, inputs, badges, cards).
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>Benedita Tech | Início</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,700;1,400;1,700&family=DM+Sans:opsz,wght@9..40,400;9..40,500;9..40,700&display=swap" rel="stylesheet">
    <style>
        /* === RESET & BASE === */
        *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

        :root {
            --roxo:         #5A1ED6;
            --roxo-escuro:  #3f11a0;
            --roxo-claro:   #ede6fb;
            --bege:         #F3E7D2;
            --bege-escuro:  #e6d4b8;
            --marrom:       #B8834E;
            --marrom-claro: #f5ebe0;
            --branco:       #FFFFFF;
            --preto:        #1a1a1a;
            --cinza:        #6b6b6b;
            --verde:        #2a7a4b;
            --shadow-card:  4px 4px 0px var(--marrom);
            --shadow-hover: 7px 7px 0px var(--marrom);
            --radius:       16px;
            --radius-sm:    10px;
        }

        html { font-size: 16px; scroll-behavior: smooth; }

        body {
            font-family: 'DM Sans', sans-serif;
            background-color: var(--bege);
            background-image:
                radial-gradient(circle at 15% 50%, rgba(90,30,214,.06) 0%, transparent 50%),
                radial-gradient(circle at 85% 20%, rgba(184,131,78,.08) 0%, transparent 40%);
            color: var(--preto);
            min-height: 100vh;
        }

        .sr-only {
            position: absolute; width: 1px; height: 1px;
            padding: 0; margin: -1px; overflow: hidden;
            clip: rect(0,0,0,0); white-space: nowrap; border: 0;
        }

        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 6px;
            background-color: var(--bege);
            color: var(--roxo);
            border: 2.5px solid var(--preto);
            outline: 2px solid var(--preto);
            outline-offset: 3px;
            border-radius: 50px;
            padding: 10px 24px;
            font-family: 'DM Sans', sans-serif;
            font-size: 0.9rem;
            font-weight: 700;
            letter-spacing: 0.02em;
            cursor: pointer;
            transition: background-color .18s ease, color .18s ease, transform .12s ease, box-shadow .15s ease;
        }
        .btn:hover {
            background-color: var(--roxo);
            color: var(--branco);
            outline-color: var(--roxo);
            transform: translateY(-2px);
        }
        .btn:active { transform: translateY(0); }

        .btn-sm { padding: 7px 18px; font-size: 0.82rem; }

        .btn-destaque {
            background-color: var(--roxo);
            color: var(--branco);
            border-color: var(--roxo);
            outline-color: var(--roxo);
            box-shadow: 3px 3px 0px var(--preto);
        }
        .btn-destaque:hover {
            background-color: var(--roxo-escuro);
            border-color: var(--roxo-escuro);
            outline-color: var(--roxo-escuro);
            transform: translate(-2px, -2px);
            box-shadow: 5px 5px 0px var(--preto);
        }

        .btn-header {
            background-color: var(--branco);
            color: var(--roxo);
            border-color: var(--branco);
            outline-color: rgba(255,255,255,.5);
            white-space: nowrap;
        }
        .btn-header:hover {
            background-color: var(--preto);
            color: var(--branco);
            border-color: var(--preto);
            outline-color: var(--preto);
        }

        .input-wrap { display: flex; flex-direction: column; gap: 6px; width: 100%; }
        .input-label { font-size: 0.82rem; font-weight: 700; color: var(--preto); letter-spacing: 0.02em; }
        .input-label span.obrigatorio { color: var(--roxo); margin-left: 2px; }
        .input-base {
            width: 100%; background-color: var(--branco);
            border: 2.5px solid var(--preto); border-radius: var(--radius-sm);
            padding: 10px 14px; font-family: 'DM Sans', sans-serif;
            font-size: 0.9rem; color: var(--preto); outline: none;
            transition: border-color .18s ease, box-shadow .18s ease;
        }
        .input-base::placeholder { color: #aaa; }
        .input-base:focus { border-color: var(--roxo); box-shadow: 0 0 0 3px rgba(90,30,214,.15); }
        .input-base:disabled { background-color: var(--bege-escuro); color: var(--cinza); cursor: not-allowed; border-color: var(--bege-escuro); }
        .input-icon-wrap { position: relative; }
        .input-icon-wrap .input-icon { position: absolute; left: 12px; top: 50%; transform: translateY(-50%); pointer-events: none; font-size: 1rem; }
        .input-icon-wrap .input-base { padding-left: 38px; }
        .textarea-base {
            width: 100%; background-color: var(--branco);
            border: 2.5px solid var(--preto); border-radius: var(--radius-sm);
            padding: 10px 14px; font-family: 'DM Sans', sans-serif;
            font-size: 0.9rem; color: var(--preto); outline: none;
            resize: vertical; min-height: 100px;
            transition: border-color .18s ease, box-shadow .18s ease;
        }
        .textarea-base::placeholder { color: #aaa; }
        .textarea-base:focus { border-color: var(--roxo); box-shadow: 0 0 0 3px rgba(90,30,214,.15); }
        .input-msg { font-size: 0.76rem; font-weight: 600; margin-top: 2px; }
        .input-msg.erro  { color: #c0392b; }
        .input-msg.sucesso { color: var(--verde); }
        select.input-base {
            appearance: none;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%235A1ED6' stroke-width='2' fill='none' stroke-linecap='round'/%3E%3C/svg%3E");
            background-repeat: no-repeat; background-position: right 14px center; padding-right: 36px;
        }

        .badge {
            display: inline-flex; align-items: center; gap: 4px;
            border-radius: 50px; padding: 3px 11px;
            font-size: 0.74rem; font-weight: 700;
            letter-spacing: 0.03em; border: 1.5px solid transparent; white-space: nowrap;
        }
        .badge-roxo { background-color: var(--roxo-claro); color: var(--roxo); border-color: var(--roxo); }
        .badge-marrom { background-color: var(--marrom-claro); color: var(--marrom); border-color: var(--marrom); }
        .badge-verde { background-color: #d1fae5; color: var(--verde); border-color: var(--verde); }
        .badge-cinza { background-color: var(--bege-escuro); color: var(--cinza); border-color: var(--cinza); }
        .badge-preto { background-color: var(--preto); color: var(--branco); border-color: var(--preto); }
        .badge-selo { border: 2px solid var(--preto); box-shadow: 2px 2px 0 var(--preto); font-size: 0.72rem; }
        .badge-destaque { background: linear-gradient(90deg, var(--roxo), #8b47e8); color: var(--branco); border-color: var(--roxo-escuro); box-shadow: 2px 2px 0 var(--preto); }
        .badge-novo { background: linear-gradient(90deg, #22c55e, #16a34a); color: var(--branco); border-color: #15803d; box-shadow: 2px 2px 0 var(--preto); }
        .badge-verificado { background: linear-gradient(90deg, var(--marrom), #d4a267); color: var(--branco); border-color: #8a5c2e; box-shadow: 2px 2px 0 var(--preto); }
        .badge-popular { background: linear-gradient(90deg, #f59e0b, #d97706); color: var(--branco); border-color: #b45309; box-shadow: 2px 2px 0 var(--preto); }

        #landingPage {
            display: flex; align-items: center; justify-content: center;
            min-height: 100vh; padding: 1.5rem;
        }
        .landing-container {
            max-width: 1300px; width: 100%;
            background: rgba(255, 255, 255, 0.4);
            backdrop-filter: blur(2px); border-radius: 48px;
            padding: 1rem; box-shadow: 0 20px 35px -12px rgba(0,0,0,0.2);
        }
        .landing-card {
            background-color: var(--branco); border-radius: 40px;
            overflow: hidden; box-shadow: 8px 8px 0 var(--marrom);
            border: 2px solid var(--preto);
        }
        .hero-landing {
            background: linear-gradient(125deg, #3f0fa0 0%, var(--roxo) 45%, #a36eff 100%);
            padding: 3rem 2.5rem 4rem; text-align: center;
            position: relative; border-bottom: 3px solid var(--preto); overflow: hidden;
        }
        .hero-landing::before { content: "✨"; font-size: 110px; position: absolute; bottom: -30px; right: 20px; opacity: 0.15; pointer-events: none; transform: rotate(10deg); }
        .hero-landing::after { content: "📚"; font-size: 95px; position: absolute; top: 20px; left: 25px; opacity: 0.12; pointer-events: none; }
        .logo-landing {
            display: inline-flex; align-items: center; gap: 12px;
            background: rgba(255,255,255,0.12); backdrop-filter: blur(6px);
            padding: 8px 24px; border-radius: 100px;
            border: 1px solid rgba(255,255,255,0.3); margin-bottom: 2rem;
        }
        .logo-icon-land { font-size: 2rem; animation: float 3s ease infinite; }
        @keyframes float { 0% { transform: translateY(0px); } 50% { transform: translateY(-5px); } 100% { transform: translateY(0px); } }
        .logo-landing h2 { font-family: 'Playfair Display', serif; font-size: 1.9rem; color: white; letter-spacing: -0.5px; }
        .hero-landing h1 { font-family: 'Playfair Display', serif; font-size: clamp(2.4rem, 6vw, 4rem); font-weight: 700; color: white; line-height: 1.2; margin-bottom: 1.2rem; text-shadow: 2px 2px 0 rgba(0,0,0,0.1); }
        .hero-landing h1 em { font-style: italic; color: #fdd67a; font-weight: 400; }
        .hero-landing p { font-size: 1.1rem; max-width: 600px; margin: 0 auto 1.8rem; color: rgba(255,255,255,0.85); }
        .btn-entrar {
            background-color: var(--bege); border: 3px solid var(--preto);
            outline: 3px solid var(--preto); outline-offset: 4px;
            border-radius: 60px; padding: 14px 38px;
            font-family: 'DM Sans', sans-serif; font-weight: 800;
            font-size: 1.2rem; color: var(--roxo); cursor: pointer;
            transition: 0.2s ease; box-shadow: 6px 6px 0 var(--preto);
            display: inline-flex; align-items: center; gap: 12px;
        }
        .btn-entrar:hover {
            background-color: var(--roxo); color: white;
            transform: translate(-3px, -3px); box-shadow: 10px 10px 0 var(--preto);
            border-color: white; outline-color: var(--roxo);
        }
        .features-grid {
            display: flex; flex-wrap: wrap; justify-content: center;
            gap: 2rem; padding: 3rem 2rem; background: var(--branco);
        }
        .feature-item {
            flex: 1; min-width: 180px; background: var(--bege);
            border-radius: 28px; padding: 1.5rem 1rem; text-align: center;
            border: 2px solid var(--preto); box-shadow: 5px 5px 0 var(--marrom);
            transition: all 0.2s;
        }
        .feature-item:hover { transform: translateY(-6px); box-shadow: 8px 8px 0 var(--marrom); }
        .feature-icon {
            font-size: 2.3rem; width: 65px; height: 65px;
            display: flex; align-items: center; justify-content: center;
            margin: 0 auto 1rem; border-radius: 30px;
            background: var(--roxo); color: white; border: 2px solid var(--preto);
        }
        .feature-item h3 { font-family: 'Playfair Display', serif; font-size: 1.3rem; margin-bottom: 0.4rem; color: var(--roxo); }
        .feature-item p { font-size: 0.85rem; color: #444; }
        .testimonials { background: var(--bege-escuro); padding: 2.5rem 2rem; text-align: center; border-top: 2px solid var(--marrom); }
        .testimonials h3 { font-family: 'Playfair Display', serif; font-size: 1.8rem; color: var(--preto); margin-bottom: 1.2rem; }
        .quote { font-style: italic; max-width: 550px; margin: 0.6rem auto; color: #2c2c2c; font-weight: 500; }
        .footer-landing { background-color: var(--preto); color: #aaa; text-align: center; padding: 1.2rem; font-size: 0.8rem; }

        #platformPage { display: none; flex-direction: column; min-height: 100vh; }
        #platformPage.visible { display: flex; }

        #platformPage header {
            background-color: var(--roxo);
            background-image: linear-gradient(135deg, var(--roxo) 0%, #7b3fe4 100%);
            display: flex; align-items: center; justify-content: space-between;
            gap: 16px; padding: 14px 40px; flex-wrap: wrap;
            position: sticky; top: 0; z-index: 100;
            box-shadow: 0 2px 20px rgba(90,30,214,.3);
        }

        .logo { display: flex; align-items: center; gap: 8px; }
        .logo-icon {
            display: flex; align-items: center;
        }
        .logo h1 {
            font-family: 'Playfair Display', serif;
            font-weight: 700; font-size: 1.45rem;
            color: var(--branco); letter-spacing: 0.02em;
        }

        .nav-materias { display: flex; align-items: center; gap: 6px; flex-wrap: wrap; }
        .nav-tag {
            color: rgba(255,255,255,.7); text-decoration: none;
            font-size: 0.82rem; font-weight: 500; padding: 5px 12px;
            border-radius: 50px; border: 1.5px solid transparent; transition: all .2s ease;
        }
        .nav-tag:hover, .nav-tag.active {
            color: var(--branco); border-color: rgba(255,255,255,.5);
            background-color: rgba(255,255,255,.12);
        }

        .header-actions { display: flex; align-items: center; gap: 10px; }
        .search-wrap { position: relative; display: flex; align-items: center; }
        .search-icon { position: absolute; left: 12px; color: var(--cinza); pointer-events: none; }
        #platformPage header input[type="search"] {
            background-color: rgba(255,255,255,.95); border: 2px solid transparent;
            border-radius: 50px; padding: 8px 18px 8px 36px;
            font-family: 'DM Sans', sans-serif; font-size: 0.88rem;
            color: var(--preto); width: 220px; transition: all .2s ease;
        }
        #platformPage header input[type="search"]:focus {
            outline: none; border-color: var(--marrom);
            width: 260px; box-shadow: 0 0 0 3px rgba(184,131,78,.2);
        }
        #platformPage header input[type="search"]::placeholder { color: #999; }

        .hero {
            background: linear-gradient(135deg, #3a0fa8 0%, var(--roxo) 50%, #8b47e8 100%);
            padding: 52px 40px 48px; display: flex; align-items: center;
            justify-content: space-between; gap: 40px; flex-wrap: wrap;
            overflow: hidden; position: relative;
        }
        .hero::before { content: ''; position: absolute; top: -80px; right: -80px; width: 350px; height: 350px; border-radius: 50%; background: rgba(255,255,255,.04); border: 1px solid rgba(255,255,255,.08); }
        .hero::after { content: ''; position: absolute; bottom: -60px; left: 200px; width: 220px; height: 220px; border-radius: 50%; background: rgba(184,131,78,.12); }
        .hero-content { position: relative; z-index: 1; max-width: 500px; }
        .hero-eyebrow {
            display: inline-block; background-color: rgba(255,255,255,.15);
            border: 1px solid rgba(255,255,255,.25); color: rgba(255,255,255,.9);
            font-size: 0.78rem; font-weight: 700; letter-spacing: 0.08em;
            text-transform: uppercase; padding: 5px 14px; border-radius: 50px; margin-bottom: 18px;
        }
        .hero-title { font-family: 'Playfair Display', serif; font-size: clamp(2rem, 4vw, 3rem); font-weight: 700; color: var(--branco); line-height: 1.15; margin-bottom: 16px; }
        .hero-title em { font-style: italic; font-weight: 400; color: #f0c87a; }
        .hero-sub { font-size: 0.95rem; color: rgba(255,255,255,.75); line-height: 1.65; max-width: 420px; }
        .hero-stats { display: flex; gap: 28px; position: relative; z-index: 1; flex-wrap: wrap; }
        .stat { background: rgba(255,255,255,.1); border: 1px solid rgba(255,255,255,.2); backdrop-filter: blur(8px); border-radius: var(--radius); padding: 18px 24px; text-align: center; min-width: 100px; transition: transform .2s ease; }
        .stat:hover { transform: translateY(-4px); }
        .stat-num { display: block; font-family: 'Playfair Display', serif; font-size: 1.9rem; font-weight: 700; color: #f0c87a; }
        .stat-label { display: block; font-size: 0.74rem; color: rgba(255,255,255,.7); font-weight: 500; margin-top: 2px; }

        #platformPage main {
            display: grid; grid-template-columns: 280px 1fr;
            gap: 32px; padding: 36px 40px; flex: 1;
            align-items: start; max-width: 1280px; width: 100%; margin: 0 auto;
        }

        .sidebar { display: flex; flex-direction: column; gap: 20px; position: sticky; top: 72px; }
        .sidebar > section {
            background-color: var(--branco); border: 2.5px solid var(--preto);
            border-radius: var(--radius); padding: 22px 20px;
            animation: slideUp .4s ease both;
        }
        @keyframes slideUp { from { opacity: 0; transform: translateY(16px); } to { opacity: 1; transform: translateY(0); } }
        .sidebar > section:nth-child(2) { animation-delay: .05s; }
        .sidebar > section:nth-child(3) { animation-delay: .10s; }
        .sidebar > section:nth-child(4) { animation-delay: .15s; }

        .perfil { text-align: center; display: flex; flex-direction: column; align-items: center; gap: 10px; }
        .avatar-wrap { position: relative; display: inline-block; }
        .avatar {
            width: 76px; height: 76px; border-radius: 50%;
            background: linear-gradient(135deg, var(--roxo), #8b47e8); color: var(--branco);
            font-family: 'Playfair Display', serif; font-size: 2.1rem; font-weight: 700;
            display: flex; align-items: center; justify-content: center;
            border: 3px solid var(--preto); box-shadow: 3px 3px 0px var(--marrom);
        }
        .avatar-badge { position: absolute; bottom: 3px; right: 3px; width: 14px; height: 14px; border-radius: 50%; background: #22c55e; border: 2px solid var(--branco); }
        .perfil-info { display: flex; flex-direction: column; gap: 3px; }
        .perfil h2 { font-family: 'Playfair Display', serif; font-size: 1.2rem; color: var(--preto); }
        .usuario-email { font-size: 0.76rem; color: var(--cinza); word-break: break-all; }
        .perfil-meta { display: flex; gap: 8px; flex-wrap: wrap; justify-content: center; }
        .meta-pill { background-color: var(--roxo-claro); color: var(--roxo); border-radius: 50px; padding: 3px 10px; font-size: 0.75rem; font-weight: 700; }

        .progresso h3, .agenda h3 { font-family: 'Playfair Display', serif; font-size: 1rem; color: var(--roxo); display: flex; align-items: center; gap: 6px; margin-bottom: 14px; }
        .progress-item { margin-bottom: 12px; }
        .progress-item:last-child { margin-bottom: 0; }
        .progress-label { display: flex; justify-content: space-between; font-size: 0.8rem; font-weight: 500; color: var(--preto); margin-bottom: 5px; }
        .progress-val { color: var(--roxo); font-weight: 700; }
        .progress-bar { background-color: var(--bege-escuro); border-radius: 50px; height: 8px; overflow: hidden; }
        .progress-fill { height: 100%; background: linear-gradient(90deg, var(--roxo), #8b47e8); border-radius: 50px; transition: width .6s ease; }

        .agenda textarea {
            resize: vertical; min-height: 100px; width: 100%;
            border: 2px solid var(--bege-escuro); border-radius: var(--radius-sm);
            padding: 10px 12px; font-family: 'DM Sans', sans-serif;
            font-size: 0.87rem; color: var(--preto); background-color: var(--bege);
            outline: none; transition: border-color .15s; margin-bottom: 10px;
        }
        .agenda textarea:focus { border-color: var(--roxo); }

        .sidebar-actions { background: none !important; border: none !important; padding: 0 !important; }
        .sidebar-actions .btn { width: 100%; justify-content: center; }

        .feed-artigos { display: flex; flex-direction: column; gap: 22px; }
        .feed-header { display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap; gap: 12px; margin-bottom: 4px; }
        .feed-titulo { font-family: 'Playfair Display', serif; font-size: 1.5rem; color: var(--preto); }
        .feed-filtros { display: flex; gap: 6px; }
        .filtro {
            background: none; border: 2px solid var(--bege-escuro); border-radius: 50px;
            padding: 5px 14px; font-family: 'DM Sans', sans-serif; font-size: 0.8rem;
            font-weight: 600; color: var(--cinza); cursor: pointer; transition: all .2s ease;
        }
        .filtro:hover, .filtro.active { background-color: var(--roxo); border-color: var(--roxo); color: var(--branco); }

        .artigo {
            background-color: var(--branco); border: 2.5px solid var(--preto);
            border-radius: var(--radius); padding: 26px 28px;
            display: flex; flex-direction: column; gap: 12px;
            box-shadow: var(--shadow-card); transition: transform .18s ease, box-shadow .18s ease;
            animation: slideUp .45s ease both;
        }
        .artigo:nth-child(2) { animation-delay: .08s; }
        .artigo:nth-child(3) { animation-delay: .14s; }
        .artigo:nth-child(4) { animation-delay: .20s; }
        .artigo:hover { transform: translate(-3px, -3px); box-shadow: var(--shadow-hover); }
        .artigo-destaque { border-color: var(--roxo); background: linear-gradient(160deg, #faf7ff 0%, var(--branco) 100%); }

        .artigo-header { display: flex; align-items: center; justify-content: space-between; }
        .artigo-autor { display: flex; align-items: center; gap: 10px; }
        .mini-avatar {
            width: 36px; height: 36px; border-radius: 50%;
            background-color: var(--roxo); color: var(--branco);
            font-size: 0.88rem; font-weight: 700;
            display: flex; align-items: center; justify-content: center;
            border: 2px solid var(--preto); flex-shrink: 0;
        }
        .autor-nome { display: block; font-size: 0.85rem; font-weight: 700; color: var(--preto); }
        .artigo-data { display: block; font-size: 0.74rem; color: var(--cinza); }
        .artigo-materia { background-color: var(--roxo-claro); color: var(--roxo); border-radius: 50px; padding: 4px 12px; font-size: 0.74rem; font-weight: 700; letter-spacing: 0.03em; }
        .artigo h2 { font-family: 'Playfair Display', serif; font-size: 1.22rem; color: var(--preto); line-height: 1.3; transition: color .15s ease; }
        .artigo h2:hover { color: var(--roxo); cursor: pointer; }
        .artigo p { font-size: 0.9rem; color: #555; line-height: 1.65; }

        .tags { list-style: none; display: flex; flex-wrap: wrap; gap: 6px; }
        .tag { background-color: var(--bege); border: 1.5px solid var(--bege-escuro); border-radius: 50px; padding: 3px 11px; font-size: 0.76rem; font-weight: 600; color: var(--cinza); cursor: pointer; transition: all .15s ease; }
        .tag:hover { background-color: var(--roxo-claro); border-color: var(--roxo); color: var(--roxo); }

        .artigo-footer { display: flex; align-items: center; justify-content: space-between; padding-top: 8px; border-top: 1.5px solid var(--bege-escuro); flex-wrap: wrap; gap: 10px; }
        .artigo-meta { display: flex; gap: 16px; }
        .meta-item { display: flex; align-items: center; gap: 5px; font-size: 0.8rem; color: var(--cinza); }

        #platformPage footer { background-color: var(--preto); color: rgba(255,255,255,.6); text-align: center; padding: 20px 40px; font-size: 0.82rem; margin-top: auto; }
        #platformPage footer a { color: var(--marrom); text-decoration: none; }
        #platformPage footer a:hover { text-decoration: underline; }
    </style>
</head>
<body>

    <!-- ===== LANDING PAGE ===== -->
    <div id="landingPage">
        <div class="landing-container">
            <div class="landing-card">
                <div class="hero-landing">
                    <div class="logo-landing">
                        <span class="logo-icon-land">⚡</span>
                        <h2>Benedita Tech</h2>
                    </div>
                    <h1>Estude, compartilhe e <em>transforme</em><br>o seu futuro</h1>
                    <p>Uma comunidade vibrante onde estudantes publicam resumos, artigos e se ajudam a conquistar notas incríveis.</p>
                    <button id="enterPlatformBtn" class="btn-entrar">
                        🚀 Explorar plataforma <span aria-hidden="true">→</span>
                    </button>
                </div>
                <div class="features-grid">
                    <div class="feature-item">
                        <div class="feature-icon">📘</div>
                        <h3>+1.200 Artigos</h3>
                        <p>Conteúdo colaborativo de estudantes para estudantes.</p>
                    </div>
                    <div class="feature-item">
                        <div class="feature-icon">🏆</div>
                        <h3>Rankings & Metas</h3>
                        <p>Acompanhe seu progresso e incentive colegas.</p>
                    </div>
                    <div class="feature-item">
                        <div class="feature-icon">💬</div>
                        <h3>Comunidade Ativa</h3>
                        <p>Comentários, dicas e suporte em todas as matérias.</p>
                    </div>
                </div>
                <div class="testimonials">
                    <h3>💜 O que dizem por aqui</h3>
                    <div class="quote">"A Benedita Tech me ajudou a passar no vestibular com resumos incríveis de matemática!" — Marina R.</div>
                    <div class="quote">"Publiquei meus resumos de história e recebi feedbacks que me fizeram evoluir demais." — João P.</div>
                </div>
                <div class="footer-landing">
                    <p>© 2026 Benedita Tech — conhecimento livre e colaborativo</p>
                </div>
            </div>
        </div>
    </div>

    <!-- ===== PLATAFORMA ===== -->
    <div id="platformPage">

        <header>
            <div class="logo">
                <span class="logo-icon" aria-hidden="true"><img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAADqUlEQVR4nO2XX0iddRjHP8/7vuePHttZsR2nsTb/HNwuogl62dW2GriK3SVBFxXBWAMDI+jAWJEFG0qsGBPzsNlWUUHUhXIqyFCXsgWtsgtj/qsdp55Q53/POe/ThZvO1HPeI8Yi+t79+D1/vs+f3/M+r6iqcg9h3Evn/xNwRMAw0nN0IrMhAmK4aawJcaPr1LoyZcXbaKwJYRqy+QTCNa8C0HGpYc0oP3/pIdqutgLQ8GZocwmILEY0PjHN0+/1MdhZC8RXyNiGie+BfSvkN43A3eOhuvIAXU21iJW9rCjCG1+P8/IzBxifmN6Q85QE7sbpDyM8erINsRURQURQ4MTBLdRdjIBuLHoANAVM06UuK0uHR68roIB+erxQZyJFusWDWpal8elu1T5RSW1qXVipyCUSc4iYeGYKcHks5udmpbx4hyYMP+NzC2KKW6dje9laoMwvFAG206Q6ywCCIqiq4vP5VFWJDfdr7+Vzqhq/o45hmarzuWon4xlnYBVd27axbRsAUfjkWAG3ot/o1OSUTEQva1IM8m6FiPW1qtoqXd81aqInieUbg34PIoJt245fhaim/hpmiXA9ehNRE7c1RtJYrtpXtYcZmwxw+stuBgcaSEoFJimrugppCzarSn7gfnmt8iOqn4+gaqNqszP3INv3XeLqz0cYHOgHeSpj544IALzwRL3iTfJD26/sCjzG/j2nKPFW8HG4FfHOg2Sn1FdVyvbmEv2+bs1LB41SogYl+rD/qLqkWMPhsD7iO6YGJZpIptcfHhnUaKxfDdzpm3DtNC2Q0J/EiHt5v6maw0/ux9AsEvqjZJnBlLoiJkiC/G27Ser8GrYdIK69uMSj8mAYsFFNUlVfiClZuqC/ra+YiFIWtMgLFK4Y7SvgpASABne4tDTo19KgX0djQ1qct3hezwSgw6O9695nVII7EMOi6sTbNDc3szXHx+TUDAYuxHSvlBMvIyP95G5PEfltOCagAi3tV5bOf05McV9ONjeunKW02L/s3BL+6DxJbmB3WueOCaxlqLO7h6nJGb79ZYGW869QvmcXTRfruXD+HK6iSmyH237aSQgQzHfTfq2HSKRlUQkvZ15/jtCRcmbjE8xIgBfPtKO2LI1xp8ioBzxd7wBw6NDjVFUUoGXPUhcZ490vupEkGTsHnL+CbLepQx01+tnxnRodGtCBjrc05/aOIBg6+HuvE1OrbWcifOGDs0uLyc3Yxhz+HY564J/Ev//P6D9P4C+M5KHk67UacQAAAABJRU5ErkJggg==" style="width:28px;height:28px;image-rendering:pixelated;vertical-align:middle;" alt="gato logo"></span>
                <h1>Benedita Tech</h1>
            </div>
            <nav class="nav-materias" aria-label="Matérias">
                <a href="#" class="nav-tag active" data-filter="all">Todas</a>
                <a href="#" class="nav-tag" data-filter="Matemática">Matemática</a>
                <a href="#" class="nav-tag" data-filter="Português">Português</a>
                <a href="#" class="nav-tag" data-filter="Ciências">Ciências</a>
                <a href="#" class="nav-tag" data-filter="História">História</a>
                <a href="#" class="nav-tag" data-filter="Geografia">Geografia</a>
            </nav>
            <div class="header-actions">
                <div class="search-wrap">
                    <span class="search-icon" aria-hidden="true">🔍</span>
                    <input type="search" id="searchInput" placeholder="Buscar artigos…" aria-label="Buscar artigos">
                </div>
                <button class="btn btn-header btn-sm" id="publishBtnSimulate">+ Publicar</button>
            </div>
        </header>

        <section class="hero" aria-label="Destaque">
            <div class="hero-content">
                <span class="hero-eyebrow">Plataforma de Estudos</span>
                <h2 class="hero-title">Aprenda e compartilhe<br><em>conhecimento</em> com todos</h2>
                <p class="hero-sub">Uma comunidade colaborativa onde estudantes publicam resumos, dicas e artigos para ajudar outros a aprender mais.</p>
            </div>
            <div class="hero-stats" aria-label="Estatísticas da plataforma">
                <div class="stat"><span class="stat-num">1.2k</span><span class="stat-label">Artigos</span></div>
                <div class="stat"><span class="stat-num">340</span><span class="stat-label">Autores</span></div>
                <div class="stat"><span class="stat-num">8.5k</span><span class="stat-label">Leituras</span></div>
            </div>
        </section>

        <main>
            <aside class="sidebar">
                <section class="perfil" aria-label="Perfil do usuário">
                    <div class="avatar-wrap">
                        <div class="avatar" aria-hidden="true">A</div>
                        <span class="avatar-badge" title="Online"></span>
                    </div>
                    <div class="perfil-info">
                        <h2>Ana Souza</h2>
                        <span class="usuario-email">ana.souza@escola.edu.br</span>
                    </div>
                    <div class="perfil-meta">
                        <span class="meta-pill">3º Ano</span>
                        <span class="meta-pill">12 artigos</span>
                    </div>
                </section>

                <section class="progresso" aria-label="Progresso de estudos">
                    <h3>📊 Progresso</h3>
                    <div class="progress-item">
                        <div class="progress-label"><span>Matemática</span><span class="progress-val">72%</span></div>
                        <div class="progress-bar"><div class="progress-fill" style="width:72%"></div></div>
                    </div>
                    <div class="progress-item">
                        <div class="progress-label"><span>Português</span><span class="progress-val">58%</span></div>
                        <div class="progress-bar"><div class="progress-fill" style="width:58%"></div></div>
                    </div>
                    <div class="progress-item">
                        <div class="progress-label"><span>Ciências</span><span class="progress-val">85%</span></div>
                        <div class="progress-bar"><div class="progress-fill" style="width:85%"></div></div>
                    </div>
                </section>

                <section class="agenda" aria-label="Anotações rápidas">
                    <h3>📝 Anotações</h3>
                    <textarea id="notesTextarea" placeholder="Escreva lembretes, tarefas ou metas de estudo…" aria-label="Campo de anotações"></textarea>
                    <button class="btn btn-destaque btn-sm" id="saveNotesBtn">Salvar</button>
                </section>

                <section class="sidebar-actions">
                    <button class="btn" id="configMockBtn">⚙️ Configurações</button>
                </section>

                <section aria-label="Busca rápida">
                    <h3 style="font-family:'Playfair Display',serif;font-size:1rem;color:var(--roxo);display:flex;align-items:center;gap:6px;margin-bottom:14px;">🔎 Busca rápida</h3>
                    <div class="input-wrap">
                        <label class="input-label" for="quickSearch">Matéria ou tema <span class="obrigatorio">*</span></label>
                        <div class="input-icon-wrap">
                            <span class="input-icon">📖</span>
                            <input id="quickSearch" type="text" class="input-base" placeholder="Ex: fotossíntese…">
                        </div>
                    </div>
                    <div class="input-wrap" style="margin-top:10px;">
                        <label class="input-label" for="quickSelect">Filtrar por ano</label>
                        <select id="quickSelect" class="input-base" style="cursor:pointer;">
                            <option value="">Todos os anos</option>
                            <option>1º Ano</option>
                            <option>2º Ano</option>
                            <option selected>3º Ano</option>
                        </select>
                    </div>
                    <button class="btn btn-destaque btn-sm" style="width:100%;margin-top:12px;" onclick="
                        const q = document.getElementById('quickSearch').value;
                        if(q.trim()){
                            const si = document.getElementById('searchInput');
                            si.value = q;
                            si.dispatchEvent(new Event('input'));
                        }
                    ">Buscar</button>
                </section>
            </aside>

            <section class="feed-artigos" aria-label="Feed de artigos">
                <div class="feed-header">
                    <h2 class="feed-titulo">Artigos Recentes</h2>
                    <div class="feed-filtros" role="group" aria-label="Filtrar artigos">
                        <button class="filtro active" data-sort="recent">Recentes</button>
                        <button class="filtro" data-sort="popular">Populares</button>
                        <button class="filtro" data-sort="saved">Salvos</button>
                    </div>
                </div>

                <div id="articlesContainer">
                    <article class="artigo artigo-destaque" data-materia="Matemática" data-likes="48" data-titulo="Guia completo de funções do 2º grau para o ENEM">
                        <div class="artigo-header">
                            <div class="artigo-autor">
                                <div class="mini-avatar" aria-hidden="true">C</div>
                                <div><span class="autor-nome">Carlos Menezes</span><span class="artigo-data">28 mai 2026</span></div>
                            </div>
                            <div style="display:flex;gap:6px;align-items:center;flex-wrap:wrap;">
                                <span class="badge badge-destaque badge-selo">⭐ Destaque</span>
                                <span class="badge badge-popular badge-selo">🔥 Popular</span>
                                <span class="artigo-materia">Matemática</span>
                            </div>
                        </div>
                        <h2>Guia completo de funções do 2º grau para o ENEM</h2>
                        <p>Entenda de vez como funcionam as parábolas, vértice, delta e todas as propriedades que mais caem nas provas. Com exemplos resolvidos passo a passo.</p>
                        <ul class="tags">
                            <li><button class="tag">funções</button></li>
                            <li><button class="tag">ENEM</button></li>
                            <li><button class="tag">parábola</button></li>
                        </ul>
                        <div class="artigo-footer">
                            <div class="artigo-meta">
                                <span class="meta-item like-count">👍 48</span>
                                <span class="meta-item">💬 12</span>
                                <span class="meta-item">⏱️ 8 min</span>
                            </div>
                            <button class="btn btn-destaque btn-sm read-btn">Ler artigo</button>
                        </div>
                    </article>

                    <article class="artigo" data-materia="Português" data-likes="36" data-titulo="Como escrever uma redação nota 1000 no ENEM">
                        <div class="artigo-header">
                            <div class="artigo-autor">
                                <div class="mini-avatar" style="background:#b8834e" aria-hidden="true">M</div>
                                <div><span class="autor-nome">Mariana Lima</span><span class="artigo-data">27 mai 2026</span></div>
                            </div>
                            <div style="display:flex;gap:6px;align-items:center;flex-wrap:wrap;">
                                <span class="badge badge-novo badge-selo">✨ Novo</span>
                                <span class="artigo-materia">Português</span>
                            </div>
                        </div>
                        <h2>Como escrever uma redação nota 1000 no ENEM</h2>
                        <p>Dicas práticas de estrutura, coesão, coerência e proposta de intervenção. Exemplos de introduções que impressionam os corretores.</p>
                        <ul class="tags">
                            <li><button class="tag">redação</button></li>
                            <li><button class="tag">dissertação</button></li>
                            <li><button class="tag">escrita</button></li>
                        </ul>
                        <div class="artigo-footer">
                            <div class="artigo-meta">
                                <span class="meta-item like-count">👍 36</span>
                                <span class="meta-item">💬 7</span>
                                <span class="meta-item">⏱️ 6 min</span>
                            </div>
                            <button class="btn btn-sm read-btn">Ler artigo</button>
                        </div>
                    </article>

                    <article class="artigo" data-materia="Ciências" data-likes="29" data-titulo="Fotossíntese e respiração celular: diferenças e semelhanças">
                        <div class="artigo-header">
                            <div class="artigo-autor">
                                <div class="mini-avatar" style="background:#2a7a4b" aria-hidden="true">P</div>
                                <div><span class="autor-nome">Pedro Alves</span><span class="artigo-data">26 mai 2026</span></div>
                            </div>
                            <div style="display:flex;gap:6px;align-items:center;flex-wrap:wrap;">
                                <span class="badge badge-verificado badge-selo">✅ Verificado</span>
                                <span class="artigo-materia">Ciências</span>
                            </div>
                        </div>
                        <h2>Fotossíntese e respiração celular: diferenças e semelhanças</h2>
                        <p>Um resumo visual e didático dos dois processos mais cobrados em Biologia, com esquemas e macetes para não confundir nas provas.</p>
                        <ul class="tags">
                            <li><button class="tag">biologia</button></li>
                            <li><button class="tag">fotossíntese</button></li>
                            <li><button class="tag">célula</button></li>
                        </ul>
                        <div class="artigo-footer">
                            <div class="artigo-meta">
                                <span class="meta-item like-count">👍 29</span>
                                <span class="meta-item">💬 5</span>
                                <span class="meta-item">⏱️ 5 min</span>
                            </div>
                            <button class="btn btn-sm read-btn">Ler artigo</button>
                        </div>
                    </article>

                    <article class="artigo" data-materia="História" data-likes="22" data-titulo="Revolução Industrial: causas e impactos no mundo atual">
                        <div class="artigo-header">
                            <div class="artigo-autor">
                                <div class="mini-avatar" style="background:#5A1ED6" aria-hidden="true">L</div>
                                <div><span class="autor-nome">Laura Mendes</span><span class="artigo-data">25 mai 2026</span></div>
                            </div>
                            <span class="artigo-materia">História</span>
                        </div>
                        <h2>Revolução Industrial: causas e impactos no mundo atual</h2>
                        <p>Contexto histórico, invenções e transformações sociais. Resumo completo para provas e vestibulares.</p>
                        <ul class="tags">
                            <li><button class="tag">industrial</button></li>
                            <li><button class="tag">século XVIII</button></li>
                        </ul>
                        <div class="artigo-footer">
                            <div class="artigo-meta">
                                <span class="meta-item like-count">👍 22</span>
                                <span class="meta-item">💬 8</span>
                                <span class="meta-item">⏱️ 7 min</span>
                            </div>
                            <button class="btn btn-sm read-btn">Ler artigo</button>
                        </div>
                    </article>
                </div>
            </section>
        </main>

        <footer>
            <p>© 2026 Benedita Tech — Feito com 💜 para estudantes. <a href="#">Termos</a> · <a href="#">Privacidade</a></p>
        </footer>
    </div>

    <script>
    (function () {
        const landingDiv  = document.getElementById('landingPage');
        const platformDiv = document.getElementById('platformPage');
        const enterBtn    = document.getElementById('enterPlatformBtn');

        function showPlatform() {
            landingDiv.style.display = 'none';
            platformDiv.classList.add('visible');
            document.body.style.padding = '0';
            document.body.style.backgroundImage = 'none';
            const savedNotes = localStorage.getItem('benedita_notes');
            if (savedNotes) {
                const notesArea = document.getElementById('notesTextarea');
                if (notesArea) notesArea.value = savedNotes;
            }
        }

        if (enterBtn) enterBtn.addEventListener('click', showPlatform);

        const saveNotesBtn  = document.getElementById('saveNotesBtn');
        const notesTextarea = document.getElementById('notesTextarea');
        if (saveNotesBtn && notesTextarea) {
            saveNotesBtn.addEventListener('click', () => {
                localStorage.setItem('benedita_notes', notesTextarea.value);
                alert('Anotações salvas com sucesso! 📝');
            });
        }

        const navTags = document.querySelectorAll('.nav-tag');
        const articles = document.querySelectorAll('#articlesContainer .artigo');

        function filterBySubject(subject) {
            articles.forEach(art => {
                art.style.display = (subject === 'all' || art.dataset.materia === subject) ? 'flex' : 'none';
            });
            navTags.forEach(tag => {
                tag.classList.toggle('active', tag.dataset.filter === subject || (tag.dataset.filter === 'all' && subject === 'all'));
            });
        }

        navTags.forEach(tag => {
            tag.addEventListener('click', e => {
                e.preventDefault();
                filterBySubject(tag.dataset.filter || 'all');
            });
        });

        const searchInput = document.getElementById('searchInput');
        if (searchInput) {
            searchInput.addEventListener('input', e => {
                const q = e.target.value.toLowerCase().trim();
                articles.forEach(art => {
                    const title = art.querySelector('h2')?.innerText.toLowerCase() || '';
                    const desc  = art.querySelector('p')?.innerText.toLowerCase() || '';
                    art.style.display = (!q || title.includes(q) || desc.includes(q)) ? 'flex' : 'none';
                });
            });
        }

        const sortButtons = document.querySelectorAll('.filtro');
        sortButtons.forEach(btn => {
            btn.addEventListener('click', () => {
                sortButtons.forEach(b => b.classList.remove('active'));
                btn.classList.add('active');
                const sort = btn.dataset.sort;
                if (sort === 'saved') { alert('🔖 Funcionalidade "Salvos" em breve!'); return; }
                const container = document.getElementById('articlesContainer');
                const arr = Array.from(articles);
                if (sort === 'popular') {
                    arr.sort((a, b) => parseInt(b.dataset.likes || 0) - parseInt(a.dataset.likes || 0));
                }
                arr.forEach(art => container.appendChild(art));
            });
        });

        document.querySelectorAll('.read-btn').forEach(btn => {
            btn.addEventListener('click', e => {
                e.stopPropagation();
                const titulo = btn.closest('.artigo')?.querySelector('h2')?.innerText || 'artigo';
                alert('📖 Abrindo "' + titulo + '"\n(conteúdo completo em breve!)');
            });
        });

        const publishBtn = document.getElementById('publishBtnSimulate');
        if (publishBtn) publishBtn.addEventListener('click', () => {
            alert('✍️ Em breve você poderá publicar seus próprios artigos!');
        });

        const configBtn = document.getElementById('configMockBtn');
        if (configBtn) configBtn.addEventListener('click', () => {
            alert('⚙️ Central de configurações em desenvolvimento.');
        });

        document.querySelectorAll('.like-count').forEach(span => {
            span.style.cursor = 'pointer';
            span.addEventListener('click', e => {
                e.stopPropagation();
                let n = parseInt(span.innerText.replace('👍', '').trim()) || 0;
                span.innerText = '👍 ' + (n + 1);
                const art = span.closest('.artigo');
                if (art) art.dataset.likes = n + 1;
            });
        });

        document.querySelectorAll('.tag').forEach(tag => {
            tag.addEventListener('click', e => {
                e.preventDefault();
                if (searchInput) {
                    searchInput.value = tag.innerText;
                    searchInput.dispatchEvent(new Event('input'));
                }
            });
        });
    })();
    </script>
</body>
</html>
