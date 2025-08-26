# 🛡️ Smart Contract Auditing Process

A step-by-step process to approach audits, inspired by professional workflows and adapted from the Cyfrin Updraft Smart Contract Security course.

---

## 1. 🔍 Reconnaissance (Understanding the Project)
- **Read the docs**: Whitepaper, README, contest details, or audit scope.
- **Identify key goals**: What does the protocol do? (DEX, lending, governance, NFT, etc.)
- **Understand trust assumptions**: Which roles have power (owner, admin, multisig)?
- **Map external dependencies**: Oracles, DeFi integrations, external calls.

---

## 2. 🗂️ Codebase Mapping
- Clone the repo & explore project structure.
- Note:
  - Contracts in `src/` or `contracts/`.
  - Interfaces & libraries.
  - Tests (if any).
- Draw a **high-level architecture diagram** (contracts → interactions).

---

## 3. 🏗️ Threat Modeling
- Ask: “What can go wrong?”
- Use STRIDE framework:
  - **S**poofing (identity theft / fake addresses)
  - **T**ampering (unauthorized modification)
  - **R**epudiation (no accountability / logs missing)
  - **I**nformation disclosure (leaks of sensitive info)
  - **D**enial of service
  - **E**levation of privilege (owner → super admin)
- Identify **assets** (funds, governance power, NFTs, etc.).
- Identify **attack surfaces** (external/public functions, external calls, modifiers, upgradeability).

---

## 4. 📜 Manual Review
- **Go line by line** in critical contracts.
- Focus on:
  - Access control
  - State variable changes
  - Math (overflows, precision loss)
  - External calls (reentrancy, ordering issues)
  - Upgradable patterns (storage collisions, delegatecall risks)
- Document suspicious code snippets.

---

## 5. ⚙️ Automated Analysis
- Run **static analyzers**:
  - [Slither](https://github.com/crytic/slither)
  - [Mythril](https://github.com/ConsenSys/mythril)
  - [Echidna](https://github.com/crytic/echidna) (fuzzing)
- Cross-check findings with manual notes.
- Be careful: Tools produce **false positives**.

---

## 6. 🧪 Testing & Proof of Concept
- Write **foundry/hardhat test cases** for suspected bugs.
- Reproduce:
  - Reentrancy attacks
  - Price oracle manipulation
  - Privilege escalation
- Confirm whether the issue is **real & exploitable**.

---

## 7. 📝 Reporting
- Use a consistent format:
  - **Title**: Short + descriptive
  - **Severity**: Critical / High / Medium / Low / Informational
  - **Description**: What the bug is
  - **Impact**: Why it matters
  - **Proof of Concept**: Test case / tx trace
  - **Recommendation**: Fix or mitigation
- Example:
  ```markdown
  ## Finding: Reentrancy in `withdraw()`
  - **Severity**: High
  - **Description**: `withdraw()` sends ETH before updating balances.
  - **Impact**: Attacker drains contract via reentrancy.
  - **PoC**: [Foundry test case link]
  - **Recommendation**: Use checks-effects-interactions pattern or reentrancy guard.
