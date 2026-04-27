

# Options Learning Log — 2026‑02‑07

> Context: This log captures a full learning journey around stocks, ETFs, options, liquidity, and IBKR execution mechanics. It preserves confusion, corrections, concrete examples, and risk lessons. This is not a summary; it is a thinking record.

---

## 1. Starting Point — Equity & ETF Foundations

### Index & ETF grounding
- **NASDAQ** in trading conversations almost always refers to **NASDAQ‑100**, not NASDAQ Composite.
- **QQQ** tracks NASDAQ‑100.
- Canadian equivalents:
  - XQQ / QQC → NASDAQ‑100 (CAD)
  - VFV → S&P 500 (CAD)
  - XIC / VCN → Canadian market (TSX)

Key realization:
> Indices are references; ETFs are execution vehicles. Understanding which index an ETF tracks matters more than the ticker itself.

---

## 2. Stocks vs Options — Structural Difference

### Stocks ("正股")
- Linear exposure
- No expiration
- Liquidity usually higher
- Risk = capital invested

### Options
- Non‑linear payoff
- Expiration matters
- Liquidity varies dramatically
- Risk depends on structure, not direction alone

Key realization:
> Options are not directional bets; they are **contracts with structure**.

---

## 3. Core Options Concepts (Clarified Sequentially)

### Call vs Put
- **Call**: right to buy → bullish exposure
- **Put**: right to sell → bearish exposure or protection

### Buy vs Sell
- **Buy** = pay premium, limited risk
- **Sell** = receive premium, obligation + tail risk

This produces four primitives:
- Buy Call
- Buy Put
- Sell Put
- Sell Call

---

## 4. Buy Call vs Sell Put — Same Direction, Different World

Initial confusion:
> "Buy Call and Sell Put are both bullish — so are they the same?"

Resolution:
- **Yes, both are bullish**
- **No, they are not equivalent trades**

### Buy Call
- Bet: price rises **fast enough**
- Enemies: time decay (theta), IV crush
- Max loss: premium
- Max gain: theoretically unlimited

### Sell Put
- Bet: price does **not fall below strike**
- Friend: time decay
- Risk: forced stock purchase during drawdowns
- Gain: capped at premium

Mental model:
- Buy Call = buying a lottery ticket
- Sell Put = selling insurance

---

## 5. Greeks That Actually Matter

### Delta
- Directional exposure
- How much option price changes per $1 move in stock

### Theta
- Time decay
- Hurts buyers, helps sellers

### IV (Implied Volatility)
- Market’s expectation of future movement
- High IV inflates premiums
- IV collapse can destroy option value even if direction is right

Key realization:
> You can lose money being right on direction if IV and liquidity move against you.

---

## 6. Liquidity — The Hidden Axis (Critical Lesson)

### Spread
- Spread = Ask − Bid
- Immediate, unavoidable cost

Rules learned:
- Stocks: spread ideally < 1%
- Options:
  - < 5% → good
  - 5–10% → risky
  - > 10% → dangerous
  - > 20% → untradable for non‑professionals

### Volume & Open Interest
- Volume = today’s activity
- Open Interest = existing positions

Red flags:
- Bid size = 1
- OI < 100
- Huge spread with no depth

Key realization:
> Liquidity determines whether theoretical value can be realized.

---

## 7. Daily Range — Misleading Without Context

Daily Range on an option =
- The **lowest and highest traded prices that day**

Critical clarification:
- It does NOT mean fair value
- In illiquid contracts, extremes are often accidents

Lesson:
> “It traded there once” ≠ “you can trade there now.”

---

## 8. Real Case Study — LITE Call Loss

### Setup
- Long‑dated call
- Appeared ITM near expiry
- Extremely poor liquidity

Observed:
- Wide spreads
- Minimal bid size
- Collapsing IV

Outcome:
- Bought near emotional/illiquid high
- Forced to sell near bid floor
- Large loss despite ITM narrative

Core mistake (not directional):
> Trading a structure that could not be exited.

---

## 9. Expiry Mechanics — The IBKR Reality Check

### ITM at expiry does NOT require a buyer
- ITM options have intrinsic value
- Exercise is mechanical, not market‑based

### But margin matters

If account **cannot support exercise**:
- IBKR intervenes
- Positions may be force‑closed
- Execution prioritizes risk removal, not price

