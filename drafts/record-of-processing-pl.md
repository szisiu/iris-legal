> Tłumaczenie pliku record-of-processing.md. W razie różnic rozstrzyga wersja angielska.

# Rejestr czynności przetwarzania (art. 30 RODO): IRIS

**Dokument wewnętrzny. Nie publikować.**

- Data: 2026-11-09
- Status: Projekt do przeglądu prawnego
- Źródło faktów w tabelach: `internal/privacy/registry.go`
- Inne źródła: `subprocessors.html`, `privacy-en.html` i `dpa-en.html` (Załącznik 1 i Załącznik 2), wszystkie w wersji 3 projektu z 8 listopada 2026. Okresy zadań sprawdzono w `internal/jobs/` (`retention.go`, `identity_retention.go`).
- Uwaga: `registry_test.go` kończy się błędem, gdy migracja dodaje tabelę, której rejestr nie wymienia. Rejestr ma więc jeden wpis dla każdej tabeli. Część C wymienia każdy wpis.

Jak czytać ten rejestr. Jedynymi źródłami są rejestr (registry) i projekty dokumentów prawnych. Jeżeli źródło nie podaje faktu, w tekście stoi `[DO SPRAWDZENIA: ...]`. Nie dodano żadnego okresu przechowywania, podstawy prawnej ani podmiotu podprzetwarzającego spoza tych plików.

Role. IRIS ("Operator") jest administratorem danych kont swoich klientów, użytkowników, zapisów logowania, rozliczeń, zaproszeń, zapisów operatora i audytu, wsparcia oraz zgłoszeń (Część A). IRIS jest podmiotem przetwarzającym, w imieniu każdego klienta, w odniesieniu do osób komentujących, kontaktów i subskrybentów, rozmów, zapisów zgód, list wykluczeń, dostarczeń i zdarzeń poczty, dostarczeń webhooków oraz wysyłek masowych (Część B). Klient jest twórcą lub firmą i jest administratorem tych danych.

---

## Część A. Art. 30 ust. 1: IRIS jako administrator

### A.1 Pola wymagane przez art. 30 ust. 1

**(a) Nazwa i dane kontaktowe administratora.**
`[DO UZUPEŁNIENIA: nazwa i dane kontaktowe operatora, przechowywane poza repozytorium]`

**(b) Cele przetwarzania.**
- Prowadzenie konta, logowania, sesji i wybranej usługi.
- Zarządzanie zaproszeniami i dostępem.
- Dokumentowanie przyjęcia umowy powierzenia (DPA).
- Prowadzenie audytu działań klientów i operatora.
- Obsługa integracji z Instagramem i bezpieczne jej zakończenie.
- Identyfikacja nadawcy w stopkach wiadomości i na stronach zbierania danych oraz konfiguracja domeny nadawczej.
- Rozliczanie klientów, prowadzenie dokumentacji podatkowej i księgowej oraz obsługa roszczeń.
- Przygotowanie eksportów konta oraz udowodnienie usunięcia konta i żądań usunięcia danych od Meta.
- Odpowiadanie na zgłoszenia do wsparcia, skargi i żądania osób, których dane dotyczą.
- Zapewnienie bezpieczeństwa i niezawodności usługi (logi, liczniki, limity, historia stanu).
- Uniemożliwienie późniejszemu kontu użycia adresu nadawcy usuniętego konta.

**(c) Kategorie osób, których dane dotyczą.**
- Klienci oraz przedstawiciele klientów będących osobami prawnymi.
- Zaproszeni, którzy nie mają konta.
- Odwiedzający panel i strony prawne.
- Osoby, które kontaktują się z IRIS.
- Pracownicy IRIS, którzy korzystają z dostępu operatora.

**(c) Kategorie danych osobowych.**
- Dane konta: adres e-mail, język, nazwa konta, ustawienia, strefa czasowa, preferencje powiadomień.
- Dane logowania: adres e-mail, skrót jednorazowego tokenu, prefiks IP. Dane sesji: skrót tokenu, prefiks IP, user agent, czasy aktywności.
- Dane zaproszenia: adres e-mail, język, notatka operatora, kto i kiedy dodał zaproszenie, termin ważności, stan przyjęcia.
- Przyjęcie DPA: wersja, czas, prefiks IP, user agent.
- Zapisy audytu: czas, identyfikatory, prefiks IP, przeglądarka, nazwy zmienionych pól i wartości niebędące danymi osobowymi.
- Połączenie z Instagramem: identyfikatory, nazwa użytkownika, typ konta, uprawnienia, zaszyfrowany token, termin ważności.
- Tożsamość nadawcy: nazwa, adresy pocztowy i e-mail do kontaktu, domena nadawcza.
- Dane rozliczeniowe: adres e-mail, NIP, dane nabywcy, identyfikatory klienta, subskrypcji, ceny i płatności w Stripe, zakupione bloki i liczby leadów w blokach.
- Zapisy eksportów i usunięć.
- Korespondencja ze wsparciem: adres, treść, załączniki, metadane.
- Logi żądań i błędów, identyfikatory, domena nadawcy.
- Dane operatora: adres e-mail, sesje, prefiks IP, przeglądarka, identyfikator (handle) operatora i jego działania.
- Liczniki techniczne z identyfikatorami kont.
- Skrót identyfikatora nadawcy po usunięciu konta.

**(d) Kategorie odbiorców.**
- Resend, dla poczty logowania i innej poczty IRIS oraz dla poczty klientów. AWS jest dalszym podmiotem przetwarzającym Resend.
- Cloudflare: proxy, TLS, DNS, Tunnel, pamięć podręczna obrazów publicznych i Access dla operatora. Widzi przesyłane dane, adresy IP, pełne ścieżki, formularze, webhooki i pliki cookie.
- OVHcloud: skrzynka pocztowa operatora i przekierowania poczty. VPS dla aplikacji i PostgreSQL jest planowany i jeszcze nie zamówiony.
- Stripe Payments Europe Ltd., dla rozliczeń własnych klienta. `[DO SPRAWDZENIA: właściwy podmiot Stripe dla umowy IRIS, rola dla każdej usługi, kraje i podstawy przekazań poza EOG.]`
- Meta Platforms Ireland Ltd., niezależny administrator danych na swojej platformie.
- GitHub Pages, które hostuje publiczne strony prawne i otrzymuje dane o wizytach, takie jak adresy IP.
- Tailscale, które służy do administracji hostem. Dokumentacja wdrożenia stwierdza, że nie przenosi danych klientów.
- Organy publiczne, gdy wymaga tego prawo.
- Księgowi lub inni doradcy: `[DO SPRAWDZENIA: faktyczne korzystanie z księgowych lub innych doradców, ich role i zakres odbiorców; nie zakłada się żadnego takiego dostawcy.]`

**(e) Przekazania do państw trzecich i zabezpieczenia.**
- Resend wysyła z AWS eu-west-1 (Irlandia). Według dokumentacji użytej do projektów Resend przechowuje dane konta i metadane w USA. Projekty wskazują standardowe klauzule umowne. `[DO SPRAWDZENIA: zakres danych w USA, aktualna umowa, moduł SCC, dalsi podprzetwarzający i środki dodatkowe.]`
- Infrastruktura AWS znajduje się w UE i w USA według dokumentacji projektu. `[DO SPRAWDZENIA: właściwy podmiot AWS, lokalizacje i podstawa dalszych przekazań.]`
- Cloudflare prowadzi sieć globalną. Nie zweryfikowano żadnego ograniczenia do samej UE. `[DO SPRAWDZENIA: umowa i podstawa przekazania dla konta IRIS, w tym SCC i środki dodatkowe; kraje przetwarzania, zdalny dostęp i okres przechowywania.]` Nie zweryfikowano oparcia się na unijno-amerykańskich ramach ochrony danych (EU-US Data Privacy Framework).
- Skrzynka OVHcloud: `[DO SPRAWDZENIA: kraj przechowywania skrzynki, kopie i dostęp serwisowy oraz czy poczta wiąże się z przekazaniami poza EOG.]`
- Stripe: zob. (d).
- Baza danych we Francji nie oznacza, że wszystkie dane pozostają w EOG.

