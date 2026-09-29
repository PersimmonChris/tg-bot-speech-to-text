# Rinomina tg-bot-speech-to-text

- [x] Identificare la cartella con codice e la voce Desktop inesistente.
- [x] Verificare modello API e codice effettivamente in produzione.
- [ ] Rimuovere il progetto Codex collegato al Desktop inesistente.
- [x] Rinominare la repository GitHub in tg-bot-speech-to-text.
- [x] Aggiornare nome e repository sorgente in Coolify.
- [x] Aggiornare il remote Git locale.
- [x] Rinominare la cartella Mac.
- [ ] Aggiornare percorso e nome del progetto Codex.
- [ ] Verificare deploy, stato del bot e collegamenti.
- [ ] Documentare il flusso locale → GitHub → Coolify e completare la checklist.

## Verifiche e passaggi rimanenti

Modelli letti dal container in esecuzione: `gemini-3.5-flash-lite`, fallback `gemini-3.1-flash-lite`. SHA256 di `bot.py` locale e produzione identico prima della rinomina.

Codex: controllo UI negato dallo strumento per motivi di sicurezza; nessun tool dedicato per rimuovere o modificare progetti. Resta da rimuovere la voce Desktop inesistente e aggiornare il progetto corrente al nuovo percorso/nome attraverso l'interfaccia. Le chat vanno conservate.

Il vecchio percorso Developer è ora un symlink temporaneo alla cartella rinominata, per mantenere funzionante questa chat finché il progetto Codex non viene aggiornato. Dopo l’aggiornamento, rimuovere solo il symlink.
