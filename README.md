# camera-sitee
موقع إلكتروني لعرض الكاميرات" أو "مشروع واجهة أمامية لموقع كامره 
<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>كاميرا أمامية</title>
  <style>
    body {
      text-align: center;
      font-family: Arial;
      background: #111;
      color: white;
    }
    video {
      margin-top: 20px;
      border-radius: 15px;
      width: 300px;
    }
    button {
      padding: 10px 20px;
      margin: 10px;
      font-size: 16px;
      border: none;
      border-radius: 10px;
      cursor: pointer;
    }
  </style>
</head>
<body>

<h2>فتح الكاميرا الأمامية</h2>

<video id="video" autoplay playsinline></video>
<br>

<button onclick="startCamera()">تشغيل الكاميرا</button>
<button onclick="stopCamera()">إيقاف</button>

<script>
let stream;

function startCamera() {
  navigator.mediaDevices.getUserMedia({
    video: { facingMode: "user" } // كاميرا أمامية
  })
  .then(s => {
    stream = s;
    document.getElementById("video").srcObject = stream;
  })
  .catch(err => {
    alert("لازم توافق على الكاميرا");
  });
}

function stopCamera() {
  if (stream) {
    stream.getTracks().forEach(track => track.stop());
  }
}
</script>

</body>
</html>