**(f) Terminy usunięcia.** Zob. kolumnę "Okres przechowywania" w tabeli w A.2. Rejestr (registry) ustala każdy okres. Polityka prywatności stwierdza, że zadania usuwające działają według progów oraz że harmonogram, partie i blokady mogą opóźnić usunięcie. `[DO SPRAWDZENIA: ustawienia produkcyjne i maksymalne opóźnienia.]`

**(g) Środki bezpieczeństwa (opis ogólny, z Załącznika 2 do DPA).**
- HTTPS dla ruchu publicznego. HSTS przez rok wraz z subdomenami poza trybem deweloperskim. Cloudflare kończy TLS. Ścieżka od hosta do Cloudflare korzysta z Cloudflare Tunnel.
- Nagłówki bezpieczeństwa: restrykcyjna Content-Security-Policy, zakaz osadzania w ramkach, nosniff, polityka referrer.
- Tokeny dostępu do Instagrama i tokeny wypisania są szyfrowane algorytmem AES-256-GCM. Klucze można rotować.
- Logowanie jednorazowym linkiem. Tabele uwierzytelniania przechowują skróty tokenów logowania i sesji. Pliki cookie sesji używają HttpOnly i SameSite=Lax. Obowiązuje ochrona CSRF.
- Izolacja kont: zapytania w panelu klienta są ograniczone do zalogowanego konta. Identyfikator konta nie pochodzi z treści żądania.
- Ślad audytowy działań klientów i operatora. IP skrócone do /24 (IPv4) lub /48 (IPv6), gdy jest zapisywane.
- Webhooki są przyjmowane tylko z prawidłowym podpisem.
- Dostęp operatora tylko przez Cloudflare Access z jednorazowym PIN-em i osobną sesją aplikacji. Administracja hostem korzysta z Tailscale. Host nie udostępnia publicznie portu aplikacji ani bazy danych.
- Minimalizacja i usuwanie: automatyczne usuwanie według okresów z rejestru (registry), usunięcie danych wskazanej osoby, eksport konta, usunięcie konta z dowodem.
- Brak zewnętrznej analityki, śledzenia błędów i zbierania logów aplikacji.
- Jeszcze niewdrożone: monitoring i kopie zapasowe. `[DO SPRAWDZENIA: środki produkcyjne przed uruchomieniem VPS, szyfrowanie dysków i kopii zapasowych, odtwarzanie, monitoring.]`

### A.2 Czynności przetwarzania jako administrator

Podstawy prawne są te z `privacy-en.html` sekcja 3: b to art. 6 ust. 1 lit. b RODO (umowa), c to art. 6 ust. 1 lit. c (obowiązek prawny), f to art. 6 ust. 1 lit. f (prawnie uzasadnione interesy). Sam `privacy-en.html` oznacza przyporządkowanie podstaw jako `[DO SPRAWDZENIA: zatwierdzenie przyporządkowania podstaw, testów równowagi i przepisów szczególnych uzasadniających c.]`

