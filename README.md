    .logo{display:flex;align-items:center;gap:12px}
    .cup{width:54px;height:54px;background:linear-gradient(180deg,var(--accent),var(--accent-2));border-radius:8px;display:flex;align-items:center;justify-content:center;font-weight:800;color:#141414}
    h1{margin:0;font-size:28px;letter-spacing:0.6px}
    .tag{margin-left:auto;text-align:right}
    .tag h2{margin:0;font-size:34px;color:#fff}
    .tag p{margin:4px 0 0;color:var(--muted)}
    main{margin-top:18px;display:grid;grid-template-columns:1fr;gap:18px}
    .games{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:16px}
    .card{background:linear-gradient(180deg, #1b1b1b, #151515);padding:16px;border-radius:10px;border:1px solid rgba(255,255,255,0.03)}
    .match{font-weight:700;font-size:18px;margin-bottom:12px}
    .odds{display:flex;gap:8px;margin-bottom:12px}
    .odd{background:#0f0f0f;padding:8px 12px;border-radius:8px;color:#fff;border:1px solid rgba(255,255,255,0.04)}
    .betbtn{display:block;width:100%;padding:12px;border-radius:8px;border:none;background:linear-gradient(180deg,var(--accent),var(--accent-2));color:#111;font-weight:700;font-size:16px;cursor:pointer}
    .controls{display:flex;gap:12px;flex-wrap:wrap;align-items:center}
    .small{background:transparent;border:1px solid rgba(255,255,255,0.04);padding:8px 12px;border-radius:8px;color:var(--muted)}
    .panel{background:linear-gradient(180deg,#0f0f0f, #0b0b0b);padding:16px;border-radius:10px;border:1px solid rgba(255,255,255,0.02)}
    table{width:100%;border-collapse:collapse;color:var(--muted)}
    th,td{padding:10px;border-bottom:1px solid rgba(255,255,255,0.02);text-align:left}
    .cta-row{display:flex;gap:12px;flex-wrap:wrap;margin-top:12px}
    .cta{flex:1;padding:12px;border-radius:8px;background:rgba(255,255,255,0.02);border:1px solid rgba(255,255,255,0.03);text-align:center;color:var(--muted)}
    footer{margin-top:18px;text-align:center;color:var(--muted);font-size:13px}
    @media (max-width:700px){
      .tag h2{font-size:24px}
      header{flex-direction:column;align-items:flex-start;gap:8px}
    }
    /* modal */
    .modal{position:fixed;inset:0;display:none;align-items:center;justify-content:center;background:rgba(0,0,0,0.6)}
    .modal.open{display:flex}
    .modal .box{background:var(--panel);padding:18px;border-radius:10px;width:380px;max-width:90%}
    label{display:block;color:var(--muted);font-size:13px;margin-top:8px}
    input,select{width:100%;padding:10px;border-radius:8px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:#fff}
    .row-flex{display:flex;gap:8px}
  </style>
</head>
<body>
  <div class="wrap">
    <header>
      <div class="logo">
        <div class="cup">🏆</div>
        <div>
          <h1>Aposta Amigo</h1>
          <div style="color:var(--muted);font-size:13px">Entre amigos — simples e rápido</div>
        </div>
      </div>
      <div class="tag">
        <h2>Aposte no Amigo</h2>
        <p>Apostas entre amigos, simples e seguras via Pix</p>
      </div>
    </header>

    <main>
      <section class="games">
        <div class="card">
          <div class="match">Real Madrid <br> Barcelona</div>
          <div class="odds"><div class="odd">1.8</div><div class="odd">2.2</div><div class="odd">1.6</div></div>
          <button class="betbtn" data-match="Real Madrid vs Barcelona">APOSTAR</button>
        </div>
        <div class="card">
          <div class="match">Atlético <br> Sevilla</div>
          <div class="odds"><div class="odd">1.3</div><div class="odd">1.6</div><div class="odd">1.8</div></div>
          <button class="betbtn" data-match="Atlético vs Sevilla">APOSTAR</button>
        </div>
        <div class="card">
          <div class="match">Benfica <br> Porto</div>
          <div class="odds"><div class="odd">1.6</div><div class="odd">1.6</div><div class="odd">1.8</div></div>
          <button class="betbtn" data-match="Benfica vs Porto">APOSTAR</button>
        </div>
        <div class="card">
          <div class="match">Inter <br> Milan</div>
          <div class="odds"><div class="odd">1.2</div><div class="odd">1.6</div><div class="odd">1.6</div></div>
          <button class="betbtn" data-match="Inter vs Milan">APOSTAR</button>
        </div>
      </section>

      <section class="panel">
        <h3 style="margin-top:0">Apostas registradas</h3>
        <div style="margin:8px 0;color:var(--muted)">Total apostado: R$ <span id="total">0.00</span></div>
        <div id="betsTable">
          <table>
            <thead><tr><th>Jogador</th><th>Time</th><th>Valor (R$)</th></tr></thead>
            <tbody id="tb"></tbody>
          </table>
        </div>

        <div class="cta-row">
          <div class="cta"><button class="small" id="export">Exportar CSV</button></div>
          <div class="cta"><button class="small" id="instr">Gerar instruções Pix</button></div>
          <div class="cta"><button class="small" id="summary">Gerar resumo</button></div>
        </div>
      </section>
    </main>

    <footer>
      <div style="max-width:800px;margin:8px auto;color:var(--muted)">⚠️ Pagamentos manuais via Pix — esta ferramenta apenas gera instruções. Verifique regras locais antes de apostar com dinheiro real.</div>
    </footer>
  </div>

  <div class="modal" id="modal">
    <div class="box">
      <h3>Registrar aposta</h3>
      <label>Jogador</label>
      <input id="mName" placeholder="Seu nome" />
      <label>Escolha time/mercado</label>
      <select id="mTeam"></select>
      <label>Valor (R$)</label>
      <input id="mAmount" type="number" min="1" step="0.01" />
      <label>Chave PIX (opcional)</label>
      <input id="mPix" placeholder="Ex: cpf - email - telefone" />
      <div style="margin-top:12px;display:flex;gap:8px;justify-content:flex-end">
        <button class="small" id="cancel">Cancelar</button>
        <button class="small" id="save">Registrar</button>
      </div>
    </div>
  </div>

<script>
let bets = JSON.parse(localStorage.getItem('bets_v1') || '[]')

function renderBets(){
  const tb = document.getElementById('tb'); tb.innerHTML = ''
  let total = 0
  bets.forEach(b=>{
    total += Number(b.amount)
    const tr = document.createElement('tr')
    tr.innerHTML = `<td>${b.player}</td><td>${b.team}</td><td>R$ ${Number(b.amount).toFixed(2)}</td>`
    tb.appendChild(tr)
  })
  document.getElementById('total').textContent = Number(total).toFixed(2)
  localStorage.setItem('bets_v1', JSON.stringify(bets))
}
renderBets()

document.querySelectorAll('.betbtn').forEach(btn=>{
  btn.onclick = ()=>{
    const match = btn.dataset.match
    openModal(match)
  }
})

function openModal(match){
  document.getElementById('modal').classList.add('open')
  document.getElementById('mTeam').innerHTML = `<option>${match}</option>`
  document.getElementById('mName').value = ''
  document.getElementById('mAmount').value = ''
  document.getElementById('mPix').value = ''
}

document.getElementById('cancel').onclick = ()=> document.getElementById('modal').classList.remove('open')

document.getElementById('save').onclick = ()=>{
  const player = document.getElementById('mName').value.trim()
  const team = document.getElementById('mTeam').value
  const amount = parseFloat(document.getElementById('mAmount').value)
  const pix = document.getElementById('mPix').value.trim()
  if(!player) return alert('Informe seu nome')
  if(isNaN(amount) || amount<=0) return alert('Valor inválido')
  bets.push({player,team,amount,pix})
  renderBets()
  document.getElementById('modal').classList.remove('open')
}

document.getElementById('export').onclick = ()=>{
  const rows = [['player','team','amount','pix']]
  bets.forEach(b=>rows.push([b.player,b.team,b.amount,b.pix||'']))
  const csv = rows.map(r=>r.map(c=>`"${((''+c).replace(/"/g,'""'))}"`).join(',')).join('\n')
  const blob = new Blob([csv],{type:'text/csv'}); const url = URL.createObjectURL(blob); const a=document.createElement('a'); a.href=url; a.download='apostas.csv'; a.click(); URL.revokeObjectURL(url)
}

document.getElementById('instr').onclick = ()=>{
  if(bets.length===0) return alert('Sem apostas')
  // prepare a simple instructions string
  const total = bets.reduce((s,b)=>s+Number(b.amount),0).toFixed(2)
  let html = '<h3>Instruções Pix (copie e cole)</h3><div style="max-height:300px;overflow:auto">'
  bets.forEach(b=>{
    html += `<div style="margin-bottom:8px">Devedor: <strong>${b.player}</strong> — Valor: R$ ${Number(b.amount).toFixed(2)} — Chave: ${b.pix||'[não informada]'}</div>`
  })
  html += '</div>'
  const panel = document.createElement('div')
  panel.className = 'panel'
  panel.innerHTML = html
  document.getElementById('modal').classList.add('open')
  document.getElementById('modal').querySelector('.box').innerHTML = panel.innerHTML + '<div style="margin-top:8px;text-align:right"><button class="small" id="closeInstr">Fechar</button></div>'
  document.getElementById('closeInstr').onclick = ()=> location.reload()
}

document.getElementById('summary').onclick = ()=>{
  if(bets.length===0) return alert('Sem apostas')
  // simple net balance per player
  const map = {}
  bets.forEach(b=>{ if(!map[b.player]) map[b.player]={staked:0,received:0}; map[b.player].staked += Number(b.amount) })
  // for demo purposes assume winners split equally - we won't calculate winners here
  let html = '<h3>Resumo (exporte CSV para cálculo)</h3><div style="max-height:300px;overflow:auto">'
  Object.keys(map).forEach(p=> html += `<div>${p} — Apostou: R$ ${map[p].staked.toFixed(2)}</div>`)
  html += '</div>'
  document.getElementById('modal').classList.add('open')
  document.getElementById('modal').querySelector('.box').innerHTML = html + '<div style="margin-top:8px;text-align:right"><button class="small" onclick="location.reload()">Fechar</button></div>'
}

</script>
</body>
</html>
