# Business-help-book
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>BTEC Business Year 1 — Study Tracker</title>
<style>
:root{
  --bg:#f6f5f2; --card:#ffffff; --ink:#1f2321; --muted:#6b6f6c;
  --accent:#0f6b4c; --accent2:#c96f2b; --line:#e4e1da; --pass:#0f6b4c; --merit:#1d6fa5; --dist:#8a3fc9;
}
@media (prefers-color-scheme: dark){
  :root:not([data-theme="light"]){--bg:#15170f;--card:#1e2118;--ink:#eceae2;--muted:#a3a89c;--line:#2c2f24;}
}
:root[data-theme="dark"]{--bg:#15170f;--card:#1e2118;--ink:#eceae2;--muted:#a3a89c;--line:#2c2f24;}
*{box-sizing:border-box;}
html,body{margin:0;background:var(--bg);color:var(--ink);font-family:"Segoe UI",system-ui,-apple-system,sans-serif;
  padding-top:env(safe-area-inset-top,0px); padding-bottom:env(safe-area-inset-bottom,0px);}
header{padding:28px 20px 18px; text-align:center; border-bottom:1px solid var(--line);}
header h1{margin:0 0 4px; font-size:1.5rem;}
header p{margin:0; color:var(--muted); font-size:.92rem;}
.wrap{max-width:920px; margin:0 auto; padding:20px;}
.progress-card{background:var(--card); border:1px solid var(--line); border-radius:14px; padding:18px 20px; margin-bottom:20px;}
.bar{height:12px; border-radius:8px; background:var(--line); overflow:hidden; margin-top:10px;}
.bar-fill{height:100%; background:linear-gradient(90deg,var(--accent),var(--accent2)); width:0%; transition:width .3s;}
.progress-row{display:flex; justify-content:space-between; align-items:baseline;}
.progress-row .pct{font-size:1.4rem; font-weight:700; color:var(--accent);}
.tabs{display:flex; flex-wrap:wrap; gap:8px; margin-bottom:16px;}
.tab{padding:8px 12px; border-radius:20px; border:1px solid var(--line); background:var(--card); cursor:pointer; font-size:.85rem; color:var(--ink);}
.tab.active{background:var(--accent); color:#fff; border-color:var(--accent);}
.tab .dot{display:inline-block;width:7px;height:7px;border-radius:50%;background:var(--line);margin-right:6px;}
.tab.done .dot{background:var(--accent);}
.unit{display:none;}
.unit.active{display:block;}
.unit-card{background:var(--card); border:1px solid var(--line); border-radius:14px; padding:20px; margin-bottom:16px;}
.unit-card h2{margin:0 0 4px; font-size:1.15rem;}
.assess{display:inline-block; font-size:.72rem; padding:2px 8px; border-radius:10px; margin-left:6px; vertical-align:middle;}
.assess.internal{background:#e6f2ea; color:var(--pass);}
.assess.external{background:#fdece0; color:var(--accent2);}
.year-tag{font-size:.72rem; color:var(--muted); display:block; margin-bottom:10px;}
.unit-card p.desc{color:var(--muted); font-size:.92rem; line-height:1.5;}
h3.sub{font-size:.85rem; text-transform:uppercase; letter-spacing:.04em; color:var(--muted); margin:18px 0 8px;}
.topics label{display:flex; align-items:flex-start; gap:10px; padding:7px 0; border-bottom:1px dashed var(--line); font-size:.92rem; cursor:pointer;}
.topics label:last-child{border-bottom:none;}
.topics input{margin-top:3px;}
.topics input:checked + span{text-decoration:line-through; color:var(--muted);}
.links a{display:block; padding:8px 10px; margin-bottom:6px; border:1px solid var(--line); border-radius:8px; text-decoration:none; color:var(--ink); font-size:.88rem;}
.links a:hover{border-color:var(--accent);}
.links a::before{content:"↗ "; color:var(--accent);}
textarea{width:100%; min-height:80px; border:1px solid var(--line); border-radius:8px; padding:10px; font-family:inherit; font-size:.9rem; background:var(--bg); color:var(--ink); resize:vertical;}
.savehint{font-size:.72rem; color:var(--muted); margin-top:4px;}
footer{text-align:center; color:var(--muted); font-size:.75rem; padding:20px; }
</style>
</head>
<body>
<header>
  <h1>BTEC Extended Diploma in Business — Year 1</h1>
  <p>Paddington Green · City of Westminster College · study &amp; progress tracker</p>
</header>

<div class="wrap">

  <div class="progress-card">
    <div class="progress-row">
      <span>Overall progress</span>
      <span class="pct" id="overallPct">0%</span>
    </div>
    <div class="bar"><div class="bar-fill" id="overallBar"></div></div>
  </div>

  <div class="tabs" id="tabs"></div>
  <div id="units"></div>

</div>

<footer>Progress and notes are saved in this browser only. Use the same browser/device to keep your history.</footer>

<script>
const UNITS = [
  {
    id: "u1", num: 1, title: "Exploring Business", assess: "internal", year: "Commonly Year 1",
    desc: "How different businesses are structured, owned and organised, and how they're influenced by stakeholders and the wider environment.",
    topics: [
      "Purposes of different business forms (sole trader, partnership, Ltd, plc, franchise, social enterprise)",
      "Ownership, liability and sources of finance for each business type",
      "How businesses are organised: functional areas and organisational structures",
      "How stakeholders (owners, employees, customers, government, community) influence a business",
      "How the political, legal and social environment affects a business",
      "How competitive markets and the economy affect business behaviour"
    ],
    links: [
      ["Pearson – official BTEC Business specification & support", "https://qualifications.pearson.com/en/qualifications/btec-nationals/business-2016.html"],
      ["tutor2u Business – topic explainers", "https://www.tutor2u.net/business"],
      ["BBC Bitesize – Business subjects hub", "https://www.bbc.co.uk/bitesize/subjects"],
      ["Seneca Learning – free interactive courses", "https://senecalearning.com"]
    ]
  },
  {
    id: "u2", num: 2, title: "Developing a Marketing Campaign", assess: "external", year: "Often Year 1/2",
    desc: "Externally assessed. How marketing supports business objectives, and how to plan a coherent marketing campaign.",
    topics: [
      "Role of marketing and the marketing mix (7Ps)",
      "Market research: primary vs secondary, quantitative vs qualitative",
      "Market segmentation and targeting",
      "Analysing marketing data and drawing conclusions",
      "Planning a marketing campaign: objectives, budget, timescale",
      "Evaluating a campaign against its objectives"
    ],
    links: [
      ["Chartered Institute of Marketing (CIM)", "https://www.cim.co.uk"],
      ["tutor2u – Marketing", "https://www.tutor2u.net/business"],
      ["Pearson – Business specification & past papers", "https://qualifications.pearson.com/en/qualifications/btec-nationals/business-2016.html"]
    ]
  },
  {
    id: "u3", num: 3, title: "Personal and Business Finance", assess: "external", year: "Commonly Year 1",
    desc: "Externally assessed. Managing personal finance and understanding how businesses record, report and use financial information.",
    topics: [
      "Personal finance: budgeting, saving, borrowing, financial products",
      "Sources of business finance (internal and external)",
      "Recording financial transactions and double-entry basics",
      "Statement of comprehensive income and statement of financial position",
      "Using ratios to assess business performance",
      "Cash flow forecasting and break-even analysis"
    ],
    links: [
      ["Corporate Finance Institute – free resources", "https://corporatefinanceinstitute.com/resources/"],
      ["tutor2u – Business Finance", "https://www.tutor2u.net/business"],
      ["Pearson – Business specification & past papers", "https://qualifications.pearson.com/en/qualifications/btec-nationals/business-2016.html"]
    ]
  },
  {
    id: "u4", num: 4, title: "Managing an Event", assess: "internal", year: "Commonly Year 1",
    desc: "Planning, running and reviewing a real or simulated business event, applying project-management skills.",
    topics: [
      "Purposes and types of business events",
      "Planning an event: objectives, budget, resources, risk assessment",
      "Roles and responsibilities within an event team",
      "Running the event and dealing with problems on the day",
      "Reviewing and evaluating the event against objectives"
    ],
    links: [
      ["tutor2u – Business Events / Project Management", "https://www.tutor2u.net/business"],
      ["Association for Project Management – free guides", "https://www.apm.org.uk"]
    ]
  },
  {
    id: "u5", num: 5, title: "International Business", assess: "internal", year: "Often Year 1/2",
    desc: "Why businesses trade internationally, and the opportunities and risks this creates.",
    topics: [
      "Reasons for international trade and globalisation",
      "How exchange rates affect business",
      "Trade blocs, tariffs and barriers to trade",
      "Cultural, legal and ethical issues of operating internationally",
      "Opportunities and risks of expanding into new markets"
    ],
    links: [
      ["tutor2u – International Business", "https://www.tutor2u.net/business"],
      ["World Trade Organization – trade basics", "https://www.wto.org"]
    ]
  },
  {
    id: "u6", num: 6, title: "Principles of Management", assess: "external", year: "Usually Year 2",
    desc: "Externally assessed. Management styles, structures and how managers plan, organise and lead.",
    topics: [
      "Management functions: planning, organising, leading, controlling",
      "Leadership and management styles",
      "Organisational structures and culture",
      "Motivation theories (Maslow, Herzberg, Taylor)",
      "Managing change within a business"
    ],
    links: [
      ["CIPD – management & leadership factsheets", "https://www.cipd.org"],
      ["tutor2u – Management", "https://www.tutor2u.net/business"]
    ]
  },
  {
    id: "u7", num: 7, title: "Business Decision Making", assess: "external", year: "Usually Year 2",
    desc: "Externally assessed. Using data and quantitative techniques to support business decisions.",
    topics: [
      "Interpreting business data: tables, charts, index numbers",
      "Financial techniques for decision making (ratios, breakeven)",
      "Investment appraisal (payback, ARR, NPV)",
      "Presenting recommendations based on data"
    ],
    links: [
      ["tutor2u – Business Decision Making", "https://www.tutor2u.net/business"],
      ["Corporate Finance Institute – investment appraisal", "https://corporatefinanceinstitute.com/resources/"]
    ]
  }
];

const store = {
  get(){ try{ return JSON.parse(localStorage.getItem('btecTracker')||'{}'); }catch(e){ return {}; } },
  set(d){ try{ localStorage.setItem('btecTracker', JSON.stringify(d)); }catch(e){} }
};
let data = store.get();

function unitProgress(u){
  const d = data[u.id] || {};
  const checked = (d.topics||[]).filter(Boolean).length;
  return {checked, total: u.topics.length};
}

function renderTabs(activeId){
  const tabs = document.getElementById('tabs');
  tabs.innerHTML = '';
  UNITS.forEach(u=>{
    const {checked,total} = unitProgress(u);
    const btn = document.createElement('div');
    btn.className = 'tab' + (u.id===activeId?' active':'') + (checked===total?' done':'');
    btn.innerHTML = `<span class="dot"></span>Unit ${u.num}`;
    btn.onclick = ()=> showUnit(u.id);
    tabs.appendChild(btn);
  });
}

function renderUnit(u){
  const d = data[u.id] || {topics: Array(u.topics.length).fill(false), notes:''};
  const div = document.createElement('div');
  div.className = 'unit';
  div.id = 'view-'+u.id;
  const assessLabel = u.assess === 'external' ? 'Externally assessed' : 'Internally assessed';
  div.innerHTML = `
    <div class="unit-card">
      <h2>Unit ${u.num}: ${u.title}<span class="assess ${u.assess}">${assessLabel}</span></h2>
      <span class="year-tag">${u.year} — check your own college timetable, sequencing varies</span>
      <p class="desc">${u.desc}</p>

      <h3 class="sub">What I've learnt</h3>
      <div class="topics">
        ${u.topics.map((t,i)=>`<label><input type="checkbox" data-unit="${u.id}" data-idx="${i}" ${d.topics[i]?'checked':''}><span>${t}</span></label>`).join('')}
      </div>

      <h3 class="sub">Resources</h3>
      <div class="links">
        ${u.links.map(([label,url])=>`<a href="${url}" target="_blank" rel="noopener">${label}</a>`).join('')}
      </div>

      <h3 class="sub">What I've missed / need to revisit</h3>
      <textarea data-notes="${u.id}" placeholder="Jot down anything you're unsure about, missed a lesson on, or want to revise before an assessment...">${d.notes||''}</textarea>
      <div class="savehint">Saves automatically in this browser</div>
    </div>
  `;
  return div;
}

function showUnit(id){
  document.querySelectorAll('.unit').forEach(el=>el.classList.remove('active'));
  document.getElementById('view-'+id).classList.add('active');
  renderTabs(id);
  localStorage.setItem('btecTrackerActive', id);
}

function updateOverall(){
  let checked=0, total=0;
  UNITS.forEach(u=>{ const p = unitProgress(u); checked+=p.checked; total+=p.total; });
  const pct = total? Math.round(checked/total*100) : 0;
  document.getElementById('overallPct').textContent = pct+'%';
  document.getElementById('overallBar').style.width = pct+'%';
}

function init(){
  const unitsEl = document.getElementById('units');
  UNITS.forEach(u=>{
    if(!data[u.id]) data[u.id] = {topics: Array(u.topics.length).fill(false), notes:''};
    unitsEl.appendChild(renderUnit(u));
  });
  store.set(data);

  unitsEl.addEventListener('change', e=>{
    if(e.target.matches('input[type=checkbox]')){
      const uid = e.target.dataset.unit, idx = +e.target.dataset.idx;
      data[uid].topics[idx] = e.target.checked;
      store.set(data);
      updateOverall();
      renderTabs(document.querySelector('.unit.active').id.replace('view-',''));
    }
  });
  unitsEl.addEventListener('input', e=>{
    if(e.target.matches('textarea[data-notes]')){
      const uid = e.target.dataset.notes;
      data[uid].notes = e.target.value;
      store.set(data);
    }
  });

  const startId = localStorage.getItem('btecTrackerActive') || UNITS[0].id;
  showUnit(document.getElementById('view-'+startId) ? startId : UNITS[0].id);
  updateOverall();
}
init();
</script>
</body>
</html>
