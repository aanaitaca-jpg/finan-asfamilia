<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>CRM Financeiro</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=DM+Mono:wght@300;400;500&display=swap" rel="stylesheet"/>
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js"></script>
<style>
  :root {
    --bg: #0d0f12;
    --bg2: #13161b;
    --bg3: #1a1e26;
    --border: rgba(255,255,255,0.07);
    --border2: rgba(255,255,255,0.12);
    --text: #f0ede8;
    --muted: #7a7d85;
    --muted2: #505360;
    --green: #00e08e;
    --green2: #00b872;
    --red: #ff4d4d;
    --red2: #cc2e2e;
    --blue: #3d8bff;
    --amber: #ffb347;
    --purple: #a78bfa;
    --accent: #00e08e;
    --card-r: 12px;
    --font: 'Syne', sans-serif;
    --mono: 'DM Mono', monospace;
  }
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  html, body { height: 100%; background: var(--bg); color: var(--text); font-family: var(--font); font-size: 14px; }

  /* LAYOUT */
  .app { display: flex; height: 100vh; overflow: hidden; }
  .sidebar { width: 220px; min-width: 220px; background: var(--bg2); border-right: 1px solid var(--border); display: flex; flex-direction: column; padding: 0; overflow: hidden; }
  .sidebar-logo { padding: 24px 20px 20px; border-bottom: 1px solid var(--border); }
  .sidebar-logo .logo-tag { font-size: 9px; font-family: var(--mono); color: var(--green); letter-spacing: .1em; text-transform: uppercase; margin-bottom: 4px; }
  .sidebar-logo h1 { font-size: 16px; font-weight: 800; color: var(--text); line-height: 1.1; }
  .sidebar-logo h1 span { color: var(--green); }
  .sidebar-nav { flex: 1; padding: 12px 0; overflow-y: auto; }
  .nav-section { font-size: 9px; font-family: var(--mono); color: var(--muted2); letter-spacing: .12em; text-transform: uppercase; padding: 12px 20px 6px; }
  .nav-item { display: flex; align-items: center; gap: 10px; padding: 9px 20px; cursor: pointer; font-size: 13px; font-weight: 500; color: var(--muted); transition: all .15s; border-left: 2px solid transparent; }
  .nav-item:hover { color: var(--text); background: rgba(255,255,255,.04); }
  .nav-item.active { color: var(--green); background: rgba(0,224,142,.06); border-left-color: var(--green); }
  .nav-item .icon { width: 16px; height: 16px; opacity: .7; flex-shrink: 0; }
  .nav-item.active .icon { opacity: 1; }
  .sidebar-footer { padding: 16px 20px; border-top: 1px solid var(--border); font-size: 11px; font-family: var(--mono); color: var(--muted2); }
  .sidebar-footer span { color: var(--green); }

  /* MAIN */
  .main { flex: 1; display: flex; flex-direction: column; overflow: hidden; }
  .topbar { height: 56px; background: var(--bg2); border-bottom: 1px solid var(--border); display: flex; align-items: center; justify-content: space-between; padding: 0 24px; flex-shrink: 0; }
  .topbar-title { font-size: 15px; font-weight: 700; color: var(--text); }
  .topbar-right { display: flex; align-items: center; gap: 12px; }
  .topbar-badge { font-size: 11px; font-family: var(--mono); background: rgba(0,224,142,.1); color: var(--green); border: 1px solid rgba(0,224,142,.25); border-radius: 4px; padding: 3px 8px; }
  .topbar-date { font-size: 11px; font-family: var(--mono); color: var(--muted); }
  .content { flex: 1; overflow-y: auto; padding: 24px; }

  /* TAB PAGES */
  .page { display: none; }
  .page.active { display: block; }

  /* CARDS */
  .card { background: var(--bg2); border: 1px solid var(--border); border-radius: var(--card-r); padding: 18px; }
  .card-title { font-size: 10px; font-family: var(--mono); color: var(--muted); letter-spacing: .1em; text-transform: uppercase; margin-bottom: 14px; }

  /* KPI GRID */
  .kpi-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(160px, 1fr)); gap: 12px; margin-bottom: 20px; }
  .kpi { background: var(--bg2); border: 1px solid var(--border); border-radius: var(--card-r); padding: 16px 18px; position: relative; overflow: hidden; }
  .kpi::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 2px; background: var(--kpi-color, var(--border2)); }
  .kpi.green { --kpi-color: var(--green); }
  .kpi.red { --kpi-color: var(--red); }
  .kpi.blue { --kpi-color: var(--blue); }
  .kpi.amber { --kpi-color: var(--amber); }
  .kpi-label { font-size: 10px; font-family: var(--mono); color: var(--muted); text-transform: uppercase; letter-spacing: .08em; margin-bottom: 8px; }
  .kpi-value { font-size: 22px; font-weight: 700; color: var(--text); font-family: var(--mono); line-height: 1; }
  .kpi.green .kpi-value { color: var(--green); }
  .kpi.red .kpi-value { color: var(--red); }
  .kpi.blue .kpi-value { color: var(--blue); }
  .kpi.amber .kpi-value { color: var(--amber); }
  .kpi-sub { font-size: 10px; font-family: var(--mono); color: var(--muted); margin-top: 5px; }

  /* CHARTS ROW */
  .charts-row { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; margin-bottom: 20px; }
  @media(max-width:900px) { .charts-row { grid-template-columns: 1fr; } }

  /* TABLE */
  .table-wrap { overflow-x: auto; border-radius: var(--card-r); border: 1px solid var(--border); }
  table { width: 100%; border-collapse: collapse; font-size: 12px; }
  thead th { background: var(--bg3); font-size: 10px; font-family: var(--mono); color: var(--muted); text-transform: uppercase; letter-spacing: .08em; padding: 10px 14px; text-align: left; white-space: nowrap; border-bottom: 1px solid var(--border); }
  tbody td { padding: 10px 14px; border-bottom: 1px solid var(--border); color: var(--text); vertical-align: middle; }
  tbody tr:last-child td { border-bottom: none; }
  tbody tr:hover td { background: rgba(255,255,255,.025); }

  /* BADGES */
  .badge { display: inline-block; padding: 2px 8px; border-radius: 4px; font-size: 10px; font-family: var(--mono); font-weight: 500; }
  .badge-green { background: rgba(0,224,142,.1); color: var(--green); border: 1px solid rgba(0,224,142,.2); }
  .badge-red { background: rgba(255,77,77,.1); color: var(--red); border: 1px solid rgba(255,77,77,.2); }
  .badge-blue { background: rgba(61,139,255,.1); color: var(--blue); border: 1px solid rgba(61,139,255,.2); }
  .badge-amber { background: rgba(255,179,71,.1); color: var(--amber); border: 1px solid rgba(255,179,71,.2); }
  .badge-gray { background: rgba(255,255,255,.05); color: var(--muted); border: 1px solid var(--border); }
  .badge-purple { background: rgba(167,139,250,.1); color: var(--purple); border: 1px solid rgba(167,139,250,.2); }

  /* FORM */
  .form-row { display: flex; gap: 8px; flex-wrap: wrap; margin-bottom: 14px; }
  .form-row input, .form-row select { flex: 1; min-width: 100px; background: var(--bg3); border: 1px solid var(--border2); border-radius: 6px; padding: 8px 10px; font-size: 12px; font-family: var(--mono); color: var(--text); outline: none; transition: border-color .15s; }
  .form-row input:focus, .form-row select:focus { border-color: var(--green); }
  .form-row input::placeholder { color: var(--muted2); }
  .form-row select option { background: var(--bg3); }
  .btn-add { background: rgba(0,224,142,.12); color: var(--green); border: 1px solid rgba(0,224,142,.3); border-radius: 6px; padding: 8px 16px; font-size: 12px; font-family: var(--mono); font-weight: 500; cursor: pointer; white-space: nowrap; transition: all .15s; }
  .btn-add:hover { background: rgba(0,224,142,.2); }

  /* SECTION HEADER */
  .section-title { display: flex; align-items: center; gap: 10px; margin: 20px 0 12px; }
  .section-title .line { flex: 1; height: 1px; background: var(--border); }
  .section-title span { font-size: 10px; font-family: var(--mono); color: var(--muted); text-transform: uppercase; letter-spacing: .1em; white-space: nowrap; }
  .section-title .dot { width: 6px; height: 6px; border-radius: 50%; flex-shrink: 0; }

  /* RESUMO BOX */
  .resumo-box { background: var(--bg3); border: 1px solid var(--border); border-radius: var(--card-r); padding: 14px 16px; margin-bottom: 16px; }
  .resumo-tag { font-size: 9px; font-family: var(--mono); color: var(--green); letter-spacing: .12em; text-transform: uppercase; margin-bottom: 10px; }
  .resumo-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; }
  .resumo-item { }
  .resumo-item .rl { font-size: 10px; font-family: var(--mono); color: var(--muted); margin-bottom: 2px; }
  .resumo-item .rv { font-size: 15px; font-weight: 700; font-family: var(--mono); }
  .resumo-insights { margin-top: 12px; padding-top: 10px; border-top: 1px solid var(--border); font-size: 11px; font-family: var(--mono); color: var(--muted); display: flex; flex-direction: column; gap: 4px; }

  /* MES TABS */
  .mes-tabs-wrap { display: flex; gap: 4px; flex-wrap: wrap; margin-bottom: 16px; }
  .mes-tab { padding: 5px 10px; font-size: 10px; font-family: var(--mono); border: 1px solid var(--border); border-radius: 4px; cursor: pointer; background: transparent; color: var(--muted); transition: all .12s; }
  .mes-tab:hover { color: var(--text); border-color: var(--border2); }
  .mes-tab.active { background: rgba(0,224,142,.1); color: var(--green); border-color: rgba(0,224,142,.35); }

  /* PROGRESS */
  .progress-bar { height: 5px; border-radius: 3px; background: var(--bg3); overflow: hidden; margin-top: 5px; }
  .progress-fill { height: 100%; border-radius: 3px; transition: width .4s cubic-bezier(.4,0,.2,1); }

  /* META CARD */
  .meta-item { padding: 14px 0; border-bottom: 1px solid var(--border); }
  .meta-item:last-child { border-bottom: none; }
  .meta-header { display: flex; justify-content: space-between; align-items: flex-start; margin-bottom: 8px; }
  .meta-name { font-size: 13px; font-weight: 600; }
  .meta-footer { display: flex; align-items: center; gap: 10px; }
  .meta-pct { font-size: 13px; font-weight: 700; font-family: var(--mono); }

  /* RANKING */
  .rank-item { display: flex; align-items: center; gap: 12px; padding: 8px 0; border-bottom: 1px solid var(--border); }
  .rank-item:last-child { border-bottom: none; }
  .rank-num { font-size: 11px; font-family: var(--mono); color: var(--muted2); min-width: 20px; }
  .rank-name { flex: 1; font-size: 12px; }
  .rank-bar { width: 100px; }
  .rank-val { font-size: 12px; font-family: var(--mono); color: var(--red); min-width: 80px; text-align: right; font-weight: 500; }

  /* CUSTOM SCROLLBAR */
  ::-webkit-scrollbar { width: 6px; height: 6px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--bg3); border-radius: 3px; }
  ::-webkit-scrollbar-thumb:hover { background: var(--muted2); }

  /* MOBILE */
  @media(max-width:700px) {
    .sidebar { width: 56px; min-width: 56px; }
    .sidebar-logo h1, .sidebar-logo .logo-tag, .nav-item span, .nav-section, .sidebar-footer { display: none; }
    .nav-item { justify-content: center; padding: 12px; }
    .content { padding: 16px; }
    .kpi-grid { grid-template-columns: 1fr 1fr; }
  }

  /* LEGEND */
  .legend { display: flex; flex-wrap: wrap; gap: 12px; margin-top: 10px; }
  .legend-item { display: flex; align-items: center; gap: 5px; font-size: 11px; font-family: var(--mono); color: var(--muted); }
  .legend-dot { width: 10px; height: 10px; border-radius: 2px; flex-shrink: 0; }

  /* INVEST SUMMARY */
  .inv-kpi-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 12px; margin-bottom: 16px; }
  @media(max-width:600px) { .inv-kpi-grid { grid-template-columns: 1fr; } }
