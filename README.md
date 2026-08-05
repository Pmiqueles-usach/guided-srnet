# guided-srnet
Mitigation of Cover Source Mismatch in JPEG Steganalysis via Exif Side-Information: Empirical Evidence of SRNet Collapse and Guided-SRNet Validation
Pier Miqueles
Department of Computer Engineering
Universidad de Santiago de Chile
Santiago, Chile
pier.miqueles@gmail.com
The operational deployment of deep steganalysis
models in real-world forensic infrastructures faces a critical vul-
nerability: the Cover Source Mismatch (CSM) phenomenon. This
degradation occurs when the statistical signatures of the capture
sensor differ between the training and evaluation phases, neu-
tralizing the generalization capabilities of blind neural networks.
This paper presents a comprehensive empirical investigation
evaluating the Guided-SRNet architecture, a dual convolutional
model designed to exploit Exif thumbnails (remnants in the APP1
marker) as side-information. The methodological design was
structured through an automated 6-module pipeline, evaluating
an effective volume of 1,574 samples extracted from a real-world
environment (Dresden Image Database). Training was executed
on a CPU for 15 epochs (η = 0.001, 256 × 256 crops, 0.4
bpp payload), utilizing 1,134 samples from Sensor A (Canon
DIGITAL IXUS 70) for optimization, and 440 samples from
Sensor B (_Camera) for cross-validation. The results expose
the catastrophic collapse of the conventional blind network
(Standard SRNet Baseline), which, despite achieving 97.46%
training accuracy, plummeted to 52.42% in CSM validation
with an uncontrolled loss of 9.1037. In contrast, Guided-SRNet
demonstrated exceptional resilience, reaching a training accuracy
of 98.35% and sustaining a Cross-Sensor validation accuracy
of 98.68% (loss of 0.0325). This evidence confirms that lat-
eral metadata injection neutralizes overfitting to sensor noise,
providing a highly stable, scalable, and operationally superior
steganalytic detection framework compared to recent state-of-the-
art architectures based on Transformer and KAN approaches
# Access Script Path  
cd ./src
# Install dependencies
pip install -q exifread
# Run training with real-time output
## Organize by CSM Sensor
python 01_organize_csm.py
## Generate Stego  
python 02_generate_stego.py
## Thumbnail Generator
python 03_generate_thumbnails.py
# Run  check pairs
python 04_check_pairs.py
## Train Guided Srnet to obtain BACC%  
python 06_train_guided.py
## Train Baseline Srnet to obtain BACC%  
python 05_train_baseline.py
## run seed 
python 07_run_multiseed_experiments.py

########## Directory Definitions
checkpoints: Output folder containing the trained models best_baseline_srnet.pth - best_guided_srnet.pth and history.log showing  values obtained per epoch.
data: Datasets folder. The Dresden datasets must be downloaded from https://www.kaggle.com/datasets/micscodes/dresden-image-database (53.51GB), though it is possible to download just a few. They must be copied into the Raw_Images directory, not in subdirectories. You can run:
cd Raw_Images/
find . -mindepth 2 -type f \( -iname "*.jpg" -o -iname "*.jpeg" -o -iname "*.png" -o -iname "*.gif" -o -iname "*.webp" \) -exec mv -t . -- {} +
To leave all images in the root directory.
src: Contains Python Scripts 01 to 07 and dataset_loader.py - guided_model.py
######################
AI Declaration: AI was used to structure the paper in LaTeX, translate the text into technical English, and format the alignment matrix. Code debugging was AI-assisted.

# Acceder Ruta de Script  
cd ./src
#Instalar dependencias
pip install -q exifread
# Ejecutar el entrenamiento con salida en tiempo real
## Ordenar por Sensor CSM
python 01_organize_csm.py
## Generar Stego  
python 02_generate_stego.py
## Generador Thumbails
python 03_generate_thumbnails.py
# Ejecutar revisar pares imagen
python 04_check_pairs.py
## Entrenar Srnet Guiada  para obtener BACC% 
python 06_train_guided.py
## Entrenar Linea Base  Srnet para obtener BACC% 
python 05_train_baseline.py
## Ejecutar Semillas
python 07_run_multiseed_experiments.py

########## Directorios Definicion
checkpoints: Carpeta Output con entrenamiento best_baseline_srnet.pth - best_guided_srnet.pth y history.log salida de valores obtenidos  por epoca.
data: Carpeta datasets se debe cargar datasets Dresden desde la direccion https://www.kaggle.com/datasets/micscodes/dresden-image-database (53.51GB) pero es posible bajar algunos. Se debe copiar en el directorio Raw_Images no en subdirectorios, puede ejecutar
cd Raw_Images/
find . -mindepth 2 -type f \( -iname "*.jpg" -o -iname "*.jpeg" -o -iname "*.png" -o -iname "*.gif" -o -iname "*.webp" \) -exec mv -t . -- {} +
Para dejar todas las imagenes en la raiz.
src: Contiene Script Python 01 al 07 y dataset_loader.py - guided_model.py
######################
Declaración de IA: Se utilizó IA para estructurar el paper en LaTeX, traducir el texto al inglés técnico y formatear la matriz de alineación. La depuración de código fue asistida por IA.

$$$$$$$$ Para Conseguir Password de .Zip contactar: pier.miqueles@usach.cl sera enviado inmediatamente.
