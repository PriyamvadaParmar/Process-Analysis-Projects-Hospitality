<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:var(--font-sans)}
.wrap{padding:0 0 1.5rem;display:flex;flex-direction:column;gap:20px}
.section-label{font-size:11px;font-weight:500;text-transform:uppercase;letter-spacing:.06em;color:var(--color-text-tertiary);margin-bottom:10px}

.tab-row{display:flex;gap:6px;margin-bottom:14px}
.tab{font-size:12px;padding:5px 14px;border-radius:20px;border:0.5px solid var(--color-border-secondary);cursor:pointer;background:transparent;color:var(--color-text-secondary);transition:all .15s}
.tab.active{background:var(--color-background-info);color:var(--color-text-info);border-color:var(--color-border-info)}

.process-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.proc-col-head{font-size:11px;font-weight:500;padding:6px 10px;border-radius:var(--border-radius-md);margin-bottom:8px;text-align:center}
.proc-step{display:flex;align-items:flex-start;gap:8px;padding:8px 10px;border-radius:var(--border-radius-md);border:0.5px solid var(--color-border-tertiary);margin-bottom:6px;background:var(--color-background-primary)}
.proc-step-dot{width:8px;height:8px;border-radius:50%;margin-top:4px;flex-shrink:0}
.proc-step-text{font-size:12px;color:var(--color-text-primary);line-height:1.4;font-weight:500}
.proc-step-sub{font-size:11px;color:var(--color-text-secondary);margin-top:2px}
.proc-arrow{text-align:center;font-size:11px;color:var(--color-text-tertiary);margin:2px 0}
.pain-tag{font-size:10px;padding:2px 7px;border-radius:10px;background:#FAECE7;color:#712B13;display:inline-block;margin-top:3px}
.fix-tag{font-size:10px;padding:2px 7px;border-radius:10px;background:#E1F5EE;color:#085041;display:inline-block;margin-top:3px}

.sla-table{width:100%;border-collapse:collapse}
.sla-table th{font-size:11px;font-weight:500;color:var(--color-text-secondary);text-align:left;padding:6px 10px;border-bottom:0.5px solid var(--color-border-secondary)}
.sla-table td{font-size:12px;padding:8px 10px;border-bottom:0.5px solid var(--color-border-tertiary);vertical-align:middle}
.sla-bar-wrap{width:140px;height:8px;background:var(--color-background-tertiary);border-radius:4px;overflow:hidden;display:inline-block;vertical-align:middle}
.sla-bar{height:100%;border-radius:4px;transition:width .4s}
.sla-status{font-size:10px;padding:2px 8px;border-radius:10px;display:inline-block;font-weight:500}

.room-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:8px}
.room-card{border-radius:var(--border-radius-md);border:0.5px solid var(--color-border-tertiary);padding:10px 10px 8px;cursor:pointer;transition:border-color .15s;background:var(--color-background-primary)}
.room-card:hover{border-color:var(--color-border-primary)}
.room-number{font-size:13px;font-weight:500;margin-bottom:4px}
.room-status-pill{font-size:10px;padding:2px 8px;border-radius:10px;display:inline-block;margin-bottom:6px}
.room-detail{font-size:11px;color:var(--color-text-secondary);line-height:1.5}
.room-sla{font-size:10px;margin-top:4px;font-weight:500}

.stat-row{display:grid;grid-template-columns:repeat(3,1fr);gap:10px}
.stat-card{background:var(--color-background-secondary);border-radius:var(--border-radius-md);padding:12px 14px}
.stat-val{font-size:22px;font-weight:500;color:var(--color-text-primary)}
.stat-lbl{font-size:11px;color:var(--color-text-secondary);margin-top:2px}
.stat-delta{font-size:11px;font-weight:500;margin-top:4px}

.panel{display:none}
.panel.active{display:block}
</style>

<div class="wrap">

<div class="stat-row">
  <div class="stat-card">
    <div class="stat-val">45<span style="font-size:14px;font-weight:400;color:var(--color-text-secondary)"> min</span></div>
    <div class="stat-lbl">AS-IS turnaround</div>
    <div class="stat-delta" style="color:#D85A30">Avg. room delay</div>
  </div>
  <div class="stat-card">
    <div class="stat-val">20<span style="font-size:14px;font-weight:400;color:var(--color-text-secondary)"> min</span></div>
    <div class="stat-lbl">TO-BE target (SLA)</div>
    <div class="stat-delta" style="color:#1D9E75">55% reduction</div>
  </div>
  <div class="stat-card">
    <div class="stat-val">3</div>
    <div class="stat-lbl">Key gaps closed</div>
    <div class="stat-delta" style="color:#1D9E75">Comms + tracking + SLA</div>
  </div>
</div>

<div>
  <div class="section-label">View</div>
  <div class="tab-row">
    <button class="tab active" onclick="showPanel('process',this)">AS-IS vs TO-BE</button>
    <button class="tab" onclick="showPanel('sla',this)">SLA breakdown</button>
    <button class="tab" onclick="showPanel('board',this)">Room status board</button>
  </div>

  <div id="process" class="panel active">
    <div class="process-grid">
      <div>
        <div class="proc-col-head" style="background:#FAECE7;color:#712B13">AS-IS — current state</div>
        <div class="proc-step">
          <div class="proc-step-dot" style="background:#888780"></div>
          <div><div class="proc-step-text">Guest checks out</div><div class="proc-step-sub">Room handed back verbally</div></div>
        </div>
        <div class="proc-arrow">↓</div>
        <div class="proc-step">
          <div class="proc-step-dot" style="background:#D85A30"></div>
          <div><div class="proc-step-text">Front desk calls HK</div><div class="proc-step-sub">Phone / radio — no record</div><span class="pain-tag">No task log</span></div>
        </div>
        <div class="proc-arrow">↓</div>
        <div class="proc-step">
          <div class="proc-step-dot" style="background:#D85A30"></div>
          <div><div class="proc-step-text">HK allocates room manually</div><div class="proc-step-sub">Verbal assignment to attendant</div><span class="pain-tag">No priority logic</span></div>
        </div>
        <div class="proc-arrow">↓</div>
        <div class="proc-step">
          <div class="proc-step-dot" style="background:#D85A30"></div>
          <div><div class="proc-step-text">Cleaning begins (untracked)</div><div class="proc-step-sub">No start time recorded</div><span class="pain-tag">No SLA defined</span></div>
        </div>
        <div class="proc-arrow">↓</div>
        <div class="proc-step">
          <div class="proc-step-dot" style="background:#D85A30"></div>
          <div><div class="proc-step-text">Inspection (ad hoc)</div><div class="proc-step-sub">Supervisor checks if available</div><span class="pain-tag">Inconsistent</span></div>
        </div>
        <div class="proc-arrow">↓</div>
        <div class="proc-step">
          <div class="proc-step-dot" style="background:#D85A30"></div>
          <div><div class="proc-step-text">HK calls front desk</div><div class="proc-step-sub">Room ready — by phone</div><span class="pain-tag">Delayed notification</span></div>
        </div>
        <div class="proc-arrow">↓</div>
        <div class="proc-step">
          <div class="proc-step-dot" style="background:#888780"></div>
          <div><div class="proc-step-text">Room released for check-in</div><div class="proc-step-sub">Manual PMS update</div></div>
        </div>
      </div>

      <div>
        <div class="proc-col-head" style="background:#E1F5EE;color:#085041">TO-BE — optimised state</div>
        <div class="proc-step">
          <div class="proc-step-dot" style="background:#888780"></div>
          <div><div class="proc-step-text">Guest checks out</div><div class="proc-step-sub">PMS auto-triggers workflow</div></div>
        </div>
        <div class="proc-arrow">↓</div>
        <div class="proc-step">
          <div class="proc-step-dot" style="background:#1D9E75"></div>
          <div><div class="proc-step-text">Digital task auto-assigned</div><div class="proc-step-sub">HK app alert — priority order</div><span class="fix-tag">Instant, logged</span></div>
        </div>
        <div class="proc-arrow">↓</div>
        <div class="proc-step">
          <div class="proc-step-dot" style="background:#1D9E75"></div>
          <div><div class="proc-step-text">Attendant accepts task</div><div class="proc-step-sub">Clock starts — SLA timer on</div><span class="fix-tag">SLA: 12 min clean</span></div>
        </div>
        <div class="proc-arrow">↓</div>
        <div class="proc-step">
          <div class="proc-step-dot" style="background:#1D9E75"></div>
          <div><div class="proc-step-text">Cleaning (tracked live)</div><div class="proc-step-sub">Status: In progress on dashboard</div><span class="fix-tag">Real-time visibility</span></div>
        </div>
        <div class="proc-arrow">↓</div>
        <div class="proc-step">
          <div class="proc-step-dot" style="background:#1D9E75"></div>
          <div><div class="proc-step-text">Attendant marks done</div><div class="proc-step-sub">Supervisor notified instantly</div><span class="fix-tag">SLA: 5 min inspect</span></div>
        </div>
        <div class="proc-arrow">↓</div>
        <div class="proc-step">
          <div class="proc-step-dot" style="background:#1D9E75"></div>
          <div><div class="proc-step-text">Auto-release to front office</div><div class="proc-step-sub">PMS updated, desk alerted</div><span class="fix-tag">Zero phone calls</span></div>
        </div>
        <div class="proc-arrow">↓</div>
        <div class="proc-step">
          <div class="proc-step-dot" style="background:#888780"></div>
          <div><div class="proc-step-text">Room ready for check-in</div><div class="proc-step-sub">Avg. 20 min end-to-end</div></div>
        </div>
      </div>
    </div>
  </div>

  <div id="sla" class="panel">
    <table class="sla-table">
      <thead>
        <tr>
          <th>Stage</th>
          <th>AS-IS time</th>
          <th>TO-BE SLA</th>
          <th>Target</th>
          <th>Owner</th>
          <th>Status</th>
        </tr>
      </thead>
      <tbody id="slaBody"></tbody>
    </table>
  </div>

  <div id="board" class="panel">
    <div class="room-grid" id="roomGrid"></div>
    <div style="display:flex;gap:14px;margin-top:12px;flex-wrap:wrap">
      <div style="display:flex;align-items:center;gap:5px;font-size:11px;color:var(--color-text-secondary)"><span style="width:10px;height:10px;border-radius:50%;background:#D85A30;display:inline-block"></span>Occupied / checkout</div>
      <div style="display:flex;align-items:center;gap:5px;font-size:11px;color:var(--color-text-secondary)"><span style="width:10px;height:10px;border-radius:50%;background:#BA7517;display:inline-block"></span>In progress</div>
      <div style="display:flex;align-items:center;gap:5px;font-size:11px;color:var(--color-text-secondary)"><span style="width:10px;height:10px;border-radius:50%;background:#378ADD;display:inline-block"></span>Inspection</div>
      <div style="display:flex;align-items:center;gap:5px;font-size:11px;color:var(--color-text-secondary)"><span style="width:10px;height:10px;border-radius:50%;background:#1D9E75;display:inline-block"></span>Ready</div>
      <div style="display:flex;align-items:center;gap:5px;font-size:11px;color:var(--color-text-secondary)"><span style="width:10px;height:10px;border-radius:50%;background:#888780;display:inline-block"></span>Occupied (stay)</span></div>
    </div>
    <button onclick="sendPrompt('How do I define SLAs for each housekeeping stage?')" style="margin-top:14px;font-size:12px">Define SLAs for each stage ↗</button>
  </div>

</div>
</div>

<script>
const slaData=[
  {stage:"Checkout trigger",asIs:"5–10 min",toBe:"Instant",pct:100,owner:"PMS / System",ok:true},
  {stage:"Task assignment",asIs:"8–15 min",toBe:"< 1 min",pct:97,owner:"HK supervisor",ok:true},
  {stage:"Room cleaning",asIs:"15–20 min",toBe:"12 min",pct:75,owner:"HK attendant",ok:true},
  {stage:"Inspection",asIs:"5–10 min (if done)",toBe:"3 min",pct:65,owner:"HK supervisor",ok:true},
  {stage:"Status update to front desk",asIs:"3–8 min (phone)",toBe:"Auto (< 30 sec)",pct:98,owner:"System",ok:true},
  {stage:"PMS room release",asIs:"2–5 min (manual)",toBe:"Auto (instant)",pct:99,owner:"System",ok:true},
];

const rooms=[
  {num:"101",status:"ready",guest:"Mehta, A.",detail:"Cleaned 08:42 · inspected 08:49",sla:"On time",slaOk:true},
  {num:"102",status:"in-progress",guest:"Pending",detail:"Attendant: Reena · started 09:10",sla:"7 min elapsed",slaOk:true},
  {num:"103",status:"checkout",guest:"Singh, R. (CO)",detail:"Checkout 08:55 · awaiting assign",sla:"Task pending",slaOk:false},
  {num:"104",status:"inspection",guest:"Pending",detail:"Cleaned 09:05 · supervisor en route",sla:"2 min in inspect",slaOk:true},
  {num:"201",status:"occupied",guest:"Kapoor, S.",detail:"Stay through 12 May",sla:"No action",slaOk:true},
  {num:"202",status:"ready",guest:"Sharma, P.",detail:"Cleaned 07:55 · inspected 08:03",sla:"On time",slaOk:true},
  {num:"203",status:"in-progress",guest:"Pending",detail:"Attendant: James · started 09:15",sla:"2 min elapsed",slaOk:true},
  {num:"204",status:"checkout",guest:"Nair, V. (CO)",detail:"Checkout 09:00 · task assigned",sla:"Task live",slaOk:true},
];

const statusMeta={
  "ready":{pill:"Ready",bg:"#E1F5EE",txt:"#085041",dot:"#1D9E75"},
  "in-progress":{pill:"In progress",bg:"#FAEEDA",txt:"#633806",dot:"#BA7517"},
  "checkout":{pill:"Checkout",bg:"#FAECE7",txt:"#712B13",dot:"#D85A30"},
  "inspection":{pill:"Inspection",bg:"#E6F1FB",txt:"#0C447C",dot:"#378ADD"},
  "occupied":{pill:"Occupied",bg:"#F1EFE8",txt:"#444441",dot:"#888780"},
};

function buildSLA(){
  const tbody=document.getElementById('slaBody');
  slaData.forEach(r=>{
    const tr=document.createElement('tr');
    const barColor=r.pct>=90?'#1D9E75':r.pct>=70?'#BA7517':'#D85A30';
    tr.innerHTML=`
      <td style="font-weight:500">${r.stage}</td>
      <td style="color:var(--color-text-secondary)">${r.asIs}</td>
      <td style="font-weight:500;color:#085041">${r.toBe}</td>
      <td><div class="sla-bar-wrap"><div class="sla-bar" style="width:${r.pct}%;background:${barColor}"></div></div></td>
      <td style="color:var(--color-text-secondary)">${r.owner}</td>
      <td><span class="sla-status" style="background:${r.ok?'#E1F5EE':'#FAECE7'};color:${r.ok?'#085041':'#712B13'}">${r.ok?'Defined':'Needs SLA'}</span></td>`;
    tbody.appendChild(tr);
  });
}

function buildRooms(){
  const grid=document.getElementById('roomGrid');
  rooms.forEach(r=>{
    const m=statusMeta[r.status];
    const card=document.createElement('div');
    card.className='room-card';
    card.innerHTML=`
      <div class="room-number">Room ${r.num}</div>
      <div class="room-status-pill" style="background:${m.bg};color:${m.txt}">${m.pill}</div>
      <div class="room-detail">${r.guest}<br>${r.detail}</div>
      <div class="room-sla" style="color:${r.slaOk?'#1D9E75':'#D85A30'}">${r.sla}</div>`;
    grid.appendChild(card);
  });
}

function showPanel(id,btn){
  document.querySelectorAll('.panel').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.tab').forEach(t=>t.classList.remove('active'));
  document.getElementById(id).classList.add('active');
  btn.classList.add('active');
}

buildSLA();
buildRooms();
</script>