</style>
</head>
<body>

<div class="app">

  <!-- SIDEBAR -->
  <aside class="sidebar">
    <div class="sidebar-logo">
      <div class="logo-tag">CRM / v1.0</div>
      <h1>Finance<span>OS</span></h1>
    </div>
    <nav class="sidebar-nav">
      <div class="nav-section">Principal</div>
      <div class="nav-item active" onclick="showPage('dashboard',this)">
        <svg class="icon" viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="1" y="1" width="6" height="6" rx="1"/><rect x="9" y="1" width="6" height="6" rx="1"/><rect x="1" y="9" width="6" height="6" rx="1"/><rect x="9" y="9" width="6" height="6" rx="1"/></svg>
        <span>Dashboard</span>
      </div>
      <div class="nav-item" onclick="showPage('mes',this)">
        <svg class="icon" viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="1" y="2" width="14" height="13" rx="1.5"/><path d="M5 1v2M11 1v2M1 6h14"/></svg>
        <span>Por Mês</span>
      </div>
      <div class="nav-item" onclick="showPage('anual',this)">
        <svg class="icon" viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M2 12l4-4 3 2 5-6"/><circle cx="2" cy="12" r="1.2" fill="currentColor"/><circle cx="6" cy="8" r="1.2" fill="currentColor"/><circle cx="9" cy="10" r="1.2" fill="currentColor"/><circle cx="14" cy="4" r="1.2" fill="currentColor"/></svg>
        <span>Consolidado Anual</span>
      </div>
      <div class="nav-section">Gestão</div>
      <div class="nav-item" onclick="showPage('metas',this)">
        <svg class="icon" viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="8" cy="8" r="6"/><circle cx="8" cy="8" r="3"/><path d="M8 1v2M8 13v2M1 8h2M13 8h2"/></svg>
        <span>Metas</span>
      </div>
      <div class="nav-item" onclick="showPage('fixas',this)">
        <svg class="icon" viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="1" y="3" width="14" height="11" rx="1.5"/><path d="M1 7h14M5 10h2M5 12h4"/></svg>
        <span>Contas Fixas</span>
      </div>
      <div class="nav-item" onclick="showPage('invest',this)">
        <svg class="icon" viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M2 14l3-4 3 1 3-5 3 2"/><path d="M11 3h3v3"/></svg>
        <span>Investimentos</span>
      </div>
    </nav>
    <div class="sidebar-footer">versão <span>1.0.0</span> · 2025</div>
  </aside>

  <!-- MAIN -->
  <main class="main">
    <div class="topbar">
      <div class="topbar-title" id="pageTitle">Dashboard</div>
      <div class="topbar-right">
        <span class="topbar-badge" id="todayBadge"></span>
        <span class="topbar-date" id="nowTime"></span>
      </div>
    </div>

    <div class="content">

      <!-- ===== DASHBOARD ===== -->
      <div class="page active" id="page-dashboard">
        <div class="kpi-grid">
          <div class="kpi green"><div class="kpi-label">Receita do mês</div><div class="kpi-value" id="kpi-receita">R$ 0</div><div class="kpi-sub">+ registre receitas</div></div>
          <div class="kpi red"><div class="kpi-label">Total de gastos</div><div class="kpi-value" id="kpi-gastos">R$ 22.318</div><div class="kpi-sub">fixos + variáveis</div></div>
          <div class="kpi blue"><div class="kpi-label">Lucro líquido</div><div class="kpi-value" id="kpi-lucro">—</div><div class="kpi-sub">receita − despesas</div></div>
          <div class="kpi amber"><div class="kpi-label">Cartão de crédito</div><div class="kpi-value">R$ 10.000</div><div class="kpi-sub">variável mensal</div></div>
        </div>

        <div class="charts-row">
          <div class="card">
            <div class="card-title">Distribuição de gastos fixos</div>
            <div style="position:relative;height:200px"><canvas id="chartPizza" role="img" aria-label="Pizza de gastos fixos por categoria">Gastos fixos por categoria.</canvas></div>
            <div class="legend" id="legendPizza"></div>
          </div>
          <div class="card">
            <div class="card-title">Gastos por categoria</div>
            <div style="position:relative;height:200px"><canvas id="chartBarras" role="img" aria-label="Barras de gastos por categoria">Gastos por categoria.</canvas></div>
          </div>
        </div>

        <div class="card">
          <div class="card-title">Ranking — maiores despesas</div>
          <div id="rankingList"></div>
        </div>
      </div>

      <!-- ===== POR MÊS ===== -->
      <div class="page" id="page-mes">
        <div class="mes-tabs-wrap" id="mesTabs"></div>

        <div class="resumo-box">
          <div class="resumo-tag">resumo rápido do mês</div>
          <div class="resumo-grid">
            <div class="resumo-item"><div class="rl">Receita total</div><div class="rv" id="mes-rec" style="color:var(--green)">R$ 0</div></div>
            <div class="resumo-item"><div class="rl">Despesa total</div><div class="rv" id="mes-desp" style="color:var(--red)">R$ 22.318</div></div>
            <div class="resumo-item"><div class="rl">Lucro líquido</div><div class="rv" id="mes-lucro">—</div></div>
            <div class="resumo-item"><div class="rl">% lucro</div><div class="rv" id="mes-pct">—</div></div>
          </div>
          <div class="resumo-insights">
            <div>Gastei mais com: <span style="color:var(--text)" id="ins-gasto">Parcela Apartamento</span></div>
            <div>Melhor fonte: <span style="color:var(--text)" id="ins-fonte">— adicione receitas</span></div>
          </div>
        </div>

        <div class="section-title"><span class="dot" style="background:var(--red)"></span><span>Bloco 1 — Despesas</span><div class="line"></div></div>
        <div class="form-row">
          <input type="date" id="desp-data"/>
          <select id="desp-tipo"><option>Fixo</option><option>Variável</option></select>
          <select id="desp-cat"><option>Moradia</option><option>Educação</option><option>Saúde</option><option>Transporte</option><option>Dívida</option><option>Seguro</option><option>Cartão</option><option>Lazer</option><option>Alimentação</option><option>Outro</option></select>
          <input type="text" id="desp-desc" placeholder="Descrição"/>
          <input type="number" id="desp-valor" placeholder="Valor R$"/>
          <button class="btn-add" onclick="addDespesa()">+ Adicionar</button>
        </div>
        <div class="table-wrap" style="margin-bottom:20px">
          <table id="tblDespesas">
            <thead><tr><th>Data</th><th>Tipo</th><th>Categoria</th><th>Descrição</th><th>Valor</th><th>Essencial</th><th>Impacto</th></tr></thead>
            <tbody id="bodyDespesas"></tbody>
          </table>
        </div>

        <div class="section-title"><span class="dot" style="background:var(--green)"></span><span>Bloco 2 — Receitas</span><div class="line"></div></div>
        <div class="form-row">
          <input type="date" id="rec-data"/>
          <input type="text" id="rec-fonte" placeholder="Cliente / Fonte"/>
          <input type="text" id="rec-servico" placeholder="Serviço"/>
          <input type="number" id="rec-valor" placeholder="Valor R$"/>
          <select id="rec-status"><option>Recebido</option><option>A receber</option><option>Pendente</option></select>
          <button class="btn-add" onclick="addReceita()">+ Adicionar</button>
        </div>
        <div class="table-wrap">
          <table id="tblReceitas">
            <thead><tr><th>Data</th><th>Fonte / Cliente</th><th>Serviço</th><th>Valor</th><th>Status</th></tr></thead>
            <tbody id="bodyReceitas"></tbody>
          </table>
        </div>
      </div>

      <!-- ===== CONSOLIDADO ANUAL ===== -->
      <div class="page" id="page-anual">
        <div class="card" style="margin-bottom:16px">
          <div class="card-title">Evolução anual — receita vs despesas</div>
          <div style="position:relative;height:220px"><canvas id="chartAnual" role="img" aria-label="Evolução anual receita e despesas">Dados mensais.</canvas></div>
        </div>
        <div class="table-wrap">
          <table>
            <thead><tr><th>Mês</th><th>Receita</th><th>Despesas</th><th>Lucro</th><th>% Lucro</th><th>Status</th></tr></thead>
            <tbody id="bodyAnual"></tbody>
          </table>
        </div>
      </div>

      <!-- ===== METAS ===== -->
      <div class="page" id="page-metas">
        <div class="card">
          <div class="form-row">
            <input type="text" id="meta-nome" placeholder="Descrição da meta" style="flex:2"/>
            <input type="number" id="meta-valor" placeholder="Valor R$"/>
            <input type="number" id="meta-atual" placeholder="Atual R$"/>
            <input type="text" id="meta-prazo" placeholder="Prazo ex: Dez/2026"/>
            <select id="meta-tipo"><option>Financeira</option><option>Investimento</option><option>Quitar dívida</option><option>Economia</option></select>
            <button class="btn-add" onclick="addMeta()">+ Meta</button>
          </div>
          <div id="listaMetas"></div>
        </div>
      </div>

      <!-- ===== CONTAS FIXAS ===== -->
      <div class="page" id="page-fixas">
        <div class="table-wrap">
          <table>
            <thead><tr><th>Conta</th><th>Valor</th><th>Vencimento</th><th>Tipo</th><th>Status</th><th>Observação</th></tr></thead>
            <tbody id="bodyFixas"></tbody>
          </table>
        </div>
      </div>

      <!-- ===== INVESTIMENTOS ===== -->
      <div class="page" id="page-invest">
        <div class="inv-kpi-grid">
          <div class="kpi blue"><div class="kpi-label">Total investido</div><div class="kpi-value" id="inv-total">R$ 0</div></div>
          <div class="kpi green"><div class="kpi-label">Ativos cadastrados</div><div class="kpi-value" id="inv-count">0</div></div>
          <div class="kpi amber"><div class="kpi-label">Objetivo principal</div><div class="kpi-value" style="font-size:14px" id="inv-obj">—</div></div>
        </div>
        <div class="card">
          <div class="form-row">
            <select id="inv-tipo"><option>Renda Fixa</option><option>Ações</option><option>FIIs</option><option>Tesouro</option><option>Criptomoedas</option><option>Poupança</option><option>Outro</option></select>
            <input type="text" id="inv-ativo" placeholder="Ativo ex: CDB XP 13%"/>
            <input type="number" id="inv-valor" placeholder="Valor R$"/>
            <input type="text" id="inv-rent" placeholder="Rentab. ex: 12% a.a."/>
            <input type="text" id="inv-objetivo" placeholder="Objetivo"/>
            <button class="btn-add" onclick="addInvest()">+ Adicionar</button>
          </div>
          <div class="table-wrap">
            <table>
              <thead><tr><th>Tipo</th><th>Ativo</th><th>Valor</th><th>Rentabilidade</th><th>Objetivo</th></tr></thead>
              <tbody id="bodyInvest"></tbody>
            </table>
          </div>
        </div>
      </div>

    </div><!-- /content -->
  </main>
