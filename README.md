<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>เข้าร่วมเซิร์ฟเวอร์ดิสคอร์ด</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    :root {
      --discord-blue: #5865F2;
      --discord-dark: #36393f;
      --discord-darker: #2f3136;
      --discord-light: #ffffff;
      --discord-green: #3ba55c;
    }
    
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    
    body {
      font-family: 'Whitney', 'Helvetica Neue', Helvetica, Arial, sans-serif;
      background-color: var(--discord-dark);
      color: var(--discord-light);
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      background-image: url('https://cdnjs.cloudflare.com/ajax/libs/jquery.cycle/3.0.3/jquery.cycle.all.min.js');
      background-size: cover;
      background-position: center;
      position: relative;
      overflow: hidden;
    }
    
    /* เอฟเฟกต์พื้นหลังแบบเคลื่อนไหว */
    body::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(125deg, #5865F2 0%, #57F287 25%, #FEE75C 50%, #EB459E 75%, #ED4245 100%);
      opacity: 0.1;
      z-index: -1;
      animation: gradientBG 15s ease infinite;
      background-size: 400% 400%;
    }
    
    @keyframes gradientBG {
      0% {
        background-position: 0% 50%;
      }
      50% {
        background-position: 100% 50%;
      }
      100% {
        background-position: 0% 50%;
      }
    }
    
    .container {
      max-width: 800px;
      padding: 40px;
      background-color: var(--discord-darker);
      border-radius: 15px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
      text-align: center;
      position: relative;
      overflow: hidden;
      backdrop-filter: blur(5px);
      border: 1px solid rgba(255, 255, 255, 0.1);
      z-index: 1;
    }
    
    .logo {
      width: 100px;
      height: 100px;
      margin: 0 auto 20px;
      background-color: var(--discord-blue);
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      box-shadow: 0 5px 15px rgba(88, 101, 242, 0.4);
    }
    
    .logo i {
      font-size: 50px;
      color: white;
    }
    
    h1 {
      font-size: 32px;
      margin-bottom: 20px;
      color: white;
      text-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
    }
    
    p {
      font-size: 18px;
      color: #dcddde;
      margin-bottom: 30px;
      line-height: 1.6;
    }
    
    .features {
      display: flex;
      justify-content: center;
      margin-bottom: 30px;
      flex-wrap: wrap;
    }
    
    .feature {
      flex: 1;
      min-width: 200px;
      margin: 10px;
      padding: 20px;
      background-color: rgba(47, 49, 54, 0.6);
      border-radius: 10px;
      transition: transform 0.3s, box-shadow 0.3s;
    }
    
    .feature:hover {
      transform: translateY(-5px);
      box-shadow: 0 7px 15px rgba(0, 0, 0, 0.2);
    }
    
    .feature i {
      font-size: 28px;
      color: var(--discord-blue);
      margin-bottom: 15px;
    }
    
    .feature h3 {
      font-size: 18px;
      margin-bottom: 10px;
    }
    
    .feature p {
      font-size: 14px;
      color: #b9bbbe;
    }
    
    .join-btn {
      display: inline-block;
      padding: 15px 32px;
      font-size: 18px;
      font-weight: bold;
      background-color: var(--discord-blue);
      color: white;
      border: none;
      border-radius: 28px;
      cursor: pointer;
      transition: all 0.3s ease;
      text-decoration: none;
      position: relative;
      overflow: hidden;
      z-index: 1;
      box-shadow: 0 5px 15px rgba(88, 101, 242, 0.4);
    }
    
    .join-btn::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
      transition: 0.5s;
      z-index: -1;
    }
    
    .join-btn:hover {
      background-color: #4752c4;
      transform: translateY(-3px);
      box-shadow: 0 8px 20px rgba(88, 101, 242, 0.6);
    }
    
    .join-btn:hover::before {
      left: 100%;
    }
    
    .join-btn i {
      margin-right: 10px;
    }
    
    .member-count {
      margin-top: 30px;
      background-color: rgba(47, 49, 54, 0.6);
      border-radius: 10px;
      padding: 15px;
      display: inline-block;
    }
    
    .member-count i {
      color: var(--discord-green);
      margin-right: 8px;
    }
    
    .pulser {
      position: absolute;
      width: 100%;
      height: 100%;
      background: radial-gradient(circle, var(--discord-blue) 0%, transparent 70%);
      opacity: 0;
      top: 0;
      left: 0;
      z-index: -1;
      animation: pulse 3s infinite;
    }
    
    @keyframes pulse {
      0% {
        transform: scale(0.5);
        opacity: 0;
      }
      50% {
        opacity: 0.1;
      }
      100% {
        transform: scale(1.5);
        opacity: 0;
      }
    }
    
    /* เอฟเฟกต์ฟลอตติ้ง */
    .floating {
      animation-name: floating;
      animation-duration: 3s;
      animation-iteration-count: infinite;
      animation-timing-function: ease-in-out;
    }
    
    @keyframes floating {
      0% { transform: translateY(0px); }
      50% { transform: translateY(-10px); }
      100% { transform: translateY(0px); }
    }
    
    /* รองรับการแสดงผลบนมือถือ */
    @media (max-width: 768px) {
      .container {
        width: 90%;
        padding: 30px 20px;
      }
      
      .features {
        flex-direction: column;
      }
      
      h1 {
        font-size: 28px;
      }
      
      p {
        font-size: 16px;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="pulser"></div>
    
    <div class="logo floating">
      <i class="fab fa-discord"></i>
    </div>
    
    <h1>เข้าร่วมเซิร์ฟเวอร์ดิสคอร์ดของเรา!</h1>
    <p>เชื่อมต่อ พูดคุย และแบ่งปันกับชุมชนของเรา จะรออะไรอยู่? มาร่วมสนุกกันเลย!</p>
    
    <div class="features">
      <div class="feature">
        <i class="fas fa-users"></i>
        <h3>ชุมชนที่เป็นมิตร</h3>
        <p>พบปะเพื่อนใหม่และสร้างความสัมพันธ์ในเซิร์ฟเวอร์ของเรา</p>
      </div>
      
      <div class="feature">
        <i class="fas fa-gamepad"></i>
        <h3>เล่นเกมด้วยกัน</h3>
        <p>หาเพื่อนร่วมทีมและสนุกไปกับเกมโปรดของคุณ</p>
      </div>
      
      <div class="feature">
        <i class="fas fa-headset"></i>
        <h3>แชทเสียงคุณภาพสูง</h3>
        <p>พูดคุยกับเพื่อนด้วยระบบเสียงคุณภาพสูง</p>
      </div>
    </div>
    
    <a href="https://discord.gg/yTeu5V7sNJ" class="join-btn">
      <i class="fab fa-discord"></i>เข้าร่วมเลย!
    </a>
    
    <div class="member-count">
      <i class="fas fa-circle"></i>สมาชิกออนไลน์ <span class="online-count">500+</span>
    </div>
  </div>

  <script>
    // สคริปต์แสดงผลจำนวนคนออนไลน์แบบสุ่ม (เพื่อความสมจริง)
    function updateOnlineCount() {
      const min = 450;
      const max = 550;
      const onlineCount = Math.floor(Math.random() * (max - min + 1)) + min;
      document.querySelector('.online-count').textContent = onlineCount.toString();
    }
    
    // อัพเดททุกๆ 5 วินาที
    updateOnlineCount();
    setInterval(updateOnlineCount, 5000);
  </script>
</body>
</html>
