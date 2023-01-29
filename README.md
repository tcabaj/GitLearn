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
$ git checkout -b [nazwa nowej ga³êzi]
```
* Nastêpnie krok piierwszy tylko push na storzonego brancha

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
Sklonuj istniej¹ce repozytorium z GitHub na lokaln¹ stacjê robocz¹:

 ```sh 
git clone git@github.com:##orgname##/##reponame##
```
Proszê pamiêtaj:

Nie rozwidlaj repozytorium na GitHub - klonuj repozytorium g³ówne bezpoœrednio.
### 2. Zainicjuj narzêdzia HubFlow
Narzêdzia HubFlow musz¹ zostaæ zainicjowane, zanim bêd¹ mog³y byæ u¿ywane:
 ```sh 
cd ##reponame##
git hf init
```
Proszê pamiêtaj:

Musisz to robiæ za ka¿dym razem, gdy klonujesz repozytorium.
### 3. Utwórz ga³¹Ÿ funkcji
Jeœli tworzysz now¹ ga³¹Ÿ funkcji, wykonaj nastêpuj¹ce czynnoœci:
 ```sh 
git hf feature start ##feature-name##
```
Jeœli zaczynasz pracowaæ nad istniej¹c¹ ga³êzi¹ funkcji, zrób to:
 ```sh 
git hf feature checkout ##feature-name##
```
Proszê pamiêtaj:

Wszystkie nowe prace (nowe funkcje, niezwi¹zane z sytuacjami awaryjnymi poprawki b³êdów) nale¿y wykonaæ w nowej ga³êzi funkcji.
Nadaj ga³êziom funkcji rozs¹dne nazwy. Jeœli pracujesz nad biletem, u¿yj numeru biletu jako nazwy oddzia³u funkcji (np. Bilet-1234).
Jeœli ga³¹Ÿ funkcji ju¿ istnieje w repozytorium g³ównym, to polecenie zakoñczy siê niepowodzeniem z b³êdem.
### 4. Opublikuj ga³¹Ÿ funkcji w serwisie GitHub
W miarê postêpów we wprowadzanych zmianach przenieœ ga³¹Ÿ funkcji z powrotem do GitHub:
 ```sh 
git hf push
```
### 5. B¹dŸ na bie¿¹co
Bêdziesz musia³ usuwaæ ukoñczone funkcje i poprawki od innych programistów i regularnie w³¹czaæ je do swojej ga³êzi funkcji. (Zalecana praktyczna zasada to raz dziennie, z samego rana).

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
### 6. Wspó³pracuj z innymi
Przenieœ swoj¹ ga³¹Ÿ funkcji z powrotem do GitHub, gdy chcesz udostêpniæ swoje zmiany wspó³pracownikom:
 ```sh 
git hf push
```
Wyci¹gnij zmiany kolegi z powrotem do lokalnego klona:
 ```sh 
git hf pull
```
### 7. Po³¹cz swoj¹ funkcjê z rozwijan¹ ga³êzi¹
 ```sh 
git hf push
```
Nastêpnie u¿yj witryny GitHub, aby utworzyæ ¿¹danie œci¹gniêcia do ## reponame ## / develop branch from ## reponame ## / feature / ## feature-name ##.

Poproœ wspó³pracownika o przejrzenie Twojego ¿¹dania œci¹gniêcia; nie akceptuj tego sam, chyba ¿e musisz. Po zaakceptowaniu ¿¹dania œci¹gniêcia zamknij funkcjê za pomoc¹ narzêdzi HubFlow:
 ```sh 
git hf feature finish
```
### 8. Tworzenie wersji
Gdy masz wystarczaj¹co du¿o ukoñczonych funkcji, utwórz ga³¹Ÿ wydania:
 ```sh 
git hf update
git hf release start ##version-number##
```
Ga³êzie wydania otrzymuj¹ numery wersji dla nazwy. Na przyk³ad:
 ```sh 
git hf release start 2.6.0
```
tworzy wydanie ga³êzi / 2.6.0 .

Po utworzeniu ga³êzi wydania pamiêtaj, aby zaktualizowaæ numer wersji w swoim kodzie (w pom.xml, Makefile, build.xml lub gdziekolwiek jest przechowywany).

Zbuduj kod, wdró¿ go w œrodowiskach testowych, znajdŸ b³êdy. Napraw b³êdy bezpoœrednio w ga³êzi wydania. Kontynuuj tworzenie, wdra¿anie, debugowanie i naprawianie, a¿ bêdziesz zadowolony, ¿e wersja jest gotowa.

Kiedy bêdziesz gotowy, aby oznaczyæ wydanie i scaliæ je z powrotem w g³ówne i rozwijaæ ga³êzie, wykonaj nastêpuj¹ce czynnoœci:
 ```sh 
git hf release finish ##version-number##
```
To zamyka ga³¹Ÿ wydania i tworzy tag o nazwie ## numer-wersji ## wzglêdem ga³êzi g³ównej .

### 9. Tworzenie poprawek
Poprawka (nie pokazana na diagramie u góry tej strony) to specjalny rodzaj wydania. W przeciwieñstwie do funkcji i wydañ (które s¹ rozga³êzione od dewelopera ), poprawki s¹ rozga³êzione od g³ównego . U¿ywaj poprawek, gdy chcesz wprowadziæ i wydaæ piln¹ zmianê w najnowszym wydanym kodzie i nie chcesz, aby zmiany, które s¹ obecnie opracowywane, zosta³y jeszcze wys³ane.

Aby utworzyæ now¹ poprawkê:
 ```sh 
git hf update
git hf hotfix start ##version-number##
```
Spowoduje to utworzenie nowej ga³êzi o nazwie poprawka / ## numer wersji ## , z najnowszej ga³êzi g³ównej .

Po utworzeniu ga³êzi poprawek pamiêtaj, aby zaktualizowaæ numer wersji w swoim kodzie (w pom.xml, Makefile, build.xml lub gdziekolwiek jest przechowywany).

Edytuj kod, zbuduj go, wdró¿ w œrodowiskach testowych, upewnij siê, ¿e poprawka dzia³a. Kontynuuj edycjê, budowanie, wdra¿anie, debugowanie i naprawianie, a¿ bêdziesz zadowolony, ¿e poprawka jest gotowa. Pamiêtaj, ¿e mo¿esz u¿yæ polecenia git merge, jeœli chcesz scaliæ zmiany z ga³êzi funkcji do poprawki, któr¹ przygotowujesz.

Kiedy bêdziesz gotowy, aby oznaczyæ poprawkê i scaliæ j¹ z powrotem w g³ówne i rozwijaæ ga³êzie, wykonaj nastêpuj¹ce czynnoœci:

git hf hotfix finish ##version-number##
Spowoduje to zamkniêcie ga³êzi poprawki i utworzenie znacznika o nazwie ## numer-wersji ## wzglêdem ga³êzi g³ównej .

Uwa¿aj na poprawki:

Mo¿esz u¿yæ git hf hotfix start ## numer-wersji ## ## starszy-tag ##, aby utworzyæ poprawkê ze starszego tagu. Jeœli jednak spojrzysz wstecz na oryginalny diagram Vincenta , zwróæ uwagê, jak zachodz¹ zmiany w porz¹dku czasowym . Po zakoñczeniu tego rodzaju poprawki zostanie ona ponownie w³¹czona do najnowszej ga³êzi g³ównej ; nie jest scalany zaraz po rozga³êzionym tagu. Mo¿e to powodowaæ problemy, takie jak b³¹d mastera z nieprawid³owym numerem wersji, który na razie bêdziesz musia³ znaleŸæ i naprawiæ rêcznie.
