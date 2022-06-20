# SatelitePhotosLabeler - Projekt na BMMSI/BIAI

### Przygotownaie

Najpierw należy pobrać dataset, na którym chcemy trenować lub który chcemy oznakować.<br/>
Mój dataset znajduje się [tutaj](https://drive.google.com/drive/folders/1Sxu7SRQqr6uXDnMY6ll3dIVd5tC7P3w0?usp=sharing). Ten dataset należy dać do głównego folderu obok folderów yolov5 i CurrentBest. <br/>

### Trenowanie

Aby trenować należy wejść do folderu yolov5 i uruchomić skrypt train.py w taki sposób: <br/>
`python train.py --img 1280 --batch XXX --epochs YYY --data .\coco.yaml --weights yolov5n6.pt`    
Gdzie pod XXX wpisujemy batch, a pod YYY ilość epok, jaką chcemy trenować. Wielkość batch zależy od wielkości obrazków i pojemności pamięci RAM/karty graficznej. <br/>
Informacje o datasecie są zawarte w pliku coco.yaml


### Wykrywanie

Aby wykryć coś na obrazkach używając wytrenowanego modelu należy wejść do folderu yolov5 i uruchomić skrypt detect.py w odpowiedni sposób. Ja to robiłem zawsze tak: <br/>
`python detect.py --img 2048 --data .\coco.yaml --weights [ŚCIEŻKA DO MODELU] --source ..\datasets\coco\images --conf-thres 0.5` <br/>
Te ustawienia oznaczają zdjęcia dla pewnści powyżej 50%. Bez `--conf-thres` domyślnie jest 25%. Jeśli chodzi o ścieżkę do modelu to znajduje się on w yolov5/runs/train/expXXX/weights/bext.pt, gdzie XXX to wybrany numer treningu. <br/>
Dodałem też swój najlepszy model, który znajduje się w folderze CurrentBest/weights/best.pt. Jest to wynik ~600 epok treningu.