</div><!-- /app -->

<script>
// ─── DATA ────────────────────────────────────────────────────────────────────
const MESES = ['Jan/2025','Fev/2025','Mar/2025','Abr/2025','Mai/2025','Jun/2025','Jul/2025','Ago/2025','Set/2025','Out/2025','Nov/2025','Dez/2025','Jan/2026','Fev/2026','Mar/2026','Abr/2026','Mai/2026','Jun/2026','Jul/2026','Ago/2026','Set/2026','Out/2026','Nov/2026','Dez/2026'];

const FIXAS = [
  {conta:'Parcela Apartamento',valor:7000,venc:'Dia 10',tipo:'Moradia',status:'Ativo',obs:''},
  {conta:'Escola Malu',valor:2500,venc:'Dia 5',tipo:'Educação',status:'Ativo',obs:''},
  {conta:'Seguro Carro',valor:0,venc:'—',tipo:'Transporte',status:'A confirmar',obs:'Verificar valor'},
  {conta:'Parcela Carro 1',valor:3000,venc:'Dia 15',tipo:'Transporte',status:'Ativo',obs:''},
  {conta:'Parcela Carro 2',valor:3600,venc:'Dia 20',tipo:'Transporte',status:'Ativo',obs:''},
  {conta:'Conta Luz',valor:400,venc:'Dia 8',tipo:'Moradia',status:'Ativo',obs:''},
  {conta:'Conta Água',valor:0,venc:'—',tipo:'Moradia',status:'A confirmar',obs:'Verificar valor'},
  {conta:'Internet',valor:400,venc:'Dia 12',tipo:'Moradia',status:'Ativo',obs:''},
  {conta:'IPTU',valor:791,venc:'Mensal',tipo:'Moradia',status:'Ativo',obs:''},
  {conta:'Seguro Saúde',valor:2500,venc:'Dia 1',tipo:'Saúde',status:'Ativo',obs:''},
  {conta:'Nubank 78',valor:78,venc:'Até Set/2026',tipo:'Dívida',status:'Ativo',obs:'Termina Set/2026'},
  {conta:'Seguro de Vida Nubank',valor:47,venc:'Mensal',tipo:'Seguro',status:'Ativo',obs:''},
];

