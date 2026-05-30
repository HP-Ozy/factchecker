# 🔎 FactChecker — Skill per Claude Code

Una skill per [Claude Code](https://claude.com/claude-code) che verifica un'affermazione cercando su internet **almeno 3 fonti autorevoli** (pubbliche istituzionali o private ma autorevoli), cita **chi l'ha detta / dove è stata trovata** e il **tipo e livello di autorevolezza** di ogni fonte, e infine emette un verdetto:

**VALIDA ✅ · PARZIALMENTE VALIDA ⚠️ · NON VALIDA ❌ · NON VERIFICABILE ❔**

## Come si usa

Dentro Claude Code:

```
/factchecker Le carni rosse lavorate aumentano il rischio di cancro del colon-retto
```

Oppure in linguaggio naturale:
- `fact check: i pinguini vivono al Polo Nord`
- `verifica questa informazione: ...`
- `è vero che ...?`

### Esempio di output

```
🔎 AFFERMAZIONE: "La carne lavorata aumenta il rischio di cancro"
📊 VERDETTO: VALIDA ✅
📚 FONTI (3 autorevoli)
 1. OMS/IARC — who.int — Pubblica istituzionale — Alta
 2. AIRC — airc.it — Privata autorevole — Alta
 3. Fondazione Veronesi — fondazioneveronesi.it — Privata autorevole — Alta/Media
```

## Installazione

La skill è una cartella con dentro `SKILL.md`. Per installarla:

**Windows**
```powershell
git clone https://github.com/<tuo-utente>/factchecker.git "$env:USERPROFILE\.claude\skills\factchecker"
```

**macOS / Linux**
```bash
git clone https://github.com/<tuo-utente>/factchecker.git ~/.claude/skills/factchecker
```

Poi riavvia Claude Code. Verifica che sia attiva con `/factchecker`.

> In alternativa: scarica lo ZIP del repo e scompattalo nella cartella `~/.claude/skills/factchecker/`.

## Come funziona

1. **Scompone** l'affermazione isolando i fatti verificabili (scarta le opinioni).
2. **Cerca** con WebSearch e **legge le pagine reali** con WebFetch (non solo gli snippet).
3. Trova **≥3 fonti indipendenti**, classifica ognuna per **tipo** e **autorevolezza** (Alta/Media/Bassa).
4. **Verdetto** in base alle fonti autorevoli trovate — risalendo, quando possibile, alla fonte primaria.

### Cosa conta come fonte autorevole
- **Pubbliche istituzionali/mondiali:** ONU, OMS, UE, ISTAT, banche centrali, IPCC…
- **Scientifiche peer-reviewed:** Nature, Science, NEJM, Lancet, PubMed…
- **Private autorevoli:** Reuters, AP, AFP, BBC, ANSA + fact-checker (Snopes, Pagella Politica, Full Fact…)
- **Escluse dal verdetto:** blog anonimi, social non verificati, contenuti senza fonte.

## Principi anti-bufala

- Mai inventare fonti, link o citazioni.
- Legge il contenuto reale prima di citarlo.
- Segnala se le fonti derivano tutte dalla stessa origine (non sono conferme indipendenti).
- Dichiara apertamente i limiti (paywall, dati datati, affermazione non verificabile).

## Licenza

MIT — vedi [LICENSE](LICENSE). Usala, modificala e condividila liberamente.
