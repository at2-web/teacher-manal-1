<!doctype html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>نموذج الفحص اللغوي للطالب</title>
  <style>
    body{font-family:"Segoe UI",Arial,sans-serif;background:#f9f9fb;margin:0;padding:20px;direction:rtl;color:#222}
    .container{max-width:900px;margin:auto;background:#fff;padding:20px;border-radius:12px;box-shadow:0 0 10px #ccc}
    h1{text-align:center;font-size:22px;margin-bottom:10px}
    p.desc{text-align:center;color:#555;margin-bottom:25px}
    label{font-weight:600;display:block;margin-top:10px}
    input,select,textarea{width:100%;padding:8px;margin-top:5px;border:1px solid #ddd;border-radius:8px}
    .choices{display:flex;gap:10px;margin-top:5px}
    .section{margin-bottom:25px}
    button{background:#007bff;color:#fff;border:none;padding:10px 15px;border-radius:8px;font-weight:bold;cursor:pointer}
  </style>
</head>
<body>
  <div class="container">
    <h1>📝 نموذج الفحص اللغوي</h1>
    <p class="desc">عزيزي الطالب، جاوب على الأسئلة التالية بعناية ثم اضغط حفظ لتحميل إجابتك.</p>

    <form id="examForm">
      <div class="section">
        <label>اسم الطالب:</label>
        <input type="text" name="student_name" required>
        <label>الصف الدراسي:</label>
        <input type="text" name="grade">
        <label>تاريخ الميلاد:</label>
        <input type="date" name="dob">
      </div>

      <div class="section">
        <label>هل تواجه صعوبة في السمع؟</label>
        <div class="choices">
          <label><input type="radio" name="hearing" value="نعم"> نعم</label>
          <label><input type="radio" name="hearing" value="لا" checked> لا</label>
        </div>

        <label>هل تستخدم سماعة؟</label>
        <div class="choices">
          <label><input type="radio" name="aid" value="نعم"> نعم</label>
          <label><input type="radio" name="aid" value="لا" checked> لا</label>
        </div>
      </div>

      <div class="section">
        <label>ملاحظات عامة:</label>
        <textarea name="notes" rows="4" placeholder="اكتب أي ملاحظات إضافية هنا..."></textarea>
      </div>

      <button type="button" onclick="saveCSV()">💾 حفظ وتنزيل النتيجة</button>
    </form>
  </div>

  <script>
    function saveCSV(){
      const form=document.getElementById('examForm');
      const data=new FormData(form);
      let csv='السؤال,الإجابة\\n';
      for(const [k,v] of data.entries()){csv+=\"${k}\",\"${v}\"\\n;}
      const blob=new Blob([csv],{type:'text/csv;charset=utf-8;'});
      const a=document.createElement('a');
      a.href=URL.createObjectURL(blob);
      a.download='fahs_lughawi.csv';
      a.click();
    }
  </script>
</body>
</html>
