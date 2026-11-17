# DVS Music: creare un IPA su Windows e installarlo sull’iPhone

Questo pacchetto è il progetto Expo/React Native con un workflow GitHub Actions per creare un IPA **non firmato**. Il workflow non è ancora stato provato su un runner GitHub, quindi potrebbe richiedere correzioni in caso di errore.

## Parte 1: creare l'IPA

1. Registrati o accedi su https://github.com/ e vai su https://github.com/new.
2. Crea un repository chiamato `DVS-Music`. Puoi impostarlo **privato** (le build GitHub Actions consumano la quota inclusa; controlla i limiti del tuo account). Non aggiungere README o .gitignore da GitHub.
3. Estrai questo ZIP sul PC e apri la cartella `DVS_Music_Compila_IPA_GitHub`.
4. Nel repository GitHub clicca **uploading an existing file** (oppure **Add file → Upload files**).
5. Trascina nella pagina **tutti i file e le cartelle all'interno** della cartella del progetto, inclusa la cartella **.github**. Assicurati che GitHub mostri `.github/workflows/crea-ipa.yml` nella struttura.
6. Conferma con **Commit changes**.
7. Vai nella scheda **Actions → Crea DVS Music IPA (senza firma) → Run workflow → Run workflow**.
8. Quando l'esecuzione risulta verde, aprila e scarica **DVS_Music_IPA_non_firmato** dalla sezione **Artifacts**.
9. Estrai il file ZIP scaricato da GitHub: al suo interno trovi `DVS_Music_unsigned.ipa`.

Se appare un errore rosso, leggi i log della fase fallita. La compilazione di Expo/React Native non è garantita finché non viene eseguita davvero su macOS; il sorgente potrebbe necessitare modifiche.

## Parte 2: installare su iPhone

1. Installa Sideloadly da https://sideloadly.io/ sul PC Windows. Leggi i requisiti Windows nella loro guida (iTunes e iCloud in versione desktop dal sito Apple).
2. Collega l'iPhone via USB e autorizza il computer dal telefono. Se richiesto abilita la **Modalità sviluppatore** in Impostazioni → Privacy e sicurezza.
3. Apri Sideloadly, seleziona `DVS_Music_unsigned.ipa`, scegli l'iPhone e autentica il tuo account Apple in Sideloadly.
4. Premi Start. Al termine autorizza l'app in Impostazioni, se richiesto da iOS.
5. Con account Apple gratuito il rinnovo della firma è normalmente necessario ogni 7 giorni.

### Avvertenze

- DVS Music non è stata ancora compilata né testata su iPhone: il workflow automatizza il tentativo di creazione dell'IPA, **non garantisce l'esito**.
- Audio a schermo spento previsto per i brani **Audius** disponibili. YouTube non viene riprodotto in background tramite le API ufficiali.
- Questo IPA non è firmato: non si installa direttamente dall'app File o da Safari, ma va firmato con Sideloadly o con altri strumenti compatibili.
- Questo processo richiede l'accesso al tuo repository GitHub e un computer Windows per l'installazione.

Fonti: https://docs.github.com/en/actions/how-tos/manage-workflow-runs/manually-run-a-workflow ; https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository ; https://sideloadly.io ; https://docs.expo.dev/.


## Aggiornare il progetto precedente alla versione 0.3

Se avevi già caricato la versione vecchia su GitHub, cancella o sostituisci tutti i file precedenti con quelli presenti in **questo** ZIP, comprese `App.tsx`, `queueLogic.ts`, `package.json`, `app.json` e `.github/workflows/crea-ipa.yml`, poi fai **Commit changes**. Evita di lasciare due copie dei file nelle sottocartelle.

Questa versione abilita Radio automatica e playlist native su **Audius**. Il file `.ipa` non è incluso, e le build GitHub e l'installazione su iPhone non sono ancora state testate.
