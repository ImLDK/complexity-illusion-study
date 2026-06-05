# The Illusion of Password Complexity

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)
![Dataset](https://img.shields.io/badge/Dataset-595%20passwords-orange)
![Type](https://img.shields.io/badge/Type-Simulation--Based%20Research-purple)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

> **Simulation-based computational study.**  
> No live systems, real cracking tools, or unauthorized access used at any point.

---

## The Question

Most websites enforce password complexity rules:

- Minimum 8 characters
- At least one uppercase letter
- At least one digit
- At least one symbol

A password like `Password1!` satisfies all four.  
Does that make it secure?

> *Do common password complexity requirements produce passwords that are  
> actually resistant to rule-based dictionary attacks?*

---

## Key Finding

**63.7% of passwords passing all four complexity rules are predictable.**

Of 146 passwords satisfying all complexity requirements:
- **93 (63.7%)** contain a recognizable dictionary base word — structurally vulnerable to rule-based attacks
- **53 (36.3%)** appear genuinely unpredictable

> Complexity rules correctly identify genuinely strong passwords only **36.3% of the time**.

---

## The Entropy Paradox

Of rule-compliant passwords:
- **77.4%** score *Strong* on standard entropy metrics
- **63.7%** are structurally predictable

A password can score *Strong* on entropy **and** be structurally predictable at the same time.  
`Password2024!` scores Strong. It also has `password` as its base word.

---

## Why This Matters

| Password | Passes rules | Has dict base | Entropy says | Reality |
|---|---|---|---|---|
| `password` | ✗ | ✓ | Weak | Weak — obvious |
| `Password1!` | ✓ | ✓ | Strong | **False secure** |
| `Welcome2024!` | ✓ | ✓ | Strong | **False secure** |
| `Iloveyou2024!` | ✓ | ✓ | Strong | **False secure** |
| `X7#kP2!zQ9` | ✓ | ✗ | Strong | Genuinely strong |

This is consistent with NIST SP 800-63B (2017), which moved away from mandatory complexity rules — partly because they encourage predictable substitution patterns.

---

## Repository Structure

```
complexity-illusion-study/
│
├── complexity_analysis.py      # Main analysis script
│
├── data/
│   └── passwords_large.csv     # 595-password dataset
│
├── results/
│   └── complexity_results.csv  # Auto-generated output
│
└── docs/
    └── paper.md                # Full research paper
```

---

## Quick Start

**Requirements:** Python 3.8+ (no external libraries needed)

```bash
git clone https://github.com/YOUR_USERNAME/complexity-illusion-study.git
cd complexity-illusion-study
python complexity_analysis.py --file data/passwords_large.csv
```

To use a real dataset (e.g. RockYou):
```bash
python complexity_analysis.py --file data/rockyou-top10k.txt
```

---

## Results Summary

### Rule compliance (595 passwords)

| Rule | Count | % |
|---|---|---|
| Length ≥ 8 | 522 | 87.7% |
| Has uppercase | 488 | 82.0% |
| Has digit | 527 | 88.6% |
| Has symbol | 205 | 34.5% |
| **Passes ALL 4 rules** | **146** | **24.5%** |

### Among rule-compliant passwords (146)

| | Count | % |
|---|---|---|
| Structurally predictable (dict base) | **93** | **63.7%** |
| Appears genuinely unpredictable | 53 | 36.3% |

### Entropy scores of rule-compliant passwords

| Entropy label | Count | % |
|---|---|---|
| Critical | 0 | 0.0% |
| Weak | 0 | 0.0% |
| Moderate | 33 | 22.6% |
| **Strong** | **113** | **77.4%** |

**77.4% score Strong on entropy — but 63.7% are predictable.**  
This is the core finding: entropy metrics and complexity rules together fail to detect predictable structure.

### Length ≥ 10 — unexpected finding

- 101 passwords with length ≥ 10 still have a dictionary base word (55.5%)
- Length alone does not reliably indicate resistance to rule-based attacks

---

## Methodology

### Complexity rules modeled

| Rule | Condition |
|---|---|
| Minimum length | ≥ 8 characters |
| Has uppercase | At least one A–Z |
| Has digit | At least one 0–9 |
| Has symbol | At least one non-alphanumeric |

### Predictability detection

A password is **dict-based** if, after reversing leet substitutions (`@→a`, `3→e`, `1→i`, `0→o`, `$→s`) and stripping digits/symbols from ends, the base string matches a word in a frequency dictionary.

This models the necessary structural condition for rule-based attack success — without claiming specific cracking times.

---

## Limitations

- Dictionary covers a subset of common words; production tools use millions
- Leet-reversal models common substitutions only
- Does not model PCFG or neural network attacks
- Structural detection is a proxy for vulnerability, not a direct measurement

---

## Related Work

Companion study: [password-strength-study](https://github.com/YOUR_USERNAME/password-strength-study) —  
entropy metrics vs brute-force resistance across password categories.

---

## References

- NIST SP 800-63B (2017). *Digital Identity Guidelines.*
- Weir, M. et al. (2009). Password cracking using probabilistic context-free grammars. *IEEE S&P.*
- Veras, R. et al. (2014). On the semantic patterns of passwords. *NDSS 2014.*
- Mazurek, M. et al. (2013). Measuring password guessability for an entire university. *CCS 2013.*
- Ur, B. et al. (2012). How does your password measure up? *USENIX Security 2012.*

---

## License

MIT — free to use for educational purposes.

---

*This study is intended as an educational and comparative computational model for security analysis.*