const DESPESAS_BASE = [
  {data:'2025-04-01',tipo:'Fixo',cat:'Moradia',desc:'Parcela Apartamento',valor:7000,ess:'Sim',impacto:'Alto'},
  {data:'2025-04-05',tipo:'Fixo',cat:'Educação',desc:'Escola Malu',valor:2500,ess:'Sim',impacto:'Alto'},
  {data:'2025-04-01',tipo:'Fixo',cat:'Saúde',desc:'Seguro Saúde',valor:2500,ess:'Sim',impacto:'Alto'},
  {data:'2025-04-15',tipo:'Fixo',cat:'Transporte',desc:'Parcela Carro 1',valor:3000,ess:'Sim',impacto:'Alto'},
  {data:'2025-04-20',tipo:'Fixo',cat:'Transporte',desc:'Parcela Carro 2',valor:3600,ess:'Sim',impacto:'Alto'},
  {data:'2025-04-01',tipo:'Fixo',cat:'Moradia',desc:'IPTU',valor:791,ess:'Sim',impacto:'Médio'},
  {data:'2025-04-10',tipo:'Fixo',cat:'Moradia',desc:'Conta Luz',valor:400,ess:'Sim',impacto:'Médio'},
  {data:'2025-04-12',tipo:'Fixo',cat:'Moradia',desc:'Internet',valor:400,ess:'Sim',impacto:'Médio'},
  {data:'2025-04-01',tipo:'Fixo',cat:'Dívida',desc:'Nubank 78',valor:78,ess:'Sim',impacto:'Baixo'},
  {data:'2025-04-01',tipo:'Fixo',cat:'Seguro',desc:'Seguro Vida Nubank',valor:47,ess:'Sim',impacto:'Baixo'},
  {data:'2025-04-30',tipo:'Variável',cat:'Cartão',desc:'Cartão de Crédito',valor:10000,ess:'Variável',impacto:'Alto'},
];

