[index.html](https://github.com/user-attachments/files/26373333/index.html)
<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:'Noto Sans KR',sans-serif;background:#fff;padding:0;min-height:100vh;display:flex;justify-content:center;align-items:flex-start}
.card{background:#fff;border-radius:0;overflow:hidden;width:100%;max-width:100%;box-shadow:none}
.hero{background:#1565C0;padding:20px 24px}
.hero-title{color:#fff;font-size:22px;font-weight:700;letter-spacing:-.3px}
.body{padding:20px 24px}
.sec{font-size:11px;color:#999;margin-bottom:6px;font-weight:600;letter-spacing:.04em}
.row{display:flex;align-items:center;gap:12px;margin-bottom:16px}
.row label{font-size:13px;color:#555;min-width:36px}
.row input,.row select{flex:1;border:1px solid #e0e0e0;border-radius:10px;padding:10px 14px;font-size:13px;outline:none;background:#fafafa;color:#333}
.row input:focus,.row select:focus{border-color:#2196F3;background:#fff}
.list{display:grid;grid-template-columns:1fr 1fr;gap:6px;margin-bottom:14px}
.item{display:flex;align-items:center;gap:8px;padding:10px 12px;background:#f5f5f5;border:1px solid #eee;border-radius:10px;cursor:pointer;user-select:none;transition:all .12s}
.item:hover{background:#E3F2FD;border-color:#90CAF9}
.item.on{background:#E3F2FD;border-color:#2196F3}
.box{width:18px;height:18px;border:1.5px solid #ccc;border-radius:4px;flex-shrink:0;display:flex;align-items:center;justify-content:center;font-size:11px;color:#fff;transition:all .12s}
.item.on .box{background:#2196F3;border-color:#2196F3}
.item.on .box::after{content:'✓'}
.text{font-size:12px;color:#333;line-height:1.4}
.item.on .text{color:#1565C0;font-weight:500}
.btn{width:100%;background:#2196F3;color:#fff;border:none;border-radius:12px;padding:14px;font-size:14px;font-weight:700;cursor:pointer;transition:background .15s}
.btn:hover:not(:disabled){background:#1976D2}
.btn:disabled{background:#bbb;cursor:not-allowed}
.note{text-align:center;font-size:11px;color:#aaa;margin-top:8px}
.result{display:none;background:#E3F2FD;border:1px solid #90CAF9;border-radius:10px;padding:14px;text-align:center;margin-top:10px}
.result.show{display:block}
.result-t{font-size:14px;font-weight:700;color:#1565C0;margin-bottom:3px}
.result-s{font-size:11px;color:#1976D2}
@media(max-width:480px){.list{grid-template-columns:1fr}}
</style>

<div class="card">
  <div class="hero">
    <div class="hero-title">업무 기록</div>
  </div>
  <div class="body">
    <div class="sec">담당자</div>
    <div class="row">
      <label>이름</label>
      <input type="text" id="nf-writer" placeholder="이름을 입력하세요">
    </div>
    <div class="row">
      <label>마을</label>
      <select id="nf-village">
        <option value="">마을 선택</option>
        <option value="상주 두릉덕가">상주 두릉덕가</option>
        <option value="순창 덕천리">순창 덕천리</option>
        <option value="영동 부릉리">영동 부릉리</option>
        <option value="진천 당골화양">진천 당골화양</option>
        <option value="홍성 화신모전">홍성 화신모전</option>
        <option value="의성 장2리">의성 장2리</option>
        <option value="청주 노현괴곡">청주 노현괴곡</option>
        <option value="청주 종암2리">청주 종암2리</option>
      </select>
    </div>
    <div class="sec">업무 체크리스트</div>
    <div class="list" id="nf-list"></div>
    <button class="btn" id="nf-btn" onclick="nfSubmit()">완료 체크 제출하기</button>
    <div class="note">제출하면 관리자 모니터링에 자동 반영됩니다</div>
    <div class="result" id="nf-result">
      <div class="result-t">제출 완료!</div>
      <div class="result-s" id="nf-result-s"></div>
    </div>
  </div>
</div>

<script>
var NF_SCRIPT = "https://script.google.com/macros/s/AKfycbxnj4XeoH8KNIJRmSs-mYa_p6lUwvB7rBcUYSsm-Hfpjf35cTgUrcjoaaXHOp9_DUo9vA/exec";

var TASKS = [
  "마을 방문 및 계약 진행",
  "수요조사 자료 준비",
  "주민교육 실시",
  "현장조원조직 교육 참석",
  "개인활동 진행 안내 및 사진정리",
  "공동활동 청구서 작성",
  "공동활동 점검",
  "상반기 개인활동 청구서 작성",
  "상반기 이행점검 제출",
  "생태조사",
  "토양 및 용수조사",
  "개인활동·공동활동 마감",
  "개인활동 청구서 작성",
  "농프 경진대회",
  "최종보고서 작성",
  "하반기 이행점검 제출"
];

var list = document.getElementById("nf-list");
TASKS.forEach(function(task){
  var div = document.createElement("div");
  div.className = "item";
  div.innerHTML = '<div class="box"></div><span class="text">'+task+'</span>';
  div.onclick = function(){this.classList.toggle("on")};
  list.appendChild(div);
});

var now = new Date();
function nfSubmit(){
  var writer = document.getElementById("nf-writer").value.trim();
  var village = document.getElementById("nf-village").value;
  if(!writer){alert("이름을 입력해주세요.");return;}
  if(!village){alert("마을을 선택해주세요.");return;}
  var checked = [].slice.call(document.querySelectorAll(".item.on")).map(function(el){return el.querySelector(".text").textContent});
  if(!checked.length){alert("완료한 업무를 하나 이상 체크해주세요.");return;}
  var btn = document.getElementById("nf-btn");
  btn.disabled = true; btn.textContent = "제출 중...";
  var url = NF_SCRIPT
    +"?submittedAt="+encodeURIComponent(now.toLocaleString("ko-KR"))
    +"&writer="+encodeURIComponent(writer)
    +"&village="+encodeURIComponent(village)
    +"&tasks="+encodeURIComponent(checked.join(", "));
  var img = new Image();
  img.onload = img.onerror = function(){
    btn.textContent = "제출 완료!";
    document.getElementById("nf-result-s").textContent = writer+"님 · "+village+" · "+checked.length+"개 업무 제출됨";
    document.getElementById("nf-result").classList.add("show");
  };
  img.src = url;
}
</script>
