html = "<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport"
content="width=device-width, initialscale=1.0">
<title>ORBIT.IO - JEE Physics</title>
<link href="https://fonts.googleapis.com/
css2?
family=Space+Grotesk:wght@400;600;700
&family=Inter:wght@400;500&family=JetBr
ains+Mono:wght@400&display=swap"
rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/
ajax/libs/three.js/r128/three.min.js"></
script>
<style>
:root{--bg:#0a0a0a;--bg2:#111;-
bg3:#141414;--text:#fff;--text2:#a0a0a0;--
text3:#666;--border:#222;--
border2:#2a2a2a}
*{margin:0;padding:0;box-sizing:borderbox}
body{font-family:'Inter', sansserif;background:var(--bg);color:var(--
text);height:100vh;overflow:hidden}
/* Top Bar */
.top{position:fixed;top:0;left:0;right:0;height:
56px;background:var(--bg2);borderbottom:1px solid var(--
border);display:flex;alignitems:center;justify-content:spасеbetween;padding:0 24px;z-index:100}
.logo{display:flex;alignitems:center;gap:10px;cursor:pointer}
.logo
span{width:30px;height:30px;background:#
fff;color:#000;borderradius:6px;display:flex;align-
items:center;justify-content:center;fontfamily:'Space Grotesk';font-weight:700;fontsize:13px}
.logo h1{font-family:'Space Grotesk';fontsize:17px;letter-spacing:2px;fontweight:600}
.chapter{position:relative}
.chapter>div{display:flex;alignitems:center;gap:8px;padding:8px
14px;background:var(--bg3);border:1px
solid var(--border);borderradius:8px;cursor:pointer;fontsize:13px;color:var(--text2)}
.chapter>div:hover{border-color:var(--
text3)}
.dropdown{position:absolute;top:calc(100%
+6px);left:0;width:320px;background:var(--
bg2);border:1px solid var(--border);borderradius:10px;padding:6px;display:none;fleхdirection:column;gap:2px;maxheight:350px;overflow-y:auto;box-
shadow:0 20px 50px rgba(0,0,0,.8);zindex:200}
.dropdown.show{display:flex}
.dropdown div{padding:10px 12px;borderradius:6px;font-size:12px;color:var(--
text2);cursor:pointer;display:flex;gap:10px}
.dropdown div:hover{background:var(--
bg3);color:var(--text)}
.dropdown div.active{background:var(--
bg3);color:var(--text);border-left:2px solid
#fff}
.dropdown div span:first-child{fontfamily:'JetBrains Mono';color:var(--
text3);min-width:22px}
.actions{display:flex;gap:8px}
.btn{width:34px;height:34px;borderradius:8px;border:1 px solid var(--
border);background:var(--bg3);color:var(--
text2);display:flex;align-items:center;justifycontent:center;cursor:pointer}
.btn:hover{border-color:var(--
text3);color:var(--text)}
.btn.active{border-color:#fff;color:#fff}
/* Main */
.main{position:fixed;top:56px;left:0;right:0;b
ottom:64px;display:flex}
.left{width:42%;border-right:1px solid var(--
border);overflow-y:auto;padding:28px 36px}
.left::-webkit-scrollbar{width:5px}
.left::-webkit-scrollbarthumb{background:var(--border);borderradius:3px}
.left h2{font-family:'Space Grotesk';fontsize:11px;color:var(--text3);letterspacing:3px;texttransform:uppercase;margin-bottom:16px}
.left h1{font-family:'Space Grotesk';fontsize:24px;font-weight:700;marginbottom:8px;line-height:1.2}
.tags{display:flex;flexwrap:wrap;gap:6px;margin-bottom:24px}
.tag{padding:5px 12px;background:var(--
bg3);border:1px solid var(--border);borderradius:50px;font-size:11px;color:var(--
text3);cursor:pointer}
.tag:hover{border-color:var(--
text3);color:var(--text2)}
.content p{font-size:13.5px;lineheight:1.8;color:var(--text2);marginbottom:14px}
.content .key{color:var(--text);fontweight:600;border-bottom:1px dashed
var(--text3);cursor:help}
.formula{background:var(--bg3);border:1px
solid var(--border);borderradius:10px;padding:16px
20px;margin:16px 0;font-family:'JetBrains
Mono';font-size:13px;position:relative}
.formula::before{content:";position:absolute
;left:0;top:0;bottom:0;width:3px;background
:#fff}
.formula .expr{color:#fff;font-
size:14px;margin-bottom:6px}
.formula .lbl{font-family:'Inter';fontsize:11px;color:var(--text3);font-style:italic}
.insight{background:var(--bg3);border:1px
solid var(--border2);borderradius:10px;padding:20px;margin:20px 0}
.insight h4{font-family:'Space Grotesk';fontsize:11px;color:var(--text3);letterspacing:2px;texttransform:uppercase;margin-bottom:10px}
.insight p{font-size:13px;lineheight:1.7;color:var(--text2);margin:0}
.ref{color:var(--text3);font-size:11px;margintop:24px;padding-top:16px;border-top:1 px
solid var(--border)}
/* Right - 3D */
.right{width:58%;position:relative}
.right
.header{position:absolute;top:20px;left:28p
x;right:28px;z-index:10;display:flex;justify-
content:space-between;alignitems:center;pointer-events:none}
.right .header span{font-family:'Space
Grotesk';font-size:11px;color:var(--
text3);letter-spacing:3px;texttransform:uppercase}
.axes{display:flex;gap:6px;pointerevents:all}
.axes
button{width:36px;height:36px;borderradius:8px;border:1px solid var(--
border);background:var(--bg3);color:var(--
text3);font-family:'JetBrains Mono';fontsize:13px;font-weight:600;cursor:pointer)
axes button:hover{border-color:var(--
text3);color:var(--text2)}
.axes button.on{border-color:#fff;color:#fff}
canvas{width:100%;height:100%;display:blo
ck;cursor:grab}
canvas:active{cursor:grabbing}
.overlay{position:absolute;bottom:20px;left:
28px;right:28px;display:flex;justifycontent:space-between;align-items:flexend;pointer-events:none}
.legend{display:flex;flexdirection:column;gap:6рх}
.legend div{display:flex;alignitems:center;gap:6px;fontsize:11px;color:var(--text3)}
.legend div i{width:7px;height:7px;borderradius:50%;display:block}
.params{background:var(--bg3);border:1px
solid var(--border);borderradius:10px;padding:14px 18px;pointerevents:all;min-width:200px}
.params div{display:flex;justifycontent:space-between;padding:6px
0;border-bottom:1px solid var(--
border);font-size:11px}
.params div:last-child{border:none}
.params div span:first-child{color:var(--
text3);text-transform:uppercase;letter-
spacing:1px}
.params div span:last-child{fontfamily:'JetBrains Mono';color:#fff}
/* Bottom */
.bottom{position:fixed;bottom:0;left:0;right:
0;height:64px;background:var(--
bg2);border-top:1px solid var(--
border);display:flex;alignitems:center;justify-content:spaсеbetween;padding:0 24px;z-index:100}
.search{display:flex;alignitems:center;gap:8px;background:var(--
bg);border:1px solid var(--border);borderradius:8px;padding:9px 14px;width:260px}
.search
input{background:none;border:none;outline
:none;color:#fff;font-size:13px;width:100%}
.search input::placeholder{color:var(--
text3)}
.tabs{display:flex;gap:4px}
.tab{display:flex;flex-direction:column;alignitems:center;gap:3px;padding:7px
18px;border-radius:10px;border:1px solid
transparent;background:transparent;color:v
ar(--text3);cursor:pointer;fontsize:10px;font-weight:600;letterspacing:1px;text-transform:uppercase}
.tab:hover{background:var(--
bg3);color:var(--text2)}
.tab.on{background:var(--bg3);bordercolor:var(--
border2);color:#fff;position:relative}
.tab.on::after{content:";position:absolute;bo
ttom:-3px;left:50%;transform:translateX(-50
%);width:18px;height:2px;background:#fff;b
order-radius:1px}
.time{font-family:'JetBrains Mono';fontsize:12px;color:var(--text3)}
/* Sidebar */
.overlay2{position:fixed;inset:0;background:
rgba(0,0,0,.6);z-index:99;display:none}
.overlay2.show{display:block}
.sidebar{position:fixed;top:56px;right:0;bott
om:64px;width:360px;background:var(--
bg2);border-left:1px solid var(--border);zindex:100;transform:translateX(100%);trans
ition:transform .35s;display:flex;flexdirection:column}
.sidebar.show{transform:translateX(0)}
.sidebar .head{padding:18px 22px;borderbottom:1px solid var(--
border);display:flex;justify-content:spacebetween;align-items:center}
.sidebar .head h3{font-family:'Space
Grotesk';font-size:13px;letterspacing:2px;text-transform:uppercase}
.sidebar .head
button{width:30px;height:30px;borderradius:6px;border:1px solid var(--
border);background:var(--bg3);color:var(--
text2);display:flex;align-items:center;justify-
content:center;cursor:pointer}
.sidebar.head button:hover{bordercolor:#fff;color:#fff}
.sidebar .body{flex:1;overflowy:auto;padding:18px 22px}
.note{padding:12px;background:var(--
bg3);border:1px solid var(--border);borderradius:8px;marginbottom:8px;cursor:pointer}
.note:hover{border-color:var(--text3)}
.note h4{font-size:12px;margin-bottom:3px}
.note p{font-size:11px;color:var(--text3)}
.sidebar .foot{padding:14px 22px;bordertop:1px solid var(--border)}
.sidebar .foot
button{width:100%;padding:10px;backgrou
nd:var(--bg3);border:1px solid var(--
border);border-radius:8px;color:var(--
text2);font-size:12px;fontweight:600;cursor:pointer;display:flex;alignitems:center;justify-content:center;gap:6рx}
.sidebar .foot button:hover{bordercolor:#fff;color:#fff}
@media(max-width:900px)
{.left{width:50%;padding:20px}.right{width:
50%}}
@media(max-width:700px){.main{flexdirection:column}.left{width:100%;height:50
%;border-right:none;border-bottom:1px
solid var(--
border)}.right{width:100%;height:50%}.tabs{
display:none}}
</style>
</head>
<body>
<div class="top">
<div class="logo" onclick="load('systemparticles')">
<span>O</span>
<h1>ORBIT.IO</h1>
</div>
<div class="chapter"
<div onclick="toggleDropdown()">
<span id="ch-title">System of Particles
& Rotational Motion</span>
<svg width="14" height="14"
viewBox="0 0 24 24" fill="none"
stroke="currentColor" strokewidth="2"><polyline points="6 9 12 15 18
9"/></svg>
</div>
<div class="dropdown" id="dropdown">
<div onclick="load('unitsdimensions')"><span>01</
span><span>Units and Measurements</
span></div>
<div onclick="load('motion-straightline')"><span>02</span><span>Motion in
a Straight Line</span></div>
<div onclick="load('motionplane')"><span>03</span><span>Motion
in a Plane</span></div>
<div onclick="load('lawsmotion')"><span>04</span><span>Laws
of Motion</span></div>
<div onclick="load('workenergy')"><span>05</span><span>Work,
Energy and Power</span></div>
<div class="active"
onclick="load('systemparticles')"><span>06</
span><span>System of Particles &
Rotational Motion</span></div>
<div
onclick="load('gravitation')"><span>07</
span><span>Gravitation</span></div>
</div>
</div>
<div class="actions">
<button class="btn" id="note-btn'"
onclick="toggleSidebar()" title="Notes">
<svg width="16" height="16"
viewBox="0 0 24 24" fill="none"
stroke="currentColor" strokewidth="2"><path d="M14 2H6а2 2 0 0 0-2
2v16a2 20002 2h12a22000 2-2V8z"/
><polyline points="14 2 14 8 20 8"/><line
x1="16" y1="13" x2="8" y2="13"/><line
x1="16" y1="17" x2="8" y2="17"/></svg>
</button>
<button class="btn"
onclick="alert('Menu: Bookmarks,
Downloads, Study Planner (coming
soon!)')" title="Menu">
<svg width="16" height="16"
viewBox="0 0 24 24" fill="none"
stroke="currentColor" strokewidth="2"><line x1="3" y1="12" x2="21"
y2="12"/><line x1="3" y1="6" x2="21"
y2="6"/><line x1="3" y1="18" x2="21"
y2="18"/></svg>
</button>
<button class="btn"
onclick="alert('Profile: 12 day streak, 3/7
chapters, 48h study time (coming soon!)')"
title="Profile">
<svg width="16" height="16"
viewBox="0 0 24 24" fill="none"
stroke="currentColor" strokewidth="2"><path d="M20 21v-2a4 4 00
0-4-4H8a4 4 0 0 0-4 4v2"/><circle cx="12"
cy="7" r="4"/></svg>
</button>
</div>
</div>
<div class="overlay2" id="overlay2"
onclick="toggleSidebar()"></div>
<div class="sidebar" id="sidebar">
<div class="head">
<h3>My Notes</h3>
<button onclick="toggleSidebar()">
<svg width="14" height="14"
viewBox="0 0 24 24" fill="none"
stroke="currentColor" strokewidth="2"><line x1="18" y1="6" x2="6"
y2="18"/><line x1="6" y1="6" x2="18"
y2="18"/></svg>
</button<
</div>
<div class="body" id="note-list">
<div class="note"><h4>lmportant
Formula</h4><p>torque = r x F for all
calculations</p></div>
<div class="note"><h4>Doubt</
h4><p>Why does precession decrease
with faster spin?</p></div>
<div class="note"><h4>Shortcut</
h4><p>Rolling without slipping: v = rw
always</p></div>
</div>
<div class="foot"
<button onclick="addNote()">
<svg width="14" height="14"
viewBox="0 0 24 24" fill="none"
stroke="currentColor" strokewidth="2"><line x1="12" y1="5" x2="12"
y2="19"/><line x1="5" y1="12" x2="19"
y2="12"/></svg>
Add Note
</button>
</div>
</div>
<div class="main">
<div class="left" id="left">
<h2>PHYSICS ACTIVE STUDY</h2>
<h1 id="title">System of Particles &
Rotational Motion</h1>
<div class="tags" id="tags"></div>
<div class="content" id="content"></div>
</div>
<div class="right">
<div class="header">
<span id="viz-name">Rotational
Dynamics Visualizer</span>
<div class="axes">
<button class="on"
onclick="setAxis('x',this)">X</button>
<button onclick="setAxis('y',this)">Y</
button>
<button onclick="setAxis('z',this)">Z</
button>
<button onclick="setAxis('t',this)">t</
button>
</div>
</div>
<canvas id="c"></canvas<
<div class="overlay">
<div class="legend" id="legend"></div>
<div class="params" id="params"></div>
</div>
</div>
</div>
<div class="bottom">
<div class="search">
<svg width="14" height="14" viewBox="0
0 24 24" fill="none" stroke="currentColor"
stroke-width="2"><circle cx="11" cy="11"
r="8"/><line x1="21" y1="21" x2="16.65"
y2="16.65"/></svg>
<input type="text" placeholder="Search
topics..." id="search"
oninput="doSearch(this.value)">
</div>
<div class="tabs">
<button class="tab on"
onclick="setTab(this)">Notes</button>
<button class="tab"
onclick="setTab(this);alert('Profile coming
soon!')">Profile</button>
<button class="tab"
onclick="setTab(this);alert('SEAMS coming
soon!')">Seams</button>
</div>
<div style="display:flex;alignitems:center;gap:12px">
<span class="time" id="time">00:00</
span>
<button class="btn"
onclick="alert('Settings: Theme, Font,
Notifications (coming soon!)')">
<svg width="14" height="14"
viewBox="0 0 24 24" fill="none"
stroke="currentColor" strokewidth="2"><circle cx="12" cy="12" r="3"/
><path d="M19.4 15a1.65 1.65 000.33
1.821.06.06a2 2 00102.83
0 0-1.82-.33 1.65
2 2 00 1-2.83
01-.06-.06a1.65 1.65 0
1.6500 0-1 1.51V21a222001-222200
1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65
1.6500 0-1.82.33-.06.06a2 2 00 1-2.83
22001 0-2.83I.06-.06A1.65 1.65000
4.67 15a1.65 1.65000-1.51-1H3a2 2 00
1-2-2 2 20012-2h.09A1.65 1.65000
4.67 9a1.65 1.65000-.33-1.821-.06-.06a2
이
20010-2.83 22001 2.83 0l.06.06A1.65
1.6500 09 4.67a1.65 1.650 00
1-1.51V3a2 2 0 0 1 2-2 220012
2v.09a1.65 1.650 이 1 1.51
0 1.82-.331.06-.06a2 2 001
10 2.83l-.06.06a1.65 1.65 0
1.65 1.6500
2.83 0 2200
이 0-.33
1.82V9a1.65 1.65000 1.51 1H21a2 2 00
12222001-2 2h-.09a1.65 1.6500
0-1.51 1z"/></svg>
</button>
</div>
</div>
<script>
// CHAPTER DATA
const DATA={
"units-dimensions":{t:"Units and
Measurements", topics:["SI
Units","Dimensions","Error
Analysis","Significant
Figures"],viz:"Measurement
Visualizer",type:"measure"
theory:`<p>The study of physics begins
with measurement. A <span
class="key">unit</span> is a standard
(A),
quantity. The <span class="key">SI
system</span> has seven base units:
length (m), mass (kg), time (s), current
temperature (K), amount (mol), and
luminous intensity (cd).</p><p><span
class="key">Fundamental quantities</
span> are independent. <span
class="key">Derived quantities</span> like
velocity (m/s), force (kg.m/s²), and energy
(kg.m²/s²) are expressed in terms of
fundamentals.</p>,
formulas:[{e:"[F] = M1L1T-2",I:"Dimensional
formula for Force"},{e:"n2 = n₁(M1/M2)a(L₁/
L2)b(T1/T2) c",I:"Unit conversion"},{e:"% error
= |Ax/x| × 100",l:"Percentage error"}],
insight:"Dimensional analysis checks
equation correctness and derives
relationships. It cannot find dimensionless
constants.",
params:["L = 2.45 m""M = 0.500 kg","T =
1.23 s""±0.01"],
legend:["#fff|Base Unit","#888|Derived
Unit""#444|Dimension"]}.
"motion-straight-line":{t:"Motion in a
Straight Line",topics:
["Kinematics""Graphs","Relative
Velocity","Free Fall"],viz:"Kinematic
Simulator",type:"kinematic"
theory:`<p>Motion is described by <span
class="key">position</span>, <span
class="key">displacement</span>, <span
class="key">velocity</span>, and <span
class="key">acceleration</span>.
Displacement is the change in position
(vector). Distance is the total path length
(scalar).</p><p>For <span
class="key">uniformly accelerated
motion</span>, kinematic equations relate
initial velocity (u), final velocity (v),
acceleration (a), displacement (s), and
time (t).</p>
formulas:[{e:"v'v == u + at",I:"Velocity-time"},
{e:"s = ut + 2at²",I:"Displacement-time"},
{e:"v² = u² + 2as",l:"Velocity-displacement"},
{e:"Sn = u + a(n - 12)",I:"nth second
displacement"}],
insight:"Slope of position-time graph =
velocity. Slope of velocity-time graph =
acceleration. Area under velocity-time
graph = displacement."
params:["u = 15.0 m/s","a = 2.5 m/s²""t =
4.0 s""s = 80.0 m"],
legend:["#fff|Position""#888|
Velocity""#444|Acceleration"]},
"motion-plane":{t:"Motion in a Plane",topics:
["Vectors","Projectile""Circular
Motion","Relative Motion"],viz:"Projectile
Lab",type:"projectile",
theory:`<p>2D motion needs <span
class="key">vector analysis</span>.
Vectors have magnitude and direction.
<span class="key">Projectile motion</
span> has horizontal motion (constant
velocity) and vertical motion (constant
acceleration g).</p><p><span
class="key">Circular motion</span> has
centripetal acceleration directed toward
the center: a = v²/r.</p>`,
formulas:[{e:"R = (u² sin 20)/g",l:"Horizontal
range"},{e:"H = (u² sin²0)/2g",l:"Max height"},
{e:"T = (2u sin 0)/g",I:"Time of flight"},
{e:"a_c = v²/r = w²r",I:"Centripetal
acceleration"}],
insight:"At 45°, range is maximum. For
complementary angles (0 and 90°-0),
range is identical.",
params:["u = 25.0 m/s""0 = 45°""R = 63.8
m","H = 15.9 m"],
legend:["#fff|Trajectory""#888|
Velocity","#444|Gravity"]},
"laws-motion":{t:"Laws of Motion",topics:
["Newton's
Laws","Friction","Pulleys","Circular
Dynamics"],viz:"Force
Simulator",type:"forces",
theory:`<p><span class="key">First Law
(Inertia)</span>: Body stays at rest or
uniform motion unless forced. <span
class="key">Second Law</span>: F = ma =
dp/dt. <span class="key">Third Law</
span>: Action = Reaction.</p><p><span
class="key">Friction</span> opposes
motion. Static friction adjusts up to µN.
Kinetic friction is µκΝ. <span
class="key">Pseudo forces</span> appear
in accelerated frames.</p>`,
formulas:[{e:"F = ma = dp/dt",l:"Newton's
Second Law"},{e:"fs ≤ µsN",I:"Static friction
limit"},{e:"fk = HkN",l:"Kinetic friction"},{e:"T
= 2πv(L/g)",I:"Pendulum period"}],
insight:"In an accelerating lift: upward
acceleration increases apparent weight
(N=m(g+a)), free fall makes weight zero.",
params:["m = 5.0 kg""F = 25.0 N","a = 5.0
m/s2""f = 12.5 N"],
legend:["#fff|Applied Force""#888|
Friction","#444|Normal"]},
"work-energy":{t:"Work, Energy and
Power",topics:["Work","Kinetic
Energy","Potential
Energy","Collisions"],viz:"Energy
Lab",type:"energy",
theory:`<p><span class="key">Work</
span> is scalar: W = F.s cose. <span
class="key">Kinetic energy</span> =
12mv². <span class="key">Potential
energy</span> = mgh (gravitational).</
p><p>The <span class="key">Work-Energy
Theorem</span>: net work = change in KE.
<span class="key">Conservative forces</
span> have path-independent work. <span
class="key">Power</span> = dW/dt = F.v.</
p>,
formulas:[{e:"W = F·s cose = AKE",I:"WorkEnergy Theorem"},{e:"KE = 2mv²",I:"Kinetic
Energy"},{e:"PE = mgh",l:"Gravitational PE"},
{e:"P = dW/dt = F-v",I:"Power"}],
insight:"In conservative systems, total
mechanical energy (KE + PE) is constant.
Compare energy at two points instead of
analyzing all forces.",
params:["m = 2.0 kg","h = 10.0 m","PE = 196
J""v = 14.0 m/s"],
legend:["#fff|Kinetic""#888|
Potential","#444|Total"]},
"system-particles":{t:"System of Particles &
Rotational Motion",topics:["Center of
Mass","Torque","Moment of
Inertia","Angular
Momentum"],viz:"Rotational
Visualizer",type:"gyro",
theory:`<p>The <span class="key">center
of mass</span> moves as if all mass is
concentrated there. For two particles: r_cm
= (m,r, + m₂r2)/(m, + m2).</p><p><span
class="key">Torque</span> t = rx F
causes angular acceleration. <span
class="key">Moment of inertia</span> I =
Σmr². <span class="key">Angular
momentum</span> L = Iw is conserved
when net torque is zero.</p>`,
formulas:[{e:"T = r × F = la",l:"Torque"},{e:"L
= lw = r × p",l:"Angular momentum"},{e:"K =
1/2lw² + 2Mv2",I:"Rolling body KE"},
{e:"I_parallel = I_cm + Md2",I:"Parallel axis
theorem"}],
insight:"Parallel axis theorem calculates I
about any axis parallel to CM axis.
Essential for rods rotating about one end.",
params:["w = 45.2 rad/s","Q = 2.1 rad/s","t
= 12.8 N m","I = 0.45 kg.m²"],
legend:["#fff|Angular Momentum","#888|
Torque","#444|Precession"]},
"gravitation":{t:"Gravitation",topics:
["Gravitational Force","Field &
Potential""Satellites","Kepler's
Laws"],viz:"Orbital Simulator",type:"orbit",
theory:`<p><span class="key">Newton's
Law</span>: F = Gm,m2/r2. Every particle
attracts every other particle. <span
class="key">Gravitational field</span> g
GM/r². <span class="key">Potential</
span> V = -GM/r.</p><p><span
class="key">Escape velocity</span> is
minimum speed to break free. <span
class="key">Satellite motion</span>
follows Kepler's laws: T2 x r³.</p>`,
formulas:[{e:"F = G(m,m2)/r2",l:"Newton's
Law"},{e:"g = GM/R2",I:"Gravity"},{e:"v_e =
√(2GM/R)",I:"Escape velocity"},{e:"T2 x
r3",I:"Kepler's Third Law"}],
=
insight:"Earth's escape velocity is 11.2 km/
s. Same for all masses - feather or rocket
need the same speed, but rocket has more
KE.",
params:["M = 5.97×1024 kg""r = 6.37×106
m","g = 9.81 m/s²""v = 11.2 km/s"],
legend:["#fff|Planet","#888|Satellite""#444|
Orbit"]}
};
let current='systemparticles', scene,camera,renderer,objects=];
// LOAD CHAPTER
function load(key){
const d=DATA[key];if(!
d)return;current=key;
document.getElementByld('chtitle').textContent=d.t;
document.getElementByld('title').textConte
nt=d.t;
document.getElementByld('vizname').textContent=d.viz;
document.getElementByld('tags').innerHT
ML=d.topics.map(x=>`<span class="tag">$
{x}</span>`).join(");
let html=`<p>${d.theory}</p>`;
d.formulas.forEach(f=>{html+=`<div
class="formula"><div class="expr">${f.e}</
div><div class="lbl">${f.l}</div></div>});
html+=`<div class="insight"><h4>Key
Insight</h4><p>${d.insight}</p></div><div
class="ref"><strong>Reference:</strong>
NCERT Physics Class 11 - ${d.t}</div>;
document.getElementByld('content').inner
HTML=html;
document.getElementByld('params').inner
HTML=d.params.map(p=>{const[s,v]=p.spli
t('=');return`<div><span>${s.trim()}</
span><span>= ${v.trim()}</span></
div>`}).join(");
document.getElementByld('legend').innerH
TML=d.legend.map(l=>{const[c,t]=l.split('l');
return`<div><i style="background:${c}"></
i><span>${t}</span></div>`}).join(");
document.querySelectorAll('.dropdown
div').forEach(el=>el.classList.toggle('active',
el.getAttribute('onclick').includes(key)));
document.getElementByld('left').scrollTop=
0;
makeViz(d.type);
}
// DROPDOWN
function toggleDropdown()
{document.getElementByld('dropdown').cla
ssList.toggle('show')}
document.addEventListener('click',e=>{if(!
e.target.closest('.chapter'))document.getEl
ementByld('dropdown').classList.remove('s
how')});
// SIDEBAR
}
function toggleSidebar(){
document.getElementByld('sidebar').classL
ist.toggle('show');
document.getElementByld('overlay2').class
List.toggle('show');
document.getElementByld('notebtn').classList.toggle('active');
function addNote(){
const text=prompt('Enter note:');if(!
text)return;
const
div=document.createElement('div');div.clas
sName='note';
div.innerHTML=`<h4>Note</h4><p>${text}
</p>;
document.getElementByld('notelist').prepend(div);
}
// TABS
function setTab(el)
{document.querySelectorAll('.tab').forEach(
t=>t.classList.remove('on'));el.classList.add
('on');}
// AXIS
function setAxis(axis,btn){
document.querySelectorAll('.axes
button').forEach(b=>b.classList.remove('on'
));
btn.classList.add('on');
const pos={x:[12,0,0],y:[0,12,0],z:[0,0,12],t:
[8,6,10]};
const
p=pos[axis];camera.position.set(p[0],p[1],p[
2]);camera.lookAt(0,0,0);
}
// SEARCH
function doSearch(q(}
q=q.toLowerCase();if(q.length<2)return;
for(const[k,d]of Object.entries(DATA)){
if(d.t.toLowerCase().includes(q)
d.topics.some(t=>t.toLowerCase().includes
(q))){load(k);break}
}
}
// CLOCK
setInterval(()=>{
const n=new Date();
document.getElementByld('time').textCont
ent=String(n.getHours()).padStart(2,'0')
+':'+String(n.getMinutes()).padStart(2,0');
},1000);
// THREE.JS
function init(){
const
canvas=document.getElementByld('c');
renderer=new
THREE.WebGLRenderer({canvas,antialias:tr
ue});
renderer.setSize(canvas.clientWidth,canvas
.clientHeight);
scene=new
THREE.Scene();scene.background=new
THREE.Color(0x0a0a0a);
camera=neW
THREE.PerspectiveCamera(45,canvas.clien
tWidth/canvas.clientHeight,0.1,100);
camera.position.set(8,6,10);camera.lookAt(
0,0,0);
scene.add(new
THREE.AmbientLight(0xffffff,0.4));
const dl=new
THREE.DirectionalLight(0xffffff,0.8);dl.posit
ion.set(5,10,7);scene.add(dl);
makeViz('gyro');
animate();
new ResizeObserver(()=>{
renderer.setSize(canvas.clientWidth,canvas
.clientHeight);
camera.aspect=canvas.clientWidth/
canvas.clientHeight;
camera.updateProjectionMatrix();
}).observe(canvas.parentElement);
canvas.addEventListener('mousemove',e=>
}
const r=canvas.getBoundingClientRect();
camera.position.x=8+(((e.clientX-r.left)/
r.width)*2-1)*3;
camera.position.y=6+(-((e.clientY-r.top)/
r.height)*2+1)*3;
camera.lookAt(0,0,0);
}};
}
function clear()
{objects.forEach(o=>scene.remove(o));objects=]}
function makeViz(tyрe){
clear();
const g=new THREE.Group();
const metal=new
THREE.MeshStandardMaterial({color:0xccс
,metalness:0.9,roughness:0.2});
const dark=new
THREE.MeshStandardMaterial({color:0x33
3,metalness:0.8,roughness:0.3});
const ringMat=new
THREE.MeshStandardMaterial ({color:0x88
8,metalness:0.9,roughness:0.15,transparen
t:true,opacity:0.9});
if(type==='gyro'){
const rotor=new THREE.Mesh(new
THREE.CylinderGeometry(2,2,0.3,64),metal)
;rotor.rotation.x=Math.PI/2;g.add(rotor);
g.add(new THREE.Mesh(new
THREE.TorusGeometry(2.8,0.06,16,64), ring
Mat));
const outer=new THREE.Mesh(new
THREE. TorusGeometry(3.5,0.05,16,64),dark
);outer.rotation.x=Math.PI/2;g.add(outer);
const axle=new THREE.Mesh(new
THREE.CylinderGeometry(0.08,0.08,5,16),d
ark);axle.rotation.x=Math.PI/2;g.add(axle);
const base=new THREE.Mesh(new
THREE.CylinderGeometry(3,3.2,0.2,64), dark
);base.position.y=-3.3;g.add(base);
g.add(new
THREE.GridHelper(8,16,0x333,0x1a1a1a));
const arr=(dir,col,len,pos)=>new
THREE.ArrowHelper(dir.normalize(),pos,len,
col,0.3,0.2);
g.add(arr(new
THREE.Vector3(1,0.5,0),0x0ff,2.5,new
THREE.Vector3(2.5,1,0)));
g.add(arr(new
THREE.Vector3(-1,0.3,0.5),0x0ff,2.2,new
THREE.Vector3(-2.5,0.5,1)));
g.add(arr(new
THREE.Vector3(0.5,-0.8,0.3),0x0ff,2,new
THREE.Vector3(1,-1.5,1.5)));
g.add(arr(new
THREE.Vector3(-0.3,0.6,-0.8),0x0ff,2.3,new
THREE.Vector3(-1.5,1.5,-1.5)));
g.userData.animate=t=>{rotor.rotation.y=t*
3;g.rotation.y=t*0.3;g.rotation.z=Math.sin(t*0.5)*0.1};
}
else if(type==='projectile'||
type==='kinematic'){
const pts=[];for(let i=0;i<=50;i++){const
t=i/50;pts.push(new
THREE.Vector3(t*8-4,4*t-4* *t,0))}
const curve=new
THREE.CatmullRomCurve3(pts);
g.add(new THREE.Mesh(new
THREE.TubeGeometry(curve,64,0.05,8,false
),new
THREE.MeshStandardMaterial({color:0xfff,
emissive:0x444})));
const ball=new THREE.Mesh(new
THREE.SphereGeometry(0.2,32,32), new
THREE.MeshStandardMaterial({color:0xfff,
emissive:0x666}));g.add(ball);
for(let i=0;i<5;i++){const t=i/5;g.add(new
THREE.ArrowHelper(new
THREE.Vector3(1,1-2*t,0).normalize(),new
THREE.Vector3(t*8-4,4*t-4*+*t,0),0.8,0x888,
0.2,0.15))}
const gr=new THREE.Mesh(new
THREE.PlaneGeometry(20,20),new
THREE.MeshStandardMaterial ({color:0x11
1,roughness:0.9}));gr.rotation.x=-Math.PI/
2;gr.position.y=-1;g.add(gr);
g.userData.animate=t=>{const
p=(t*0.3)%1;ball.position.set(p*8-4,4*p-4*p*
p,0)};
}
else if(type==='forces'){
const block=new THREE.Mesh(new
THREE.BoxGeometry(2,2,2), new
THREE.MeshStandardMaterial({color:0x66
6,metalness:0.5}));g.add(block);
g.add(new THREE.ArrowHelper(new
THREE.Vector3(1,0,0),new
THREE.Vector3(1,0,0),3,0xfff,0.4,0.3));
g.add(new THREE.ArrowHelper(new
THREE.Vector3(-1,0,0), new
THREE.Vector3(-1,0,0),2,0x888,0.3,0.2));
g.add(new THREE.ArrowHelper(new
THREE.Vector3(0,1,0), new
THREE.Vector3(0,1,0),2.5,0x444,0.3,0.2));
g.add(new THREE.ArrowHelper(new
THREE.Vector3(0,-1,0), new
THREE.Vector3(0,-1,0),2.5,0x444,0.3,0.2));
const gr=new THREE.Mesh(new
THREE.PlaneGeometry(20,20),new
THREE.MeshStandardMaterial({color:0x1a
1a1a}));gr.rotation.x=-Math.PI/
2;gr.position.y=-1.5;g.add(gr);
g.userData.animate=t=>{block.position.x=
Math.sin(t)*2};
}
else if(type==='energy'){
const bob=new THREE.Mesh(new
THREE.SphereGeometry(0.5,32,32),new
THREE.MeshStandardMaterial({color:0xfff,
emissive:0x444}));g.add(bob);
const str=new THREE.Line(new
THREE.BufferGeometry().setFromPoints([n
ew THREE.Vector3(0,4,0),new
THREE.Vector3(0,0,0)]),new
THREE.LineBasicMaterial({color:0x888}));g.
add(str);
const pivot=new THREE.Mesh(new
THREE.SphereGeometry(0.2,16,16), new
THREE.MeshStandardMaterial({color:0x44
4}));pivot.position.y=4;g.add(pivot);
const ke=new THREE.Mesh(new
THREE.BoxGeometry(0.3,1,0.3), new
THREE.MeshStandardMaterial({color:0xfff}
));ke.position.set(3,0.5,0);g.add(ke);
const pe=new THREE.Mesh(new
THREE.BoxGeometry(0.3,1,0.3),new
THREE.MeshStandardMaterial({color:0x66
6}));pe.position.set(3.5,0.5,0);g.add(pe);
g.userData.animate=t=>{
const
a=Math.sin(t*1.5)*0.8;bob.position.set(Mat
h.sin(a)*4,4-Math.cos(a)*4,0);
str.geometry.setFromPoints([new
THREE.Vector3(0,4,0),bob.position]);
const
kev=Math.cos(a)**2,pev=Math.sin(a)**2;
ke.scale.y=kev*3;ke.position.y=ke.scale.y/
2;pe.scale.y=pev*3;pe.position.y=pe.scale.y
/2;
};
}
else if(type==='orbit'){
const planet=new THREE.Mesh(new
THREE.SphereGeometry(1.5,64,64), new
THREE.MeshStandardMaterial({color:0x66
6,emissive:0x222,metalness:0.8}));g.add(pl
anet);
const oc=new
THREE.EllipseCurve(0,0,4,3,0,Math.PI*2,fals
e,0);
const op=oc.getPoints(100);
g.add(new THREE.Line(new
THREE.BufferGeometry().setFromPoints(o
p.map(p=>new
THREE.Vector3(p.x,0,p.y))),new
THREE.LineBasicMaterial({color:0x444})));
const sat=new THREE.Mesh(new
THREE.SphereGeometry(0.2,16,16), new
THREE.MeshStandardMaterial({color:0xfff,
emissive:0x888}));g.add(sat);
const va=new THREE.ArrowHelper(new
THREE.Vector3(0,0,1),new
THREE.Vector3(4,0,0),1.5,0x888,0.3,0.2);g.a
dd(va);
const fa=new THREE.ArrowHelper(new
THREE.Vector3(-1,0,0),new
THREE.Vector3(4,0,0),1.2,0x444,0.25,0.15);
g.add(fa);
g.userData.animate=t=>{
const
a=t*0.5;sat.position.set(Math.cos(a)*4,0,M
ath.sin(a)*3);
va.position.copy(sat.position);va.setDirecti
on(new THREE.Vector3(-
Math.sin(a),0,Math.cos(a)));
fa.position.copy(sat.position);fa.setDirectio
n(new THREE.Vector3(-Math.cos(a),0,-
Math.sin(a)));
};
else if(type==='measure'){
g.add(new THREE.Mesh(new
THREE.BoxGeometry(8,0.3,0.1), new
THREE.MeshStandardMaterial({color:0x44
4})));
for(let i=-4;i<=4;i++){const m=new
THREE.Mesh(new
THREE.BoxGeometry(0.02,0.2,0.05),new
THREE.MeshStandardMaterial({color:0xfff}
));m.position.set(i,0.25,0);g.add(m)}
const obj=new THREE.Mesh(new
THREE.BoxGeometry(2.5,1,1), new
THREE.MeshStandardMaterial({color:0x88
8,metalness:0.6}));obj.position.set(-0.5,0.8,
0);g.add(obj);
const j1=new THREE.Mesh(new
THREE.BoxGeometry(0.1,1.5,0.3),dark);j1.p
osition.set(-1.75,0.5,0);g.add(j1);
const j2=new THREE.Mesh(new
THREE.BoxGeometry(0.1,1.5,0.3),dark);j2.p
osition.set(0.75,0.5,0);g.add(j2);
g.userData.animate=t=>{const
m=2.5+Math.sin(t)*0.3;obj.scale.x=m/
2.5;j2.position.x=-1.75+m};
}
scene.add(g);objects.push(g);
}
function animate(){
requestAnimationFrame(animate);
const t=Date.now()*0.001;
objects.forEach(o=>o.userData.animate&&
o.userData.animate(t));
renderer.render(scene,camera);
}
// START
window.onload=()=>{init();load('systemparticles')};
</script>
</body>
</html>"
