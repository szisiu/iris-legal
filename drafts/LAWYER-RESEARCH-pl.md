> Tłumaczenie pliku LAWYER-RESEARCH.md. W razie różnic rozstrzyga wersja angielska.

# IRIS: materiał badawczy dla prawnika i księgowego

Dokument wewnętrzny. Nie publikować. Opracowany 2026-11-09 przez agenta AI na podstawie
przepisów, które agent zna, wcześniejszych badań projektu i wyszukiwań w sieci. Żaden prawnik
ani doradca podatkowy go nie sprawdził. To wstępny brief: przy każdym punkcie podano, czego
wymaga prawo (z dużym prawdopodobieństwem), jak pewny jest autor, bezpieczne ustawienie
domyślne, którego używają projekty dokumentów do czasu odpowiedzi specjalisty, oraz kto musi
je potwierdzić.

Pewność: **wysoka** = regułę odczytano ze źródła pierwotnego albo od dawna jest ustalona;
**średnia** = reguła jest znana, ale jej dopasowanie do IRIS to ocena; **niska** = przywołana
z pamięci albo wyłącznie ze źródeł wtórnych.

Fakty o przedsiębiorcy użyte w tym dokumencie: jednoosobowa działalność gospodarcza w Polsce,
czynny podatnik VAT, sprzedaż do przedsiębiorców i konsumentów, jedna usługa online płatna
kartą przez Stripe w cyklicznych okresach.

Pliki towarzyszące: `LAWYER-NOTES-v3.md` (pytania do każdego dokumentu, ze źródłami w kodzie)
oraz pola w nawiasach kwadratowych w każdym projekcie.

## Część 1. Pytania do prawnika

### 1.1 Dziesięć pytań z konspektu

