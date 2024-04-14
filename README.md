Dane:
https://cernbox.cern.ch/s/<<<id>>>
 
Są to dwa obrazki 2D o pewnym kształcie. Należy opracować metodę ML wskazującą czy są między nimi różnice. Te różnice mogą być, ale nie muszą być.
import uproot
with uproot.open('file.root') as datafile:
data_df = datafile['R0Tree'].arrays(library='pd')

W pliku są cztery zmienne: x, y, id, sample
 
x, y wartości, po wyrysowaniu powstanie obrazek
 
id:  -1 to jeden obrazek, +1 to drugi obrazek
 
sample - liczba próbek (17) w każdej taka sama statystyka.
