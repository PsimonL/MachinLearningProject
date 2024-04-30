# Opis:
Dane:
https://cernbox.cern.ch/rootjs/public/7YO5OWzWt1NLODU/toyForStudents_5.root?contextRouteName=files-public-link&contextRouteParams.driveAliasAndItem=public%2F7YO5OWzWt1NLODU&items-per-page=100
 
Są to dwa obrazki 2D o pewnym kształcie. Należy opracować metodę ML wskazującą czy są między nimi różnice. Te różnice mogą być, ale nie muszą być.
import uproot
with uproot.open('file.root') as datafile:
data_df = datafile['R0Tree'].arrays(library='pd')

W pliku są cztery zmienne: x, y, id, sample
 
x, y wartości, po wyrysowaniu powstanie obrazek
 
id:  -1 to jeden obrazek, +1 to drugi obrazek
 
sample - liczba próbek (17) w każdej taka sama statystyka.

# Wskazówka:
sample oznacza numer próbki. W każdej próbce statystyka danych jest taka sama, czyli po 200000 przypadków. Innymi słowy mają Panowie 17 zbiorów danych, czyli mogą Panowie przeprowadzić 17 testów (17 eksperymentów, 17 grup studentów ma inny zbiór danych). 
 
Dlatego wybierają Panowie jedną z próbek, na której budują i testują swój model, np. sample==1.
Tu otrzymają Panowie jakiś wynik - informację, czy dwa obrazki 2D (x,y) różną się od siebie, czy też nie (jeden obrazek 2D (x,y ) to id ==1, drugi obrazek 2D (x,y) to id==-1). 
 
Zbudowany i zoptymalizowany model na próbce z sample==1  (mrożą Panowie kod, nic nie zmieniają) stosują na pozostałych 16 próbkach, podmieniając tylko dane. Dlatego będą mieli Panowie łącznie 16 odpowiedzi.
 
To zadanie ma wysymulować sytuację rzeczywistą. Np. mają Panowie zdjęcia dwóch pacjenta z tomografu, Xray itp. Jedno zdjęcie 2D (x, y) pacjenta wzorowo zdrowego (id==1), drugie zdjęcie pacjenta wzorowo chorego (id==-1). To jest nasza próbka sample==1. Te dwa wzorowe zdjęcia służą Panom do zbudowania i zoptymalizowania modelu w celu rozpoznawania różnic między zdrowym i chorym pacjentem, np. zmian w płucach. 
 
Teraz przychodzi kolejny pacjent i przynosi ze sobą zdjęcie płuc wykonane rok wcześniej. Wykonujemy mu kolejne zdjęcie i sprawdzamy czy nastąpiły jakieś zmiany w płucach w ciągu roku. To jest pacjent oznaczony sample==2. Ale szukamy konkretnych zmian. Już mamy zbudowany model do rozpoznawania tych konkretnych zmian. Stosujemy nasz algorytm i mamy odpowiedź, czy u pacjenta wystąpiły zmiany, czy nie. Następnie przychodzi kolejnych 15 pacjentów (sample==3, sample==4 .....) i powtarzamy czynność.

Opis jak dobrać optymalnie liczbę klastrów mogą Panowie znaleźć np. pod linkiem: https://www.displayr.com/understanding-cluster-analysis-a-comprehensive-guide/#choosing-the-right-number-of-clusters

Na tym etapie nie chcę Panom sugerować jak szukać różnic przy użyciu klasteryzacji. Proszę pomyśleć, poszukać. Dajmy sobie tydzień. Jeżeli Panowie nie będą mieli żadnej idei jak to wykonać, to proszę napisać.