Key rule learned:
> Never hold ITM options into expiry unless you can carry the resulting stock position.

---

## 10. Sell Put — Proper Mental Framing

Correct interpretation:
> Selling a put means believing the stock will NOT fall below strike by expiry — and being willing to buy it if wrong.

Breakeven logic:
- Strike − Premium received

Non‑negotiable rule:
> If you do not want to own 100 shares at that price, you must not sell the put.

---

## 11. Execution Rules Internalized

### Before any option trade
- Check spread
- Check volume
- Check open interest
- Check ability to exit
- Check margin impact at expiry

### Absolute prohibitions (current skill level)
- Illiquid single‑name options
- Crypto‑adjacent equities
- Wide‑spread contracts
- Naked calls
- Letting IBKR manage expiry for you

---

## 12. Cognitive Upgrade Summary

Progression observed:
1. Directional thinking (up/down)
2. Structure awareness (call vs put vs sell)
3. Liquidity awareness
4. Broker behavior awareness
5. Risk ownership

Key identity shift:
> From "Will it go up?" → "Can I exit safely under stress?"

---

## 13. Final Hard Rules (Personal)

- Liquidity first, thesis second
- If exit is unclear, entry is forbidden
- ITM ≠ profit
- Premium is not free money
- Never outsource risk decisions to the broker

---

## 14. Closing Note

This log exists to prevent future repetition of the same structural mistakes. Any future option strategy must be justifiable against the rules documented above.

---

## 15. Reusable Pre‑Trade & Pre‑Expiry Checklists

This section distills the lessons above into **mechanical checklists**. These are meant to be used *before clicking Buy/Sell* and *before expiry*, without reinterpretation.

### 15.1 Option Pre‑Trade Checklist (Must Pass All)

**Liquidity (non‑negotiable)**
- [ ] Bid–Ask spread ≤ 10% (≤ 5% preferred)
- [ ] Bid size ≥ 10 contracts
- [ ] Open Interest ≥ 200
- [ ] Today’s volume ≥ 100
- [ ] Underlying stock average daily volume ≥ 2M shares

**Structure & Risk**
- [ ] I understand whether I am buying or selling optionality
- [ ] Max loss is explicitly known *in dollars*
- [ ] I know which Greek hurts me the most (Theta or IV)
- [ ] This trade does not rely on a single liquidity print (no “accident price”)

**Broker & Execution**
- [ ] I can exit this position without relying on market miracles
- [ ] IBKR will not need to intervene for margin or expiry

If **any box is unchecked → trade is forbidden**.

---

### 15.2 Sell Put Specific Checklist

- [ ] I genuinely want to own 100 shares at the strike price
- [ ] I can financially support assignment (cash or margin)
- [ ] I am comfortable holding the stock through a drawdown
- [ ] I know my true breakeven (strike − premium)
- [ ] I have a plan for early close (e.g., 70–80% premium captured)

If assignment would cause panic → do not sell the put.

---

### 15.3 Buy Call / Buy Put Checklist

- [ ] There is a *reason* for urgency (catalyst, momentum, volatility expansion)
- [ ] Time decay profile is understood (short‑dated vs long‑dated)
- [ ] IV is not already pricing perfection
- [ ] Loss of 100% premium is emotionally acceptable

Buying options without a time thesis = slow guaranteed decay.

---

### 15.4 Pre‑Expiry Checklist (Critical for IBKR)

**At least 3 trading days before expiry:**
- [ ] Is the option ITM or likely to become ITM?
- [ ] If exercised/assigned, can I hold the resulting stock position?
- [ ] If not, have I already closed the position myself?

Rules:
- ITM + cannot carry stock → **close early, no exceptions**
- Never allow IBKR to decide the exit price for you

---

### 15.5 Absolute Red Flags (Auto‑Reject)

- [ ] Spread > 20%
- [ ] Single‑digit bid size
- [ ] OI < 50
- [ ] Small‑cap / crypto‑adjacent / news‑only names
- [ ] “It was higher earlier today” as justification

Encountering any red flag = walk away immediately.

---

### 15.6 Identity Reminder

> My edge is **survival + repeatability**, not hero trades.
>
> Any trade that cannot be exited cleanly is already a losing trade.