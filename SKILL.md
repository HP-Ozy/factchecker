---
name: factchecker
description: Fact-checker — prende un'informazione/affermazione e cerca su internet almeno 3 fonti autorevoli (pubbliche o private ma autorevoli) per verificarla. Cita chi l'ha detta o dove è stata trovata, il tipo di ciascuna fonte e il suo livello di autorevolezza, poi emette un verdetto VALIDA / NON VALIDA / PARZIALMENTE VALIDA in base alle fonti trovate. Trigger: "fact check", "verifica questa informazione", "è vero che", "trova le fonti", "/factchecker".
---

# FactChecker

Verifica un'affermazione cercando fonti autorevoli su internet e produce un verdetto motivato.

## Input

L'affermazione/informazione da verificare (`$ARGUMENTS`). Se manca, chiedi all'utente quale informazione verificare e da quale contesto proviene (chi l'ha detta, dove l'ha letta), poi procedi.

## Procedura

### 1. Scomponi l'affermazione
- Isola la/le **affermazione/i fattuale/i** verificabili (data, numero, evento, citazione, relazione causale).
- Nota chi la sostiene, se indicato (persona, testata, post, sito).
- Distingui FATTO da OPINIONE: si fact-checkano solo i fatti. Se è pura opinione, dillo e fermati.

### 2. Cerca su internet (≥3 fonti indipendenti)
Usa **WebSearch** per trovare candidati e **WebFetch** per leggere il contenuto reale prima di citarlo (non fidarti solo dello snippet). Obiettivi:
- Trova **almeno 3 fonti** che trattino l'affermazione.
- Punta a fonti **indipendenti tra loro** (non 3 ripubblicazioni della stessa agenzia).
- Varia gli angoli di ricerca: termini diretti, nome di chi l'ha detta, evento + data, eventuali smentite ("debunk", "smentita", "falso").
- Quando possibile risali alla **fonte primaria** (documento originale, comunicato ufficiale, studio, dato grezzo), non solo a chi la riporta.

### 3. Valuta l'autorevolezza di ogni fonte
Per ciascuna fonte classifica **tipo** e **autorevolezza**:

**Pubbliche autorevoli (mondiali/istituzionali):**
- Organismi internazionali: ONU, OMS/WHO, UE, Banca Mondiale, FMI, IPCC
- Enti statistici e istituzioni nazionali: ISTAT, Eurostat, governi, banche centrali
- Pubblicazioni scientifiche peer-reviewed: Nature, Science, NEJM, Lancet, PubMed/riviste indicizzate
- Università e centri di ricerca riconosciuti

**Private ma autorevoli:**
- Testate giornalistiche affermate con standard editoriali (Reuters, AP, AFP, BBC, ANSA, NYT, Financial Times...)
- Fact-checker riconosciuti (Snopes, PolitiFact, Pagella Politica, AFP Factuel, Full Fact)
- Aziende/laboratori leader nel proprio settore (per dati di dominio specifico)

**Basse / da trattare con cautela (non contano come autorevoli):**
- Blog anonimi, social media non verificati, forum, contenuti AI-generated senza fonte, siti con evidente bias o scopo promozionale.

Per ogni fonte registra: **nome/testata o autore**, **link**, **tipo** (pubblica/privata + categoria), **livello** (Alta/Media/Bassa), e una **citazione/estratto** che sostiene o smentisce l'affermazione.

### 4. Verdetto
Decidi in base alle fonti **autorevoli** trovate (le fonti basse non fanno verdetto):

- **VALIDA** ✅ — ≥3 fonti autorevoli indipendenti confermano concordemente.
- **PARZIALMENTE VALIDA** ⚠️ — confermata in parte, o con sfumature/condizioni, o le fonti autorevoli sono <3, o c'è qualche disaccordo.
- **NON VALIDA** ❌ — fonti autorevoli la smentiscono, oppure nessuna fonte autorevole la sostiene.
- **NON VERIFICABILE** ❔ — affermazione troppo vaga, sul futuro, o nessuna fonte affidabile trovata in nessuna direzione.

Regola chiave: la validità dipende dall'**aver trovato fonti pubbliche/private autorevoli** che la sostengano, non dal numero grezzo di link.

## Formato output

```
🔎 AFFERMAZIONE VERIFICATA
"<affermazione esatta>"
Sostenuta da: <chi l'ha detta / dove trovata, se noto>

📊 VERDETTO: <VALIDA ✅ | PARZIALMENTE VALIDA ⚠️ | NON VALIDA ❌ | NON VERIFICABILE ❔>
<1-2 frasi di motivazione>

📚 FONTI (<n> trovate, <m> autorevoli)

1. <Nome fonte / autore> — <link>
   Tipo: <Pubblica istituzionale | Pubblica scientifica | Privata testata | Fact-checker | ...>
   Autorevolezza: <Alta | Media | Bassa>
   Dice: "<citazione/estratto rilevante>"

2. ...
3. ...

🧭 NOTE
- <conflitti tra fonti, sfumature, mancanza di fonte primaria, cautele>
```

## Regole

- **Mai inventare fonti, link o citazioni.** Se non trovi 3 fonti autorevoli, dichiaralo apertamente e abbassa il verdetto — non riempire con fonti deboli spacciate per autorevoli.
- **Leggi prima di citare**: usa WebFetch sul link reale, non solo lo snippet di ricerca.
- **Segnala l'indipendenza**: se le 3 fonti derivano tutte dalla stessa origine, dillo (non sono 3 conferme reali).
- **Dichiara le date**: per fatti che cambiano nel tempo, indica a quando si riferisce la fonte.
- **Trasparenza sui limiti**: se una fonte è dietro paywall o non accessibile, segnalalo.
- Rispondi nella lingua dell'utente (default: italiano).
