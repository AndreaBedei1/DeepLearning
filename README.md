🧠 Separation of CIFAR-10 Images
✍️ Andrea Bedei
🔍 Obiettivo del progetto

Allenare un modello in grado di riconoscere due categorie distinte a partire da una singola immagine composta, ottenuta facendo la media pixel a pixel di due immagini diverse del dataset CIFAR-10.
📦 Descrizione dei dati
    Il dataset CIFAR-10 contiene 10 classi:
    airplane, automobile, bird, cat, deer, dog, frog, horse, ship, truck.
    Ogni immagine composta è ottenuta sommando due immagini e dividendo per 2.
        La prima immagine (componente A) è scelta tra le prime 5 classi:
        airplane, automobile, bird, cat, deer → etichetta A ∈ {0, 1, 2, 3, 4}
        La seconda immagine (componente B) è scelta tra le ultime 5 classi:
        dog, frog, horse, ship, truck → etichetta B ∈ {0, 1, 2, 3, 4}` (rappresenta offset 5–9)
🎯 Compito del modello
Dato in input un'immagine composta X = (img_A + img_B) / 2, il modello deve:
    Predire due etichette distinte:
        y_pred_A ∈ {0, 1, 2, 3, 4} → classe della prima immagine (tra le prime 5)
        y_pred_B ∈ {0, 1, 2, 3, 4} → classe della seconda immagine (tra le ultime 5, mappate su 0–4)
📏 Valutazione
    Genera 10.000 immagini miste a partire dal test set di CIFAR-10.
    Per ogni immagine, calcola:
        acc_A: accuratezza sulla componente A (prima immagine)
        acc_B: accuratezza sulla componente B (seconda immagine)
        acc_total = (acc_A + acc_B) / 2
    Ripeti l’intera valutazione 10 volte, generando ogni volta nuove coppie casuali.
    Riporta media e deviazione standard delle accuratezze finali.
🛠️ Note tecniche
    L’output del modello può essere composto da due "testate" softmax (una per ciascuna previsione).
    È importante che il modello impari a disentangle (separare) visivamente le due componenti sovrapposte, basandosi su feature discriminanti delle due metà del dominio.
