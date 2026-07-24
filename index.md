---
layout: page
title: "Formation & Transition"
---

<div id="password-gate" style="min-height:60vh;display:flex;align-items:center;justify-content:center;font-family:sans-serif;">
  <form id="gate-form" style="background:#fff;padding:2rem;border-radius:8px;box-shadow:0 2px 10px rgba(0,0,0,0.1);text-align:center;border:1px solid #ddd;">
    <p style="margin:0 0 1rem;font-size:1rem;">Enter password to continue</p>
    <input type="password" id="gate-password" style="padding:0.5rem;font-size:1rem;width:200px;" autofocus />
    <button type="submit" style="padding:0.5rem 1rem;font-size:1rem;margin-left:0.5rem;">Go</button>
    <p id="gate-error" style="color:#c00;font-size:0.85rem;margin-top:0.75rem;display:none;">Incorrect password.</p>
  </form>
</div>

<div id="gated-content" style="display:none;" markdown="1">

**Formation & Transition** is a body of theological and ecclesiological research on how a congregation moves from consumer-attendance patterns toward the genuine *ekklēsia* Scripture describes.

## Start Here

### [A Pastoral Working Paper]({{ "/docs/pastoral-working-paper-web.html" | relative_url }})

The synthesis. Read this first — it lays out the whole shape of the research, names what Scripture states directly versus what has been carefully inferred versus what has been borrowed and labeled as borrowed, and closes without resolving what comes next.

### [Would That All the Lord's People Were Prophets]({{ "/docs/would-that-all-the-lords-people-were-prophets-web.html" | relative_url }})

Read this once the Working Paper is finished. It picks up the unresolved close directly — the ache of carrying this alone, and the biblical case for wanting more formed people in it with you, not fewer.

---

## For Further Reading

The working paper above draws on nineteen underlying documents. Anyone who wants to go deeper on a specific piece can find the full research below, grouped as it was built.

### Founding Documents

- [Trained, Not Consumed]({{ "/docs/trained-not-consumed-web.html" | relative_url }}) — the full biblical case for *paideia*/*hexis* formation
- [Assembled, Not Attending]({{ "/docs/assembled-not-attending-web.html" | relative_url }}) — the full biblical case for genuine *ekklēsia* and the *sympatheia* chain
- [Assembled, Not Attending — Greek Word Study]({{ "/docs/assembled-not-attending-greek-word-study-web.html" | relative_url }}) — full lexical detail on all twenty Greek and Hebrew terms involved

### Core Track Documents

- [Development Plan]({{ "/docs/development-plan-web.html" | relative_url }}) — the governing roadmap and First Things
- [Scaling Mechanism Research]({{ "/docs/scaling-mechanism-research-web.html" | relative_url }}) — six historical formation-at-scale models
- [Polity Foundation]({{ "/docs/polity-foundation-web.html" | relative_url }}) — how a leader's formation flows into the body's capacity
- [The Allēlōn Functions]({{ "/docs/allelon-functions-web.html" | relative_url }}) — what the one-another commands require to actually operate
- [The Demand Landscape]({{ "/docs/demand-landscape-web.html" | relative_url }}) — the full cultural-forces case
- [The Telos of a Formed Congregation]({{ "/docs/telos-of-a-formed-congregation.html" | relative_url }}) — what a formed congregation displays and why
- [Modern Western Constraint Matrix]({{ "/docs/modern-western-constraint-matrix.html" | relative_url }}) — seven structural conditions any design must work within
- [Remnant Theology — Biblical Research]({{ "/docs/remnant-theology-biblical-research.html" | relative_url }}) — the exegetical case for a formed-nucleus strategy
- [Pastoral Formation Pathway Assessment]({{ "/docs/pastoral-formation-pathway-assessment.html" | relative_url }}) — the full four-pathway assessment

### More Recent Additions

- [Practitioner Curriculum Source Library]({{ "/docs/practitioner-curriculum-source-library.html" | relative_url }}) — non-scriptural sources organized by practitioner capability
- [Pastoral Briefing Guide]({{ "/docs/pastoral-briefing-guide.html" | relative_url }}) — a spoken-format briefing for groups earlier in the process than this one
- [Pastoral Briefing Visual Companion]({{ "/docs/pastoral-briefing-visual-companion.html" | relative_url }}) — one-page companion to the Briefing Guide
- [New Clothes, Same Body]({{ "/docs/new-clothes-same-body.html" | relative_url }}) — why exit-and-reform cycles repeat themselves
- [Pastor Formation as Prequel to Remnant Cohort Formation]({{ "/docs/pastor-formation-as-prequel.html" | relative_url }}) — the case for concurrent, not sequential, formation and facilitation
- [The Biblical Ekklēsia as Normative Foundation]({{ "/docs/biblical-ekklesia-as-normative-foundation.html" | relative_url }}) — the full warrant argument
- [Facilitator Competency — Initial Stage]({{ "/docs/facilitator-competency-initial-stage.html" | relative_url }}) — the first-stage framework for holding formation space for others
- [Plurality, Multiplication & the Architecture of Formed Leadership]({{ "/docs/plurality-multiplication.html" | relative_url }}) — the full research behind *Would That All the Lord's People Were Prophets*, including the historical and denominational landscape that reader-facing version leaves out

---

*This research is not a consulting product. It is a development track — theological and ecclesiological groundwork toward understanding what genuine ekklēsia requires and what produces it.*

</div>

<script>
  const CORRECT_HASH = "2fe70464aadf5873057c7c15ef38cc0d7fdb1cbb55b14e4f3c934e9ea45ad6f5";

  async function sha256(text) {
    const buf = await crypto.subtle.digest('SHA-256', new TextEncoder().encode(text));
    return Array.from(new Uint8Array(buf)).map(b => b.toString(16).padStart(2, '0')).join('');
  }

  function unlock() {
    document.getElementById('password-gate').style.display = 'none';
    document.getElementById('gated-content').style.display = 'block';
  }

  if (sessionStorage.getItem('gate-unlocked') === CORRECT_HASH) {
    unlock();
  }

  document.getElementById('gate-form').addEventListener('submit', async (e) => {
    e.preventDefault();
    const input = document.getElementById('gate-password').value;
    const hash = await sha256(input);
    if (hash === CORRECT_HASH) {
      sessionStorage.setItem('gate-unlocked', CORRECT_HASH);
      unlock();
    } else {
      document.getElementById('gate-error').style.display = 'block';
    }
  });
</script>
