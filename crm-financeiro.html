
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
    --bg:#0d0f12;--bg2:#13161b;--bg3:#1a1e26;--bg4:#20252f;
    --border:rgba(255,255,255,0.07);--border2:rgba(255,255,255,0.13);
    --text:#f0ede8;--muted:#7a7d85;--muted2:#505360;
    --green:#00e08e;--red:#ff4d4d;--blue:#3d8bff;
    --amber:#ffb347;--purple:#a78bfa;--teal:#00c5cc;
    --card-r:12px;--font:'Syne',sans-serif;--mono:'DM Mono',monospace;
  }
  *,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
  html,body{height:100%;background:var(--bg);color:var(--text);font-family:var(--font);font-size:14px;}
  .app{display:flex;height:100vh;overflow:hidden;}

  .sidebar{width:220px;min-width:220px;background:var(--bg2);border-right:1px solid var(--border);display:flex;flex-direction:column;}
  .sidebar-logo{padding:22px 20px 18px;border-bottom:1px solid var(--border);}
  .logo-tag{font-size:9px;font-family:var(--mono);color:var(--green);letter-spacing:.1em;text-transform:uppercase;margin-bottom:4px;}
  .sidebar-logo h1{font-size:16px;font-weight:800;line-height:1.1;}
  .sidebar-logo h1 span{color:var(--green);}
  .sidebar-nav{flex:1;padding:10px 0;overflow-y:auto;}
  .nav-sec{font-size:9px;font-family:var(--mono);color:var(--muted2);letter-spacing:.12em;text-transform:uppercase;padding:12px 20px 5px;}
  .nav-item{display:flex;align-items:center;gap:10px;padding:9px 20px;cursor:pointer;font-size:13px;font-weight:500;color:var(--muted);transition:all .14s;border-left:2px solid transparent;}
  .nav-item:hover{color:var(--text);background:rgba(255,255,255,.035);}
  .nav-item.active{color:var(--green);background:rgba(0,224,142,.06);border-left-color:var(--green);}
  .nav-item svg{width:15px;height:15px;opacity:.65;flex-shrink:0;}
  .nav-item.active svg{opacity:1;}
  .sidebar-foot{padding:14px 20px;border-top:1px solid var(--border);font-size:10px;font-family:var(--mono);color:var(--muted2);}
  .sidebar-foot span{color:var(--green);}

  .main{flex:1;display:flex;flex-direction:column;overflow:hidden;}
  .topbar{height:54px;background:var(--bg2);border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;padding:0 24px;flex-shrink:0;}
  .topbar-title{font-size:15px;font-weight:700;}
  .topbar-right{display:flex;align-items:center;gap:10px;}
  .topbar-badge{font-size:10px;font-family:var(--mono);background:rgba(0,224,142,.1);color:var(--green);border:1px solid rgba(0,224,142,.25);border-radius:4px;padding:3px 8px;}
  .topbar-date{font-size:10px;font-family:var(--mono);color:var(--muted);}
  .content{flex:1;overflow-y:auto;padding:22px;}
  .page{display:none;} .page.active{display:block;}

  .card{background:var(--bg2);border:1px solid var(--border);border-radius:var(--card-r);padding:16px 18px;}
  .card-title{font-size:10px;font-family:var(--mono);color:var(--muted);letter-spacing:.1em;text-transform:uppercase;margin-bottom:12px;}

  .kpi-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(148px,1fr));gap:10px;margin-bottom:18px;}
  .kpi{background:var(--bg2);border:1px solid var(--border);border-radius:var(--card-r);padding:14px 16px;position:relative;overflow:hidden;}
  .kpi::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:var(--kc,var(--border2));}
  .kpi.g{--kc:var(--green);} .kpi.r{--kc:var(--red);} .kpi.b{--kc:var(--blue);} .kpi.a{--kc:var(--amber);} .kpi.t{--kc:var(--teal);}
  .kpi-lbl{font-size:10px;font-family:var(--mono);color:var(--muted);text-transform:uppercase;letter-spacing:.07em;margin-bottom:7px;}
  .kpi-val{font-size:19px;font-weight:700;font-family:var(--mono);line-height:1;}
  .kpi.g .kpi-val{color:var(--green);} .kpi.r .kpi-val{color:var(--red);} .kpi.b .kpi-val{color:var(--blue);} .kpi.a .kpi-val{color:var(--amber);} .kpi.t .kpi-val{color:var(--teal);}
  .kpi-sub{font-size:10px;font-family:var(--mono);color:var(--muted);margin-top:4px;}

  .charts-row{display:grid;grid-template-columns:1fr 1fr;gap:14px;margin-bottom:18px;}
  @media(max-width:860px){.charts-row{grid-template-columns:1fr;}}

  .tw{overflow-x:auto;border-radius:var(--card-r);border:1px solid var(--border);}
  table{width:100%;border-collapse:collapse;font-size:12px;}
  thead th{background:var(--bg3);font-size:10px;font-family:var(--mono);color:var(--muted);text-transform:uppercase;letter-spacing:.07em;padding:9px 13px;text-align:left;white-space:nowrap;border-bottom:1px solid var(--border);}
  tbody td{padding:9px 13px;border-bottom:1px solid var(--border);color:var(--text);vertical-align:middle;}
  tbody tr:last-child td{border-bottom:none;}
  tbody tr:hover td{background:rgba(255,255,255,.02);}

  .badge{display:inline-block;padding:2px 7px;border-radius:4px;font-size:10px;font-family:var(--mono);font-weight:500;}
  .bg{background:rgba(0,224,142,.1);color:var(--green);border:1px solid rgba(0,224,142,.2);}
  .br{background:rgba(255,77,77,.1);color:var(--red);border:1px solid rgba(255,77,77,.2);}
  .bb{background:rgba(61,139,255,.1);color:var(--blue);border:1px solid rgba(61,139,255,.2);}
  .ba{background:rgba(255,179,71,.1);color:var(--amber);border:1px solid rgba(255,179,71,.2);}
  .bx{background:rgba(255,255,255,.05);color:var(--muted);border:1px solid var(--border);}
  .bt{background:rgba(0,197,204,.1);color:var(--teal);border:1px solid rgba(0,197,204,.2);}

  .form-row{display:flex;gap:7px;flex-wrap:wrap;margin-bottom:12px;}
  .form-row input,.form-row select{flex:1;min-width:90px;background:var(--bg3);border:1px solid var(--border2);border-radius:6px;padding:7px 9px;font-size:12px;font-family:var(--mono);color:var(--text);outline:none;transition:border-color .14s;}
  .form-row input:focus,.form-row select:focus{border-color:var(--green);}
  .form-row input::placeholder{color:var(--muted2);}
  .form-row select option{background:var(--bg3);}
  .btn-add{background:rgba(0,224,142,.11);color:var(--green);border:1px solid rgba(0,224,142,.28);border-radius:6px;padding:7px 14px;font-size:12px;font-family:var(--mono);font-weight:500;cursor:pointer;white-space:nowrap;transition:all .14s;}
  .btn-add:hover{background:rgba(0,224,142,.2);}
  .btn-del{background:rgba(255,77,77,.08);color:var(--red);border:1px solid rgba(255,77,77,.18);border-radius:4px;padding:3px 7px;font-size:10px;font-family:var(--mono);cursor:pointer;}
  .btn-del:hover{background:rgba(255,77,77,.18);}

  .sec-title{display:flex;align-items:center;gap:8px;margin:18px 0 11px;}
  .sec-title .line{flex:1;height:1px;background:var(--border);}
  .sec-title span{font-size:10px;font-family:var(--mono);color:var(--muted);text-transform:uppercase;letter-spacing:.1em;white-space:nowrap;}
  .sec-title .dot{width:6px;height:6px;border-radius:50%;flex-shrink:0;}

  .mes-tabs{display:flex;gap:4px;flex-wrap:wrap;margin-bottom:14px;}
  .mes-tab{padding:5px 9px;font-size:10px;font-family:var(--mono);border:1px solid var(--border);border-radius:4px;cursor:pointer;background:transparent;color:var(--muted);transition:all .12s;}
  .mes-tab:hover{color:var(--text);border-color:var(--border2);}
  .mes-tab.active{background:rgba(0,224,142,.09);color:var(--green);border-color:rgba(0,224,142,.35);}

  .pb{height:5px;border-radius:3px;background:var(--bg3);overflow:hidden;margin-top:4px;}
  .pf{height:100%;border-radius:3px;transition:width .4s cubic-bezier(.4,0,.2,1);}

  /* RECEITA MANAGER */
  .rec-manager{background:var(--bg3);border:1px solid rgba(0,224,142,.18);border-radius:var(--card-r);padding:16px 18px;margin-bottom:14px;}
  .rec-manager-top{display:flex;align-items:center;justify-content:space-between;margin-bottom:12px;flex-wrap:wrap;gap:8px;}
  .rec-manager-title{font-size:11px;font-family:var(--mono);color:var(--green);text-transform:uppercase;letter-spacing:.09em;display:flex;align-items:center;gap:7px;}
  .rec-manager-title::before{content:'';width:6px;height:6px;border-radius:50%;background:var(--green);display:inline-block;}
  .rec-form-grid{display:grid;grid-template-columns:2fr 1fr 1fr auto;gap:8px;align-items:end;}
  @media(max-width:700px){.rec-form-grid{grid-template-columns:1fr 1fr;}}
  .rec-field label{font-size:10px;font-family:var(--mono);color:var(--muted);margin-bottom:4px;display:block;text-transform:uppercase;letter-spacing:.07em;}
  .rec-field input,.rec-field select{width:100%;background:var(--bg4);border:1px solid var(--border2);border-radius:6px;padding:8px 10px;font-size:13px;font-family:var(--mono);color:var(--text);outline:none;transition:border-color .14s;}
  .rec-field input:focus,.rec-field select:focus{border-color:var(--green);}
  .rec-list{display:flex;flex-direction:column;gap:4px;margin-top:10px;}
  .rec-list-header{font-size:10px;font-family:var(--mono);color:var(--muted);text-transform:uppercase;letter-spacing:.08em;margin-bottom:4px;}
  .rec-item{display:flex;align-items:center;justify-content:space-between;padding:8px 11px;background:var(--bg4);border-radius:7px;border:1px solid var(--border);}
  .rec-item-info{font-size:12px;font-weight:600;}
  .rec-item-meta{font-size:10px;font-family:var(--mono);color:var(--muted);margin-top:2px;display:flex;gap:5px;}
  .rec-item-right{display:flex;align-items:center;gap:9px;}
  .rec-item-val{font-size:13px;font-family:var(--mono);font-weight:700;color:var(--green);}

  /* ECONOMIA */
  .eco-box{background:rgba(0,197,204,.04);border:1px solid rgba(0,197,204,.2);border-radius:var(--card-r);padding:16px 18px;margin-bottom:14px;}
  .eco-top{display:flex;align-items:center;justify-content:space-between;margin-bottom:14px;flex-wrap:wrap;gap:8px;}
  .eco-title{font-size:11px;font-family:var(--mono);color:var(--teal);text-transform:uppercase;letter-spacing:.09em;display:flex;align-items:center;gap:7px;}
  .eco-title::before{content:'';width:6px;height:6px;border-radius:50%;background:var(--teal);display:inline-block;}
  .eco-pct-wrap{display:flex;align-items:center;gap:7px;}
  .eco-pct-wrap span{font-size:10px;font-family:var(--mono);color:var(--muted);}
  .eco-pct-wrap input{width:52px;background:var(--bg4);border:1px solid var(--border2);border-radius:5px;padding:5px 7px;font-size:12px;font-family:var(--mono);color:var(--text);outline:none;text-align:center;}
  .eco-pct-wrap input:focus{border-color:var(--teal);}
  .eco-nums{display:grid;grid-template-columns:repeat(4,1fr);gap:9px;margin-bottom:14px;}
  @media(max-width:700px){.eco-nums{grid-template-columns:1fr 1fr;}}
  .eco-num{background:rgba(0,0,0,.22);border:1px solid rgba(255,255,255,.05);border-radius:8px;padding:11px 13px;}
  .eco-num-lbl{font-size:9px;font-family:var(--mono);color:var(--muted);text-transform:uppercase;letter-spacing:.08em;margin-bottom:5px;}
  .eco-num-val{font-size:16px;font-weight:700;font-family:var(--mono);}
  .eco-num-sub{font-size:10px;font-family:var(--mono);color:var(--muted);margin-top:3px;}
  .eco-destinos{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;}
  @media(max-width:660px){.eco-destinos{grid-template-columns:1fr;}}
  .eco-dest{background:rgba(0,0,0,.18);border:1px solid rgba(255,255,255,.06);border-radius:8px;padding:12px 14px;}
  .eco-dest-lbl{font-size:10px;font-family:var(--mono);margin-bottom:6px;display:flex;align-items:center;gap:6px;}
  .eco-dest-val{font-size:15px;font-weight:700;font-family:var(--mono);}
  .eco-dest-desc{font-size:10px;color:var(--muted);margin-top:3px;font-family:var(--mono);}

  /* RESUMO */
  .resumo{background:var(--bg3);border:1px solid var(--border);border-radius:var(--card-r);padding:14px 16px;margin-bottom:14px;}
  .resumo-tag{font-size:9px;font-family:var(--mono);color:var(--green);letter-spacing:.12em;text-transform:uppercase;margin-bottom:10px;}
  .resumo-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:10px;}
  @media(max-width:700px){.resumo-grid{grid-template-columns:1fr 1fr;}}
  .ri-lbl{font-size:10px;font-family:var(--mono);color:var(--muted);margin-bottom:2px;}
  .ri-val{font-size:16px;font-weight:700;font-family:var(--mono);}
  .resumo-ins{margin-top:10px;padding-top:10px;border-top:1px solid var(--border);font-size:11px;font-family:var(--mono);color:var(--muted);display:flex;flex-direction:column;gap:4px;}

  .meta-item{padding:13px 0;border-bottom:1px solid var(--border);}
  .meta-item:last-child{border-bottom:none;}
  .meta-header{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:7px;}
  .meta-name{font-size:13px;font-weight:600;}
  .meta-foot{display:flex;align-items:center;gap:10px;}
  .meta-pct{font-size:13px;font-weight:700;font-family:var(--mono);}

  .rank-item{display:flex;align-items:center;gap:10px;padding:8px 0;border-bottom:1px solid var(--border);}
  .rank-item:last-child{border-bottom:none;}
  .rank-n{font-size:11px;font-family:var(--mono);color:var(--muted2);min-width:18px;}
  .rank-name{flex:1;font-size:12px;}
  .rank-bar{width:90px;}
  .rank-val{font-size:12px;font-family:var(--mono);color:var(--red);min-width:76px;text-align:right;font-weight:500;}

  .legend{display:flex;flex-wrap:wrap;gap:10px;margin-top:9px;}
  .legend-item{display:flex;align-items:center;gap:4px;font-size:11px;font-family:var(--mono);color:var(--muted);}
  .legend-dot{width:9px;height:9px;border-radius:2px;flex-shrink:0;}

  ::-webkit-scrollbar{width:5px;height:5px;}
  ::-webkit-scrollbar-track{background:var(--bg);}
  ::-webkit-scrollbar-thumb{background:var(--bg3);border-radius:3px;}

  @media(max-width:680px){
    .sidebar{width:54px;min-width:54px;}
    .sidebar-logo h1,.sidebar-logo .logo-tag,.nav-item span,.nav-sec,.sidebar-foot{display:none;}
    .nav-item{justify-content:center;padding:11px;}
    .content{padding:14px;}
  }
