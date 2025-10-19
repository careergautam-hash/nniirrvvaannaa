<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Animated Question Paper — 5 Questions</title>
  <style>
    :root{
      --bg:#071026;
      --card:#081226;
      --accent:#3b82f6;
      --muted:#94a3b8;
      --glass: rgba(255,255,255,0.03);
      --success:#10b981;
      --danger:#ef4444;
      --radius:12px;
      --width:920px;
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      font-family:Inter, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      background:
        radial-gradient(600px 400px at 10% 10%, rgba(59,130,246,0.05), transparent),
        radial-gradient(500px 300px at 90% 90%, rgba(16,185,129,0.03), transparent),
        var(--bg);
      color:#e6eef8;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:28px;
    }

    .container {
      width: min(var(--width), 96vw);
      background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      border-radius: calc(var(--radius) + 6px);
      padding:16px;
      box-shadow: 0 10px 30px rgba(2,6,23,0.75);
      overflow: hidden;
    }

    .topbar {
      display:flex;
      gap:12px;
      align-items:center;
      justify-content:space-between;
      margin-bottom:10px;
    }
    .title {
      display:flex;
      gap:12px;
      align-items:center;
      font-size:18px;
      font-weight:700;
      color:#e7f0ff;
    }
    .meta {
      display:flex;
      gap:10px;
      align-items:center;
    }

    .timer {
      display:flex;
      gap:10px;
      align-items:center;
      background:var(--glass);
      padding:6px 10px;
      border-radius:999px;
      color:var(--muted);
      font-weight:600;
      font-size:14px;
    }
    .timer strong{color:var(--accent)}
    .timer-bar-wrap{
      width:160px;
      height:8px;
      background: rgba(255,255,255,0.03);
      border-radius:999px;
      overflow:hidden;
    }
    .timer-bar{
      height:100%;
      width:100%;
      background: linear-gradient(90deg, var(--accent), #60a5fa);
      transition: width 0.25s linear, background 0.3s linear;
    }

    .stage {
      display:flex;
      height:480px;
      max-height:65vh;
      align-items:center;
      justify-content:center;
      position:relative;
      overflow:hidden;
      padding:18px;
    }

    .slide {
      position:absolute;
      width:100%;
      max-width: calc(var(--width) - 56px);
      left:50%;
      transform: translateX(-50%) translateY(0) scale(0.98);
      background: linear-gradient(180deg, rgba(255,255,255,0.015), rgba(255,255,255,0.008));
      border-radius: var(--radius);
      padding:22px;
      box-shadow: 0 8px 26px rgba(2,6,23,0.6);
      opacity:0;
      pointer-events:none;
      transition: transform 420ms cubic-bezier(.2,.9,.3,1), opacity 320ms ease;
      will-change: transform, opacity;
    }
    .slide.active {
      opacity:1;
      pointer-events:auto;
      transform: translateX(-50%) translateY(0) scale(1);
    }
    .slide.in-from-right { transform: translateX(30%) scale(0.98); opacity:0; }
    .slide.in-from-left  { transform: translateX(-30%) scale(0.98); opacity:0; }
    .slide.out-to-left   { transform: translateX(-40%) scale(0.98); opacity:0; }
    .slide.out-to-right  { transform: translateX(40%) scale(0.98); opacity:0; }

    .q-head { display:flex; justify-content:space-between; align-items:center; gap:10px; margin-bottom:12px; }
    .q-num { font-weight:800; color:#eaf2ff; font-size:16px; }
    .q-type { font-size:13px; color:var(--muted); padding:6px 8px; border-radius:10px; background:rgba(255,255,255,0.02) }

    .q-body { font-size:18px; line-height:1.5; color:#e6eef8; margin-bottom:14px; }
    .choices {display:flex; flex-direction:column; gap:10px; margin-bottom:14px}
    .choice {
      background: rgba(255,255,255,0.02);
      padding:10px 12px;
      border-radius:10px;
      cursor:pointer;
      transition: background 140ms, transform 120ms;
      border: 1px solid rgba(255,255,255,0.03);
      user-select:none;
    }
    .choice:hover { background: rgba(255,255,255,0.035); transform: translateY(-2px); }
    .choice.selected { outline:2px solid rgba(59,130,246,0.18); background: linear-gradient(90deg, rgba(59,130,246,0.06), rgba(96,165,250,0.02)); }

    .short-answer { width:100%; min-height:84px; resize:vertical; padding:10px; border-radius:10px; background:rgba(255,255,255,0.02); color:inherit; border:1px solid rgba(255,255,255,0.03); }

    .actions { display:flex; gap:8px; align-items:center; margin-top:6px; }
    .btn {
      background:transparent;
      border:1px solid rgba(255,255,255,0.06);
      color: #dbeafe;
      padding:8px 12px;
      border-radius:8px;
      cursor:pointer;
      transition: background 140ms, transform 120ms;
    }
    .btn:hover{ background: rgba(255,255,255,0.02); transform: translateY(-1px); }
    .btn.primary {
      background: linear-gradient(90deg, var(--accent), #60a5fa);
      color: #021028;
      border: none;
      font-weight:700;
      box-shadow: 0 6px 18px rgba(59,130,246,0.12);
    }

    .nav { display:flex; gap:8px; align-items:center; justify-content:space-between; margin-top:12px; }

    .bottom { display:flex; align-items:center; justify-content:space-between; margin-top:12px; gap:12px; }
    .progress-wrap { flex:1; display:flex; align-items:center; gap:12px; }
    .progress { height:10px; flex:1; background: rgba(255,255,255,0.03); border-radius:999px; overflow:hidden; }
    .progress-inner { height:100%; width:0%; background: linear-gradient(90deg, #34d399, #60a5fa); transition: width 360ms ease; }
    .dots { display:flex; gap:8px; align-items:center; }
    .dot { width:10px; height:10px; border-radius:50%; background: rgba(255,255,255,0.06); cursor:pointer; transition: transform 120ms, background 120ms; border:1px solid rgba(255,255,255,0.03); }
    .dot.active { transform: scale(1.25); background: var(--accent); box-shadow:0 6px 18px rgba(59,130,246,0.12); }

    .overlay {
      position:absolute;
      inset:0;
      display:flex;
      align-items:center;
      justify-content:center;
      background: linear-gradient(180deg, rgba(2,6,23,0.85), rgba(2,6,23,0.9));
      z-index:40;
      color:#e6eef8;
      gap:18px;
      padding:20px;
      text-align:center;
      display:none;
      flex-direction:column;
    }
    .overlay.show { display:flex; }
    .small { font-size:13px; color:var(--muted) }

    @media (max-width:760px){
      .stage{height:auto; max-height:unset; padding:10px}
      .container{padding:12px}
      .slide{padding:14px}
      .timer-bar-wrap{width:110px}
    }
  </style>
</head>
<body>
  <main class="container" role="application" aria-label="Question paper widget">
    <div class="topbar">
      <div class="title" aria-hidden="false">
        <svg width="28" height="28" viewBox="0 0 24 24" fill="none" aria-hidden="true">
          <rect x="3" y="4" width="18" height="16" rx="2" stroke="rgba(255,255,255,0.08)" stroke-width="1.5"/>
          <path d="M7 8h10" stroke="rgba(255,255,255,0.08)" stroke-width="1.5" stroke-linecap="round"/>
        </svg>
        Animated Question Paper
      </div>

      <div class="meta">
        <div class="timer" aria-live="polite" title="Remaining time">
          <span class="timer-label small">Time</span>
          <strong id="timer-text">05:00</strong>
          <div class="timer-bar-wrap" aria-hidden="true">
            <div id="timer-bar" class="timer-bar" style="width:100%"></div>
          </div>
        </div>

        <button id="print-btn" class="btn" title="Print / Save as PDF">Print</button>
      </div>
    </div>

    <section class="stage" id="stage" tabindex="0" aria-live="polite">
      <!-- slides injected here -->
    </section>

    <div class="nav" role="navigation" aria-label="Slide navigation">
      <button id="prev-btn" class="btn" aria-label="Previous question">&larr; Prev</button>
      <div style="display:flex; gap:8px; align-items:center;">
        <div class="small" style="margin-right:8px">Question</div>
        <div id="current-counter" class="small">1 / 5</div>
      </div>
      <button id="next-btn" class="btn primary" aria-label="Next question">Next &rarr;</button>
    </div>

    <div class="bottom">
      <div class="progress-wrap">
        <div class="small">Progress</div>
        <div class="progress" aria-hidden="true">
          <div id="progress-inner" class="progress-inner"></div>
        </div>
      </div>

      <div class="dots" id="dots" aria-hidden="true"></div>
    </div>

    <div class="overlay" id="overlay" role="status" aria-hidden="true">
      <h2 id="overlay-title">Finished</h2>
      <div class="small" id="overlay-sub">You completed the paper or the timer ended.</div>
      <div style="display:flex; gap:8px; margin-top:8px;">
        <button id="restart-btn" class="btn">Restart</button>
        <button id="close-overlay" class="btn primary">Close</button>
      </div>
    </div>
  </main>

  <script>
    // Configuration
    const QUESTIONS = [
      {
        id:1,
        type: 'MCQ',
        q: 'Which of the following is NOT a JavaScript data type?',
        choices: ['Undefined', 'Number', 'Character', 'Symbol'],
        answerIndex: 2
      },
      {
        id:2,
        type: 'Short Answer',
        q: 'Explain event delegation in JavaScript in one sentence.',
        choices: [],
        answerText: 'Event delegation is using a single listener on a parent to handle events from its children via bubbling.'
      },
      {
        id:3,
        type: 'MCQ',
        q: 'What does CSS "flex: 1" do in a flex container?',
        choices: ['Sets flex-basis to 1px', 'Gives the item equal flex-grow/shrink to fill space', 'Fixes width to 1rem', 'Removes margins'],
        answerIndex: 1
      },
      {
        id:4,
        type: 'MCQ',
        q: 'Which HTTP status code means "Not Found"?',
        choices: ['200', '301', '404', '500'],
        answerIndex: 2
      },
      {
        id:5,
        type: 'Short Answer',
        q: 'Write the CSS rule to center a block element horizontally.',
        choices: [],
        answerText: 'Use margin: 0 auto; and a defined width on the block element.'
      }
    ];

    // Timer: total seconds (default 5 minutes)
    let TOTAL_TIME = 60 * 5;

    // State
    let currentIndex = 0;
    let userSelections = new Array(QUESTIONS.length).fill(null);
    let userShortAnswers = new Array(QUESTIONS.length).fill('');
    let timerRemaining = TOTAL_TIME;
    let timerInterval = null;
    let isFinished = false;
    let isAnimating = false;

    // DOM refs
    const stage = document.getElementById('stage');
    const prevBtn = document.getElementById('prev-btn');
    const nextBtn = document.getElementById('next-btn');
    const progressInner = document.getElementById('progress-inner');
    const dotsWrap = document.getElementById('dots');
    const timerText = document.getElementById('timer-text');
    const timerBar = document.getElementById('timer-bar');
    const overlay = document.getElementById('overlay');
    const overlayTitle = document.getElementById('overlay-title');
    const overlaySub = document.getElementById('overlay-sub');
    const restartBtn = document.getElementById('restart-btn');
    const closeOverlay = document.getElementById('close-overlay');
    const currentCounter = document.getElementById('current-counter');
    const printBtn = document.getElementById('print-btn');

    // Build slides
    function createSlide(item, idx) {
      const slide = document.createElement('article');
      slide.className = 'slide';
      slide.dataset.index = idx;

      const head = document.createElement('div');
      head.className = 'q-head';
      head.innerHTML = `<div class="q-num">Q${idx+1}</div><div class="q-type">${item.type}</div>`;

      const body = document.createElement('div');
      body.className = 'q-body';
      body.textContent = item.q;

      slide.appendChild(head);
      slide.appendChild(body);

      if (item.type === 'MCQ') {
        const choices = document.createElement('div');
        choices.className = 'choices';
        item.choices.forEach((c, i) => {
          const btn = document.createElement('button');
          btn.type = 'button';
          btn.className = 'choice';
          btn.textContent = c;
          btn.dataset.choice = i;
          btn.addEventListener('click', () => {
            selectChoice(idx, i);
          });
          choices.appendChild(btn);
        });
        slide.appendChild(choices);
        const actions = document.createElement('div');
        actions.className = 'actions';
        const reveal = document.createElement('button');
        reveal.className = 'btn';
        reveal.textContent = 'Reveal Answer';
        reveal.addEventListener('click', () => revealAnswer(idx, slide));
        actions.appendChild(reveal);
        slide.appendChild(actions);
      } else { // Short answer
        const ta = document.createElement('textarea');
        ta.className = 'short-answer';
        ta.placeholder = 'Type your answer here...';
        ta.value = userShortAnswers[idx] || '';
        ta.addEventListener('input', (e) => {
          userShortAnswers[idx] = e.target.value;
        });
        slide.appendChild(ta);
        const actions = document.createElement('div');
        actions.className = 'actions';
        const reveal = document.createElement('button');
        reveal.className = 'btn';
        reveal.textContent = 'Show Model Answer';
        reveal.addEventListener('click', () => revealAnswer(idx, slide));
        actions.appendChild(reveal);
        slide.appendChild(actions);
      }

      return slide;
    }

    function mountSlides() {
      stage.innerHTML = '';
      QUESTIONS.forEach((q, i) => {
        const s = createSlide(q, i);
        stage.appendChild(s);
      });
      updateDots();
      showSlide(0, false);
    }

    // Navigation & animation
    function showSlide(newIndex, withAnimation = true, direction = 'left') {
      if (isAnimating || isFinished) return;
      const slides = Array.from(stage.querySelectorAll('.slide'));
      if (newIndex < 0) newIndex = 0;
      if (newIndex >= slides.length) newIndex = slides.length -1;
      const prev = stage.querySelector('.slide.active');
      const next = slides[newIndex];

      if (prev === next) return;

      isAnimating = true;
      // prepare classes for animation
      if (withAnimation && prev) {
        prev.classList.remove('active');
        prev.classList.add(direction === 'left' ? 'out-to-left' : 'out-to-right');
        setTimeout(() => prev.classList.remove('out-to-left','out-to-right'), 450);
      }

      // incoming
      next.classList.add(direction === 'left' ? 'in-from-right' : 'in-from-left');
      // force reflow
      void next.offsetWidth;
      next.classList.add('active');
      next.classList.remove('in-from-right','in-from-left');

      setTimeout(() => {
        isAnimating = false;
      }, 460);

      currentIndex = newIndex;
      updateUI();
    }

    function updateUI() {
      // progress
      const pct = Math.round(((currentIndex + 1) / QUESTIONS.length) * 100);
      progressInner.style.width = `${pct}%`;
      // dots
      Array.from(dotsWrap.children).forEach((d, i) => {
        d.classList.toggle('active', i === currentIndex);
      });
      // counter
      currentCounter.textContent = `${currentIndex+1} / ${QUESTIONS.length}`;

      // reflect selected choices
      const slide = stage.querySelector(`.slide[data-index="${currentIndex}"]`);
      if (!slide) return;
      const choices = slide.querySelectorAll('.choice');
      choices.forEach(c => {
        const i = Number(c.dataset.choice);
        c.classList.toggle('selected', userSelections[currentIndex] === i);
      });
    }

    function selectChoice(qIndex, choiceIndex) {
      userSelections[qIndex] = choiceIndex;
      updateUI();
    }

    function revealAnswer(idx, slide) {
      const q = QUESTIONS[idx];
      const revealWrap = document.createElement('div');
      revealWrap.style.marginTop = '10px';
      revealWrap.style.padding = '10px';
      revealWrap.style.borderRadius = '8px';
      revealWrap.style.background = 'rgba(255,255,255,0.02)';
      revealWrap.style.border = '1px solid rgba(255,255,255,0.03)';
      if (q.type === 'MCQ') {
        const correct = q.answerIndex;
        revealWrap.innerHTML = `<strong style="color:var(--accent)">Correct answer:</strong> ${q.choices[correct]}`;
        // highlight correct / wrong choices
        const choices = slide.querySelectorAll('.choice');
        choices.forEach((el, i) => {
          el.style.outline = '';
          if (i === correct) {
            el.style.background = 'linear-gradient(90deg, rgba(34,197,94,0.08), rgba(96,165,250,0.02))';
            el.style.border = '1px solid rgba(34,197,94,0.15)';
          } else if (userSelections[idx] === i) {
            el.style.border = '1px solid rgba(239,68,68,0.15)';
          }
        });
      } else {
        revealWrap.innerHTML = `<strong style="color:var(--accent)">Model answer:</strong> ${q.answerText}`;
      }
      // avoid adding multiple reveals
      const existing = slide.querySelector('.reveal');
      if (existing) existing.remove();
      revealWrap.className = 'reveal';
      slide.appendChild(revealWrap);
    }

    // Dots
    function updateDots() {
      dotsWrap.innerHTML = '';
      QUESTIONS.forEach((_, i) => {
        const d = document.createElement('div');
        d.className = 'dot';
        d.title = `Go to question ${i+1}`;
        d.addEventListener('click', () => {
          showSlide(i, true, i > currentIndex ? 'left' : 'right');
        });
        dotsWrap.appendChild(d);
      });
      updateUI();
    }

    // Timer
    function startTimer() {
      stopTimer();
      timerRemaining = TOTAL_TIME;
      updateTimerUI();
      timerInterval = setInterval(() => {
        timerRemaining--;
        if (timerRemaining <= 0) {
          timerRemaining = 0;
          updateTimerUI();
          stopTimer();
          finishPaper('Time is up');
          return;
        }
        updateTimerUI();
      }, 1000);
    }

    function stopTimer() {
      if (timerInterval) { clearInterval(timerInterval); timerInterval = null; }
    }

    function updateTimerUI() {
      const mm = String(Math.floor(timerRemaining / 60)).padStart(2,'0');
      const ss = String(timerRemaining % 60).padStart(2,'0');
      timerText.textContent = `${mm}:${ss}`;
      const pct = (timerRemaining / TOTAL_TIME) * 100;
      timerBar.style.width = `${pct}%`;
      if (pct < 20) {
        timerBar.style.background = 'linear-gradient(90deg, #fb7185, #ef4444)';
      } else if (pct < 40) {
        timerBar.style.background = 'linear-gradient(90deg, #f59e0b, #f97316)';
      } else {
        timerBar.style.background = 'linear-gradient(90deg, var(--accent), #60a5fa)';
      }
    }

    // Finish handling
    function finishPaper(reason = 'Finished') {
      isFinished = true;
      overlayTitle.textContent = reason === 'Finished' ? 'Finished' : 'Time\'s up';
      overlaySub.textContent = reason === 'Finished' ? 'You completed the paper.' : 'The timer has ended.';
      overlay.classList.add('show');
      overlay.setAttribute('aria-hidden','false');
      stopTimer();
    }

    // Restart
    function restart() {
      isFinished = false;
      overlay.classList.remove('show');
      overlay.setAttribute('aria-hidden','true');
      userSelections = new Array(QUESTIONS.length).fill(null);
      userShortAnswers = new Array(QUESTIONS.length).fill('');
      currentIndex = 0;
      mountSlides();
      startTimer();
    }

    // Submit (simple local scoring for MCQ)
    function submitPaper() {
      // optional: simple scoring
      let correct = 0;
      QUESTIONS.forEach((q, i) => {
        if (q.type === 'MCQ' && q.answerIndex === userSelections[i]) correct++;
      });
      finishPaper('Finished');
      overlaySub.textContent = `You scored ${correct} / ${QUESTIONS.filter(q=>q.type==='MCQ').length} on MCQs.`;
    }

    // Keyboard navigation
    document.addEventListener('keydown', (e) => {
      if (isFinished) return;
      if (e.key === 'ArrowRight' || e.key === 'PageDown') {
        e.preventDefault();
        goNext();
      } else if (e.key === 'ArrowLeft' || e.key === 'PageUp') {
        e.preventDefault();
        goPrev();
      } else if (e.key === 'Enter' && (e.metaKey || e.ctrlKey)) {
        e.preventDefault();
        submitPaper();
      }
    });

    // Next/Prev
    function goNext() {
      if (currentIndex < QUESTIONS.length -1) {
        showSlide(currentIndex + 1, true, 'left');
      } else {
        // end reached
        submitPaper();
      }
    }
    function goPrev() {
      if (currentIndex > 0) {
        showSlide(currentIndex - 1, true, 'right');
      }
    }

    prevBtn.addEventListener('click', goPrev);
    nextBtn.addEventListener('click', goNext);

    // Overlay buttons
    restartBtn.addEventListener('click', restart);
    closeOverlay.addEventListener('click', () => {
      overlay.classList.remove('show');
      overlay.setAttribute('aria-hidden','true');
    });

    // Print
    printBtn.addEventListener('click', () => window.print());

    // Initialize
    mountSlides();
    startTimer();

    // Expose small helper to show answer on last submit (optional)
    // For accessibility, focus stage on slide change
    const observer = new MutationObserver(() => {
      const active = stage.querySelector('.slide.active');
      if (active) active.scrollIntoView({behavior:'smooth', block:'center'});
    });
    observer.observe(stage, { childList: true, subtree: true });

    // Ensure UI initial update
    updateUI();
  </script>
</body>
</html>
