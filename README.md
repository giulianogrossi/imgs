#  Vademecum per studenti in tesi

Il presente sito contine le tesi sviluppate presso il laboratorio **phuselab**. Per ogni studente viene predisposta una cartella che ha nome  `Nome_Cognome` dello studente e collocata sotto una delle cartelle principali inerenti uno dei topic di studio, per es. `VHR/Nome_Cognome`

## Accesso ai server via SSH
Per usare i server `pascal.di.unimi.it` o `volta.di.unimi.it` del laboratorio _phuselab_ 
occorre un account con proprio `username` (in genere il cognome, definito a inizio tesi). 
L'autenticazione avviene tramite chiave SSH, una credenziale di accesso basata su crittografia sicura supportata dal protocollo SSH. 

Quindi:

- generare la coppia chiave pubblica-privata dal proprio pc personale utilizzando `ssh-keygen`
- inviare al docente per eemail la chiave pubblica come file allegato per avere la propria chiave accreditata sul server
- accedere a pascal: `ssh username@pascal.di.unimi.it`, oppure a volta: `ssh username@volta.di.unimi.it`
- la propria home avrà global path: `/home/studenti/<cognome>`
- cambiare subito la password temporanea definita per generare l'utente


## Installazione di Conda e Python su Jupyter Notebook
Per definire un ambiente di lavoro privato basato su python, installare mini-conda dalla propria login:
- seguire le istruzioni su https://docs.conda.io/en/latest/miniconda.html

Pe utilizzare in remoto (via browser) Python su Jupyter Notebook occorre procedere con l'installazione:
- seguire le istruzioni su https://jupyter.org/install


## Uso di Google Colab e Jupyter notebook
_Google Colab_ è una piattaforma che permette di eseguire codice direttamente sul cloud (macchina virtuale temporanea) 
 o in locale su server privato, come `pascal.di.unimi.it` o `volta.di.unimi.it`. Occorre avere un account Google con 
 accesso a Google Drive dove salvare i propri notebook. Di seguito i passi per programmare in Python sul server tramite i notebook gestiti in Colab.
 
- Collegare l'applicazione __Colaboratory__ dal _Google Workspace Marketplace_ (`Nuovo/altra applicazione/Colaboratory`)
- Aprire un nuovo notebook Colab da Drive (`Nuovo/altro/Google Colaboratory`) da browser _Chrome_, _Firefox_, _Safari_ 
- Dal pulsante _connetti_ scegliere _connetti a runtime locale_ e seguire le istruzioni _Create a local connection by following these instructions_ per installare patch locali che permettono a Colab l'accesso al server da remoto (dal prorpio PC)
  - in particolare da STEP 2 installare 
    - `pip install jupyter_http_over_ws`
    - `jupyter serverextension enable --py jupyter_http_over_ws`
- Lanciare dal terminate `tmux` per la gestione e il controllo di applicazioni da terminale (continua ad eseguire in background anche dopo logout) 
- Lanciare dal server il comando `jupyter notebook --NotebookApp.allow_origin='https://colab.research.google.com' --port=8888 --NotebookApp.port_retries=0`, che attiva il notebook su jupyther 
- Lanciare da terminale su PC locale il comando `ssh -N -f -L localhost:8888:localhost:8888 username@volta.di.unimi.it` che attiva il tunnelling verso server remoto
- __NB.__ la porta `8888` è assegnata di default e può essere usata da un solo utente per volta (come tutte le altre porte!)... scegliere quindi una porta > 9000 (a caso e senza che sia già in uso - caso quest'ultimo segnalato dal sistema)

## Compilazione della tesi in Latex
Per redigere la tesi scaricare i template latex contenuti nella cartella `util/Latex` e sincronizzare i sorgenti prodotti (per es. su [Overleaf](https://www.overleaf.com/)) con la cartella `tesi/`, da collocare sotto la propria cartella nominale `MAIN-TOPIC/Nome_Cognome/` sul sito.