</style>
</head>
<body>
<div class="app">

<aside class="sidebar">
  <div class="sidebar-logo">
    <div class="logo-tag">CRM / v1.1</div>
    <h1>Finance<span>OS</span></h1>
  </div>
  <nav class="sidebar-nav">
    <div class="nav-sec">Principal</div>
    <div class="nav-item active" onclick="showPage('dashboard',this)">
      <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="1" y="1" width="6" height="6" rx="1"/><rect x="9" y="1" width="6" height="6" rx="1"/><rect x="1" y="9" width="6" height="6" rx="1"/><rect x="9" y="9" width="6" height="6" rx="1"/></svg>
      <span>Dashboard</span>
    </div>
    <div class="nav-item" onclick="showPage('mes',this)">
      <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="1" y="2" width="14" height="13" rx="1.5"/><path d="M5 1v2M11 1v2M1 6h14"/></svg>
      <span>Por Mês</span>
    </div>
    <div class="nav-item" onclick="showPage('anual',this)">
      <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M2 12l4-4 3 2 5-6"/><circle cx="2" cy="12" r="1.2" fill="currentColor"/><circle cx="6" cy="8" r="1.2" fill="currentColor"/><circle cx="9" cy="10" r="1.2" fill="currentColor"/><circle cx="14" cy="4" r="1.2" fill="currentColor"/></svg>
      <span>Consolidado Anual</span>
    </div>
    <div class="nav-sec">Gestão</div>
    <div class="nav-item" onclick="showPage('metas',this)">
      <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="8" cy="8" r="6"/><circle cx="8" cy="8" r="3"/><path d="M8 1v2M8 13v2M1 8h2M13 8h2"/></svg>
      <span>Metas</span>
    </div>
    <div class="nav-item" onclick="showPage('fixas',this)">
      <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="1" y="3" width="14" height="11" rx="1.5"/><path d="M1 7h14M5 10h2M5 12h4"/></svg>
      <span>Contas Fixas</span>
    </div>
    <div class="nav-item" onclick="showPage('invest',this)">
      <svg viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M2 14l3-4 3 1 3-5 3 2"/><path d="M11 3h3v3"/></svg>
      <span>Investimentos</span>
    </div>
  </nav>
  <div class="sidebar-foot">versão <span>1.1</span> · 2025</div>
