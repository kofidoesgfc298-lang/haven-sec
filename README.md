[index.html](https://github.com/user-attachments/files/33016432/index.html)

<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>Haven Sec | Control Room</title>
<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
<style>
:root{--bg:#071019;--p:#0d1823;--p2:#102333;--line:#203244;--txt:#e8f0f7;--muted:#8fa3b5;--blue:#28b6ff;--green:#35d07f;--red:#ff6870}
*{box-sizing:border-box}body{margin:0;background:radial-gradient(circle at 20% 0,#10263a,#071019 48%);color:var(--txt);font:14px system-ui,Segoe UI,Arial,sans-serif}button,input,select,textarea{font:inherit}button{cursor:pointer}
.hidden{display:none!important}.login{min-height:100vh;display:grid;place-items:center;padding:20px}.loginbox{width:min(430px,100%);background:#0d1823;border:1px solid var(--line);border-radius:20px;padding:32px;box-shadow:0 20px 60px #0008}.logo{font-weight:900;letter-spacing:2px;font-size:20px}.login h1{font-size:28px;margin:25px 0 5px}.muted{color:var(--muted)}label{display:block;color:var(--muted);font-size:11px;text-transform:uppercase;letter-spacing:1px;margin:14px 0 6px}input,select,textarea{width:100%;background:#08131d;color:var(--txt);border:1px solid var(--line);border-radius:9px;padding:11px;outline:0}textarea{min-height:95px}.primary,.save{border:0;background:var(--blue);color:#00111b;font-weight:800;border-radius:9px;padding:11px 15px}.primary{width:100%;margin-top:15px}.error{margin-top:12px;background:#35171c;border:1px solid #71303a;color:#ff9aa0;padding:10px;border-radius:8px}
.app{min-height:100vh}.side{position:fixed;inset:0 auto 0 0;width:245px;background:#08131d;border-right:1px solid var(--line);padding:22px 14px}.brand{padding:0 10px 22px;border-bottom:1px solid var(--line)}.brand small{display:block;color:var(--muted);margin-top:5px}.nav{margin-top:15px}.nav button{width:100%;text-align:left;background:none;border:0;color:#9fb1c0;padding:12px;border-radius:8px}.nav button:hover,.nav button.active{background:#102536;color:#fff}.nav i{display:inline-block;width:27px;font-style:normal}.main{margin-left:245px}.top{height:75px;position:sticky;top:0;z-index:5;background:#071019eF;border-bottom:1px solid var(--line);display:flex;justify-content:space-between;align-items:center;padding:0 28px;backdrop-filter:blur(10px)}.top h2{margin:0;font-size:19px}.user{display:flex;align-items:center;gap:10px}.avatar{width:36px;height:36px;border-radius:50%;display:grid;place-items:center;background:#12344b;color:var(--blue);font-weight:800}.logout,.action{background:#102536;border:1px solid #28445a;color:#dceaf4;border-radius:8px;padding:8px 11px}.content{padding:28px;max-width:1500px;margin:auto}.hero{display:flex;justify-content:space-between;gap:15px;align-items:end;margin-bottom:22px}.hero h1{margin:0 0 5px;font-size:28px}.actions{display:flex;gap:8px;flex-wrap:wrap}.cards{display:grid;grid-template-columns:repeat(4,1fr);gap:14px}.card,.panel{background:#0b1722;border:1px solid var(--line);border-radius:14px}.card{padding:17px}.metric{font-size:30px;font-weight:850;margin:7px 0}.label{color:var(--muted);font-size:11px;text-transform:uppercase;letter-spacing:1px}.grid{display:grid;grid-template-columns:1.5fr 1fr;gap:15px;margin-top:15px}.panelhead{padding:15px 17px;border-bottom:1px solid var(--line);display:flex;justify-content:space-between}.panelhead h3{margin:0;font-size:15px}.tablewrap{overflow:auto}.table{width:100%;border-collapse:collapse;min-width:600px}.table th,.table td{padding:11px 13px;border-bottom:1px solid #172938;text-align:left;font-size:12px}.table th{color:#7890a2;text-transform:uppercase;font-size:10px}.activity{padding:5px 17px}.act{padding:12px 0;border-bottom:1px solid #172938}.act small{display:block;color:var(--muted);margin-top:3px}.page{display:none}.page.active{display:block}.form{padding:18px}.formgrid{display:grid;grid-template-columns:1fr 1fr;gap:0 16px}.full{grid-column:1/-1}.formactions{display:flex;justify-content:flex-end;gap:8px;margin-top:10px}.cancel{background:transparent;color:#b8c7d3;border:1px solid var(--line);border-radius:8px;padding:10px 15px}.notice{background:#0d2535;border:1px solid #1e4a65;border-radius:8px;padding:11px;margin:15px 17px;color:#bfe8ff}
@media(max-width:900px){.side{width:72px}.brand strong,.brand small,.nav span{display:none}.nav button{text-align:center}.main{margin-left:72px}.cards{grid-template-columns:1fr 1fr}.grid{grid-template-columns:1fr}}
@media(max-width:600px){.top{padding:0 13px}.content{padding:14px}.hero{display:block}.hero .actions{margin-top:15px}.formgrid{grid-template-columns:1fr}.full{grid-column:auto}.cards{gap:8px}.card{padding:13px}}
</style>
</head>
<body>
<div id="login" class="login"><div class="loginbox">
<div class="logo">⬡ HAVEN SEC</div><h1>Security Control Room</h1><p class="muted">Sign in to the shared Haven Sec system.</p>
<form id="loginForm"><label>Email</label><input id="email" type="email" required autocomplete="username"><label>Password</label><input id="password" type="password" required autocomplete="current-password"><button class="primary">Sign in</button><div id="loginError" class="error hidden"></div></form>
</div></div>

<div id="app" class="app hidden">
<aside class="side"><div class="brand"><strong>⬡ HAVEN SEC</strong><small>CONTROL ROOM</small></div>
<nav class="nav">
<button class="active" data-page="dashboard"><i>▣</i><span>Dashboard</span></button>
<button data-page="incidents"><i>🚨</i><span>Incidents</span></button>
<button data-page="lost_property"><i>▢</i><span>Lost Property</span></button>
<button data-page="ramtech_alarms"><i>🔔</i><span>Ramtech Alarms</span></button>
<button data-page="patrols"><i>◉</i><span>Patrols</span></button>
<button data-page="handover_notes"><i>☷</i><span>Handover Notes</span></button>
<button data-page="reports"><i>▤</i><span>Reports</span></button>
</nav></aside>
<main class="main"><header class="top"><div><h2 id="title">Dashboard</h2><small class="muted">Live shared database</small></div><div class="user"><div class="avatar" id="avatar">HS</div><span id="who">Officer</span><button id="logout" class="logout">Logout</button></div></header>
<div class="content">

<section id="dashboard" class="page active"><div class="hero"><div><h1>Security Overview</h1><p class="muted">Shared control-room activity.</p></div><div class="actions"><button class="action" data-open="incidents">+ Incident</button><button class="action" data-open="lost_property">+ Lost Property</button><button class="action" data-open="ramtech_alarms">+ Alarm</button><button class="action" data-open="patrols">+ Patrol</button></div></div>
<div class="cards"><div class="card"><div class="label">Incidents</div><div id="n1" class="metric">—</div></div><div class="card"><div class="label">Lost Property</div><div id="n2" class="metric">—</div></div><div class="card"><div class="label">Ramtech Alarms</div><div id="n3" class="metric">—</div></div><div class="card"><div class="label">Patrols</div><div id="n4" class="metric">—</div></div></div>
<div class="grid"><div class="panel"><div class="panelhead"><h3>Recent Logs</h3><span class="muted">Newest first</span></div><div class="tablewrap"><table class="table"><thead><tr><th>Type</th><th>Time</th><th>Location</th><th>Status</th></tr></thead><tbody id="recent"></tbody></table></div></div><div class="panel"><div class="panelhead"><h3>Latest Activity</h3><span class="muted">Shared</span></div><div id="activity" class="activity"></div></div></div></section>

<div id="incidents" class="page"><div class="panel"><div class="panelhead"><h3>Log Incident</h3><span class="muted">Shared online</span></div><form class="form" data-table="incidents"><div class="formgrid">
<div><label>Incident time</label><input name="incident_time" type="datetime-local" required></div><div><label>Location</label><input name="location" required></div><div><label>Incident type</label><input name="incident_type" required placeholder="Theft, disorder, damage..."></div><div><label>Priority</label><select name="priority"><option>Normal</option><option>High</option><option>Critical</option></select></div><div class="full"><label>Description</label><textarea name="description" required></textarea></div><div class="full"><label>Action taken</label><textarea name="action_taken"></textarea></div></div><div class="formactions"><button type="button" class="cancel" data-open="dashboard">Cancel</button><button class="save">Save Incident</button></div></form></div></div> <div class="panel">
  <div class="panelhead">
    <h3>Saved Incidents</h3>
    <span class="muted">Click an incident to view details</span>
  </div>
  <div id="incidentList" class="incident-list">
    <div class="muted" style="padding:18px">No incidents loaded yet.</div>
  </div>
</div>

<

<div id="lost_property" class="page"><div class="panel"><div class="panelhead"><h3>Log Lost Property</h3></div><form class="form" data-table="lost_property"><div class="formgrid"><div><label>Found time</label><input name="found_time" type="datetime-local" required></div><div><label>Location</label><input name="location" required></div><div><label>Item description</label><input name="item_description" required></div><div><label>Found by</label><input name="found_by"></div><div><label>Stored location</label><input name="stored_location"></div><div><label>Reference number</label><input name="reference_number"></div><div><label>Status</label><select name="status"><option>Stored</option><option>Returned</option><option>Disposed</option></select></div></div><div class="formactions"><button type="button" class="cancel" data-open="dashboard">Cancel</button><button class="save">Save Lost Property</button></div></form></div></div>

<div id="ramtech_alarms" class="page"><div class="panel"><div class="panelhead"><h3>Log Ramtech Alarm</h3></div><form class="form" data-table="ramtech_alarms"><div class="formgrid"><div><label>Alarm time</label><input name="alarm_time" type="datetime-local" required></div><div><label>Location</label><input name="location" required></div><div><label>Alarm type</label><input name="alarm_type" required></div><div><label>Status</label><select name="status"><option>Open</option><option>Attended</option><option>Closed</option></select></div><div class="full"><label>Description</label><textarea name="description"></textarea></div><div class="full"><label>Action taken</label><textarea name="action_taken"></textarea></div></div><div class="formactions"><button type="button" class="cancel" data-open="dashboard">Cancel</button><button class="save">Save Alarm</button></div></form></div></div>

<div id="patrols" class="page"><div class="panel"><div class="panelhead"><h3>Log Patrol</h3></div><form class="form" data-table="patrols"><div class="formgrid"><div><label>Patrol time</label><input name="patrol_time" type="datetime-local" required></div><div><label>Area</label><input name="area" required></div><div><label>Officer name</label><input name="officer_name"></div><div><label>Result</label><select name="result"><option>All clear</option><option>Issue found</option><option>Unable to complete</option></select></div><div class="full"><label>Notes</label><textarea name="notes"></textarea></div></div><div class="formactions"><button type="button" class="cancel" data-open="dashboard">Cancel</button><button class="save">Save Patrol</button></div></form></div></div>

<div id="handover_notes" class="page"><div class="panel"><div class="panelhead"><h3>Handover Note</h3></div><form class="form" data-table="handover_notes"><div class="formgrid"><div><label>Note time</label><input name="note_time" type="datetime-local" required></div><div><label>Officer name</label><input name="officer_name"></div><div><label>Shift</label><select name="shift"><option>Day</option><option>Night</option><option>Other</option></select></div><div><label>Priority</label><select name="priority"><option>Normal</option><option>High</option><option>Critical</option></select></div><div class="full"><label>Handover note</label><textarea name="note" required></textarea></div></div><div class="formactions"><button type="button" class="cancel" data-open="dashboard">Cancel</button><button class="save">Save Handover</button></div></form></div></div>

<div id="reports" class="page"><div class="panel"><div class="panelhead"><h3>Reports & Export</h3></div><div class="notice">Export records your signed-in account can read as CSV files.</div><div class="actions" style="padding:0 17px 18px"><button class="action" data-export="incidents">Incidents CSV</button><button class="action" data-export="lost_property">Lost Property CSV</button><button class="action" data-export="ramtech_alarms">Alarms CSV</button><button class="action" data-export="patrols">Patrols CSV</button><button class="action" data-export="handover_notes">Handover CSV</button></div></div></div>

</div></main></div>

<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

<script>
const SUPABASE_URL = 'https://wjvlnkvufgiajhkyetih.supabase.co';
const SUPABASE_KEY = 'sb_publishable_nmS8qXIcyCpc6taGs9sKyA_6kw_uUKG';
const db = window.supabase.createClient(SUPABASE_URL, SUPABASE_KEY);
const names={incidents:'Incidents',lost_property:'Lost Property',ramtech_alarms:'Ramtech Alarms',patrols:'Patrols',handover_notes:'Handover Notes'};
const time={incidents:'incident_time',lost_property:'found_time',ramtech_alarms:'alarm_time',patrols:'patrol_time',handover_notes:'note_time'};
let user=null,cache={};

const $=id=>document.getElementById(id);
function localNow(){let d=new Date();d.setMinutes(d.getMinutes()-d.getTimezoneOffset());return d.toISOString().slice(0,16)}
function defaults(){document.querySelectorAll('input[type=datetime-local]').forEach(x=>{if(!x.value)x.value=localNow()})}
function openPage(p){document.querySelectorAll('.page').forEach(x=>x.classList.remove('active'));$(p).classList.add('active');document.querySelectorAll('.nav button').forEach(x=>x.classList.toggle('active',x.dataset.page===p));$('title').textContent=p==='dashboard'?'Dashboard':names[p]||p;defaults();scrollTo(0,0);if(p==='dashboard')refresh()}
  $('activity').innerHTML = 'Activity loaded';
loadIncidents():
function msg(t,good=true){let x=document.createElement('div');x.textContent=t;x.style='position:fixed;right:18px;bottom:18px;background:'+(good?'#123a2a':'#41191e')+';border:1px solid #345;padding:12px;border-radius:9px;z-index:99';document.body.appendChild(x);setTimeout(()=>x.remove(),3000)}
document.querySelectorAll('.nav button').forEach(x=>x.onclick=()=>openPage(x.dataset.page));
document.querySelectorAll('[data-open]').forEach(x=>x.onclick=()=>openPage(x.dataset.open));

$('loginForm').onsubmit=async e=>{e.preventDefault();$('loginError').classList.add('hidden');let {error}=await db.auth.signInWithPassword({email:$('email').value.trim(),password:$('password').value});if(error){$('loginError').textContent=error.message;$('loginError').classList.remove('hidden')}};
$('logout').onclick=()=>db.auth.signOut();
  async function loadIncidents(){
  let {data,error}=await db.from('incidents').select('*').order('incident_time',{ascending:false});
  if(error){
    console.error('Incident load error:',error);
    return;
  }

  let box=document.getElementById('incidentList');
  if(!box)return;

  if(!data.length){
    box.innerHTML='<div class="muted" style="padding:18px">No incidents yet.</div>';
    return;
  }

  box.innerHTML=data.map(x=>`
    <div class="incident-row" style="padding:14px;border-bottom:1px solid #333;cursor:pointer" data-id="${x.id}">
      <b>${x.incident_type||'Incident'}</b><br>
      <small>${x.location||'—'} · ${x.incident_time?new Date(x.incident_time).toLocaleString():'—'}</small>
    </div>
  `).join('');

  box.querySelectorAll('.incident-row').forEach(row=>{
  row.onclick=()=>{
    let x=data.find(i=>i.id===row.dataset.id);
    if(!x)return;

    alert(
      'INCIDENT DETAILS\n\n'+
      'Type: '+(x.incident_type||'—')+'\n'+
      'Time: '+(x.incident_time?new Date(x.incident_time).toLocaleString():'—')+'\n'+
      'Location: '+(x.location||'—')+'\n'+
      'Priority: '+(x.priority||'Normal')+'\n\n'+
      'Description:\n'+(x.description||'—')+'\n\n'+
      'Action Taken:\n'+(x.action_taken||'—')
    );
  };
});
    
}

  let {data,error}=await db.from('incidents').select('*').order('incident_time',{ascending:false});
  if(error){
    console.error('Incident load error:',error);
    return;
  }

  let box=$('incidentList');
  if(!box)return;

  if(!data.length){
    box.innerHTML='<div class="muted" style="padding:18px">No incidents yet.</div>';
    return;
  }

  box.innerHTML=data.map(x=>`
    <div class="incident-row" style="padding:14px;border-bottom:1px solid #333;cursor:pointer" data-id="${x.id}">
      <b>${x.incident_type||'Incident'}</b><br>
      <small>${x.location||'—'} · ${x.incident_time?new Date(x.incident_time).toLocaleString():'—'}</small>
    </div>
  `).join('');

  box.querySelectorAll('.incident-row').forEach(row=>{
    row.onclick=()=>{
      let x=data.find(i=>i.id===row.dataset.id);
      if(!x)return;

      alert(
        'INCIDENT DETAILS\n\n'+
        'Type: '+(x.incident_type||'—')+'\n'+
        'Time: '+(x.incident_time?new Date(x.incident_time).toLocaleString():'—')+'\n'+
        'Location: '+(x.location||'—')+'\n'+
        'Priority: '+(x.priority||'Normal')+'\n\n'+
        'Description:\n'+(x.description||'—')+'\n\n'+
        'Action Taken:\n'+(x.action_taken||'—')
      );
    };
  });
}
async function loadIncidents(){
  let {data,error}=await db.from('incidents').select('*').order('incident_time',{ascending:false});
  if(error){
    console.error('Incident load error:',error);
    return;
  }

  let box=document.getElementById('incidentList');
  if(!box)return;

  if(!data.length){
    box.innerHTML='<div class="muted" style="padding:18px">No incidents yet.</div>';
    return;
  }

  box.innerHTML=data.map(x=>`
    <div class="incident-row" style="padding:14px;border-bottom:1px solid #333;cursor:pointer">
      <b>${x.incident_type||'Incident'}</b><br>
      <small>${x.location||'—'} · ${x.incident_time?new Date(x.incident_time).toLocaleString():'—'}</small>
    </div>
  `).join('');
}
  async function rows(t){let {data,error}=await db.from(t).select('*').order('created_at',{ascending:false}).limit(100);if(error){console.error(error);return[]}return data||[]}
async function refresh(){loadIncidents();
 let [i,l,a,p,h]=await Promise.all(Object.keys(names).map(rows));cache={incidents:i,lost_property:l,ramtech_alarms:a,patrols:p,handover_notes:h};
 $('n1').textContent=i.length;$('n2').textContent=l.length;$('n3').textContent=a.length;$('n4').textContent=p.length;
 let all=[...i.map(x=>({t:'Incident',d:x[time.incidents]||x.created_at,l:x.location,s:x.status||'Open'})),...l.map(x=>({t:'Lost Property',d:x[time.lost_property]||x.created_at,l:x.location,s:x.status||'Stored'})),...a.map(x=>({t:'Ramtech Alarm',d:x[time.ramtech_alarms]||x.created_at,l:x.location,s:x.status||'Open'})),...p.map(x=>({t:'Patrol',d:x[time.patrols]||x.created_at,l:x.area,s:x.result||'Logged'})),...h.map(x=>({t:'Handover',d:x[time.handover_notes]||x.created_at,l:'—',s:x.priority||'Normal'}))].sort((x,y)=>new Date(y.d)-new Date(x.d));
 $('recent').innerHTML=all.length?all.slice(0,10).map(x=>`<tr><td>${x.t}</td><td>${new Date(x.d).toLocaleString()}</td><td>${x.l||'—'}</td><td>${x.s||'—'}</td></tr>`).join(''):`<tr><td colspan="4">No logs yet.</td></tr>`;
 $('activity').innerHTML = 'Activity loaded';
}
document.querySelectorAll('[data-export]').forEach(b=>b.onclick=async()=>{let t=b.dataset.export,r=cache[t]||await rows(t);if(!r.length){msg('No records to export',false);return}let c=[...new Set(r.flatMap(x=>Object.keys(x)))];let csv=[c.join(','),...r.map(x=>c.map(k=>`"${String(x[k]??'').replaceAll('"','""')}"`).join(','))].join('\\n');let a=document.createElement('a');a.href=URL.createObjectURL(new Blob([csv],{type:'text/csv'}));a.download='haven-sec-'+t+'.csv';a.click()});

async function start(){let {data:{session}}=await db.auth.getSession();if(session?.user){user=session.user;show()}else{$('login').classList.remove('hidden');$('app').classList.add('hidden')}db.auth.onAuthStateChange((e,s)=>{if(s?.user){user=s.user;show()}else if(e==='SIGNED_OUT'){user=null;$('login').classList.remove('hidden');$('app').classList.add('hidden')}})}
function show(){$('login').classList.add('hidden');$('app').classList.remove('hidden');$('who').textContent=user.email;$('avatar').textContent=(user.email||'HS').slice(0,2).toUpperCase();defaults();refresh()}
start();
</script>
</body></html>
