# Results Summary — The Illusion of Password Complexity

Analysis of 595 passwords across complexity rule compliance and structural predictability.

---

## Main Finding

**63.7% of passwords satisfying all complexity rules are structurally predictable.**

| Group | Count | % |
|---|---|---|
| Total passwords analyzed | 595 | 100% |
| Passing all 4 complexity rules | 146 | 24.5% |
| Of those — structurally predictable | **93** | **63.7%** |
| Of those — genuinely unpredictable | 53 | 36.3% |

---

## The Entropy Paradox

Among the 146 rule-compliant passwords:

| Entropy label | Count | % | Reality |
|---|---|---|---|
| Strong | 113 | 77.4% | 63.7% are still predictable |
| Moderate | 33 | 22.6% | Mixed |
| Weak / Critical | 0 | 0% | — |

A password scoring *Strong* on entropy can simultaneously be structurally predictable.

---

## Rule Compliance Breakdown

| Rule | Count | % |
|---|---|---|
| Length ≥ 8 | 522 | 87.7% |
| Has uppercase | 488 | 82.0% |
| Has digit | 527 | 88.6% |
| Has symbol | 205 | 34.5% |
| **All 4 rules** | **146** | **24.5%** |

---

## Examples — Passes All Rules, Remains Predictable

| Password | Rules passed | Entropy | Predictability |
|---|---|---|---|
| `Princess2024!` | 4/4 | Strong | dict_based |
| `Password2024!` | 4/4 | Strong | dict_based |
| `Football2024!` | 4/4 | Strong | dict_based |
| `Superman2024!` | 4/4 | Strong | dict_based |
| `Welcome2024!` | 4/4 | Strong | dict_based |
| `Iloveyou2024!` | 4/4 | Strong | dict_based |
| `Letmein2024!` | 4/4 | Strong | dict_based |
| `Dragon2024!` | 4/4 | Strong | dict_based |

---

## Length vs Predictability

| Length threshold | Dict-based | Unpredictable |
|---|---|---|
| Length ≥ 10 | 101 (55.5%) | 80 (44.5%) |

**Conclusion:** length ≥ 10 does not reliably indicate resistance to rule-based attacks.

---

## Key Conclusion

> Complexity rules correctly identify genuinely strong passwords only **36.3%** of the time.  
> Entropy metrics score 77.4% of rule-compliant passwords as *Strong* —  
> yet 63.7% of those are structurally predictable.  
>  
> Complexity rules measure **form**, not **unpredictability**.