| Czynność | Osoby, których dane dotyczą | Dane | Cel | Podstawa prawna | Tabele | Okres przechowywania | Odbiorcy |
|---|---|---|---|---|---|---|---|
| A1 Konto | Klienci i ich przedstawiciele | Adres e-mail, język, nazwa konta, ustawienia, strefa czasowa, preferencje powiadomień | Usługa konta | b; f dla przedstawicieli | `users`, `tenants` | Tak długo, jak tenant (rejestr). Polityka prywatności: do usunięcia konta | Resend, Cloudflare |
| A2 Logowanie | Posiadacze kont i osoby bez konta, które proszą o link | Adres e-mail, skrót jednorazowego tokenu, prefiks IP | Wysyłanie linków logowania, zapobieganie nadużyciom | b na żądanie osoby; f dla bezpieczeństwa | `sign_in_tokens` | 7 dni po `expires_at` (zadanie `identity_retention`). Polityka prywatności dodaje: token ważny domyślnie 15 minut | Resend, Cloudflare |
| A3 Sesje | Klienci | Skrót tokenu, prefiks IP (/24 lub /48), user agent, czasy aktywności | Uwierzytelnianie | b i f (ochrona dostępu) | `sessions` | Usunięcie w chwili `expires_at` (zadanie `identity_retention`). Rejestr nie podaje liczby. Polityka prywatności podaje domyślny maksymalny czas 7 dni | Cloudflare |
| A4 Zaproszenia | Zaproszeni bez konta | Adres e-mail, język, notatka operatora, kto i kiedy dodał, termin ważności, stan przyjęcia | Dostęp do usługi | f (zarządzanie zaproszeniami i dostępem) | `invitations` | 30 dni po `lapsed_at` (zadanie `identity_retention`). Niewykorzystane zaproszenie wygasa w terminie ważności albo 180 dni po dodaniu, gdy nie ma terminu | Resend |
| A5 Przyjęcie DPA | Przedstawiciele klientów | Wersja, czas, prefiks IP, user agent | Udokumentowanie zawarcia DPA | c (dokumentowanie przetwarzania na podstawie art. 28 RODO); f (dowód i obrona roszczeń) | `dpa_acceptances` (`dpa_versions` nie zawiera danych osobowych) | Tak długo, jak tenant | Brak wskazania |
| A6 Audyt klienta | Klienci i ich użytkownicy | Czas, identyfikatory, prefiks IP, przeglądarka, nazwy zmienionych pól, wartości niebędące danymi osobowymi | Rozliczalność i bezpieczeństwo | f (wykrywanie nadużyć, ustalanie działań) | `audit_events` | 730 dni od `occurred_at` (zadanie `registry_retention`) | Brak wskazania |
| A7 Połączenie z Instagramem | Klienci | Identyfikatory, nazwa użytkownika, typ konta, uprawnienia, zaszyfrowany token, termin ważności | Żądana integracja | b | `social_accounts` | Tak długo, jak tenant. Usunięcie połączenia usuwa wiersz (`connect.Remove`) | Meta (niezależny administrator) |
| A8 Usunięte połączenia z Instagramem | Klienci | Identyfikator Instagrama i daty | Rozpoznanie późniejszych webhooków i bezpieczne zakończenie subskrypcji | f (bezpieczne odłączenie i obsługa usunięcia) | `removed_instagram_accounts` | 90 dni od `unsubscribed_at` (zadanie `webhook_retention`). Wiersz bez znacznika nie ma wieku i pozostaje do udanego wypisania | Meta |
| A9 Tożsamość nadawcy i domena nadawcza | Klienci i przedstawiciele | Nazwa, adresy pocztowy i e-mail do kontaktu, domena nadawcza | Identyfikacja nadawcy w stopkach i na stronach zbierania danych, konfiguracja poczty | b; f dla danych przedstawicieli | `tenant_brands`, `sending_domains`, `sending_domain_tombstones` | `tenant_brands` i `sending_domains`: tak długo, jak tenant. `sending_domain_tombstones`: rejestr nie podaje okresu przechowywania. `[DO SPRAWDZENIA: maksymalny okres przechowywania pozostałych danych po usunięciu domeny.]` | Resend (domena), Cloudflare |
| A10 Treści i ustawienia klienta | Klienci | Kampanie, szablony, obrazy, listy, tagi, linki, ustawienia | Świadczenie usługi | b dla danych klienta (dane powierzone innych osób: Część B) | `campaigns`, `campaign_variants`, `campaign_links`, `email_templates`, `links`, `lists`, `tags`, `media_images`, `settings` | `campaigns` i `media_images`: tak długo, jak tenant. Pozostałe tabele: brak okresu w rejestrze; znikają z tenantem kaskadowo, z wyjątkiem `settings` (partia czyszcząca) | Cloudflare (obrazy publiczne w pamięci podręcznej) |
| A11 Rozliczenia | Klienci i ich przedstawiciele | Adres e-mail, NIP, dane nabywcy, identyfikatory klienta, subskrypcji, ceny i płatności w Stripe, zakupione bloki i liczby leadów | Płatności i fakturowanie | b (umowa); c (dokumentacja podatkowa i księgowa); f (roszczenia) | `plan_addons`, `subscriptions`, `stripe_events` (`plans` i `addon_blocks` nie zawierają danych osobowych) | `plan_addons` i `subscriptions`: tak długo, jak tenant. `stripe_events`: 90 dni od `received_at` (zadanie `stripe_events_retention`). Klient Stripe i dokumentacja podatkowa pozostają w Stripe po usunięciu konta. `[DO SPRAWDZENIA: przepisy szczególne, okresy i punkty początkowe dla faktur, korekt, płatności i zachowanych danych Stripe.]` | Stripe |
| A12 Eksporty i dowód usunięcia | Klienci | Plik eksportu, identyfikator tenanta, kroki i czasy, żądania usunięcia od Meta | Zwrot danych i rozliczalność | b (usługa); f (dowód); c, gdy wykonywany jest obowiązek z RODO | `account_exports`, `account_deletions`, `data_deletion_requests` | `account_exports`: 24 godziny od `expires_at`. `account_deletions`: 365 dni od `finished_at`. `data_deletion_requests`: 365 dni od `received_at`, nigdy nie czyszczone, dopóki mają stan received (zadanie `registry_retention`) | Brak wskazania |
| A13 Wsparcie, skargi i żądania osób, których dane dotyczą | Osoby kontaktujące się z IRIS | Adres, treść, załączniki, metadane | Odpowiedź i obsługa spraw | b dla wsparcia umownego; f dla pozostałej korespondencji i roszczeń; c dla żądań osób, których dane dotyczą, i obowiązków prawnych | Brak w rejestrze (skrzynka OVHcloud) | `[DO SPRAWDZENIA: okresy dla korespondencji, żądań, skarg i roszczeń, kryteria oraz usuwanie ze skrzynki OVHcloud.]` | OVHcloud |
| A14 Logi żądań i błędów | Odwiedzający, klienci | Logi żądań i błędów, identyfikatory, domena nadawcy. Zwykłe logi żądań zawierają wzorzec trasy, status i czas trwania, a nie pełny link z tokenem | Diagnostyka i ochrona | f (bezpieczeństwo i niezawodność) | Brak w rejestrze (logi Dockera) | Do 5 plików po 10 MB na kontener, bez ustalonego limitu czasu. `[DO SPRAWDZENIA: maksymalny okres przechowywania i minimalizacja logów, w tym błędów i logów dostawców.]` | Cloudflare (logi dostawcy) |
| A15 Dostęp operatora | Pracownicy IRIS | Adres e-mail, sesje, prefiks IP, przeglądarka, identyfikator (handle) operatora, działania | Kontrolowane wsparcie i bezpieczeństwo | f (kontrola dostępu uprzywilejowanego) | `operator_sign_in_tokens`, `operator_sessions`, `operator_events` | `operator_sign_in_tokens`: 7 dni po `expires_at`. `operator_sessions`: usunięcie w chwili `expires_at` (polityka prywatności podaje maksimum 8 godzin i 60 minut bezczynności). `operator_events`: 730 dni od `occurred_at`, także po usunięciu konta przez klienta | Cloudflare Access, Resend |
| A16 Liczniki techniczne i historia stanu | Klienci (identyfikatory kont) | Stan, kody, liczby i klasa dla każdego konta. Rejestr stwierdza, że te tabele nie zawierają osób | Działanie usługi, limity, zapobieganie nadużyciom | f (niezawodność i zapobieganie nadużyciom) | `health_transitions`, `meta_calls`, `outbox_skips`, `rate_limit_buckets`, `circuit_breakers`, `account_polls`, `usage_events` | `health_transitions`: 730 dni od `at`. `meta_calls`: 14 dni od `at`. `outbox_skips`: 90 dni od `hour`. `rate_limit_buckets` i `circuit_breakers`: 90 dni od `removed_instagram_accounts.removed_at`. `account_polls` i `usage_events`: brak okresu w rejestrze | Meta (wywołania) |
| A17 Skrót identyfikatora nadawcy | Usunięci klienci | SHA-256 z identyfikatora nadawcy (slug) i czasu | Uniemożliwienie innemu kontu ponownego użycia adresu nadawcy | f (zapobieganie podszywaniu się) | `tenant_slug_tombstones` | Bezterminowo (rejestr). `[DO SPRAWDZENIA: proporcjonalność i ewentualny maksymalny okres przechowywania tego skrótu.]` | Brak wskazania |

---

## Część B. Art. 30 ust. 2: IRIS jako podmiot przetwarzający

### B.1 Pola wymagane przez art. 30 ust. 2

**(a) Nazwa i dane kontaktowe podmiotu przetwarzającego.**
`[DO UZUPEŁNIENIA: nazwa i dane kontaktowe operatora, przechowywane poza repozytorium]`

**(a) Administratorzy, w imieniu których działa IRIS.** Każdy klient IRIS (twórca lub firma, która ma konto i przyjęła DPA). Zapis przyjęcia znajduje się w `dpa_acceptances`. `[DO SPRAWDZENIA: czy rejestr musi zawierać nazwę i dane kontaktowe każdego administratora i gdzie.]`

**(b) Kategorie przetwarzania dokonywanego w imieniu każdego administratora.**
- Zbieranie leadów z komentarzy pod postami administratora na Instagramie.
- Odpowiadanie osobom komentującym wiadomością prywatną i odpowiedzią publiczną.
- Tworzenie kontaktów dla osób komentujących i zbieranie adresów e-mail.
- Potwierdzanie i przechowywanie subskrybentów, z przypisaniem do list i tagów.
- Rejestrowanie zgód, wypisań i wykluczeń.
- Wysyłanie wiadomości e-mail i wysyłek masowych administratora oraz mierzenie dostarczenia i kliknięć w linki.
- Odbieranie i przechowywanie surowych webhooków.
- Przygotowanie eksportu konta oraz usunięcie danych wskazanej osoby na polecenie administratora.

