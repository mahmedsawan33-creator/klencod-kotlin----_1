
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#081b14">
<title>قُم صَلِّ</title>

<style>
*{box-sizing:border-box}
body{
margin:0;background:#081b14;color:#fff;
font-family:Arial,sans-serif;text-align:center
}
header{padding:25px 15px 10px}
h1{color:#e8c35a;font-size:34px;margin:10px}
.subtitle{color:#a8c5b4}
.card{
background:#11291f;border:1px solid #264837;
border-radius:20px;padding:20px;margin:14px auto;
width:92%;max-width:480px
}
.clock{font-size:38px;font-weight:bold;color:#e8c35a}
.grid{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.prayer{background:#19382a;border-radius:12px;padding:14px}
.prayer span{display:block;margin-top:7px;font-size:21px}
.prayer.active{border:2px solid #e8c35a}
button{
border:0;border-radius:12px;padding:15px;
font-size:17px;font-weight:bold;width:100%;
margin-top:10px;cursor:pointer
}
.gold{background:#e8c35a;color:#102117}
.green{background:#246743;color:white}
.red{background:#a32727;color:white}
input,select{
width:100%;padding:14px;border-radius:10px;
border:1px solid #496655;background:#071a13;
color:white;font-size:18px;text-align:center;margin-top:10px
}
small{color:#9db9a9}
#alarmScreen{
display:none;position:fixed;inset:0;z-index:999;
background:#170909;padding:18px;overflow-y:auto
}
#alarmScreen h1{color:#ff4545;font-size:35px}
#alarmScreen h2{font-size:26px}
#message{font-size:22px;line-height:1.9;color:#ffe6b2}
#equation{font-size:27px;color:#ffdb76;margin:20px}
</style>
</head>

<body>

<header>
<h1>🕌 قُم صَلِّ</h1>
<div class="subtitle">لا تؤجل الصلاة… قم الآن</div>
</header>

<div class="card">
<div id="clock" class="clock">--:--:--</div>
<div id="date"></div>
<p>📍 بنغازي – ليبيا</p>
</div>

<div class="card">
<h3>مواقيت الصلاة اليوم</h3>
<div class="grid" id="prayers"></div>
</div>

<div class="card">
<h3>الصلاة القادمة</h3>
<div id="nextPrayer" class="clock" style="font-size:23px">--</div>
</div>

<div class="card">
<h3>⚙️ إعدادات التنبيه</h3>
<select id="intensity">
<option value="1">تنبيه هادئ</option>
<option value="2">تنبيه متوسط</option>
<option value="3" selected>تنبيه صارم</option>
</select>

<button class="green" onclick="testAlarm()">🔔 تجربة المنبه</button>
<button class="gold" onclick="stopTest()">إيقاف التجربة</button>
<small>اختبر المنبه للتأكد من عمل الصوت.</small>
</div>

<div class="card">
<h3>🤲 دعاء</h3>
<p>اللهم أعني على ذكرك وشكرك وحسن عبادتك.</p>
<button class="green" onclick="alert('اللهم ثبتنا على الصلاة واجعلها قرة أعيننا ❤️')">
اللهم أعني على الصلاة
</button>
</div>

<div id="alarmScreen">
<h1>🔔 حان وقت الصلاة</h1>
<h2 id="alarmPrayer"></h2>
<div id="message"></div>

<p style="color:#ffaaaa;font-size:19px">
قم الآن، توضأ، ولا تجعل التأجيل عادة.
</p>

<div class="card" style="background:#291515">
<h3>🧠 حل المسألة لإيقاف التنبيه</h3>
<div id="equation"></div>
<input id="answer" type="number" placeholder="اكتب الإجابة">
<button class="gold" onclick="checkAnswer()">تحقق من الإجابة</button>

<hr style="border-color:#533333;margin:25px 0">

<h3>أو أكد قيامك للصلاة</h3>
<input id="pledge" placeholder="اكتب: والله قايم أصلي">
<button class="green" onclick="checkPledge()">أنا قمت للصلاة</button>

<p style="font-size:13px;color:#aaa">
هذا عهد بينك وبين الله، وليس مع التطبيق.
</p>

<button class="red" onclick="snooze()">تأجيل 5 دقائق</button>
</div>
</div>

<script>
// =============================
// إعداد بنغازي
// =============================
const LAT=32.1167;
const LON=20.0686;
const UTC_OFFSET=2;
const FAJR_ANGLE=18;
const ISHA_ANGLE=17;

let todayTimes={};
let activeAlarm=null;
let alarmAudio=null;
let alarmInterval=null;
let currentEquation=null;
let lastAlarmDate="";
let testMode=false;
let snoozeToken=0;

const reminders=[
"الصلاة ليست عبئًا على يومك، بل هي صلة بينك وبين ربك. قم الآن.",
"مهما كان ما يشغلك، لا تجعل الدنيا تأخذ منك صلاتك.",
"تخيّل أن هذه الصلاة هي آخر صلاة تصليها في حياتك. هل ستؤجلها؟",
"قم للصلاة. لا تنتظر أن يأتيك النشاط؛ انهض وسيأتي النشاط بعد قيامك.",
"يا نفس، الصلاة دقائق، لكن أثرها أعظم من ساعات من اللهو.",
"لا تجعل هاتفك يأخذ وقت الصلاة منك. قم وتوضأ.",
"أنت تعرف أن الصلاة مهمة، فلا تجعل معرفتك مجرد كلام.",
"كلما حافظت على الصلاة، درّبت نفسك على الوفاء بأهم عهد.",
"قم، واترك ما في يدك، فالصلاة أولى من كل شيء الآن.",
"باب التوبة مفتوح، وباب العودة إلى الصلاة مفتوح. ابدأ الآن."
];

// =============================
// أدوات الحساب
// =============================
function rad(x){return x*Math.PI/180}
function deg(x){return x*180/Math.PI}
function normalize(x){return ((x%360)+360)%360

}

function dayOfYear(date){
return Math.floor(
(Date.UTC(date.getFullYear(),date.getMonth(),date.getDate())-
Date.UTC(date.getFullYear(),0,1))/86400000
)+1;
}

// حساب زاوية الشمس
function solarCalc(date,angle,isSunrise=false){
const N=dayOfYear(date);
const lngHour=LON/15;
const t=N+((isSunrise?6:18)-lngHour)/24;
const M=(0.9856*t)-3.289;
let L=M+1.916*Math.sin(rad(M))+0.020*Math.sin(rad(2*M))+282.634;
L=normalize(L);
let RA=deg(Math.atan(0.91764*Math.tan(rad(L))));
RA=normalize(RA);
RA+=(Math.floor(L/90)*90-Math.floor(RA/90)*90);
RA/=15;
const sinDec=0.39782*Math.sin(rad(L));
const cosDec=Math.cos(Math.asin(sinDec));
const cosH=(Math.sin(rad(-angle))-Math.sin(rad(LAT))*sinDec)/
(Math.cos(rad(LAT))*cosDec);
if(cosH>1||cosH<-1)return null;
let H=isSunrise?360-deg(Math.acos(cosH)):deg(Math.acos(cosH));
H/=15;
const T=H+RA-(0.06571*t)-6.622;
const UT=T-lngHour;
return (UT+UTC_OFFSET+24)%24;
}

// منتصف النهار الحقيقي (الظهر)
function solarNoon(date){
const N=dayOfYear(date);
const lngHour=LON/15;
const t=N+(12-lngHour)/24;
const M=(0.9856*t)-3.289;
let L=M+1.916*Math.sin(rad(M))+0.020*Math.sin(rad(2*M))+282.634;
L=normalize(L);
let RA=deg(Math.atan(0.91764*Math.tan(rad(L))));
RA=normalize(RA);
RA+=(Math.floor(L/90)*90-Math.floor(RA/90)*90);
RA/=15;
const T=RA-(0.06571*t)-6.622;
return (T-lngHour+UTC_OFFSET+24)%24;
}

// العصر (ظل 1)
function asrCalc(date){
const N=dayOfYear(date);
const decl=23.45*Math.sin(rad(360*(284+N)/365));
const altitude=deg(Math.atan(
1/(1+Math.tan(rad(Math.abs(LAT-decl))))
));
return solarCalc(date,altitude,false);
}

function fmt(hours){
if(hours==null)return "--:--";
let h=Math.floor(hours);
let m=Math.round((hours-h)*60);
if(m===60){h++;m=0}
h=((h%24)+24)%24;
return String(h).padStart(2,"0")+":"+String(m).padStart(2,"0");
}

function toDateTime(hours,date){
const d=new Date(date);
d.setHours(0,0,0,0);
d.setMinutes(Math.round(hours*60));
return d;
}

// =============================
// حساب المواقيت
// =============================
function calculatePrayerTimes(){
const d=new Date();
const fajr=solarCalc(d,FAJR_ANGLE,true);
const dhuhr=(solarNoon(d)+0.03)%24;
const asr=asrCalc(d);
const maghrib=solarCalc(d,0.833,false);
const isha=solarCalc(d,ISHA_ANGLE,false);

todayTimes={
"الفجر":fajr,
"الظهر":dhuhr,
"العصر":asr,
"المغرب":maghrib,
"العشاء":isha
};
renderPrayers();
}

// =============================
// عرض المواقيت
// =============================
function renderPrayers(){
const box=document.getElementById("prayers");
box.innerHTML="";
const now=new Date();
let upcoming=null;

for(const [name,time] of Object.entries(todayTimes)){
if(time==null)continue;
const dt=toDateTime(time,now);
const next=!upcoming&&dt>now;
if(next)upcoming={name,time,dateTime:dt};
box.innerHTML+=`
<div class="prayer ${next?'active':''}">
${name}<span>${fmt(time)}</span>
</div>`;
}

if(!upcoming){
const tomorrow=new Date();
tomorrow.setDate(tomorrow.getDate()+1);
const fajr=solarCalc(tomorrow,FAJR_ANGLE,true);
upcoming={
name:"الفجر",
time:fajr,
dateTime:toDateTime(fajr,tomorrow)
};
}
window.nextPrayerData=upcoming;
}

// =============================
// الساعة
// =============================
function updateClock(){
const now=new Date();
document.getElementById("clock").textContent=
now.toLocaleTimeString("ar-LY");
document.getElementById("date").textContent=
now.toLocaleDateString("ar-LY",{
weekday:"long",year:"numeric",month:"long",day:"numeric"
});
updateCountdown();
checkPrayerAlarm();
}

function updateCountdown(){
const p=window.nextPrayerData;
if(!p)return;
const diff=Math.max(0,p.dateTime-new Date());
const h=Math.floor(diff/3600000);
const m=Math.floor(diff%3600000/60000);
const s=Math.floor(diff%60000/1000);
document.getElementById("nextPrayer").textContent=
`${p.name} بعد ${h} ساعة ${m} دقيقة ${s} ثانية`;
}

// =============================
// المنبه
// =============================
function checkPrayerAlarm(){
if(testMode)return;
const now=new Date();
for(const [name,time] of Object.entries(todayTimes)){
const target=toDateTime(time,now);
const key=name+"-"+target.toDateString();
if(now>=target&&now-target<60000&&lastAlarmDate!==key){
lastAlarmDate=key;
startAlarm(name);
}
}
}

function startAlarm(name){
activeAlarm=name;
document.getElementById("alarmPrayer").textContent="صلاة "+name;
document.getElementById("message").textContent=
reminders[Math.floor(Math.random()*reminders.length)];
document.getElementById("alarmScreen").style.display="block";
makeEquation();
startSound();
}

// =============================
// صوت التنبيه
// =============================
function startSound(){
stopSound();
try{
alarmAudio=new(window.AudioContext||window.webkitAudioContext)();
const level=Number(document.getElementById("intensity").value);
function beep(){
if(!alarmAudio)return;
const osc=alarmAudio.createOscillator();
const gain=alarmAudio.createGain();
osc.type="square";
osc.frequency.value=level===1?500:level===2?800:1050;
gain.gain.value=0.12;
osc.connect(gain);
gain.connect(alarmAudio.destination);
osc.start();
osc.stop(alarmAudio.currentTime+0.3);
}
beep();
alarmInterval=setInterval(beep,900);
}catch(e){}
}

function stopSound(){
if(alarmInterval)clearInterval(alarmInterval);
alarmInterval=null;
if(alarmAudio){
try{alarmAudio.close()}catch(e){}
alarmAudio=null;
}
}

// =============================
// معادلة رياضية
// =============================
function makeEquation(){
const a=Math.floor(Math.random()*40)+15;
const b=Math.floor(Math.random()*30)+10;
const c=Math.floor(Math.random()*20)+5;
const d=Math.floor(Math.random()*12)+2;
currentEquation=(a*b)+(c*c)-d;
document.getElementById("equation").textContent=
`(${a} × ${b}) + (${c} × ${c}) - ${d} = ؟`;
document.getElementById("answer").value="";
}

function checkAnswer(){
if(Number(document.getElementById("answer").value)===currentEquation){
unlockAlarm("تم حل المسألة. قم الآن للصلاة ولا تعد إلى النوم.");
}else{
document.getElementById("message").textContent=
"الإجابة غير صحيحة. حاول مرة أخرى، وتذكّر لماذا قمت بتشغيل هذا المنبه.";
makeEquation();
}
}

// =============================
// التعهد
// =============================
function checkPledge(){
const text=document.getElementById("pledge").value.trim();
if(text==="والله قايم أصلي"||text==="والله قائم أصلي"){
unlockAlarm("أسأل الله أن يعينك ويثبتك. قم الآن وتوضأ.");
}else{
alert("اكتب العبارة المطلوبة كما هي.");
}
}

function unlockAlarm(msg){
stopSound();
document.getElementById("alarmScreen").style.display="none";
alert(msg);
activeAlarm=null;
}

// =============================
// تأجيل
// =============================
function snooze(){
stopSound();
document.getElementById("alarmScreen").style.display="none";
const token=++snoozeToken;
alert("تم تأجيل التنبيه 5 دقائق. لا تجعل التأجيل عادة.");
setTimeout(()=>{
if(token===snoozeToken&&!testMode){
startAlarm(activeAlarm||"الصلاة");
}
},5*60*1000);
}

// =============================
// تجربة
// =============================
function testAlarm(){
testMode=true;
startAlarm("تجربة المنبه");
}
function stopTest(){
testMode=false;
snoozeToken++;
stopSound();
document.getElementById("alarmScreen").style.display="none";
activeAlarm=null;
}

// تحديث التاريخ
calculatePrayerTimes();
updateClock();
setInterval(updateClock,1000);
setInterval(()=>{
const today=new Date().toDateString();
if(today!==window.savedDay){
window.savedDay=today;
calculatePrayerTimes();
}
},30000);

// تفعيل الصوت عند أول لمسة
document.body.addEventListener("click",()=>{
if(alarmAudio&&alarmAudio.state==="suspended"){
alarmAudio.resume();
}
},{once:true});
</script>
</body>
</html>