| # | Pytanie | Co wynika z badań | Pewność | Ustawienie domyślne w projektach |
|---|---|---|---|---|
| 1 | Przedsiębiorcy jednoosobowi, dla których umowa nie ma charakteru zawodowego: wyłączyć ich, czy dać każdemu klientowi prawo odstąpienia od umowy? | Od 2021 r. przedsiębiorca jednoosobowy, który kupuje poza zakresem swojej działalności, ma prawo odstąpienia od umowy przysługujące konsumentowi oraz ochronę przed klauzulami niedozwolonymi (ustawa o prawach konsumenta art. 7aa; Kodeks cywilny art. 385^5). Sprzedawca nie może tego wyłączyć umową. IRIS sprzedaje też zwykłym konsumentom, więc reżim konsumencki i tak musi działać w pełni. | wysoka co do reguły | Każdy klient dostaje warunki na poziomie konsumenckim. Nie wymaga się oświadczenia o zawodowym charakterze umowy. |
| 2 | Klauzule o zmianie, cenie, odnowieniu, sądzie i limicie odpowiedzialności a lista klauzul niedozwolonych (Kodeks cywilny art. 385^1 do 385^3); jeden limit dla Regulaminu i umowy powierzenia przetwarzania | Ograniczenie odpowiedzialności za szkodę na osobie albo za szkodę wyrządzoną umyślnie jest nieważne. Jednostronna zmiana ceny lub warunków bez podania przyczyny i bez prawa wypowiedzenia to klauzula z listy szarej. Klauzula o sądzie właściwym nie wiąże konsumenta. Limit w umowie powierzenia przetwarzania nie może ograniczać roszczeń osoby, której dane dotyczą (RODO art. 82). | średnia | Zamknięta lista przyczyn zmiany, 30 dni powiadomienia, prawo wypowiedzenia umowy, brak klauzuli o sądzie właściwym dla konsumentów, wyłączenie limitu wobec konsumentów tam, gdzie prawo tego zakazuje. |
| 3 | Łańcuch zgód komentarz-wiadomość prywatna (DM): czy pierwsza wiadomość prywatna to odpowiedź w ramach usługi, czy informacja handlowa? Jakie musi być brzmienie według PKE art. 398? Linki ze śledzeniem według art. 399? | Art. 398 PKE wymaga uprzedniej zgody na marketing przez automatyczne systemy i urządzenia końcowe. Odpowiedź, o którą osoba poprosiła komentarzem ze słowem kluczowym, jest prawdopodobnie żądaną wiadomością w ramach usługi, ale tylko wtedy, gdy nie zawiera promocji wykraczającej poza żądany materiał. Pomiar kliknięć przez link przekierowujący z identyfikatorem mieści się w art. 399: wytyczne EROD 2/2023 (pkt 49 do 51) stanowią, że link śledzący wysłany e-mailem lub wiadomością to zapisanie informacji w urządzeniu i uzyskanie dostępu do nich. Zgoda marketingowa z art. 398 jej nie obejmuje. | średnia do niskiej | Pierwsza wiadomość prywatna zawiera tylko żądany materiał i zdanie o zgodzie. Marketing wymaga odrębnej drugiej zgody i potwierdzonego adresu. Linki nie zawierają identyfikatora odbiorcy, chyba że odbiorca wcześniej zgodził się na pomiar; pomiar kliknięć w produkcie trzeba sprawdzić pod tym kątem. |
| 4 | Informacja twórcy przy pierwszej wiadomości prywatnej i jak długo można przechowywać komentującego, który nigdy nie odpowiedział | RODO art. 14 ust. 3 lit. b: najpóźniej przy pierwszej komunikacji. Kod usuwa kontakt bez adresu po 90 dniach od ostatniej aktywności, chyba że zatrzymuje go tag lub lista. | wysoka co do art. 14; średnia co do 90 dni | Szablon `end-user-notice.html`; pole produktu na informację twórcy to zgłoszenie #44. |
| 5 | Usługa hostingowa czy platforma internetowa według DSA; co musi działać | IRIS przechowuje treści klientów i część z nich pokazuje publicznie na życzenie klienta (strony zapisu, obrazy). Rozpowszechnianie wśród ogółu jest drobną, pomocniczą funkcją usługi głównej, co wskazuje na „usługę hostingową”, a nie „platformę internetową” (art. 3 lit. i oraz motyw 13). Nawet jako platforma, mikroprzedsiębiorca lub małe przedsiębiorstwo jest wyłączone z sekcji o platformach (art. 19), z jednym wyjątkiem: art. 24 ust. 3, czyli obowiązku podania koordynatorowi lub Komisji na żądanie liczby aktywnych odbiorców. Obowiązki dla hostingu, które trzeba spełniać: art. 11, 12, 14, 16, 17, 18; art. 15 nie dotyczy mikroprzedsiębiorców ani małych przedsiębiorstw. Polska ustawa (Dz.U. 2026 poz. 1296) obowiązuje od 2026-11-06. | wysoka co do dat; średnia co do klasyfikacji | Traktowane jako hosting. `report.html` i `acceptable-use.html` opublikowano 2026-11-09. |
| 6 | Przepisy o zmianie dostawcy w akcie w sprawie danych (rozporządzenie (UE) 2023/2854, art. 23 do 31) | Obejmują „usługi przetwarzania danych”, co pasuje do SaaS. Stosuje się od 2025-09-12; opłaty za zmianę dostawcy muszą zniknąć do 2027-01-12. Obowiązki: warunki umowne o zmianie dostawcy, okres wypowiedzenia do 2 miesięcy, okres przejściowy 30 dni, eksport danych klienta. | średnia | Regulamin ma sekcję o zmianie dostawcy; plik eksportu w 24 godziny nie jest przedstawiany jako cała procedura. |
| 7 | Jaki adres publikuje przedsiębiorca jednoosobowy | UŚUDE art. 5 i ustawa o prawach konsumenta art. 12 wymagają nazwy, adresu miejsca prowadzenia działalności i adresu e-mail. Dla przedsiębiorcy jednoosobowego to adres wskazany do rejestru działalności, nawet jeśli to dom. Adres biura wirtualnego jest dopuszczalny tylko wtedy, gdy jest adresem wskazanym w rejestrze. | wysoka | Projekty zawierają adres z rejestru. Strony opublikowane 2026-11-09 nie zawierają danych identyfikacyjnych z decyzji właściciela; to otwarta luka. |
| 8 | Dyrektywa (UE) 2023/2673 o funkcji odstąpienia od umowy i przepisy o informowaniu o cenach | Dyrektywa wymaga funkcji „odstąp od umowy” online dla umów zawieranych na odległość, stosowanej od 2026-06-19. Nie potwierdzono, czy polska ustawa wdrażająca już obowiązuje (źródła z połowy 2026 r. są niezgodne). | niska co do stanu w Polsce | Zapewnić odstąpienie e-mailem i napisać o tym; zaplanować funkcję w produkcie (zob. Część 3). |
| 9 | Minimalny wiek | Instagram dopuszcza od 13 lat. Polski wiek zgody na usługi społeczeństwa informacyjnego to 16 lat (RODO art. 8 wraz z polską ustawą). Umowa z osobą poniżej 18 lat wymaga dla bezpieczeństwa zgody opiekuna. | wysoka co do wieku | Klienci muszą być pełnoletni. Informacja twórcy ma pole dotyczące małoletnich. IRIS nie sprawdza wieku. |
| 10 | Czy uchylenie rozdziału o hostingu w UŚUDE (od 2026-11-06) zmienia Regulamin? | Wyłączenie odpowiedzialności wynika teraz bezpośrednio z DSA art. 6. Odwołania do UŚUDE art. 14 trzeba usunąć. | średnia | Projekty powołują się tylko na DSA. |

