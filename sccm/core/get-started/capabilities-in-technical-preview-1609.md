---
title: Funkcje w wersji zapoznawczej Technical Preview 1609 programu Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview programu System Center Configuration Manager, wersja 1609."
ms.custom: na
ms.date: 01/23/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: article
ms.assetid: e2a59116-b2e5-4dd2-90eb-0b8a5eb50b56
caps.latest.revision: "2"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 89a41c8a3137d0e54011ddf9a1d9b4894ecb7df8
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="capabilities-in-technical-preview-1609-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1609 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*



W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1609. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview.      Przed zainstalowaniem tej wersji technical Preview, przejrzyj temat wprowadzający [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.    

**Znane problemy w tej wersji Technical Preview:**  
*  Podczas aktualizacji do wersji zapoznawczej Technical Preview programu Configuration Manager 1609 jakiekolwiek zasady uaktualniania wersji, które zostały wdrożone zostaną usunięte. Aby nadal używać tych zasad, należy ponownie utworzyć i wdrożyć je.


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

## <a name="improvements-to-endpoint-protection"></a>Ulepszenia dotyczące programu Endpoint Protection
Poprawy ustawień zasad ochrony przed złośliwym kodem programu Endpoint Protection — można teraz określić poziom, jaką Usługa ochrony programu Endpoint Protection chmury zablokuje podejrzanych plików. Nowe ustawienie umożliwia administratorom określenie "ryzykowne" komputery oparte na wysoki ilości złośliwego oprogramowania, napotkanych.

## <a name="increased-number-of-enrolled-devices"></a>Zwiększenie liczby zarejestrowanych urządzeń
Administratorzy mogą teraz włączyć użytkownikom na rejestrację maksymalnie 15 urządzeń w hybrydowego zarządzania urządzeniami przenośnymi za pomocą usługi Intune. Limit został wcześniej 5 urządzeń dla każdego użytkownika.

## <a name="additional-apple-dep-settings"></a>Dodatkowe ustawienia programu DEP firmy Apple

Administratorzy mogą teraz skonfiguruj następujące ustawienia programu Apple Device Enrollment Program (DEP) w profilu DEP dla systemu iOS i Mac urządzenia:
- **Touch ID**
- **Powiększenie**
- **Siri**

U możliwia firmy Apple Asystent ustawień wyświetla monit dotyczący tej usługi podczas aktywacji urządzenia.

## <a name="integration-with-upgrade-analytics"></a>Integracja z uaktualnienia analityka

Uaktualnienia analytics zapewnia do oceny i analizowania gotowości urządzenia i zgodności z systemem Windows 10 umożliwiają łatwiejsze i bardziej płynny uaktualnienia. Dzięki integracji usługi Analytics uaktualniania z programu Configuration Manager można uzyskać dostęp do danych zgodności uaktualnienia w konsoli administracyjnej programu Configuration Manager i następnie z listy urządzeń docelowych urządzeń do uaktualnienia lub korygowania.

Więcej o uaktualnienie analityka w [wprowadzenie uaktualnienia Analytics](https://technet.microsoft.com/itpro/windows/deploy/upgrade-analytics-get-started).

## <a name="native-connection-types-for-windows-10-vpn-hybrid-profiles"></a>Profile sieci VPN hybrydowego typy połączeń natywnej dla systemu Windows 10

Korzystając z programu Configuration Manager z usługą Intune, możesz teraz utworzyć profile sieci VPN systemu Windows 10 z Automatic firmy Microsoft, IKEv2, PPTP, L2TP połączenia typów i w konsoli programu Configuration Manager, bez przy użyciu identyfikatora OMA-URI.

## <a name="enhancements-to-windows-store-for-business-integration-with-configuration-manager"></a>Rozszerzenia do Sklepu Windows dla firm integracji z programem Configuration Manager

W tej wersji Zaktualizowaliśmy [Sklepu Windows dla firm integracji](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business) o te nowe funkcje:

**Aktualizacja:** W bieżącej wersji technical preview funkcja natychmiastową synchronizację nie działa.

- Wcześniej można wdrażać tylko bezpłatnych aplikacji ze Sklepu Windows dla firm. Configuration Manager teraz również obsługują wdrażanie płatności online licencjonowane aplikacje (tylko urządzenia zarejestrowane w usłudze Intune).
- Teraz można zainicjować natychmiastową synchronizację między Sklep Windows dla firm i programie Configuration Manager.
- Można również zmodyfikować klucza tajnego klienta, które zostały uzyskane z usługi Azure Active Directory

### <a name="try-it-out"></a>Wypróbuj

#### <a name="purchase-and-sync-a-paid-online-licensed-app"></a>Kup i synchronizacji płatnej aplikacji licencjonowanych online

1. Kup online płatną licencjonowanych aplikacji ze Sklepu Windows dla firm.
2. W **administracji** obszaru roboczego w konsoli programu Configuration Manager, kliknij przycisk **usługi w chmurze** > **aktualizacje i obsługa** > **Sklep Windows dla firm**.
3. Na **Home** karcie **synchronizacji** kliknij przycisk **Synchronizuj teraz**.
4. Niedługo potem zakupiono aplikacja pojawi się w **informacji o licencji dla aplikacji ze sklepu** węzła **Zarządzanie aplikacjami** obszaru roboczego.

#### <a name="create-and-deploy-a-configuration-manager-application-from-the-synchronized-app-data"></a>Tworzenie i wdrażanie aplikacji programu Configuration Manager z danych zsynchronizowanych aplikacji

Procedura tworzenia i wdrażania aplikacji programu Configuration Manager z magazynu płatnych aplikacji jest taka sama jak w przypadku tworzenia aplikacji z bezpłatną aplikację. Zobacz sekcję **tworzenie i wdrażanie aplikacji programu Configuration Manager w Sklepie Windows dla aplikacji biznesowych** w [Zarządzanie aplikacjami ze Sklepu Windows dla firm z System Center Configuration Manager](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).


#### <a name="modify-the-client-secret-key-from-azure-active-directory"></a>Modyfikowanie klucza tajnego klienta z usługi Azure Active Directory

1. W **administracji** obszaru roboczego w konsoli programu Configuration Manager, kliknij przycisk **usługi w chmurze** > **aktualizacje i obsługa** > **Sklep Windows dla firm**.
2. Wybierz konto firmowe w Sklepie Windows, a następnie kliknij przycisk **właściwości**.
3. W **Sklep Windows dla firm właściwości konta** okna dialogowego wprowadź nowy klucz w **klucza tajnego klienta** pola, a następnie kliknij przycisk **Sprawdź**. Po zweryfikowaniu kliknij **Zastosuj**, a następnie zamknij okno dialogowe.


## <a name="new-compliance-settings-for-configuration-items"></a>Nowe ustawienia zgodności dla elementów konfiguracji

Dodaliśmy wiele nowych ustawień, które można używać we wszystkich elementach konfiguracji dla różnych platform urządzeń.
Są to ustawienia, które wcześniej były dostępne w programie Microsoft Intune w konfiguracji autonomicznej i są teraz dostępne podczas korzystania z usługi Intune z programem Configuration Manager.
Jeśli potrzebujesz pomocy z dowolnymi spośród tych ustawień, otwórz [Zarządzanie ustawieniami i funkcjami na urządzeniach przy użyciu zasad usługi Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) , a następnie wybierz podrzędny ustawień dla platformy ma.


### <a name="new-settings-for-android-devices"></a>Nowe ustawienia dla urządzeń z systemem Android

#### <a name="password-settings"></a>Ustawienia hasła

- **Pamiętaj historię haseł**
- **Zezwalaj na odcisk palca odblokowania**

#### <a name="security-settings"></a>Ustawienia zabezpieczeń

- **Wymagaj szyfrowania na kartach pamięci**
- **Zezwalaj na przechwytywanie ekranu**
- **Zezwalaj na przesyłanie danych diagnostycznych**

#### <a name="browser-settings"></a>Ustawienia przeglądarki

- **Zezwalaj na używanie przeglądarki sieci web**
- **Zezwalaj na automatyczne uzupełnianie**
- **Zezwalaj na blokowanie wyskakujących okienek**
- **Zezwalaj na pliki cookie**
- **Zezwalaj na wykonywanie aktywnych skryptów**

#### <a name="app-settings"></a>Ustawienia aplikacji

- **Zezwalaj na sklep Google Play**

#### <a name="device-capability-settings"></a>Ustawienia możliwości urządzenia

- **Zezwalaj na używanie magazynu wymiennego**
- **Zezwalaj na tethering Wi-Fi**
- **Zezwalaj na używanie funkcji geolokalizacji**
- **Zezwalaj na komunikację NFC**
- **Zezwalaj na połączenia Bluetooth**
- **Zezwalaj na Roaming połączeń głosowych**
- **Zezwalaj na roaming danych**
- **Zezwalaj na obsługę wiadomości SMS/MMS**
- **Zezwalaj na Asystenta głosowego**
- **Zezwalaj na wybieranie głosowe**
- **Zezwalaj na kopiowanie i wklejanie**


### <a name="new-settings-for-ios-devices"></a>Nowe ustawienia dla urządzeń z systemem iOS

#### <a name="password-settings"></a>Ustawienia hasła

- **Liczba znaków złożonych w haśle**
- **Zezwalaj na proste hasła**
- **Liczba minut braku aktywności, zanim będzie wymagane hasło**
- **Pamiętaj historię haseł**

### <a name="new-settings-for-mac-os-x-devices"></a>Nowe ustawienia dla urządzeń z systemem Mac OS X

#### <a name="password-settings"></a>Ustawienia hasła

- **Liczba znaków złożonych w haśle**
- **Zezwalaj na proste hasła**
- **Pamiętaj historię haseł**
- **Liczba minut braku aktywności przed uaktywnieniem wygaszacza ekranu**

### <a name="new-settings-for-windows-10-desktop-and-mobile-devices"></a>Nowe ustawienia dla urządzeń z systemem Windows 10 Desktop i Mobile

#### <a name="password-settings"></a>Ustawienia hasła

- **Minimalna liczba zestawów znaków**
- **Pamiętaj historię haseł**
- **Wymagaj hasła, gdy urządzenie powraca ze stanu bezczynności**

#### <a name="security-settings"></a>Ustawienia zabezpieczeń

- **Wymagaj szyfrowania na urządzeniu przenośnym**
- **Zezwalaj na ręczne Wyrejestrowanie**

#### <a name="device-capability-settings"></a>Ustawienia możliwości urządzenia

- **Zezwalaj na połączenia VPN przez sieć komórkową**
- **Zezwalaj na roaming VPN przez sieć komórkową**
- **Zezwalaj na resetowanie telefonu**
- **Zezwalaj na połączenie USB**
- **Zezwalaj na funkcję Cortana**
- **Zezwalaj na powiadomienia Centrum akcji**

### <a name="new-settings-for-windows-10-team-devices"></a>Nowe ustawienia dla urządzeń z systemem Windows 10 Team

#### <a name="device-settings"></a>Ustawienia urządzenia

- **Włącz usługę Azure Operational Insights**
- **Włącz projekcję bezprzewodową Miracast**
- **Wybierz informacje o spotkaniu wyświetlane na ekranie powitalnym**
- **Adres URL obrazu tła ekranu blokady**


### <a name="new-settings-for-windows-81-devices"></a>Nowe ustawienia dla urządzeń Windows 8.1

#### <a name="applicability-settings"></a>Ustawienia zastosowania

- **Zastosuj wszystkie konfiguracje dla systemu Windows 10**

#### <a name="password-settings"></a>Ustawienia hasła

- **Wymagany typ hasła**
- **Minimalna liczba zestawów znaków**
- **Minimalna długość hasła**
- **Liczba dopuszczalnych nieudanych logowań przed usunięciem zawartości urządzenia**
- **Liczba minut braku aktywności przed wyłączeniem ekranu**
- **Wygaśnięcie hasła (dni)**
- **Pamiętaj historię haseł**
- **Zapobiegaj ponownemu używaniu poprzednich haseł**
- **Zezwalaj na hasło obrazkowe i numer PIN**

#### <a name="browser-settings"></a>Ustawienia przeglądarki

- **Zezwalaj na automatyczne wykrywanie sieci intranet**


### <a name="new-settings-for-windows-phone-81-devices"></a>Nowe ustawienia dla urządzeń Windows Phone 8.1

#### <a name="applicability-settings"></a>Ustawienia zastosowania

- **Zastosuj wszystkie konfiguracje dla systemu Windows 10**

#### <a name="password-settings"></a>Ustawienia hasła

- **Minimalna liczba zestawów znaków**
- **Zezwalaj na proste hasła**
- **Pamiętaj historię haseł**

#### <a name="device-capability-settings"></a>Ustawienia możliwości urządzenia

- **Zezwalaj na automatyczne łączenie z bezpłatnymi punktami HotSpot Wi-Fi**


## <a name="improvements-for-boundary-groups"></a>Ulepszenia grup granic
Tej wersji zapoznawczej wprowadzono istotne zmiany do grupy granic oraz ich współdziałaniu z punktami dystrybucji. Te zmiany uprości projektowania infrastruktury zawartości podczas zapewniając większą kontrolę nad jak i kiedy klienci powrotu do wyszukiwania dystrybucji dodatkowe punkty jako lokalizacji źródła zawartości. W tym zarówno lokalnie, jak i punkty dystrybucji w chmurze.

Te ulepszenia zastąpienie pojęcia i zachowania, może być znasz już dziś (np. Konfigurowanie punktów dystrybucji jako dużą lub małą) i zastępuje je nowy model, który powinien być łatwiejsze Konfiguracja i konserwacja. Te zmiany są również przygotowuje przyszłe zmiany, które poprawią inne role systemu lokacji, które można powiązać do grup granic.  

Podczas uaktualniania do 1609 uaktualnienia konwertuje bieżącej konfiguracji grupy granic do nowego modelu tak, aby te zmiany nie przeszkadzać konfiguracje dystrybucji zawartości (zobacz [aktualizowanie istniejących grup granic do nowego modelu](/sccm/core/get-started/capabilities-in-technical-preview-1609#bkmk_update)).

W poniższych sekcjach opisano zmiany wprowadzone w tej wersji zapoznawczej, jak działa nowy model i czego można oczekiwać podczas uaktualniania lokacji, która ma już skonfigurowanych grup granic.



### <a name="changes-in-ui-and-behavior-for-boundary-groups-and-content-locations"></a>Zmiany interfejsu użytkownika oraz zachowanie dla grupy granic i lokalizacji zawartości
Poniżej przedstawiono zmiany klucza do grupy granic i jak klienci znajdują zawartości. Wiele z tych zmian i pojęcia współdziałają ze sobą.
-   **Konfiguracje dla Fast lub wolno zostaną usunięte:** Można już konfigurować poszczególne punkty dystrybucji można dużą lub małą.  Zamiast tego jest traktowany każdego systemu lokacji skojarzone z grupą granic takie same. Z powodu tej zmiany **odwołania** na karcie właściwości grupy granic już nie obsługuje konfiguracji Fast lub niska.
-   **Nową grupę granic domyślne w każdej lokacji:**  Każda lokacja główna ma nowej grupy granic domyślny o nazwie ***domyślna--grupy granic lokacji\<kod lokacji >***.  Gdy klient nie jest w lokalizacji sieciowej, która jest przypisana do grupy granic, klient użyje systemy lokacji skojarzone z domyślnej grupy z przypisanej lokacji. Zaplanuj użycie tej grupy granic w zastępstwie koncepcję rezerwowej lokalizacji zawartości.    
 -  **"Zezwalaj na lokalizacji rezerwowej dla zawartości"** zostaną usunięte: Nie jest już jawnie skonfigurować punkt dystrybucji do użycia jako metody rezerwowej i opcji, aby ustawić to są usuwane z interfejsu użytkownika.

    Ponadto wynik ustawienie **Zezwalaj klientom na użycie rezerwowej lokalizacji źródła zawartości** w ramach wdrożenia zmienił się typ dla aplikacji. To ustawienie w typie wdrożenia teraz umożliwia klienta do używania domyślnej grupy granic lokacji jako lokalizacji źródła zawartości.

 -  **Relacje grupy granic:** Każda grupa granic może odnosić się do co najmniej jednej grupy granic dodatkowe. Łącza te tworzą relacje, które są skonfigurowane na karcie właściwości nowej grupy granic o nazwie **relacje**:
    -   Każdą grupą granic, klient jest bezpośrednio z którym skojarzony jest nazywany **bieżącego** grupy granic.  
    -   Żadną inną grupą granic klient może korzystać z powodu skojarzenia między tego klienta *bieżącego* nosi nazwę grupy granic i innej grupy **sąsiada** grupy granic.
    -  Znajduje się na **relacje** kartę Dodaj grupy granic, które mogą być używane jako *sąsiada* grupy granic. Można również skonfigurować czas w minutach, które określa, kiedy klient, który nie może odnaleźć zawartości z punktu dystrybucji w *bieżącego* grupy rozpocznie się wyszukiwanie lokalizacji zawartości od tych *sąsiada* grup granic.

        Podczas dodawania lub zmienić konfigurację grupy granic, konieczne będzie opcja powrotu do tej grupy granic określone z bieżącej grupy, który jest konfigurowany bloku.

    Aby korzystać z nowej konfiguracji, zdefiniować jawnej skojarzenia (linki) z jednej grupy granic i skonfiguruj wszystkie punkty dystrybucji w tej grupie skojarzony z tym samym czasie w minutach. Określa czas, należy skonfigurować, gdy klient, który nie uda się znaleźć źródła zawartości z jego *bieżącego* grupy granic można rozpocząć wyszukiwanie źródła zawartości z tej grupy granic sąsiedniego.

    Oprócz grup granic, które jawnie skonfigurować każdą grupą granic ma domniemanych łącze do domyślnej grupy granic lokacji. To łącze staje się aktywny po 120 minut po tym czasie domyślnej grupy granic lokacji staje się sąsiada grupy granic, która umożliwia klientom korzystanie z punktów dystrybucji skojarzone z daną grupą granic jako lokalizacji źródła zawartości.

    To zachowanie zastępuje, co zostało wcześniej określone jako metody rezerwowej dla zawartości.  Można zastąpić to domyślne zachowanie 120 minut, kojarząc jawnie domyślnej grupy granic lokacji do *bieżącego* grupy i ustawienie określony czas w minutach lub blokuje powrotu całkowicie uniemożliwić korzystanie z niego.


-   **Klienci próbują pobrać zawartości z poszczególnych punktów dystrybucji przez maksymalnie 2 minuty:** Gdy klient wyszukuje lokalizacji źródła zawartości, próbuje uzyskiwać dostęp do poszczególnych punktów dystrybucji dla dwóch minut przed podjęciem próby następnie innego punktu dystrybucji. Jest to zmiana z poprzednich wersji, której klienci nastąpiła próba połączenia do punktu dystrybucji przez maksymalnie 2 godziny.

    - Pierwszy punkt dystrybucji, który klient próbuje użyć jest wybierane losowo z puli dostępnych punktów dystrybucji na komputerze klienckim *bieżącego* grupy granic (lub grupy).

    - Po dwóch minut Jeśli klient nie odnalazł zawartości, go przełącza się do nowego punktu dystrybucji i próbuje pobrać zawartość z tego serwera. Ten proces jest powtarzany co dwie minuty, aż do klienta znajduje się zawartość lub osiągnie ostatni serwer w jego puli.

    - Jeśli klient nie może znaleźć lokalizację poprawne źródło zawartości z jego *bieżącego* puli przed okresem powrotu do *sąsiada* osiągnięciu grupy granic, klient następnie dodaje punktów dystrybucji niż *sąsiada* grupy w celu jego bieżącej listy, a następnie będzie wyszukać rozwiniętej grupy lokalizacje źródłowe zawiera punkty dystrybucji z obu tych grup granic.

        > [!TIP]  
        > Podczas tworzenia wyraźnego związku z bieżącej grupy granic do domyślnej grupy granic lokacji i rezerwowy czasu, która jest mniejsza niż rezerwowy czasu dla łącza do grupy granic sąsiada, klienci rozpocznie się wyszukiwanie źródła lokalizacji do domyślnej grupy granic lokacji przed dołączeniem grupy sąsiedniego.

    - Gdy klient nie można pobrać zawartości z ostatniego serwera w puli, rozpoczyna proces ponownie.


### <a name="how-the-new-model-works"></a>Jak działa nowy model
Podczas konfigurowania grup granic można skojarzyć granic (lokalizacje sieciowe) i role systemu lokacji, takich jak punkty dystrybucji do grupy granic. Dzięki temu klientów na serwerach systemu lokacji, takich jak punkty dystrybucji, które znajdują się w pobliżu klientów w sieci.   
-   Tej samej granicy można przypisać do wielu grup granic
-   Serwery systemu lokacji, takich jak punkty dystrybucji może być skojarzona z wielu grup granic, udostępnia je dla szerszej grupy lokalizacji sieciowych
-   Jeśli punkt dystrybucji nie jest skojarzony z grupą granic, klienci nie będą mogli używać tego punktu dystrybucji jako lokalizacji źródła zawartości.

Począwszy od tej wersji technical preview, należy zdefiniować relacje grupy granic, aby skonfigurować działanie rezerwowe dla lokalizacji źródła zawartości. To nowe zachowanie jest skonfigurowany na nowym **relacje** na karcie właściwości grupy granic i zamienia Konfigurowanie systemów lokacji jako wolne lub szybkiego i skonfigurowania granic grupy Zezwalaj na rezerwową lokalizację źródła zawartości.

Na karcie relacje możesz dodać inne grupy granic, aby skonfigurować relację do tych grup. Każdej relacji jest jednokierunkowa łącza z **bieżącego** grupy granic do grupy granic, możesz dodać, która jest wywoływana **sąsiada**. Dla każdego łącza, które tworzysz można skonfigurować punkty dystrybucji z rezerwowego czas w minutach. Teraz służy do określania po jak długo klientów w *bieżącego* grupy granic można rozpocząć korzystanie z punktów dystrybucji w *sąsiada* grupy granic, jeśli nie można znaleźć lokalizacji poprawne źródło zawartości z ich bieżącą grupę granic.

Gdy klient nie można odnaleźć zawartości i rozpocznie się wyszukiwanie w lokalizacjach z grupy granic sąsiada, zwiększa puli dostępnych punktów dystrybucji dla tego klienta w kontrolowany sposób.  

-   Grupa granic może mieć więcej niż jedną relację. Dzięki temu można skonfigurować powrotu do różnych sąsiadów występuje po różnych okresach czasu.
-   Klienci będą tylko powrotu do grupy granic, która jest bezpośrednio sąsiada ich bieżącej grupy granic.
-   Gdy klient jest członkiem wielu grup granic, bieżącą grupę granic jest zdefiniowany jako Unii całkowicie grup granic klienta.  Klient może następnie powrotu do sąsiada któregokolwiek z tych oryginalnego grup granic.

Oprócz łącza, które należy zdefiniować Brak domyślnych łącza, który jest tworzony automatycznie między grupami granic, tworzonych i domyślnej grupy granic, która jest tworzona automatycznie dla każdej lokacji. To łącze automatyczne:
-   Jest używany przez klientów, którzy są nie na granicy automatycznie skojarzony z żadną inną grupą granic w hierarchii używają domyślnej grupy granic z przypisanej lokacji do identyfikowania lokalizacji poprawne źródło zawartości.   
-   To domyślne opcji rezerwowej z bieżącej grupy granic do domyślnej grupy granic lokacji jest używany po 120 minut.

**Przykład użycia nowego modelu:**     
Możesz tworzyć trzech grup granic, które nie udostępniają granic lub serwerów systemu lokacji:
-   Grupy BG_A z punktami dystrybucji DP_A1 i DP_A2 skojarzonego z grupy
-   Grupy BG_B z punktami dystrybucji DP_B1 i DP_B2 skojarzonego z grupy
-   Grupy BG_C z punktami dystrybucji DP_C1 i DP_C2 skojarzonego z grupy

Dodawanie lokalizacje sieciowe klientów jako granic tylko grupy granic BG_A, i można następnie skonfigurować relacje z tej grupy granic do innych grup granic dwóch:
-   Konfigurowanie punktów dystrybucji w pierwszym *sąsiada* grupy (BG_B) do użycia po 10 minutach. Ta grupa zawiera punkty dystrybucji DP_B1 i DP_B2. Oba są dobrze połączonych do pierwszej grupy lokalizacje granic.
-   Skonfiguruj drugi *sąsiada* grupy (BG_C) do użycia po upływie 20 minut. Ta grupa zawiera punkty dystrybucji DP_C1 i DP_C2. Są w sieci WAN z innych grup granic dwa.
-   Można również dodać dodatkowe punkt dystrybucji znajdującego się na serwerze lokacji do grupy granic lokacji domyślnej witryny. Jest to najmniej preferowanych lokalizacji źródła zawartości, ale jest on umieszczony centralnie do grup granic.

    Przykład grupy granic i rezerwowy razy:

     ![BG_Fallack](media/BG_Fallback.png)


W tej konfiguracji:
-   Klient rozpocznie się wyszukiwanie zawartości z punktów dystrybucji w jego *bieżącego* grupy granic (BG_A), wyszukiwanie każdego dystrybucji punkt dla dwóch minut przed przełączeniem do następnego punktu dystrybucji w grupie granic. Pula klientów lokalizacji poprawne źródło zawartości zawiera DP_A1 i DP_A2.
-   Jeśli klient nie można odnaleźć zawartości z jego *bieżącego* grupy granic po przeszukaniu przez 10 minut, następnie dodaje punkty dystrybucji z grupy granic BG_B do jego wyszukiwania. Następnie kontynuuje do wyszukiwania zawartości z punktu dystrybucji w jego Scalonej puli punktów dystrybucji, która zawiera teraz od BG_A i BG_B grup granic. Klient w dalszym ciągu do kontaktowania się z poszczególnych punktów dystrybucji dla dwóch minut przed przełączeniem do następnego punktu dystrybucji z puli. Pula klientów lokalizacji poprawne źródło zawartości zawiera DP_A1, DP_A2 DP_B1 i DP_B2.
-   Po 10 minutach dodatkowe (całkowita liczba 20 minut), jeśli klient nadal nie odnalazł do punktu dystrybucji z zawartością, zostanie on rozszerzony puli dostępnych punktów dystrybucji te od drugiego *sąsiada* grupy, grupa granic BG_C. Klient teraz ma 6 punktów dystrybucji do wyszukiwania (DP_A1, DP_A2 DP_B2, DP_B2, DP_C1 i DP_C2) i kontynuuje wprowadzanie zmian do nowego punktu dystrybucji co dwie minuty, aż do znalezienia zawartości.
-   Jeśli klient nie odnalazł zawartości po łącznie 120 minut, jego powraca do uwzględnienia *domyślnej grupy granic lokacji* jako część jej ciągłego wyszukiwania. Pula punktów dystrybucji zawiera teraz wszystkie punkty dystrybucji z trzech skonfigurowanych grup granic i punktu końcowego dystrybucji znajdujących się na komputerze serwera lokacji.  Klient kontynuuje wyszukiwanie zawartości, zmiana co dwie minuty, aż do znalezienia zawartości w punktach dystrybucji.

Konfigurując grupy różnych sąsiada mają być dostępne w różnych momentach kontrolować woluminowi konkretnych punktów dystrybucji jako lokalizacji źródła zawartości i gdy lub jeśli klient używa powrotu do domyślnej grupy granic lokacji zabezpieczenie na zawartość, która nie jest dostępna w innej lokalizacji.


### <a name="bkmk_update"></a>Aktualizowanie istniejących grup granic do nowego modelu
Po zainstalowaniu wersji 1609 i zaktualizować lokację, następujące konfiguracje zostaną zastosowane automatycznie. Są one przeznaczone do upewnij się, że Twoje bieżące działanie rezerwowe pozostaje dostępna, w przypadku konfigurowania nowej grupy granic i relacje.  
-   Punkty dystrybucji niechronione w lokacji są dodawane do *domyślna--grupy granic lokacji\<kod lokacji >* grupy granic w tej lokacji.
-   Kopia składa się z każdej istniejącej grupy granic, która obejmuje serwer lokacji skonfigurowany z wolnego połączenia. Nazwa nowej grupy jest *** \<oryginalna nazwa grupy granic > - wolno — Tmp***:  
    -   Systemy lokacji, które mają szybkiego połączenia są pozostawiane w oryginalnej grupy granic.
    -   Kopiuj systemów lokacji, które mają wolne połączenia są dodawane do kopii grupy granic. Oryginalne systemy lokacji skonfigurowana jako niska pozostają w grupie granic oryginalnego dla zgodności z poprzednimi wersjami, ale nie są używane z tej grupy granic.
    -   Ta kopia grupy granic nie ma granicach skojarzonych z nim. Jednak tworzone jest połączenie rezerwowy między oryginalnej grupy i nową kopię grupy granic o czasie rezerwowy ustawić na zero.

 W poniższej tabeli przedstawiono nowe działanie rezerwowe można spodziewać się z kombinacji oryginalne ustawienia wdrożenia i punktu dystrybucji konfiguracje:

Oryginalna konfiguracja wdrożenia "Nie należy uruchamiać program" w wolnej sieci  |Punkt dystrybucji oryginalnej konfiguracji "Client Zezwalaj na użycie rezerwowej lokalizacji źródła zawartości"  |Nowe działanie rezerwowe  
---------|---------|---------
Wybrane     |  Wybrane    |  **Rezerwowe nie** -punktów dystrybucji należy używać tylko w bieżącej grupie granic       
Wybrane     |  Nie wybrano|  **Rezerwowe nie** -punktów dystrybucji należy używać tylko w bieżącej grupie granic       
Nie wybrano |  Nie wybrano|  **Powrót do sąsiada** — używać punktów dystrybucji w bieżącej grupie granic, a następnie dodaj punkty dystrybucji z grupy granic sąsiedniego. Chyba że jawne łącze do domyślnej grupy granic lokacji jest skonfigurowany, klienci nie będą powrotu do tej grupy.    
Nie wybrano | Wybrane     |   **Normalne powrotu** -używać punktów dystrybucji w bieżącej grupie granic, a następnie od sąsiada i lokacji domyślnych grup granic

 Wszystkie konfiguracje wdrożenia powoduje **normalne powrotu**.  



## <a name="office-365-client-management-dashboard"></a>Pulpit nawigacyjny zarządzania klienta usługi Office 365  
Program Configuration Manager 1609 Technical Preview wprowadzono nowy pulpit nawigacyjny. Aby wyświetlić pulpit nawigacyjny, w konsoli programu Configuration Manager przejdź do **Biblioteka oprogramowania** > **omówienie** > **zarządzania klienta usługi Office 365**.
>[!NOTE]
>W **What's New** obszaru roboczego w konsoli programu Configuration Manager, nowy pulpit nawigacyjny jest niepoprawna **obsługi usługi Office 365 pulpitu nawigacyjnego**.

Pulpit nawigacyjny Wyświetla wykresy dla następujących elementów:

- Liczba klientów usługi Office 365
- Wersje klienta usługi Office 365
- Języki klienta usługi Office 365
- Kanały klienta usługi Office 365     
Aby uzyskać więcej informacji, zobacz [Omówienie aktualizacji kanałów dla usługi Office 365 ProPlus](https://technet.microsoft.com/library/mt455210.aspx).
- Reguły automatycznego wdrażania klienta usługi Office 365 wybrane w zestawie dostępnych produktów.

Na pulpicie nawigacyjnym można wykonać następujące czynności:
- W górnej części pulpitu nawigacyjnego, należy użyć **kolekcji** ustawienie listy rozwijanej, aby filtrować dane pulpitu nawigacyjnego przez członków określonej kolekcji.
- W prawym górnym pulpitu nawigacyjnego, kliknij **Office 365 Instalator** można uruchomić Kreatora instalacji klienta Office 365 do wdrażania aplikacji usługi Office 365 na klientach. Aby uzyskać więcej informacji, zobacz [aplikacji wdrożenia usługi Office 365 dla klientów](#deploy-office-365-apps-to-clients).
- W środku po prawej stronie pulpitu nawigacyjnego, kliknij polecenie **utworzyć regułę ADR** otworzyć kreatorze reguły wdrażania automatycznego, aby utworzyć nową regułę wdrażania automatycznego (ADR). Aby utworzyć regułę ADR dla aplikacji usługi Office 365, wybierz **klienta usługi Office 365** po wybraniu produktu. Aby uzyskać więcej informacji, zobacz [automatyczne wdrażanie aktualizacji oprogramowania](/sccm/sum/deploy-use/automatically-deploy-software-updates).
- W prawym dolnym pulpitu nawigacyjnego, kliknij **Utwórz ustawienia agenta klienta** można otworzyć ustawień agenta klienta. Aby uzyskać więcej informacji, zobacz [informacje o ustawieniach klienta](/sccm/core/clients/deploy/about-client-settings).



Aby uzyskać więcej informacji na temat aktualizacji usługi Office 365 ProPlus, zobacz [zarządzania usługi Office 365 ProPlus aktualizacji z programu Configuration Manager](/sccm/sum/deploy-use/manage-office-365-proplus-updates).

## <a name="deploy-office-365-apps-to-clients"></a>Wdrażanie aplikacji usługi Office 365 na klientach
W tej wersji, z poziomu pulpitu nawigacyjnego zarządzania klienta usługi Office 365 możesz uruchomić Instalatora 365 pakietu Office, które umożliwia konfigurowanie ustawień instalacji usługi Office 365, pobierania plików z pakietu Office sieci dostarczania zawartości (CDN) i wdrożenia plików jako aplikacji w programie Configuration Manager.

### <a name="limitations-of-office-365-deployment"></a>Ograniczenia dotyczące wdrożenia usługi Office 365
- Problemy mogą wystąpić podczas próby zaimportowania istniejących ustawień klienta (XML) w Kreatorze instalacji programu Office 365 aplikacji. Można ręcznie skonfigurować ustawienia klienta bez problemu.

#### <a name="to-deploy-office-365-apps-to-clients"></a>Do wdrażania aplikacji usługi Office 365 na klientach
1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **omówienie** > **zarządzania klienta usługi Office 365**.
2. Kliknij przycisk **Office 365 Instalator** w prawym górnym okienku. Zostanie otwarty Kreator instalacji klienta Office 365.
3. Na **ustawienia aplikacji** , podaj nazwę i opis aplikacji, wprowadź lokalizację pobierania dla plików, a następnie kliknij przycisk **dalej**. Należy pamiętać, że lokalizacja musi być określony w formularzu &#92; &#92; *server*&#92; *udostępnianie*.
4. Na **importowania ustawień klienta** strony wybierz, czy do zaimportowania ustawień klienta usługi Office 365 z istniejącego pliku konfiguracji XML lub ręcznie określ ustawienia, a następnie kliknij przycisk **dalej**.
Jeśli masz istniejący plik konfiguracyjny wprowadź lokalizację pliku, a następnie przejdź do kroku 7. Należy pamiętać, że lokalizacja musi być określony w formularzu &#92; &#92; *server*&#92; *udostępnianie*&#92; *Nazwa pliku*. KOD XML.

    > [!IMPORTANT]
    >Problemy mogą wystąpić podczas próby zaimportowania istniejących ustawień klienta (XML) w tej wersji technical preview.

5. Na **produktów klienta** , wybierz usługi Office 365 pakiet, którego używasz, wybierz aplikacje, które chcesz dołączyć, wybierz wszelkie dodatkowe produktów pakietu Office, które powinny być uwzględnione, a następnie kliknij **dalej**.
6. Na **ustawień klienta** wybierz ustawienia do uwzględnienia, a następnie kliknij pozycję **dalej**.
7. Na **wdrożenia** wybierz, czy wdrożyć aplikację, a następnie kliknij przycisk **dalej**.
Jeśli wybierzesz nie wdrożyć pakiet w kreatorze, przejdź do kroku 9.
8. W pozostałej części strony kreatora należy skonfigurować, jak w przypadku wdrażania Typowa aplikacja. Aby uzyskać więcej informacji, zobacz [tworzenie i wdrażanie aplikacji](/sccm/apps/get-started/create-and-deploy-an-application).
9. Ukończ pracę kreatora.
10. Można wdrożyć lub edytować aplikację tak samo jak z dowolnej innej aplikacji w programie Configuration Manager z **Biblioteka oprogramowania** > **omówienie** > **Zarządzanie aplikacjami** > **aplikacji**.

>[!NOTE]
>Po wdrożeniu aplikacji usługi Office 365, można utworzyć reguły automatycznego wdrażania do obsługi aplikacji. Aby utworzyć regułę ADR dla aplikacji usługi Office 365, kliknij przycisk **utworzyć regułę ADR**i wybierz **klienta usługi Office 365** po wybraniu produktu. Aby uzyskać więcej informacji, zobacz [automatyczne wdrażanie aktualizacji oprogramowania](/sccm/sum/deploy-use/automatically-deploy-software-updates).

## <a name="BKMK_UEFIConversion"></a>Ulepszenia systemu BIOS z interfejsem UEFI konwersji
Teraz można dostosować sekwencję zadań wdrażania systemu operacyjnego z nową zmienną TSUEFIDrive, tak, aby krok Uruchom ponownie komputer będzie przygotować przejścia do UEFI FAT32 partycji na dysku twardym. Poniższa procedura zawiera przykładowy sposób tworzenia kroków sekwencji zadań, aby przygotować dysk twardy dla systemu BIOS z interfejsem UEFI konwersji.

#### <a name="to-prepare-the-fat32-partition-for-the-conversion-to-uefi"></a>Aby przygotować partycji FAT32 do konwersji na UEFI:
W istniejącej sekwencji zadań instalacji systemu operacyjnego doda nową grupę prostych kroków, czy system BIOS z interfejsem UEFI konwersji.

1. Utwórz grupę sekwencji zadań po wykonaniu kroków przechwytywania plików i ustawień, a przed kroki, aby zainstalować system operacyjny. Na przykład utworzyć grupę po **przechwytywania plików i ustawień** grupę o nazwie **systemu BIOS-UEFI**.
2. Na **opcje** kartę nowej grupy, należy dodać zmienną sekwencji zadań jako warunek gdzie **_SMSTSBootUEFI** jest **równa** do **true**. Zapobiega to uruchomiony, gdy komputer jest już w trybie UEFI kroków w grupie.
![System BIOS z interfejsem UEFI grupy](media/BIOS-to-UEFI-group.png)
3. W ramach nowej grupy, należy dodać **Uruchom ponownie komputer** krok sekwencji zadań. W **Określ, co uruchomić po ponownym uruchomieniu**, wybierz pozycję **obraz rozruchowy przypisany do tej sekwencji zadań jest zaznaczone** do uruchomienia komputera w środowisku Windows PE.  
4. Na **opcje** , Dodaj zmienną sekwencji zadań jako warunek gdzie **_SMSTSInWinPE jest równa false**. Zapobiega to uruchomiony, jeśli komputer jest już w systemie Windows PE w tym kroku.

    ![Uruchom ponownie komputer kroku](media/Restart-in-Windows-PE.png)
5. Dodaj krok, aby uruchomić narzędzie OEM przekonwertuje oprogramowanie układowe BIOS z interfejsem UEFI. Są to zazwyczaj **Uruchom wiersz polecenia** krok sekwencji zadań przy użyciu wiersza polecenia, aby uruchomić narzędzie OEM.
5.  Dodaj krok sekwencji zadań Formatuj partycję dysk i partycje i sformatowanie dysku twardego. W kroku wykonaj następujące czynności:
    1.  Utwórz partycję FAT32, który zostanie przekonwertowany na UEFI, przed zainstalowaniem systemu operacyjnego. Wybierz **GPT** dla **typ dysku**.
    ![Format i partycji dysku kroku](media/Format-and-partition-disk.png)
    2.  Przejdź do właściwości partycji FAT32. Wprowadź **TSUEFIDrive** w **zmiennej** pola. Jeśli sekwencja zadań wykryje tej zmiennej, przygotuj przejścia z interfejsem UEFI przed ponownym uruchomieniem komputera.
    ![Właściwości partycji.](media/Partition-properties.png)
    3. Utwórz partycję NTFS, używaną przez aparat sekwencji zadań można zapisać stanu i do przechowywania plików dziennika.
6.  Dodaj **Uruchom ponownie komputer** krok sekwencji zadań. W **Określ, co uruchomić po ponownym uruchomieniu**, wybierz pozycję **obraz rozruchowy przypisany do tej sekwencji zadań jest zaznaczone** do uruchomienia komputera w środowisku Windows PE.  




## <a name="intune-compliance-charts"></a>Wykresy zgodności usługi Intune
W tej wersji można uzyskać szybki przegląd ogólnej zgodności dla urządzeń i do górnej przyczyn braku zgodności, za pomocą nowych wykresów w obszarze **obszaru roboczego monitorowanie** w konsoli programu Configuration Manager.

#### <a name="to-view-the-intune-compliance-charts"></a>Aby wyświetlić wykresy zgodności usługi Intune
1. W konsoli programu Configuration Manager, przejdź do **monitorowanie** > **omówienie** > **ustawień zgodności**.
2. **Ogólnej zgodności urządzenia** wyświetleniem wykresu.
3. Kliknij przycisk **zasady zgodności** węzeł, aby wyświetlić **ogólnej zgodności urządzenia** i **górnej niezgodności powodów** wykresów.

### <a name="limitations-of-intune-compliance-charts-in-tp-1609"></a>Ograniczenia wykresów zgodności usługi Intune w TP 1609
- Przechodzenie do **ogólnej zgodności urządzenia** wykresu obecnie powoduje błąd.
- **Głównych powodów niezgodności** wymieniono nazwę zasady, a nie poszczególnych przyczyn braku zgodności. Możesz kliknąć zasady przechodzenia i urządzenia, które są niezgodne dla tej zasady.

### <a name="try-it-out"></a>Podczas próby
Wypełnij następujące sekcje w kolejności:

#### <a name="check-overall-compliance-chart"></a>Sprawdź zgodność ogólna wykresu
1. Dodać na dwa iOS zasady zgodności w programie Configuration Manager. Jedne zasady powinny mieć jeden zestaw ustawień dla urządzeń (na przykład zestaw długości numeru PIN do 6). Inne zasady powinny mieć inny zestaw ustawień (na przykład złożoności kodu PIN). Ustawienia zasad nie nakłada się na ani pozostawać w konflikcie.
2. Wdrażanie zasad dwóch zbioru użytkowników.
3. Zarejestrować dwa urządzenia z systemem iOS w usłudze Intune przy użyciu tego samego konta użytkownika, a konto, które odebrano zasady w poprzednim kroku. Urządzenia nie powinna spełniać kryteria zasad zgodności.
4. Sprawdź w Menedżerze konfiguracji **ogólnej zgodności urządzenia** wykresu. Zarówno na urządzeniach należy raportowane jako niezgodne.
<!-- 5. Click the **Non-compliant** section of the chart. Both devices should appear in the filtered view under **Assets and Compliance** > **Overview** > **Device**. -->

#### <a name="check-the-top-non-compliance-reasons-chart"></a>Sprawdź wykres głównych powodów niezgodności
5. Sprawdź **głównych powodów niezgodności** wykresu. Ten wykres Wyświetla do górnej 5 przyczyn braku zgodności, ale po tylko dwa ustawienia zgodności zostały ustawione przez zasady tylko 2 pierwszych niezgodności przyczyny są wyświetlane.
6. Kliknij jedną z części wykresu. Zarówno na urządzeniach powinny być wyświetlane w widoku filtrowanego w obszarze **zasoby i zgodność** > **omówienie** > **urządzenia**.

#### <a name="make-devices-compliant-and-check-the-charts"></a>Zapewnienia zgodności urządzenia i sprawdź wykresy
7. Utworzyć urządzenia zgodne z jedną z zasad. Sprawdź **ogólnej zgodności urządzenia** wykresu ponownie. Jedno urządzenie zgodne i niezgodne jeden wykres powinien być wyświetlany.
8. Inne urządzenie zapewnienia zgodności z tych samych zasad. Spowoduje to jedno urządzenie zgodne z zasadami i urządzenia zgodne z tylko jedną z zasad.
9. Sprawdź **głównych powodów niezgodności** wykresu. Należy tylko jedną z wymienionych przyczyn braku zgodności.
<!--7. Click the **Compliant** section of the chart. Only the compliant device should appear in the filtered view. -->





## <a name="see-also"></a>Zobacz też
[Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md)
