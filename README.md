# 🔎 FactChecker — Skill 
Una skill che verifica un'affermazione usando parametri di confronto e tacniche utilizzate da, Avvocati, Analisti professionisti, Scienziati rinomati, Giornalisti, e al termine del processo ti da **almeno 3 fonti autorevoli** (pubbliche istituzionali o private ma autorevoli), cita **chi l'ha detta / dove è stata trovata** e il **tipo e livello di autorevolezza della fonte** :
**VALIDA ✅ · PARZIALMENTE VALIDA ⚠️ · NON VALIDA ❌ · NON VERIFICABILE ❔**

## Come si usa

Dentro il tuo sistema Claude:

```
/factchecker Le carni rosse lavorate aumentano il rischio di cancro del colon-retto 
```

### Esempio di output

```
🔎 AFFERMAZIONE: "La carne lavorata aumenta il rischio di cancro"
📊 VERDETTO: VALIDA ✅
📚 FONTI (Verificate dal processo)
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

1. **Scompone** l'affermazione isolando i fatti verificabili (scarta le opinioni).
2. **Cerca** con WebSearch e **legge le pagine reali**.
3. Trova molteplici **fonti indipendenti**, classifica segendo le abitudini e i metodi degli esperti poi suddivide le fonti ognuna per **tipo** e **autorevolezza in base a quello che farebbero gli esperti**.
4. **Verdetto** in base alle fonti autorevoli trovate — risalendo, quando possibile, alla fonte primaria.

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