</aside>

<main class="main">
  <div class="topbar">
    <div class="topbar-title" id="pageTitle">Dashboard</div>
    <div class="topbar-right">
      <span class="topbar-badge" id="todayBadge"></span>
      <span class="topbar-date" id="nowTime"></span>
    </div>
  </div>
  <div class="content">

    <!-- DASHBOARD -->
    <div class="page active" id="page-dashboard">
      <div class="kpi-grid">
        <div class="kpi g"><div class="kpi-lbl">Receita do mês</div><div class="kpi-val" id="kpi-receita">R$ 20.000</div><div class="kpi-sub">mês selecionado</div></div>
        <div class="kpi r"><div class="kpi-lbl">Total de gastos</div><div class="kpi-val" id="kpi-gastos">R$ 22.318</div><div class="kpi-sub">fixos + variáveis</div></div>
        <div class="kpi b"><div class="kpi-lbl">Saldo líquido</div><div class="kpi-val" id="kpi-lucro">-R$ 2.318</div><div class="kpi-sub">receita − gastos</div></div>
        <div class="kpi t"><div class="kpi-lbl">Meta de economia</div><div class="kpi-val" id="kpi-eco">R$ 4.000</div><div class="kpi-sub" id="kpi-eco-sub">20% da receita</div></div>
        <div class="kpi a"><div class="kpi-lbl">Cartão de crédito</div><div class="kpi-val">R$ 10.000</div><div class="kpi-sub">variável mensal</div></div>
      </div>
      <div class="charts-row">
        <div class="card">
          <div class="card-title">Distribuição de gastos</div>
          <div style="position:relative;height:195px"><canvas id="chartPizza" role="img" aria-label="Gastos por categoria">Gastos.</canvas></div>
          <div class="legend" id="legendPizza"></div>
        </div>
        <div class="card">
          <div class="card-title">Gastos por categoria</div>
          <div style="position:relative;height:195px"><canvas id="chartBarras" role="img" aria-label="Barras de gastos">Gastos.</canvas></div>
        </div>
      </div>
      <div class="card">
        <div class="card-title">Ranking — maiores despesas</div>
        <div id="rankingList"></div>
      </div>
    </div>

    <!-- POR MÊS -->
    <div class="page" id="page-mes">
      <div class="mes-tabs" id="mesTabs"></div>

      <!-- RECEITA MANAGER -->
      <div class="rec-manager">
        <div class="rec-manager-top">
          <div class="rec-manager-title">Receita — <span id="rm-mes-lbl" style="color:var(--text);font-weight:700;margin-left:4px"></span></div>
          <div style="display:flex;align-items:center;gap:8px">
            <span style="font-size:10px;font-family:var(--mono);color:var(--muted)">Total do mês:</span>
            <span style="font-size:15px;font-weight:700;font-family:var(--mono);color:var(--green)" id="rm-total">R$ 20.000</span>
          </div>
        </div>
        <div class="rec-form-grid">
          <div class="rec-field">
            <label>Fonte / Cliente</label>
            <input type="text" id="rm-fonte" placeholder="ex: Projeto XYZ, Salário, Freelance"/>
          </div>
          <div class="rec-field">
            <label>Valor R$</label>
            <input type="number" id="rm-valor" placeholder="20000"/>
          </div>
          <div class="rec-field">
            <label>Recorrente?</label>
            <select id="rm-recorrente">
              <option value="nao">Só este mês</option>
              <option value="sim">Todos os meses</option>
            </select>
          </div>
          <div style="padding-bottom:1px">
            <button class="btn-add" onclick="addReceitaMes()">+ Lançar</button>
          </div>
        </div>
        <div class="rec-list">
          <div class="rec-list-header">Entradas lançadas</div>
          <div id="recMesList"></div>
        </div>
      </div>

      <!-- ECONOMIA -->
      <div class="eco-box">
        <div class="eco-top">
          <div class="eco-title">Plano de economia do mês</div>
          <div class="eco-pct-wrap">
            <span>Meta de poupar:</span>
            <input type="number" id="eco-pct" value="20" min="0" max="100" oninput="renderEco()"/>
            <span>% da receita</span>
          </div>
        </div>
        <div class="eco-nums">
          <div class="eco-num">
            <div class="eco-num-lbl">Receita total</div>
            <div class="eco-num-val" id="eco-receita" style="color:var(--green)">—</div>
            <div class="eco-num-sub">entradas do mês</div>
          </div>
          <div class="eco-num">
            <div class="eco-num-lbl">Gastos totais</div>
            <div class="eco-num-val" id="eco-gastos" style="color:var(--red)">—</div>
            <div class="eco-num-sub">despesas lançadas</div>
          </div>
          <div class="eco-num">
            <div class="eco-num-lbl">Saldo livre</div>
            <div class="eco-num-val" id="eco-saldo">—</div>
            <div class="eco-num-sub">receita − gastos</div>
          </div>
          <div class="eco-num" style="border:1px solid rgba(0,197,204,.25)">
            <div class="eco-num-lbl">Poupar este mês</div>
            <div class="eco-num-val" id="eco-meta" style="color:var(--teal)">—</div>
            <div class="eco-num-sub" id="eco-meta-sub">— da receita</div>
          </div>
        </div>
        <div style="font-size:10px;font-family:var(--mono);color:var(--muted);text-transform:uppercase;letter-spacing:.08em;margin-bottom:8px;">Como distribuir a economia (regra 50/30/20)</div>
        <div class="eco-destinos">
          <div class="eco-dest">
            <div class="eco-dest-lbl" style="color:var(--blue)">
              <span style="width:7px;height:7px;border-radius:50%;background:var(--blue);display:inline-block"></span>
              Reserva de emergência
            </div>
            <div class="eco-dest-val" id="eco-d1" style="color:var(--blue)">—</div>
            <div class="eco-dest-desc">50% · objetivo: 6x seus custos fixos</div>
            <div class="pb" style="margin-top:8px"><div class="pf" id="eco-d1-bar" style="background:var(--blue);width:0%"></div></div>
          </div>
          <div class="eco-dest">
            <div class="eco-dest-lbl" style="color:var(--purple)">
              <span style="width:7px;height:7px;border-radius:50%;background:var(--purple);display:inline-block"></span>
              Investimentos
            </div>
            <div class="eco-dest-val" id="eco-d2" style="color:var(--purple)">—</div>
            <div class="eco-dest-desc">30% · CDB, FIIs, ações ou tesouro</div>
            <div class="pb" style="margin-top:8px"><div class="pf" id="eco-d2-bar" style="background:var(--purple);width:0%"></div></div>
          </div>
          <div class="eco-dest">
            <div class="eco-dest-lbl" style="color:var(--amber)">
              <span style="width:7px;height:7px;border-radius:50%;background:var(--amber);display:inline-block"></span>
              Objetivos pessoais
            </div>
            <div class="eco-dest-val" id="eco-d3" style="color:var(--amber)">—</div>
            <div class="eco-dest-desc">20% · viagem, carro, quitação</div>
            <div class="pb" style="margin-top:8px"><div class="pf" id="eco-d3-bar" style="background:var(--amber);width:0%"></div></div>
          </div>
        </div>
      </div>

      <!-- RESUMO -->
      <div class="resumo">
        <div class="resumo-tag">resumo rápido — <span id="resumo-mes-lbl" style="color:var(--text)"></span></div>
        <div class="resumo-grid">
          <div><div class="ri-lbl">Receita</div><div class="ri-val" id="mes-rec" style="color:var(--green)">—</div></div>
          <div><div class="ri-lbl">Despesas</div><div class="ri-val" id="mes-desp" style="color:var(--red)">—</div></div>
          <div><div class="ri-lbl">Saldo</div><div class="ri-val" id="mes-lucro">—</div></div>
          <div><div class="ri-lbl">% saldo</div><div class="ri-val" id="mes-pct">—</div></div>
        </div>
        <div class="resumo-ins">
          <div>Gastei mais com: <span style="color:var(--text)" id="ins-gasto">—</span></div>
          <div>Melhor fonte: <span style="color:var(--text)" id="ins-fonte">—</span></div>
          <div>Preciso melhorar: <span style="color:var(--amber)" id="ins-melhora">—</span></div>
        </div>
      </div>

      <!-- DESPESAS -->
      <div class="sec-title"><span class="dot" style="background:var(--red)"></span><span>Despesas do mês</span><div class="line"></div></div>
      <div class="form-row">
        <input type="date" id="desp-data"/>
        <select id="desp-tipo"><option>Fixo</option><option>Variável</option></select>
        <select id="desp-cat"><option>Moradia</option><option>Educação</option><option>Saúde</option><option>Transporte</option><option>Dívida</option><option>Seguro</option><option>Cartão</option><option>Lazer</option><option>Alimentação</option><option>Outro</option></select>
        <input type="text" id="desp-desc" placeholder="Descrição"/>
        <input type="number" id="desp-valor" placeholder="Valor R$"/>
        <button class="btn-add" onclick="addDespesa()">+ Adicionar</button>
      </div>
      <div class="tw">
        <table><thead><tr><th>Data</th><th>Tipo</th><th>Categoria</th><th>Descrição</th><th>Valor</th><th>Impacto</th><th></th></tr></thead>
        <tbody id="bodyDespesas"></tbody></table>
      </div>
    </div>

    <!-- CONSOLIDADO ANUAL -->
    <div class="page" id="page-anual">
      <div class="card" style="margin-bottom:14px">
        <div class="card-title">Evolução — receita vs despesas</div>
        <div style="position:relative;height:210px"><canvas id="chartAnual" role="img" aria-label="Anual">Dados.</canvas></div>
      </div>
      <div class="tw">
        <table><thead><tr><th>Mês</th><th>Receita</th><th>Despesas</th><th>Saldo</th><th>% Saldo</th><th>Economia</th><th>Status</th></tr></thead>
        <tbody id="bodyAnual"></tbody></table>
      </div>
    </div>

    <!-- METAS -->
    <div class="page" id="page-metas">
      <div class="card">
        <div class="form-row">
          <input type="text" id="meta-nome" placeholder="Descrição da meta" style="flex:2"/>
          <input type="number" id="meta-valor" placeholder="Valor alvo R$"/>
          <input type="number" id="meta-atual" placeholder="Valor atual R$"/>
          <input type="text" id="meta-prazo" placeholder="Prazo ex: Dez/2026"/>
          <select id="meta-tipo"><option>Financeira</option><option>Investimento</option><option>Quitar dívida</option><option>Economia</option></select>
          <button class="btn-add" onclick="addMeta()">+ Meta</button>
        </div>
        <div id="listaMetas"></div>
      </div>
    </div>

    <!-- CONTAS FIXAS -->
    <div class="page" id="page-fixas">
      <div class="tw">
        <table><thead><tr><th>Conta</th><th>Valor</th><th>Vencimento</th><th>Tipo</th><th>Status</th><th>Obs</th></tr></thead>
        <tbody id="bodyFixas"></tbody></table>
      </div>
    </div>

    <!-- INVESTIMENTOS -->
    <div class="page" id="page-invest">
      <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-bottom:14px">
        <div class="kpi b"><div class="kpi-lbl">Total investido</div><div class="kpi-val" id="inv-total">R$ 0</div></div>
        <div class="kpi g"><div class="kpi-lbl">Ativos</div><div class="kpi-val" id="inv-count">0</div></div>
        <div class="kpi a"><div class="kpi-lbl">Último objetivo</div><div class="kpi-val" style="font-size:14px" id="inv-obj">—</div></div>
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
        <div class="tw">
          <table><thead><tr><th>Tipo</th><th>Ativo</th><th>Valor</th><th>Rentabilidade</th><th>Objetivo</th></tr></thead>
          <tbody id="bodyInvest"></tbody></table>
        </div>
      </div>
    </div>

  </div>
