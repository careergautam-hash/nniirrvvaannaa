<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>AK CLASSES — Class 12 Question Paper (Merged)</title>

  <!-- --------- Page 1 styles (kept) --------- -->
  <style>
    /* Page size and print settings */
    @page { size: A4; margin: 10mm 10mm; }
    html, body { height: 100%; margin: 0; -webkit-print-color-adjust: exact; }

    body {
      font-family: Arial, Helvetica, sans-serif;
      font-size: 11px;            /* small to compress content */
      line-height: 1.02;         /* minimum spacing between lines */
      color: #000;
      padding: 12mm 10mm;
      box-sizing: border-box;
      background: #fff;
    }

    /* Container that will be printed on A4 pages */
    .paper {
      width: 190mm;             /* A4 printable width minus margins */
      min-height: 277mm;        /* A4 printable height minus margins */
      margin: 0 auto;
      position: relative;
      box-sizing: border-box;
      column-count: 2;          /* two columns to compress content into 2 pages */
      column-gap: 12mm;
      break-inside: avoid;
    }

    header {
      text-align: center;
      margin-bottom: 6px;
    }
    h1 { margin: 0; font-size: 16px; letter-spacing: 1px; }
    .meta { font-size: 10px; margin-top: 3px; }

    .instructions {
      margin: 6px 0 10px 0;
      font-size: 10px;
      line-height: 1.02;
    }

    ol.questions { counter-reset: qnum; margin:0; padding:0; }
    ol.questions li {
      display: block;
      margin: 2px 0;            /* very small vertical spacing */
      padding: 0 0 0 0;
      break-inside: avoid-column;
    }

    /* small answer choices style for MCQs */
    .choices { margin-left: 10px; font-size: 10px; }

    /* Sections styling */
    .section-title { display:block; width:100%; margin:6px 0 2px 0; font-weight:700; }
    .marks { font-weight:600; font-size:10px; }

    /* Make sure watermarks appear on every printed page */
    @media print {
      body { margin: 0; }
      .paper { column-break-inside: avoid; }
      .watermark { -webkit-print-color-adjust: exact; }
    }

    /* Footer area for marks distribution */
    .marks-summary { display:block; margin-top: 6px; font-size: 10px; }

    /* Reduce space for headings inside columns */
    .section-header { font-weight:700; font-size:12px; margin-top:4px; }

    /* Avoid page breaks inside list items */
    li { break-inside: avoid; }
  </style>

  <!-- --------- Page 2 styles (kept) ---------
       Note: some rules are adapted to avoid conflict.
       Hindi-specific typography is applied to .hindi-section below.
  -->
  <style>
    @page { /* keep/override Page2 @page margin if needed; already set above */ }

    /* Hindi section font — keep original family, applied only to the Hindi block */
    .hindi-section {
      font-family: "Noto Sans Devanagari", sans-serif;
      font-size: 11px;
      line-height: 1.1;
      position: relative;
      margin-top: 12mm;
      /* ensure Hindi section flows after the first paper content */
    }

    /* Page2 had watermark positioning but we'll use a unified watermark below */
    /* Page2 heading sizes */
    .hindi-section h1, .hindi-section h2, .hindi-section h3 {
      text-align: center;
      margin: 0;
    }
    .hindi-section h1 { font-size: 18px; margin-bottom: 4px; }
    .hindi-section h2 { font-size: 14px; margin-bottom: 4px; }
    .hindi-section h3 { font-size: 12px; margin-top: 8px; }

    .hindi-section ol { margin: 0; padding-left: 18px; }
    .hindi-section .section { margin-bottom: 8px; }
    .hindi-section .question { margin-bottom: 3px; }
    .hindi-section .options { margin-left: 18px; }

    /* Reduce hr margin used in Page2 */
    hr { border: none; border-top: 1px solid #ccc; margin: 10px 0; }
  </style>

  <!-- --------- Unified watermark style (single faint watermark used in six positions) --------- -->
  <style>
    /* unified faint watermark used across the merged document */
    .watermark {
      position: fixed;
      font-size: 42px;
      font-weight: 700;
      color: rgba(0,0,0,0.06); /* faint and semi-transparent */
      pointer-events: none;
      white-space: nowrap;
      -webkit-print-color-adjust: exact;
      z-index: 9999;
      transform-origin: center;
    }

    /* Top row */
    .wm-top-left  { top: 12mm; left: 8%; transform: translateX(-50%) rotate(-20deg); }
    .wm-top-center{ top: 12mm; left: 50%; transform: translateX(-50%) rotate(-25deg); }
    .wm-top-right { top: 12mm; left: 92%; transform: translateX(-50%) rotate(-20deg); }

    /* Bottom row */
    .wm-bot-left  { bottom: 12mm; left: 8%; transform: translateX(-50%) rotate(-20deg); top: auto; }
    .wm-bot-center{ bottom: 12mm; left: 50%; transform: translateX(-50%) rotate(-25deg); top: auto; }
    .wm-bot-right { bottom: 12mm; left: 92%; transform: translateX(-50%) rotate(-20deg); top: auto; }

    /* Ensure watermarks print (some printers ignore z-index; use opacity and fixed positioning) */
    @media print {
      .watermark { color: rgba(0,0,0,0.06); z-index: -1; } /* send behind content when printing */
    }

    /* Make sure Hindi section doesn't inherit the Page1 two-column layout */
    .hindi-section { column-count: 1; }
  </style>

</head>
<body>

  <!-- Unified watermarks (six fixed positions). Text: AK CLASSES (faint) -->
  <div class="watermark wm-top-left">AK CLASSES</div>
  <div class="watermark wm-top-center">AK CLASSES</div>
  <div class="watermark wm-top-right">AK CLASSES</div>
  <div class="watermark wm-bot-left">AK CLASSES</div>
  <div class="watermark wm-bot-center">AK CLASSES</div>
  <div class="watermark wm-bot-right">AK CLASSES</div>

  <!-- ==================== Page 1 content (kept as-is, first) ==================== -->
  <div class="paper" id="paper">
    <header>
      <h1>AK CLASSES — Class 12 Examination</h1>
      <div class="meta">Subject: ____________________ &nbsp; | &nbsp; Date: ____________ &nbsp; | &nbsp; Duration: ____ hrs</div>
    </header>

    <div class="instructions">
      Instructions: Total marks: 100. Read instructions carefully before attempting. Minimum spacing has been applied to compress content — use A4, two-column print and "Save as PDF" to produce a 2-page PDF. Watermarks are fixed and will appear on the saved PDF.
    </div>

    < ="clear:both; column-span: all; margin-top:8px; font-size:10px;">
      <strong>Marks distribution:</strong> Section A — Attempt any 20 ×1 = 20 marks. Section B — Attempt any 15 ×2 = 30 marks. Section C — Attempt any 10 ×5 = 50 marks. Total = 100 marks.
    </div>

    <div style="margin-top:12mm; font-size:10px;">Signature of Examiner: ________________________</div>
  </div>

  <!-- ==================== Page 2 content (Hindi) — placed AFTER Page 1 content ==================== -->
  <div class="hindi-section" lang="hi" aria-label="Hindi version of paper">
    <!-- Keep Page 2 heading/title structure -->
    <h1>AK CLASSES</h1>
    <h2>कक्षा 12 परीक्षा प्रश्नपत्र</h2>
    <h3>कुल प्रश्न: 90 | समय: 3 घंटे | अधिकतम अंक: 100</h3>

    <hr>

    <div class="section">
      <h3>SECTION A: बहुविकल्पीय प्रश्न (किसी भी 40 प्रश्नों के उत्तर दें)</h3>
      <ol>
        <li class="question">गाँधीजी शिक्षा का उद्देश्य क्या मानते थे?<br>
          <div class="options">(A) नौकरी पाना<br>(B) वैज्ञानिक दक्षता<br>(C) चरित्र-निर्माण<br>(D) यांत्रिक दक्षता</div>
        </li>
        <li class="question">घनानंद ने किस मार्ग को अत्यन्त सीधा व सरल कहा है?<br>
          <div class="options">(A) क्रोध<br>(B) प्रेम<br>(C) घृणा<br>(D) कपट</div>
        </li>
        <li class="question">'रसखान' को किसने दीक्षा दी?<br>
          <div class="options">(A) वल्लभाचार्य<br>(B) गोकुलनाथ<br>(C) गोस्वामी विट्ठलनाथ<br>(D) गोरखनाथ</div>
        </li>
        <li class="question">घनानंद किस भाषा के कवि हैं?<br>
          <div class="options">(A) अवधी<br>(B) ब्रजभाषा<br>(C) भोजपुरी<br>(D) गुजराती</div>
        </li>
        <li class="question">'तुलनात्मक व्याकरण' किसकी रचना है?<br>
          <div class="options">(A) सातकोड़ी होता<br>(B) सुजाता<br>(C) काल्डवेल<br>(D) सौवर दइया</div>
        </li>
        <li class="question">मंगम्मा को किससे विवाद था?<br>
          <div class="options">(A) बेटे से<br>(B) बहू से<br>(C) पोते से<br>(D) सास से</div>
        </li>
        <li class="question">'हिरोशिमा' शीर्षक कविता में वर्णित सूरज कहाँ निकला?<br>
          <div class="options">(A) पूर्वी क्षितिज पर<br>(B) नगर के चौक पर<br>(C) पूर्वी दिशा में<br>(D) इनमें से कहीं नहीं</div>
        </li>
        <li class="question">अव्ययीभाव समास का उदाहरण है?<br>
          <div class="options">(A) लवकुश<br>(B) भरपेट<br>(C) त्रिभुवन<br>(D) छत्रधारी</div>
        </li>
        <li class="question">बेईमान में कौन-सा उपसर्ग है?<br>
          <div class="options">(A) बेइन<br>(B) बेइ<br>(C) बे<br>(D) इन</div>
        </li>
        <li class="question">इनमें से शुद्ध वाक्य को पहचानें।<br>
          <div class="options">(A) मेरे को घर जाना है।<br>(B) मेरा नाम आनन्द जी है।<br>(C) मेरे को घर जाना है।<br>(D) मुझको घर पर जाना है।</div>
        </li>
        <li class="question">'अज्ञान' का पर्यायवाची शब्द है।<br>
          <div class="options">(A) ज्ञान<br>(B) अज्ञान<br>(C) अज्ञानता<br>(D) समझ</div>
        </li>
        <li class="question">'अज्ञान' का विलोम शब्द है।<br>
          <div class="options">(A) ज्ञान<br>(B) अज्ञान<br>(C) अज्ञानता<br>(D) समझ</div>
        </li>
        <li class="question">'अत्यधिक' में कौन-सा उपसर्ग है?<br>
          <div class="options">(A) अति<br>(B) परा<br>(C) उप<br>(D) अनु</div>
        </li>
        <li class="question">'अत्यधिक' शब्द का अर्थ क्या है?<br>
          <div class="options">(A) बहुत अधिक<br>(B) थोड़ा<br>(C) कम<br>(D) मध्यम</div>
        </li>
        <li class="question">मैक्समूलर ने सर्वविद्संपदा और प्राकृतिक सौंदर्य से परिपूर्ण किस देश को माना है?<br>
          <div class="options">(A) जापान<br>(B) श्रीलंका<br>(C) India<br>(D) कनाडा</div>
        </li>
        <li class="question">गुरु नानक के किस पद में राम-नाम के कीर्तन पर बल दिया गया है?<br>
          <div class="options">(A) प्रथम पद<br>(B) द्वितीय पद<br>(C) तृतीय पद<br>(D) इनमें से कोई नहीं</div>
        </li>
        <li class="question">राधा किसकी पत्नी है?<br>
          <div class="options">(A) कैलास की<br>(B) नारायण की<br>(C) हरि की<br>(D) बिज्जू की</div>
        </li>
        <li class="question">बहादुर से सोने के समय कौन मालिश करता था?<br>
          <div class="options">(A) किशोर<br>(B) निर्मला<br>(C) लेखक<br>(D) काशु</div>
        </li>
        <li class="question">बिरजू महाराज की शादी कितनी उम्र में हुई थी?<br>
          <div class="options">(A) 16 वर्ष<br>(B) 18 वर्ष<br>(C) 15 वर्ष<br>(D) 17 वर्ष</div>
        </li>
        <li class="question">'श्रम' शब्द का पर्यायवाची है?<br>
          <div class="options">(A) परिश्रम<br>(B) श्रम<br>(C) काम<br>(D) मजदूरी</div>
        </li>
        <li class="question">'विनायक' शब्द का संधि विच्छेद क्या है?<br>
          <div class="options">(A) वि + नायक<br>(B) विन + नायक<br>(C) विना + यक<br>(D) इनमें से कोई नहीं</div>
        </li>
        <li class="question">'अग्नि' शब्द का विलोम है?<br>
          <div class="options">(A) जल<br>(B) पृथ्वी<br>(C) वायु<br>(D) आकाश</div>
        </li>
        <li class="question">'उच्छ्वास' शब्द का अर्थ है?<br>
          <div class="options">(A) ऊपर की श्वास<br>(B) अंदर की श्वास<br>(C) नीचे की श्वास<br>(D) बाहर की श्वास</div>
        </li>
        <!-- Remaining Hindi MCQs up to 40 can be pasted here if needed -->
      </ol>
    </div>

    <hr>

    <div class="section">
      <h3>SECTION B: लघु उत्तरीय प्रश्न (किसी भी 15 प्रश्नों के उत्तर दें)</h3>
      <ol start="41">
        <li>‘चरित्र निर्माण’ शब्द से आप क्या समझते हैं?</li>
        <li>‘घनानंद’ की कविता की प्रमुख विशेषताएँ लिखिए।</li>
        <li>‘अव्ययीभाव समास’ का उदाहरण दीजिए।</li>
        <li>‘हिरोशिमा’ कविता का संदेश क्या है?</li>
        <li>‘गुरु नानक’ के उपदेश का मुख्य सार क्या है?</li>
        <li>‘मैक्समूलर’ ने भारत की किन बातों की प्रशंसा की?</li>
        <li>‘अत्यधिक’ शब्द का प्रयोग कर दो वाक्य बनाइए।</li>
        <li>‘रसखान’ का जीवन दर्शन क्या है?</li>
        <li>‘अग्नि’ शब्द से क्या प्रतीक मिलता है?</li>
        <li>‘श्रम’ का महत्व स्पष्ट कीजिए।</li>
        <li>‘अज्ञान’ से समाज को क्या हानि होती है?</li>
        <li>‘बेईमान’ शब्द से वाक्य बनाइए।</li>
        <li>‘राधा’ का साहित्यिक स्वरूप वर्णन करें।</li>
        <li>‘विनायक’ का अर्थ क्या है?</li>
        <li>‘प्रेम’ के मार्ग को सरल क्यों कहा गया है?</li>
        <li>‘भाषा’ का समाज पर प्रभाव क्या है?</li>
        <li>‘सत्य’ का महत्व बताइए।</li>
        <li>‘कवि’ समाज का दर्पण क्यों कहलाता है?</li>
        <li>‘शिक्षा’ का उद्देश्य क्या होना चाहिए?</li>
        <li>‘कला’ का महत्व समझाइए।</li>
        <li>‘भारतीय संस्कृति’ की विशेषताएँ क्या हैं?</li>
        <li>‘चरित्र’ निर्माण में शिक्षा की भूमिका लिखिए।</li>
        <li>‘कविता’ जीवन से कैसे जुड़ी है?</li>
        <li>‘भक्ति’ और ‘प्रेम’ का संबंध स्पष्ट करें।</li>
        <li>‘गांधीजी’ के अनुसार सच्ची शिक्षा क्या है?</li>
        <li>‘अध्ययन’ का लाभ लिखिए।</li>
        <li>‘गुरु’ का महत्व बताइए।</li>
        <li>‘भारत’ की विशेषता क्या है?</li>
        <li>‘विद्या’ का उद्देश्य क्या होना चाहिए?</li>
        <li>‘महात्मा गांधी’ के विचारों पर टिप्पणी करें।</li>
      </ol>
    </div>

    <hr>

    <div class="section">
      <h3>SECTION C: दीर्घ उत्तरीय प्रश्न (किसी भी 10 प्रश्नों के उत्तर दें)</h3>
      <ol start="71">
        <li>‘भारतीय संस्कृति और शिक्षा’ पर एक निबंध लिखिए।</li>
        <li>‘घनानंद’ के काव्य में प्रेम का चित्रण कीजिए।</li>
        <li>‘गुरु नानक’ के उपदेशों पर टिप्पणी करें।</li>
        <li>‘मैक्समूलर’ द्वारा भारत की प्रशंसा का विश्लेषण करें।</li>
        <li>‘गांधीजी’ के शिक्षा संबंधी विचारों का विवेचन करें।</li>
        <li>‘भक्ति साहित्य’ का सामाजिक प्रभाव बताइए।</li>
        <li>‘हिरोशिमा’ कविता का भावार्थ लिखिए।</li>
        <li>‘रसखान’ की कविताओं में प्रेम भावना का वर्णन करें।</li>
        <li>‘भारतीय भाषा और साहित्य’ पर विस्तृत टिप्पणी करें।</li>
        <li>‘चरित्र निर्माण में शिक्षा’ की भूमिका लिखिए।</li>
        <li>‘साहित्य समाज का दर्पण है’ — इस कथन की व्याख्या करें।</li>
        <li>‘श्रम’ का जीवन में महत्व लिखिए।</li>
        <li>‘भारत की सांस्कृतिक एकता’ पर निबंध लिखिए।</li>
        <li>‘कवि’ की समाज में भूमिका समझाइए।</li>
        <li>‘ज्ञान और अज्ञान’ का तुलनात्मक विवेचन कीजिए।</li>
        <li>‘कला और साहित्य’ का संबंध बताइए।</li>
        <li>‘मानवता’ का महत्व बताइए।</li>
        <li>‘प्रेम’ की शक्ति पर अपने विचार लिखिए।</li>
        <li>‘सत्य और अहिंसा’ के महत्व पर चर्चा कीजिए।</li>
        <li>‘भारतीय शिक्षा पद्धति’ की विशेषताओं पर लेख लिखिए।</li>
      </ol>
    </div>
  </div>

  <!-- Keep the Page 1 script (kept) -->
  <script>
    function saveAsPDF() {
      window.print();
    }
    // Optionally, call saveAsPDF() from the console or create a button if needed.
  </script>

</body>
</html>