# Mishra-classes
Lectures 
<!DOCTYPE html>
<html>
<head>
  <title>Misra Class Scheduled Video</title>
  <meta charset="UTF-8">
  <style>
    body { font-family: sans-serif; text-align: center; margin-top: 50px; }
    #lockOverlay {
      position: fixed; top: 0; left: 0;
      width: 100%; height: 100%;
      background: rgba(0,0,0,0.8);
      display: flex; justify-content: center; align-items: center;
      color: #fff; font-size: 18px;
      flex-direction: column;
    }
    input { padding: 8px; font-size: 16px; }
    button { padding: 8px 12px; font-size: 16px; margin-top: 10px; }
  </style>
</head>
<body>
  <h2>📺 Misra Class Stream</h2>
  <div id="lockOverlay">
    <div>Enter Password to Access and Schedule Playback:</div>
    <input type="password" id="pwd" placeholder="Password">
    <button onclick="checkPwd()">Unlock</button>
    <div id="msg" style="margin-top:10px;color:#ff7070;"></div>
  </div>
  <video id="myVideo" width="640" height="360" controls style="display:none; margin-top: 20px;">
    <source src="https://drive.google.com/uc?export=download&id=1-8w_TxZhigap97PQvG_-Zjr_MQBedqVW" type="video/mp4">
    Your browser does not support the <code>video</code> tag.
  </video>

  <script>
    const targetHour = 12;
    const targetMinute = 0;
    const password = "BRIJESHEDREETAAAAA";

    const overlay = document.getElementById("lockOverlay");
    const msg = document.getElementById("msg");
    const video = document.getElementById("myVideo");

    function checkPwd() {
      if (document.getElementById("pwd").value === password) {
        overlay.style.display = "none";
        video.style.display = "block";
        schedulePlay();
      } else {
        msg.textContent = "Incorrect password. Try again.";
      }
    }

    function schedulePlay() {
      function checkAndPlay() {
        const now = new Date();
        if (now.getHours() === targetHour && now.getMinutes() === targetMinute) {
          video.play();
        } else {
          setTimeout(checkAndPlay, 30000);
        }
      }
      checkAndPlay();
    }
  </script>
</body>
</html>
