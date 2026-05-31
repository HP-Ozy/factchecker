# FactChecker — Skill 
Una skill che verifica un'affermazione usando parametri di confronto e tacniche utilizzate da, Avvocati, Analisti professionisti, Scienziati rinomati, Giornalisti. Dietro le quinte cerca le fonti, prova a smentirle, le mette a confronto e ne pesa l'autorevolezza — ma a te, di default, **non rovescia addosso tutto**: ti dà solo il **bollino** e la **confidenza** dell'informazione.

**VALIDA ✅ · PARZIALMENTE VALIDA ⚠️ · NON VALIDA ❌ · NON VERIFICABILE ❔**

## Come si usa

Dentro il tuo sistema Claude:

```
/factchecker Le carni rosse lavorate aumentano il rischio di cancro del colon-retto 
```

### Cosa vedi di default 

```
🔎 "La carne lavorata aumenta il rischio di cancro del colon-retto"
📊 VALIDA ✅  ·  🎯 Confidenza: Alta 🟢
Le agenzie sanitarie classificano la carne lavorata come cancerogena per il colon-retto; prove concordi e nessuna smentita autorevole.

ℹ️ Per fonti e analisi degli esperti: rilancia il comando /factchecker con --fonti.
```
/factchecker --fonti Le carni rosse lavorate aumentano il rischio di cancro
```

```
🔎 AFFERMAZIONE VERIFICATA
"La carne lavorata aumenta il rischio di cancro del colon-retto"

📊 VERDETTO: VALIDA ✅
🎯 CONFIDENZA: Alta 🟢 — qualità evidenza: Forte

🧪 ANALISI ESPERTI
- ⚖️ Avvocato: nessuna prova contraria autorevole; regge al contraddittorio.
- 🔬 Scienziato: classificazione IARC Gruppo 1, evidenza epidemiologica solida.

📚 FONTI (3 autorevoli — 3 a favore / 0 contrarie)
 1. OMS/IARC — who.int — Pubblica istituzionale — Alta
 2. AIRC — airc.it — Privata autorevole — Alta
 3. Fondazione Veronesi — fondazioneveronesi.it — Privata autorevole — Alta/Media
```

## Installazione

La skill è una cartella con dentro `SKILL.md`. Per installarla:

**Windows**
```powershell
git clone https://github.com/HP-Ozy/factchecker.git "$env:USERPROFILE\.claude\skills\factchecker"
```

**macOS / Linux**
```bash
git clone https://github.com/HP-Ozy/factchecker.git ~/.claude/skills/factchecker
```

Poi riavvia Claude. Verifica che sia attiva con `/factchecker`.

## Come funziona la skill ? 

Pipeline in 4 momenti — **cerca fonti → cerca controprove → valuta la qualità delle evidenze → emette confidenza**:

1. **Scompone** l'affermazione isolando i fatti verificabili (scarta le opinioni).
2. **Cerca fonti a favore** con WebSearch e **legge le pagine reali** con WebFetch (non solo gli snippet), puntando alla fonte primaria.
3. **Cerca controprove** (fase obbligatoria e separata): prova attivamente a smentire, registrando le fonti contrarie con pari rigore.
4. Classifica ogni fonte per **tipo** e **autorevolezza** seguendo i metodi degli esperti e passa l'affermazione per i **kit esperti**.
5. **Valuta la qualità delle evidenze** (Forte/Media/Debole): autorevolezza, indipendenza, concordanza, forza delle prove e delle controprove.
6. Emette **verdetto + livello di confidenza** distinti: la *direzione* (vero/falso/parziale) e *quanto è sicura* (Alta 🟢 / Media 🟡 / Bassa 🔴).

> Tutto questo lavoro (fasi 1–5) viene **sempre** fatto per intero. Quello che cambia è solo *quanto* te ne mostra: di default vedi il bollino + confidenza; con `--fonti` vedi anche fonti e analisi degli esperti. La profondità dell'analisi non cambia mai — cambia solo la verbosità.

### Cosa conta come fonte autorevole
- **Pubbliche istituzionali/mondiali:** ONU, OMS, UE, ISTAT, banche centrali, IPCC…
- **Scientifiche peer-reviewed:** Nature, Science, NEJM, Lancet, PubMed…
- **Private autorevoli:** Reuters, AP, AFP, BBC, ANSA + fact-checker (Snopes, Pagella Politica, Full Fact…)
- **Escluse dal verdetto:** blog anonimi, social non verificati, contenuti senza fonte.

## Kit esperti che rafforzano la skill principale Factcheker

Oltre alla verifica delle fonti, ogni affermazione viene passata attraverso **lenti esperte**:

- ⚖️ **Avvocato** (`kits/lawyer.md`) — sempre attivo: onere della prova e ricerca attiva della smentita più forte.
- 📊 **Analista del dato** (`kits/data-analyst.md`) — rigore statistico, provenienza del dato, cherry-picking, correlazione ≠ causazione.
- 🔬 **Scienziato** (`kits/scientist.md`) — metodo, peer-review, riproducibilità, consenso scientifico.
- 📰 **Giornalista** (`kits/journalist.md`) — chi/quando/perché, incrocio di fonti indipendenti, conflitti d'interesse.

Ogni kit produce un mini-giudizio che confluisce nel verdetto, così la verifica non si limita a *quante* fonti confermano, ma *quanto regge* l'affermazione sotto esame critico.

## Principi anti-bufala
- Verifica, non asseconda: tratta l'affermazione come ipotesi da falsificare, non da confermare.
- Mai inventare fonti, link o citazioni.
- Legge il contenuto reale prima di citarlo.
- Segnala se le fonti derivano tutte dalla stessa origine (non sono conferme indipendenti).
- Dichiara apertamente i limiti (paywall, dati datati, affermazione non verificabile).

## Licenza

MIT — vedi [LICENSE](LICENSE). Usala, modificala e condividila liberamente.