</main>
</div>

<script>
const MESES=['Jan/2025','Fev/2025','Mar/2025','Abr/2025','Mai/2025','Jun/2025','Jul/2025','Ago/2025','Set/2025','Out/2025','Nov/2025','Dez/2025','Jan/2026','Fev/2026','Mar/2026','Abr/2026','Mai/2026','Jun/2026','Jul/2026','Ago/2026','Set/2026','Out/2026','Nov/2026','Dez/2026'];

// Receitas por mês — pré-carregado com R$20k recorrente
let receitasPorMes={};
MESES.forEach((_,i)=>{receitasPorMes[i]=[{fonte:'Renda mensal base',valor:20000,status:'Recebido',recorrente:true}];});

let despesasPorMes={};
despesasPorMes[3]=[
  {data:'2025-04-01',tipo:'Fixo',cat:'Moradia',desc:'Parcela Apartamento',valor:7000,impacto:'Alto'},
  {data:'2025-04-05',tipo:'Fixo',cat:'Educação',desc:'Escola Malu',valor:2500,impacto:'Alto'},
  {data:'2025-04-01',tipo:'Fixo',cat:'Saúde',desc:'Seguro Saúde',valor:2500,impacto:'Alto'},
  {data:'2025-04-15',tipo:'Fixo',cat:'Transporte',desc:'Parcela Carro 1',valor:3000,impacto:'Alto'},
  {data:'2025-04-20',tipo:'Fixo',cat:'Transporte',desc:'Parcela Carro 2',valor:3600,impacto:'Alto'},
  {data:'2025-04-01',tipo:'Fixo',cat:'Moradia',desc:'IPTU',valor:791,impacto:'Médio'},
  {data:'2025-04-10',tipo:'Fixo',cat:'Moradia',desc:'Conta Luz',valor:400,impacto:'Médio'},
  {data:'2025-04-12',tipo:'Fixo',cat:'Moradia',desc:'Internet',valor:400,impacto:'Médio'},
  {data:'2025-04-01',tipo:'Fixo',cat:'Dívida',desc:'Nubank 78',valor:78,impacto:'Baixo'},
  {data:'2025-04-01',tipo:'Fixo',cat:'Seguro',desc:'Seguro Vida Nubank',valor:47,impacto:'Baixo'},
  {data:'2025-04-30',tipo:'Variável',cat:'Cartão',desc:'Cartão de Crédito',valor:10000,impacto:'Alto'},
];

