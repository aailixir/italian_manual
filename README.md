# Software Ailixir
Questo software di annotazione, addestramento, inferenza e gestione AI è un servizio cloud privato di edge computing basato su un'architettura web; la sua struttura flessibile favorisce la futura espansione verso servizi SaaS su cloud pubblico. Il servizio cloud privato di edge computing garantisce che i dataset degli utenti rimangano al sicuro all'interno dell'azienda, senza alcun rischio di fuga di dati, mentre il cloud pubblico può offrire comode soluzioni SaaS. L'architettura complessiva del sistema bilancia perfettamente la flessibilità e la scalabilità futura.

Inoltre, poiché i servizi di annotazione delle immagini richiedono la gestione di enormi quantità di foto e dataset etichettati (in genere, per addestrare un'IA a riconoscere una singola classe di oggetti sono necessarie circa 3.000 foto e annotazioni da varie angolazioni, di giorno e di notte), questo software offre una funzione di annotazione semi-automatica per aumentare l'efficienza. Supporta anche il caricamento in blocco (batch upload) di dataset già annotati. Il sistema integra e supporta sistematicamente i set di comandi per YOLOv5, YOLOv7, YOLOv8, YOLOv11 e YOLOv11 segmentation: non è necessario alcun background di programmazione per eseguire complessi addestramenti di modelli AI, completare l'inferenza e gestire ogni modello ampiamente addestrato.

## 📽️ Dimostrazione Video
Per i video dimostrativi sul riconoscimento e i tutorial operativi, consulta il nostro canale ufficiale:
👉 [Canale YouTube Ailixir Hus Technology](https://www.youtube.com/@ailixirailixir)

![Dimostrazione Immagini](https://github.com/aailixir/chinese_usermanual/blob/main/images/demo.jpg)

## 📞 Acquisti e Supporto Tecnico
Per acquistare licenze software o per supporto tecnico, si prega di contattare:
* **Email**: [aailixir@gmail.com](mailto:aailixir@gmail.com)
* **Contattaci**: [Sito Ufficiale Hus Technology](https://anno.ailixir.com.tw/#contact)

# Capitolo 1: Preparazione prima dell'uso
## Installazione del Software
Scarica il pacchetto di installazione del software Ailixir, fai doppio clic con il mouse ed esegui l'installazione del software AI Ailixir.

<img width="648" height="448" alt="image" src="https://github.com/user-attachments/assets/55c3708e-7c4b-460a-89bc-019e4777143f" />

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
