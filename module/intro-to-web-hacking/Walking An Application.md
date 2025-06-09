# Task 1 — Walking an Application
Nessuna risposta richiesta.
# Task 2 — Exploring The Website
Nessuna risposta richiesta.
# Task 3 — Viewing The Page Source
**What is the flag from the HTML comment?**<br>
La flag è `THM{HTML_COMMENTS_ARE_DANGEROUS}` e si trova alla pagina `/new-home-beta` menzionata nel commento leggibile dal codice sorgente della homepage: `<!-- This page is temporary while we work on the new homepage @ /new-home-beta -->`. <br>
<br>**What is the flag from the secret link?**<br>
La flag è `THM{NOT_A_SECRET_ANYMORE}` e si trova alla pagina `/secret-page` raggiungibile cliccando su "to" di "Our dedicated staff are ready to assist you with your IT problems." o attraverso il codice sorgente della homepage.<br>
<br>**What is the directory listing flag?**<br>
La flag è `THM{INVALID_DIRECTORY_PERMISSIONS}` e si trova alla pagina `/assets/flag.txt`. L'esistenza di questa directory si scopre attraverso i tag `<link>`, `<img>` e `<script>` che hanno come `src` CSS, immagini e JavaScript utilizzati nella homepage stessa.<br>
<br>**What is the framework flag?**<br>
La flag è `THM{KEEP_YOUR_SOFTWARE_UPDATED}`. Per trovarla è necessario visitare il sito del framework utilizzato (`https://static-labs.tryhackme.cloud/sites/thm-web-framework/`) e leggere il change log della versione 1.3. Secondo il change log, un processo di backup genera il file `/tmp.zip` scaricabile dai visitatori del sito; l'archivio contiene a sua volta `flag.txt`.
# Task 4 — Developer Tools - Inspector
**What is the flag behind the paywall?**<br>
La flag è `THM{NOT_SO_HIDDEN}` e si trova alla pagina `/news/article?id=3`. Diventa visibile una volta assegnato il valore di `none` alla proprietà `display` di `div.premium-customer-blocker` che causa la scomparsa del paywall.
# Task 5 — Developer Tools - Debugger
**What is the flag in the red box?**<br>
La flag è `THM{CATCH_ME_IF_YOU_CAN}`. Per trovarla è necessario impostare un breakpoint nello script `flash.min.js` alla riga 110, contenente `flash['remove']();`. Ricaricata la pagina, l'esecuzione dello script si ferma al breakpoint e questo permette di leggere la flag contenuta nel popup.
# Task 6 — Developer Tools - Network
**What is the flag shown on the contact-msg network request?**<br>
La flag è `THM{GOT_AJAX_FLAG}` e si trova nel campo `flag` dell'oggetto JSON `{"msg":"Message Received","flag":"THM{GOT_AJAX_FLAG}"}` che rappresenta la risposta del sito all'invio di un messaggio alla pagina `/contact`.