const FIXAS=[
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

let metas=[
  {nome:'Faturar R$ 20k/mês',valor:20000,atual:20000,prazo:'Mensal',tipo:'Financeira'},
  {nome:'Quitar Nubank R$ 78',valor:78,atual:78,prazo:'Set/2026',tipo:'Quitar dívida'},
  {nome:'Investir 20% da renda',valor:4000,atual:0,prazo:'Contínuo',tipo:'Investimento'},
  {nome:'Reserva emergência 6 meses',valor:133908,atual:0,prazo:'Dez/2026',tipo:'Economia'},
];
let investimentos=[];
let mesSel=3;

const BRL=v=>'R$ '+Math.round(Number(v||0)).toLocaleString('pt-BR');
const COLORS=['#ff4d4d','#3d8bff','#00e08e','#ffb347','#a78bfa','#00c5cc','#ff6b9d'];

const getRecs=i=>receitasPorMes[i]||[];
const getDesps=i=>despesasPorMes[i]||[];
const sumRec=i=>getRecs(i).reduce((a,r)=>a+Number(r.valor),0);
const sumDesp=i=>getDesps(i).reduce((a,d)=>a+Number(d.valor),0);

// Clock
function clock(){
  const n=new Date();
  document.getElementById('nowTime').textContent=n.toLocaleTimeString('pt-BR',{hour:'2-digit',minute:'2-digit'});
  document.getElementById('todayBadge').textContent=n.toLocaleDateString('pt-BR',{day:'2-digit',month:'short',year:'numeric'});
}
clock();setInterval(clock,30000);

// Nav
const TITLES={dashboard:'Dashboard',mes:'Por Mês',anual:'Consolidado Anual',metas:'Metas',fixas:'Contas Fixas',invest:'Investimentos'};
function showPage(id,el){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.nav-item').forEach(n=>n.classList.remove('active'));
  document.getElementById('page-'+id).classList.add('active');
  if(el)el.classList.add('active');
  document.getElementById('pageTitle').textContent=TITLES[id]||id;
  if(id==='anual')renderAnual();
  if(id==='invest')renderInvest();
}

// Mes tabs
function buildMesTabs(){
  const c=document.getElementById('mesTabs');c.innerHTML='';
  MESES.forEach((m,i)=>{
    const b=document.createElement('button');
    b.className='mes-tab'+(i===mesSel?' active':'');
    b.textContent=m;
    b.onclick=()=>{mesSel=i;buildMesTabs();renderMes();};
    c.appendChild(b);
  });
}

// RENDER MÊS
function renderMes(){
  const mes=MESES[mesSel];
  document.getElementById('rm-mes-lbl').textContent=mes;
  document.getElementById('resumo-mes-lbl').textContent=mes;

  // Receita list
  const recs=getRecs(mesSel);
  const rl=document.getElementById('recMesList');
  if(!recs.length){
    rl.innerHTML='<div style="font-size:11px;font-family:var(--mono);color:var(--muted);padding:6px 0">Nenhuma receita lançada</div>';
  } else {
    rl.innerHTML=recs.map((r,i)=>`
      <div class="rec-item">
        <div>
          <div class="rec-item-info">${r.fonte}</div>
          <div class="rec-item-meta">
            <span class="badge ${r.status==='Recebido'?'bg':r.status==='A receber'?'bb':'ba'}">${r.status}</span>
            ${r.recorrente?'<span class="badge bt">recorrente</span>':''}
          </div>
        </div>
        <div class="rec-item-right">
          <span class="rec-item-val">${BRL(r.valor)}</span>
          <button class="btn-del" onclick="delReceita(${mesSel},${i})">remover</button>
        </div>
      </div>`).join('');
  }
  document.getElementById('rm-total').textContent=BRL(sumRec(mesSel));

  // Despesas table
  const desps=getDesps(mesSel);
  const tb=document.getElementById('bodyDespesas');
  if(!desps.length){
    tb.innerHTML='<tr><td colspan="7" style="text-align:center;color:var(--muted);padding:18px">Nenhuma despesa — adicione acima</td></tr>';
  } else {
    tb.innerHTML=desps.map((d,i)=>`
      <tr>
        <td style="font-family:var(--mono);font-size:11px;color:var(--muted)">${d.data}</td>
        <td><span class="badge ${d.tipo==='Fixo'?'bb':'ba'}">${d.tipo}</span></td>
        <td><span class="badge bx">${d.cat}</span></td>
        <td style="font-weight:500">${d.desc}</td>
        <td style="color:var(--red);font-family:var(--mono);font-weight:500">${BRL(d.valor)}</td>
        <td><span class="badge ${d.impacto==='Alto'?'br':d.impacto==='Médio'?'ba':'bx'}">${d.impacto}</span></td>
        <td><button class="btn-del" onclick="delDespesa(${mesSel},${i})">×</button></td>
      </tr>`).join('');
  }

  updateResumo();
  renderEco();
  updateDashboard();
}

function updateResumo(){
  const tr=sumRec(mesSel),td=sumDesp(mesSel),saldo=tr-td;
  const pct=tr>0?((saldo/tr)*100).toFixed(1):null;
  document.getElementById('mes-rec').textContent=BRL(tr);
  document.getElementById('mes-desp').textContent=BRL(td);
  const el=document.getElementById('mes-lucro');
  el.textContent=BRL(saldo);
  el.style.color=saldo>=0?'var(--green)':'var(--red)';
  document.getElementById('mes-pct').textContent=pct!==null?pct+'%':'—';

  const desps=getDesps(mesSel);
  const maior=desps.length?[...desps].sort((a,b)=>b.valor-a.valor)[0]:null;
  document.getElementById('ins-gasto').textContent=maior?maior.desc:'—';
  const recs=getRecs(mesSel);
  const melhor=recs.length?[...recs].sort((a,b)=>b.valor-a.valor)[0]:null;
  document.getElementById('ins-fonte').textContent=melhor?melhor.fonte:'— lance receitas';

  const ecoPct=parseFloat(document.getElementById('eco-pct').value)||20;
  const metaEco=tr*ecoPct/100;
  document.getElementById('ins-melhora').textContent=saldo<metaEco
    ?'Reduzir '+BRL(metaEco-saldo)+' nos gastos para atingir economia'
    :'Meta de economia atingida — sobram '+BRL(saldo-metaEco);
}

function renderEco(){
  const tr=sumRec(mesSel),td=sumDesp(mesSel),saldo=tr-td;
  const pct=parseFloat(document.getElementById('eco-pct').value)||20;
  const meta=Math.round(tr*pct/100);

  document.getElementById('eco-receita').textContent=BRL(tr);
  document.getElementById('eco-gastos').textContent=BRL(td);
  const se=document.getElementById('eco-saldo');
  se.textContent=BRL(saldo);
  se.style.color=saldo>=0?'var(--green)':'var(--red)';
  document.getElementById('eco-meta').textContent=BRL(meta);
  document.getElementById('eco-meta-sub').textContent=pct+'% da receita';

  const d1=Math.round(meta*.5),d2=Math.round(meta*.3),d3=Math.round(meta*.2);
  document.getElementById('eco-d1').textContent=BRL(d1);
  document.getElementById('eco-d2').textContent=BRL(d2);
  document.getElementById('eco-d3').textContent=BRL(d3);

  const base=Math.max(saldo,meta,1);
  document.getElementById('eco-d1-bar').style.width=Math.min(100,Math.round(d1/base*100))+'%';
  document.getElementById('eco-d2-bar').style.width=Math.min(100,Math.round(d2/base*100))+'%';
  document.getElementById('eco-d3-bar').style.width=Math.min(100,Math.round(d3/base*100))+'%';

  document.getElementById('kpi-eco').textContent=BRL(meta);
  document.getElementById('kpi-eco-sub').textContent=pct+'% da receita';
}

// Receita actions
function addReceitaMes(){
  const fonte=document.getElementById('rm-fonte').value.trim();
  const valor=parseFloat(document.getElementById('rm-valor').value)||0;
  const recorrente=document.getElementById('rm-recorrente').value==='sim';
  if(!fonte||!valor){alert('Preencha fonte e valor.');return;}
  const entrada={fonte,valor,status:'Recebido',recorrente};
  if(recorrente){
    for(let i=mesSel;i<MESES.length;i++){
      if(!receitasPorMes[i])receitasPorMes[i]=[];
      receitasPorMes[i].push({...entrada});
    }
  } else {
    if(!receitasPorMes[mesSel])receitasPorMes[mesSel]=[];
    receitasPorMes[mesSel].push(entrada);
  }
  document.getElementById('rm-fonte').value='';
  document.getElementById('rm-valor').value='';
  renderMes();
}

function delReceita(mesIdx,idx){
  const rec=receitasPorMes[mesIdx]&&receitasPorMes[mesIdx][idx];
  if(!rec)return;
  if(rec.recorrente&&confirm('Receita recorrente. Remover de todos os meses futuros?')){
    for(let i=mesIdx;i<MESES.length;i++){
      receitasPorMes[i]=(receitasPorMes[i]||[]).filter(r=>!(r.fonte===rec.fonte&&r.valor===rec.valor&&r.recorrente));
    }
  } else {
    receitasPorMes[mesIdx].splice(idx,1);
  }
  renderMes();
}

// Despesa actions
function addDespesa(){
  const data=document.getElementById('desp-data').value||new Date().toISOString().split('T')[0];
  const tipo=document.getElementById('desp-tipo').value;
  const cat=document.getElementById('desp-cat').value;
  const desc=document.getElementById('desp-desc').value.trim();
  const valor=parseFloat(document.getElementById('desp-valor').value)||0;
  if(!desc||!valor){alert('Preencha descrição e valor.');return;}
  if(!despesasPorMes[mesSel])despesasPorMes[mesSel]=[];
  despesasPorMes[mesSel].push({data,tipo,cat,desc,valor,impacto:'Médio'});
  document.getElementById('desp-desc').value='';
  document.getElementById('desp-valor').value='';
  renderMes();buildCharts();renderRanking();
}

function delDespesa(mesIdx,idx){
  if(despesasPorMes[mesIdx])despesasPorMes[mesIdx].splice(idx,1);
  renderMes();buildCharts();renderRanking();
}

// Dashboard
function updateDashboard(){
  const tr=sumRec(mesSel),td=sumDesp(mesSel),saldo=tr-td;
  document.getElementById('kpi-receita').textContent=BRL(tr);
  document.getElementById('kpi-gastos').textContent=BRL(td);
  const el=document.getElementById('kpi-lucro');
  el.textContent=BRL(saldo);
  el.style.color=saldo>=0?'var(--green)':'var(--red)';
}

// Contas fixas
function renderFixas(){
  document.getElementById('bodyFixas').innerHTML=FIXAS.map(f=>`
    <tr>
      <td style="font-weight:600">${f.conta}</td>
      <td style="font-family:var(--mono);color:${f.valor>0?'var(--red)':'var(--muted)'}">${f.valor>0?BRL(f.valor):'A confirmar'}</td>
      <td style="font-family:var(--mono);font-size:11px;color:var(--muted)">${f.venc}</td>
      <td><span class="badge bx">${f.tipo}</span></td>
      <td><span class="badge ${f.status==='Ativo'?'bg':'ba'}">${f.status}</span></td>
      <td style="color:var(--muted);font-size:11px">${f.obs}</td>
    </tr>`).join('');
}

// Metas
function renderMetas(){
  document.getElementById('listaMetas').innerHTML=metas.map((m,i)=>{
    const p=m.valor>0?Math.min(100,Math.round(m.atual/m.valor*100)):0;
    const c=p>=100?'var(--green)':p>=50?'var(--amber)':'var(--red)';
    return `<div class="meta-item">
      <div class="meta-header">
        <span class="meta-name">${m.nome}</span>
        <div style="display:flex;gap:5px;align-items:center">
          <span class="badge bx">${m.tipo}</span>
          <span style="font-size:10px;font-family:var(--mono);color:var(--muted)">${m.prazo}</span>
        </div>
      </div>
      <div class="meta-foot">
        <div class="pb" style="flex:1"><div class="pf" style="width:${p}%;background:${c}"></div></div>
        <span class="meta-pct" style="color:${c}">${p}%</span>
        <span style="font-size:10px;font-family:var(--mono);color:var(--muted)">${BRL(m.atual)} / ${m.valor>0?BRL(m.valor):'a definir'}</span>
      </div>
    </div>`;
  }).join('');
}

function addMeta(){
  const nome=document.getElementById('meta-nome').value.trim();
  const valor=parseFloat(document.getElementById('meta-valor').value)||0;
  const atual=parseFloat(document.getElementById('meta-atual').value)||0;
  const prazo=document.getElementById('meta-prazo').value||'—';
  const tipo=document.getElementById('meta-tipo').value;
  if(!nome)return;
  metas.push({nome,valor,atual,prazo,tipo});
  ['meta-nome','meta-valor','meta-atual','meta-prazo'].forEach(id=>document.getElementById(id).value='');
  renderMetas();
}

// Anual
function renderAnual(){
  const ecoPct=parseFloat(document.getElementById('eco-pct').value)||20;
  const dados=MESES.map((mes,i)=>{
    const rec=sumRec(i);
    const desp=despesasPorMes[i]?despesasPorMes[i].reduce((a,d)=>a+d.valor,0):22318;
    return{mes,rec,desp};
  });
  document.getElementById('bodyAnual').innerHTML=dados.map(d=>{
    const saldo=d.rec-d.desp;
    const pct=d.rec>0?((saldo/d.rec)*100).toFixed(1)+'%':'—';
    const eco=d.rec>0?BRL(d.rec*ecoPct/100):'—';
    const cor=saldo>=0?'var(--green)':'var(--red)';
    return`<tr>
      <td style="font-weight:600">${d.mes}</td>
      <td style="color:var(--green);font-family:var(--mono)">${d.rec>0?BRL(d.rec):'—'}</td>
      <td style="color:var(--red);font-family:var(--mono)">${BRL(d.desp)}</td>
      <td style="color:${cor};font-family:var(--mono);font-weight:500">${BRL(saldo)}</td>
      <td style="font-family:var(--mono);color:var(--muted)">${pct}</td>
      <td style="font-family:var(--mono);color:var(--teal)">${eco}</td>
      <td><span class="badge ${saldo>=0?'bg':'br'}">${saldo>=0?'Positivo':'Negativo'}</span></td>
    </tr>`;
  }).join('');

  const c=document.getElementById('chartAnual');
  if(window._ca)window._ca.destroy();
  const recent=dados.slice(0,8);
  window._ca=new Chart(c,{type:'bar',
    data:{labels:recent.map(d=>d.mes),datasets:[
      {label:'Receita',data:recent.map(d=>d.rec),backgroundColor:'rgba(0,224,142,.65)',borderRadius:4},
      {label:'Despesas',data:recent.map(d=>d.desp),backgroundColor:'rgba(255,77,77,.65)',borderRadius:4}
    ]},
    options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false}},
      scales:{x:{ticks:{color:'#505360',font:{size:10,family:'DM Mono'}},grid:{display:false}},
              y:{ticks:{callback:v=>'R$'+Math.round(v/1000)+'k',color:'#505360',font:{size:10,family:'DM Mono'}},grid:{color:'rgba(255,255,255,.04)'}}}}
  });
}

