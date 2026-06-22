<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Minhas Compras - Controle Mensal</title>
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }
  :root {
    --bg: #f4f5f7;
    --card: #ffffff;
    --primary: #2563eb;
    --primary-dark: #1d4ed8;
    --text: #1f2937;
    --muted: #6b7280;
    --border: #e5e7eb;
    --success: #16a34a;
    --success-bg: #dcfce7;
    --danger: #dc2626;
    --danger-bg: #fef2f2;
    --shadow: 0 1px 3px rgba(0,0,0,0.08), 0 1px 2px rgba(0,0,0,0.04);
  }
  body {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    background: var(--bg);
    color: var(--text);
    line-height: 1.5;
    -webkit-font-smoothing: antialiased;
  }
  .topbar {
    background: var(--primary);
    color: #fff;
    padding: 16px;
    position: sticky;
    top: 0;
    z-index: 10;
    box-shadow: var(--shadow);
    display: flex; align-items: center; justify-content: space-between; gap: 10px;
  }
  .topbar h1 { font-size: 19px; font-weight: 600; display: flex; align-items: center; gap: 10px; }
  .topbar .tb-btn { background: rgba(255,255,255,0.18); color:#fff; font-size:13px; padding:7px 12px; }
  .topbar .tb-btn:hover { background: rgba(255,255,255,0.30); }
  .container { max-width: 760px; margin: 0 auto; padding: 20px 16px 60px; }

  .card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    box-shadow: var(--shadow);
    padding: 18px 20px;
    margin-bottom: 14px;
  }
  .mes-card { cursor: pointer; transition: transform .12s, box-shadow .12s; }
  .mes-card:hover { transform: translateY(-1px); box-shadow: 0 4px 12px rgba(0,0,0,0.10); }

  .mes-head { display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; }
  .mes-nome { font-size: 17px; font-weight: 600; }
  .mes-info { display: flex; gap: 18px; font-size: 13px; color: var(--muted); }
  .mes-info strong { color: var(--text); font-weight: 600; }

  .badge { font-size: 12px; padding: 4px 11px; border-radius: 8px; font-weight: 500; }
  .badge-aberto { background: var(--success-bg); color: var(--success); }
  .badge-fin { background: #f3f4f6; color: var(--muted); }

  .row-novo { display: flex; gap: 8px; margin-top: 6px; }
  input, button, select { font-family: inherit; font-size: 14px; }
  input[type=text], input[type=number], select {
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 9px 11px;
    outline: none;
    background: #fff;
    color: var(--text);
    transition: border-color .15s, box-shadow .15s;
  }
  input:focus, select:focus { border-color: var(--primary); box-shadow: 0 0 0 3px rgba(37,99,235,0.12); }

  button {
    border: none;
    border-radius: 8px;
    padding: 9px 16px;
    background: var(--primary);
    color: #fff;
    font-weight: 500;
    cursor: pointer;
    transition: background .15s, transform .08s;
    display: inline-flex; align-items: center; gap: 6px; justify-content: center;
  }
  button:hover { background: var(--primary-dark); }
  button:active { transform: scale(0.98); }
  button.ghost { background: #fff; color: var(--text); border: 1px solid var(--border); }
  button.ghost:hover { background: #f9fafb; }
  button.danger { background: #fff; color: var(--danger); border: 1px solid #fecaca; }
  button.danger:hover { background: var(--danger-bg); }
  button.icon { background: none; color: var(--danger); padding: 6px 8px; }
  button.icon:hover { background: var(--danger-bg); }
  button.sm { padding: 7px 12px; font-size: 13px; }

  .empty { text-align: center; color: var(--muted); padding: 36px 0; font-size: 14px; }

  .head-mes { display: flex; align-items: center; gap: 10px; margin-bottom: 18px; }
  .back { background: none; color: var(--text); padding: 6px 8px; font-size: 20px; }
  .back:hover { background: #eef0f3; }
  .head-mes h2 { font-size: 19px; font-weight: 600; flex: 1; }

  .stats { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin-bottom: 14px; }
  .stat { background: #f8fafc; border-radius: 10px; padding: 12px 14px; }
  .stat .lbl { font-size: 12px; color: var(--muted); }
  .stat .val { font-size: 21px; font-weight: 600; margin-top: 2px; }
  .dif { font-size: 13px; color: var(--muted); margin-bottom: 16px; }
  .dif strong { font-weight: 600; }

  .toolbar { display: flex; gap: 8px; flex-wrap: wrap; margin-bottom: 16px; }

  .cat-resumo { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 18px; }
  .cat-chip { font-size: 12px; padding: 6px 11px; border-radius: 20px; background: #fff; border: 1px solid var(--border); display: inline-flex; align-items: center; gap: 6px; }
  .cat-chip .dot { width: 9px; height: 9px; border-radius: 50%; }
  .cat-chip strong { font-weight: 600; }

  .cat-bloco { margin-bottom: 16px; border-radius: 14px; transition: background .15s, outline .15s; }
  .cat-bloco.drop-target { outline: 2px dashed var(--primary); outline-offset: 3px; background: rgba(37,99,235,0.04); }
  .cat-titulo { display: flex; align-items: center; gap: 8px; font-size: 14px; font-weight: 600; margin-bottom: 6px; padding: 0 2px; }
  .cat-titulo .dot { width: 11px; height: 11px; border-radius: 50%; }
  .cat-titulo .cat-tot { margin-left: auto; font-size: 13px; color: var(--muted); font-weight: 500; }

  table { width: 100%; border-collapse: collapse; }
  th { text-align: left; font-size: 12px; color: var(--muted); font-weight: 500; padding: 8px 4px; border-bottom: 1px solid var(--border); }
  th.c { text-align: center; }
  th.r { text-align: right; }
  td { padding: 7px 3px; border-bottom: 1px solid #f1f2f4; font-size: 14px; vertical-align: middle; }
  td.r { text-align: right; }
  td.c { text-align: center; }
  td.sub { font-weight: 600; white-space: nowrap; }
  tr.item-row.dragging { opacity: .4; }
  tr.item-row.drag-over td { box-shadow: inset 0 2px 0 var(--primary); }
  .grip { cursor: grab; color: #c0c4cc; padding: 0 2px; user-select: none; touch-action: none; font-size: 16px; }
  .grip:active { cursor: grabbing; }
  .cell-in { width: 100%; }
  .in-nome { min-width: 80px; }
  .in-qtd { width: 50px; text-align: center; }
  .in-val { width: 70px; text-align: right; }
  input.compact, select.compact { padding: 7px 8px; font-size: 13px; }

  .actions { margin-top: 18px; display: flex; flex-direction: column; gap: 10px; }
  .actions button { width: 100%; padding: 12px; }
  .fin-note { font-size: 13px; color: var(--muted); text-align: center; margin-top: 8px; }

  .modelo-item { display: flex; align-items: center; gap: 8px; padding: 8px 4px; border-bottom: 1px solid #f1f2f4; }
  .modelo-item .dot { width: 10px; height: 10px; border-radius: 50%; flex-shrink: 0; }
  .modelo-item .mnome { flex: 1; font-size: 14px; }
  .modelo-add-row { display: flex; gap: 8px; margin-top: 12px; flex-wrap: wrap; }
  .chk { width: 18px; height: 18px; accent-color: var(--primary); }
  .modelo-pick { display:flex; align-items:center; gap:10px; padding:9px 4px; border-bottom:1px solid #f1f2f4; cursor:pointer; }
  .modelo-pick .dot { width:10px;height:10px;border-radius:50%; }
  .modelo-pick .mnome { flex:1; font-size:14px; }

  @media (max-width: 480px) {
    .in-nome { min-width: 64px; }
    td, th { padding: 6px 2px; font-size: 13px; }
  }
</style>
</head>
<body>
  <div class="topbar">
    <h1>🛒 Minhas Compras</h1>
    <button class="tb-btn" id="btn-modelo">⭐ Lista modelo</button>
  </div>
  <div class="container" id="app"></div>

<script>
const STORE_KEY = 'mercado_site_v3';
const MODELO_KEY = 'mercado_modelo_v3';

const CATEGORIAS = [
  { id: 'comida',    nome: 'Comida / Mercearia', cor: '#d97706', emoji: '🍚' },
  { id: 'carnes',    nome: 'Carnes e ovos',      cor: '#dc2626', emoji: '🥩' },
  { id: 'hortifruti',nome: 'Hortifrúti',          cor: '#16a34a', emoji: '🥬' },
  { id: 'laticinios',nome: 'Laticínios e frios',  cor: '#2563eb', emoji: '🧀' },
  { id: 'bebidas',   nome: 'Bebidas',            cor: '#7c3aed', emoji: '🥤' },
  { id: 'limpeza',   nome: 'Limpeza',            cor: '#0891b2', emoji: '🧽' },
  { id: 'higiene',   nome: 'Higiene',            cor: '#db2777', emoji: '🧴' },
  { id: 'outros',    nome: 'Outros',             cor: '#6b7280', emoji: '📦' }
];
const catInfo = id => CATEGORIAS.find(c => c.id === id) || CATEGORIAS[CATEGORIAS.length-1];

let state = { meses: [], aberto: null, modo: 'lista' };
let modelo = [];

function carregar() {
  try { const raw = localStorage.getItem(STORE_KEY); if (raw) state = JSON.parse(raw); } catch(e) {}
  try { const rm = localStorage.getItem(MODELO_KEY); if (rm) modelo = JSON.parse(rm); } catch(e) {}
  if (!state.meses) state.meses = [];
  if (!Array.isArray(modelo)) modelo = [];
  state.modo = state.modo || 'lista';
}
function salvar() { try { localStorage.setItem(STORE_KEY, JSON.stringify(state)); } catch(e) {} }
function salvarModelo() { try { localStorage.setItem(MODELO_KEY, JSON.stringify(modelo)); } catch(e) {} }

const brl = n => 'R$ ' + (Number(n)||0).toLocaleString('pt-BR', {minimumFractionDigits:2, maximumFractionDigits:2});
const uid = () => Date.now().toString(36) + Math.random().toString(36).slice(2,6);
const esc = s => (s||'').replace(/&/g,'&amp;').replace(/"/g,'&quot;').replace(/</g,'&lt;');
const subItem = i => (Number(i.pago)||0)*(Number(i.qtd)||0);
const totalMes = m => (m.itens||[]).reduce((s,i)=> s + subItem(i), 0);
const orcMes   = m => (m.itens||[]).reduce((s,i)=> s + (Number(i.orc)||0)*(Number(i.qtd)||0), 0);
const totalCat = (m, cid) => (m.itens||[]).filter(i=>(i.cat||'outros')===cid).reduce((s,i)=> s+subItem(i), 0);

function render() {
  const app = document.getElementById('app');
  if (state.modo === 'modelo') app.innerHTML = viewModelo();
  else if (state.modo === 'mes') app.innerHTML = viewMes();
  else app.innerHTML = viewLista();
  wire();
}

function viewLista() {
  const cards = state.meses.length ? state.meses.map(m => `
    <div class="card mes-card" data-id="${m.id}">
      <div class="mes-head">
        <span class="mes-nome">${esc(m.nome)}</span>
        ${m.finalizado ? '<span class="badge badge-fin">🔒 finalizado</span>' : '<span class="badge badge-aberto">aberto</span>'}
      </div>
      <div class="mes-info">
        <span>${(m.itens||[]).length} itens</span>
        <span>Pago: <strong>${brl(totalMes(m))}</strong></span>
      </div>
    </div>`).join('') : '<div class="empty">Nenhum mês ainda. Crie o primeiro abaixo.</div>';

  return `${cards}
    <div class="card">
      <div class="row-novo">
        <input id="novo-nome" type="text" placeholder="Ex: Janeiro 2026" style="flex:1;">
        <button id="btn-novo">+ Novo mês</button>
      </div>
    </div>`;
}

/* ---------- LISTA MODELO ---------- */
function viewModelo() {
  const itens = modelo.map(it => {
    const c = catInfo(it.cat);
    return `<div class="modelo-item" data-mid="${it.id}">
      <span class="dot" style="background:${c.cor}"></span>
      <span class="mnome">${esc(it.nome)}</span>
      <span style="font-size:12px;color:var(--muted);">${c.emoji} ${esc(c.nome.split(' ')[0])}</span>
      <button class="icon del-modelo" data-mid="${it.id}" title="Remover">🗑</button>
    </div>`;
  }).join('') || '<div class="empty">Nenhum item no modelo. Adicione os que você compra sempre.</div>';

  return `
    <div class="head-mes">
      <button class="back" id="voltar-modelo" title="Voltar">←</button>
      <h2>⭐ Lista modelo</h2>
    </div>
    <p style="font-size:13px;color:var(--muted);margin-bottom:14px;">Itens que você compra sempre. Em qualquer mês aberto, use “Adicionar do modelo” para trazer todos de uma vez, sem digitar.</p>
    <div class="card">
      ${itens}
      <div class="modelo-add-row">
        <input id="mod-nome" type="text" placeholder="Ex: Arroz" style="flex:1; min-width:120px;">
        <select id="mod-cat" style="min-width:130px;">
          ${CATEGORIAS.map(c=>`<option value="${c.id}">${c.emoji} ${c.nome}</option>`).join('')}
        </select>
        <button id="mod-add">+ Adicionar ao modelo</button>
      </div>
    </div>`;
}

/* ---------- MÊS ---------- */
function linhaItem(i, fin) {
  const sub = subItem(i);
  if (fin) return `
    <tr>
      <td>${esc(i.nome)||'—'}</td>
      <td class="c">${i.qtd||0}</td>
      <td class="r" style="color:var(--muted);font-size:13px;">${brl(i.orc)}</td>
      <td class="r">${brl(i.pago)}</td>
      <td class="r sub">${brl(sub)}</td>
    </tr>`;
  return `
    <tr class="item-row" data-iid="${i.id}" draggable="true">
      <td style="width:24px;"><span class="grip" title="Arrastar">⠿</span></td>
      <td><input class="cell-in in-nome compact f-nome" data-iid="${i.id}" value="${esc(i.nome)}" placeholder="Item"></td>
      <td><input class="in-qtd compact f-qtd" data-iid="${i.id}" type="number" min="0" step="1" value="${i.qtd||''}" placeholder="0"></td>
      <td><input class="in-val compact f-orc" data-iid="${i.id}" type="number" min="0" step="0.01" value="${i.orc||''}" placeholder="0,00"></td>
      <td><input class="in-val compact f-pago" data-iid="${i.id}" type="number" min="0" step="0.01" value="${i.pago||''}" placeholder="0,00"></td>
      <td class="r sub" data-sub="${i.id}">${brl(sub)}</td>
      <td><button class="icon del-item" data-iid="${i.id}" title="Excluir">🗑</button></td>
    </tr>`;
}

function viewMes() {
  const m = state.meses.find(x => x.id === state.aberto);
  if (!m) { state.modo = 'lista'; return viewLista(); }
  const fin = m.finalizado;

  const usadas = CATEGORIAS.filter(c => (m.itens||[]).some(i => (i.cat||'outros') === c.id));
  const chips = usadas.map(c => `
    <span class="cat-chip"><span class="dot" style="background:${c.cor}"></span>${c.emoji} ${esc(c.nome.split(' ')[0])} <strong>${brl(totalCat(m,c.id))}</strong></span>
  `).join('');

  const blocos = usadas.map(c => {
    const itens = (m.itens||[]).filter(i => (i.cat||'outros') === c.id);
    const linhas = itens.map(i => linhaItem(i, fin)).join('');
    return `
      <div class="cat-bloco" data-cat="${c.id}">
        <div class="cat-titulo">
          <span class="dot" style="background:${c.cor}"></span>${c.emoji} ${esc(c.nome)}
          <span class="cat-tot">${brl(totalCat(m,c.id))}</span>
        </div>
        <div class="card" style="padding:12px 14px;">
          <table>
            <thead><tr>${fin?'':'<th style="width:24px;"></th>'}<th>Item</th><th class="c">Qtd</th><th class="r">Orç.</th><th class="r">Pago</th><th class="r">Subtotal</th>${fin?'':'<th></th>'}</tr></thead>
            <tbody>${linhas}</tbody>
          </table>
        </div>
      </div>`;
  }).join('');

  const orc = orcMes(m), tot = totalMes(m), dif = tot - orc;
  const difCor = dif > 0 ? 'var(--danger)' : 'var(--success)';

  const corpo = (m.itens||[]).length
    ? `${chips ? `<div class="cat-resumo">${chips}</div>` : ''}${blocos}`
    : '<div class="card"><div class="empty">Nenhum item ainda. Adicione abaixo ou use o modelo.</div></div>';

  return `
    <div class="head-mes">
      <button class="back" id="voltar" title="Voltar">←</button>
      <h2>${esc(m.nome)}</h2>
      ${fin ? '<span class="badge badge-fin">🔒 finalizado</span>' : ''}
    </div>

    <div class="stats">
      <div class="stat"><div class="lbl">Orçamento</div><div class="val" id="st-orc">${brl(orc)}</div></div>
      <div class="stat"><div class="lbl">Total pago</div><div class="val" id="st-tot">${brl(tot)}</div></div>
    </div>
    <div class="dif" id="st-dif">Diferença: <strong style="color:${difCor};">${dif>0?'+':''}${brl(dif)}</strong> ${dif>0?'(acima do orçado)':'(dentro do orçado)'}</div>

    ${fin ? '' : `<div class="toolbar">
      <button class="ghost sm" id="add-modelo">⭐ Adicionar do modelo</button>
    </div>`}

    ${corpo}

    ${fin ? '<div class="fin-note">🔒 Este mês está finalizado — somente visualização.</div>' : `
    <div class="card" style="padding:14px 16px; margin-top:6px;">
      <div style="font-size:13px; color:var(--muted); margin-bottom:8px; font-weight:500;">Adicionar item avulso</div>
      <div style="display:flex; flex-direction:column; gap:8px;">
        <div style="display:flex; gap:8px;">
          <input id="add-nome" type="text" placeholder="Nome do item" style="flex:1;">
          <select id="add-cat" style="min-width:120px;">
            ${CATEGORIAS.map(c=>`<option value="${c.id}">${c.emoji} ${c.nome}</option>`).join('')}
          </select>
        </div>
        <button id="add-item">+ Adicionar</button>
      </div>
    </div>
    <div class="actions">
      <button class="danger" id="finalizar">🔒 Finalizar mês</button>
      <div class="fin-note">Ao finalizar, o mês fica travado e não poderá mais ser editado. Dica: arraste pelo ⠿ para reordenar ou mover de categoria.</div>
    </div>`}
  `;
}

function recalc(m) {
  (m.itens||[]).forEach(i => {
    const cell = document.querySelector(`[data-sub="${i.id}"]`);
    if (cell) cell.textContent = brl(subItem(i));
  });
  const orc = orcMes(m), tot = totalMes(m), dif = tot - orc;
  const eo = document.getElementById('st-orc'), et = document.getElementById('st-tot'), ed = document.getElementById('st-dif');
  if (eo) eo.textContent = brl(orc);
  if (et) et.textContent = brl(tot);
  if (ed) {
    const cor = dif > 0 ? 'var(--danger)' : 'var(--success)';
    ed.innerHTML = `Diferença: <strong style="color:${cor};">${dif>0?'+':''}${brl(dif)}</strong> ${dif>0?'(acima do orçado)':'(dentro do orçado)'}`;
  }
}

/* ---------- DRAG & DROP ---------- */
let dragId = null;

function setupDrag(m) {
  const rows = document.querySelectorAll('tr.item-row');
  rows.forEach(row => {
    row.addEventListener('dragstart', e => {
      dragId = row.dataset.iid;
      row.classList.add('dragging');
      e.dataTransfer.effectAllowed = 'move';
      try { e.dataTransfer.setData('text/plain', dragId); } catch(_) {}
    });
    row.addEventListener('dragend', () => {
      row.classList.remove('dragging');
      document.querySelectorAll('.drag-over').forEach(r=>r.classList.remove('drag-over'));
      document.querySelectorAll('.drop-target').forEach(r=>r.classList.remove('drop-target'));
      dragId = null;
    });
    row.addEventListener('dragover', e => {
      e.preventDefault();
      document.querySelectorAll('.drag-over').forEach(r=>r.classList.remove('drag-over'));
      if (row.dataset.iid !== dragId) row.classList.add('drag-over');
    });
    row.addEventListener('drop', e => {
      e.preventDefault();
      const targetId = row.dataset.iid;
      if (!dragId || dragId === targetId) return;
      const bloco = row.closest('.cat-bloco');
      const novaCat = bloco ? bloco.dataset.cat : null;
      moverItem(m, dragId, targetId, novaCat);
    });
  });

  document.querySelectorAll('.cat-bloco').forEach(bloco => {
    bloco.addEventListener('dragover', e => { e.preventDefault(); bloco.classList.add('drop-target'); });
    bloco.addEventListener('dragleave', e => { if (!bloco.contains(e.relatedTarget)) bloco.classList.remove('drop-target'); });
    bloco.addEventListener('drop', e => {
      e.preventDefault();
      if (!dragId) return;
      const novaCat = bloco.dataset.cat;
      moverItem(m, dragId, null, novaCat);
    });
  });
}

function moverItem(m, fromId, toId, novaCat) {
  const arr = m.itens;
  const fromIdx = arr.findIndex(i => i.id === fromId);
  if (fromIdx < 0) return;
  const [item] = arr.splice(fromIdx, 1);
  if (novaCat) item.cat = novaCat;
  if (toId) {
    const toIdx = arr.findIndex(i => i.id === toId);
    arr.splice(toIdx < 0 ? arr.length : toIdx, 0, item);
  } else {
    arr.push(item);
  }
  salvar(); render();
}

function wire() {
  document.getElementById('btn-modelo').onclick = () => { state.modo = 'modelo'; render(); };

  if (state.modo === 'modelo') {
    document.getElementById('voltar-modelo').onclick = () => { state.modo = state.aberto ? 'mes' : 'lista'; render(); };
    document.querySelectorAll('.del-modelo').forEach(b =>
      b.onclick = () => { modelo = modelo.filter(x=>x.id!==b.dataset.mid); salvarModelo(); render(); });
    const mn = document.getElementById('mod-nome'), mc = document.getElementById('mod-cat');
    const addMod = () => {
      const nome = (mn.value||'').trim();
      if (!nome) { mn.focus(); return; }
      modelo.push({ id: uid(), nome, cat: mc.value });
      salvarModelo(); render();
    };
    document.getElementById('mod-add').onclick = addMod;
    mn.onkeydown = e => { if (e.key === 'Enter') addMod(); };
    return;
  }

  if (state.modo === 'lista') {
    document.querySelectorAll('.mes-card').forEach(c =>
      c.onclick = () => { state.aberto = c.dataset.id; state.modo = 'mes'; render(); });
    const inp = document.getElementById('novo-nome');
    const criar = () => {
      const nome = (inp.value||'').trim();
      if (!nome) { inp.focus(); return; }
      const m = { id: uid(), nome, finalizado:false, itens:[] };
      state.meses.unshift(m);
      state.aberto = m.id; state.modo = 'mes';
      salvar(); render();
    };
    document.getElementById('btn-novo').onclick = criar;
    inp.onkeydown = e => { if (e.key === 'Enter') criar(); };
    return;
  }

  const m = state.meses.find(x => x.id === state.aberto);
  document.getElementById('voltar').onclick = () => { state.modo = 'lista'; render(); };
  if (!m || m.finalizado) return;

  document.querySelectorAll('.f-nome').forEach(el =>
    el.oninput = () => { const it = m.itens.find(i=>i.id===el.dataset.iid); if(it){ it.nome = el.value; salvar(); } });

  document.querySelectorAll('.f-qtd, .f-orc, .f-pago').forEach(el =>
    el.oninput = () => {
      const it = m.itens.find(i=>i.id===el.dataset.iid);
      if (!it) return;
      if (el.classList.contains('f-qtd')) it.qtd = el.value;
      else if (el.classList.contains('f-orc')) it.orc = el.value;
      else if (el.classList.contains('f-pago')) it.pago = el.value;
      salvar(); recalc(m);
    });

  document.querySelectorAll('.del-item').forEach(b =>
    b.onclick = () => { m.itens = m.itens.filter(i=>i.id!==b.dataset.iid); salvar(); render(); });

  const addNome = document.getElementById('add-nome'), addCat = document.getElementById('add-cat');
  const addItem = () => {
    m.itens.push({ id:uid(), nome:(addNome.value||'').trim(), cat: addCat.value, qtd:'', orc:'', pago:'' });
    salvar(); render();
  };
  document.getElementById('add-item').onclick = addItem;
  if (addNome) addNome.onkeydown = e => { if (e.key === 'Enter') addItem(); };

  const addMod = document.getElementById('add-modelo');
  if (addMod) addMod.onclick = () => {
    if (!modelo.length) { alert('Sua lista modelo está vazia. Toque em "⭐ Lista modelo" no topo para criar.'); return; }
    const existentes = new Set((m.itens||[]).map(i => (i.nome||'').trim().toLowerCase()));
    let add = 0;
    modelo.forEach(mod => {
      if (!existentes.has((mod.nome||'').trim().toLowerCase())) {
        m.itens.push({ id:uid(), nome:mod.nome, cat:mod.cat, qtd:'', orc:'', pago:'' });
        add++;
      }
    });
    salvar(); render();
    if (add === 0) setTimeout(()=>alert('Todos os itens do modelo já estão neste mês.'),50);
  };

  document.getElementById('finalizar').onclick = () => {
    if (confirm('Finalizar o mês "'+m.nome+'"?\n\nDepois disso ele fica travado e você só poderá visualizar.')) {
      m.finalizado = true; salvar(); render();
    }
  };

  setupDrag(m);
}

carregar();
render();
</script>
</body>
</html>
