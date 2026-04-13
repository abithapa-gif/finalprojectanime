# User Testing Findings — Anime Vault

**Testers:** 3 people (1 mobile casual fan, 1 desktop non-fan, 1 desktop fan + dev) | **Tasks:** 3 per tester

---

## ✅ What Worked

**Navigation was immediately clear to all three testers.** Every tester found the Series page and the About page on their first try without hesitation. The four-item nav (Home, About, Series, Contact) was simple enough that nobody misunderstood what any label meant — even the non-anime watcher knew "Series" meant the shows.

**The dark theme read as intentional and professional.** Two testers commented on the design without being asked — Tester A said it felt "like a real website," and Tester B called the form "professional." Nobody said it felt like a dark-mode cliché or a school project with CSS applied.

**Episode count information on series cards was immediately useful.** Tester A said "87 episodes — okay that's actually doable" when reading the Attack on Titan card, unprompted. This validated putting episode counts directly on the cards rather than making users click for details.

**The contact form layout and labels were understood by all three testers** with no structural confusion. Required vs. optional fields were clear, input types made sense, and the subject dropdown options covered realistic use cases.

---

## ⚠️ What Confused Them

**Filter buttons gave no visual feedback.** Tester C (the developer) clicked the filter buttons and immediately flagged that they looked inert — no active state, no pressed state, nothing changed. Even with CSS-only limitations, the buttons should acknowledge being clicked. Tester B didn't even try them, which suggests they looked non-interactive at first glance.

**"Fan Username" field confused the non-fan.** Tester B asked "what's a fan username?" The label assumes familiarity with the concept of community usernames. The help text below the field ("Your Discord or community handle if you have one") does explain it, but it was missed.

**The success message block below the form went unnoticed.** All three testers submitted the form and looked at the button — not below it — for feedback. The static success block didn't register as a "this is what you'd see" demonstration to two of the three testers.

---

## 🔄 What I Changed

**Added explicit `:focus` styling to the filter buttons.** Based on Tester C's feedback (and the visual evidence from Tester B ignoring them), I ensured filter buttons have a clear focus/active border state with the purple accent color. This is both a usability fix and an accessibility fix — keyboard users need visible focus states, which is also a WAVE requirement.

**Made the series detail info more prominent in cards.** Tester A suggested putting the most important info first. I reordered the series-info-list within each card so that studio and episode count appear before the genre and status rows, since those are the two things users scanned for first.

---

## 🚫 What I Didn't Change

**"Fan Username" label wording.** Tester B's confusion was noted, but the field is optional and has descriptive hint text. Changing it to something more generic like "Username or Handle" might be marginally clearer, but it removes the personality that makes the form feel like it belongs to a fan site rather than a corporate contact page. The hint text ("Your Discord or community handle if you have one") does its job for anyone who needs it.

**Success message placement.** The form success state is a static demonstration because the project requires no JavaScript and there is no backend. Moving the `.success-message` div would not solve the core issue — it's not connected to the submit button by design, and that is documented in a code comment for the instructor. Adding a note in the form ("You'll see a confirmation here after sending") was considered but would look strange in a real production form.