// Investimentos
function renderInvest(){
  const tb=document.getElementById('bodyInvest');
  tb.innerHTML=investimentos.length?investimentos.map(v=>`
    <tr>
      <td><span class="badge bb">${v.tipo}</span></td>
      <td style="font-weight:600">${v.ativo}</td>
      <td style="color:var(--blue);font-family:var(--mono);font-weight:500">${BRL(v.valor)}</td>
      <td style="color:var(--green);font-family:var(--mono)">${v.rent||'—'}</td>
      <td style="color:var(--muted)">${v.obj||'—'}</td>
    </tr>`).join(''):
    '<tr><td colspan="5" style="text-align:center;color:var(--muted);padding:18px">Nenhum investimento cadastrado</td></tr>';
  const total=investimentos.reduce((a,v)=>a+v.valor,0);
  document.getElementById('inv-total').textContent=BRL(total);
  document.getElementById('inv-count').textContent=investimentos.length;
  const last=investimentos[investimentos.length-1];
  document.getElementById('inv-obj').textContent=last?last.obj||'—':'—';
}

function addInvest(){
  const tipo=document.getElementById('inv-tipo').value;
  const ativo=document.getElementById('inv-ativo').value.trim();
  const valor=parseFloat(document.getElementById('inv-valor').value)||0;
  const rent=document.getElementById('inv-rent').value.trim();
  const obj=document.getElementById('inv-objetivo').value.trim();
  if(!ativo||!valor)return;
  investimentos.push({tipo,ativo,valor,rent,obj});
  ['inv-ativo','inv-valor','inv-rent','inv-objetivo'].forEach(id=>document.getElementById(id).value='');
  renderInvest();
}

