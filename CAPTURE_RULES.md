# Competitor Screenshot Capture Rules

> Every screenshot should reveal a **distinct business decision or interaction state**.
> If two screens don't tell you something new about the product's logic, only keep one.

---

## 1. Before You Start

Every capture session begins with a clear brief. No brief = aimless screen-grabbing.

### 1.1 Fill Out the Capture Brief

| Field | What to write | Why it matters |
|---|---|---|
| **Question** | The specific product question you're trying to answer | Prevents capturing 50 screens when you only need 8 |
| **Scope** | Which exchanges × which platforms | Ensures parity — you compare apples to apples |
| **Entry condition** | Account state before you start (new user? KYC'd? has balance?) | Different account states show completely different UIs |
| **Happy path** | The exact steps of the main scenario | Keeps you focused on one flow, not wandering |
| **Edge cases** | 1–3 specific error or boundary conditions worth capturing | Captures how the product handles real-world friction |

### 1.2 Example: A Completed Brief

```
Question:    How do competitors handle first-time spot buying for a new user?
Scope:       Binance iOS, OKX iOS, Coinbase iOS, Bitget iOS
Entry:       Fresh account, KYC level 1 verified, 0 USDT balance
Happy path:  Home → Markets → BTC → Buy → attempt purchase → deposit prompt
Edge cases:  (1) What happens with 0 balance?
             (2) Is there a minimum order warning?
             (3) Any first-trade tutorial or tooltip?
```

### 1.3 Rules

- **Do NOT start capturing without a brief.** Even a 2-line brief is better than none.
- **One brief = one flow.** If you need to capture "Spot Trading" and "Futures Trading", write two separate briefs. Do not mix them into one session.
- **Match entry conditions across exchanges.** If you test Binance with a funded account but OKX with zero balance, the comparison is invalid.

---

## 2. Capture or Skip — Decision Framework

For every screen you're about to capture, run it through this framework.

### 2.1 CAPTURE — Key State Transitions

These are the screens that matter. Each represents a **meaningful change** in what the user sees or can do.

| State type | What it reveals | Crypto exchange example |
|---|---|---|
| **Entry point** | How users discover and arrive at this feature | Home tab → "Trade" button; or Markets page → tap BTC row; or banner ad → Earn product |
| **Empty / zero state** | How the product handles first-time or no-data scenarios | Portfolio page with 0 holdings; Trade page before any pair is selected; Order history with no orders |
| **Loaded / populated state** | The "normal" working state with real data. **Capture ONE representative state only** — don't screenshot the same page with BTC, then ETH, then SOL | Trade page with BTC/USDT loaded, order book populated, chart rendered |
| **Decision fork** | Any point where the user must choose between options. This reveals what the product considers important enough to be a separate path | Order type selector (Market / Limit / Stop); Buy vs Sell toggle; Spot vs Margin vs Futures switcher |
| **Input state** | A form or input area with meaningful fields visible — capture the **empty form** showing all fields, and ONE filled state. Do NOT capture multiple typing states | Order form showing: price field, amount field, leverage selector, TP/SL toggle — all visible |
| **Confirmation / review** | The pre-commitment screen. This reveals what information the product thinks the user needs before executing | Order preview showing: pair, side, quantity, estimated fee, slippage, total cost |
| **Terminal state** | The end of the flow. Capture success AND failure if both are accessible | "Order placed" success screen; "Insufficient balance" error; "Order pending" state |
| **Permission / gate** | Any screen that blocks the user from proceeding. Reveals compliance posture and product strategy around access | KYC verification required; Region not supported; Risk assessment questionnaire; "Enable futures trading" toggle |
| **Contextual education** | First-time tooltips, guided tours, inline help that appears conditionally | "What is a limit order?" tooltip; First-trade tutorial overlay; Risk warning for leveraged products |

### 2.2 CAPTURE — Business Logic Signals

These are the details within a screen that reveal **product strategy**. You don't need a separate screenshot for each — just make sure the screen you DO capture clearly shows these elements.

| Signal | What to look for | Why it matters | Example |
|---|---|---|---|
| **Default selections** | What's pre-selected when the user arrives? | Defaults = what the product wants you to do. They've A/B tested this. | OKX defaults to 10x leverage on BTC futures. Binance defaults to 5x. This is a deliberate risk appetite choice. |
| **Information hierarchy** | What's largest/first? What's hidden? | Reveals what the product considers most important for this user at this moment | Coinbase shows total portfolio value as the hero number on Home. OKX shows "Today's PnL" first. Different philosophies. |
| **Upsell / cross-sell** | Banners, cards, or nudges promoting other features inside this flow | Reveals growth strategy and feature priority | Binance shows "Earn 5% APY" banner on the spot trading page. They want traders to also become earners. |
| **Risk controls** | Disclaimers, warnings, cooling-off periods, mandatory acknowledgments | Reveals compliance posture and target user sophistication | OKX requires a quiz before enabling futures. Bitget just shows a disclaimer checkbox. Very different approaches. |
| **Empty state design** | What the product shows (and promotes) when there's no user data | Reveals onboarding strategy — do they educate, upsell, or just show blank? | Coinbase empty portfolio shows "Buy your first crypto" CTA with curated list. Binance shows a tutorial video. |
| **Error handling** | How the product responds to invalid input or failed actions | Reveals engineering quality and user empathy | "Insufficient balance" → does it just show an error, or does it offer a "Deposit now" shortcut? |
| **Navigation structure** | Tab bar items, hamburger menu contents, breadcrumbs | Reveals feature priority and information architecture | Coinbase has 4 tabs (Home, Trade, Explore, Activity). Binance has 5 (Home, Markets, Trade, Futures, Wallet). The difference in tab count = different product philosophy. |

### 2.3 SKIP — Redundant States

These add volume but not value. **Do NOT capture them:**

| Redundant state | Why it's useless | What to do instead |
|---|---|---|
| Keyboard up vs keyboard down on same input | Same screen, different keyboard visibility. Zero new information. | Capture the form with keyboard **down** (shows all fields). Note "keyboard is standard numeric" in annotation. |
| Same list scrolled to different positions | You already showed the list structure with the first screenshot. | Capture top of list only. Note "list continues with X more items" in annotation. |
| Same form with different valid inputs | Typing "0.5 BTC" vs "1.0 BTC" doesn't reveal anything new. | Capture empty form + one filled state. That's it. |
| Loading spinners / skeleton screens | Transient state, not a product decision. | Skip entirely. Exception: if the loading state itself is a design choice (e.g., branded loading animation), note it once. |
| Toast / snackbar notifications | Ephemeral UI that disappears. Hard to read in screenshots. | Note the message text in your annotation. Don't screenshot it. |
| Animation mid-frames | A sheet sliding up halfway is not a state. | Wait for animation to finish, then capture the final state. |
| Identical modal on different parent screens | If "Confirm Order" modal looks the same on Spot and Futures, capture it once. | Capture once. In the other flow, write "Same confirmation modal as Spot — see [reference]." |
| Light mode AND dark mode of the same screen | Unless your brief specifically asks about theming, this doubles your screenshots for zero business insight. | Pick the default theme. Note "also supports dark/light mode" in annotation. |
| Different languages of the same screen | Same UI, different text. | Pick the primary market language (usually English or Chinese). Note available languages once. |

### 2.4 SKIP — Repetitive Across Flows

| Scenario | Rule |
|---|---|
| Shared sub-flow (e.g., "Enter Email → Verify Code" in Sign Up AND Password Reset) | Capture in the FIRST flow you encounter it. In subsequent flows, write: "Email verification — same as Onboarding flow, step 3–4." |
| System permission dialogs (camera, notification, biometric) | Note once in a global "System Permissions" entry. Never screenshot again. |
| Legal/Terms pages | Capture the trigger (where the link is), not the full terms page. Note "Links to standard Terms of Service." |

### 2.5 The Decision Rule

Before you press capture, ask yourself:

> **"If I remove this screenshot from the flow, would a viewer miss a step or lose understanding of how this feature works?"**

- **YES** → this screen carries unique information. Capture it.
- **NO** → this screen is decoration. Skip it.

---

## 3. Technical Requirements

### 3.1 Page Readiness — Mandatory Pre-Capture Checks

A half-loaded screenshot is worse than no screenshot — it takes up space and tells you nothing.

**Visual checklist — confirm ALL before capturing:**

| Element | What "ready" looks like | What "not ready" looks like (DO NOT CAPTURE) |
|---|---|---|
| K-line chart | Candles visible, axis labels rendered, current price line shown | Blank canvas, grey placeholder box, or only axes with no data |
| Depth chart | Bid/ask curves visible with price labels | Empty area or single flat line |
| Order book | At least 5+ bid rows and 5+ ask rows with prices and quantities | Empty rows, skeleton shimmer, or "Loading..." text |
| Account balance | Actual number displayed (even if 0.00 USDT) | Spinner icon, "—", or skeleton placeholder |
| Position / PnL | Numbers rendered with +/- and currency | Loading dots or blank fields |
| Token icons | Circular icons loaded with correct logo | Grey circle placeholder or broken image icon |
| Navigation | All tab bar icons and labels visible | Any tab showing loading state |
| Modals / bottom sheets | Fully expanded to final position, content loaded | Mid-animation, partial slide, or content still loading inside modal |

**If automating with Puppeteer / Playwright, use these wait strategies:**

```
WRONG:  await page.waitForTimeout(3000)      // Arbitrary delay, breaks on slow networks
WRONG:  await page.waitForLoadState('load')   // DOM loaded ≠ data loaded

RIGHT:  await page.waitForSelector('.chart-canvas[data-loaded="true"]')
RIGHT:  await page.waitForSelector('.orderbook-row', { state: 'attached' })
RIGHT:  await page.waitForFunction(() => !document.querySelector('.spinner'))
RIGHT:  await page.waitForFunction(() => {
          const rows = document.querySelectorAll('.orderbook-row');
          return rows.length >= 10;
        })
```

For WebSocket-driven content (K-line, order book, real-time prices):
- Wait until the **first meaningful data paint**, not just DOM ready
- Check that the chart canvas has actual pixel content, not just an empty canvas element
- Verify at least one price tick has been received (price element text is not "—" or "0")

**Discard rule:** After capturing, do a quick visual scan. If any major content area is blank, spinning, or shows placeholder data — **discard and retake**. Do not "fix it later." A bad screenshot contaminates your analysis.

### 3.2 Image Dimensions — Hard Limits

Large screenshots cause the error: `An image in the conversation exceeds the dimension limit for many-image requests (2000px)`. Follow these rules to prevent it.

**Capture resolution by platform:**

| Platform | Capture resolution | Why |
|---|---|---|
| **iOS** | **1x logical resolution** (390×844 for iPhone 14/15). In Simulator: Cmd+1 for 1x. On device: use built-in screenshot, then resize. | @2x = 780×1688, @3x = 1170×2532 — both exceed 2000px on the long side |
| **Android** | **1x or mdpi equivalent**. Target max 1080px on the long side. Most Android screenshots are 1080×2400 — resize to 818×1818. | Stock Android screenshots at high DPI easily exceed 2000px |
| **Web** | Set browser window to **1440×900** or **1280×800** before capturing. Do NOT use: ultra-wide monitors, 4K resolution, Retina @2x capture. | A 2560×1440 screenshot or a Retina capture at 2880×1800 will exceed the limit |

**Processing rules:**

| Situation | Action |
|---|---|
| Screenshot longest side is **under 1800px** | Use as-is. No processing needed. |
| Screenshot longest side is **1800–2000px** | Acceptable, but resize to 1800px if you plan to include 10+ images in one session. |
| Screenshot longest side is **over 2000px** | **MUST resize** before use. Scale down so longest side = 1800px, maintain aspect ratio. |
| Retina / HiDPI capture | Always resize down to 1x equivalent. A @2x capture of an iPhone (1170×2532) must become 585×1266 or similar. |

**Batch analysis limits:**

| Images in session | Rule |
|---|---|
| 1–10 | Safe. Proceed normally. |
| 11–15 | Proceed with caution. Ensure all images are under 1800px longest side. |
| 16–20 | Split into two analysis rounds, OR stitch closely related screens into composite images (e.g., 3 onboarding screens → 1 horizontal strip). |
| 20+ | Must split. Do not send 20+ images in a single analysis session. |

**Recommended resize command (macOS):**
```bash
# Resize single image, longest side to 1800px
sips --resampleHeightWidthMax 1800 screenshot.png

# Batch resize all PNGs in a folder
for f in *.png; do sips --resampleHeightWidthMax 1800 "$f"; done
```

---

## 4. Flow Organization & Annotation

### 4.1 Naming Convention

```
{Exchange}_{Platform}_{Module}_{FlowName}
```

| Part | Values | Example |
|---|---|---|
| Exchange | `Binance`, `OKX`, `Bitget`, `Coinbase` | `OKX` |
| Platform | `iOS`, `Android`, `Web` | `iOS` |
| Module | Top-level feature area | `Trade` |
| FlowName | Specific scenario in PascalCase | `FirstSpotBuy` |

Full example: `OKX_iOS_Trade_FirstSpotBuy`

### 4.2 Flow Structure

A flow should read like a story with no filler. The ideal structure:

```
Entry → [Education?] → Decision → Input → Confirmation → Result
```

**Length guidelines:**

| Flow length | Assessment |
|---|---|
| 3–4 screens | Probably too short. You're likely missing the decision fork or confirmation step. |
| **5–10 screens** | Ideal range. Enough to tell the story, not so much that there's filler. |
| 11–12 screens | Acceptable for complex flows (e.g., futures onboarding with quiz). Review each screen critically. |
| 13+ screens | Too many. You are either (a) capturing redundant states, or (b) mixing two flows. Split it. |

**Branching rule:** If a flow has branches, capture the **common trunk ONCE**, then show only the divergent parts:

```
Example: OKX_iOS_Trade_SpotOrder

Trunk (shared):
  1. Home → Markets tab
  2. Search "BTC" → tap BTC/USDT
  3. Tap "Buy" button

Branch A — Market Order:
  4a. Market order form (amount input)
  5a. Confirm → Success

Branch B — Limit Order:
  4b. Limit order form (price + amount inputs)
  5b. Confirm → Success → Open Orders tab shows pending order

DO NOT recapture screens 1–3 for Branch B.
```

**Multi-exchange parity:** When capturing the same flow across competitors, aim for the same number of screens (±2). If Binance takes 6 screens and OKX takes 12 for the same flow, either:
- OKX genuinely has more steps (document why — e.g., extra KYC gate, risk quiz)
- You captured redundant screens for OKX. Review and prune.

### 4.3 Per-Screen Annotation

Every screenshot MUST have three fields. A screenshot without annotation is just a picture — it has no analytical value.

| Field | What to write | Anti-pattern (don't do this) |
|---|---|---|
| **Screen name** | A descriptive noun phrase that identifies this screen uniquely within the flow | "Screenshot 1", "Screen", "Page" — too vague |
| **Trigger** | The exact user action that led to this screen appearing | "User navigated here" — too vague. Say HOW. |
| **Observation** | ONE sentence stating what business logic, product decision, or design pattern this screen reveals. This is the analytical value. | "This is the order form" — that's a description, not an observation. |

**Good annotation examples:**

```
Screen:      Order Type Selector
Trigger:     Tap "Limit" tab on spot order form
Observation: OKX shows Market/Limit/Stop-Limit/TWAP — 4 order types vs Coinbase's 2 (Market/Limit).
             More options = targeting sophisticated traders.

Screen:      Insufficient Balance Prompt
Trigger:     Tap "Buy BTC" with 0 USDT balance
Observation: Binance shows a bottom sheet with 3 deposit options (bank, card, P2P) inline.
             OKX redirects to a separate deposit page. Binance's approach has fewer taps to resolution.

Screen:      Futures Risk Quiz
Trigger:     First attempt to open a futures position
Observation: OKX requires a 5-question quiz before enabling futures.
             Binance only shows a disclaimer checkbox. OKX is more conservative on compliance.
```

**Bad annotation examples (don't do this):**

```
WRONG — Screen: "Screen 3"                          → Not descriptive
WRONG — Trigger: "Tapped button"                     → Which button?
WRONG — Observation: "This shows the trading page"   → That's what it IS, not what it REVEALS
WRONG — Observation: "Nice UI design"                → Subjective, not analytical
```

---

## 5. Quality Gate — Post-Capture Review

After capturing a complete flow, run these 5 checks **in order**. Do not publish or use the screenshots until all checks pass.

### Check 1: Story Coherence

Lay out all screenshots in sequence. Read through them as if you've never seen this app.

- Can you understand what the user is trying to do?
- Can you follow each step without confusion?
- Is there a "jump" where you suddenly don't know how the user got to the next screen?

**If there's a gap:** you're missing a screen. Go back and capture it.

### Check 2: Dedup Pass

For EACH screenshot, answer: "What does this screen show that the previous one doesn't?"

- If you can answer in one sentence → keep it.
- If you struggle to articulate the difference → remove it.
- If two consecutive screens only differ by keyboard visibility, scroll position, or a minor input change → remove one.

### Check 3: Completeness

Check that you haven't missed any of these key states:

- [ ] Entry point — how the user gets to this flow
- [ ] The primary "happy path" action
- [ ] At least one decision fork (if the feature has options)
- [ ] Confirmation/review before commitment (if applicable)
- [ ] Success state
- [ ] At least one error/edge case from your brief

### Check 4: Cross-Competitor Parity

If you captured the same flow for multiple exchanges:

- Screen counts should be within ±2 of each other
- If one exchange has significantly more screens, verify it's because of genuine extra steps (document why), not because you over-captured
- Ensure entry conditions were the same across all exchanges

### Check 5: Technical Quality

Scan every screenshot for these issues:

| Issue | Action |
|---|---|
| Blank chart / empty canvas | Discard. Retake after page fully loads. |
| Visible spinner or loading indicator | Discard. Retake. |
| Skeleton / placeholder UI | Discard. Retake. |
| Broken image icons | Discard. Retake. |
| Screenshot longer than 2000px on any side | Resize to 1800px max before use. |
| Notification bar / system UI obscuring content | Retake with clean status bar, or crop. |
| Personal data visible (real email, phone, balance) | Redact or retake with test account. |

**Only after all 5 checks pass is the flow ready for analysis.**

---

## Appendix: Common Mistakes

| Mistake | Why it happens | How to avoid |
|---|---|---|
| 20 screenshots for a simple buy flow | No brief defined; capturing everything "just in case" | Write a brief first. Target 5–10 screens. |
| Half-loaded trading page with blank chart | Captured too early; didn't wait for WebSocket data | Follow §3.1 readiness checklist. Every element loaded before capture. |
| "Dimension limit exceeded" error during analysis | iOS @3x or web @2x screenshots are 2000px+ | Follow §3.2. Capture at 1x. Resize if needed. |
| Can't compare exchanges — different number of screens, different account states | No standardized brief | Same brief for all exchanges. Same entry conditions. |
| Screenshots have no annotations | Rushed through capture; planned to "annotate later" | Annotate immediately. If you can't write an observation, the screen probably isn't worth keeping. |
| Same sub-flow captured in 3 different features | Didn't check for overlap | Before a new capture session, review existing flows. Reference shared sub-flows, don't re-capture. |
