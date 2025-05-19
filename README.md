# five-lounge-ai
<!DOCTYPE html>
<html lang="fa">
<head>
  <meta charset="UTF-8">
  <title>فایوبات | پیشنهاد شخصی‌سازی‌شده</title>
  <style>
    body {
      font-family: sans-serif;
      direction: rtl;
      background-color: #fafafa;
      padding: 20px;
      max-width: 600px;
      margin: auto;
    }
    .question, .response {
      margin-bottom: 20px;
    }
    button {
      padding: 10px 20px;
      margin: 5px;
      background-color: #111;
      color: #fff;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }
    button:hover {
      background-color: #444;
    }
  </style>
</head>
<body>
  <h1>🍽 به فایوبات خوش اومدی!</h1>
  <p>چند تا سوال ساده می‌پرسم تا یه پیشنهاد مخصوص حال و هوات بدم 😎</p>

  <div class="question" id="q1">
    <strong>1. الان چه حسی داری؟</strong><br>
    <button onclick="answer(1, 'آروم و ریلکسم')">آروم و ریلکسم</button>
    <button onclick="answer(1, 'گرسنه‌ام و هیجان‌زده')">گرسنه‌ام و هیجان‌زده</button>
    <button onclick="answer(1, 'خسته‌ام ولی خوشحالم')">خسته‌ام ولی خوشحالم</button>
  </div>

  <div class="question" id="q2" style="display:none">
    <strong>2. دنبال چه نوع تجربه‌ای هستی؟</strong><br>
    <button onclick="answer(2, 'یه وعده مفصل و خاص')">یه وعده مفصل و خاص</button>
    <button onclick="answer(2, 'یه چیز سبک و خوشمزه')">یه چیز سبک و خوشمزه</button>
    <button onclick="answer(2, 'فقط یه نوشیدنی باحال')">فقط یه نوشیدنی باحال</button>
  </div>

  <div class="question" id="q3" style="display:none">
    <strong>3. سبک غذای مورد علاقه‌ات چیه؟</strong><br>
    <button onclick="answer(3, 'ایتالیایی')">ایتالیایی</button>
    <button onclick="answer(3, 'کلاسیک ایرانی')">کلاسیک ایرانی</button>
    <button onclick="answer(3, 'گریل و رژیمی')">گریل و رژیمی</button>
  </div>

  <div class="question" id="q4" style="display:none">
    <strong>4. اهل چه نوشیدنی‌هایی هستی؟</strong><br>
    <button onclick="answer(4, 'نوشیدنی میوه‌ای')">نوشیدنی میوه‌ای</button>
    <button onclick="answer(4, 'قهوه یا چای')">قهوه یا چای</button>
    <button onclick="answer(4, 'میلک‌شیک')">میلک‌شیک</button>
  </div>

  <div class="question" id="q5" style="display:none">
    <strong>5. قلیون هم می‌خوای؟</strong><br>
    <button onclick="answer(5, 'آره حتماً')">آره حتماً</button>
    <button onclick="answer(5, 'نه، مرسی')">نه، مرسی</button>
  </div>

  <div class="question" id="q6" style="display:none">
    <strong>6. دوست داری طعم پیشنهادی چجوری باشه؟</strong><br>
    <button onclick="answer(6, 'تند و پرادویه')">تند و پرادویه</button>
    <button onclick="answer(6, 'خامه‌ای و لطیف')">خامه‌ای و لطیف</button>
    <button onclick="answer(6, 'کلاسیک و متعادل')">کلاسیک و متعادل</button>
  </div>

  <div class="response" id="suggestion" style="display:none">
    <h3>🍴 پیشنهاد فایوبات:</h3>
    <p id="final-recommendation"></p>
    <p><strong>راضی بودی از پیشنهادم؟</strong></p>
    <button onclick="satisfaction(true)">آره، عالی بود!</button>
    <button onclick="satisfaction(false)">نه، یه چیز دیگه می‌خوام</button>
  </div>

  <script>
    let answers = {};

    function answer(q, val) {
      answers[q] = val;
      document.getElementById('q' + q).style.display = 'none';
      const next = document.getElementById('q' + (q + 1));
      if (next) {
        next.style.display = 'block';
      } else {
        showSuggestion();
      }
    }

    function showSuggestion() {
      const {1: mood, 2: experience, 3: food, 4: drink, 5: hookah, 6: flavor} = answers;
      let suggestion = `با توجه به حس ${mood} و سلیقه‌ات:`;

      if (experience.includes('مفصل')) {
        if (food === 'ایتالیایی') suggestion += ' پاستا آلفردو مرغ + موهیتو کوبایی';
        else if (food === 'کلاسیک ایرانی') suggestion += ' شش‌کباب + چای مراکشی';
        else suggestion += ' استیک مرغ گریل + لیموناد زنجبیلی';
      } else if (experience.includes('سبک')) {
        suggestion += ' سالاد استیک با زرشک + موهیتو بری';
      } else {
        suggestion += ' اسپیشیال آیس‌کافی یا میلک‌شیک لوتوس';
      }

      if (hookah === 'آره حتماً') suggestion += ' + یه قلیون خوش‌طعم هم کنارش هست 😌';

      suggestion += ' 🍽✨';

      document.getElementById('final-recommendation').innerText = suggestion;
      document.getElementById('suggestion').style.display = 'block';
    }

    function satisfaction(happy) {
      if (happy) {
        alert('مرسی که انتخابم رو دوست داشتی! ✨ نوش جان 💛');
      } else {
        alert('باشه! یه پیشنهاد تازه برات می‌سازم 😊 فقط صفحه رو رفرش کن.');
        location.reload();
      }
    }
  </script>
</body>
</html>