// Charts
function buildCharts(){
  const cats={};
  getDesps(mesSel).forEach(d=>{cats[d.cat]=(cats[d.cat]||0)+Number(d.valor);});
  const labels=Object.keys(cats),vals=Object.values(cats);

  const cp=document.getElementById('chartPizza');
  if(window._cp)window._cp.destroy();
  window._cp=new Chart(cp,{type:'doughnut',
    data:{labels,datasets:[{data:vals,backgroundColor:COLORS.slice(0,labels.length),borderWidth:2,borderColor:'#13161b'}]},
    options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false}},cutout:'60%'}
  });
  document.getElementById('legendPizza').innerHTML=labels.map((l,i)=>
    `<div class="legend-item"><div class="legend-dot" style="background:${COLORS[i%COLORS.length]}"></div>${l}</div>`).join('');

  const cb=document.getElementById('chartBarras');
  if(window._cb)window._cb.destroy();
  window._cb=new Chart(cb,{type:'bar',
    data:{labels,datasets:[{data:vals,backgroundColor:COLORS.slice(0,labels.length),borderRadius:4}]},
    options:{indexAxis:'y',responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false}},
      scales:{x:{ticks:{callback:v=>'R$'+Math.round(v/1000)+'k',color:'#505360',font:{size:10,family:'DM Mono'}},grid:{color:'rgba(255,255,255,.04)'}},
              y:{ticks:{color:'#7a7d85',font:{size:10,family:'DM Mono'}},grid:{display:false}}}}
  });
}

// Ranking
function renderRanking(){
  const desps=getDesps(mesSel);
  const sorted=[...desps].sort((a,b)=>b.valor-a.valor).slice(0,7);
  const max=sorted[0]?.valor||1;
  document.getElementById('rankingList').innerHTML=sorted.map((d,i)=>`
    <div class="rank-item">
      <span class="rank-n">#${i+1}</span>
      <span class="rank-name">${d.desc}</span>
      <div class="rank-bar"><div class="pb"><div class="pf" style="width:${Math.round(d.valor/max*100)}%;background:var(--red)"></div></div></div>
      <span class="rank-val">${BRL(d.valor)}</span>
    </div>`).join('');
}

// Init
buildMesTabs();renderMes();renderFixas();renderMetas();renderRanking();updateDashboard();
setTimeout(buildCharts,150);
</script>
</body>
</html>