let despesas = [...DESPESAS_BASE];
let receitas = [];
let investimentos = [];
let metas = [
  {nome:'Faturar R$ 10k/mês',valor:10000,atual:0,prazo:'Mensal',tipo:'Financeira'},
  {nome:'Quitar Nubank R$ 78',valor:78,atual:78,prazo:'Set/2026',tipo:'Quitar dívida'},
  {nome:'Investir 20% da renda',valor:0,atual:0,prazo:'Contínuo',tipo:'Investimento'},
];
let mesSel = 3;

// ─── UTILS ───────────────────────────────────────────────────────────────────
const BRL = v => 'R$ ' + Math.round(Number(v||0)).toLocaleString('pt-BR');
const COLORS = ['#ff4d4d','#3d8bff','#00e08e','#ffb347','#a78bfa','#ff6b9d','#00c5cc'];

// ─── CLOCK ────────────────────────────────────────────────────────────────────
function updateClock(){
  const now = new Date();
  document.getElementById('nowTime').textContent = now.toLocaleTimeString('pt-BR',{hour:'2-digit',minute:'2-digit'});
  document.getElementById('todayBadge').textContent = now.toLocaleDateString('pt-BR',{day:'2-digit',month:'short',year:'numeric'});
}
updateClock();
setInterval(updateClock,30000);

