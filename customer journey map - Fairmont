file:///Users/priyamvadaparmar/Downloads/fairmont_customer_journey_map.html

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Fairmont Hotels & Resorts – Customer Journey Map</title>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    background: #f8f7f4;
    color: #1a1a18;
    padding: 32px 24px 48px;
    min-height: 100vh;
  }
  .page-header { margin-bottom: 28px; }
  .page-header h1 { font-size: 20px; font-weight: 500; color: #1a1a18; margin-bottom: 4px; }
  .page-header p { font-size: 13px; color: #73726c; }
  .card { background: #ffffff; border-radius: 14px; border: 0.5px solid rgba(0,0,0,0.12); padding: 24px; }
  .cjm { font-family: inherit; }
  .phase-rail { display: grid; grid-template-columns: repeat(5,1fr); gap: 8px; padding: 0 4px; }
  .phase { border-radius: 8px; padding: 10px 10px 8px; cursor: pointer; border: 1.5px solid transparent; transition: border-color .15s; }
  .phase.active { border-color: currentColor; }
  .phase-label { font-size: 11px; font-weight: 500; text-transform: uppercase; letter-spacing: .04em; opacity: .6; margin-bottom: 4px; }
  .phase-title { font-size: 13px; font-weight: 500; line-height: 1.3; }
  .phase-sub { font-size: 11px; margin-top: 3px; opacity: .7; line-height: 1.4; }
  .chart-wrap { position: relative; height: 130px; margin: 14px 4px 0; }
  svg.curve { width: 100%; height: 100%; overflow: visible; }
  .detail-panel { margin: 14px 4px 0; border: 0.5px solid rgba(0,0,0,0.1); border-radius: 12px; padding: 14px 16px; min-height: 140px; }
  .dp-header { display: flex; align-items: center; gap: 10px; margin-bottom: 10px; }
  .dp-phase-pill { font-size: 11px; font-weight: 500; padding: 3px 10px; border-radius: 20px; }
  .dp-title { font-size: 14px; font-weight: 500; color: #1a1a18; }
  .dp-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
  .dp-col-label { font-size: 11px; font-weight: 500; text-transform: uppercase; letter-spacing: .04em; color: #888780; margin-bottom: 5px; }
  .dp-item { font-size: 12px; padding: 4px 0; border-bottom: 0.5px solid rgba(0,0,0,0.08); line-height: 1.4; color: #5f5e5a; }
  .dp-item:last-child { border-bottom: none; }
  .pain-dot { display: inline-block; width: 7px; height: 7px; border-radius: 50%; margin-right: 5px; vertical-align: middle; }
  .legend-row { display: flex; align-items: center; gap: 18px; padding: 12px 4px 0; flex-wrap: wrap; }
  .leg-item { display: flex; align-items: center; gap: 6px; font-size: 11px; color: #73726c; }
  .leg-dot { width: 10px; height: 10px; border-radius: 50%; }
  .leg-line { width: 20px; height: 2px; border-radius: 1px; }
  .footer { margin-top: 20px; font-size: 11px; color: #888780; text-align: center; }
</style>
</head>
<body>

<div class="page-header">
  <h1>Customer Journey Map — Fairmont Hotels &amp; Resorts</h1>
  <p>End-to-end guest journey · Pre-booking to post-stay · CX / Journey mapping</p>
</div>

<div class="card">
<div class="cjm">
  <div class="phase-rail" id="phaseRail"></div>
  <div class="chart-wrap">
    <svg class="curve" id="curveSvg" viewBox="0 0 600 120" preserveAspectRatio="none"></svg>
  </div>
  <div class="detail-panel" id="detailPanel"></div>
  <div class="legend-row">
    <div class="leg-item"><div class="leg-line" style="background:#1D9E75"></div> Sentiment curve</div>
    <div class="leg-item"><div class="leg-dot" style="background:#1D9E75"></div> Positive moment</div>
    <div class="leg-item"><div class="leg-dot" style="background:#D85A30"></div> Pain point</div>
    <div class="leg-item"><div class="leg-dot" style="background:#BA7517"></div> Gap / friction</div>
  </div>
</div>
</div>

<div class="footer">Prepared by Priya &nbsp;·&nbsp; Fairmont Hotels &amp; Resorts CX Analysis &nbsp;·&nbsp; Portfolio document</div>

<script>
const phases=[
  {
    id:0,label:"Pre-booking",title:"Discover & book",sub:"Research, compare, reserve",
    color:"#E1F5EE",textColor:"#085041",borderColor:"#1D9E75",sentiment:72,
    touchpoints:["Hotel website / OTA","Social media & reviews","Email inquiry","Reservation confirmation"],
    emotions:["Excited anticipation","Comparison anxiety","Price sensitivity"],
    painPoints:["Inconsistent info across channels","No personalised outreach after enquiry","Slow email response times"],
    gaps:["No pre-stay preference capture","Missed upsell opportunity at booking"],
    dept:"Reservations / Marketing"
  },
  {
    id:1,label:"Pre-arrival",title:"Prepare & anticipate",sub:"Confirmation, reminders, prep",
    color:"#E6F1FB",textColor:"#0C447C",borderColor:"#378ADD",sentiment:65,
    touchpoints:["Booking confirmation email","Pre-arrival email (if any)","Mobile app / website"],
    emotions:["Anticipation","Mild uncertainty","Planning mode"],
    painPoints:["No pre-arrival communication","No room preference collection","Generic confirmation emails"],
    gaps:["No pre-check-in option","No itinerary or local tips sent"],
    dept:"Reservations / CRM"
  },
  {
    id:2,label:"Arrival & check-in",title:"Arrive & settle",sub:"First impression moment",
    color:"#FAECE7",textColor:"#712B13",borderColor:"#D85A30",sentiment:30,
    touchpoints:["Hotel entrance","Front desk","Bellboy / porter","Room key handover"],
    emotions:["First impression fragile","Frustration at wait","Relief on room entry"],
    painPoints:["Long queue — avg. 15 min wait","Manual ID verification slowdown","No real-time room readiness info","Impersonal greeting"],
    gaps:["No departmental coordination (front desk vs. housekeeping)","No digital check-in alternative"],
    dept:"Front Desk / Housekeeping"
  },
  {
    id:3,label:"In-stay",title:"Experience the stay",sub:"Services, dining, activities",
    color:"#E6F1FB",textColor:"#0C447C",borderColor:"#378ADD",sentiment:58,
    touchpoints:["Room service","F&B outlets","Spa & leisure","Concierge","Housekeeping visits"],
    emotions:["Comfort seeking","Delight when exceeded","Annoyance at inconsistency"],
    painPoints:["Inconsistent service across shifts","Slow housekeeping response","Lack of proactive communication"],
    gaps:["Departments operate in silos","No mid-stay check-in from staff","Guest preferences not shared across teams"],
    dept:"All departments"
  },
  {
    id:4,label:"Check-out & post-stay",title:"Depart & reflect",sub:"Check-out, feedback, loyalty",
    color:"#FAEEDA",textColor:"#633806",borderColor:"#BA7517",sentiment:50,
    touchpoints:["Check-out desk","Departure message","Post-stay survey","Loyalty programme"],
    emotions:["Reflection on experience","Openness to feedback","Decision on return / referral"],
    painPoints:["Paper-heavy check-out process","Feedback form not always offered","No personalised follow-up"],
    gaps:["No closed-loop on complaints","Survey response rates low","Loyalty re-engagement weak"],
    dept:"Front Desk / CRM"
  }
];

const sentimentPath=[72,65,30,58,50];
const xs=[60,180,300,420,540];
function getY(s){return 100-(s/100)*85;}

function buildCurve(){
  const svg=document.getElementById('curveSvg');
  const pts=xs.map((x,i)=>({x,y:getY(sentimentPath[i])}));
  let d=`M ${pts[0].x} ${pts[0].y}`;
  for(let i=1;i<pts.length;i++){
    const cp1x=pts[i-1].x+40,cp1y=pts[i-1].y,cp2x=pts[i].x-40,cp2y=pts[i].y;
    d+=` C ${cp1x} ${cp1y} ${cp2x} ${cp2y} ${pts[i].x} ${pts[i].y}`;
  }
  const yLabels=[{label:'High',y:10},{label:'Mid',y:55},{label:'Low',y:100}];
  yLabels.forEach(({label,y})=>{
    const line=document.createElementNS('http://www.w3.org/2000/svg','line');
    line.setAttribute('x1','40');line.setAttribute('x2','580');
    line.setAttribute('y1',y);line.setAttribute('y2',y);
    line.setAttribute('stroke','rgba(0,0,0,0.08)');line.setAttribute('stroke-width','0.5');
    svg.appendChild(line);
    const t=document.createElementNS('http://www.w3.org/2000/svg','text');
    t.setAttribute('x','6');t.setAttribute('y',y+4);
    t.setAttribute('font-size','9');t.setAttribute('fill','#888780');t.textContent=label;
    svg.appendChild(t);
  });
  const path=document.createElementNS('http://www.w3.org/2000/svg','path');
  path.setAttribute('d',d);path.setAttribute('fill','none');
  path.setAttribute('stroke','#1D9E75');path.setAttribute('stroke-width','2');
  path.setAttribute('stroke-linecap','round');
  svg.appendChild(path);
  pts.forEach((pt,i)=>{
    const s=sentimentPath[i];
    const col=s<40?'#D85A30':s<60?'#BA7517':'#1D9E75';
    const circle=document.createElementNS('http://www.w3.org/2000/svg','circle');
    circle.setAttribute('cx',pt.x);circle.setAttribute('cy',pt.y);
    circle.setAttribute('r','7');circle.setAttribute('fill',col);
    circle.setAttribute('stroke','#ffffff');circle.setAttribute('stroke-width','2');
    circle.style.cursor='pointer';
    circle.addEventListener('click',()=>selectPhase(i));
    svg.appendChild(circle);
    const label=document.createElementNS('http://www.w3.org/2000/svg','text');
    label.setAttribute('x',pt.x);label.setAttribute('y',pt.y-13);
    label.setAttribute('text-anchor','middle');label.setAttribute('font-size','10');
    label.setAttribute('fill',col);label.setAttribute('font-weight','500');
    label.textContent=s+'%';
    svg.appendChild(label);
  });
}

function renderPhases(activeId){
  const rail=document.getElementById('phaseRail');
  rail.innerHTML='';
  phases.forEach(p=>{
    const div=document.createElement('div');
    div.className='phase'+(p.id===activeId?' active':'');
    div.style.background=p.color;
    if(p.id===activeId) div.style.borderColor=p.borderColor;
    div.innerHTML=`<div class="phase-label" style="color:${p.textColor}">${p.label}</div>
      <div class="phase-title" style="color:${p.textColor}">${p.title}</div>
      <div class="phase-sub" style="color:${p.textColor}">${p.sub}</div>`;
    div.addEventListener('click',()=>selectPhase(p.id));
    rail.appendChild(div);
  });
}

function renderDetail(p){
  const panel=document.getElementById('detailPanel');
  const sentCol=p.sentiment<40?'#D85A30':p.sentiment<60?'#BA7517':'#1D9E75';
  panel.innerHTML=`
    <div class="dp-header">
      <span class="dp-phase-pill" style="background:${p.color};color:${p.textColor}">${p.label}</span>
      <span class="dp-title">${p.title}</span>
      <span style="margin-left:auto;font-size:12px;font-weight:500;color:${sentCol}">Sentiment ${p.sentiment}%</span>
    </div>
    <div class="dp-grid">
      <div>
        <div class="dp-col-label">Touchpoints</div>
        ${p.touchpoints.map(t=>`<div class="dp-item">${t}</div>`).join('')}
        <div class="dp-col-label" style="margin-top:10px">Owner</div>
        <div class="dp-item">${p.dept}</div>
      </div>
      <div>
        <div class="dp-col-label">Pain points</div>
        ${p.painPoints.map(t=>`<div class="dp-item"><span class="pain-dot" style="background:#D85A30"></span>${t}</div>`).join('')}
        <div class="dp-col-label" style="margin-top:10px">Gaps identified</div>
        ${p.gaps.map(t=>`<div class="dp-item"><span class="pain-dot" style="background:#BA7517"></span>${t}</div>`).join('')}
      </div>
    </div>`;
}

function selectPhase(id){
  renderPhases(id);
  renderDetail(phases[id]);
}

buildCurve();
selectPhase(0);
</script>
</body>
</html>
