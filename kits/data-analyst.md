# Kit — Analista del dato

Lente: rigore statistico e qualità della prova numerica. Domanda guida:
**"Il dato misura davvero ciò che l'affermazione sostiene?"**

## Controlli analitici
- **Provenienza**: chi ha raccolto il dato, con quale metodo, su quale popolazione/campione? Dato grezzo o rielaborato?
- **Numerosità e rappresentatività**: campione sufficiente? Auto-selezionato? Generalizzabile alla popolazione di cui si parla?
- **Definizioni**: la metrica citata coincide con ciò che si afferma? (es. "morti per X" vs "morti con X", "casi" vs "contagi").
- **Periodo e aggiornamento**: a quando si riferisce il dato? È ancora valido oggi?
- **Base e denominatore**: numeri assoluti vs tassi/percentuali. Una percentuale senza base è sospetta.

## Controlli controfattuali
- **Cherry-picking**: l'intervallo temporale o il sottoinsieme è scelto per favorire la tesi? Cosa mostra la serie completa?
- **Correlazione ≠ causazione**: c'è un confondente plausibile? Causalità inversa?
- **Significatività vs rilevanza**: differenza statisticamente significativa ma praticamente irrilevante (o viceversa)?
- **Test del contrario**: quali dati, se esistessero, smentirebbero l'affermazione? Sono stati cercati?

## Output del kit
1-3 righe: cosa il dato sostiene davvero, eventuali distorsioni metodologiche, e quanto la prova numerica è solida (Forte / Debole / Inconcludente).
