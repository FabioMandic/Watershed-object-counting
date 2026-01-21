# Watershed-object-counting

Cilj projekta je implementirati sustav računalnog vida koji može automatski segmentirati i prebrojati objekte na slici (npr. kovanice, stanice, zrna) koristeći **Watershed transformaciju** za razdvajanje objekata koji se dodiruju.

##  O Projektu

Watershed (algoritam vododjelnice) je klasičan algoritam za segmentaciju slike, posebno koristan kada se objekti na slici dodiruju ili preklapaju. Tretira sliku kao topografsku kartu gdje intenzitet piksela predstavlja nadmorsku visinu.

### Ključne funkcionalnosti:
* Učitavanje slike i pretvorba u sivu skalu (Grayscale).
* Binarizacija slike (Thresholding) i uklanjanje šuma.
* Izračun udaljenosti (Distance Transform) za pronalaženje središta objekata.
* Kreiranje markera za Watershed algoritam.
* Konačna segmentacija i ispis broja detektiranih objekata.

##  Tehnologije

Projekt je realiziran koristeći:
* **Jezik:** Python 3.x
* **Biblioteke:**
  * `OpenCV` (cv2) - za obradu slike
  * `NumPy` - za matrične operacije
  * `Matplotlib` - za vizualizaciju rezultata (opcionalno)

##  Algoritam (Pipeline)

Proces obrade slike sastoji se od sljedećih koraka:

1.  **Predobrada:** Primjena Gaussian Blura za smanjenje šuma.
2.  **Binarizacija:** Korištenje Otsu metode za automatsko određivanje praga.
3.  **Morfološke operacije:** "Opening" operacija (erozija pa dilatacija) za uklanjanje sitnog šuma.
4.  **Sure Background/Foreground:**
    * Dilatacija za pronalaženje sigurne pozadine.
    * Distance Transform za pronalaženje sigurnog prednjeg plana (središta objekata).
5.  **Marker Labelling:** Kreiranje markera za nepoznata područja (rubove).
6.  **Watershed:** Primjena algoritma koji "poplavljuje" područja i povlači granice.
7.  **Rezultat:** Iscrtavanje kontura i ispis broja objekata.