### 1.2 Trzy pytania z 2026-11-08

| # | Pytanie | Co wynika z badań | Pewność | Ustawienie domyślne |
|---|---|---|---|---|
| 11 | Czy jedna linijka pod przyciskiem logowania wystarcza jako wyrażenie zgody na Regulamin, bez pola wyboru (#465)? | Warunki umowy wiążą, gdy klient mógł się z nimi zapoznać przed zawarciem umowy (Kodeks cywilny art. 384). Pole wyboru nie jest wymagane ustawą, ale jest zwykłym dowodem. Zgody na marketing lub na przetwarzanie danych nigdy nie można łączyć z tą linijką. Konsumentowi trzeba też przekazać warunki na trwałym nośniku (e-mail) po zawarciu umowy. | średnia | Jedna linijka, plus zapisany ślad zaakceptowanej wersji (#381), plus warunki e-mailem. |
| 12 | Czy baner cookies jest potrzebny, gdy wszystkie pliki cookie są ściśle niezbędne (#54)? | PKE art. 399 zwalnia z obowiązku zapisywanie informacji, które jest niezbędne do świadczenia usługi, o którą użytkownik poprosił. Informacja nadal jest wymagana, zgoda nie. | średnia do wysokiej | Bez banera; informacja o plikach cookie. Baner stanie się potrzebny w dniu, w którym pojawią się skrypty analityczne lub marketingowe. |
| 13 | Czy pole wyboru dla umowy powierzenia przetwarzania nadal jest potrzebne? | RODO art. 28 ust. 9 wymaga umowy powierzenia „na piśmie, w tym w formie elektronicznej”. Działa każda możliwa do udowodnienia akceptacja; pole wyboru z zapisaną wersją to najmocniejszy dowód. | średnia | Zachować pole wyboru. |

### 1.3 Pytania znalezione 2026-11-09

| # | Pytanie | Co wynika z badań | Pewność | Ustawienie domyślne |
|---|---|---|---|---|
| 14 | DSA art. 12 ust. 1: czy potrzebny jest drugi elektroniczny sposób kontaktu? Kto jest „odbiorcą”: tylko klienci, czy także subskrybenci? | Tekst stanowi, że odbiorcy muszą móc wybrać sposób komunikacji. Jeden adres e-mail nie daje wyboru. | średnia | Dziś tylko e-mail; formularz zgłoszeń to zgłoszenie #475. |
| 15 | Czy automatyczne zawieszenie z powodu dostarczalności wymaga uzasadnienia według DSA art. 17? | Art. 17 obejmuje ograniczenia nałożone, ponieważ treść jest nielegalna albo narusza warunki. Zawieszenie z powodu wysokiego odsetka odbić to prawdopodobnie środek techniczny, ale polityka traktuje je jako sygnał naruszenia. | niska | Traktować jako objęte: e-mail o zawieszeniu powinien podawać fakty i sposób zaskarżenia. Dziś nie podaje żadnego z nich. |
| 16 | Czy blokada adresu może przetrwać usunięcie danych osoby i zakończenie umowy z klientem? | RODO art. 17 ust. 3 lit. b oraz art. 21 ust. 3 uzasadniają zachowanie minimalnego rejestru blokad. Kod usuwa wszystkie blokady, gdy konto klienta zostaje usunięte. | średnia | Zachować przy usunięciu danych osoby; usunąć razem z kontem. |
| 17 | Skrót (hash) nazwy nadawcy przechowywany bez limitu czasu | Skrót nazwy firmowej nadawcy jest co najwyżej słabo osobowy; „bez limitu czasu” nadal wymaga uzasadnienia na tle zasady ograniczenia przechowywania. | niska | Zachowany; pole w stronie o usuwaniu danych. |
| 18 | Czy opublikowana strona DSA jest zgodna z prawem bez danych identyfikacyjnych przedsiębiorcy? | UŚUDE art. 5 oraz DSA art. 11 i 12 zakładają możliwego do zidentyfikowania usługodawcę. | wysoka co do tego, że to luka | Opublikować dane identyfikacyjne razem z Regulaminem. |
| 19 | Czy przedsiębiorca musi mieć adres do doręczeń elektronicznych? | Przedsiębiorcy jednoosobowi wpisani do CEIDG przed 2025 r. musieli mieć adres do e-Doręczeń od 2026-10-01 (wpis do bazy adresów do 2026-09-30), według kilku źródeł z 2026 r. Nie zgłoszono kary za opóźnienie, ale pisma urzędowe mogą zostać uznane za doręczone. | średnia (źródła wtórne) | Krok właściciela, pilny: sprawdzić na biznes.gov.pl i założyć adres. |
| 20 | Inne akty do wykluczenia | Europejski akt o dostępności (usługi dla konsumentów od 2025-06-28): mikroprzedsiębiorstwa świadczące usługi są wyłączone. NIS2: mikro i małe podmioty co do zasady są poza zakresem. Rozporządzenie o relacjach platforma-przedsiębiorca (P2B): IRIS nie jest usługą pośrednictwa. Akt w sprawie sztucznej inteligencji: dziś brak funkcji AI. | średnia | Bez działań; sprawdzić ponownie, gdy firma urośnie albo zmienią się funkcje. |

## Część 2. Lista kontrolna dokumentów

| Dokument | Wymagany przez | Dla kogo | Stan |
|---|---|---|---|
| Regulamin | UŚUDE art. 8; ustawa o prawach konsumenta art. 12 | Klienci | Projekt v1 |
| Informacje przedumowne i podsumowanie zamówienia | Ustawa o prawach konsumenta art. 12, 17 | Konsumenci | Nie zbudowano (Część 3) |
| Pouczenie o odstąpieniu od umowy i wzór formularza | Ustawa o prawach konsumenta art. 12 ust. 1 pkt 9, załączniki 1 i 2 | Konsumenci | Nie napisano |
| Potwierdzenie zawarcia umowy na trwałym nośniku | Ustawa o prawach konsumenta art. 21 | Konsumenci | Nie zbudowano |
| Procedura reklamacyjna | UŚUDE art. 8 ust. 3 pkt 4 | Klienci | W Regulaminie, § 10 |
| Polityka prywatności | RODO art. 13, 14 | Klienci, odwiedzający, zaproszeni | Projekt v3 |
| Informacja o plikach cookie | PKE art. 399 | Odwiedzający | Projekt v3 |
| Umowa powierzenia przetwarzania danych i lista podmiotów przetwarzających (podprocesorów) | RODO art. 28 | Klienci | Projekt v1 |
| Rejestr czynności przetwarzania | RODO art. 30 | Wewnętrzny | Projekt (`record-of-processing.md`) |
| Rejestr naruszeń i procedura | RODO art. 33 ust. 5 | Wewnętrzny | Nie napisano |
| Oceny transferów dla podprocesorów spoza EOG | RODO art. 44 do 46 | Wewnętrzny | Nie napisano |
| Wzór informacji twórcy | RODO art. 13, 14 (obowiązek twórcy) | Odbiorcy | Projekt |
| Zasady dopuszczalnego użycia | DSA art. 14; umowa | Klienci | Opublikowano 2026-11-09 |
| Punkt kontaktowy DSA i droga zgłoszeń | DSA art. 11, 12, 16 | Wszyscy | Opublikowano 2026-11-09 |
| Strona o usuwaniu danych | Warunki platformy Meta (Meta Platform Terms) | Klienci, odbiorcy | Projekt; stara strona jest nadal publiczna |
| Strona o bezpieczeństwie | Zaufanie klientów; nie jest obowiązkiem prawnym | Klienci | Nie napisano (#467) |

Inspektor ochrony danych nie jest wymagany przy tej skali (RODO art. 37). Ocena skutków dla
ochrony danych: warto przygotować pisemną jednostronicową wstępną analizę, ponieważ usługa
wysyła wiadomości do wielu osób w imieniu klientów (art. 35); pewność niska co do tego, czy
pełna ocena jest wymagana.

## Część 3. Zamówienie: zasady konsumenckie i proponowane brzmienie

### 3.1 Zasady

- **Odstąpienie od umowy.** Konsument może odstąpić od umowy zawartej na odległość w ciągu 14
  dni (ustawa o prawach konsumenta art. 27). IRIS to **usługa** cyfrowa świadczona w czasie,
  a nie jednorazowa treść cyfrowa. Przy usłudze prawo wygasa tylko po jej całkowitym
  wykonaniu (art. 38 ust. 1 pkt 1), czego działający plan nigdy nie osiąga w ciągu 14 dni.
  Wyłączenie dla treści cyfrowych (art. 38 ust. 1 pkt 13) nie pasuje więc do planu. Pewność:
  średnia do wysokiej.
- **Rozpoczęcie przed upływem 14 dni.** Sprzedawca może zacząć od razu tylko na wyraźne
  żądanie konsumenta (art. 15 ust. 3, art. 21 ust. 2). Konsument, który następnie odstępuje
  od umowy, płaci proporcjonalnie za wykorzystaną część (art. 35). Bez takiego żądania
  sprzedawca nie może naliczyć opłaty za dni wykorzystania. To samo oświadczenie musi
  zawierać przyjęcie przez konsumenta do wiadomości, że prawo odstąpienia wygasa z chwilą
  pełnego wykonania (art. 21 ust. 2); dla działającego planu ta chwila nie następuje w ciągu
  14 dni, ale to przyjęcie do wiadomości jest częścią procedury. To żądanie to poniższe pole
  wyboru.
- **Okres próbny.** Bezpłatny okres próbny bez karty nie rodzi obowiązku zapłaty; przepisy
  zaczynają działać przy pierwszym płatnym zamówieniu.
- **Przycisk zamówienia.** Przycisk musi informować, że zamówienie oznacza obowiązek zapłaty,
  słowami takimi jak „zamówienie z obowiązkiem zapłaty” (art. 17 ust. 3). W przeciwnym razie
  umowa nie zostaje zawarta. Tekst przycisku w Stripe Checkout trzeba sprawdzić pod tym
  kątem; etykietę można konfigurować w pewnych granicach. Pewność: wysoka co do reguły,
  niska co do tego, na co pozwala Stripe.
- **Przed zamówieniem** konsument musi zobaczyć: główne cechy usługi, całkowitą cenę z VAT,
  okres rozliczeniowy, że plan odnawia się do czasu rezygnacji, jak zrezygnować, prawo
  odstąpienia od umowy, dane sprzedawcy (art. 12, art. 17 ust. 1).
- **Po zamówieniu** sprzedawca wysyła potwierdzenie z tymi warunkami na trwałym nośniku, na
  przykład e-mailem (art. 21 ust. 1).
- **Odnowienie i zmiany ceny.** Odnowienie po nowej cenie wymaga uprzedniego powiadomienia
  i bezpłatnego sposobu wyjścia. Reguły organizacji kartowych wymagają tego samego przy
  płatnościach cyklicznych: kwota, częstotliwość i sposób rezygnacji, pokazane przy
  rejestracji i na potwierdzeniu płatności.
- **Silne uwierzytelnianie klienta.** Pierwsza płatność kartą jest uwierzytelniana (3-D
  Secure). Późniejsze obciążenia są inicjowane przez sprzedawcę i zwolnione, o ile pierwsza
  płatność ustanowiła upoważnienie. Obsługuje to Stripe.
- **Obniżki cen.** Gdy ogłaszana jest obniżka, trzeba pokazać najniższą cenę z 30 dni przed
  nią (ustawa o informowaniu o cenach towarów i usług art. 4 ust. 2). Brak obowiązku, gdy
  obniżka nie jest pokazywana.
- **Żadnych zaznaczonych z góry pól** dla czegokolwiek, co kosztuje dodatkowo (art. 10).

### 3.2 Proponowane brzmienie, polskie (rozstrzyga)

Wymagane pole wyboru, konsumenci i przedsiębiorcy jednoosobowi z prawami konsumenta:

> Proszę o rozpoczęcie świadczenia usługi przed upływem 14 dni na odstąpienie od umowy.
> Wiem, że jeśli odstąpię od umowy w tym terminie, zapłacę za okres, w którym korzystam
> z usługi, proporcjonalnie do ceny planu. Przyjmuję do wiadomości, że po pełnym wykonaniu
> usługi tracę prawo odstąpienia od umowy.

Linijka nad przyciskiem płatności (bez pola wyboru):

> Plan [NAZWA] kosztuje [KWOTA] zł brutto za [miesiąc / rok]. Odnawia się automatycznie na
> kolejny okres, a opłatę pobieramy z karty, dopóki nie zrezygnujesz. Zrezygnować możesz
> w każdej chwili w ustawieniach konta; plan działa do końca opłaconego okresu. Składając
> zamówienie, akceptujesz [Regulamin] i [Zasady dopuszczalnego użycia]. Informacje o danych
> podaje [Polityka prywatności].

Przycisk: **Zamawiam z obowiązkiem zapłaty**

Pouczenie o odstąpieniu do e-maila z potwierdzeniem:

> Masz prawo odstąpić od umowy w terminie 14 dni od jej zawarcia bez podania przyczyny.
> Wystarczy, że przed upływem terminu wyślesz oświadczenie na adres support@irisapp.pl albo
> użyjesz funkcji odstąpienia w ustawieniach konta. Możesz użyć wzoru formularza, ale nie
> jest to obowiązkowe. Zwrócimy płatność w ciągu 14 dni, tym samym sposobem. Jeżeli na Twoją
> prośbę usługa zaczęła działać wcześniej, potrącimy kwotę proporcjonalną do okresu
> korzystania.

### 3.3 Proponowane brzmienie, angielskie (tłumaczenie)

> I ask you to start the service before the 14-day withdrawal period ends. I understand that
> if I withdraw in that period, I pay for the time I use the service, in proportion to the
> price of the plan. I acknowledge that I lose the right of withdrawal when the service is
> fully performed.

> The [NAME] plan costs PLN [AMOUNT] including VAT per [month / year]. It renews
> automatically for the next period, and we charge your card until you cancel. You can cancel
> at any time in the account settings; the plan runs to the end of the paid period. By
> ordering you accept the [Terms] and the [Acceptable-use policy]. The [Privacy Policy] says
> how we use data.

Przycisk: **Order and pay**

> You can withdraw from the contract within 14 days of its conclusion, without a reason.
> Send a statement to support@irisapp.pl or use the withdrawal function in the account
> settings before the period ends. You can use the model form, but you do not have to. We
> refund the payment within 14 days, by the same method. If the service started earlier at
> your request, we keep the amount in proportion to the time of use.

### 3.4 Czego potrzebuje produkt

Pole wyboru i linijka przy zamówieniu, zapisany ślad obu z datą i godziną oraz wersją tekstu,
e-mail z potwierdzeniem, funkcja odstąpienia i procedura zwrotu proporcjonalnego. Dziś nic
z tego nie istnieje. Dla klienta będącego przedsiębiorcą z numerem NIP pole wyboru można
pominąć tylko wtedy, gdy prawnik zaakceptuje sposób odróżniania chronionych przedsiębiorców
jednoosobowych; bezpieczne ustawienie domyślne to pokazanie go wszystkim.

## Część 4. Podatki i faktury (dla księgowego)

Wszystko tutaj ma pewność **średnią**, chyba że zaznaczono inaczej; przepisy podatkowe się
zmieniają, a o wyniku decydują własne fakty przedsiębiorcy.

### 4.1 Gdzie należy się VAT

| Klient | Reguła | Faktura |
|---|---|---|
| Polska, przedsiębiorca lub konsument | Polski VAT, 23% | Polska faktura; dla konsumenta na żądanie |
| Inny kraj UE, przedsiębiorca z ważnym numerem VAT UE | Miejscem świadczenia jest kraj klienta (ustawa o VAT art. 28b). Brak polskiego VAT; rozlicza go klient | Faktura z adnotacją „odwrotne obciążenie”. Przedsiębiorca musi być zarejestrowany jako podatnik VAT UE (VAT-UE) i składać informację podsumowującą |
| Inny kraj UE, konsument | Usługi elektroniczne opodatkowuje się w kraju konsumenta (art. 28k). Wyjątek: dopóki łączna sprzedaż transgraniczna takich usług konsumentom w UE nie przekracza 10 000 EUR (42 000 zł) netto w bieżącym i poprzednim roku, stosuje się polski VAT | Powyżej limitu: rejestracja w procedurze unijnej One Stop Shop (OSS) w Polsce i płacenie VAT każdego kraju jedną kwartalną deklaracją albo rejestracja w każdym kraju |
| Poza UE, przedsiębiorca | Poza zakresem polskiego VAT | Faktura z oznaczeniem „NP”; mogą obowiązywać lokalne przepisy kraju klienta |
| Poza UE, konsument | Nie podlega opodatkowaniu w Polsce; niektóre kraje (na przykład Wielka Brytania, Norwegia, Szwajcaria) opodatkowują zagranicznych sprzedawców cyfrowych, niektóre od pierwszej sprzedaży | Do sprawdzenia dla każdego kraju albo nie sprzedawać tam |

Aby ustalić, gdzie jest konsument, przepisy UE wymagają dwóch dowodów, które nie są ze sobą
sprzeczne (adres rozliczeniowy, kraj karty, adres IP). Jeden dowód wystarczy tylko przy
spełnieniu trzech warunków: taka sprzedaż nie przekracza 100 000 EUR w bieżącym i poprzednim
roku kalendarzowym, a dowód pochodzi od osoby zaangażowanej w świadczenie, innej niż
sprzedawca i klient, na przykład od dostawcy płatności (rozporządzenie wykonawcze Rady (UE)
nr 282/2011 art. 24b, 24f). Samo oświadczenie klienta o adresie nie wystarcza.

### 4.2 Przepływ pasujący do kodu

1. Zamówienie zbiera kraj, adres rozliczeniowy i, dla przedsiębiorcy, numer podatkowy
   (kod już włącza zbieranie numeru podatkowego).
2. Numer VAT UE jest sprawdzany w VIES. Stripe Tax weryfikuje numery UE; zachować wynik
   i czas jako dowód. Nieważny numer oznacza, że sprzedaż traktuje się jak sprzedaż
   konsumencką.
3. Stripe Tax wylicza stawkę (kod ma przełącznik automatycznego podatku). Wymaga to
   wpisania w Stripe rejestracji przedsiębiorcy: Polska oraz OSS, gdy jest używany.
4. Webhook opłaconej faktury uruchamia wystawienie polskiej faktury. Faktura lub
   potwierdzenie płatności ze Stripe nie jest samo w sobie polską fakturą VAT, chyba że
   zawiera wszystkie wymagane pola; większość polskich sprzedawców wystawia fakturę z programu
   fakturowego zasilanego webhookiem.
5. Faktura trafia do KSeF tam, gdzie jest to wymagane (4.3), i do klienta e-mailem.
6. Zwroty i proporcjonalne odstąpienia powodują wystawienie faktury korygującej.
7. Co miesiąc: JPK_V7; co kwartał: deklaracja OSS, gdy jest rejestracja; informacja
   podsumowująca UE dla sprzedaży z odwrotnym obciążeniem.

Zamówienie dodatku nie wysyła dziś żadnych ustawień podatkowych (zgłoszenie #453).

### 4.3 KSeF

- Obowiązkowy dla większości sprzedawców od 2026-04-01. Najmniejsi sprzedawcy (faktury do
  10 000 zł brutto miesięcznie) są zwolnieni do 2026-12-31; pełny obowiązek i kary od
  2027-01-01 (kilka źródeł z 2026 r.; potwierdzić na ksef.podatki.gov.pl).
- Faktury dla konsumentów są poza obowiązkiem; można je wystawiać po staremu. Pewność niska.
- Faktury dla zagranicznych przedsiębiorców wystawia się w KSeF i dodatkowo dostarcza
  nabywcy w uzgodniony sposób, ponieważ nabywca nie ma dostępu do KSeF. Pewność niska.
- Stripe nie wysyła faktur do KSeF. Potrzebny jest program fakturowy z połączeniem do KSeF
  albo własna integracja.

### 4.4 Inne punkty dla księgowego

- **Kasa rejestrująca.** Sprzedaż konsumentom zwykle wymaga kasy fiskalnej. Istnieje
  zwolnienie dla usług opłaconych w całości przez bank lub instytucję płatniczą, gdy
  ewidencja pokazuje, której sprzedaży dotyczyła wpłata; trzeba potwierdzić, czy obejmuje
  ono usługi elektroniczne sprzedawane przez IRIS. Pewność niska. Ma to znaczenie od
  pierwszej sprzedaży konsumenckiej.
- **Opłaty Stripe.** Opłaty Stripe to usługa nabywana od spółki z UE (Irlandia): import
  usług, rozliczany przez przedsiębiorcę metodą odwrotnego obciążenia.
- **Waluta.** Sprzedaż w PLN pozwala uniknąć przepisów o kursach walut na fakturach.
- **Przechowywanie dokumentów.** Dokumenty podatkowe przechowuje się 5 lat od końca roku,
  w którym upłynął termin płatności podatku; dokumenty OSS przez 10 lat.
- **Moment powstania obowiązku podatkowego** dla usługi cyklicznej: koniec każdego okresu
  rozliczeniowego albo wpłata, jeśli nastąpi wcześniej.

## Część 5. Akt o cyberodporności i prawo bezpieczeństwa

Rozporządzenie (UE) 2024/2847 obejmuje produkty z elementami cyfrowymi wprowadzane na rynek
UE. Usługa oferowana wyłącznie online nie jest takim produktem; jest objęta tylko jako część
„zdalnego przetwarzania danych” produktu, który ten sam producent sprzedaje. IRIS nie
dostarcza klientom żadnego oprogramowania. Obowiązki sprawozdawcze zaczynają się 2026-09-11,
a główne obowiązki 2027-12-11, dla podmiotów objętych zakresem. Pewność: średnia, że IRIS jest
poza zakresem. Obowiązki dotyczące bezpieczeństwa, które mają zastosowanie, wynikają z RODO
art. 32 i z umowy powierzenia przetwarzania, Załącznik 2.

## Część 6. Kto co weryfikuje i kiedy

| Pozycja | Kto | Kiedy |
|---|---|---|
| Adres do e-Doręczeń (1.3, #19) | Właściciel | Teraz; termin minął |
| Kasa rejestrująca i faktury dla konsumentów (4.4, 4.3) | Księgowy | Przed pierwszą płatną sprzedażą konsumencką |
| Limit OSS, rejestracja VAT-UE, procedura VIES (4.1, 4.2) | Księgowy | Przed pierwszą sprzedażą poza Polską |
| Ścieżka KSeF (4.3) | Księgowy | Odbiór faktur zakupu przez KSeF: teraz, obowiązek dotyczy każdego przedsiębiorcy od 2026-02-01. Wystawianie: przed 2027-01-01, wcześniej, jeśli faktury miesięczne przekroczą 10 000 zł |
| Brzmienie zamówienia i żądanie rozpoczęcia od razu (Część 3) | Prawnik | Przed pierwszą płatną sprzedażą konsumencką |
| Funkcja odstąpienia (pytanie 8) | Prawnik, potem wykonanie | Przy pracach nad zamówieniem |
| Klasyfikacja DSA i opublikowane strony (pytania 5, 14, 15, 18) | Prawnik | Pierwsza pozycja przekazania (#234) |
| Łańcuch zgód i pierwsza wiadomość prywatna (pytanie 3) | Prawnik | Przed promowaniem funkcji marketingowych |
| Klauzule niedozwolone i limit (pytanie 2) | Prawnik | Przed publikacją Regulaminu |
| Podmioty będące podprocesorami i transfery | Właściciel (umowy), prawnik | Przed publikacją umowy powierzenia przetwarzania |
| Właściciel skrzynki i czasy odpowiedzi (#158) | Właściciel | Teraz; opublikowane strony wskazują skrzynki |
