<!doctype html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>새싹 떡이 군단</title>
<style>
*{box-sizing:border-box}body{margin:0;background:#eef6ed;color:#294332;font:14px/1.5 system-ui,'Malgun Gothic',sans-serif}main{max-width:720px;padding:12px;margin:auto}header{padding:20px;border-radius:18px;background:linear-gradient(120deg,#266d4b,#49a46f);color:#fff}h1{font-size:26px;margin:0 0 4px}h3{font-size:16px;margin:0 0 12px}.stats{display:flex;gap:9px;flex-wrap:wrap;margin-top:12px}.stats span{padding:7px 12px;background:#ffffff29;border-radius:25px;font-weight:700}nav{display:grid;grid-template-columns:repeat(4,1fr);gap:5px;margin:12px 0}button{cursor:pointer;border:none;border-radius:10px;padding:11px 8px;font:700 13px/1.45 inherit;font-family:inherit}button:disabled{opacity:.45;cursor:not-allowed}nav button{background:#dbe9d9}nav button.active{background:#28784e;color:#fff}.card{background:white;border:1px solid #d7e6d6;border-radius:16px;padding:15px;margin-bottom:12px}.grid{display:grid;grid-template-columns:1fr 1fr;gap:8px}.triple{display:grid;grid-template-columns:repeat(3,1fr);gap:7px}.row{display:flex;align-items:center;justify-content:space-between;gap:8px}.center{text-align:center}.muted{color:#6a806e;font-size:12px}.green{background:#328957;color:white}.blue{background:#deebff;color:#2a5791}.red{background:#ffe2e2;color:#9f3d3d}.light{background:#e6f3e5;color:#286641}.gold{background:#fff0c6;color:#825d1e}.pill{background:#e4f0e1;padding:4px 8px;border-radius:30px;font-size:12px}.hidden{display:none!important}.farm-scene{height:190px;border:2px solid #c8dfc2;border-radius:14px;background:linear-gradient(#e3f6ed 65%,#c8e1aa 65%);display:grid;place-items:center}.unit,.team-unit{display:flex;align-items:center;gap:8px;width:100%;padding:8px;border:1px solid #dce9d9;background:#f9fcf8;text-align:left;border-radius:12px;margin:5px 0}.unit.selected,.team-unit.selected{border:2px solid #4b9e65;background:#e6f5e8;padding:7px}.unit svg,.team-unit svg{flex:0 0 auto}.grow{flex:1;min-width:0}.truncate{overflow:hidden;text-overflow:ellipsis;white-space:nowrap}input[type=text]{width:100%;padding:9px;border:1px solid #c3d5c0;border-radius:9px}#message{background:#e1f0de;color:#315f3e;padding:13px;border-radius:12px;min-height:43px;font-size:13px}.arena{border:2px solid #cde1cd;border-radius:13px;padding:10px;background:#f6fbf6}.fighters{min-height:85px;display:flex;flex-wrap:wrap;justify-content:center;align-items:center;gap:7px}.fighter{width:66px;text-align:center;font-size:10px}.fighter.dead{opacity:.28}.hpbar{height:7px;border-radius:8px;background:#f1c6c6;overflow:hidden;margin-top:5px}.hpfill{height:100%;background:#4aa973}.battle-team-list{max-height:265px;overflow:auto}.battle-team-list .team-unit input{accent-color:#33875a;width:18px;height:18px}.field-area{height:350px;width:100%;position:relative;border:5px solid #82ad83;border-radius:18px;overflow:hidden;background:radial-gradient(circle at 21% 20%,#f9fff7,#dcf3dc 65%,#c5e6ba);touch-action:pan-y;contain:layout paint}.field-area:before{content:'🌼  ·  🌱  ·  🌼  ·  🌿  ·  🌼';position:absolute;bottom:8px;left:10px;color:#75a86e;opacity:.65}.field-agent{position:absolute;left:0;top:0;width:78px;height:77px;will-change:transform;pointer-events:none;text-align:center}.field-agent svg{width:78px;max-height:59px}.field-agent .agent-name{font-size:10px;line-height:13px;white-space:nowrap;text-overflow:ellipsis;overflow:hidden;background:#ffffffbb;border-radius:8px;padding:1px 3px}.field-note{font-size:12px;color:#57745e;margin-top:9px}.bottom{text-align:center;font-size:11px;color:#78907b;padding:10px}
@media(max-width:380px){.stats{font-size:12px}.triple button{font-size:11px;padding:9px 3px}nav button{font-size:12px;padding:10px 2px}}

.tutorial-overlay{position:fixed;inset:0;background:#183323aa;display:flex;align-items:center;justify-content:center;padding:16px;z-index:1000}
.tutorial-panel{width:min(100%,520px);max-height:85vh;overflow:auto;background:#fff;border-radius:18px;padding:20px;box-shadow:0 18px 55px #102a1b55}
.tutorial-panel h2{margin:0 0 10px;color:#286641}.tutorial-panel p{margin:8px 0;color:#4c6651}.tutorial-actions{display:flex;gap:8px;margin-top:16px}.tutorial-actions button{flex:1}

#sellModal .tutorial-panel{border:2px solid #e7b8b8}
#sellMessage{background:#f5faf3;padding:13px;border-radius:12px;margin:12px 0;font-weight:700}
.tutorial-page{min-height:245px}
.tutorial-page h3{color:#286641;margin:8px 0}
.tutorial-page p{margin:10px 0;color:#4c6651}
.tutorial-progress{height:7px;background:#e4eee1;border-radius:10px;overflow:hidden;margin:8px 0 16px}
.tutorial-progress span{display:block;height:100%;background:#49a46f;transition:width .2s}
</style>
</head>
<body>
<main>
<header><h1>🌱 새싹 떡이 군단</h1><div class="row"><span>떡이를 모으고 키우는 작은 세상</span><button class="light" onclick="openTutorial()">📖 튜토리얼</button></div>
<div class="stats"><span>💧 <b id="water">5,000</b>ml</span><span>🌱 <b id="count">1</b> / <b id="slots">5</b>칸</span><span>🏆 <b id="wins">0</b>승</span></div></header>
<nav><button id="nav-farm" onclick="showTab('farm')">🏡 농장</button><button id="nav-field" onclick="showTab('field')">🌿 필드</button><button id="nav-bag" onclick="showTab('bag')">🎒 가방</button><button id="nav-battle" onclick="showTab('battle')">⚔️ 전투</button></nav>
<section id="farm">
<div class="card"><div class="row"><button class="light" onclick="move(-1)">◀</button><div class="center"><h3 id="farmName"></h3><div id="farmInfo" class="muted"></div></div><button class="light" onclick="move(1)">▶</button></div><div id="mainTteok" class="farm-scene"></div><div class="triple center" style="margin-top:12px"><div>⚔️ 공격력<br><b id="atk"></b></div><div>❤️ 체력<br><b id="hp"></b></div><div>🍓 토핑<br><b id="top"></b></div></div></div>
<div class="card"><div class="row"><h3>🌱 내 떡이</h3><span id="slotText" class="pill"></span></div><div id="roster"></div><div class="row" style="background:#f1f9ee;padding:12px;border-radius:12px;margin-top:12px"><div><b>🔓 보유 슬롯 확장</b><div id="slotCost" class="muted"></div></div><button id="buySlot" class="green" onclick="expandSlot()">💧 슬롯 +1</button></div></div>
<div class="card"><h3>🛠️ 떡이 관리</h3><div class="triple"><button class="light" onclick="toggleHealer()">💚 힐러</button><button class="gold" onclick="cycleTopping()">🍓 토핑 변경</button><button class="blue" onclick="rename()">✏️ 이름 변경</button></div><button class="red" style="width:100%;margin-top:9px" onclick="askSellTteok()">💧 선택한 떡이 판매</button><div id="renameArea" class="hidden" style="margin-top:12px"><input type="text" maxlength="15" id="newName" placeholder="떡이 이름"><button class="green" style="margin-top:8px" onclick="saveName()">변경 완료</button></div></div>
<div class="card"><h3>🎁 뽑기와 성장</h3><button id="attendance" class="green" style="width:100%;margin-bottom:9px" onclick="claimAttendance()">📅 출석 보상</button><div class="grid"><button class="blue" onclick="drawTteok()">🥚 떡이 뽑기<br>1,000ml</button><button class="blue" onclick="drawItem()">🎁 아이템 뽑기<br>1,000ml</button><button id="levelUpBtn" class="light" onclick="levelUp()">⬆️ 레벨업 / 승급</button><button class="red" onclick="showTab('battle')">⚔️ 출전 인원 선택</button></div></div>
</section>
<section id="field" class="hidden"><div class="card"><h3>🌿 떡이들의 필드</h3><p class="muted">보유하신 떡이들이 자유롭게 돌아다닙니다. 어떤 떡이들은 폴짝폴짝 뛰기도 합니다!</p><div id="fieldArea" class="field-area"></div><div class="field-note">🔒 떡이들은 울타리 안에서만 움직입니다. 떡이가 늘어나면 필드에도 함께 등장합니다.</div><div class="row" style="margin-top:12px"><span class="pill" id="fieldCount"></span><button class="light" onclick="resetFieldPositions()">↻ 위치 섞기</button></div></div></section>
<section id="bag" class="hidden"><div class="card"><h3>🎒 아이템 가방</h3><p class="muted">선택하신 떡이에게 아이템을 사용할 수 있습니다.</p><div class="grid" id="bagItems"></div></div></section>
<section id="battle" class="hidden"><div class="card"><div class="row"><h3>🛡️ 전투 출전 인원</h3><span class="pill" id="teamCount">0/5명 선택</span></div><p class="muted">보유하신 떡이 중 1~5마리를 선택해 전투에 출전시킬 수 있습니다. 선택한 떡이만 싸우며, 힐러 능력도 출전한 떡이에게 적용됩니다.</p><div id="teamList" class="battle-team-list"></div><button id="battleStart" class="green" style="width:100%;margin-top:10px" onclick="startBattle()">⚔️ 선택한 군단으로 전투 시작</button></div>
<div class="card"><div class="row"><h3>⚔️ 군단 전투</h3><span id="clock" class="pill">0 / 30초</span></div><div class="arena" style="background:#fff3f2"><div class="row"><b>🔴 적군</b><span id="enemyHp">대기 중</span></div><div class="hpbar"><div id="enemyBar" class="hpfill" style="width:100%;background:#df6e6e"></div></div><div id="enemies" class="fighters"></div></div><div id="effect" class="center" style="min-height:30px;color:#ba6d2c;font-weight:800;margin:8px">VS</div><div class="arena"><div class="row"><b>🟢 아군</b><span id="allyCount"></span></div><div id="allies" class="fighters"></div></div><div id="result" class="center" style="font-size:18px;font-weight:800;margin:12px 0"></div><div class="grid"><button id="special" class="red" onclick="specialAttack()">💥 특수 공격</button><button class="light" onclick="showTab('farm')">🏡 마을로</button></div></div><div id="battleLog" class="card muted">전투 대기 중</div></section>
<div id="message" role="status">💬 새싹 떡이 군단에 오신 것을 환영합니다!</div><button class="light" style="margin-top:10px" onclick="resetGame()">게임 초기화</button><footer class="bottom">게임 데이터는 현재 브라우저에 저장돼.</footer>
</main>

<div id="tutorialModal" class="tutorial-overlay hidden" role="dialog" aria-modal="true" aria-labelledby="tutorialTitle">
 <div class="tutorial-panel">
  <div class="row"><h2 id="tutorialTitle">🌱 새싹 떡이 군단 안내</h2><span class="pill" id="tutorialPageCount">1 / 7</span></div>
  <div id="tutorialPageContent"></div>
  <div class="tutorial-actions">
   <button id="tutorialPrev" class="light" onclick="tutorialPrev()" disabled>이전</button>
   <button id="tutorialNext" class="green" onclick="tutorialNext()">다음</button>
  </div>
 </div>
</div>
<div id="sellModal" class="tutorial-overlay hidden" role="dialog" aria-modal="true" aria-labelledby="sellTitle">
 <div class="tutorial-panel">
  <h2 id="sellTitle">💧 떡이 판매 확인</h2>
  <div id="sellMessage"></div>
  <p class="muted">판매하면 해당 떡이는 군단에서 사라지며, 되돌릴 수 없습니다.</p>
  <div class="tutorial-actions">
   <button class="light" onclick="closeSellModal()">취소</button>
   <button class="red" onclick="confirmSellTteok()">판매하기</button>
  </div>
 </div>
</div>
<script>
const KEY='sprout_tteok_army_v3';
const MAX_SLOTS=20;
const GRADES={'보통':1,'희귀':1.5,'신화':2.2,'전설':3,'초월 5성':4.5,'최고 레벨':6};
const TOPS=['없음','딸기(불)','멜론(풀)','블루베리(물)'];
const TOPITEM={'딸기(불)':'딸기토핑','멜론(풀)':'멜론토핑','블루베리(물)':'블루베리토핑'};
const ITEMS=['회복약','딸기토핑','멜론토핑','블루베리토핑','레벨업권'];
const EMOJI=['🧪','🍓','🍈','🫐','⬆️'];
const $=id=>document.getElementById(id);
const rand=(a,b)=>Math.floor(Math.random()*(b-a+1))+a;
const safe=text=>String(text).replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));
function stats(t){let b=GRADES[t.grade]||1;t.atk=Math.floor(10*t.level*b);t.maxHp=Math.floor(100*t.level*b);t.hp=t.maxHp}
function make(name,grade){let t={name,grade,level:1,topping:'없음',healer:false};stats(t);return t}
function fresh(){return {water:5000,slots:5,inv:[make('기본 떡이','보통')],items:[],selected:0,lineup:[0],wins:0,day:1,claimedDate:'',needHeal:false}}
let game=fresh();
try{let old=JSON.parse(localStorage.getItem(KEY));if(old&&Array.isArray(old.inv)&&old.inv.length){game={...game,...old};game.slots=Math.min(MAX_SLOTS,Math.max(5,game.slots||5,game.inv.length));game.inv.forEach(t=>{if(t.topping==='소다(물)')t.topping='블루베리(물)';if(typeof t.healer!=='boolean')t.healer=!!t.is_healer;if(!Number.isFinite(t.maxHp)||!Number.isFinite(t.hp))stats(t)});game.items=(game.items||[]).map(x=>x==='소다토핑'?'블루베리토핑':x);game.lineup=Array.isArray(game.lineup)?game.lineup:[0];game.lineup=[...new Set(game.lineup.filter(i=>Number.isInteger(i)&&i>=0&&i<game.inv.length))].slice(0,5);game.selected=Math.max(0,Math.min(game.inv.length-1,game.selected||0));}}catch(e){}
let battle=null,battleTimer=null,currentTab='farm';
function save(){try{localStorage.setItem(KEY,JSON.stringify(game))}catch(e){}}
function log(m){$('message').textContent='💬 '+m}
function chosen(){return game.inv[game.selected]||game.inv[0]}
function slotPrice(){return (game.slots-3)*1000}

function tteokSVG(t,enemy=false,width=150){
 const top=t.topping||'없음';let fruit='';
 if(top==='딸기(불)')fruit=`<g transform="translate(99 33)"><path d="M0 1Q-13 -4 -11 10Q-8 24 0 27Q8 24 11 10Q13 -4 0 1Z" fill="#ee555a" stroke="#222" stroke-width="2"/><path d="M-10 2L-4 -4L0 2L5 -4L10 2" fill="#4aaf55" stroke="#222" stroke-width="1.5"/><g fill="#ffe6ae"><circle cx="-5" cy="9" r="1.4"/><circle cx="5" cy="10" r="1.4"/><circle cy="18" r="1.4"/></g></g>`;
 if(top==='멜론(풀)')fruit=`<g transform="translate(104 40)"><circle r="17" fill="#b8da89" stroke="#222" stroke-width="2"/><path d="M-14 -8Q0 3 14 -8M-15 1Q0 11 15 1M-12 9Q0 17 12 9M-7 -15Q-15 0 -7 15M7 -15Q15 0 7 15" fill="none" stroke="#83ad61" stroke-width="2"/></g>`;
 if(top==='블루베리(물)')fruit=`<g stroke="#222" stroke-width="2"><circle cx="99" cy="43" r="12" fill="#556ccf"/><circle cx="115" cy="40" r="12" fill="#5369bd"/><circle cx="109" cy="53" r="11" fill="#3e56ad"/><path d="M111 28L115 23" stroke="#3e874f" stroke-width="3"/></g>`;
 const leaf=enemy?'#c27a7a':'#67bb75';
 const level=enemy?1:Math.max(1,Math.min(5,Number(t.level)||1));

 let growth='';
 if(!enemy && level>=2){
   growth+=`<path d="M91 49Q91 25 91 3" stroke="#222" stroke-width="7" fill="none" stroke-linecap="round"/><path d="M91 23Q70 4 59 12Q60 31 91 30Z" fill="${leaf}" stroke="#222" stroke-width="6" stroke-linejoin="round"/><path d="M91 13Q108 -7 123 1Q123 20 91 23Z" fill="${leaf}" stroke="#222" stroke-width="6" stroke-linejoin="round"/>`;
 }
 if(!enemy && level>=3){
   growth+=`<path d="M91 9Q112 -10 132 -19" stroke="#222" stroke-width="6" fill="none" stroke-linecap="round"/><path d="M119 -13Q127 -34 145 -31Q151 -13 119 -13Z" fill="${leaf}" stroke="#222" stroke-width="6" stroke-linejoin="round"/>`;
 }
 if(!enemy && level===4){
   growth+=`<path d="M91 4L91 -28" stroke="#222" stroke-width="5" fill="none" stroke-linecap="round"/><path d="M91 -28Q73 -43 82 -55Q91 -61 91 -43Q101 -61 110 -55Q119 -43 91 -28Z" fill="#f3a9c1" stroke="#222" stroke-width="4" stroke-linejoin="round"/><path d="M91 -29L91 -40" stroke="#a94d70" stroke-width="2"/>`;
 }
 if(!enemy && level>=5){
   growth+=`<path d="M91 4L91 -31" stroke="#222" stroke-width="6" fill="none" stroke-linecap="round"/><g transform="translate(91 -39)" stroke="#222" stroke-width="3"><ellipse cy="-13" rx="8" ry="14" fill="#ffcf55"/><ellipse cy="13" rx="8" ry="14" fill="#ffcf55"/><ellipse cx="-13" rx="14" ry="8" fill="#ffcf55"/><ellipse cx="13" rx="14" ry="8" fill="#ffcf55"/><ellipse cx="-9" cy="-9" rx="7" ry="12" transform="rotate(-45 -9 -9)" fill="#ffd978"/><ellipse cx="9" cy="-9" rx="7" ry="12" transform="rotate(45 9 -9)" fill="#ffd978"/><circle r="8" fill="#8b5b32"/></g>`;
 }

 return `<svg viewBox="0 -68 180 198" width="${width}" aria-label="레벨 ${level} 새싹 떡이" style="display:block;max-width:100%;overflow:visible">
 <ellipse cx="91" cy="120" rx="63" ry="5" fill="#79977b" opacity=".16"/>
 ${growth}
 <path d="M91 53L80 20" stroke="#222" stroke-width="9" fill="none" stroke-linecap="round"/>
 <ellipse cx="61" cy="18" rx="27" ry="15" transform="rotate(8 61 18)" fill="${leaf}" stroke="#222" stroke-width="8"/>
 <ellipse cx="109" cy="15" rx="25" ry="15" transform="rotate(-10 109 15)" fill="${leaf}" stroke="#222" stroke-width="8"/>
 <path d="M34 69Q40 47 81 48Q122 40 151 67Q170 91 143 108Q98 130 49 108Q12 98 34 69Z" fill="#fffefa" stroke="#222" stroke-width="7" stroke-linejoin="round"/>
 ${enemy?'<path d="M65 81L75 85M116 79L106 83" stroke="#222" stroke-width="5" stroke-linecap="round"/>':'<circle cx="66" cy="83" r="5" fill="#222"/><circle cx="116" cy="77" r="5" fill="#222"/>'}
 ${fruit}</svg>`;
}
function showTab(tab){currentTab=tab;for(let t of ['farm','field','bag','battle']){$(t).classList.toggle('hidden',t!==tab);$('nav-'+t).classList.toggle('active',t===tab)}render();if(tab==='field')syncField()}
function render(){let t=chosen();$('water').textContent=game.water.toLocaleString();$('count').textContent=game.inv.length;
 let levelCost=t.level===5?500:t.level*200;
 $('levelUpBtn').innerHTML=['초월 5성','최고 레벨'].includes(t.grade)&&t.level===5?'⬆️ 최고 단계 달성':`⬆️ 레벨업 / 승급<br>💧 필요 물 ${levelCost.toLocaleString()}ml`;$('slots').textContent=game.slots;$('wins').textContent=game.wins;$('farmName').textContent=t.name+'의 농장';$('farmInfo').textContent=t.grade+' · LV.'+t.level+(t.healer?' · 힐러':'');$('mainTteok').innerHTML=tteokSVG(t,false,187);$('atk').textContent=t.atk;$('hp').textContent=t.hp+'/'+t.maxHp;$('top').textContent=t.topping;
 $('slotText').textContent=game.inv.length+' / '+game.slots+'칸';$('slotCost').textContent=game.slots>=MAX_SLOTS?'최대 20칸':`다음 슬롯: ${slotPrice().toLocaleString()}ml`;$('buySlot').disabled=game.slots>=MAX_SLOTS||game.water<slotPrice();$('buySlot').textContent=game.slots>=MAX_SLOTS?'최대 확장 완료':'💧 슬롯 +1';
 $('roster').innerHTML=Array.from({length:game.slots},(_,i)=>{let u=game.inv[i];return u?`<button class="unit ${game.selected===i?'selected':''}" data-roster="${i}">${tteokSVG(u,false,65)}<div class="grow"><b>${safe(u.name)} ${u.healer?'💚':''}</b><div class="muted truncate">${u.grade} · LV.${u.level} · ${u.topping}</div><div class="muted">ATK ${u.atk} · HP ${Math.max(0,u.hp)}/${u.maxHp}</div></div></button>`:`<div class="unit muted" style="padding:12px">＋ 빈 슬롯 ${i+1}</div>`}).join('');document.querySelectorAll('[data-roster]').forEach(el=>el.onclick=()=>{game.selected=Number(el.dataset.roster);save();render()});
 let date=new Date().toLocaleDateString('en-CA');$('attendance').disabled=game.claimedDate===date||game.day>50;$('attendance').textContent=game.claimedDate===date?'✅ 오늘 출석 완료':`📅 ${game.day}일차 출석 (+물 ${game.day===1?500:100}ml · 회복약 5개)`;
 $('bagItems').innerHTML=ITEMS.map((item,i)=>{let n=game.items.filter(x=>x===item).length;return `<button class="light" data-item="${item}" ${n?'':'disabled'}>${EMOJI[i]} ${item}<br>× ${n}</button>`}).join('');document.querySelectorAll('[data-item]').forEach(el=>el.onclick=()=>useItem(el.dataset.item));
 renderTeam();renderBattle();if(currentTab==='field')syncField();
}
function move(dir){game.selected=(game.selected+dir+game.inv.length)%game.inv.length;save();render()}
function expandSlot(){if(game.slots>=MAX_SLOTS)return log('최대 20칸이야!');let p=slotPrice();if(game.water<p)return log(`물 ${p}ml가 필요해!`);game.water-=p;game.slots++;log(`슬롯 확장! 최대 ${game.slots}마리 보유 가능.`);save();render()}
function claimAttendance(){let today=new Date().toLocaleDateString('en-CA');if(game.claimedDate===today)return log('오늘은 이미 출석했어!');if(game.day>50)return log('50일 출석 미션 완료!');let n=game.day===1?500:100;game.water+=n;game.items.push(...Array(5).fill('회복약'));game.claimedDate=today;game.day++;log(`출석 완료! 물 ${n}ml · 회복약 5개 지급.`);save();render()}
function drawTteok(){if(game.water<1000)return log('물 1,000ml가 필요해!');if(game.inv.length>=game.slots)return log('보유 슬롯이 꽉 찼어. 슬롯을 확장해!');game.water-=1000;let n=rand(1,100),msg='';if(n<=10){game.water+=500;msg='꽝! 물 500ml 반환.'}else if(n<=98){let grade=n<=60?'보통':n<=80?'희귀':n<=95?'신화':'전설';game.inv.push(make(grade+' 떡이',grade));msg=grade+' 떡이 획득!'}else{let room=game.slots-game.inv.length;let grades=['보통','희귀','신화','전설'].slice(-room);grades.forEach(g=>game.inv.push(make(g+' 떡이',g)));msg='울트라 팩! '+grades.join(', ')+' 획득!'}log(`[${n}] ${msg}`);save();render()}
function drawItem(){if(game.water<1000)return log('물 1,000ml가 필요해!');game.water-=1000;let item=ITEMS[rand(0,ITEMS.length-1)];game.items.push(item);log(item+' 획득!');save();render()}
function levelUp(){let t=chosen();if(t.level===5){if(['초월 5성','최고 레벨'].includes(t.grade))return log('이미 최고 단계야!');const cost=500;if(game.water<cost)return log(`승급에 물 ${cost}ml가 필요해! (현재 ${game.water.toLocaleString()}ml)`);game.water-=cost;t.grade=t.grade==='전설'?'최고 레벨':'초월 5성';stats(t);log(`${t.name} 승급! ${t.grade} · 물 ${cost}ml 사용`)}else{const cost=t.level*200;if(game.water<cost)return log(`레벨업에 물 ${cost}ml가 필요해! (현재 ${game.water.toLocaleString()}ml)`);game.water-=cost;t.level++;stats(t);log(`${t.name} LV.${t.level} 달성! · 물 ${cost}ml 사용`)}save();render()}
function toggleHealer(){let t=chosen();t.healer=!t.healer;log(`${t.name} ${t.healer?'힐러 등록!':'힐러 해제!'}`);save();render()}
function cycleTopping(){let t=chosen(),pos=TOPS.indexOf(t.topping);for(let j=1;j<=4;j++){let next=TOPS[(pos+j)%4];if(next==='없음'){if(t.topping!=='없음')game.items.push(TOPITEM[t.topping]);t.topping='없음';log('토핑을 가방에 넣었어.');save();render();return}let item=TOPITEM[next],idx=game.items.indexOf(item);if(idx>=0){if(t.topping!=='없음')game.items.push(TOPITEM[t.topping]);game.items.splice(game.items.indexOf(item),1);t.topping=next;log(next+' 장착!');save();render();return}}log('장착할 토핑이 없어!')}
function rename(){$('renameArea').classList.toggle('hidden');$('newName').value=chosen().name}
function saveName(){let name=$('newName').value.trim().slice(0,15);if(!name)return log('이름을 입력해!');chosen().name=name;$('renameArea').classList.add('hidden');log('이름 변경 완료!');save();render()}
function useItem(item){let i=game.items.indexOf(item);if(i<0)return;let t=chosen();if(item==='회복약'){if(t.hp>=t.maxHp)return log('체력이 가득 차 있어!');t.hp=t.maxHp;game.items.splice(i,1);if(game.inv.every(x=>x.hp>0))game.needHeal=false;log(t.name+' 체력 회복!')}else if(item==='레벨업권'){if(t.level>=5)return log('LV.5는 승급을 해야 해!');game.items.splice(i,1);t.level++;stats(t);log(t.name+' 레벨업!')}else{let next=Object.keys(TOPITEM).find(x=>TOPITEM[x]===item);if(t.topping!=='없음')game.items.push(TOPITEM[t.topping]);game.items.splice(game.items.indexOf(item),1);t.topping=next;log(next+' 장착!')}save();render()}

function renderTeam(){let locked=!!(battle&&!battle.finished);$('teamCount').textContent=game.lineup.length+'/5명 선택';$('teamList').innerHTML=game.inv.map((t,i)=>`<label class="team-unit ${game.lineup.includes(i)?'selected':''}"><input type="checkbox" data-team="${i}" ${game.lineup.includes(i)?'checked':''} ${locked?'disabled':''}>${tteokSVG(t,false,55)}<span class="grow"><b>${safe(t.name)}</b><span class="muted" style="display:block">${t.grade} · LV.${t.level} · HP ${t.maxHp} ${t.healer?'· 💚 힐러':''}</span></span></label>`).join('');document.querySelectorAll('[data-team]').forEach(box=>box.onchange=()=>toggleTeam(Number(box.dataset.team)));$('battleStart').disabled=locked||game.lineup.length===0;$('battleStart').textContent=locked?'전투 진행 중':`⚔️ 선택한 ${game.lineup.length}마리로 전투 시작`}
function toggleTeam(i){if(battle&&!battle.finished)return log('전투 중에는 출전 인원을 변경할 수 없어.');let p=game.lineup.indexOf(i);if(p>=0)game.lineup.splice(p,1);else if(game.lineup.length>=5)return log('출전할 수 있는 떡이는 최대 5마리야!');else game.lineup.push(i);save();renderTeam()}
function advantage(a,b){return a==='딸기(불)'&&b==='멜론(풀)'||a==='멜론(풀)'&&b==='블루베리(물)'||a==='블루베리(물)'&&b==='딸기(불)'}
function startBattle(){if(battle&&!battle.finished)return log('진행 중인 전투가 있어!');let team=game.lineup.filter(i=>i>=0&&i<game.inv.length).slice(0,5);if(!team.length)return log('출전할 떡이를 1마리 이상 선택해!');if(game.needHeal){let i=game.items.indexOf('회복약');if(i<0)return log('패배 상태야! 회복약이 필요해!');game.items.splice(i,1);game.needHeal=false}team.forEach(i=>game.inv[i].hp=game.inv[i].maxHp);let max=team.reduce((sum,i)=>sum+game.inv[i].maxHp,0);battle={team,enemies:team.map(()=>TOPS[rand(0,3)]),frames:0,maxHp:max,hp:max,cooldown:0,finished:false,result:'',effect:'VS',log:'전투 시작!'};showTab('battle');battleTimer=setInterval(battleTick,1000/30);log('전투 시작!');save()}
function finishBattle(win,message){if(!battle||battle.finished)return;battle.finished=true;if(win){let reward=rand(500,1500);game.water+=reward;game.wins++;battle.result=message+` (+${reward}ml)`}else{game.needHeal=true;battle.result=message}battle.log=battle.result;clearInterval(battleTimer);battleTimer=null;save();render()}
function battleTick(){let b=battle;if(!b||b.finished)return;b.frames++;if(b.cooldown>0)b.cooldown--;if(b.frames%30===0){b.team.forEach((index,i)=>{let t=game.inv[index];if(t.hp<=0)return;if(advantage(b.enemies[i],t.topping)&&rand(1,100)<=25){t.hp=0;b.log=t.name+' 상성 공격으로 쓰러짐!';return}t.hp=Math.max(0,t.hp-rand(5,12));b.hp-=rand(4,10)});if(b.hp<=0){b.hp=0;finishBattle(true,'전투 승리!');return}if(b.team.every(i=>game.inv[i].hp<=0)){finishBattle(false,'전멸! 전투 패배!');return}}if(b.frames%150===0){b.team.forEach(i=>{let h=game.inv[i];if(!h.healer||h.hp<=0)return;b.team.forEach(j=>{let t=game.inv[j];if(t.hp>0&&t.topping===h.topping)t.hp=Math.min(t.maxHp,t.hp+Math.max(1,Math.floor((t.maxHp-t.hp)/2)))})})}if(b.frames>=900){finishBattle(false,'30초 시간 초과! 패배!');return}if(b.frames%6===0)renderBattle()}
function specialAttack(){let b=battle;if(!b||b.finished)return;if(b.cooldown>0)return log('특수 공격 대기 중!');b.cooldown=150;let damage=0,critical=false;b.team.forEach((idx,i)=>{let t=game.inv[idx];if(t.hp<=0)return;if(t.topping!=='없음'&&advantage(t.topping,b.enemies[i])&&rand(1,100)<=25){damage+=b.maxHp;critical=true}else damage+=rand(30,60)});b.hp=Math.max(0,b.hp-damage);b.effect=critical?'💥 CRITICAL HIT!':'💥 '+damage+' 피해!';b.log=b.effect;if(b.hp<=0)finishBattle(true,critical?'치명타 즉사 승리!':'특수 공격 승리!');renderBattle()}
function renderBattle(){let b=battle;if(!b){$('clock').textContent='0 / 30초';$('enemyHp').textContent='대기';$('enemyBar').style.width='100%';$('enemies').textContent='전투 전';$('allies').textContent='출전 인원을 선택해';$('effect').textContent='VS';$('result').textContent='';$('special').disabled=true;return}$('clock').textContent=Math.floor(b.frames/30)+' / 30초';$('enemyHp').textContent=Math.ceil(Math.max(0,b.hp))+' / '+b.maxHp+' HP';$('enemyBar').style.width=Math.max(0,100*b.hp/b.maxHp)+'%';$('enemies').innerHTML=b.enemies.map(top=>`<div class="fighter">${tteokSVG({topping:top},true,65)}</div>`).join('');$('allies').innerHTML=b.team.map(i=>{let t=game.inv[i];return `<div class="fighter ${t.hp<=0?'dead':''}">${tteokSVG(t,false,65)}<div class="hpbar"><div class="hpfill" style="width:${Math.max(0,100*t.hp/t.maxHp)}%"></div></div><div class="truncate">${safe(t.name)}</div></div>`}).join('');$('allyCount').textContent=b.team.filter(i=>game.inv[i].hp>0).length+'/'+b.team.length+' 생존';$('effect').textContent=b.effect;$('result').textContent=b.result;$('battleLog').textContent=b.log;$('special').disabled=b.finished||b.cooldown>0;$('special').textContent=b.finished?'전투 종료':b.cooldown>0?'쿨타임 '+Math.ceil(b.cooldown/30)+'초':'💥 특수 공격'}

const AGENT_W=78,AGENT_H=77;
let agents=[],lastFrame=0;
function syncField(){if(currentTab!=='field')return;let area=$('fieldArea');if(!area.clientWidth)return;let changed=agents.length!==game.inv.length;if(!changed){for(let i=0;i<agents.length;i++)if(agents[i].name!==game.inv[i].name||agents[i].topping!==game.inv[i].topping||agents[i].level!==game.inv[i].level){changed=true;break}}if(!changed)return;area.innerHTML='';agents=game.inv.map((t,i)=>{let node=document.createElement('div');node.className='field-agent';node.innerHTML=tteokSVG(t,false,78)+`<div class="agent-name">${safe(t.name)}</div>`;area.appendChild(node);let w=Math.max(0,area.clientWidth-AGENT_W),h=Math.max(0,area.clientHeight-AGENT_H);let jumping=(i%3===0||i%4===1);return {node,name:t.name,topping:t.topping,level:t.level,jumping,x:rand(0,Math.floor(w)),y:rand(42,Math.max(42,Math.floor(h))),vx:(Math.random()<.5?-1:1)*rand(18,48),vy:(Math.random()<.5?-1:1)*rand(12,35),phase:Math.random()*6.28,speed:2.8+Math.random()*2.2}});$('fieldCount').textContent=agents.length+'마리가 필드에 있어'}
function resetFieldPositions(){agents=[];syncField();log('떡이들이 새 위치로 이동했어!')}
function animateField(time){let dt=Math.min(.04,(time-(lastFrame||time))/1000);lastFrame=time;if(currentTab==='field'&&agents.length){let area=$('fieldArea'),w=Math.max(0,area.clientWidth-AGENT_W),h=Math.max(42,area.clientHeight-AGENT_H);for(let a of agents){a.x+=a.vx*dt;a.y+=a.vy*dt;if(a.x<0){a.x=0;a.vx=Math.abs(a.vx)}if(a.x>w){a.x=w;a.vx=-Math.abs(a.vx)}if(a.y<42){a.y=42;a.vy=Math.abs(a.vy)}if(a.y>h){a.y=h;a.vy=-Math.abs(a.vy)}a.phase+=a.speed*dt;let jump=a.jumping?Math.abs(Math.sin(a.phase))*31:0;let py=Math.max(0,Math.min(h,a.y-jump));a.node.style.transform=`translate3d(${a.x}px,${py}px,0)`}}requestAnimationFrame(animateField)}
requestAnimationFrame(animateField);
function resetGame(){if(!confirm('정말로 초기화하시겠습니까?'))return;if(battleTimer)clearInterval(battleTimer);battleTimer=null;battle=null;game=fresh();agents=[];save();showTab('farm');log('새 게임을 시작했어!')}
const SALE_BASE={'보통':100,'희귀':200,'신화':300,'전설':400,'초월 5성':500,'최고 레벨':600};
let pendingSale=null;
function salePriceInfo(t){
 const base=SALE_BASE[t.grade]||100;
 const effectiveLevel=t.grade==='초월 5성'?6:(Number(t.level)||1);
 const core=base+effectiveLevel*20;
 return {min:Math.max(0,core-50),max:core+50,amount:Math.max(0,core+rand(-50,50))};
}
function askSellTteok(){
 const t=chosen();
 if(!t)return log('판매할 떡이를 선택해 주세요.');
 if(game.inv.length<=1)return log('마지막 떡이는 판매할 수 없습니다. 군단에 최소 한 마리는 남겨 주세요.');
 const price=salePriceInfo(t);
 pendingSale={index:game.selected,name:t.name,amount:price.amount};
 
 // ▼ 확정 지급 금액 표시 부분을 삭제한 영역입니다[span_1](start_span)[span_1](end_span)
 $('sellMessage').innerHTML=`<div>정말 <b>${safe(t.name)}</b>을(를) 판매하시겠습니까?</div><div style="margin-top:8px">예상 판매 금액: <b>${price.min.toLocaleString()}~${price.max.toLocaleString()}ml</b></div>`;
 
 $('sellModal').classList.remove('hidden');
}
function closeSellModal(){pendingSale=null;$('sellModal').classList.add('hidden')}
function confirmSellTteok(){
 if(!pendingSale)return;
 const {index,name,amount}=pendingSale;
 if(!game.inv[index]||game.inv.length<=1){closeSellModal();return log('판매할 수 없습니다.');}
 game.water+=amount;game.inv.splice(index,1);
 game.selected=Math.max(0,Math.min(game.inv.length-1,index>0?index-1:0));
 game.lineup=(game.lineup||[]).filter(i=>i!==index).map(i=>i>index?i-1:i);
 if(!game.lineup.length)game.lineup=[game.selected];
 if(battle) { }
 closeSellModal();save();render();syncField();log(`${name} 판매 완료! 물 ${amount.toLocaleString()}ml를 받았습니다.`);
}
const tutorialPages=[
 `<div class="tutorial-page"><h3>🌱 환영합니다!</h3><p>새싹 떡이 군단에 오신 것을 환영합니다!</p><p>떡이를 모으고 성장시키며 농장과 필드, 전투를 즐겨 보세요.</p></div>`,
 `<div class="tutorial-page"><h3>🏡 농장과 떡이 관리</h3><p>보유한 떡이를 선택하고 이름, 토핑, 힐러 능력을 관리할 수 있습니다.</p><p>떡이는 레벨업할수록 강해집니다. 레벨업 버튼에서 필요한 물의 양을 확인해 주세요.</p></div>`,
 `<div class="tutorial-page"><h3>💧 물과 뽑기</h3><p>물은 떡이 뽑기, 아이템 뽑기, 레벨업과 승급에 사용됩니다.</p><p>출석 보상으로 물과 아이템을 받을 수도 있습니다.</p></div>`,
 `<div class="tutorial-page"><h3>🌿 필드</h3><p>보유하신 떡이들이 필드에서 자유롭게 움직입니다.</p><p>어떤 떡이들은 폴짝폴짝 뛰기도 합니다. 떡이가 늘어나면 필드에도 함께 등장합니다.</p></div>`,
 `<div class="tutorial-page"><h3>🎒 가방과 ⚔️ 전투</h3><p>가방에서는 선택한 떡이에게 아이템을 사용할 수 있습니다.</p><p>전투에는 1~5마리의 떡이를 출전시킬 수 있습니다. 선택한 떡이만 전투에 참여합니다.</p></div>`,
 `<div class="tutorial-page"><h3>💧 떡이 판매</h3><p>농장의 <b>떡이 관리</b>에서 선택한 떡이를 판매할 수 있습니다.</p><p>판매 금액은 등급별 기본 금액(보통 100ml, 희귀 200ml, 신화 300ml, 전설 400ml, 초월 5성 500ml, 최고 레벨 600ml)에 레벨 × 20ml를 더한 뒤, 50ml를 더하거나 뺀 금액입니다.</p><p>초월 5성은 판매 계산에서 6레벨로 취급합니다. 판매 전 확인 창에서 지급 금액을 확인할 수 있으며, 마지막 떡이는 판매할 수 없습니다.</p></div>`,
 `<div class="tutorial-page"><h3>⚠️ 저장과 초기화</h3><p>게임 데이터는 현재 브라우저에 저장됩니다.</p><p>게임 초기화를 선택하면 확인 창이 표시됩니다. 확인하면 저장된 진행 상황이 삭제되므로 주의해 주세요.</p><p>이제 게임을 시작해 보세요!</p></div>`
];
let tutorialPage=0;
function renderTutorialPage(){
 $('tutorialPageContent').innerHTML=`<div class="tutorial-progress"><span style="width:${(tutorialPage+1)/tutorialPages.length*100}%"></span></div>`+tutorialPages[tutorialPage];
 $('tutorialPageCount').textContent=(tutorialPage+1)+' / '+tutorialPages.length;
 $('tutorialPrev').disabled=tutorialPage===0;
 $('tutorialNext').textContent=tutorialPage===tutorialPages.length-1?'확인했습니다':'다음';
}
function openTutorial(){tutorialPage=0;renderTutorialPage();$('tutorialModal').classList.remove('hidden')}
function tutorialPrev(){if(tutorialPage>0){tutorialPage--;renderTutorialPage()}}
function tutorialNext(){if(tutorialPage<tutorialPages.length-1){tutorialPage++;renderTutorialPage()}else closeTutorial()}
function closeTutorial(){$('tutorialModal').classList.add('hidden');try{localStorage.setItem('sprout_tutorial_seen','1')}catch(e){}}
showTab('farm');
try{if(!localStorage.getItem('sprout_tutorial_seen'))openTutorial()}catch(e){openTutorial()}
</script>
</body>
</html>
