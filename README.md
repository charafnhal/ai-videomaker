 ai-videomaker
AI Video Studio - Generate videos from text descriptions using fal.ai
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover" />
  <meta name="theme-color" content="#0d1220" />
  <meta name="description" content="AI Video Studio Pro - منصة توليد فيديوهات احترافية بالذكاء الاصطناعي" />
  <link rel="manifest" href="manifest.json" />
  <link rel="icon" href="icon.svg" />
  <title>AI Video Studio Pro</title>
  <style>
    :root{
      --bg:#0d1220;
      --bg2:#111a29;
      --panel:#111b2d;
      --panel2:#0e1626;
      --card:#101c2d;
      --line:rgba(148,163,184,.18);
      --text:#edf6ff;
      --muted:#a0b4d4;
      --accent:#62d9ff;
      --accent2:#7bf0b7;
      --accent3:#8d6cff;
      --danger:#ff6b6b;
      --success:#8df0ba;
      --warning:#f5cb63;
      --shadow:rgba(0,0,0,.4);
    }

    *{box-sizing:border-box}
    html,body{margin:0;padding:0}
    body{
      min-height:100vh;
      background:
        radial-gradient(circle at top left, rgba(98,217,255,.14), transparent 28%),
        radial-gradient(circle at bottom right, rgba(141,108,255,.12), transparent 30%),
        linear-gradient(135deg, var(--bg), var(--bg2));
      color:var(--text);
      font:14px/1.6 system-ui,-apple-system,"Segoe UI",Tahoma,sans-serif;
    }

    main{
      max-width:860px;
      margin:0 auto;
      padding:20px 16px 42px;
    }

    .shell{
      background:rgba(12,17,28,.78);
      border:1px solid var(--line);
      border-radius:28px;
      overflow:hidden;
      box-shadow:0 32px 90px var(--shadow);
      backdrop-filter:blur(8px);
    }

    .topbar{
      display:flex;
      justify-content:space-between;
      align-items:center;
      padding:18px 20px;
      background:rgba(8,12,20,.9);
      border-bottom:1px solid var(--line);
    }

    .brand{
      display:flex;
      align-items:center;
      gap:12px;
      font-weight:800;
      letter-spacing:.2px;
    }

    .brand-mark{
      width:42px;height:42px;
      display:grid;place-items:center;
      border-radius:14px;
      background:linear-gradient(135deg,var(--accent),var(--accent3));
      box-shadow:0 14px 30px rgba(98,217,255,.28);
    }

    .brand-mark svg{width:22px;height:22px}

    .nav-buttons{
      display:flex;
      gap:8px;
    }

    .nav-btn{
      border:none;
      background:transparent;
      color:var(--muted);
      cursor:pointer;
      font:inherit;
      font-weight:700;
      padding:8px 12px;
      border-radius:8px;
      transition:.2s ease;
      font-size:.85rem;
    }

    .nav-btn.active{
      background:rgba(98,217,255,.1);
      color:var(--accent);
    }

    .nav-btn:hover{
      color:var(--accent);
    }

    .install-btn{
      display:none;
      border:1px solid rgba(98,217,255,.38);
      background:rgba(98,217,255,.08);
      color:var(--accent);
      border-radius:999px;
      padding:8px 12px;
      cursor:pointer;
      font:inherit;
      font-weight:800;
      font-size:.85rem;
    }
    .install-btn:hover{
      transform:translateY(-1px);
      background:rgba(98,217,255,.12);
    }

    .content{padding:18px}

    .page{
      display:none;
    }
    .page.active{
      display:block;
    }

    .hero{
      text-align:center;
      padding:40px 20px;
    }

    .hero-mark{
      width:80px;
      height:80px;
      display:grid;
      place-items:center;
      margin:0 auto 20px;
      border-radius:20px;
      background:linear-gradient(135deg,var(--accent),var(--accent3));
      box-shadow:0 20px 40px rgba(98,217,255,.3);
    }

    .hero-mark svg{
      width:48px;
      height:48px;
    }

    .hero h1{
      font-size:2.2rem;
      margin:0 0 12px;
      background:linear-gradient(90deg,var(--accent),var(--accent2));
      -webkit-background-clip:text;
      -webkit-text-fill-color:transparent;
      background-clip:text;
    }

    .hero p{
      color:var(--muted);
      margin:0 0 28px;
      font-size:1.05rem;
    }

    .hero-buttons{
      display:flex;
      gap:12px;
      justify-content:center;
      flex-wrap:wrap;
    }

    .btn-primary{
      border:none;
      border-radius:15px;
      background:linear-gradient(135deg,var(--accent),var(--accent2));
      color:#071827;
      padding:12px 24px;
      font:inherit;
      font-weight:900;
      cursor:pointer;
      box-shadow:0 16px 32px rgba(98,217,255,.24);
      transition:.2s ease;
    }

    .btn-primary:hover{
      transform:translateY(-2px);
      box-shadow:0 20px 40px rgba(98,217,255,.32);
    }

    .btn-secondary{
      border:1px solid var(--line);
      border-radius:15px;
      background:transparent;
      color:var(--text);
      padding:12px 24px;
      font:inherit;
      font-weight:700;
      cursor:pointer;
      transition:.2s ease;
    }

    .btn-secondary:hover{
      border-color:var(--accent);
      color:var(--accent);
    }

    .features{
      display:grid;
      grid-template-columns:repeat(auto-fit,minmax(240px,1fr));
      gap:16px;
      margin-top:32px;
    }

    .feature{
      background:rgba(98,217,255,.05);
      border:1px solid rgba(98,217,255,.18);
      border-radius:16px;
      padding:20px;
      text-align:center;
    }

    .feature-icon{
      font-size:2.5rem;
      margin-bottom:12px;
    }

    .feature h3{
      margin:0 0 8px;
      color:var(--accent);
      font-size:1rem;
    }

    .feature p{
      margin:0;
      color:var(--muted);
      font-size:.9rem;
    }

    .panel{
      background:linear-gradient(180deg, rgba(18,27,45,.9), rgba(11,17,27,.9));
      border:1px solid var(--line);
      border-radius:20px;
      padding:18px;
      margin-bottom:18px;
    }

    .panel-head{
      display:flex;align-items:center;justify-content:space-between;
      margin-bottom:12px;
    }

    .panel-title{
      font-size:.74rem;
      letter-spacing:.12em;
      text-transform:uppercase;
      color:var(--accent);
      font-weight:900;
    }

    .badge{
      display:inline-flex;
      align-items:center;
      gap:6px;
      background:rgba(123,240,183,.08);
      border:1px solid rgba(123,240,183,.2);
      color:var(--accent2);
      border-radius:999px;
      padding:4px 8px;
      font-size:.72rem;
      font-weight:700;
    }

    label{
      display:block;
      font-size:.84rem;
      color:var(--muted);
      margin:12px 0 7px;
      font-weight:700;
    }

    textarea,input,select{
      width:100%;
      background:rgba(8,12,21,.85);
      color:var(--text);
      border:1px solid var(--line);
      border-radius:14px;
      padding:12px 14px;
      font:inherit;
      transition:border-color .2s ease, box-shadow .2s ease;
    }

    textarea{
      min-height:118px;
      resize:vertical;
    }

    textarea:focus,input:focus,select:focus{
      outline:none;
      border-color:rgba(98,217,255,.72);
      box-shadow:0 0 0 4px rgba(98,217,255,.08);
    }
    input::placeholder{color:rgba(159,179,204,.8)}

    .seg{
      display:grid;
      grid-template-columns:repeat(3,minmax(0,1fr));
      gap:8px;
      margin-top:8px;
    }
    .seg button{
      border:1px solid var(--line);
      background:rgba(8,12,21,.84);
      color:var(--muted);
      border-radius:12px;
      padding:11px 10px;
      font:inherit;
      cursor:pointer;
      font-weight:800;
      transition:.2s ease;
    }
    .seg button.on{
      background:linear-gradient(135deg,var(--accent),var(--accent2));
      color:#071827;
      border-color:transparent;
      box-shadow:0 12px 24px rgba(98,217,255,.2);
    }

    .two-col{
      display:grid;
      grid-template-columns:repeat(2,minmax(0,1fr));
      gap:12px;
      margin-top:12px;
    }

    .info-box{
      background:rgba(98,217,255,.06);
      border:1px solid rgba(98,217,255,.18);
      border-radius:12px;
      padding:12px;
      margin-top:10px;
      color:var(--muted);
      line-height:1.8;
    }
    .info-box a{color:var(--accent);text-decoration:none}

    .details-wrap{
      background:rgba(8,12,21,.66);
      border:1px solid var(--line);
      border-radius:16px;
      overflow:hidden;
    }
    details summary{
      list-style:none;
      padding:14px 16px;
      cursor:pointer;
      color:var(--muted);
      font-weight:800;
      user-select:none;
    }
    details summary::-webkit-details-marker{display:none}
    details[open] summary{border-bottom:1px solid var(--line)}
    details .inner{padding:14px 16px 18px}

    .primary-btn{
      width:100%;
      border:none;
      border-radius:15px;
      background:linear-gradient(135deg,var(--accent),var(--accent2));
      color:#071827;
      padding:15px 18px;
      font:inherit;
      font-weight:900;
      cursor:pointer;
      box-shadow:0 18px 36px rgba(98,217,255,.24);
      transition:transform .2s ease, box-shadow .2s ease;
    }
    .primary-btn:hover:not(:disabled){
      transform:translateY(-1px);
      box-shadow:0 22px 42px rgba(98,217,255,.32);
    }
    .primary-btn:disabled{
      opacity:.6;
      cursor:progress;
    }

    .status{
      min-height:18px;
      margin-top:14px;
      padding:11px 12px;
      border-radius:12px;
      font-size:.9rem;
      border:1px solid var(--line);
      color:var(--muted);
      background:rgba(255,255,255,.02);
    }
    .status.info{
      background:rgba(98,217,255,.06);
      border-color:rgba(98,217,255,.18);
      color:var(--accent);
    }
    .status.success{
      background:rgba(141,240,186,.08);
      border-color:rgba(141,240,186,.22);
      color:var(--success);
    }
    .status.error{
      background:rgba(255,107,107,.08);
      border-color:rgba(255,107,107,.2);
      color:var(--danger);
    }

    .progress{
      margin-top:10px;
      height:8px;
      border-radius:999px;
      border:1px solid var(--line);
      background:rgba(255,255,255,.04);
      overflow:hidden;
    }
    .progress span{
      display:block;
      width:0%;
      height:100%;
      background:linear-gradient(135deg,var(--accent),var(--accent2));
      border-radius:inherit;
      transition:width .35s ease;
    }

    .library{
      display:grid;
      gap:14px;
      margin-top:14px;
    }
    .empty{
      text-align:center;
      padding:28px 18px;
      border:1px dashed var(--line);
      background:rgba(255,255,255,.02);
      border-radius:16px;
      color:var(--muted);
    }

    .video-card{
      background:rgba(8,12,21,.82);
      border:1px solid var(--line);
      border-radius:18px;
      overflow:hidden;
    }

    .video-thumb{
      position:relative;
      aspect-ratio:16/9;
      background:#000;
      overflow:hidden;
    }
    .video-thumb video{
      display:block;
      width:100%;
      height:100%;
      object-fit:cover;
      background:#000;
    }

    .video-body{
      padding:12px;
    }
    .video-title{
      margin:0 0 8px;
      color:var(--text);
      font-size:.95rem;
      line-height:1.5;
      display:-webkit-box;
      -webkit-line-clamp:2;
      -webkit-box-orient:vertical;
      overflow:hidden;
    }
    .video-meta{
      margin:0;
      font-size:.76rem;
      color:var(--muted);
    }

    .video-actions{
      display:flex;
      gap:8px;
      padding:0 12px 12px;
    }
    .video-actions button{
      flex:1;
      border:1px solid var(--line);
      background:rgba(255,255,255,.02);
      color:var(--text);
      border-radius:12px;
      padding:9px 10px;
      cursor:pointer;
      font:inherit;
      transition:.2s ease;
    }
    .video-actions button:hover{
      border-color:rgba(98,217,255,.42);
      transform:translateY(-1px);
    }

    .about-section{
      background:linear-gradient(180deg, rgba(18,27,45,.9), rgba(11,17,27,.9));
      border:1px solid var(--line);
      border-radius:20px;
      padding:28px;
      margin-bottom:18px;
    }

    .about-section h2{
      margin:0 0 16px;
      color:var(--accent);
      font-size:1.4rem;
    }

    .about-section p{
      color:var(--muted);
      line-height:1.8;
      margin:0 0 12px;
    }

    .steps{
      display:grid;
      grid-template-columns:repeat(auto-fit,minmax(200px,1fr));
      gap:16px;
      margin-top:24px;
    }

    .step{
      background:rgba(98,217,255,.05);
      border:1px solid rgba(98,217,255,.18);
      border-radius:14px;
      padding:18px;
      counter-increment:step;
    }

    .step-number{
      display:inline-flex;
      align-items:center;
      justify-content:center;
      width:36px;
      height:36px;
      background:linear-gradient(135deg,var(--accent),var(--accent3));
      color:#071827;
      border-radius:8px;
      font-weight:900;
      margin-bottom:12px;
    }

    .step h3{
      margin:0 0 8px;
      color:var(--text);
      font-size:1rem;
    }

    .step p{
      margin:0;
      color:var(--muted);
      font-size:.9rem;
    }

    @media (max-width:560px){
      .seg,.two-col{grid-template-columns:1fr}
      .content{padding:14px}
      .panel{padding:14px}
      .topbar{padding:16px 14px}
      .nav-buttons{gap:4px}
      .nav-btn{padding:6px 8px;font-size:.8rem}
      .hero h1{font-size:1.6rem}
    }
  </style>