**(c) Przekazania do państw trzecich i zabezpieczenia.** Te same fakty co w Części A, (e). Lista podmiotów podprzetwarzających obejmuje dane powierzone: Resend (z AWS jako jego dalszym podmiotem przetwarzającym) i Cloudflare. Planowany VPS OVHcloud jest wymieniony jako planowany podmiot podprzetwarzający. Wszystkie są oznaczone `[DO SPRAWDZENIA]` w `subprocessors.html` co do podmiotu, lokalizacji i podstawy przekazania. Meta jest niezależnym administratorem, a nie podmiotem podprzetwarzającym. Stripe nie jest podmiotem podprzetwarzającym danych powierzonych: kod nie wysyła do Stripe danych poszczególnych osób komentujących ani subskrybentów.

**(d) Środki bezpieczeństwa.** Takie same jak w Części A, (g). Opisuje je Załącznik 2 do DPA.

### B.2 Czynności przetwarzania jako podmiot przetwarzający

Klient decyduje o celu i podstawie prawnej oraz sam przekazuje informację osobom, których dane dotyczą (`privacy-en.html` sekcja 4). IRIS przetwarza dane na udokumentowane polecenie klienta (DPA sekcja 4). Z tego powodu tabela nie ma kolumny z podstawą prawną.

| Czynność | Osoby, których dane dotyczą | Dane | Cel | Tabele | Okres przechowywania | Podmioty podprzetwarzające i odbiorcy |
|---|---|---|---|---|---|---|
| B1 Kontakty i subskrybenci | Osoby komentujące, osoby piszące do konta, osoby podające adres e-mail | Identyfikator Instagrama, nazwa użytkownika, adres e-mail i jego postać znormalizowana, status potwierdzenia, przypisania do list i tagów, zaszyfrowany token wypisania | Tworzenie kontaktów, zbieranie i potwierdzanie adresów e-mail, przechowywanie subskrybentów | `contacts`, `list_members`, `contact_tags` | `contacts`: 90 dni, liczone od największej z wartości `updated_at`, `lead_conversations.updated_at` i `automation_executions.evaluated_at`, tylko dla kontaktu, który nigdy nie miał adresu i nie ma tagu, członkostwa w aktywnej liście, zgody, dostarczenia, wykluczenia ani wiersza odbiorcy wysyłki masowej (zadanie `contact_retention`). Każdy inny kontakt żyje tak długo, jak tenant. `list_members` i `contact_tags`: tak długo, jak kontakt | Resend, Cloudflare |
| B2 Odbiór komentarzy i wiadomości | Osoby komentujące i nadawcy wiadomości | Surowe treści webhooków z tekstem komentarzy i wiadomości, identyfikatory postów i komentarzy, wyniki oceny | Odbiór zdarzeń z Meta i dopasowanie ich do reguł administratora | `webhook_deliveries`, `webhook_delivery_accounts`, `processed_events`, `automation_executions` | `webhook_deliveries`: 90 dni od `received_at` (zadanie `webhook_retention`). `webhook_delivery_accounts`: 90 dni, liczone od `received_at` dostarczenia. `processed_events`: 45 dni od `first_seen_at`. `automation_executions`: 90 dni od `evaluated_at` (zadanie `pipeline_retention`) | Cloudflare; Meta (niezależny administrator) |
| B3 Odpowiedzi | Osoby komentujące i nadawcy wiadomości | Tekst wychodzących wiadomości prywatnych i odpowiedzi publicznych, linki, identyfikator odbiorcy | Odpowiadanie osobom komentującym | `outbound_intents` | 30 dni od `updated_at` (zadanie `pipeline_retention`) | Meta |
| B4 Rozmowy zbierające dane | Osoby podające adres w wiadomości lub na stronie zbierania danych | Stan rozmowy, próby i metoda weryfikacji, skrót z kluczem sześciocyfrowego kodu, skrót tokenu strony zbierania danych | Weryfikacja adresów | `lead_conversations`, `capture_tokens` | `lead_conversations`: razem z kontaktem; 90 dni od `updated_at` dla wiersza bez kontaktu (zadanie `registry_retention`). `capture_tokens`: 30 dni od `expires_at` (zadanie `capture_retention`) | Resend, Cloudflare |
| B5 Zgoda i wykluczenie | Kontakty i subskrybenci | Zakres zgody, kanał, czas, klucz, zapisane brzmienie, język, identyfikatory źródła. Wykluczony adres, powód i data | Udokumentowanie zgody, respektowanie wypisań, zapobieganie dalszym wysyłkom | `consent_events`, `suppressions` | `consent_events`: tak długo, jak kontakt. `suppressions`: bezterminowo w rejestrze, usuwane z tenantem kaskadowo | Brak wskazania |
| B6 Dostarczenia i zdarzenia poczty | Odbiorcy poczty administratora | Adres odbiorcy, identyfikatory dostarczenia, zdarzenia dostarczenia, diagnostyka odbić i skarg | Wysyłanie poczty administratora, mierzenie dostarczenia | `email_deliveries`, `mail_events` | `email_deliveries`: 90 dni od `created_at` (zadanie `capture_retention`). `mail_events`: 90 dni od `received_at` (zadanie `registry_retention`); usuwane z kontem, z wyjątkiem zdarzeń, których nie przypisano do konta: nie mają klucza konta i pozostają do końca tego zegara | Resend (AWS jako dalszy podmiot przetwarzający) |
| B7 Wysyłki masowe i kliknięcia | Odbiorcy i osoby klikające śledzone linki | Wiersze odbiorców wysyłki masowej; liczniki kliknięć na link i dzień (UTC), bez wskazania odbiorcy ani wysyłki (link w wiadomości zawiera tylko identyfikator linku; adres IP i user agent są używane tylko w pamięci, bez zapisu) | Wysyłanie wysyłek masowych, mierzenie kliknięć | `broadcast_recipients`, `link_click_days`, `broadcasts` | `broadcast_recipients`: tak długo, jak kontakt. `link_click_days`: tak długo, jak jego link albo tenant; usunięcie danych osoby go zachowuje. `broadcasts`: brak okresu w rejestrze | Resend, Cloudflare |
| B8 Treści administratora | Osoby, których dane znajdują się w treściach lub obrazach dostarczonych przez administratora | Treść kampanii, wiadomości, stron zbierania danych i obrazów, w zakresie, w jakim zawiera dane osobowe | Świadczenie usługi | `campaigns`, `campaign_variants`, `campaign_links`, `email_templates`, `links`, `lists`, `tags`, `media_images` | `campaigns` i `media_images`: tak długo, jak tenant. Pozostałe tabele: brak okresu w rejestrze | Cloudflare (obrazy publiczne w pamięci podręcznej) |
| B9 Eksport konta | Kontakty i subskrybenci wskazani w eksporcie | Plik zip z eksportem zawierający kontakty, zapisy zgód, wykluczenia, zdarzenia audytu, kampanie, szablony, wysyłki masowe, markę (z potwierdzoną treścią informacji dla subskrybentów), rozliczenia i ograniczenia treści | Zwrot danych | `account_exports` | 24 godziny od `expires_at` (zadanie `registry_retention`) | Brak wskazania |

---

## Część C. Każda tabela w rejestrze (registry)

Źródło: `internal/privacy/registry.go`, w kolejności rejestru. "Rola" to rola IRIS dla tabeli. Klasa rejestru `none` jest zapisana jako "brak danych osobowych". "Okres przechowywania" powtarza rejestr. "Usunięcie danych" podaje, co robi usunięcie danych jednej osoby, a następnie co dzieje się po usunięciu tenanta. Dla tabeli bez rodzaju usunięcia w rejestrze komórka to stwierdza.

