# Knightstour
Benchmarkowanie agentów AI w oparciu o stary kod PHP.

# Stan początkowy, ustalenia
- Skopiowałem [repozytorium](https://github.com/krzysztofkotwica/knightstour-old) do dwóch katalogów w tym samym systemie (Linux ZorinOS 18.1) na tej samej maszynie.
- Zaopatrzyłem się w pakiety Google AI Pro oraz Claude Invidual Pro.
- Zainstalowałem agentów [Gemini-CLI](https://geminicli.com) i [Claude Code](https://claude.com/product/claude-code) oraz zalogowałem się swoimi kontami.
- Ręcznie nie wykonywałem żadnych zmian w kodzie/dockerze.
- Czasem popracowałem trochę bardziej szczegółowo z agentem, jeśli widziałem problem.
- Kontrolowałem oba agenty równolegle, w tym samym czasie.
- Całą komunikację prowadziłem w języku polskim.

# Wywołane prompty
1. Twoim zadaniem jest przebudowanie aplikacji, żeby jak najszybciej rozwiązywała problem Knight's tour dla pola szachownicy 8x8. Do uruchomienia korzystaj z docker compose. Stwórz jak najwydajniejszy algorytm.
2. Podnieś wszytkie zależności (PHP, obraz docker, używane biblioteki) oraz usuń niepotrzebne narzędzia z docker compose.
3. Zmień aplikację, żeby domyślnie szukała rozwiązania dla tablicy 16x16.
4. Usuń niepotrzebny kod.
5. sprawdź configi i envy czy nie zawierają niepotrzebnych rzeczy 
6. Zoptymalizuj aplikację, php, opcache i obraz dockera żeby uzyskany wynik uruchomienia obliczeń aplikacji był jak najmniejszy.
7. (wywołanie komendy /code-review lub /review) Wprowadź poprawki otrzymane w code review i sprawdź, czy wszystko działa poprawnie.

# Wyniki działania zaimplementowanego algorytmu
- Wynik obliczeń  16x16: Claude 3779.982us vs Gemini 90.62us
- Wynik obliczeń 128x128: Claude 21152.24us vs Gemini 5242.64 us

# Wnioski
## Claude - [repozytorium](https://github.com/krzysztofkotwica/knightstour-claude): 
- Limit pro wystarczył na 1.5h intensywnego korzystania.
- Myślał dłużej od Gemini przy zapytaniach, code-review, wdrażaniu zmian.
- Kod lepiej udokumentowany, lepsza jakość README, nad którym sam działał bez przypominania.
- Zignorował wszelkie interfejsy i zrobił po swojemu, wstępnie oceniam że kod niższej jakości niż otrzymany od Gemini.
- Prawdopodobnie mógłbym zoptymalizować algorytm dalej, ale skończył mi się limit.
## Gemini - [repozytorium](https://github.com/krzysztofkotwica/knightstour-gemini): 
- Na koniec zostawił babola z uruchamianiem apki, było inaczej niż w README, ale uczciwie poprawił po wywołaniu.
- Kod dość chaotyczny na pierwszy rzut oka, nie wiem czemu wziął possibleMoves do CalculateGreedyCommand, a nie  wykorzystał modelu Knight.
- Zostawił interfejs algorytmu i nawet z niego skorzystał.
- Musiałem się przypominać z uzupełnianiem README.
- Subiektywnie oceniam, że kod wyższej jakości niż Claude.
