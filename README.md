# FactChecker — Skill

A skill that verifies a claim using evaluation methods inspired by lawyers, professional analysts, renowned scientists, and journalists. Behind the scenes, it searches for sources, actively tries to disprove the claim, compares competing evidence, and weighs the authority of each source.

## How to Use

Inside your Claude system:

```text
/factchecker Processed red meat increases the risk of colorectal cancer
```

### Default Output

```text
🔎 "Processed meat increases the risk of colorectal cancer"
📊 VALID ✅  ·  🎯 Confidence: High 🟢
Health agencies classify processed meat as carcinogenic for colorectal cancer; the evidence is consistent and no authoritative refutation was found.
```

⬇ By adding `--sources`, you can also view the sources used and the expert analyses.

```text
/factchecker --sources Processed red meat increases the risk of cancer
```

## Installation

### Windows

```powershell
git clone https://github.com/HP-Ozy/factchecker.git "$env:USERPROFILE\.claude\skills\factchecker"
```

### macOS / Linux

```bash
git clone https://github.com/HP-Ozy/factchecker.git ~/.claude/skills/factchecker
```

Then restart Claude. Verify that the skill is active by running:

```text
/factchecker
```

## How Does the Skill Work?

A 4-stage pipeline — **find evidence → find counter-evidence → evaluate evidence quality → assign confidence**:

1. **Breaks down** the claim into verifiable facts (discarding opinions).
2. **Searches for supporting evidence** using WebSearch and **reads the actual pages** with WebFetch (not just snippets), prioritizing primary sources.
3. **Searches for counter-evidence** (a mandatory and separate step): it actively attempts to refute the claim and records opposing sources with the same level of rigor.
4. Classifies each source by **type** and **authority**, applying expert evaluation frameworks.
5. **Evaluates evidence quality** (Strong / Moderate / Weak) based on authority, independence, consistency, supporting evidence, and counter-evidence.
6. Produces a **verdict + confidence level** separately: the *direction* (true / false / partially true) and *how certain* the conclusion is (High / Medium / Low).

### What Counts as an Authoritative Source?

- **Institutional and global organizations:** UN, WHO, EU, national statistics agencies, central banks, IPCC, and similar bodies.
- **Peer-reviewed scientific sources:** Nature, Science, NEJM, Lancet, PubMed, and related journals.
- **Trusted private organizations:** Reuters, AP, AFP, BBC, ANSA, as well as fact-checking organizations such as Snopes, Pagella Politica, and Full Fact.
- **Excluded from verdicts:** anonymous blogs, unverified social media posts, and content without identifiable sources.

## Expert Kits That Strengthen FactChecker

Each expert kit produces a mini-assessment that contributes to the final verdict. This means verification is not limited to counting how many sources support a claim; it evaluates how well the claim withstands critical scrutiny according to anti-misinformation principles:

- Verify, don't validate: treat every claim as a hypothesis to falsify, not something to confirm.
- Never invent sources, links, or quotations.
- Read the actual content before citing it.
- Detect when multiple sources originate from the same underlying source (not independent confirmation).
- Explicitly state limitations such as paywalls, outdated data, or non-verifiable claims.

## License

MIT — see [LICENSE](LICENSE).

Use it, modify it, and share it freely.
