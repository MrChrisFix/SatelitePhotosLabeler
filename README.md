# SatelitePhotosLabeler - Projekt na BMMSI/BIAI

## Polski/Polish
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
Dodałem też swój najlepszy model, który znajduje się w folderze CurrentBest/weights/best.pt. Jest to wynik ~800 epok treningu.

## English

### Preparation
First, you need to download the dataset on which you want to train or which you want to get labeled.
My dataset is located [here](https://drive.google.com/drive/folders/1Sxu7SRQqr6uXDnMY6ll3dIVd5tC7P3w0?usp=sharing). This dataset should be put in the root folder next to yolov5 and CurrentBest.

### Training
To train, enter the yolov5 folder and run the train.py script in this way: <br/>
`python train.py --img 1280 --batch XXX --epochs YYY --data .\coco.yaml --weights yolov5n6.pt` <br/>
Under XXX we enter the batch and under YYY the number of epochs we want to train. The size of the batch depends on the size of the images and the capacity of the RAM/graphics card.
The dataset information is contained in the coco.yaml file

### Detection
To detect something in images using a trained model, go to the yolov5 folder and run the detect.py script in an appropriate manner. I've always done it like this: <br/>`python detect.py --img 2048 --data .\coco.yaml --weights [MODEL PATH] --source ..\datasets\coco\images --conf-thres 0.5` <br/>
These settings label pictures for confidence above 50%. Without --conf-thres the default is 25%. As for the path to the model, it can be found in yolov5/runs/train/expXXX/weights/bext.pt, where XXX is the selected training number.
I also added my best model which is in the folder CurrentBest/weights/best.pt. This is the result of ~800 training epochs.