// ─── PAGE NAV ────────────────────────────────────────────────────────────────
const pageTitles = {dashboard:'Dashboard',mes:'Por Mês',anual:'Consolidado Anual',metas:'Metas',fixas:'Contas Fixas',invest:'Investimentos'};
function showPage(id,el){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.nav-item').forEach(n=>n.classList.remove('active'));
  document.getElementById('page-'+id).classList.add('active');
  if(el) el.classList.add('active');
  document.getElementById('pageTitle').textContent = pageTitles[id]||id;
  if(id==='anual') renderAnual();
  if(id==='invest') renderInvest();
}

// ─── MES TABS ────────────────────────────────────────────────────────────────
function buildMesTabs(){
  const c = document.getElementById('mesTabs');
  c.innerHTML = '';
  MESES.forEach((m,i)=>{
    const b = document.createElement('button');
    b.className = 'mes-tab'+(i===mesSel?' active':'');
    b.textContent = m;
    b.onclick = ()=>{ mesSel=i; buildMesTabs(); renderMes(); };
    c.appendChild(b);
  });
}

// ─── RENDER MES ──────────────────────────────────────────────────────────────
function renderMes(){
  const tbody = document.getElementById('bodyDespesas');
  if(!despesas.length){
    tbody.innerHTML = '<tr><td colspan="7" style="text-align:center;color:var(--muted);padding:20px">Nenhuma despesa registrada</td></tr>';
  } else {
    tbody.innerHTML = despesas.map(d=>`
      <tr>
        <td style="font-family:var(--mono);font-size:11px;color:var(--muted)">${d.data}</td>
        <td><span class="badge ${d.tipo==='Fixo'?'badge-blue':'badge-amber'}">${d.tipo}</span></td>
        <td><span class="badge badge-gray">${d.cat}</span></td>
        <td style="font-weight:500">${d.desc}</td>
        <td style="color:var(--red);font-family:var(--mono);font-weight:500">${BRL(d.valor)}</td>
        <td style="color:var(--muted);font-size:11px">${d.ess}</td>
        <td><span class="badge ${d.impacto==='Alto'?'badge-red':d.impacto==='Médio'?'badge-amber':'badge-gray'}">${d.impacto}</span></td>
      </tr>`).join('');
  }

  const rbody = document.getElementById('bodyReceitas');
  if(!receitas.length){
    rbody.innerHTML = '<tr><td colspan="5" style="text-align:center;color:var(--muted);padding:20px">Nenhuma receita ainda — adicione acima</td></tr>';
  } else {
    rbody.innerHTML = receitas.map(r=>`
      <tr>
        <td style="font-family:var(--mono);font-size:11px;color:var(--muted)">${r.data}</td>
        <td style="font-weight:500">${r.fonte}</td>
        <td style="color:var(--muted)">${r.servico}</td>
        <td style="color:var(--green);font-family:var(--mono);font-weight:500">${BRL(r.valor)}</td>
        <td><span class="badge ${r.status==='Recebido'?'badge-green':r.status==='A receber'?'badge-blue':'badge-amber'}">${r.status}</span></td>
      </tr>`).join('');
  }

  const td = despesas.reduce((a,d)=>a+Number(d.valor),0);
  const tr = receitas.reduce((a,r)=>a+Number(r.valor),0);
  const lucro = tr - td;
  const pct = tr > 0 ? ((lucro/tr)*100).toFixed(1) : null;

  document.getElementById('mes-rec').textContent = BRL(tr);
  document.getElementById('mes-desp').textContent = BRL(td);
  const el = document.getElementById('mes-lucro');
  el.textContent = tr>0 ? BRL(lucro) : '—';
  el.style.color = lucro>=0?'var(--green)':'var(--red)';
  document.getElementById('mes-pct').textContent = pct!==null ? pct+'%' : '—';

  const maior = despesas.sort((a,b)=>b.valor-a.valor)[0];
  document.getElementById('ins-gasto').textContent = maior ? maior.desc : '—';
  const melhor = receitas.sort((a,b)=>b.valor-a.valor)[0];
  document.getElementById('ins-fonte').textContent = melhor ? melhor.fonte : '— adicione receitas';

  document.getElementById('kpi-receita').textContent = BRL(tr);
  document.getElementById('kpi-gastos').textContent = BRL(td);
  const kl = document.getElementById('kpi-lucro');
  kl.textContent = tr>0 ? BRL(lucro) : '—';
  kl.style.color = lucro>=0?'var(--green)':'var(--red)';
}

