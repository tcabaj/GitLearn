# GitLearn

## 1. Wrzucanie na gita

 ```sh 
$ git status
$ git add . / git add [nazwa pliku]
$ git commit -m ''
$ git push origin master
```

## 2. Branches

 ```sh 
$ git checkout -b [nazwa nowej ga��zi]
```
* Nast�pnie krok piierwszy tylko push na storzonego brancha

 ```sh 
$ git checkout master
$ git merge --no-ff [nazwa galezi]
$ git branch [nazwa galezi] -D
```

## 3. Logi

??

## 4. Git Flow

#1 INIT
https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow

```sh 
$ git flow init
```

#2  Creating a feature branch

Without the git-flow extensions:

```sh 
$ git checkout develop
$ git checkout -b feature_branch
```

Using the git-flow extensions:

```sh 
$ git flow feature start feature_branch
```

#3 Finishing a feature branch 

Without the git-flow extensions:

```sh 
$ git checkout develop
$ git merge feature_branch
```

Using the git-flow extensions:

```sh 
$ git flow feature finish feature_branch
```
#4 Summary #1 #2

 ```sh 
$ git flow init
$ git flow feature start feature_branch
$ ...
$ git add . / git add [nazwa pliku]
$ git commit -m ''
$ git push
$ ...
$ git flow feature finish feature_branch
```

#4 release without git flow
 ```sh 
$ commit in dev
$ checout release
$ merge --no-ff into release
$ checout maser
$ merge --no-ff into master
$ checout dev
$ merge release
$ merge master

```