| # | Tabela | Rola | Czyje dane | Okres przechowywania (rejestr) | Usunięcie danych (rejestr) |
|---|---|---|---|---|---|
| 1 | `contacts` | podmiot przetwarzający | Osoba niebędąca klientem; wyszukiwana po adresie e-mail, identyfikatorze użytkownika Instagrama, handle | Stały wiek: 90 dni od największej z wartości `updated_at`, `lead_conversations.updated_at`, `automation_executions.evaluated_at`. 90 dni dotyczy tylko kontaktu, który nigdy nie miał adresu i nie ma tagu, członkostwa w aktywnej liście, zgody, dostarczenia, wykluczenia ani wiersza odbiorcy wysyłki masowej; każdy inny kontakt żyje tak długo, jak tenant. Zadanie `contact_retention` | Osoba: usunięcie. Tenant: jawne usunięcie w sekwencji usuwania (partia czyszcząca) |
| 2 | `lead_conversations` | podmiot przetwarzający | Osoba niebędąca klientem; wyszukiwana po identyfikatorze kontaktu, identyfikatorze użytkownika Instagrama, adresie e-mail | Stały wiek: 90 dni od `updated_at`, przegląd wierszy z `contact_id IS NULL`. Rozmowa z kontaktem znika razem z kontaktem. Zadanie `registry_retention` | Osoba: usunięcie. Tenant: kaskada |
| 3 | `consent_events` | podmiot przetwarzający | Osoba niebędąca klientem; wyszukiwana po identyfikatorze kontaktu, identyfikatorze użytkownika Instagrama | Tak długo, jak kontakt | Osoba: kaskada przez `contact_id`. Tenant: kaskada |
| 4 | `capture_tokens` | podmiot przetwarzający | Osoba niebędąca klientem; brak klucza wyszukiwania | Stały wiek: 30 dni od `expires_at`. Zadanie `capture_retention` | Osoba: kaskada przez `conversation_id`. Tenant: kaskada |
| 5 | `suppressions` | podmiot przetwarzający | Osoba niebędąca klientem; wyszukiwana po adresie e-mail | Bezterminowo: nigdy nie usuwane. Powód: adres, który zrezygnował lub którego wiadomość została odbita, musi pozostać odrzucany; zachowany na podstawie RODO art. 17 ust. 3 lit. b i art. 21 | Osoba: odłączenie (zachowane z przerwanym powiązaniem osobowym); usunięcie danych ustawia `contact_id` NULL i diagnostykę ''. Tenant: kaskada |
| 6 | `email_deliveries` | podmiot przetwarzający | Osoba niebędąca klientem; wyszukiwana po adresie e-mail, identyfikatorze kontaktu | Stały wiek: 90 dni od `created_at`. Zadanie `capture_retention` | Osoba: usunięcie. Tenant: jawne usunięcie w sekwencji usuwania (partia czyszcząca) |
| 7 | `mail_events` | podmiot przetwarzający | Osoba niebędąca klientem; wyszukiwana po adresie e-mail | Stały wiek: 90 dni od `received_at`. Zadanie `registry_retention` | Osoba: usunięcie (wyszukiwane przez `email_deliveries` tenanta, po `provider_message_id` i po id dostarczenia oraz po tenancie i adresie odbiorcy). Tenant: jawne usunięcie w sekwencji usuwania (partia czyszcząca); wiersz bez `tenant_id` (zdarzenie, którego nie przypisano do konta) usuwa zegar okresu przechowywania |
| 8 | `broadcast_recipients` | podmiot przetwarzający | Osoba niebędąca klientem; wyszukiwana po identyfikatorze kontaktu | Tak długo, jak kontakt | Osoba: kaskada przez `contact_id`. Tenant: kaskada |
| 9 | `link_click_days` | podmiot przetwarzający | Osoba niebędąca klientem; brak klucza wyszukiwania. Link, dzień (UTC) i liczba kliknięć; żadna kolumna nie wskazuje odbiorcy ani wysyłki | Tak długo, jak tenant; usuwany razem ze swoim linkiem | Osoba: zachowanie (żaden klucz osoby nie znajduje wiersza). Tenant: kaskada |
| 10 | `list_members` | podmiot przetwarzający | Osoba niebędąca klientem; wyszukiwana po identyfikatorze kontaktu. Na których listach tenanta jest kontakt | Tak długo, jak kontakt | Osoba: kaskada przez `contact_id`. Tenant: kaskada |
| 11 | `contact_tags` | podmiot przetwarzający | Osoba niebędąca klientem; wyszukiwana po identyfikatorze kontaktu. Które tagi tenanta nosi kontakt | Tak długo, jak kontakt | Osoba: kaskada przez `contact_id`. Tenant: kaskada |
| 12 | `automation_executions` | podmiot przetwarzający | Osoba niebędąca klientem; wyszukiwana po identyfikatorze użytkownika Instagrama, handle | Stały wiek: 90 dni od `evaluated_at`. Zadanie `pipeline_retention` | Osoba: usunięcie. Tenant: jawne usunięcie w sekwencji usuwania (partia czyszcząca) |
| 13 | `outbound_intents` | podmiot przetwarzający | Osoba niebędąca klientem; wyszukiwana po identyfikatorze użytkownika Instagrama | Stały wiek: 30 dni od `updated_at`. Zadanie `pipeline_retention` | Osoba: usunięcie. Wiersz oczekujący lub niepewny (`send_unknown`) wskazujący id jest anulowany i usuwany razem z wierszami końcowymi. Wiersz objęty dzierżawą (leased) jest oznaczany, a nie anulowany: pompa go trzyma, a wiadomość może już być u Meta. Znacznik zamienia każdy późniejszy powrót do stanu oczekującego w anulowanie i zatrzymuje znacznik wysyłki, ponowną wysyłkę i odtworzenie. Wiersz już wysłany pozostaje do końca 30-dniowego okresu przechowywania. Tenant: kaskada |
| 14 | `processed_events` | podmiot przetwarzający | Osoba niebędąca klientem; wyszukiwana po identyfikatorze użytkownika Instagrama | Stały wiek: 45 dni od `first_seen_at`. Zadanie `pipeline_retention` | Osoba: usunięcie. Tenant: jawne usunięcie w sekwencji usuwania (partia czyszcząca) |
| 15 | `webhook_deliveries` | podmiot przetwarzający | Osoba niebędąca klientem; wyszukiwana po identyfikatorze użytkownika Instagrama, adresie e-mail | Stały wiek: 90 dni od `received_at`. Zadanie `webhook_retention` | Osoba: usunięcie. Tenant: jawne usunięcie w sekwencji usuwania (partia czyszcząca) |
| 16 | `webhook_delivery_accounts` | podmiot przetwarzający | Osoba niebędąca klientem; brak klucza wyszukiwania. Znika razem ze swoim dostarczeniem | Stały wiek: 90 dni, od `webhook_deliveries.received_at`. Zadanie `webhook_retention` | Osoba: kaskada przez `delivery_id`. Tenant: jawne usunięcie w sekwencji usuwania (partia czyszcząca) |
| 17 | `sign_in_tokens` | administrator | Osoba niebędąca klientem (osoba, która prosi o link logowania); wyszukiwana po adresie e-mail | Stały wiek: 7 dni od `expires_at`. Zadanie `identity_retention` | Osoba: zachowanie. Brak klucza tenanta, więc żadne usunięcie danych dla tenanta nie znajdzie wiersza; znika siedem dni po wygaśnięciu. Tenant: brak klucza tenanta, usuwa go zegar okresu przechowywania |
| 18 | `invitations` | administrator | Osoba niebędąca klientem (zaproszony); wyszukiwana po adresie e-mail | Stały wiek: 30 dni od `lapsed_at`. Zadanie `identity_retention`. Usunięty lub wygasły wiersz jest usuwany 30 dni po wygaśnięciu; niewykorzystany wiersz wygasa w terminie ważności albo 180 dni po dodaniu, gdy nie ma terminu | Osoba: zachowanie. Lista zaproszeń to adres bez klucza tenanta, więc usunięcie danych dla tenanta nie znajdzie wiersza; żądanie zaproszonego jest obsługiwane przez `iris invite remove --forget`. Tenant: jawne usunięcie w sekwencji usuwania (partia czyszcząca) |
| 19 | `operator_sign_in_tokens` | administrator | Pracownik IRIS (operator). Własny adres operatora; brak klucza tenanta | Stały wiek: 7 dni od `expires_at`. Zadanie `identity_retention` | Zachowanie (znika siedem dni po wygaśnięciu). Tenant: usuwa je zegar okresu przechowywania |
| 20 | `operator_sessions` | administrator | Pracownik IRIS (operator). Sesja z `ip_prefix` i `user_agent` | Stały wiek liczony od `expires_at`; rejestr nie podaje liczby; usunięcie w chwili wygaśnięcia. Zadanie `identity_retention` | Zachowanie. Tenant: usuwa je zegar okresu przechowywania |
| 21 | `operator_events` | administrator | Pracownik IRIS (operator). Co zrobił operator, według handle; nigdy nie eksportowane | Stały wiek: 730 dni od `occurred_at`. Zadanie `registry_retention` | Zachowanie. Tenant: celowo go przeżywa (brak klucza obcego do tenanta) |
| 22 | `account_exports` | administrator | Osoba niebędąca klientem według klasy rejestru `subject`; brak klucza wyszukiwania. Zip z eksportem tenanta | Stały wiek: 24 godziny od `expires_at`. Zadanie `registry_retention` | Osoba: odłączenie. Gotowe eksporty tenanta wygasają przy usunięciu danych: zip NULL, `expires_at` teraz. Tenant: przeżywa go (brak klucza obcego; sekwencja usuwania buduje eksport przed usunięciem wiersza tenanta, a zip pozostaje do pobrania 24 godziny po nim) |
| 23 | `users` | administrator | Klient; wyszukiwany po adresie e-mail. Własne logowanie klienta, nie osoba, której dane dotyczą w sensie rejestru | Tak długo, jak tenant | Zachowanie. Tenant: kaskada |
| 24 | `sessions` | administrator | Klient. Zawiera `ip_prefix` i `user_agent` klienta | Stały wiek liczony od `expires_at`; rejestr nie podaje liczby; usunięcie w chwili wygaśnięcia. Zadanie `identity_retention` | Zachowanie. Tenant: kaskada |
| 25 | `dpa_acceptances` | administrator | Klient. Zapis, że klient przyjął DPA | Tak długo, jak tenant | Zachowanie. Tenant: kaskada |
| 26 | `audit_events` | administrator | Klient. `changes` zawiera tylko nazwy pól i wartości niebędące danymi osobowymi | Stały wiek: 730 dni od `occurred_at`. Zadanie `registry_retention` | Zachowanie. Tenant: jawne usunięcie w sekwencji usuwania (partia czyszcząca) |
| 27 | `social_accounts` | administrator | Klient; wyszukiwany po identyfikatorze użytkownika Instagrama, handle. Własne połączenie klienta, usuwane przez `connect.Remove` | Tak długo, jak tenant | Zachowanie. Tenant: kaskada |
| 28 | `removed_instagram_accounts` | administrator | Klient; wyszukiwany po identyfikatorze użytkownika Instagrama. Własne usunięte połączenie klienta | Stały wiek: 90 dni od `unsubscribed_at`. Zadanie `webhook_retention`. Wiersz bez znacznika nie ma wieku i pozostaje. Do udanego wypisania pozostaje, także po żądaniu usunięcia danych od Meta. Wiersz znika razem z tenantem albo przy nowym połączeniu tego id przez dowolnego tenanta | Zachowanie. Usunięcie danych osoby przez tenanta i usunięcie jego konta odczytują go, aby znaleźć dostarczenia webhooków, które wskazują id i przychodzą po usunięciu. Tenant: kaskada |
| 29 | `tenant_brands` | administrator | Własny adres pocztowy i adres do kontaktu klienta | Tak długo, jak tenant | Zachowanie. Tenant: kaskada |
| 30 | `tenants` | administrator | Klient. Korzeń; jego usunięcie uruchamia kaskadę | Tak długo, jak tenant | Zachowanie. Tenant: kaskada |
| 31 | `sending_domains` | administrator | Klient. Usuwana przez `sendingdomain.Remove`, które usuwa też domenę u dostawcy | Tak długo, jak tenant | Zachowanie. Tenant: kaskada |
| 32 | `media_images` | administrator | Klient: logo i obrazy tenanta | Tak długo, jak tenant; zachowane, dopóki tenant istnieje, ponieważ wysłana już poczta odwołuje się do nich przez id | Zachowanie. Tenant: kaskada |
| 33 | `data_deletion_requests` | administrator | Klient. Dowód usunięcia, o które poprosiła Meta; brak klucza tenanta | Stały wiek: 365 dni od `received_at` (12 miesięcy), aby link ze statusem działał, gdy Meta może pytać; nigdy nie czyszczone, dopóki mają stan received. Zadanie `registry_retention` | Zachowanie. Tenant: przeżywa go |
| 34 | `campaigns` | administrator | Własna konfiguracja klienta; wyszukiwana po handle | Tak długo, jak tenant | Zachowanie. `erase --handle` zgłasza, ile kampanii wskazuje handle w `ignore_handles`. Tenant: kaskada |
| 35 | `campaign_variants` | brak danych osobowych | Kopia tenanta; eksportowana w `campaigns.json` | Brak wskazania | Brak wskazania. Tenant: kaskada |
| 36 | `campaign_links` | brak danych osobowych | Adresy URL napisane przez tenanta; eksportowane w `campaigns.json` | Brak wskazania | Brak wskazania. Tenant: kaskada |
| 37 | `email_templates` | brak danych osobowych | Treść tenanta, bez osób | Brak wskazania | Brak wskazania. Tenant: kaskada |
| 38 | `broadcasts` | brak danych osobowych | Treść tenanta | Brak wskazania | Brak wskazania. Tenant: kaskada |
| 39 | `links` | brak danych osobowych | Adresy URL napisane przez tenanta | Brak wskazania | Brak wskazania. Tenant: kaskada |
| 40 | `lists` | brak danych osobowych | Nazwy, które tenant nadał swoim listom; kto jest na liście, wskazuje `list_members` | Brak wskazania | Brak wskazania. Tenant: kaskada |
| 41 | `tags` | brak danych osobowych | Nazwy, które tenant nadał swoim tagom; kto nosi tag, wskazuje `contact_tags` | Brak wskazania | Brak wskazania. Tenant: kaskada |
| 42 | `usage_events` | brak danych osobowych | Liczby | Brak wskazania | Brak wskazania. Tenant: kaskada |
| 43 | `account_polls` | brak danych osobowych | Kursory i liczniki; znika razem ze swoim kontem | Brak wskazania | Brak wskazania. Tenant: kaskada |
| 44 | `outbox_skips` | brak danych osobowych | Liczby na godzinę | Stały wiek: 90 dni od `hour`. Zadanie `pipeline_retention` | Brak wskazania. Tenant: jawne usunięcie w sekwencji usuwania (partia czyszcząca) |
| 45 | `health_transitions` | brak danych osobowych | Stany i kody Meta; tylko historia, żadna decyzja nie czyta jej po fakcie | Stały wiek: 730 dni od `at`. Zadanie `registry_retention` | Brak wskazania. Tenant: jawne usunięcie w sekwencji usuwania (partia czyszcząca) |
| 46 | `meta_calls` | brak danych osobowych | Klasa, status i kody; ścieżka zawiera identyfikatory obiektów Meta, nie osoby | Stały wiek: 14 dni od `at`. Zadanie `meta_calls_retention` | Brak wskazania. Tenant: jawne usunięcie w sekwencji usuwania (partia czyszcząca) |
| 47 | `rate_limit_buckets` | brak danych osobowych | Liczby tokenów, bez osób. Usunięcie zachowuje wiersze konta, dopóki trwa jego okno ochrony, więc ponowne połączenie tego samego konta Instagrama je przejmuje. Wiersze dla całej aplikacji nie mają konta i pozostają | Stały wiek: 90 dni od `removed_instagram_accounts.removed_at`. Zadanie `meta_calls_retention` | Brak wskazania. Tenant: brak klucza tenanta, usuwa je zegar okresu przechowywania |
| 48 | `circuit_breakers` | brak danych osobowych | Stan wyłącznika, bez osób. Usunięcie zachowuje wiersz konta, dopóki trwa jego okno ochrony, więc ponowne połączenie tego samego konta Instagrama go przejmuje. Wiersz globalny nie ma konta i pozostaje | Stały wiek: 90 dni od `removed_instagram_accounts.removed_at`. Zadanie `meta_calls_retention` | Brak wskazania. Tenant: brak klucza tenanta, usuwa go zegar okresu przechowywania |
| 49 | `settings` | brak danych osobowych | Klucze przełączników; `updated_by` to nazwa operatora | Brak wskazania | Brak wskazania. Tenant: jawne usunięcie w sekwencji usuwania (partia czyszcząca). Klucze tenanta i zawieszenia usuwa partia czyszcząca, klucze konta usuwa `connect.Remove` |
| 50 | `oauth_state_nonces` | brak danych osobowych | Losowe wartości nonce, bez klucza tenanta | Brak wskazania | Brak wskazania. Tenant: przeżywa go |
| 51 | `dpa_versions` | brak danych osobowych | Teksty DPA, wspólne dla każdego tenanta | Brak wskazania | Brak wskazania. Tenant: przeżywa go |
| 52 | `subprocessors` | brak danych osobowych | Nazwy firm, wspólne dla każdego tenanta | Brak wskazania | Brak wskazania. Tenant: przeżywa go |
| 53 | `sending_domain_tombstones` | brak danych osobowych | Domena firmowa oraz albo identyfikator dostawcy, albo czasy wiersza w trakcie tworzenia, którego żądanie utworzenia mogło dotrzeć do dostawcy, a odpowiedź zginęła; zadanie i uzgodnienie usuwające domenę dostawcy czytają go po zniknięciu tenanta | Brak wskazania | Brak wskazania. Tenant: przeżywa go |
| 54 | `tenant_slug_tombstones` | brak danych osobowych | SHA-256 z identyfikatora nadawcy (slug) usuniętego tenanta i czas, bez klucza tenanta. Rejestr stwierdza, że skrót jest pseudonimowy, a nie anonimowy: slug to złożona lokalna część adresu logowania, a lista popularnych imion go odtwarza | Zachowany bezterminowo (brak pola okresu przechowywania) | Brak wskazania. Tenant: przeżywa go |
| 55 | `account_deletions` | brak danych osobowych | Id tenanta, kroki i czasy: dowód usunięcia, bez klucza tenanta | Stały wiek: 365 dni od `finished_at` (12 miesięcy po zakończeniu). Zadanie `registry_retention` | Brak wskazania. Tenant: przeżywa go |
| 56 | `plans` | brak danych osobowych | Wspólne dane początkowe, katalog, względem którego rozstrzygany jest każdy tenant | Brak wskazania | Brak wskazania. Tenant: przeżywa go |
| 57 | `addon_blocks` | brak danych osobowych | Wspólne dane początkowe, katalog, względem którego rozstrzygany jest każdy tenant | Brak wskazania | Brak wskazania. Tenant: przeżywa go |
| 58 | `plan_addons` | administrator | Klient. Dodatkowe bloki leadów kupione przez klienta | Tak długo, jak tenant | Kaskada przez `tenant_id`. Tenant: kaskada |
| 59 | `subscriptions` | administrator | Klient. Nasza kopia subskrypcji klienta; sam klient Stripe jest zachowany w Stripe, ponieważ jego faktury są dokumentacją podatkową | Tak długo, jak tenant | Kaskada przez `tenant_id`. Tenant: kaskada |
| 60 | `stripe_events` | administrator | Klient. Dane Stripe zawierają adres e-mail i identyfikator podatkowy klienta | Stały wiek: 90 dni od `received_at`. Zadanie `stripe_events_retention` | Kaskada przez `tenant_id`. Tenant: kaskada |
| 61 | `river_*` | brak danych osobowych | Własne tabele River. Argumenty zadania (`to` w `template_test_email`) znikają w partii czyszczącej sekwencji usuwania, która usuwa zadania tenanta w każdym stanie poza running. `account_unsubscribe` nie niesie id tenanta i celowo go przeżywa: jego argumenty zawierają id Instagrama i zapieczętowany token, gdy czeka na wysłanie wypisania potrzebnego Meta, co trwa tak długo, jak przełącznik lub wyłącznik odrzuca wywołanie. River zachowuje zakończony wiersz z tymi argumentami przez 24 godziny po zakończeniu i 7 dni po odrzuceniu (domyślny okres przechowywania River, który dotyczy każdego rodzaju zadania jednakowo) | Brak wskazania | Brak wskazania. Tenant: przeżywa go |