function addDespesa(){
  const data = document.getElementById('desp-data').value || new Date().toISOString().split('T')[0];
  const tipo = document.getElementById('desp-tipo').value;
  const cat = document.getElementById('desp-cat').value;
  const desc = document.getElementById('desp-desc').value.trim();
  const valor = parseFloat(document.getElementById('desp-valor').value)||0;
  if(!desc||!valor) return alert('Preencha descrição e valor.');
  despesas.push({data,tipo,cat,desc,valor,ess:'Sim',impacto:'Médio'});
  document.getElementById('desp-desc').value='';
  document.getElementById('desp-valor').value='';
  renderMes(); buildCharts(); renderRanking();
}

function addReceita(){
  const data = document.getElementById('rec-data').value || new Date().toISOString().split('T')[0];
  const fonte = document.getElementById('rec-fonte').value.trim();
  const servico = document.getElementById('rec-servico').value.trim();
  const valor = parseFloat(document.getElementById('rec-valor').value)||0;
  const status = document.getElementById('rec-status').value;
  if(!fonte||!valor) return alert('Preencha fonte e valor.');
  receitas.push({data,fonte,servico,valor,status});
  document.getElementById('rec-fonte').value='';
  document.getElementById('rec-servico').value='';
  document.getElementById('rec-valor').value='';
  renderMes();
}

// ─── CONTAS FIXAS ────────────────────────────────────────────────────────────
function renderFixas(){
  document.getElementById('bodyFixas').innerHTML = FIXAS.map(f=>`
    <tr>
      <td style="font-weight:600">${f.conta}</td>
      <td style="font-family:var(--mono);color:${f.valor>0?'var(--red)':'var(--muted)'}">${f.valor>0?BRL(f.valor):'A confirmar'}</td>
      <td style="font-family:var(--mono);font-size:11px;color:var(--muted)">${f.venc}</td>
      <td><span class="badge badge-gray">${f.tipo}</span></td>
      <td><span class="badge ${f.status==='Ativo'?'badge-green':'badge-amber'}">${f.status}</span></td>
      <td style="color:var(--muted);font-size:11px">${f.obs}</td>
    </tr>`).join('');
}

// ─── METAS ────────────────────────────────────────────────────────────────────
function renderMetas(){
  const c = document.getElementById('listaMetas');
  c.innerHTML = metas.map((m,i)=>{
    const pct = m.valor>0 ? Math.min(100,Math.round((m.atual/m.valor)*100)) : 0;
    const cor = pct>=100?'var(--green)':pct>=50?'var(--amber)':'var(--red)';
    return `<div class="meta-item">
      <div class="meta-header">
        <span class="meta-name">${m.nome}</span>
        <div style="display:flex;gap:6px;align-items:center">
          <span class="badge badge-gray">${m.tipo}</span>
          <span style="font-size:10px;font-family:var(--mono);color:var(--muted)">${m.prazo}</span>
        </div>
      </div>
      <div class="meta-footer">
        <div class="progress-bar" style="flex:1"><div class="progress-fill" style="width:${pct}%;background:${cor}"></div></div>
        <span class="meta-pct" style="color:${cor}">${pct}%</span>
        <span style="font-size:10px;font-family:var(--mono);color:var(--muted)">${BRL(m.atual)} / ${m.valor>0?BRL(m.valor):'a definir'}</span>
      </div>
    </div>`;
  }).join('');
}

function addMeta(){
  const nome = document.getElementById('meta-nome').value.trim();
  const valor = parseFloat(document.getElementById('meta-valor').value)||0;
  const atual = parseFloat(document.getElementById('meta-atual').value)||0;
  const prazo = document.getElementById('meta-prazo').value||'—';
  const tipo = document.getElementById('meta-tipo').value;
  if(!nome) return;
  metas.push({nome,valor,atual,prazo,tipo});
  ['meta-nome','meta-valor','meta-atual','meta-prazo'].forEach(id=>document.getElementById(id).value='');
  renderMetas();
}

// ─── ANUAL ────────────────────────────────────────────────────────────────────
function renderAnual(){
  const dados = MESES.map((mes,i)=>{
    const isAtual = i===mesSel;
    const desp = isAtual ? despesas.reduce((a,d)=>a+Number(d.valor),0) : 22318;
    const rec = isAtual ? receitas.reduce((a,r)=>a+Number(r.valor),0) : 0;
    return {mes,rec,desp};
  });

  document.getElementById('bodyAnual').innerHTML = dados.map(d=>{
    const lucro = d.rec - d.desp;
    const pct = d.rec>0 ? ((lucro/d.rec)*100).toFixed(1)+'%' : '—';
    const cor = lucro>=0?'var(--green)':'var(--red)';
    return `<tr>
      <td style="font-weight:600">${d.mes}</td>
      <td style="color:var(--green);font-family:var(--mono)">${d.rec>0?BRL(d.rec):'—'}</td>
      <td style="color:var(--red);font-family:var(--mono)">${BRL(d.desp)}</td>
      <td style="color:${cor};font-family:var(--mono);font-weight:500">${d.rec>0?BRL(lucro):'—'}</td>
      <td style="font-family:var(--mono);color:var(--muted)">${pct}</td>
      <td><span class="badge ${d.rec>0?(lucro>=0?'badge-green':'badge-red'):'badge-gray'}">${d.rec>0?(lucro>=0?'Positivo':'Negativo'):'Sem receita'}</span></td>
    </tr>`;
  }).join('');

  const c = document.getElementById('chartAnual');
  if(window._ca) window._ca.destroy();
  const recent = dados.slice(0,6);
  window._ca = new Chart(c,{
    type:'bar',
    data:{
      labels:recent.map(d=>d.mes),
      datasets:[
        {label:'Receita',data:recent.map(d=>d.rec),backgroundColor:'rgba(0,224,142,.7)',borderRadius:4},
        {label:'Despesas',data:recent.map(d=>d.desp),backgroundColor:'rgba(255,77,77,.7)',borderRadius:4}
      ]
    },
    options:{
      responsive:true,maintainAspectRatio:false,
      plugins:{legend:{display:false}},
      scales:{
        x:{ticks:{color:'#505360',font:{size:10,family:'DM Mono'}},grid:{display:false}},
        y:{ticks:{callback:v=>'R$'+Math.round(v/1000)+'k',color:'#505360',font:{size:10,family:'DM Mono'}},grid:{color:'rgba(255,255,255,.05)'}}
      }
    }
  });
}