## 5. GitHub - GitFlow
https://datasift.github.io/gitflow/GitFlowForGitHub.html
![HubFLow](https://datasift.github.io/gitflow/GitFlowWorkflowNoFork.png)

### 1. Klonowanie repozytorium
Sklonuj istniej�ce repozytorium z GitHub na lokaln� stacj� robocz�:

 ```sh 
git clone git@github.com:##orgname##/##reponame##
```
Prosz� pami�taj:

Nie rozwidlaj repozytorium na GitHub - klonuj repozytorium g��wne bezpo�rednio.
### 2. Zainicjuj narz�dzia HubFlow
Narz�dzia HubFlow musz� zosta� zainicjowane, zanim b�d� mog�y by� u�ywane:
 ```sh 
cd ##reponame##
git hf init
```
Prosz� pami�taj:

Musisz to robi� za ka�dym razem, gdy klonujesz repozytorium.
### 3. Utw�rz ga��� funkcji
Je�li tworzysz now� ga��� funkcji, wykonaj nast�puj�ce czynno�ci:
 ```sh 
git hf feature start ##feature-name##
```
Je�li zaczynasz pracowa� nad istniej�c� ga��zi� funkcji, zr�b to:
 ```sh 
git hf feature checkout ##feature-name##
```
Prosz� pami�taj:

Wszystkie nowe prace (nowe funkcje, niezwi�zane z sytuacjami awaryjnymi poprawki b��d�w) nale�y wykona� w nowej ga��zi funkcji.
Nadaj ga��ziom funkcji rozs�dne nazwy. Je�li pracujesz nad biletem, u�yj numeru biletu jako nazwy oddzia�u funkcji (np. Bilet-1234).
Je�li ga��� funkcji ju� istnieje w repozytorium g��wnym, to polecenie zako�czy si� niepowodzeniem z b��dem.
### 4. Opublikuj ga��� funkcji w serwisie GitHub
W miar� post�p�w we wprowadzanych zmianach przenie� ga��� funkcji z powrotem do GitHub:
 ```sh 
git hf push
```
### 5. B�d� na bie��co
B�dziesz musia� usuwa� uko�czone funkcje i poprawki od innych programist�w i regularnie w��cza� je do swojej ga��zi funkcji. (Zalecana praktyczna zasada to raz dziennie, z samego rana).

* if you're not on your feature branch
 ```sh 
git hf feature checkout ##feature-name##
```
* pull down master and develop branches
 ```sh 
git hf update
```
* merge develop into your feature branch
 ```sh 
git merge develop
```
### 6. Wsp�pracuj z innymi
Przenie� swoj� ga��� funkcji z powrotem do GitHub, gdy chcesz udost�pni� swoje zmiany wsp�pracownikom:
 ```sh 
git hf push
```
Wyci�gnij zmiany kolegi z powrotem do lokalnego klona:
 ```sh 
git hf pull
```
### 7. Po��cz swoj� funkcj� z rozwijan� ga��zi�
 ```sh 
git hf push
```
Nast�pnie u�yj witryny GitHub, aby utworzy� ��danie �ci�gni�cia do ## reponame ## / develop branch from ## reponame ## / feature / ## feature-name ##.

Popro� wsp�pracownika o przejrzenie Twojego ��dania �ci�gni�cia; nie akceptuj tego sam, chyba �e musisz. Po zaakceptowaniu ��dania �ci�gni�cia zamknij funkcj� za pomoc� narz�dzi HubFlow:
 ```sh 
git hf feature finish
```
### 8. Tworzenie wersji
Gdy masz wystarczaj�co du�o uko�czonych funkcji, utw�rz ga��� wydania:
 ```sh 
git hf update
git hf release start ##version-number##
```
Ga��zie wydania otrzymuj� numery wersji dla nazwy. Na przyk�ad:
 ```sh 
git hf release start 2.6.0
```
tworzy wydanie ga��zi / 2.6.0 .

Po utworzeniu ga��zi wydania pami�taj, aby zaktualizowa� numer wersji w swoim kodzie (w pom.xml, Makefile, build.xml lub gdziekolwiek jest przechowywany).

Zbuduj kod, wdr� go w �rodowiskach testowych, znajd� b��dy. Napraw b��dy bezpo�rednio w ga��zi wydania. Kontynuuj tworzenie, wdra�anie, debugowanie i naprawianie, a� b�dziesz zadowolony, �e wersja jest gotowa.

Kiedy b�dziesz gotowy, aby oznaczy� wydanie i scali� je z powrotem w g��wne i rozwija� ga��zie, wykonaj nast�puj�ce czynno�ci:
 ```sh 
git hf release finish ##version-number##
```
To zamyka ga��� wydania i tworzy tag o nazwie ## numer-wersji ## wzgl�dem ga��zi g��wnej .

### 9. Tworzenie poprawek
Poprawka (nie pokazana na diagramie u g�ry tej strony) to specjalny rodzaj wydania. W przeciwie�stwie do funkcji i wyda� (kt�re s� rozga��zione od dewelopera ), poprawki s� rozga��zione od g��wnego . U�ywaj poprawek, gdy chcesz wprowadzi� i wyda� piln� zmian� w najnowszym wydanym kodzie i nie chcesz, aby zmiany, kt�re s� obecnie opracowywane, zosta�y jeszcze wys�ane.

Aby utworzy� now� poprawk�:
 ```sh 
git hf update
git hf hotfix start ##version-number##
```
Spowoduje to utworzenie nowej ga��zi o nazwie poprawka / ## numer wersji ## , z najnowszej ga��zi g��wnej .

Po utworzeniu ga��zi poprawek pami�taj, aby zaktualizowa� numer wersji w swoim kodzie (w pom.xml, Makefile, build.xml lub gdziekolwiek jest przechowywany).

Edytuj kod, zbuduj go, wdr� w �rodowiskach testowych, upewnij si�, �e poprawka dzia�a. Kontynuuj edycj�, budowanie, wdra�anie, debugowanie i naprawianie, a� b�dziesz zadowolony, �e poprawka jest gotowa. Pami�taj, �e mo�esz u�y� polecenia git merge, je�li chcesz scali� zmiany z ga��zi funkcji do poprawki, kt�r� przygotowujesz.

Kiedy b�dziesz gotowy, aby oznaczy� poprawk� i scali� j� z powrotem w g��wne i rozwija� ga��zie, wykonaj nast�puj�ce czynno�ci:

git hf hotfix finish ##version-number##
Spowoduje to zamkni�cie ga��zi poprawki i utworzenie znacznika o nazwie ## numer-wersji ## wzgl�dem ga��zi g��wnej .

Uwa�aj na poprawki:

Mo�esz u�y� git hf hotfix start ## numer-wersji ## ## starszy-tag ##, aby utworzy� poprawk� ze starszego tagu. Je�li jednak spojrzysz wstecz na oryginalny diagram Vincenta , zwr�� uwag�, jak zachodz� zmiany w porz�dku czasowym . Po zako�czeniu tego rodzaju poprawki zostanie ona ponownie w��czona do najnowszej ga��zi g��wnej ; nie jest scalany zaraz po rozga��zionym tagu. Mo�e to powodowa� problemy, takie jak b��d mastera z nieprawid�owym numerem wersji, kt�ry na razie b�dziesz musia� znale�� i naprawi� r�cznie.
