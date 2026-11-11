<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>DailyWealth | محفظتي اليومية</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#0a0f1c; --card:#111a2e; --card2:#16213a; --border:#22304f;
  --text:#e8eef9; --muted:#8793ad;
  --gold:#d4a72c; --gold2:#f6d77a;
  --up:#22c55e; --down:#ef4444; --blue:#3b82f6;
  --radius:16px;
}
*{box-sizing:border-box;margin:0;padding:0}
[hidden]{display:none!important}
body{
  font-family:'Tajawal',sans-serif;color:var(--text);min-height:100vh;font-size:15px;
  background:radial-gradient(1200px 600px at 85% -10%,#1b2a4d 0%,transparent 60%),var(--bg);
}
button,input,select{font-family:inherit;font-size:14px}
.wrap{max-width:1240px;margin:0 auto;padding:20px}

/* Header */
header{display:flex;justify-content:space-between;align-items:center;gap:16px;flex-wrap:wrap;margin-bottom:16px}
.brand{display:flex;align-items:center;gap:12px}
.logo{width:46px;height:46px;border-radius:12px;background:linear-gradient(135deg,var(--gold),var(--gold2));display:grid;place-items:center;color:#1a1200;font-weight:700;font-size:17px}
.brand h1{font-size:20px}
.brand p{color:var(--muted);font-size:13px;margin-top:2px}
.tools{display:flex;gap:10px;align-items:center;flex-wrap:wrap}

select,input{background:var(--card2);color:var(--text);border:1px solid var(--border);border-radius:10px;padding:9px 12px;outline:none}
select:focus,input:focus{border-color:var(--blue)}
.btn{background:var(--blue);color:#fff;border:0;border-radius:10px;padding:9px 16px;cursor:pointer;font-weight:500;white-space:nowrap}
.btn:hover{filter:brightness(1.1)}
.btn.ghost{background:transparent;border:1px solid var(--border);color:var(--text)}
.btn.danger{background:transparent;color:var(--down);border:1px solid #3a2530;padding:4px 10px;font-size:13px}

/* Ticker */
.ticker{overflow:hidden;background:var(--card);border:1px solid var(--border);border-radius:var(--radius);margin-bottom:18px}
.ticker-track{display:flex;width:max-content;padding:12px 0;animation:scroll 45s linear infinite}
.ticker:hover .ticker-track{animation-play-state:paused}
.group{display:flex;gap:36px;padding-left:36px;white-space:nowrap}
.t-item{display:inline-flex;gap:8px;align-items:center}
.t-name{color:var(--muted)}
.t-price{font-weight:700}
@keyframes scroll{from{transform:translateX(0)}to{transform:translateX(-50%)}}

/* Grid & cards */
.grid{display:grid;grid-template-columns:repeat(12,1fr);gap:18px}
.span-4{grid-column:span 4}.span-8{grid-column:span 8}.span-12{grid-column:span 12}
.card{background:linear-gradient(180deg,var(--card),#0e1627);border:1px solid var(--border);border-radius:var(--radius);padding:20px}
.card-h{display:flex;justify-content:space-between;align-items:center;margin-bottom:14px;gap:10px}
.card-h h2{font-size:17px}
.muted{color:var(--muted);font-size:13px}
.up{color:var(--up)}.down{color:var(--down)}
@media(max-width:900px){.span-4,.span-8{grid-column:span 12}}

/* Stats */
.stats{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin-bottom:16px}
.stat{background:var(--card2);border-radius:12px;padding:14px}
.stat small{color:var(--muted)}
.stat strong{display:block;font-size:19px;margin-top:4px}
@media(max-width:700px){.stats{grid-template-columns:1fr 1fr}}

/* Forms & lists */
.form-row{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:14px}
.form-row>*{flex:1;min-width:120px}
.task-form{display:flex;gap:8px;margin:12px 0}
.task-form input{flex:1}
.task{display:flex;align-items:center;gap:10px;padding:10px 12px;background:var(--card2);border-radius:12px;margin-bottom:8px}
.task input[type=checkbox]{width:18px;height:18px;accent-color:var(--gold)}
.task span{flex:1}
.task.done span{text-decoration:line-through;color:var(--muted)}
.progress{height:8px;background:var(--card2);border-radius:99px;overflow:hidden}
.progress div{height:100%;background:linear-gradient(90deg,var(--gold),var(--gold2));transition:width .4s}

/* Tables */
table{width:100%;border-collapse:collapse}
th,td{padding:10px 8px;text-align:right;border-bottom:1px solid var(--border)}
th{color:var(--muted);font-weight:500;font-size:13px}
td.num{font-variant-numeric:tabular-nums}
.pill{display:inline-block;padding:2px 8px;border-radius:99px;font-size:12px;font-weight:500}
.pill.up{background:#0f2e1e}.pill.down{background:#341a1f}

/* Alerts & insight */
.alert{padding:12px 14px;border-radius:12px;margin-bottom:8px;border-right:3px solid;background:var(--card2);font-size:14px;line-height:1.6}
.alert.up{border-color:var(--up)}.alert.down{border-color:var(--down)}.alert.info{border-color:var(--blue)}
.insight{font-size:17px;line-height:1.9}
.disclaimer{font-size:12px;color:var(--muted);margin-top:12px}
.empty{color:var(--muted);text-align:center;padding:18px;font-size:14px}

/* Toast */
.toast{position:fixed;bottom:20px;left:20px;background:var(--card2);border:1px solid var(--border);padding:12px 16px;border-radius:12px;box-shadow:0 10px 30px #0008;transform:translateY(140px);transition:.3s;max-width:330px;z-index:9;font-size:14px}
.toast.show{transform:translateY(0)}
</style>
</head>
<body>
<div class="wrap">

  <header>
    <div class="brand">
      <div class="logo">DW</div>
      <div>
        <h1 id="greet">أهلاً بك</h1>
        <p id="today"></p>
      </div>
    </div>
    <div class="tools">
      <select id="currency" onchange="setCurrency(this.value)" aria-label="العملة">
        <option value="USD">USD ($)</option>
        <option value="SAR">SAR (ريال)</option>
        <option value="AED">AED (درهم)</option>
        <option value="EGP">EGP (جنيه)</option>
        <option value="EUR">EUR (€)</option>
      </select>
      <button class="btn ghost" onclick="refreshData()">تحديث</button>
    </div>
  </header>

  <div class="ticker"><div class="ticker-track" id="ticker"></div></div>

  <div class="grid">

    <!-- المهام -->
    <section class="card span-4">
      <div class="card-h">
        <h2>مهام اليوم</h2>
        <span class="muted" id="taskCount"></span>
      </div>
      <div class="progress"><div id="taskBar" style="width:0%"></div></div>
      <form class="task-form" onsubmit="addTask(event)">
        <input id="taskInput" placeholder="أضف مهمة جديدة..." maxlength="120" required>
        <button class="btn">إضافة</button>
      </form>
      <div id="tasks"></div>
    </section>

    <!-- الأسواق -->
    <section class="card span-8">
      <div class="card-h">
        <h2>نبض السوق</h2>
        <span class="muted">أسعار تقريبية للعرض التجريبي</span>
      </div>
      <div id="market"></div>
    </section>

    <!-- المحفظة -->
    <section class="card span-8">
      <div class="card-h"><h2>محفظتي</h2></div>
      <div class="stats" id="pStats"></div>
      <form class="form-row" onsubmit="addHolding(event)">
        <select id="hType" onchange="toggleType()">
          <option value="gold">ذهب</option>
          <option value="stock">سهم</option>
        </select>
        <select id="hKarat">
          <option value="24">عيار 24</option>
          <option value="21">عيار 21</option>
          <option value="18">عيار 18</option>
        </select>
        <select id="hSym" hidden>
          <option value="SPX">S&amp;P 500</option>
          <option value="NDX">NASDAQ 100</option>
          <option value="AAPL">Apple</option>
          <option value="MSFT">Microsoft</option>
          <option value="NVDA">NVIDIA</option>
          <option value="TSLA">Tesla</option>
        </select>
        <input id="hAmount" type="number" step="any" min="0" placeholder="عدد الجرامات" required>
        <input id="hCost" type="number" step="any" min="0" placeholder="إجمالي ما دفعته" required>
        <button class="btn">إضافة</button>
      </form>
      <div id="pTable"></div>
    </section>

    <!-- التنبيهات -->
    <section class="card span-4">
      <div class="card-h"><h2>التنبيهات</h2></div>
      <div id="alerts"></div>
    </section>

    <!-- الفكرة اليومية -->
    <section class="card span-12">
      <div class="card-h"><h2>فكرة اليوم</h2><span class="muted">دقيقة واحدة</span></div>
      <p class="insight" id="insight"></p>
      <p class="disclaimer">
        هذا المحتوى تعليمي فقط وليس نصيحة استثمارية. الاستثمار ينطوي على مخاطر، واستشر مختصاً مرخصاً قبل اتخاذ أي قرار.
      </p>
    </section>

  </div>
</div>

<div class="toast" id="toast"></div>

<script>
/* ================== الإعدادات ================== */
const KEY = 'dailywealth-v2';
const RATES = {USD:1, SAR:3.75, AED:3.6725, EGP:50.5, EUR:0.92};
const GRAM_OZ = 31.1035;
const STOCK_SYMS = ['AAPL','MSFT','NVDA','TSLA'];
const START = {XAU:3000, SPX:5400, NDX:19000, AAPL:230, MSFT:420, NVDA:130, TSLA:250};
const NAMES = {XAU:'أونصة الذهب', SPX:'S&P 500', NDX:'NASDAQ 100', AAPL:'Apple', MSFT:'Microsoft', NVDA:'NVIDIA', TSLA:'Tesla'};
const INSIGHTS = [
  'الذهب يُعتبر تقليدياً ملاذاً آمناً، لكنه قد يتذبذب بقوة في الأجل القصير.',
  'التنويع بين أصول مختلفة يقلل أثر تقلب سهم واحد على محفظتك كاملة.',
  'الاستثمار طويل الأجل يعتمد على الصبر أكثر من محاولة توقيت السوق.',
  'مؤشر S&P 500 يعكس أداء مجموعة واسعة من كبرى الشركات الأمريكية.',
  'راجع محفظتك بانتظام، لكن تجنب القرارات المتسرعة بسبب تغير يومي واحد.',
  'قبل الاستثمار، تأكد من وجود صندوق طوارئ يغطي عدة أشهر من مصاريفك.'
];

/* ================== الحالة والتخزين ================== */
const $ = id => document.getElementById(id);
let state = JSON.parse(localStorage.getItem(KEY)) || {};
state.tasks = state.tasks || [];
state.holdings = state.holdings || [];
state.open = state.open || {};
state.openDate = state.openDate || '';
state.currency = state.currency || 'USD';

const save = () => localStorage.setItem(KEY, JSON.stringify(state));

const quotes = Object.fromEntries(
  Object.entries(START).map(([k, v]) => [k, {name: NAMES[k], price: v, open: v}])
);

/* ================== مصدر البيانات ==================
   هذه الدالة هي المكان الذي تربط فيه مزود بيانات حقيقي.
   يجب أن تعيد كائناً مثل: { XAU: 3050, SPX: 5420, AAPL: 231, ... }
   أو null لاستخدام المحاكاة التجريبية.
   مزودو بيانات مقترحون: Twelve Data, Finnhub, Alpha Vantage, metals-api
   (تحقق من شروط الترخيص والتأخير في الخطة المجانية).
*/
async function fetchLive() {
  // مثال توضيحي:
  // const res = await fetch('https://your-backend.com/api/quotes');
  // return await res.json();
  return null;
}

function simulate() {
  for (const k in quotes) {
    const vol = k === 'XAU' ? 0.002 : 0.004;
    quotes[k].price *= 1 + (Math.random() - 0.5) * 2 * vol;
  }
}

/* ================== الحسابات ================== */
const fmt = (usd, d = 2) => new Intl.NumberFormat('ar', {
  style: 'currency', currency: state.currency,
  minimumFractionDigits: d, maximumFractionDigits: d
}).format(usd * RATES[state.currency]);

const pct = p => (p >= 0 ? '+' : '') + p.toFixed(2) + '%';
const cls = v => v >= 0 ? 'up' : 'down';
const esc = s => String(s).replace(/[&<>"']/g, c => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));

const goldGram = (karat, ounce) => (ounce ?? quotes.XAU.price) / GRAM_OZ * karat / 24;

function chg(k) {
  const q = quotes[k];
  return q.open ? (q.price - q.open) / q.open * 100 : 0;
}

function valueOf(h, useOpen = false) {
  if (h.type === 'gold') {
    const oz = useOpen ? quotes.XAU.open : quotes.XAU.price;
    return h.amount * goldGram(h.karat, oz);
  }
  const q = quotes[h.sym];
  return h.amount * (useOpen ? q.open : q.price);
}

function totals() {
  let v = 0, c = 0, o = 0;
  for (const h of state.holdings) {
    v += valueOf(h);
    o += valueOf(h, true);
    c += h.cost;
  }
  return {
    v, c, pl: v - c, plPct: c ? (v - c) / c * 100 : 0,
    day: v - o, dayPct: o ? (v - o) / o * 100 : 0
  };
}

function getRows() {
  return [
    {n:'ذهب عيار 24 (جرام)', p:goldGram(24), c:chg('XAU')},
    {n:'ذهب عيار 21 (جرام)', p:goldGram(21), c:chg('XAU')},
    {n:'ذهب عيار 18 (جرام)', p:goldGram(18), c:chg('XAU')},
    {n:'أونصة الذهب', p:quotes.XAU.price, c:chg('XAU')},
    ...['SPX','NDX',...STOCK_SYMS].map(k => ({n:`${quotes[k].name} (${k})`, p:quotes[k].price, c:chg(k)}))
  ];
}

/* ================== الرسم ================== */
function renderHeader() {
  const now = new Date();
  $('greet').textContent = now.getHours() < 12 ? 'صباح الخير ☀️' : 'مساء الخير 🌙';
  const date = now.toLocaleDateString('ar', {weekday:'long', day:'numeric', month:'long', year:'numeric'});
  $('today').textContent = `${date} · آخر تحديث: ${lastUpdate ? lastUpdate.toLocaleTimeString('ar', {hour:'2-digit', minute:'2-digit'}) : '—'}`;
}

function renderTicker() {
  const html = getRows().map(r =>
    `<div class="t-item"><span class="t-name">${r.n}</span><span class="t-price">${fmt(r.p)}</span><span class="${cls(r.c)}">${pct(r.c)}</span></div>`
  ).join('');
  $('ticker').innerHTML = `<div class="group">${html}</div><div class="group" aria-hidden="true">${html}</div>`;
}

function renderMarket() {
  $('market').innerHTML = `
    <table>
      <thead><tr><th>الأصل</th><th>السعر</th><th>التغير اليومي</th></tr></thead>
      <tbody>
        ${getRows().map(r => `
          <tr>
            <td>${r.n}</td>
            <td class="num">${fmt(r.p)}</td>
            <td><span class="pill ${cls(r.c)}">${pct(r.c)}</span></td>
          </tr>`).join('')}
      </tbody>
    </table>`;
}

/* --- المهام --- */
function renderTasks() {
  const done = state.tasks.filter(t => t.done).length;
  const total = state.tasks.length;
  $('taskCount').textContent = total ? `${done}/${total} مكتملة` : '';
  $('taskBar').style.width = total ? (done / total * 100) + '%' : '0%';
  $('tasks').innerHTML = total ? state.tasks.map(t => `
    <div class="task ${t.done ? 'done' : ''}">
      <input type="checkbox" ${t.done ? 'checked' : ''} onchange="toggleTask(${t.id})">
      <span>${esc(t.text)}</span>
      <button class="btn danger" onclick="delTask(${t.id})">حذف</button>
    </div>`).join('')
    : '<div class="empty">لا توجد مهام بعد. ابدأ بإضافة أول مهمة لليوم ✨</div>';
}

function addTask(e) {
  e.preventDefault();
  const input = $('taskInput');
  const text = input.value.trim();
  if (!text) return;
  state.tasks.push({id: Date.now(), text, done: false});
  input.value = '';
  save(); renderTasks();
}
function toggleTask(id) {
  const t = state.tasks.find(x => x.id === id);
  if (t) t.done = !t.done;
  save(); renderTasks();
}
function delTask(id) {
  state.tasks = state.tasks.filter(x => x.id !== id);
  save(); renderTasks();
}

/* --- المحفظة --- */
function renderPortfolio() {
  const t = totals();
  $('pStats').innerHTML = `
    <div class="stat"><small>إجمالي القيمة</small><strong>${fmt(t.v)}</strong></div>
    <div class="stat"><small>إجمالي التكلفة</small><strong>${fmt(t.c)}</strong></div>
    <div class="stat"><small>الربح / الخسارة</small>
      <strong class="${cls(t.pl)}">${fmt(t.pl)} <span style="font-size:13px">(${pct(t.plPct)})</span></strong></div>
    <div class="stat"><small>تغير اليوم</small><strong class="${cls(t.day)}">${pct(t.dayPct)}</strong></div>`;

  if (!state.holdings.length) {
    $('pTable').innerHTML = '<div class="empty">أضف ما تملكه من ذهب أو أسهم لتبدأ المتابعة.</div>';
    return;
  }
  const rows = state.holdings.map(h => {
    const v = valueOf(h), pl = v - h.cost, plp = h.cost ? pl / h.cost * 100 : 0;
    const name = h.type === 'gold' ? `ذهب عيار ${h.karat}` : `${quotes[h.sym].name} (${h.sym})`;
    const amount = h.type === 'gold' ? `${h.amount} جم` : `${h.amount} سهم`;
    return `
      <tr>
        <td>${name}</td>
        <td class="num">${amount}</td>
        <td class="num">${fmt(v)}</td>
        <td class="num ${cls(pl)}">${fmt(pl)} <span class="pill ${cls(pl)}">${pct(plp)}</span></td>
        <td><button class="btn danger" onclick="delHolding(${h.id})">حذف</button></td>
      </tr>`;
  }).join('');
  $('pTable').innerHTML = `
    <table>
      <thead><tr><th>الأصل</th><th>الكمية</th><th>القيمة الحالية</th><th>الربح / الخسارة</th><th></th></tr></thead>
      <tbody>${rows}</tbody>
    </table>`;
}

function toggleType() {
  const gold = $('hType').value === 'gold';
  $('hKarat').hidden = !gold;
  $('hSym').hidden = gold;
  $('hAmount').placeholder = gold ? 'عدد الجرامات' : 'عدد الأسهم';
}

function addHolding(e) {
  e.preventDefault();
  const type = $('hType').value;
  const amount = +$('hAmount').value;
  const cost = (+$('hCost').value) / RATES[state.currency]; // نخزن التكلفة بالدولار
  if (!(amount > 0) || !(cost >= 0)) return;
  const h = {id: Date.now(), type, amount, cost};
  if (type === 'gold') h.karat = +$('hKarat').value;
  else h.sym = $('hSym').value;
  state.holdings.push(h);
  $('hAmount').value = ''; $('hCost').value = '';
  save(); renderAll();
}

function delHolding(id) {
  state.holdings = state.holdings.filter(h => h.id !== id);
  save(); renderAll();
}

/* --- التنبيهات --- */
const seenAlerts = new Set();
let toastTimer;

function toast(msg) {
  const el = $('toast');
  el.textContent = msg;
  el.classList.add('show');
  clearTimeout(toastTimer);
  toastTimer = setTimeout(() => el.classList.remove('show'), 4500);
}

function buildAlerts() {
  const list = [];
  const t = totals();

  if (state.holdings.length && Math.abs(t.dayPct) >= 5) {
    list.push({type: t.dayPct > 0 ? 'up' : 'down',
      text: `محفظتك ${t.dayPct > 0 ? 'ارتفعت' : 'انخفضت'} بنسبة ${Math.abs(t.dayPct).toFixed(2)}% اليوم.`});
  }

  const assets = new Set(state.holdings.map(h => h.type === 'gold' ? 'XAU' : h.sym));
  assets.forEach(k => {
    const c = chg(k);
    if (Math.abs(c) >= 3) {
      list.push({type: c > 0 ? 'up' : 'down',
        text: `${quotes[k].name} ${c > 0 ? 'ارتفع' : 'انخفض'} بنسبة ${Math.abs(c).toFixed(2)}% منذ بداية اليوم.`});
    }
  });

  const pending = state.tasks.filter(x => !x.done).length;
  if (pending) list.push({type: 'info', text: `لديك ${pending} مهام غير مكتملة اليوم.`});
  if (state.holdings.length) list.push({type: 'info', text: 'تذكير: راجع محفظتك الاستثمارية اليوم.'});

  return list;
}

function renderAlerts() {
  const list = buildAlerts();
  $('alerts').innerHTML = list.length
    ? list.slice(0, 6).map(a => `<div class="alert ${a.type}">${a.text}</div>`).join('')
    : '<div class="empty">لا توجد تنبيهات حالياً ✅</div>';

  list.forEach(a => {
    if (a.type !== 'info' && !seenAlerts.has(a.text)) {
      seenAlerts.add(a.text);
      toast(a.text);
    }
  });
}

/* --- الفكرة اليومية --- */
function renderInsight() {
  const day = Math.floor(Date.now() / 86400000);
  $('insight').textContent = INSIGHTS[day % INSIGHTS.length];
}

function renderAll() {
  renderHeader();
  renderTicker();
  renderMarket();
  renderTasks();
  renderPortfolio();
  renderAlerts();
  renderInsight();
}

/* ================== التحديث والتهيئة ================== */
let lastUpdate = null;

function ensureOpen() {
  const today = new Date().toDateString();
  if (state.openDate !== today) {
    state.openDate = today;
    state.open = {};
    for (const k in quotes) state.open[k] = quotes[k].price;
    save();
  }
}

async function refreshData() {
  const live = await fetchLive();
  if (live) {
    for (const k in live) if (quotes[k]) quotes[k].price = live[k];
  } else {
    simulate();
  }
  for (const k in quotes) quotes[k].open = state.open[k] ?? quotes[k].price;
  state.last = Object.fromEntries(Object.entries(quotes).map(([k, q]) => [k, q.price]));
  save();
  lastUpdate = new Date();
  renderAll();
}

function setCurrency(c) {
  state.currency = c;
  save(); renderAll();
}

function init() {
  if (state.last) for (const k in state.last) if (quotes[k]) quotes[k].price = state.last[k];
  ensureOpen();
  $('currency').value = state.currency;
  toggleType();
  refreshData();
  setInterval(refreshData, 15000);   // تحديث كل 15 ثانية (عرض تجريبي)
  setInterval(renderHeader, 60000);
}

init();
</script>
</body>
</html>
