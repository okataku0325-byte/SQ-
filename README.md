<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SQ診断 - 構造理解指数</title>
<style>
body{
    font-family: -apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;
    background:#f5f7fa;
    margin:0;
    padding:20px;
    color:#333;
}
.container{
    max-width:800px;
    margin:auto;
}
.card{
    background:white;
    border-radius:16px;
    padding:20px;
    margin-bottom:20px;
    box-shadow:0 2px 8px rgba(0,0,0,0.08);
}
h1{
    text-align:center;
}
.question{
    margin-bottom:25px;
}
.question h3{
    font-size:1rem;
}
label{
    display:block;
    margin:8px 0;
    padding:10px;
    border-radius:8px;
    background:#f0f3f7;
}
button{
    width:100%;
    padding:15px;
    font-size:1rem;
    border:none;
    border-radius:12px;
    background:#4f46e5;
    color:white;
    cursor:pointer;
}
button:hover{
    opacity:0.9;
}
.result{
    display:none;
}
.score{
    font-size:2rem;
    font-weight:bold;
    text-align:center;
    margin:10px 0;
}
.type{
    font-size:1.3rem;
    text-align:center;
    font-weight:bold;
}
.desc{
    margin-top:15px;
    line-height:1.8;
}
</style>
</head>
<body>

<div class="container">

<div class="card" id="quiz">

<h1>SQ診断</h1>
<p>
SQ（Structure Quotient）は、
感情・事実・解釈・責任を切り分け、
問題の構造を理解しようとする傾向を測る簡易診断です。
</p>

<form id="sqForm">

<div class="question">
<h3>Q1. 誰かの一言で強く傷ついた時、最初に近いのは？</h3>
<label><input type="radio" name="q1" value="0"> なぜそんなことを言われたのか考える</label>
<label><input type="radio" name="q1" value="1"> 傷ついた理由を掘り下げる</label>
<label><input type="radio" name="q1" value="0"> 相手が悪かったと思う</label>
</div>

<div class="question">
<h3>Q2. 人間関係のトラブルが起きた時</h3>
<label><input type="radio" name="q2" value="0"> 誰が悪いか気になる</label>
<label><input type="radio" name="q2" value="1"> なぜそうなったのか気になる</label>
<label><input type="radio" name="q2" value="0"> どうすれば元に戻るか気になる</label>
</div>

<div class="question">
<h3>Q3. 怒りを感じた時</h3>
<label><input type="radio" name="q3" value="0"> 怒りをそのまま受け止める</label>
<label><input type="radio" name="q3" value="1"> 怒りの奥に別の感情がないか考える</label>
<label><input type="radio" name="q3" value="0"> 怒る原因になった相手を考える</label>
</div>

<div class="question">
<h3>Q4. 相手に誤解された時</h3>
<label><input type="radio" name="q4" value="0"> 相手の理解不足だと思う</label>
<label><input type="radio" name="q4" value="1"> 自分の伝え方が悪かったと思う</label>
<label><input type="radio" name="q4" value="2"> 認識のズレがどこで起きたか考える</label>
</div>

<div class="question">
<h3>Q5. 意見が対立した時</h3>
<label><input type="radio" name="q5" value="0"> 正しい方を明確にしたい</label>
<label><input type="radio" name="q5" value="1"> 相手の考えを知りたい</label>
<label><input type="radio" name="q5" value="2"> 前提の違いを知りたい</label>
</div>

<div class="question">
<h3>Q6. 嫉妬した時</h3>
<label><input type="radio" name="q6" value="0"> 嫉妬した自分を責める</label>
<label><input type="radio" name="q6" value="1"> 嫉妬した原因を探る</label>
<label><input type="radio" name="q6" value="0"> 嫉妬させた相手に不満を持つ</label>
</div>

<div class="question">
<h3>Q7. 誰かが怒っている時</h3>
<label><input type="radio" name="q7" value="1"> 怒りの理由を聞く</label>
<label><input type="radio" name="q7" value="2"> 怒りの奥にある感情を考える</label>
<label><input type="radio" name="q7" value="0"> とりあえず落ち着かせたい</label>
</div>

<div class="question">
<h3>Q8. コミュニケーションエラーが起きた時</h3>
<label><input type="radio" name="q8" value="0"> どちらかに原因があると思う</label>
<label><input type="radio" name="q8" value="2"> 双方に原因がある可能性を考える</label>
<label><input type="radio" name="q8" value="0"> 相性の問題だと思う</label>
</div>

<div class="question">
<h3>Q9. 対人問題について最も近い考え方は？</h3>
<label><input type="radio" name="q9" value="0"> 人の問題は感情から生まれる</label>
<label><input type="radio" name="q9" value="1"> 人の問題は価値観の違いから生まれる</label>
<label><input type="radio" name="q9" value="2"> 人の問題は複数の要因が絡み合って生まれる</label>
</div>

<div class="question">
<h3>Q10. あなたに最も近いのは？</h3>
<label><input type="radio" name="q10" value="0"> 人の気持ちを理解したい</label>
<label><input type="radio" name="q10" value="0"> 誰が正しいか理解したい</label>
<label><input type="radio" name="q10" value="2"> 何が起きているのか理解したい</label>
</div>

<button type="button" onclick="calculateSQ()">診断する</button>

</form>
</div>

<div class="card result" id="result">
<h2>診断結果</h2>
<div class="score" id="score"></div>
<div class="type" id="type"></div>
<div class="desc" id="desc"></div>
</div>

</div>

<script>
function calculateSQ(){

let total = 0;

for(let i=1;i<=10;i++){
    let selected = document.querySelector(`input[name="q${i}"]:checked`);
    if(!selected){
        alert("全ての質問に回答してください");
        return;
    }
    total += Number(selected.value);
}

let type = "";
let desc = "";

if(total <= 5){
    type = "感情直感型";
    desc = "感情や印象を重視して判断する傾向があります。";
}
else if(total <= 10){
    type = "感情理解型";
    desc = "感情の背景を理解しようとする傾向があります。";
}
else if(total <= 15){
    type = "構造理解型";
    desc = "感情と事実を切り分けて考える傾向があります。";
}
else{
    type = "高SQ型";
    desc = "感情・事実・解釈・責任を分離し、問題の構造そのものを理解しようとします。";
}

document.getElementById("result").style.display="block";
document.getElementById("score").innerText=`SQ ${total} / 17`;
document.getElementById("type").innerText=type;
document.getElementById("desc").innerText=desc;

window.scrollTo({
    top: document.body.scrollHeight,
    behavior: 'smooth'
});
}
</script>

</body>
</html>