// ─── INVEST ────────────────────────────────────────────────────────────────────
function renderInvest(){
  const tbody = document.getElementById('bodyInvest');
  tbody.innerHTML = investimentos.length ? investimentos.map(v=>`
    <tr>
      <td><span class="badge badge-blue">${v.tipo}</span></td>
      <td style="font-weight:600">${v.ativo}</td>
      <td style="color:var(--blue);font-family:var(--mono);font-weight:500">${BRL(v.valor)}</td>
      <td style="color:var(--green);font-family:var(--mono)">${v.rent||'—'}</td>
      <td style="color:var(--muted)">${v.obj||'—'}</td>
    </tr>`).join('') :
    '<tr><td colspan="5" style="text-align:center;color:var(--muted);padding:20px">Nenhum investimento cadastrado</td></tr>';
  const total = investimentos.reduce((a,v)=>a+v.valor,0);
  document.getElementById('inv-total').textContent = BRL(total);
  document.getElementById('inv-count').textContent = investimentos.length;
  const last = investimentos[investimentos.length-1];
  document.getElementById('inv-obj').textContent = last ? last.obj||'—' : '—';
}

function addInvest(){
  const tipo = document.getElementById('inv-tipo').value;
  const ativo = document.getElementById('inv-ativo').value.trim();
  const valor = parseFloat(document.getElementById('inv-valor').value)||0;
  const rent = document.getElementById('inv-rent').value.trim();
  const obj = document.getElementById('inv-objetivo').value.trim();
  if(!ativo||!valor) return;
  investimentos.push({tipo,ativo,valor,rent,obj});
  ['inv-ativo','inv-valor','inv-rent','inv-objetivo'].forEach(id=>document.getElementById(id).value='');
  renderInvest();
}

// ─── CHARTS ──────────────────────────────────────────────────────────────────
function buildCharts(){
  const cats = {};
  despesas.forEach(d=>{ cats[d.cat]=(cats[d.cat]||0)+Number(d.valor); });
  const labels = Object.keys(cats);
  const vals = Object.values(cats);

  const cp = document.getElementById('chartPizza');
  if(window._cp) window._cp.destroy();
  window._cp = new Chart(cp,{
    type:'doughnut',
    data:{labels,datasets:[{data:vals,backgroundColor:COLORS.slice(0,labels.length),borderWidth:2,borderColor:'#13161b'}]},
    options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false}},cutout:'62%'}
  });

  const leg = document.getElementById('legendPizza');
  leg.innerHTML = labels.map((l,i)=>`<div class="legend-item"><div class="legend-dot" style="background:${COLORS[i%COLORS.length]}"></div>${l}</div>`).join('');

  const cb = document.getElementById('chartBarras');
  if(window._cb) window._cb.destroy();
  window._cb = new Chart(cb,{
    type:'bar',
    data:{labels,datasets:[{data:vals,backgroundColor:COLORS.slice(0,labels.length),borderRadius:4}]},
    options:{
      indexAxis:'y',responsive:true,maintainAspectRatio:false,
      plugins:{legend:{display:false}},
      scales:{
        x:{ticks:{callback:v=>'R$'+Math.round(v/1000)+'k',color:'#505360',font:{size:10,family:'DM Mono'}},grid:{color:'rgba(255,255,255,.05)'}},
        y:{ticks:{color:'#7a7d85',font:{size:10,family:'DM Mono'}},grid:{display:false}}
      }
    }
  });
}

// ─── RANKING ────────────────────────────────────────────────────────────────
function renderRanking(){
  const sorted = [...despesas].sort((a,b)=>b.valor-a.valor).slice(0,7);
  const max = sorted[0]?.valor||1;
  document.getElementById('rankingList').innerHTML = sorted.map((d,i)=>`
    <div class="rank-item">
      <span class="rank-num">#${i+1}</span>
      <span class="rank-name">${d.desc}</span>
      <div class="rank-bar"><div class="progress-bar"><div class="progress-fill" style="width:${Math.round((d.valor/max)*100)}%;background:var(--red)"></div></div></div>
      <span class="rank-val">${BRL(d.valor)}</span>
    </div>`).join('');
}

// ─── INIT ────────────────────────────────────────────────────────────────────
buildMesTabs();
renderMes();
renderFixas();
renderMetas();
renderRanking();
setTimeout(buildCharts, 150);
</script>
</body>
</html>
