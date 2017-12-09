[![Build Status](https://travis-ci.org/jboss-outreach/compressor-head.svg)](https://travis-ci.org/jboss-outreach/compressor-head)
[![Build Status](https://travis-ci.org/jboss-outreach/compressor-head.svg?branch=addtravis)](https://travis-ci.org/Hatollint/compressor-head)
![Codacy Badge](https://api.codacy.com/project/badge/Grade/9cd479ed37e649cb9e615b20410fb79f)
# Compressor-head
* [Przygotowanie komponentów](#setup)
* [Pomoc przy projekcie](#contr)
* [Użytkowanie](#usage)
* [Przykłady użytkowania](#usage_exm)
* [Autor](#author)
* [Odniesienia](#ref)
* [Licencja](#lic)

Jest to oparta na Pythonie aplikacja internetowa przechowywana przez Google App Engine. Używając tej aplikacji można kompresować/zmieniać rozmiar obrazów przed pobraniem ich. Tym samym zaoszczędza się dane, które musiałyby być pobrane. Dzięki uruchamianiu przez Google App Engine konwersja jest szybka. Ponadto wykorzystałem bibliotekę memcache, która przyspiesza proces, jeżeli ten sam obrazek jest pobierany przez wielu użytkowników

## <a id="setup"></a>Przygotowanie komponentów
* [Instalacja Google App Engine](#ins_gae)
* [Instalacja i uruchomienie Pythona](#ins_py)

### <a id="ins_gae"></a>Instalacja Google App Engine

Pierwszą i najważniejszą rzeczą jest zainstalowanie Google App Engine. Bez niego program nie zadziała!

Windows, Linux:
```bash
cd ~
mkdir comp_head_local
cd comp_head_local
wget https://storage.googleapis.com/appengine-sdks/featured/google_appengine_1.9.63.zip
unzip google_appengine_1.9.63.zip
export PATH=$PATH:/root/comp_head_local/google_appengine/
```

MacOS:
```bash
cd ~
mkdir comp_head_local
cd comp_head_local
curl -O https://storage.googleapis.com/appengine-sdks/featured/google_appengine_1.9.63.zip
unzip google_appengine_1.9.63.zip
export PATH=$PATH:/root/comp_head_local/google_appengine/
```

### <a id="ins_py"></a>Instalacja i uruchomienie pythona
Po zainstalowaniu GAE, zainstaluj również pythona.

Windows, Linux:
```
sudo apt-get -y install python2.7
```

MacOS:
```
sudo installer -pkg python2.7
```

Zainstaluj git (jeśli nie jest zainstalowany):
```bash
cd ~
sudo apt install git
```

I wróć do folderu comp_head_local
```bash
cd comp_head_local
```
Stamtąd możesz skopiować repozytorium na twój komputer i uruchomić stamtąd program.
```
git clone https://github.com/jboss-outreach/compressor-head
cd google_appengine
python dev_appserver.py ../compressor-head --port=45456 --host=0.0.0.0
```

## <a id="contr"></a>Pomoc przy projekcie
* [Przygotowanie projektu do poprawek](#fork)
* [Configuring Git](#git_conf)
* [Coding](#code)
* [Sending a pull request](#pull)
* [Amending your pull request](#pull_amend)
* [Cleaning up](#clean_up)

### Zawartość
Na początku należy założyć konto na GitHub'ie (jeżeli go nie posiadasz). Następnie powinieneś przeczytać zasady udziału w rozwoju dla wybranego projektu. Można je znaleźć w pliku CONTRIBUTING.md w repozytorium, jednakże to repozytorium go nie posiada.

Zwykle jest kilka sposobów, aby pomóc w rozwoju projektu. Głównym sposobem jest wysłanie wiadomości o błędach, czy ewentualnych poprawkach (Submit Issue) lub dodanie własnych poprawek na GitHubie za pomocą Pull Request. Możesz również pomóc przy tworzeniu dokumentacji, odpowiadać na pytania od innych deweloperów i wiele więcej.

### <a id="fork"></a>Przygotowanie projektu do poprawek

Idź na stronę projektu i naciśnij przycisk "Fork". Komenda ta utworzy kopię repozytorium tego projektu, w której będziesz mógł wprowadzać poprawki.
![fork](https://habrastorage.org/files/22d/147/828/22d147828b834ba3b3995df947d6cc3d.png)

Następnie musisz przenieść tę kopię na swojego GitHuba.
```bash
cd ~/work/git #Folder, w którym będzie kod.
git clone https://github.com/jboss-outreach/wiki-explorer.git #Kopia repozytorium
```


### <a id="git_conf"></a>Konfiguracja Git'u
Teraz musisz wprowadzić kilka zmian w twoim Git'cie, żeby przy wysyłaniu poprawek, twoja nazwa była poprawnie wyświetlana.
Wystarczy, że uruchomisz te komendy:

```bash
git config --global user.name "Twoje imię/pseudonim"
git config --global user.email you@example.com
```


### <a id="code"></a>Kodowanie

Żeby zacząć pracować nad twoją poprawką, musisz utworzyć odpowiadającą gałąź dla Git'a, opartą na obecnym kodzie z bazowego repozytorium.

Wybierz czytelną i adekwatną nazwę dla gałęzi, która odzwierciedli to, co zmieniłeś.
Uważa się za dobrą praktykę, aby umieścić ID problemu z GitHub'a w nazwie gałęzi.
```bash
git fetch upstream
git checkout -b <nazwa-twojej-gałęzi> upstream/master #exemple
```

Teraz możesz zacząć pracować nad swoim kodem.
Pamiętaj o przestrzeganiu pewnych zasad:
* Przestrzegaj standardów programowania (zwykle standardu PSR);
* Napisz test, aby udowodnić, że naprawiłeś błąd, lub że nowa funkcja działa poprawnie;
* Nie naruszaj kompatybilności wstecznej, jeśli nie ma takiej potrzeby;
* Używaj prostych i logicznych (translation needed)whole commits;
* Pisz czyste, czytelne i pełne poprawki.


### <a id="pull"></a>Wysyłanie pull request'u

While you were working on the code, other changes could be made to the main branch of the project. Therefore, before submitting your changes, you need to rebase your branch.
This is done like this:

W czasie kiedy pracowałeś nad swoim kodem, do głównej gałęzi projektu mogły zostać dodane różne poprawki. Musisz więc przebazować twoją gałąź zanim wyślesz poprawkę.
```bash
git checkout <nazwa-twojej-gałęzi>
git fetch upstream
git rebase upstream/master
```
#### Wysyłanie na Windowsie (przy minimalnym użyciu CMD):

Pobierz Google App Engine [stąd](https://storage.googleapis.com/appengine-sdks/featured/google_appengine_1.9.63.zip), jeśli go nie posiadasz.
Rozpakuj go i dodaj ścieżkę dostępu do PATH w zmiennych środowiskowych. Więcej na ten temat możesz przeczytać [tutaj].(http://www.itprotoday.com/management-mobility/how-can-i-add-new-folder-my-system-path)

Pobierz i zainstaluj Pythona, jeśli go nie posiadasz.

Skopiuj repozytorium i dodaj jako .zip. Więcej o tym możesz przeczytać [tutaj](https://www.google.co.in/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0ahUKEwiA5_-4__fXAhWKsY8KHVSuDGQQFggrMAA&url=https%3A%2F%2Fhelp.github.com%2Farticles%2Fcloning-a-repository%2F&usg=AOvVaw0J0cOUL5nBtjkmtQfsj0w-).

Z folderu Google App Engine otwórz CMD korzystając z ```Shift+Right click```. 
Użyj tego kodu:
```python dev_appserver.py "PATH_TO_ZIP" -port=45456 --host=0.0.0.0```
gdzie ```"PATH_TO_ZIP"``` jest ścieżką to skopiowanego/pobranego repozytorium.

Teraz możesz dodać swoje poprawki.
```bash
git push origin <nazwa-twojej-gałęzi>
```
Następnie idź do skopiowanego repozytorium projektu, w którego rozwoju pomagasz i naciśnij przycisk "New Pull Request".After that, we go to your project clone repository, in which you participate and click the button "New Pull Request".
Zobaczysz taki formularz:

![New Pull Request](https://habrastorage.org/files/191/d14/269/191d14269eae48e29d2179e32cf4fb2c.png)
Po lewej musisz wybrać gałąź, w której chcesz wprowadzić zmiany (najczęściej będzie to master).
Po prawej jest gałąź z twoimi zmianami.
Następnie zobaczysz wiadomość od GitHub'a odnośnie tego, czy jest możliwe aby automatycznie wprowadzić zmiany.
W większości przypadków zobaczysz "Able to merge".
Jeśli wystąpią konflikty, prawdopodobnie będziesz musiał zedytować poprawki.
Dalej naciśnij przycisk "Send Pull Request".
Przy wypełnianiu nazwy i opisu dla twojego Pull Request'a, dobrze jest podać numer problemu, dla którego tworzysz Pull Request.
Po stworzeniu Pull Request'a, zostaną uruchomione testy, może jakieś narzędzia itd. Wynik pracy GutHub'a zobaczysz w twoim Pull Requeście.

![results](https://habrastorage.org/files/46c/e42/a41/46ce42a41ef24141a5c74d76cdb71f13.png)

In case the tests are not passed or the build is not compiled, you will see a red error message and by clicking the Details link you will see what is wrong. In most cases, you will need to fix your Pull Request so that all checks are successful.

W przypadku, gdy testy nie powiodły się, albo kod się nie skompilował, zobaczysz czerwony komunikat o błędzie. Możesz wówczas kliknąć na link "Details" ze szczegółami co poszło nie tak. W większości przypadków, będziesz musiał poprawić swój Pull Request.


### <a id="pull_amend"></a>Poprawianie Pull Request'a

Jeśli wszystko jest dobrze z twoim Pull Requestem, wkrótce zostanie wprowadzony przez autora/współautora.
Jednakże, jest możliwe, że zostaniesz poproszony o poprawki.
W tym celu wróć do kroku 6 i po wprowadzeniu zmian uruchom następujące komendy:
```bash
git checkout <nazwa-twojej-gałęzi>
git fetch upstream
git rebase upstream/master
git push origin <nazwa-twojej-gałęzi>
```
### <a id="clean_up"></a>Czyszczenie

Po tym jak twoje poprawki zostały zaakceptowane lub odrzucone, musisz usunąć gałąź z twoimi zmianami. Żeby to zrobić uruchom następujący kod:
```bash
git checkout master
git branch -D <nazwa-twojej-gałęzi>
git push origin --delete <nazwa-twojej-gałęzi>
```
Zamiast ostatniej komendy, możesz również użyć:
```bash
git push origin :<your-name-branch>
```

## <a id="usage"></a>Użycie
*URL* - ```
http://compressor-head.appspot.com/image/?image_url=[IMAGE_URL]&width=[WIDTH]&height=[HEIGHT]&format=[FORMAT]```

Gdzie
```
*IMAGE_URL* jest adresem URL obrazka, który ma być skompresowany.
*WIDTH* to oczekiwana szerokość.
*HEIGHT* to oczekiwana wysokość.
*FORMAT* to oczekiwany format pliku (Wspierane formaty - JPEG, PNG and WEBP).
```
Both WIDTH and HEIGHT should be positive integers. Both WIDTH and HEIGHT cannot be zero. If one of the two is zero it will scale that non-zero dimention and the other dimention will be scaled such that the aspect ratio remains the same. If both are not zero, both dimentions will scale accordingly which might change the aspect ratio of the image.
Zarówno WIDTH jak i HEIGHT powinny być dodatnimi liczbami całkowitymi oraz nie mogą wynosić 0. Obydwa wymiary zostaną przeskalowane tak, że może to wpłynąć na format obrazu.
### <a id="usage_exm"></a>Przykłady użycia
URL przykładowego obrazka - http://compressor-head.appspot.com/image
To jest obrazek o rozmiarze i formacie `5.8 MB JPEG`. Wymiary: `5649×3684`
![](http://compressor-head.appspot.com/image)

Żeby przeskalować obrazek -
- Szerokość : `http://compressor-head.appspot.com/image/?image_url=http://compressor-head.appspot.com/image&width=500&height=0&format=jpeg`
![](http://compressor-head.appspot.com/image/?image_url=http://compressor-head.appspot.com/image&width=500&height=0&format=jpeg)
Zwróci to obrazek o rozmiarze i formacie: `37 KB JPEG` i wymiarach: `500x326`.

- Wysokość : `http://compressor-head.appspot.com/image/?image_url=http://compressor-head.appspot.com/image&width=0&height=250&format=png`
![](http://compressor-head.appspot.com/image/?image_url=http://compressor-head.appspot.com/image&width=0&height=250&format=png)
Zwróci to obrazek o rozmiarze i formacie: `164 KB PNG` i wymiarach: `383x250`.

- Resize (Width & Height) : `http://compressor-head.appspot.com/image/?image_url=http://compressor-head.appspot.com/image&width=500&height=350&format=jpeg`
![](http://compressor-head.appspot.com/image/?image_url=http://compressor-head.appspot.com/image&width=500&height=350&format=jpeg)
Zwróci to obrazek o rozmiarze i formacie: `41 KB JPEG` i wymiarach: `500x350`
Możesz również użyć formatu `WEBP`. Nie użyłem go tu, ponieważ nie jest obsługiwany przez GitHub'a. Przykładowy obrazek WEBP do konwersji możesz znaleźć [tutaj](//compressor-head.appspot.com/image/?image_url=http://compressor-head.appspot.com/image&width=500&height=350&format=webp).

## <a id="author"></a>Autor
[@m-murad](https://github.com/m-murad)
Tłumaczenie: [@firdrich](https://github.com/firdrich)
## <a id="ref"></a>Odniesienia
[Google App Engine (Python): Images API](https://cloud.google.com/appengine/docs/standard/python/refdocs/google.appengine.api.images.html)
[Google App Engine (Python): Memcache API](https://cloud.google.com/appengine/docs/standard/python/refdocs/google.appengine.api.memcache.html)
[Google App Engine (Python): URL downloading API](https://cloud.google.com/appengine/docs/standard/python/refdocs/google.appengine.api.urlfetch.html)
[Vinay Sajip: logging](http://www.red-dove.com/python_logging.html)
[The Webapp2 Maintainers: webapp2](https://cloud.google.com/appengine/docs/standard/python/refdocs/google.appengine.api.images.html)
## <a id="lic"></a>Licencja
[Apache Wersja 2.0](http://compressor-head.appspot.com/license)