</head>
<body>
  <main>
    <div class="shell">
      <div class="topbar">
        <div class="brand">
          <div class="brand-mark">
            <svg viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg" fill="none">
              <rect x="8" y="16" width="40" height="28" rx="8" fill="#071827"/>
              <path d="M28 27.5V36.5L38 32L28 27.5Z" fill="#ffffff"/>
            </svg>
          </div>
          <span>AI Video Studio</span>
        </div>
        <div style="display:flex;align-items:center;gap:12px">
          <div class="nav-buttons">
            <button class="nav-btn active" data-page="home">الرئيسية</button>
            <button class="nav-btn" data-page="studio">الاستوديو</button>
            <button class="nav-btn" data-page="about">عن التطبيق</button>
          </div>
          <button class="install-btn" id="installBtn">تثبيت</button>
        </div>
      </div>

      <div class="content">
        <div class="page active" id="home">
          <div class="hero">
            <div class="hero-mark">
              <svg viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg" fill="none">
                <rect x="8" y="16" width="40" height="28" rx="8" fill="#071827"/>
                <path d="M28 27.5V36.5L38 32L28 27.5Z" fill="#ffffff"/>
              </svg>
            </div>
            <h1>AI Video Studio Pro</h1>
            <p>منصة توليد فيديوهات احترافية من الوصف النصي باستخدام الذكاء الاصطناعي المتقدم</p>
            <div class="hero-buttons">
              <button class="btn-primary" id="startBtn">ابدأ الآن</button>
              <button class="btn-secondary" id="learnBtn">تعرف أكثر</button>
            </div>
          </div>

          <div class="features">
            <div class="feature">
              <div class="feature-icon">🎬</div>
              <h3>فيديوهات واقعية</h3>
              <p>توليد فيديوهات سينمائية بجودة عالية وتفاصيل واقعية</p>
            </div>
            <div class="feature">
              <div class="feature-icon">🎨</div>
              <h3>أنيميشن احترافي</h3>
              <p>إنشاء رسوم متحركة ملونة وناعمة بأساليب متنوعة</p>
            </div>
            <div class="feature">
              <div class="feature-icon">✨</div>
              <h3>فن تجريدي</h3>
              <p>فيديوهات فنية حالمة وسريالية فريدة من نوعها</p>
            </div>
            <div class="feature">
              <div class="feature-icon">⚡</div>
              <h3>معالجة سريعة</h3>
              <p>توليد الفيديو في دقائق معدودة مع جودة استثنائية</p>
            </div>
            <div class="feature">
              <div class="feature-icon">💾</div>
              <h3>مكتبة محلية</h3>
              <p>احفظ جميع فيديوهاتك محليًا على جهازك بأمان</p>
            </div>
            <div class="feature">
              <div class="feature-icon">📱</div>
              <h3>تطبيق ويب</h3>
              <p>استخدم على أي جهاز بدون تثبيت إضافي</p>
            </div>
          </div>
        </div>

        <div class="page" id="studio">
          <section class="panel">
            <div class="panel-head">
              <div class="panel-title">وصف الفيديو</div>
              <div class="badge">AI Creative</div>
            </div>
            <label for="prompt">اكتب وصفًا تفصيليًا للفيديو</label>
            <textarea id="prompt" placeholder="مثال: شاطئ هادئ في الصباح الباكر، أشعة الشمس الذهبية تعكس على سطح البحر، طائرة صغيرة تحلق فوق الأفق، مشهد سينمائي واقعي ومهيب..."></textarea>
          </section>

          <section class="panel">
            <div class="panel-head">
              <div class="panel-title">إعدادات الفيديو</div>
            </div>

            <label>أسلوب الفيديو</label>
            <div class="seg" id="styleSegment">
              <button type="button" class="on" data-style="realistic">واقعي</button>
              <button type="button" data-style="animated">أنيميشن</button>
              <button type="button" data-style="abstract">تجريدي</button>
            </div>

            <div class="two-col">
              <div>
                <label for="resolution">الجودة</label>
                <select id="resolution">
                  <option value="480p">480p</option>
                  <option value="720p" selected>720p</option>
                  <option value="1080p">1080p</option>
                  <option value="4k">4K</option>
                </select>
              </div>
              <div>
                <label for="duration">المدة</label>
                <select id="duration">
                  <option value="5" selected>5 ثواني</option>
                  <option value="8">8 ثواني</option>
                  <option value="10">10 ثواني</option>
                  <option value="15">15 ثانية</option>
                </select>
              </div>
            </div>
          </section>

          <section class="panel">
            <div class="details-wrap">
              <details id="settingsDetails">
                <summary>إعدادات API</summary>
                <div class="inner">
                  <label for="apiKey">مفتاح fal.ai</label>
                  <input id="apiKey" type="password" dir="ltr" placeholder="key_id:key_secret" autocomplete="off" />

                  <label for="model">اسم النموذج</label>
                  <input id="model" dir="ltr" value="fal-ai/wan/v2.2-a14b/text-to-video" />

                  <div class="info-box">
                    قم بالتسجيل في <a href="https://www.fal.ai" target="_blank" rel="noreferrer">fal.ai</a>
                    للحصول على مفتاح مجاني. يتم حفظ المفتاح محليًا فقط على هذا الجهاز.
                  </div>
                </div>
              </details>
            </div>
          </section>

          <button class="primary-btn" id="generateBtn" type="button">إنشاء الفيديو</button>
          <div id="status" class="status info">جاهز للإنشاء</div>
          <div class="progress"><span id="progressFill"></span></div>

          <section class="panel" style="margin-top:20px">
            <div class="panel-head">
              <div class="panel-title">مكتبة الفيديوهات</div>
            </div>
            <div id="library" class="library"></div>
          </section>
        </div>

        <div class="page" id="about">
          <div class="about-section">
            <h2>عن AI Video Studio Pro</h2>
            <p>
              منصة متقدمة توفر لك القدرة على توليد فيديوهات احترافية وعالية الجودة باستخدام الذكاء الاصطناعي.
              بدون الحاجة للتعقيدات المعروفة في إنتاج الفيديو، يمكنك تحويل أفكارك النصية إلى مشاهد بصرية مذهلة.
            </p>
            <p>
              نحن نركز على تقديم تجربة سهلة وسلسة، مع الحفاظ على جودة احترافية عالية جداً.
              كل ما تحتاجه هو وصف واضح، والباقي يتولاه الذكاء الاصطناعي.
            </p>
          </div>

          <div class="about-section">
            <h2>كيف يعمل التطبيق</h2>
            <div class="steps" style="counter-reset:step">
              <div class="step">
                <div class="step-number">1</div>
                <h3>اكتب الوصف</h3>
                <p>اكتب وصفًا واضحًا ومتسلسلًا للفيديو الذي تريده</p>
              </div>
              <div class="step">
                <div class="step-number">2</div>
                <h3>اختر الأسلوب</h3>
                <p>حدد نمط الفيديو: واقعي أو أنيميشن أو تجريدي</p>
              </div>
              <div class="step">
                <div class="step-number">3</div>
                <h3>اختر الجودة</h3>
                <p>حدد جودة الفيديو والمدة المطلوبة</p>
              </div>
              <div class="step">
                <div class="step-number">4</div>
                <h3>انقر الإنشاء</h3>
                <p>اضغط زر "إنشاء الفيديو" وانتظر النتيجة</p>
              </div>
              <div class="step">
                <div class="step-number">5</div>
                <h3>شاهد وحمّل</h3>
                <p>شاهد الفيديو وحمّله على جهازك مباشرة</p>
              </div>
              <div class="step">
                <div class="step-number">6</div>
                <h3>شارك واستمتع</h3>
                <p>شارك فيديوهاتك على وسائل التواصل الاجتماعية</p>
              </div>
            </div>
          </div>

          <div class="about-section">
            <h2>المزايا المتقدمة</h2>
            <p>
              ✓ توليد فيديوهات بدقة سينمائية<br>
              ✓ دعم أنواع متعددة من الفيديوهات<br>
              ✓ جودة تصل إلى 4K<br>
              ✓ مكتبة محلية آمنة للفيديوهات<br>
              ✓ واجهة بسيطة وسهلة الاستخدام<br>
              ✓ معالجة سريعة وفعالة<br>
              ✓ يعمل على جميع الأجهزة
            </p>
          </div>
        </div>
      </div>
    </div>
  </main>

  <script>
    const $ = (id) => document.getElementById(id);

    const Storage = {
      get(key, fallback) {
        try {
          const value = localStorage.getItem(key);
          return value === null ? fallback : JSON.parse(value);
        } catch {
          return fallback;
        }
      },
      set(key, value) {
        try {
          localStorage.setItem(key, JSON.stringify(value));
        } catch {}
      }
    };

    let selectedStyle = 'realistic';

    document.querySelectorAll('.nav-btn').forEach(btn => {
      btn.addEventListener('click', () => {
        document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
        btn.classList.add('active');
        document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
        $(btn.dataset.page).classList.add('active');
      });
    });

    $('startBtn').addEventListener('click', () => {
      document.querySelectorAll('.nav-btn')[1].click();
    });

    $('learnBtn').addEventListener('click', () => {
      document.querySelectorAll('.nav-btn')[2].click();
    });

    function setStatus(message, type = 'info') {
      const el = $('status');
      el.textContent = message;
      el.className = 'status ' + type;
    }

    function setProgress(percent) {
      $('progressFill').style.width = percent + '%';
    }

    $('apiKey').value = Storage.get('apiKey', '');
    $('model').value = Storage.get('model', $('model').value);

    if (!$('apiKey').value) $('settingsDetails').open = true;

    ['apiKey', 'model'].forEach((id) => {
      $(id).addEventListener('change', () => {
        Storage.set(id, $(id).value.trim());
      });
    });

    $('styleSegment').addEventListener('click', (e) => {
      const btn = e.target.closest('button');
      if (!btn) return;
      selectedStyle = btn.dataset.style;
      [...$('styleSegment').querySelectorAll('button')].forEach((b) => {
        b.classList.toggle('on', b === btn);
      });
    });

    function renderLibrary() {
      const items = Storage.get('library', []);
      const lib = $('library');
      lib.innerHTML = '';

      if (!items.length) {
        lib.innerHTML = '<div class=\"empty\">لم يتم إنشاء أي فيديو حتى الآن. ابدأ بكتابة وصف للفيديو.</div>';
        return;
      }

      items.forEach((item, index) => {
        const card = document.createElement('div');
        card.className = 'video-card';

        const created = new Date(item.created).toLocaleDateString('ar-SA', {
          year: 'numeric', month: 'short', day: 'numeric',
          hour: '2-digit', minute: '2-digit'
        });

        card.innerHTML = `
          <div class="video-thumb">
            <video src="${item.url}" controls playsinline preload="metadata"></video>
          </div>
          <div class="video-body">
            <p class="video-title">${item.prompt}</p>
            <p class="video-meta">${created} · ${item.resolution}</p>
          </div>
          <div class="video-actions">
            <button type="button" data-action="download">تحميل</button>
            <button type="button" data-action="delete">حذف</button>
          </div>
        `;

        card.querySelector('[data-action="download"]').addEventListener('click', () => {
          downloadVideo(item.url, 'video-' + Date.now() + '.mp4');
        });

        card.querySelector('[data-action="delete"]').addEventListener('click', () => {
          const arr = Storage.get('library', []);
          arr.splice(index, 1);
          Storage.set('library', arr);
          renderLibrary();
        });

        lib.appendChild(card);
      });
    }

    const sleep = (ms) => new Promise((resolve) => setTimeout(resolve, ms));

    async function downloadVideo(url, filename) {
      try {
        const response = await fetch(url);
        const blob = await response.blob();
        const link = document.createElement('a');
        link.href = URL.createObjectURL(blob);
        link.download = filename;
        document.body.appendChild(link);
        link.click();
        link.remove();
      } catch {
        window.open(url, '_blank');
      }
    }

    async function generateVideo() {
      const apiKey = $('apiKey').value.trim();
      const prompt = $('prompt').value.trim();
      const model = $('model').value.trim();

      if (!apiKey) {
        $('settingsDetails').open = true;
        setStatus('أدخل مفتاح fal.ai أولاً', 'error');
        return;
      }

      if (!prompt) {
        setStatus('اكتب وصف الفيديو أولاً', 'error');
        return;
      }

      const stylePrompt =
        selectedStyle === 'realistic'
          ? 'cinematic photorealistic, highly detailed, realistic lighting, ultra sharp'
          : selectedStyle === 'animated'
          ? 'stylized 3D animation, vibrant colors, smooth motion, polished animation'
          : 'abstract art, surreal, artistic, dreamlike composition';

      const fullPrompt = `${prompt}, ${stylePrompt}`;
      const headers = {
        Authorization: 'Key ' + apiKey,
        'Content-Type': 'application/json'
      };

      $('generateBtn').disabled = true;
      setStatus('جاري إرسال الطلب...', 'info');
      setProgress(8);

      try {
        const response = await fetch('https://queue.fal.run/' + model, {
          method: 'POST',
          headers,
          body: JSON.stringify({
            prompt: fullPrompt,
            resolution: $('resolution').value,
            duration: Number($('duration').value),
            aspect_ratio: '16:9'
          })
        });

        if (!response.ok) {
          const text = await response.text();
          const msg =
            response.status === 401 || response.status === 403
              ? 'المفتاح غير صحيح أو الرصيد غير متوفر'
              : 'فشل الطلب: ' + response.status;
          throw new Error(msg + (text ? ' - ' + text.slice(0, 120) : ''));
        }

        const job = await response.json();
        setStatus('جاري معالجة الفيديو...', 'info');
        setProgress(18);

        for (let i = 0; i < 180; i++) {
          await sleep(4000);
          const poll = await*

