# Pre-Audit Notes – [2025-03-silo-finance] ([Code4rena])
[Silo Finance Architechture Diagram](https://claude.ai/public/artifacts/57b9ea13-bd6f-4760-b554-1e19cf109f02)

## 1. Contest Overview
- **Platform**: Code4rena.
- **Protocol Name**:  2025-03-silo-finance
- **Audit Period**:  March 24–31, 2025
- **Scope**: ~20 Solidity contracts, ~1,697 LOC   
- **Repo Link**: [GitHub repo](https://github.com/code-423n4/2025-03-silo-finance.git)  

---

## 2. Protocol Summary
*Silo Finance is a decentralized lending platform with enhanced risk management through market isolation*  
- It is a DeFi protocol  
- Core functionality : a decentralized lending platform where users can lend tokens to earn interest and borrow tokens using collateral.  
- Key assumptions?  

---

## 3. Threat Model & Audit Focus
- What are the **assets at risk**?  Assets at risk are the Funds that depositors deposit to earn interest.
- Attack ideas : Forked code, Rewards  
- Who are the potential attackers?  
  - Malicious users 
  - Rogue admin
  - External protocol integrations e.t.c  
---

## 4. Contracts Reviewed
*(List the contracts and their main responsibilities)*  
- `ContractA.sol` – manages deposits and withdrawals  
- `ContractB.sol` – issues rewards  
- `ContractC.sol` – handles governance  
- …  

---

## 5. Initial Observations
- Code smells / areas that look fragile.  
- Any suspicious TODOs or comments in the code.  
- Complexity hotspots (long functions, lots of external calls).  

---

## 6. Findings (Preliminary)
*(Write down issues you think might be vulnerabilities, even if minor or unconfirmed)*  

- **[H/M/L]** Finding Name  
  - Description:  
  - Function(s) affected:  
  - Why it could be a problem:  
  - Example scenario (if possible):  

*(Repeat for each potential issue)*  

---

## 7. Unanswered Questions
*(What you don’t fully understand yet — mark them so you can check later)*  
- How is `totalSupply` updated in XYZ contract?  
- Why is slippage tolerance handled off-chain instead of on-chain?  
- Are oracle prices trusted blindly?  

---

## 8. Next Steps
- Areas I want to dive deeper into before checking the official findings.  
- Specific functions/tests I plan to write.  

---

*End of pre-audit notes.*
