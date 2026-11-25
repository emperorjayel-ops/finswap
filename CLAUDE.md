# CLAUDE.md — FinSwap

Created by OPS' Broker

## Project

**FinSwap** — the crypto exchange and wallet app of OMNI-PRESENT SOLUTIONS, INC, built on the open-source Bitcoin code (Bitcoin Core) and the open-source Counterparty protocol on the Bitcoin blockchain. Owner: Honorable Jay Ladon Dickey Sr. EL.

Front domain: **finswap.token** (regular fallback: energysc.org — also the verified Google Play organization website; its DNS verification record must stay in place). Google Play package: `com.omnipresentsolutions.finswap`.

## Tech in this folder

- `index.html` — the entire app: one self-contained HTML file (HTML/CSS/JavaScript inline, no build step, no framework, no server). It is large (~33 MB) because media is embedded. Edit it directly and carefully.
- `README.md` — project note. Keep it accurate when behavior changes.

There is no backend. Anything that looks like an account or trade today is session-only in the browser unless this file says otherwise.

## Standing rules (apply to every change)

- **Cross-platform, no exceptions:** must work on the owner's Samsung Galaxy S9 (SM-G960U), iPhones (Safari/WebKit), all other phones, and laptops/desktops. Responsive at every width.
- **Adjust to the device:** runtime feature detection and progressive enhancement — WebGL2 → WebGL1 → CSS fallback; auto quality scaling; honor reduced-motion and low-power signals. Degrade gracefully; never hard-require a capability.
- **Lane separation:** FinSwap is the finance/exchange lane. No Excalibur train material in here. FinSwap has its own gold wallet mark.
- **One-picture rule:** visuals blend into one seamless picture — matched lighting, perspective, color, shadows. Logos merge into the design with no visible outlines or background-box edges.
- **Cross-app sidebar:** every app in this family (Excalibur Line, FinSwap, HIIYAH, Dominion Network, PMI God's Eye) carries a sidebar linking to all the others. Keep it intact and uniform.
- **Credit:** the line "Created by OPS' Broker" / "Shared by OPS' Broker" stays in the files. Do not remove it, do not add any other creator name.
- **Honesty:** never present a demo, session-only feature, or trade as live. In-app trading stays labeled demo until a real wallet integration is connected and verified.
- **Asset caution:** WEALTHTICKET and PERFECTCERTS are the owner's confirmed Counterparty assets. BRICSCOIN's owner address is a different address the owner says is also his but is **not verified** — do not present BRICSCOIN as the owner's coin in public material until ownership is proven by a signed message or a completed proof-of-ownership deposit from that wallet.

## ⭐ REAL PAYMENTS / REAL WALLETS — the top requirement

FinSwap's money movement must be **real transactions on the real Bitcoin blockchain**, not simulation.

Current state (verified 2026-11-25): the wallet **receive** QR is real — it is built from the owner's published Bitcoin address — and scan-to-send correctly hands signing to the user's own wallet. In-app **trading is labeled demo** and is session-only. Making trading real, on the same non-custodial pattern, is the job.

Required implementation:

1. Build on the open-source stack already named in the app: **Bitcoin Core + Counterparty**, operating on the Bitcoin blockchain, with ISO 20022-ready financial messaging where relevant.
2. Supported assets: **Bitcoin (BTC), XCP, PERFECTCERTS, WEALTHTICKET**, and **Alpine Gold-backed currencies** (and physical Goldbacks as the app already presents them).
3. **End users transact from their own real wallets.** Trades and sends are signed and broadcast by the user's wallet; FinSwap constructs the transaction/payment request and reads the chain for status. No in-app fake balances presented as real.
4. **Never hold, request, receive, store, or transmit a user's seed phrase or private key — server-side or anywhere else.** No custodial key storage, ever. A public address is all a flow may ask for.
5. Balances, confirmations, and trade status must be read from the real chain (Bitcoin Core / Counterparty node or public Counterparty API), never simulated.
6. Keep the "demo" label on any flow until that exact flow is connected and verified with a real (even tiny) transaction; remove the label only for verified-live flows.

## Working notes

- Test every change at phone width (Galaxy S9) and desktop width before calling it done, and check Safari/WebKit behavior for anything using newer APIs.
- Report only completed, verified results. An attempt is not a result.
