# My-first-project-
A simple web app for testing.<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>تسجيل مستخدم جديد - موقع المراهنات</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #121212;
      color: #eee;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }
    .box {
      background: #1f1f1f;
      padding: 30px;
      border-radius: 8px;
      box-shadow: 0 0 10px #00ff99;
      width: 360px;
      text-align: center;
    }
    .box h2 {
      margin-bottom: 20px;
      color: #00ff99;
    }
    input[type="text"], input[type="email"], input[type="password"], input[type="tel"] {
      width: 100%;
      padding: 10px;
      margin: 10px 0 20px 0;
      border: none;
      border-radius: 4px;
      background: #333;
      color: #eee;
      font-size: 16px;
    }
    input[type="submit"] {
      width: 100%;
      padding: 12px;
      background: #00ff99;
      border: none;
      border-radius: 4px;
      color: #121212;
      font-weight: bold;
      font-size: 16px;
      cursor: pointer;
      transition: background 0.3s;
    }
    input[type="submit"]:hover {
      background: #00cc77;
    }
    .footer {
      margin-top: 15px;
      font-size: 14px;
      color: #666;
    }
    a {
      color: #00ff99;
      text-decoration: none;
    }
    a:hover {
      text-decoration: underline;
    }
    .error {
      color: #ff4444;
      margin-bottom: 15px;
    }
    .success {
      color: #44ff44;
      margin-bottom: 15px;
    }
  </style>
</head>
<body>
  <div class="box">
    <h2>إنشاء حساب جديد</h2>
    <div id="message"></div>
    <form id="signupForm">
      <input type="text" id="username" placeholder="اسم المستخدم" required />
      <input type="email" id="email" placeholder="البريد الإلكتروني" required />
      <input type="tel" id="phone" placeholder="رقم الهاتف" required />
      <input type="password" id="password" placeholder="كلمة المرور" required />
      <input type="password" id="confirm_password" placeholder="تأكيد كلمة المرور" required />
      <input type="submit" value="تسجيل" />
    </form>
    <p>عندك حساب؟ <a href="login.html">سجل دخول</a></p>
    <div class="footer">موقع المراهنات التجريبي</div>
  </div>

  <script>
    const form = document.getElementById('signupForm');
    const messageDiv = document.getElementById('message');

    form.addEventListener('submit', function(e) {
      e.preventDefault();

      const username = document.getElementById('username').value.trim();
      const email = document.getElementById('email').value.trim();
      const phone = document.getElementById('phone').value.trim();
      const password = document.getElementById('password').value;
      const confirm_password = document.getElementById('confirm_password').value;

      if(password !== confirm_password){
        messageDiv.innerHTML = '<div class="error">كلمة المرور وتأكيدها غير متطابقين.</div>';
        return;
      }

      // تسجيل مستخدم جديد مع رصيد 100 د.ت
      const userData = { username, email, phone, password, balance: 100 };

      // تحقق إذا كان المستخدم موجود مسبقًا
      if(localStorage.getItem('user')){
        messageDiv.innerHTML = '<div class="error">يوجد مستخدم مسجل بالفعل. يرجى تسجيل الدخول.</div>';
        return;
      }

      localStorage.setItem('user', JSON.stringify(userData));

      messageDiv.innerHTML = '<div class="success">تم التسجيل بنجاح! سيتم تحويلك لتسجيل الدخول.</div>';

      form.reset();

      setTimeout(() => {
        window.location.href = 'login.html';
      }, 2000);
    });
  </script>
</body>
</html>
