# Software Ailixir
Questo software di annotazione, addestramento, inferenza e gestione AI è un servizio cloud privato di edge computing basato su un'architettura web; la sua struttura flessibile favorisce la futura espansione verso servizi SaaS su cloud pubblico. Il servizio cloud privato di edge computing garantisce che i dataset degli utenti rimangano al sicuro all'interno dell'azienda, senza alcun rischio di fuga di dati, mentre il cloud pubblico può offrire comode soluzioni SaaS. L'architettura complessiva del sistema bilancia perfettamente la flessibilità e la scalabilità futura.

Inoltre, poiché i servizi di annotazione delle immagini richiedono la gestione di enormi quantità di foto e dataset etichettati (in genere, per addestrare un'IA a riconoscere una singola classe di oggetti sono necessarie circa 3.000 foto e annotazioni da varie angolazioni, di giorno e di notte), questo software offre una funzione di annotazione semi-automatica per aumentare l'efficienza. Supporta anche il caricamento in blocco (batch upload) di dataset già annotati. Il sistema integra e supporta sistematicamente i set di comandi per YOLOv5, YOLOv7, YOLOv8, YOLOv11 e YOLOv11 segmentation: non è necessario alcun background di programmazione per eseguire complessi addestramenti di modelli AI, completare l'inferenza e gestire ogni modello ampiamente addestrato.

## 📽️ Dimostrazione Video
Per i video dimostrativi sul riconoscimento e i tutorial operativi, consulta il nostro canale ufficiale:
👉 [Canale YouTube Ailixir Huis Technology](https://www.youtube.com/@ailixirailixir)

![Dimostrazione Immagini](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo.jpg)

## 📞 Acquisti e Supporto Tecnico
Per acquistare licenze software o per supporto tecnico, si prega di contattare:
* **Email**: [aailixir@gmail.com](mailto:aailixir@gmail.com)
* **Contattaci**: [Sito Ufficiale Huis Technology](https://anno.ailixir.com.tw/#contact)

# Capitolo 1: Preparazione prima dell'uso
## Installazione del Software
Scarica il pacchetto di installazione del software Ailixir, fai doppio clic con il mouse ed esegui l'installazione del software AI Ailixir.

<img width="648" height="448" alt="image" src="https://github.com/aailixir/italian_manual/blob/main/images/install_it.jpg?raw=true" />

## Installazione di CUDA
### Passaggi per l'installazione su Windows
L'installazione di CUDA su Windows è relativamente intuitiva ed è completata principalmente tramite la procedura guidata grafica.

1. Aggiorna i driver della scheda grafica NVIDIA
Prima di installare CUDA, visita il sito ufficiale NVIDIA per scaricare e installare l'ultima versione dei driver per la tua scheda grafica. Se installi una versione precedente di CUDA, i driver più recenti sono generalmente retrocompatibili.

2. [Scarica CUDA Toolkit] (https://developer.nvidia.com/cuda-downloads)
Vai alla pagina ufficiale di download del NVIDIA CUDA Toolkit.
Seleziona le specifiche del tuo sistema operativo:

* Sistema Operativo: Windows
* Architettura: x86_64
* Versione: 10 o 11
* Tipo di Installer: exe (local)

Clicca per scaricare il file di installazione (il file di solito pesa alcuni GB).

3. Esegui il programma di installazione: Fai doppio clic sul file .exe scaricato per l'installazione. Si consiglia di scegliere l'installazione "Rapida (Express)", che installerà automaticamente tutti i componenti necessari e configurerà le variabili d'ambiente di Windows. Se disponi già di un driver più recente, il programma di installazione ti chiederà se sovrascriverlo; di solito, è meglio mantenere la versione più recente.

4. Verifica l'installazione: Al termine dell'installazione, premi Win + R, digita cmd per aprire il prompt dei comandi e inserisci il seguente comando:

```
nvidia-smi
```

![nvidia-smi](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_nvidia.jpg)

### Passaggi per l'installazione su Linux (Ubuntu)
1. Sui sistemi Linux, di solito si consiglia di utilizzare i comandi da terminale e di installare tramite file .deb o .run. 1. Installa il driver della scheda grafica NVIDIA: è necessario riavviare il sistema. Apri il terminale, aggiorna il repository dei pacchetti di sistema, quindi consenti al sistema di trovare e installare automaticamente i driver NVIDIA più adatti:

```
sudo apt update
sudo ubuntu-drivers autoinstall
sudo reboot
```

2. Scarica e installa CUDA Toolkit: Vai alla pagina di download ufficiale NVIDIA, seleziona Linux -> x86_64 -> Ubuntu -> la tua versione (es. 22.04 o 24.04) -> deb (local). I comandi del terminale corrispondenti verranno generati automaticamente in fondo alla pagina (di solito includono il download del file .pin, il download del file .deb, l'aggiunta della chiave e l'installazione di cuda-toolkit tramite apt). Copia ed esegui questi comandi nel terminale in sequenza.

3. Configura le variabili d'ambiente: Molto importante. Al termine dell'installazione, il sistema non conoscerà ancora il percorso di CUDA. È necessario aggiungerlo manualmente alle variabili d'ambiente. Usa un editor di testo per aprire il file ~/.bashrc e aggiungi le seguenti due righe in fondo (sostituisci cuda-12.x con la versione effettiva che hai installato):

```
export PATH=/usr/local/cuda-12.x/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-12.x/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```
4. Verifica e controlla lo stato:
Inserisci nvcc --version per confermare che il compilatore sia installato correttamente. Successivamente, puoi utilizzare l'interfaccia di gestione del sistema NVIDIA per visualizzare lo stato in tempo reale e l'utilizzo delle risorse della GPU.

## Requisiti dell'Host di Addestramento
* Sistema Operativo: Windows 10, Windows 11 <BR>
* Requisiti GPU: Serie RTX20, Serie RTX30, Serie RTX40, Serie RTX50 <BR>
* RAM: 4GB o superiore <BR>

## Caricamento dinamico dei modelli Agentic AI
Il sistema supporta il caricamento dinamico e l'addestramento dei seguenti modelli:

* YOLOv5 <BR>
* YOLOv7 <BR>
* YOLOv8 <BR>
* YOLOv11 <BR>
* YOLOv11-Seg (Segmentation) <BR>

# Capitolo 2: Per Iniziare
Dopo aver completato l'installazione e avviato il servizio, apri il browser e inserisci il seguente URL per accedere al sistema:

http://127.0.0.1:8080 oppure
http://localhost:8080 

Puoi accedere utilizzando il nome utente e la password predefiniti:

	Nome utente: demo@example.com
	Password: demo

Dopo aver inserito il nome utente e la password, clicca sul pulsante "Login".


<img width="1920" height="963" alt="image" src="https://github.com/user-attachments/assets/8a00ce62-53ad-40f2-a202-8ed6dc68ef31" />

## Panoramica dei Pacchetti di Configurazione dell'Ambiente
Dopo aver effettuato l'accesso, vai al menu a sinistra sotto "Addestramento Modello AI" e clicca sul pulsante "Panoramica Pacchetti". Il sistema rileverà automaticamente se CUDA e altri pacchetti necessari (come Git, PyTorch, PyYAML) sono stati installati con successo.

💡 Suggerimento: Questa funzione evita agli utenti il fastidio di configurare manualmente ambienti complessi. Se indica che non sono installati, puoi cliccare su "Diagnostica Pacchetti" per procedere con l'installazione dinamica.

![Installazione](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_install.jpg)

## Panoramica Pacchetti
Se l'installazione va a buon fine, cliccando sul pulsante "Panoramica Pacchetti" verranno mostrati i componenti essenziali come Git, PyTorch, PyYAML e il loro stato di installazione.

![Panoramica](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_pytorch.jpg)

## Diagnostica Pacchetti
Se l'installazione fallisce, puoi cliccare sul pulsante "Diagnostica Pacchetti" per avviare il processo di installazione.

![Diagnostica](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_step1.jpg)

# Capitolo 3: Introduzione ai Dataset AI
Un dataset AI di immagini è una raccolta di file fotografici, mentre il dataset annotato (file di testo txt) rappresenta il processo di istruzione dell'IA. L'immagine seguente mostra un dataset pre-etichettato. 

⚠️ I file di immagine supportano solo i formati jpg, jpeg, png, bmp.

## Schermata di Impostazione Dataset AI

<img width="1906" height="954" alt="image" src="https://github.com/user-attachments/assets/f056a99b-c7d4-47fe-889f-a70e509bcf72" />

## Impostazioni Dataset AI
Prima di tutto, clicca su "Impostazioni Dataset AI" nel menu di navigazione a sinistra per configurare "Gruppi" e "Dataset". Clicca su "Aggiungi gruppo" per gestire i gruppi.


## Aggiunta Gruppo Dataset
Inserisci un nome per creare il gruppo.

<img width="1920" height="479" alt="image" src="https://github.com/user-attachments/assets/840c638e-cf99-40a1-97f0-544963f23c1a" />

## Aggiunta Dataset
Dopo aver selezionato il gruppo appena creato, puoi cliccare sul pulsante "Aggiungi Dataset" all'interno del gruppo. Dopo averlo aggiunto, puoi iniziare a creare il dataset. I gruppi raccolgono dataset simili che condividono gli stessi tipi di oggetti (file names).
<BR>
<BR>
+ Nome dataset: Utilizzato per scopi di identificazione.
+ Nome gruppo: Il gruppo di appartenenza.
+ Percorso AI immagini: Il percorso in cui verranno salvate le foto e i file di annotazione.
+ ID Gruppo: Utilizzato per localizzare il dataset.
+ Dashboard HTML: Reportistica personalizzabile per l'utente.
  
<img width="1913" height="850" alt="image" src="https://github.com/user-attachments/assets/d2aa32b8-d0a0-4c01-8a08-5c937c63aa05" />

## Modifica Dataset
La modifica del dataset consente di cambiare i dettagli relativi al gruppo e al dataset. Il "Percorso locale" è la directory in cui sono archiviate le foto e le annotazioni.
<BR>
<BR>
<img width="1920" height="775" alt="image" src="https://github.com/user-attachments/assets/b17654e7-b431-4f23-a345-fdf20243221f" />

+ Percorso Dataset Host: Posizione del dataset sull'host di rete o locale.
+ Quantità: Etichettati: Proporzione tra le immagini totali e quelle etichettate.
+ Classi #: Il numero di righe nel file names corrisponde al numero di classi.
+ Equità: Questa funzione distribuisce il dataset di immagini e le annotazioni con un rapporto 7:2:1 nelle directory "train", "test" e "val" (addestramento, test, valutazione). Questo è l'ultimo passaggio di verifica prima dell'addestramento.


<img width="1019" height="393" alt="image" src="https://github.com/user-attachments/assets/2d4ae185-56b0-448d-a519-faaf476235b1" />

## Eliminazione Dataset

Seleziona un gruppo o un dataset per procedere all'eliminazione.

<img width="588" height="48" alt="image" src="https://github.com/user-attachments/assets/e69d009f-5759-41ee-b228-4d21940ae0bc" />

## Spostamento Dataset
Seleziona un gruppo o un dataset per spostarne la posizione.
+ Completezza: Verifica i file di testo delle etichette (label), i file delle foto, il file delle classi (names), l'allocazione media del dataset. Un indicatore percentuale mostrerà i progressi. Procedere con l'addestramento del modello AI solo al raggiungimento del 100%.
+ Download: Impacchetta e scarica il dataset annotato corrente in formato zip.
+ Caricamento (Upload): Permette di caricare sull'host file di foto o archivi zip con dataset pre-annotati.


# Capitolo 4: Annotazione Dataset AI
Dopo che il gruppo e il dataset sono stati aggiunti, appariranno nel menu a sinistra. Cliccando sul dataset si visualizzeranno le relative foto.

<img width="1904" height="957" alt="image" src="https://github.com/user-attachments/assets/9011d6bb-91e3-4827-9cc5-3967f5e60bde" />

## Caricamento, Modifica ed Eliminazione Dataset
Una volta completata la creazione dei nomi del gruppo e del dataset, puoi cliccare sul gruppo a sinistra, selezionare il dataset desiderato e accedere alle impostazioni funzionali:

+ Carica foto (nomi): Puoi usare un editor di testo per modificare file con estensione names o labels, oppure caricare nuovi file di immagini sull'host.
+ Modifica foto: Basta un clic con il mouse per iniziare a modificare il BBOX (Bounding Box) del dataset di foto.
+ Elimina foto: Permette di eliminare sia le foto che i file di annotazione associati.
+ Quantità Dataset: Numero totale delle immagini.

## Annotazione Dataset
Questo software supporta sia l'annotazione Rettangolare (Rect) che l'annotazione Poligonale (Poly). Puoi passare dalla modalità rettangolo al poligono, ma non possono essere mescolate all'interno dello stesso dataset.
L'annotazione Rettangolare è il formato base per le annotazioni AI e il formato standard per YOLO. Clicca sull'area "Titolo dell'etichetta" per entrare in modalità modifica.

- Trascina l'intero oggetto: Clicca e trascina direttamente sul "Titolo dell'etichetta".
- Trascina gli ancoraggi: Trascina i punti di ancoraggio per adattarli alle dimensioni dell'oggetto.
- Trascina i bordi: Regola i confini dell'annotazione per adattarli all'oggetto.

<img width="1920" height="967" alt="image" src="https://github.com/user-attachments/assets/f86e97b9-7e06-430c-8cb0-26aee4256367" />

L'annotazione Poligonale, nota anche come segmentazione semantica (segmentation), è un formato avanzato per l'annotazione YOLO AI.

⚠️ Clicca sull'immagine qui sotto per riprodurre il video su YouTube.

[![Guarda il video](https://img.youtube.com/vi/Nrf-e5iCbkg/0.jpg)](https://www.youtube.com/watch?v=Nrf-e5iCbkg)

- Trascina l'intero oggetto: Clicca e trascina direttamente sul "Titolo dell'etichetta".
- Trascina gli ancoraggi: Trascina i punti di ancoraggio per adattarli alle forme complesse dell'oggetto.

<img width="1920" height="964" alt="image" src="https://github.com/user-attachments/assets/4a405bbe-71bd-463e-a478-54a724b04ba9" />

## Inizia l'Annotazione
Per etichettare una specie o oggetto, seleziona prima la categoria nell'"Elenco Etichette". Sulla foto, clicca e trascina il mouse per annotare l'oggetto. I file di annotazione verranno salvati automaticamente sull'host.

+ Elimina selezionati: Clicca sul "Titolo dell'etichetta" per entrare in modalità modifica, quindi premi il pulsante "Elimina selezionati" per rimuovere quell'oggetto.
+ Elimina tutto: Clicca sul pulsante "Elimina tutto" per rimuovere tutti gli oggetti annotati nell'immagine corrente.
+ Elimina tutti con ID: Quando vuoi eliminare un oggetto specifico basato sul suo ID in tutto il progetto, seleziona la categoria nell'"Elenco Etichette" e poi clicca su "Elimina tutti con ID". Questo eliminerà quella specifica classe da tutto il dataset.
+ Sostituisci tutti gli ID: Sostituisce l'ID di una classe di oggetti con un nuovo ID selezionato dall'"Elenco Etichette" su tutto il dataset.
  
<img width="1236" height="617" alt="image" src="https://github.com/user-attachments/assets/6c2bfe74-2cd5-4d44-89da-62d0b9af92d5" />

## Elenco Etichette (Label List)
L'elenco delle etichette si basa sui file YAML o YOLO names, e mappa il nome dell'oggetto con il suo ID numerico per definire il codice della specie.

+ YOLO names: Il contenuto può essere visualizzato in Impostazioni Dataset AI -> Dataset -> data.names.
+ YAML: Il contenuto può essere visualizzato in Impostazioni Dataset AI -> Dataset -> data.yaml.

<img width="1816" height="482" alt="image" src="https://github.com/user-attachments/assets/287da6fa-0b16-4868-aad3-8ed41b311aed" />

⚠️ L'Elenco Etichette supporta esclusivamente caratteri inglesi e alfanumerici.

# Capitolo 5: Addestramento del Modello
Dopo aver completato [L'installazione di CUDA](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_cuda_ok.jpg), puoi fare riferimento alla "Panoramica dei Pacchetti di Configurazione dell'Ambiente". Clicca sul pulsante "Panoramica Pacchetti" per assicurarti che tutti i componenti siano installati correttamente. L'immagine sottostante mostra un'installazione riuscita.

![Cuda OK](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_cuda_ok.jpg)

Successivamente, procedi con l'installazione del modello YOLO.

## Installazione del Modello YOLO
Vai al menu "Addestramento Modello AI", scegli il modello AI desiderato e clicca sul pulsante "Installa Motore" (Install Engine) per scaricare il motore del modello.

⚠️ Assicurati che il tuo host di annotazione sia connesso a Internet, altrimenti non potrai scaricare il motore del modello.

Segui i passaggi per completare l'installazione del motore YOLO per il futuro addestramento.

![Installazione YOLO](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_yolo_setup.jpg)

## Comandi di Addestramento
Se preferisci utilizzare la Command Line (Terminale), puoi cliccare sul pulsante "Comando di Addestramento" per copiare la sintassi necessaria.

## Addestramento del Modello
Per addestrare il tuo modello YOLO AI, clicca sul pulsante "Avvia Addestramento".

Ciclo Epoch: Rappresenta il ciclo di addestramento. In genere, si consiglia di selezionare inizialmente 25 o 50 Epoche per un addestramento rapido. Successivamente, si potrà eseguire un addestramento iterativo più lungo per migliorare il [F1 score](https://it.wikipedia.org/wiki/F1_score).

![Addestramento YOLO](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_yolo_training.jpg)

# Capitolo 6: Gestione delle Versioni del Modello
Dopo aver addestrato il tuo primo modello YOLO, il modello AI apparirà nel menu "Gestione Rilasci" (Model Version Management), dove potrai eseguire le seguenti azioni:

## Revisione del Rapporto del Modello
Il sistema genererà automaticamente un report di addestramento dettagliato, che include:

* Grafico della distribuzione delle annotazioni (Correlogrammi/Etichette) <BR>
* Risultati dei test di inferenza <BR>
* Curva del F1 Score <BR>
* Matrice di Confusione (Confusion Matrix) <BR>

![Report Modello 1](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_yolo_release1.jpg)

![Report Modello 2](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_yolo_release2.jpg)

## Riaddestramento del Modello
Se l'accuratezza del modello non è soddisfacente, puoi cliccare sul pulsante "Riprova Addestramento" (Retrain) per eseguire un addestramento iterativo.

![Riaddestramento](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_yolo_again.jpg)

## Pre-etichettatura Foto
Puoi caricare nuovamente un dataset di foto per la pre-etichettatura. Questa funzione permette di inserire immagini più varie per validare il modello AI. Affinché un modello YOLO AI sia accurato, necessita di annotazioni da molteplici angolazioni per favorire l'apprendimento delle diversità. Generalmente, 300 foto permettono il riconoscimento base, ma per ottenere alta precisione servono dalle 3.000 alle 30.000 immagini. Fornire un dataset vario, identificando i riconoscimenti errati e correggendo le annotazioni, incrementa significativamente la precisione del modello.

![Upload](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo_yolo_upload.jpg)

# Avviso sul Copyright
Questo sito web/programma è fornito da Apache HTTP Server e sviluppato utilizzando il linguaggio di programmazione PHP. <BR>
© 2026 Hus Technology Co., Ltd. Tutti i diritti riservati. <BR>
Questo codice e la relativa documentazione sono solo per scopi di studio e ricerca, e non possono essere copiati, distribuiti o utilizzati per scopi commerciali senza autorizzazione. In caso di citazione o modifica, si prega di mantenere le informazioni dell'autore originale e questo avviso sul copyright. <BR>
Apache HTTP Server è un progetto open-source di Apache Software Foundation. <BR>
PHP è un linguaggio di programmazione open-source sviluppato e mantenuto da The PHP Group. <BR>
Entrambi vengono utilizzati in conformità con i rispettivi termini di licenza (Apache License 2.0 e PHP License). <BR>
 
Questo progetto utilizza i suddetti software esclusivamente all'interno dell'ambito di autorizzazione legale, e non rappresenta alcuna affiliazione o partnership con Apache Software Foundation o The PHP Group. <BR>