**Kontrola liczby.** Wpisy znalezione w rejestrze (slice `Registry` w `internal/privacy/registry.go`): 61. Wiersze w tabeli Części C: 61. Obie liczby się zgadzają. 61. wpis, `river_*`, nazywa grupę tabel z użyciem znaku wieloznacznego i jest liczony jako jeden wpis.

---

## Część D. Punkty otwarte

### D.1 Miejsca oznaczone `[DO SPRAWDZENIA]` lub `[DO UZUPEŁNIENIA]` w tym rejestrze

1. Część A.1 (a) i Część B.1 (a): `[DO UZUPEŁNIENIA: nazwa i dane kontaktowe operatora, przechowywane poza repozytorium]` (dwa miejsca).
2. Część A.1 (d): podmiot Stripe, role dla każdej usługi, kraje i podstawy przekazań.
3. Część A.1 (d): korzystanie z księgowych lub innych doradców.
4. Część A.1 (e): Resend i AWS (dane w USA, umowa, moduł SCC, dalsi podprzetwarzający, środki dodatkowe, właściwy podmiot AWS, dalsze przekazania).
5. Część A.1 (e): Cloudflare (umowa, podstawa przekazania, kraje przetwarzania, zdalny dostęp, okres przechowywania, DPF).
6. Część A.1 (e): skrzynka OVHcloud (kraj, kopie, dostęp, przekazania poza EOG).
7. Część A.1 (f): ustawienia produkcyjne i maksymalne opóźnienia zadań usuwających.
8. Część A.1 (g): środki produkcyjne, szyfrowanie dysków i kopii zapasowych, odtwarzanie, monitoring.
9. Część A.2, wstęp: zatwierdzenie przyporządkowania podstaw, testów równowagi i przepisów szczególnych uzasadniających podstawę c.
10. A9: maksymalny okres przechowywania pozostałych danych po usunięciu domeny (`sending_domain_tombstones`).
11. A11: przepisy, okresy i punkty początkowe dla faktur, korekt, płatności i zachowanych danych Stripe.
12. A13: okresy i kryteria dla korespondencji, żądań, skarg i roszczeń oraz usuwanie ze skrzynki OVHcloud.
13. A14: maksymalny okres przechowywania i minimalizacja logów.
14. A17: proporcjonalność i maksymalny okres przechowywania skrótu identyfikatora nadawcy.
15. Część B.1 (a): czy rejestr musi zawierać nazwę i dane kontaktowe każdego administratora i gdzie.

