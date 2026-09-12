<DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0">
<meta name="theme-color" content="#6c5ce7">
<title>StudySphere | Student Productivity</title>
<style>
:root{--bg:#f5f6fb;--panel:#fff;--text:#171827;--muted:#74778b;--line:#e9eaf1;--primary:#6c5ce7;--primary2:#8e7cff;--soft:#eeebff;--good:#20b486;--warn:#f59f00;--danger:#e05252;--shadow:0 14px 40px rgba(33,32,70,.08)}
[data-theme=dark]{--bg:#0c0d17;--panel:#151624;--text:#f5f5fa;--muted:#9a9bae;--line:#282a3a;--soft:#211e3c;--shadow:0 14px 40px rgba(0,0,0,.28)}
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:Inter,system-ui,-apple-system,Segoe UI,Arial,sans-serif;background:var(--bg);color:var(--text);min-height:100vh}
button,input,textarea,select{font:inherit}button{cursor:pointer;border:0}
.app{display:flex;min-height:100vh}.sidebar{width:250px;background:var(--panel);border-right:1px solid var(--line);padding:22px 15px;position:fixed;left:0;top:0;bottom:0;z-index:20}
.brand{display:flex;align-items:center;gap:11px;padding:5px 10px 28px;font-weight:800;font-size:20px}.logo{width:38px;height:38px;border-radius:13px;background:linear-gradient(135deg,#6c5ce7,#a66cff);display:grid;place-items:center;color:white;font-weight:900;box-shadow:0 8px 18px #6c5ce733}
.nav{display:grid;gap:5px}.nav button{background:transparent;color:var(--muted);padding:12px 13px;border-radius:12px;text-align:left;display:flex;align-items:center;gap:12px;font-weight:650}.nav button:hover,.nav button.active{background:var(--soft);color:var(--primary)}.ico{width:22px;text-align:center}
.sidebar-bottom{position:absolute;bottom:20px;left:15px;right:15px}.theme-btn{width:100%;padding:11px;border:1px solid var(--line);border-radius:12px;background:var(--panel);color:var(--text)}
main{margin-left:250px;width:calc(100% - 250px);padding:25px 30px 80px}.top{display:flex;align-items:center;justify-content:space-between;margin-bottom:26px}.top h1{font-size:28px}.top p{color:var(--muted);margin-top:4px}.avatar{width:43px;height:43px;border-radius:50%;background:linear-gradient(135deg,#6c5ce7,#9f7aea);display:grid;place-items:center;color:#fff;font-weight:800}
.page{display:none;animation:fade .22s ease}.page.active{display:block}@keyframes fade{from{opacity:.3;transform:translateY(5px)}to{opacity:1;transform:none}}
.grid{display:grid;gap:18px}.g4{grid-template-columns:repeat(4,1fr)}.g3{grid-template-columns:repeat(3,1fr)}.g2{grid-template-columns:repeat(2,1fr)}
.card{background:var(--panel);border:1px solid var(--line);border-radius:18px;padding:20px;box-shadow:var(--shadow)}.card h3{margin-bottom:8px}.muted{color:var(--muted)}.big{font-size:30px;font-weight:850}.stat{display:flex;justify-content:space-between;align-items:center}.stat-icon{width:43px;height:43px;border-radius:13px;background:var(--soft);display:grid;place-items:center;font-size:20px}
.progress{height:9px;background:var(--line);border-radius:20px;overflow:hidden}.bar{height:100%;background:linear-gradient(90deg,#6c5ce7,#9d7cff);border-radius:20px}
.hero{background:linear-gradient(135deg,#6152db,#8d70ff);color:#fff;border:0;padding:28px;position:relative;overflow:hidden}.hero:after{content:"";position:absolute;width:180px;height:180px;border-radius:50%;right:-45px;top:-70px;background:#ffffff18}.hero p{color:#eeeaff}.hero .btn{background:#fff;color:#5d4ed2}
.btn{background:var(--primary);color:#fff;padding:10px 15px;border-radius:11px;font-weight:750}.btn.secondary{background:var(--soft);color:var(--primary)}.btn.ghost{background:transparent;color:var(--muted);border:1px solid var(--line)}
.actions{display:flex;gap:8px;flex-wrap:wrap}.section-head{display:flex;justify-content:space-between;align-items:center;margin:24px 0 13px}.section-head h2{font-size:19px}
.list{display:grid;gap:10px}.item{display:flex;align-items:center;gap:12px;padding:13px;border:1px solid var(--line);border-radius:13px}.item-main{flex:1}.item small{color:var(--muted)}.check{width:22px;height:22px;border:2px solid #aaa;border-radius:7px;background:transparent}.check.done{background:var(--good);border-color:var(--good);color:white}.strike{text-decoration:line-through;opacity:.55}
.tag{display:inline-block;padding:5px 9px;border-radius:20px;background:var(--soft);color:var(--primary);font-size:12px;font-weight:750}
input,textarea,select{width:100%;padding:11px 12px;border:1px solid var(--line);border-radius:11px;background:var(--panel);color:var(--text);outline:none}input:focus,textarea:focus,select:focus{border-color:var(--primary)}textarea{min-height:120px;resize:vertical}.form{display:grid;gap:12px}.row{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.note{min-height:150px}.note h3{margin-bottom:8px}.note p{white-space:pre-wrap;color:var(--muted);line-height:1.5}.note .actions{margin-top:15px}
.task-form{display:grid;grid-template-columns:1.5fr 1fr 1fr auto;gap:9px}.search{max-width:300px}
.subject{position:relative}.subject .progress{margin:15px 0 8px}.subject-top{display:flex;justify-content:space-between}.empty{text-align:center;padding:35px;color:var(--muted)}
.timer{display:grid;place-items:center;padding:35px}.clock{font-size:74px;font-weight:900;letter-spacing:2px;margin:15px}.timer-mode{color:var(--primary);font-weight:800}.timer-ring{width:250px;height:250px;border-radius:50%;display:grid;place-items:center;border:12px solid var(--soft);box-shadow:inset 0 0 0 2px var(--line)}
.goal{display:grid;gap:10px}.goal-top{display:flex;justify-content:space-between;gap:10px}.goal-percent{font-weight:800;color:var(--primary)}
.tip{min-height:170px}.tip-icon{font-size:30px;margin-bottom:12px}
.chart{height:190px;display:flex;align-items:end;gap:12px;padding:18px 8px 5px}.col{flex:1;display:grid;grid-template-rows:1fr auto;gap:7px;height:100%;align-items:end}.colbar{background:linear-gradient(180deg,#8e7cff,#6c5ce7);border-radius:7px 7px 3px 3px;min-height:8px}.col span{text-align:center;color:var(--muted);font-size:11px}
.mobile-nav{display:none}
.modal{position:fixed;inset:0;background:#0008;display:none;align-items:center;justify-content:center;padding:20px;z-index:50}.modal.show{display:flex}.modal-box{background:var(--panel);border:1px solid var(--line);border-radius:18px;width:min(500px,100%);padding:22px}.modal-head{display:flex;justify-content:space-between;align-items:center;margin-bottom:15px}
.toast{position:fixed;bottom:22px;right:22px;background:#171827;color:#fff;padding:12px 16px;border-radius:12px;display:none;z-index:60;box-shadow:var(--shadow)}.toast.show{display:block}
@media(max-width:950px){.sidebar{display:none}main{margin-left:0;width:100%;padding:20px 16px 88px}.g4{grid-template-columns:repeat(2,1fr)}.g3{grid-template-columns:1fr 1fr}.mobile-nav{display:flex;position:fixed;bottom:0;left:0;right:0;height:65px;background:var(--panel);border-top:1px solid var(--line);z-index:30;justify-content:space-around;padding:7px}.mobile-nav button{background:transparent;color:var(--muted);font-size:11px;display:grid;place-items:center;gap:2px}.mobile-nav button.active{color:var(--primary)}}
@media(max-width:620px){.top h1{font-size:23px}.g4,.g3,.g2{grid-template-columns:1fr}.row{grid-template-columns:1fr}.task-form{grid-template-columns:1fr}.search{max-width:none}.hero{padding:22px}.clock{font-size:57px}.timer-ring{width:220px;height:220px}}
</style>
</head>
<body>
<div class="app">
<aside class="sidebar">
  <div class="brand"><div class="logo">S</div>StudySphere</div>
  <nav class="nav" id="sideNav"></nav>
  <div class="sidebar-bottom"><button class="theme-btn" onclick="toggleTheme()">🌙 Toggle Theme</button></div>
</aside>

<main>
<header class="top">
  <div><h1 id="pageTitle">Dashboard</h1><p id="dateText"></p></div>
  <div class="avatar" id="avatar">S</div>
</header>

<section class="page active" id="dashboard">
  <div class="card hero"><div style="position:relative;z-index:2"><p>Welcome back 👋</p><h2 id="welcome" style="font-size:30px;margin:6px 0 9px">Student</h2><p>Keep learning, keep growing. Your next small step matters.</p><div class="actions" style="margin-top:18px"><button class="btn" onclick="showPage('tasks')">View Tasks</button><button class="btn secondary" onclick="showPage('timer')">Start Focus</button></div></div></div>
  <div class="grid g4" style="margin-top:18px">
    <div class="card stat"><div><div class="muted">Tasks Done</div><div class="big" id="statTasks">0</div></div><div class="stat-icon">✅</div></div>
    <div class="card stat"><div><div class="muted">Subjects</div><div class="big" id="statSubjects">0</div></div><div class="stat-icon">📚</div></div>
    <div class="card stat"><div><div class="muted">Study Hours</div><div class="big" id="statHours">0</div></div><div class="stat-icon">⏱️</div></div>
    <div class="card stat"><div><div class="muted">Goals Done</div><div class="big" id="statGoals">0</div></div><div class="stat-icon">🎯</div></div>
  </div>
  <div class="grid g2">
    <div><div class="section-head"><h2>Today's Tasks</h2><button class="btn secondary" onclick="showPage('tasks')">See all</button></div><div class="card" id="dashTasks"></div></div>
    <div><div class="section-head"><h2>Weekly Focus</h2><button class="btn secondary" onclick="showPage('progress')">Progress</button></div><div class="card"><div class="muted">Study consistency</div><div class="big" id="weekPercent" style="margin:7px 0 12px">0%</div><div class="progress"><div class="bar" id="weekBar" style="width:0%"></div></div><p class="muted" style="margin-top:12px">Build a routine by completing focused sessions.</p></div></div>
  </div>
</section>

<section class="page" id="subjects">
  <div class="section-head"><h2>Your Subjects</h2><button class="btn" onclick="openSubject()">＋ Add Subject</button></div>
  <div class="grid g3" id="subjectList"></div>
</section>

<section class="page" id="notes">
  <div class="section-head"><h2>Notes</h2><button class="btn" onclick="openNote()">＋ New Note</button></div>
  <input class="search" id="noteSearch" placeholder="🔎 Search notes..." oninput="renderNotes()">
  <div class="grid g3" id="noteList" style="margin-top:16px"></div>
</section>

<section class="page" id="tasks">
  <div class="section-head"><h2>Tasks & Assignments</h2></div>
  <div class="card">
    <div class="task-form"><input id="taskText" placeholder="Task title"><select id="taskPriority"><option>High</option><option selected>Medium</option><option>Low</option></select><input id="taskDue" type="date"><button class="btn" onclick="addTask()">Add</button></div>
  </div>
  <div class="section-head"><h2>My Tasks</h2><input class="search" id="taskSearch" placeholder="Search..." oninput="renderTasks()"></div>
  <div class="card" id="taskList"></div>
</section>

<section class="page" id="planner">
  <div class="section-head"><h2>Study Planner</h2><button class="btn" onclick="openPlan()">＋ Add Session</button></div>
  <div class="card"><div class="grid g3" id="planList"></div></div>
</section>

<section class="page" id="timer">
  <div class="card timer">
    <div class="timer-mode" id="timerMode">FOCUS SESSION</div>
    <div class="timer-ring"><div class="clock" id="clock">25:00</div></div>
    <div class="actions"><button class="btn" onclick="startTimer()">▶ Start</button><button class="btn secondary" onclick="pauseTimer()">⏸ Pause</button><button class="btn ghost" onclick="resetTimer()">↺ Reset</button></div>
    <p class="muted" style="margin-top:16px;text-align:center">25 minutes focus • 5 minutes break</p>
  </div>
</section>

<section class="page" id="progress">
  <div class="grid g3">
    <div class="card"><div class="muted">Completed Tasks</div><div class="big" id="pTasks">0</div></div>
    <div class="card"><div class="muted">Focus Sessions</div><div class="big" id="pSessions">0</div></div>
    <div class="card"><div class="muted">Total Study Hours</div><div class="big" id="pHours">0</div></div>
  </div>
  <div class="section-head"><h2>Study Activity</h2></div>
  <div class="card"><div class="chart" id="chart"></div></div>
  <div class="section-head"><h2>Subject Progress</h2></div>
  <div class="card" id="progressSubjects"></div>
</section>

<section class="page" id="goals">
  <div class="section-head"><h2>My Goals</h2><button class="btn" onclick="openGoal()">＋ Add Goal</button></div>
  <div class="grid g2" id="goalList"></div>
</section>

<section class="page" id="hub">
  <div class="card hero"><h2>Study Hub 💡</h2><p style="margin-top:8px">Simple techniques to make your study sessions more effective.</p></div>
  <div class="section-head"><h2>Study Techniques</h2></div><div class="grid g3" id="tips"></div>
</section>

<section class="page" id="profile">
  <div class="card" style="max-width:700px">
    <h2 style="margin-bottom:5px">Profile & Settings</h2><p class="muted" style="margin-bottom:20px">Your information is stored only in this browser.</p>
    <div class="form"><div class="row"><div><label>Name</label><input id="profileName"></div><div><label>Student ID</label><input id="profileId"></div></div><div class="row"><div><label>Course</label><input id="profileCourse"></div><div><label>Semester</label><input id="profileSem"></div></div><div><label>College</label><input id="profileCollege"></div><button class="btn" onclick="saveProfile()">Save Profile</button><button class="btn ghost" onclick="resetData()">Reset Demo Data</button></div>
  </div>
</section>
</main>
</div>
<nav class="mobile-nav" id="mobileNav"></nav>
<div class="modal" id="modal"><div class="modal-box"><div class="modal-head"><h2 id="modalTitle">Add</h2><button class="btn ghost" onclick="closeModal()">✕</button></div><div id="modalBody"></div></div></div>
<div class="toast" id="toast"></div>

<script>
const navItems=[
['dashboard','🏠','Dashboard'],['subjects','📚','Subjects'],['notes','📝','Notes'],['tasks','✅','Tasks'],['planner','📅','Planner'],['timer','⏱️','Focus Timer'],['progress','📊','Progress'],['goals','🎯','Goals'],['hub','💡','Study Hub'],['profile','👤','Profile']
];
const tips=[
['🍅','Pomodoro','Study for 25 minutes, then take a short break. Repeat to keep your attention fresh.'],
['🧠','Active Recall','Close your notes and try to explain the topic from memory before checking your answer.'],
['🔁','Spaced Practice','Review difficult topics over several days instead of cramming everything at once.'],
['✍️','Blurting','Write everything you remember about a topic, then compare it with your notes.'],
['🎯','Small Goals','Turn a big chapter into small tasks you can finish one by one.'],
['📵','Distraction Block','Keep unnecessary notifications away during a focused study session.']
];
let data=JSON.parse(localStorage.getItem('studysphere')||'null')||{
profile:{name:'Student',id:'',course:'',sem:'',college:''},
subjects:[{name:'Mathematics',teacher:'',credits:4,progress:65},{name:'Programming',teacher:'',credits:4,progress:78},{name:'Communication',teacher:'',credits:3,progress:52}],
tasks:[{text:'Complete programming practice',priority:'High',due:'',done:false},{text:'Revise mathematics notes',priority:'Medium',due:'',done:false}],
notes:[{title:'Quick Revision',body:'Add your important formulas, definitions and reminders here.',subject:'General'}],
plans:[{day:'Monday',time:'5:00 PM',subject:'Programming',duration:'60 min'},{day:'Tuesday',time:'6:00 PM',subject:'Mathematics',duration:'45 min'}],
goals:[{text:'Finish semester revision',target:10,current:4}],
sessions:0,hours:0,activity:[2,3,1,4,2,5,3]
};
function save(){localStorage.setItem('studysphere',JSON.stringify(data));renderAll()}
function esc(s){return String(s||'').replace(/[&<>"']/g,m=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#039;'}[m]))}
function buildNav(){['sideNav','mobileNav'].forEach(id=>{document.getElementById(id).innerHTML=navItems.map((n,i)=>`<button data-page="${n[0]}" onclick="showPage('${n[0]}')"><span class="ico">${n[1]}</span><span>${n[2]}</span></button>`).join('')})}
function showPage(id){document.querySelectorAll('.page').forEach(p=>p.classList.toggle('active',p.id===id));document.querySelectorAll('[data-page]').forEach(b=>b.classList.toggle('active',b.dataset.page===id));let n=navItems.find(x=>x[0]===id);document.getElementById('pageTitle').textContent=n?n[2]:'Dashboard';window.scrollTo({top:0,behavior:'smooth'});if(id==='profile')fillProfile()}
function renderHeader(){let p=data.profile;document.getElementById('welcome').textContent=p.name||'Student';document.getElementById('avatar').textContent=(p.name||'S').trim()[0].toUpperCase();document.getElementById('dateText').textContent=new Date().toLocaleDateString(undefined,{weekday:'long',month:'long',day:'numeric',year:'numeric'})}
function renderDashboard(){let done=data.tasks.filter(x=>x.done).length;document.getElementById('statTasks').textContent=done;document.getElementById('statSubjects').textContent=data.subjects.length;document.getElementById('statHours').textContent=data.hours.toFixed(1);document.getElementById('statGoals').textContent=data.goals.filter(g=>g.current>=g.target).length;let pct=Math.min(100,Math.round((done/Math.max(1,data.tasks.length))*100));document.getElementById('weekPercent').textContent=pct+'%';document.getElementById('weekBar').style.width=pct+'%';let t=data.tasks.slice(0,4);document.getElementById('dashTasks').innerHTML=t.length?t.map((x,i)=>`<div class="item"><button class="check ${x.done?'done':''}" onclick="toggleTask(${data.tasks.indexOf(x)})">${x.done?'✓':''}</button><div class="item-main ${x.done?'strike':''}"><b>${esc(x.text)}</b><br><small>${esc(x.priority)} priority${x.due?' • '+esc(x.due):''}</small></div></div>`).join(''):'<div class="empty">No tasks yet 🎉</div>'}
function renderSubjects(){document.getElementById('subjectList').innerHTML=data.subjects.length?data.subjects.map((s,i)=>`<div class="card subject"><div class="subject-top"><div><h3>${esc(s.name)}</h3><span class="tag">${esc(s.credits)} credits</span></div><div class="actions"><button class="btn ghost" onclick="openSubject(${i})">Edit</button><button class="btn ghost" onclick="delSubject(${i})">✕</button></div></div><p class="muted" style="margin-top:9px">${esc(s.teacher)||'Teacher not added'}</p><div class="progress"><div class="bar" style="width:${s.progress}%"></div></div><div class="muted">${s.progress}% progress</div></div>`).join(''):'<div class="card empty">Add your first subject.</div>'}
function renderNotes(){let q=(document.getElementById('noteSearch')?.value||'').toLowerCase();let arr=data.notes.map((x,i)=>({...x,i})).filter(x=>(x.title+x.body+x.subject).toLowerCase().includes(q));document.getElementById('noteList').innerHTML=arr.length?arr.map(n=>`<div class="card note"><span class="tag">${esc(n.subject)}</span><h3 style="margin-top:10px">${esc(n.title)}</h3><p>${esc(n.body)}</p><div class="actions"><button class="btn secondary" onclick="openNote(${n.i})">Edit</button><button class="btn ghost" onclick="delNote(${n.i})">Delete</button></div></div>`).join(''):'<div class="card empty">No notes found.</div>'}
function renderTasks(){let q=(document.getElementById('taskSearch')?.value||'').toLowerCase();let arr=data.tasks.map((x,i)=>({...x,i})).filter(x=>x.text.toLowerCase().includes(q));document.getElementById('taskList').innerHTML=arr.length?'<div class="list">'+arr.map(t=>`<div class="item"><button class="check ${t.done?'done':''}" onclick="toggleTask(${t.i})">${t.done?'✓':''}</button><div class="item-main ${t.done?'strike':''}"><b>${esc(t.text)}</b><br><small>${esc(t.priority)} priority${t.due?' • Due '+esc(t.due):''}</small></div><button class="btn ghost" onclick="delTask(${t.i})">Delete</button></div>`).join('')+'</div>':'<div class="empty">No tasks found.</div>'}
function renderPlans(){document.getElementById('planList').innerHTML=data.plans.length?data.plans.map((p,i)=>`<div class="card"><span class="tag">${esc(p.day)}</span><h3 style="margin-top:10px">${esc(p.subject)}</h3><p class="muted">🕐 ${esc(p.time)} • ${esc(p.duration)}</p><button class="btn ghost" style="margin-top:12px" onclick="delPlan($
