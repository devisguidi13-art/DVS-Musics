# DVS Music 0.3 — Radio e riproduzione continua

Questa versione sostituisce la precedente. È un **progetto sorgente Expo/React Native**, non un IPA già compilato.

## Funzionalità implementate

- **Coda nativa `expo-audio`**: passaggio automatico al brano successivo tra le fonti audio già inserite in coda. Più affidabile del vecchio lettore JavaScript a brano singolo durante il blocco dello schermo.
- **Radio automatica**: prima che la coda termini, cerca fino a 16 brani ulteriori su Audius usando artista e genere; esclude i brani già presenti nella sessione. Disattivabile.
- **Modalità casuale**: mescola i brani successivi senza cambiare il brano corrente o quelli già ascoltati.
- **Ripetizione**: spenta / intera coda / singolo brano, gestita dalla playlist nativa.
- **Controlli**: riproduci/pausa, avanti, indietro, barra di avanzamento, pannello coda, aggiungi come prossimo, aggiungi in fondo tramite pressione prolungata.
- **Playlist personali e preferiti** salvati sul dispositivo; ricerca e classifiche Audius.
- **Audio a schermo spento** predisposto tramite `expo-audio` per i brani Audius. Controlli schermata di blocco abilitati.
- **YouTube**: pulsante per aprire ricerche video ufficiali, ma YouTube **non viene riprodotto in background** in DVS Music.

## Come avviare la compilazione per iPhone da Windows

Leggi `GUIDA_INSTALLAZIONE_WINDOWS.md`. In breve, carica il contenuto di questa cartella nel tuo repository GitHub (sostituendo il precedente), quindi avvia **Actions → Crea DVS Music IPA (senza firma) → Run workflow**. La build utilizza un Mac remoto e crea un IPA non firmato solo se tutti i passaggi riescono.

## Test

`npm run test:queue` controlla deduplicazione, ordine dei brani, shuffle e scelta delle raccomandazioni. Il progetto è stato verificato a livello di sintassi TypeScript/TSX e con i test della logica: **non è stato ancora compilato e provato su un iPhone reale**.

## Limiti rispetto a Lyra

È una ricostruzione indipendente di alcune funzioni del player, non una copia dell'app Lyra. Il catalogo non è identico: la ricerca e l'audio con schermo spento provengono da **Audius**. La Radio usa somiglianze per artista/genere, non lo stesso algoritmo proprietario di Lyra. In mancanza di connessione o tracce Audius disponibili, la riproduzione può fermarsi. I brani YouTube non possono essere usati come audio nascosto tramite le API ufficiali di YouTube.

Fonti tecniche:
- https://docs.expo.dev/versions/latest/sdk/audio/
- https://docs.audius.co/api/
- https://developers.google.com/youtube/terms/developer-policies