### D.2 Rozbieżności między rejestrem (registry) a projektami dokumentów prawnych

1. **Klasa `broadcasts`, `email_templates`, `campaign_variants`, `campaign_links`, `links`, `lists`, `tags`.** `internal/privacy/registry.go`: klasa `none`, bez osób. `dpa-en.html` (Załącznik 1, rodzaje danych): treść kampanii, wiadomości, stron zbierania danych i obrazów to dane powierzone "w zakresie, w jakim zawiera dane osobowe". Ten rejestr wymienia te tabele w Części B (B7, B8) i w Części C jako "brak danych osobowych". Wymaga decyzji.
2. **Rola `media_images`.** Rejestr: klasa `customer` (logo i obrazy tenanta, więc IRIS jako administrator). `dpa-en.html` Załącznik 1: obrazy dostarczone przez administratora to dane powierzone osób na nich pokazanych, a `privacy-en.html` sekcja 3 stwierdza, że dane innych osób na obrazach są powierzone. Ten rejestr pokazuje `media_images` w Części A (A10), w Części B (B8) i jako administratora w Części C.
3. **Rola `campaigns`.** Rejestr: klasa `customer`, "własna konfiguracja klienta". `dpa-en.html` sekcja 4: ustawienia kampanii, słowa kluczowe i tekst odpowiedzi są poleceniami administratora, a `privacy-en.html` sekcja 3 podaje podstawę b dla własnych danych klienta. To nie jest sprzeczność faktów, ale oba dokumenty nie stosują tego samego podziału.
4. **`tenant_slug_tombstones`.** Klasa rejestru `none`, choć jego własne uzasadnienie stwierdza, że skrót jest "pseudonimowy, a nie anonimowy". `privacy-en.html` sekcja 3 używa tego samego słowa, "pseudonimowy", i przechowuje go bezterminowo. Klasa `none` nie jest z tym zgodna.
5. **`river_*`.** Klasa rejestru `none`, choć jego własne uzasadnienie stwierdza, że argumenty `account_unsubscribe` zawierają id Instagrama i zapieczętowany token oraz że pozostają 24 godziny po zakończeniu lub 7 dni po odrzuceniu. `privacy-en.html` sekcja 7 i `dpa-en.html` sekcja 12 wymieniają oczekujące zadania jako wyjątek od usunięcia, z `[DO SPRAWDZENIA]` przy ich maksymalnym czasie trwania.
6. **`rate_limit_buckets` i `circuit_breakers`.** Rejestr: 90 dni od `removed_instagram_accounts.removed_at`; usunięcie tenanta to "duration" (zegar okresu przechowywania, a nie usunięcie konta). `privacy-en.html` sekcja 3 (liczniki techniczne): "dane powiązane z kontem są usuwane razem z kontem" i nie podaje okresu dla tych dwóch tabel.
7. **`suppressions`: podstawa przechowywania.** Rejestr podaje podstawę (RODO art. 17 ust. 3 lit. b i art. 21) oraz przechowywanie "bezterminowo". `dpa-en.html` Załącznik 1 oznacza "podstawę przechowywania i proporcjonalność, odwołania do art. 17 ust. 3 lit. b i art. 21 RODO" jako `[DO SPRAWDZENIA]` i stwierdza, że lista jest usuwana razem z kontem. Rejestr także usuwa ją z tenantem kaskadowo, więc fakty się zgadzają, ale podstawa jest niezweryfikowana w projektach dokumentów prawnych.
8. **`suppressions`: co pozostaje po usunięciu danych osoby.** Rejestr: `contact_id` ustawione na NULL i diagnostyka ''. `privacy-en.html` sekcja 4 i `dpa-en.html` Załącznik 1 stwierdzają też, że identyfikator wysyłki masowej (`broadcast_id`) może pozostać. Rejestr tego nie wspomina.
9. **`contacts`: zegar 90 dni.** Rejestr: największa z wartości `updated_at`, `lead_conversations.updated_at` i `automation_executions.evaluated_at`. `privacy-en.html` sekcja 4 i `dpa-en.html` Załącznik 1: od ostatniego komentarza lub wiadomości, z uwzględnieniem późniejszych aktualizacji kontaktu lub rozmowy. Żaden z projektów nie wymienia wykonań automatyzacji.
10. **`contacts`: przesłanki wstrzymujące 90 dni.** Rejestr: tag, członkostwo w aktywnej liście, zgoda, dostarczenie, wykluczenie, wiersz odbiorcy wysyłki masowej. Projekty dodają listę w 10-sekundowym oknie przywracania, adres lub weryfikację w rozmowie, oczekiwanie na kod oraz ważny niewykorzystany link zbierania danych. Komentarz w rejestrze ich nie wymienia.
11. **Sesje.** Rejestr: `sessions` i `operator_sessions` są usuwane w chwili `expires_at`, bez liczby. `privacy-en.html` sekcja 3 podaje domyślne maksimum 7 dni dla sesji klienta oraz maksimum 8 godzin i 60 minut bezczynności dla sesji operatora. Tych liczb nie ma w rejestrze.
12. **Długość roku.** Komentarz w rejestrze: rok to 365 dni, a 24 miesiące to 730 dni. Projekty mówią "12 miesięcy" i "24 miesiące". Zgodność wartości: `audit_events`, `operator_events` i `health_transitions` 730 dni (24 miesiące); `account_deletions` i `data_deletion_requests` 365 dni (12 miesięcy).
13. **Przetwarzanie bez tabeli w rejestrze.** Korespondencja ze wsparciem (A13) oraz logi żądań i błędów (A14) są przetwarzaniem w `privacy-en.html` i `dpa-en.html` (rotacja logów Dockera), ale żaden wpis rejestru ich nie wymienia, ponieważ nie są tabelami bazy danych. Ich okres przechowywania jest w projektach oznaczony `[DO SPRAWDZENIA]`.
14. **Klasa rejestru `subject` dla tabel administratora.** `sign_in_tokens`, `invitations` i `account_exports` mają klasę `subject` (osoba niebędąca klientem). Według `privacy-en.html` IRIS jest ich administratorem. Ten rejestr przypisuje w Części C rolę "administrator". `account_exports` zawiera w zipie dane powierzone i jest też wymieniona w B9.

Punkty od 1 do 6 oraz 14 zmieniają to, co rejestr mówi o rolach. Wymagają decyzji właściciela lub prawnika, zanim rejestr będzie ostateczny.
