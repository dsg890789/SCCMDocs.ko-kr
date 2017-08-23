---
title: Definiowanie grup granic | Dokumentacja firmy Microsoft
description: "Zrozumienie grup granic, połączonych klientów z systemami lokacji w programie System Center Configuration Manager."
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5db2926f-f03e-49c7-b44b-e89b1a5a6779
caps.latest.revision: "10"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 5debc6559f4b1c213e8ca513d685941c9e669063
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="configure-boundary-groups-for-system-center-configuration-manager"></a>Konfigurowanie grup granic dla programu System Center Configuration Manager


*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Używasz grup granic w programie System Center Configuration Manager do logicznego pogrupowania powiązanych lokalizacji sieciowych ([granice](/sccm/core/servers/deploy/configure/boundaries)) aby ułatwić zarządzanie infrastrukturą. Granice można przypisać do grup granic, zanim będzie możliwe użycie grupy granic.

Domyślnie program Configuration Manager tworzy domyślną grupę granic lokacji w każdej lokacji.

> [!IMPORTANT]  
>  **Informacje przedstawione w tej sekcji grupy granic i jego sekcje podrzędnych dotyczy wersji 1610 lub nowszej.** Ta zawartość została zmieniona jest specyficzny dla zmian projektowych wprowadzonych w grupach granic w tej wersji aktualizacji.
>
> **Jeśli używasz wersji przed 1610**, zobacz [grup granic dla programu System Center Configuration Manager w wersji 1511, 1602 i 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606) informacji na temat użycia i konfigurowania grup granic z tymi wersjami produktu.

Aby skonfigurować grupy granic, należy skojarzyć granic (lokalizacje sieciowe) i role systemu lokacji, takich jak punkty dystrybucji do grupy granic. Dzięki temu można skojarzyć klientów na serwerach systemu lokacji, takich jak punkty dystrybucji, które znajdują się w pobliżu klientów w sieci.

Należy przypisać tej samej granicy do wielu grup granic, a tej samej lokacji serwery systemu, takich jak punkty dystrybucji do wielu grup granic zwiększa dostępność systemów lokacji dla szerszej grupy lokalizacji sieciowych.

Klienci używają grupę granic:  

-   Automatycznego przypisywania lokacji  
-   Aby znaleźć serwer systemu lokacji, która może zapewnić usługę, w tym:
    - Punkty dystrybucji dla lokalizacji zawartości
    -   Punkty aktualizacji oprogramowania (począwszy od wersji 1702)
    - Punkty migracji stanu
    - Preferowanych punktów zarządzania (Jeśli używasz preferowane punkty zarządzania, należy włączyć tę opcję dla hierarchii, a nie za pomocą konfiguracji grupy granic. Zobacz [umożliwia korzystanie z preferowanych punktów zarządzania](#to-enable-use-of-preferred-management-points) w tym temacie.)

##  <a name="boundary-groups-and-relationships"></a>Grupy granic i relacje
Dla każdej grupy granic w hierarchii można przypisać:

-  Co najmniej jedną granicę. Kiedy klient znajduje się w lokalizacji sieciowej, która jest zdefiniowana jako granicę przypisane do określonej grupy, która jest wywoływana **bieżącego** grupy granic. Klient może mieć więcej niż jednej grupy granic bieżącej.
- Jeden lub więcej ról systemu lokacji.  Klienci mogą zawsze używać ról systemu lokacji skojarzone z ich bieżącą grupę granic. W zależności od dodatkowe konfiguracje mogą one można używać w grupach granic dodatkowe role systemu lokacji.  

Dla każdej grupy granic, które możesz utworzyć można skonfigurować jednokierunkowe łącze do innej grupy granic. Łącze jest nazywany **relacji**. Łącze do grupy granic są nazywane **sąsiada** grup granic. Grupa granic może mieć wiele relacji, każdy z grupą granic określonych sąsiedniego.

Konfiguracja każdej relacji określa, kiedy klient, który zakończy się niepowodzeniem, aby dowiedzieć się, że serwer systemu lokacji dostępne w jego bieżącej grupy granic można rozpocząć wyszukiwania sąsiada grupy granic można znaleźć systemu lokacji. To wyszukiwanie dodatkowych grup jest nazywany **rezerwowy**.

## <a name="fallback"></a>Opcja rezerwowa
Aby zapobiec problemom dla klientów, gdy system lokacji dostępny nie znajduje się w ich bieżącej grupy granic, należy zdefiniować relacji między grupami granic, które definiuje zachowanie rezerwowego. Rezerwa umożliwia klienta rozwiń wyszukiwanie do grup granic dodatkowe można znaleźć systemu lokacji.

Relacje są skonfigurowane na właściwości grupy granic **relacje** kartę. Po skonfigurowaniu relacji z grupą granic sąsiada należy zdefiniować łącza. Dla każdego typu Rola systemu lokacji, która jest obsługiwana można skonfigurować niezależnie od ustawień powrotu do tej grupy granic sąsiedniego. Na przykład po skonfigurowaniu relacji z grupą granic określonych można ustawić rezerwowy dla punktów dystrybucji zostać przeprowadzone po upływie 20 minut, zamiast domyślnej 120. Zobacz [przykład za pomocą grup granic](#example-of-using-boundary-groups) szerszej np.

Jeśli klient nie może znaleźć dostępna Rola systemu lokacji w jego bieżącej grupy granic, klient używa rezerwowej czas w minutach do określenia po jak długo można rozpocząć wyszukiwania system lokacji dostępny, który jest skojarzony z tej grupy granic sąsiedniego.  

Gdy klient nie może znaleźć system lokacji dostępny i rozpocznie się wyszukiwanie w lokalizacjach od sąsiada grup granic, zwiększa puli systemy lokacji dostępne, które mogą być używane w taki sposób, który jest zdefiniowany w bieżącej konfiguracji grupy granic i ich relacji.

- Grupa granic może mieć więcej niż jedną relację. Relacje wiele można skonfigurować używane dla każdego typu systemu lokacji z różnych sąsiadów występuje po różnych okresach czasu.    
- Klienci tylko powrotu do grupy granic, która jest bezpośrednio sąsiada ich bieżącej grupy granic.
- Gdy klient jest członkiem wielu grup granic, bieżącą grupę granic jest zdefiniowany jako Unii całkowicie grup granic klienta. Klient może następnie powrotu do sąsiadów któregokolwiek z tych oryginalnego grup granic.

### <a name="the-default-site-boundary-group"></a>Domyślna grupa granic lokacji
Oprócz grup granic, które możesz utworzyć każda lokacja ma domyślne grupy granic lokacji jest tworzony przez program Configuration Manager. Ta grupa ma nazwę ***domyślna--grupy granic lokacji&lt;kod lokacji >***. Na przykład, czy nazwę grupy w lokacji ABC *domyślna--grupy granic lokacji —&lt;ABC >.*

Dla każdej grupy granic tworzonych programu Configuration Manager automatycznie tworzy domniemanych łącze do każdej grupy granic lokacji domyślnej w hierarchii.
-   Dorozumiany łącze jest domyślne opcji rezerwowej z bieżącej grupy granic do domyślnej grupy granic lokacji rezerwowego czasu domyślne 120 minut.
-   Klienci, którzy nie znajdują się na granicy skojarzony z żadną inną grupą granic w hierarchii umożliwia domyślnej grupy granic lokacji w przypisanej lokacji zidentyfikowanie role systemu lokacji prawidłowy, którego mogą używać.

Aby zarządzać powrotu do domyślnej grupy granic lokacji:
- Można przejść do właściwości grupy granic domyślnej witryny i zmień wartości w **domyślne zachowanie** kartę. Zmiany wprowadzone w tym miejscu dotyczą *wszystkie* niejawnego łącza do tej grupy granic. Te ustawienia mogą zostać zastąpione podczas konfigurowania jawne łącze do tej grupy granic lokacji domyślnej z innej grupy granic.
- Przejdź do okna właściwości grupy granic utworzonej i zmień wartości jawne łącza, który jest przesyłany do domyślnej grupy granic lokacji. Po ustawieniu nowego czas w minutach, powrotu lub bloku powrotu tej wpływa tylko łącze, które są konfigurowane. Konfiguracje wyraźnego związku przesłaniają akcje na **domyślne zachowanie** kartę domyślne grupy granic lokacji.


## <a name="site-assignment"></a>Przypisanie lokacji  
 Do każdej grupy granic można wprowadzić przypisaną lokację do klientów.  

-   Nowo zainstalowanego klienta, który używa automatycznego przypisania lokacji łączy przypisanej lokacji grupę granic zawierającą bieżącą lokalizację sieciową klienta.  
-   Po przypisaniu do lokacji klient nie zmienia przypisania lokacji, gdy zmienia lokalizację sieciową. Na przykład, jeśli klient przejdzie do nowej lokalizacji sieciowej, która jest reprezentowana przez granicę w grupie granic z innym przypisaniem lokacji, klienta przypisanej lokacji pozostaną bez zmian.  
-   Kiedy funkcja odnajdowania systemu usługi Active Directory odnajdzie nowy zasób, informacje o sieci odnalezionego zasobu zostaną ocenione względem granic w grupach granic. Ten proces powoduje skojarzenie nowego zasobu z przypisaną lokacją w celu użycia przez metodę instalacji klienta w trybie wypychania.  
-   Gdy granicy do wielu grup granic, które mają przypisane różne lokacje, klientów losowo wybierać jedną z lokacji.  
-   Zmiany lokacji przypisanej do grup granic dotyczą tylko nowych akcji przypisania lokacji. Klienci, którzy wcześniej przypisani do lokacji, nie obliczyć ponownie przypisania lokacji na podstawie zmian w konfiguracji grupy granic (lub do lokalizacji sieciowej).  

Aby uzyskać więcej informacji o przypisywaniu lokacji klienta, zobacz [przy użyciu automatycznego przypisania lokacji komputerów](../../../../core/clients/deploy/assign-clients-to-a-site.md#BKMK_AutomaticAssignment) w [jak przypisać klientów do lokacji w programie System Center Configuration Manager](../../../../core/clients/deploy/assign-clients-to-a-site.md).  

## <a name="distribution-points"></a>Punkty dystrybucji

Gdy klient żąda lokalizacji punktu dystrybucji, programu Configuration Manager wysyła klientowi listę, która obejmuje systemy lokacji odpowiedniego typu, które są skojarzone z każdą grupą granic, co obejmuje także bieżącą lokalizację sieciową klientów:

-   **Podczas dystrybucji oprogramowania**, klient żąda lokacji wdrożenia zawartości, która jest dostępna z punktem dystrybucji lub innych poprawne źródło zawartości (na przykład klient skonfigurowany na potrzeby równorzędnej pamięci podręcznej).

-   **Podczas wdrażania systemu operacyjnego**, klienci żądają lokalizacji do wysłania lub odebrania informacji o migracji stanu.  

Podczas wdrażania zawartości Jeśli klient żąda zawartości, który nie jest dostępny ze źródła w jego bieżącej grupy granic, klient w dalszym ciągu zażądać tej zawartości do momentu osiągnięcia okres rezerwowy dla grupy granic sąsiada lub domyślna grupa granic lokacji w trakcie różnych źródeł zawartości w jego bieżącej grupy granic. Jeśli klient nie odnalazł jeszcze zawartość, następnie rozwija wyszukiwanie źródeł zawartości uwzględnić sąsiada grupy granic.

Jednak jeśli zawartość będzie rozmieszczona na żądanie i nie jest dostępna w punkcie dystrybucji, gdy żądany przez klienta, rozpoczyna proces transferu zawartości do tego punktu dystrybucji i jest możliwe, klient będzie znaleźć ten serwer jako źródła zawartości przed powrotem do używania grupy granic sąsiedniego.

## <a name="software-update-points"></a>Punkty aktualizacji oprogramowania
Począwszy od wersji 1702, klienci używają grup granic do znajdowania punktu aktualizacji oprogramowania. Punkty aktualizacji oprogramowania można dodać do różnych grup granic do serwerów, które klient można znaleźć formantu.

Po aktualizacji z wersji przed 1702 wszystkie istniejące punkty aktualizacji oprogramowania są dodawane do domyślnej grupy granic lokacji w każdej lokacji. Zapewnia to dostępność zachowanie przed aktualizacją, gdzie klienci wybierają punkt aktualizacji oprogramowania z puli punktów aktualizacji oprogramowania dostępne, które zostały skonfigurowane dla danej hierarchii.  To zachowanie jest zachowywana do momentu dodania do różnych grup granic zaznaczenia kontrolowane i działanie rezerwowe punkty aktualizacji oprogramowania.

W przypadku instalowania nowej lokacji, na którym działa wersja 1702 lub później, punkty aktualizacji oprogramowania nie są dodawane do domyślnej grupy granic lokacji. Przypisać punkty aktualizacji oprogramowania do grupy granic, tak aby klienci mogą znaleźć i używać ich.

### <a name="fallback-for-software-update-points"></a>Używane dla punktów aktualizacji oprogramowania
Używane dla punktów aktualizacji oprogramowania jest skonfigurowane tak jak inne role systemu lokacji, ale ma następujące ostrzeżenia:
- **Nowi klienci używają grup granic, aby wybrać punkty aktualizacji oprogramowania.** Po zainstalowaniu wersji 1702 nowych klientów, które można zainstalować, wybierz punkt aktualizacji oprogramowania z skojarzonych z grupami granic, które zostały skonfigurowane. Spowoduje to zastąpienie poprzedniego zachowanie, gdy klienci wybierają punkt aktualizacji oprogramowania losowo z listy osób, które współużytkują lesie klienta.

- **Klienci w dalszym ciągu korzystać punktu aktualizacji oprogramowania dobrej Ostatnia znana do nich rezerwowy można znaleźć nową.** Klienci, którzy już mają punkt aktualizacji oprogramowania w dalszym ciągu używać tego punktu aktualizacji oprogramowania, dopóki nie może uzyskać dostępu do tego serwera.  Dotyczy to również dalsze używanie punkt aktualizacji oprogramowania, który nie jest skojarzony z bieżącą grupę granic klienta.

  Dalsze używanie istniejącego punktu aktualizacji oprogramowania nawet wtedy, gdy ten serwer nie jest w bieżącej grupie granic klienta jest zamierzone. Jest to spowodowane Zmiana punktu aktualizacji oprogramowania może spowodować duże wykorzystanie przepustowości sieci, jak klient synchronizuje dane z nowego punktu aktualizacji oprogramowania. Opóźnienie w przejście może pomóc uniknąć nasycenia sieci, jeśli wszystkich klientów przełącznik nowe oprogramowanie punktu aktualizacji w tym samym czasie.

- **Klient zawsze próbuje nawiązać połączenie jego ostatnim punktem aktualizacji oprogramowania znanego dobrego na 120 minut przed uruchomieniem rezerwowego.** Po 120 minut Jeśli klient nie ma nawiązać kontaktu, następnie rozpoczyna powrotu. Po uruchomieniu rezerwowe, klient odbierze listę wszystkich punktów aktualizacji oprogramowania z jego bieżącej grupy granic. Dodatkowe punkty aktualizacji oprogramowania od sąsiada grupy granic i grupy granic lokacji domyślne dostępnych konfiguracji rezerwowego.

### <a name="fallback-configurations-for-software-update-points"></a>Konfiguracje rezerwowy dla punktów aktualizacji oprogramowania
#### <a name="beginning-with-version-1706"></a>Począwszy od wersji 1706   
Można skonfigurować **powrotu czas (w minutach)** na aktualizacji oprogramowania punktów za mniej niż 120 minut. Jednak klient musi nadal próbują uzyskać dostęp jego oryginalnej punktu aktualizacji oprogramowania na 120 minut przed rozszerza on wyszukiwania do dodatkowych serwerów. Ponieważ razy rezerwowy grupy granic uruchomić, gdy klient nie dokona najpierw do oryginalnego serwera, tych grup granic, które są skonfigurowane do 120 minut są dostarczane do klienta podczas rozszerza on wyszukiwanie po awarii do oryginalnego serwera na 120 minut.

Można skonfigurować **nigdy rezerwowy** blok rezerwowy dla oprogramowania punktu z grupą granic sąsiada aktualizacji.

Po awarii do oryginalnego serwera przez 2 godziny, klient używa następnie wywołania skrócenie cyklu nawiązanie połączenia punktu aktualizacji oprogramowania. Dzięki temu klientowi szybko przeszukiwać rosnącą listę potencjalnych punktów aktualizacji oprogramowania.

 -  **Przykład powrotu:**  
    Bieżącą grupę granic klienta jest używane dla punktów aktualizacji oprogramowania, które są skonfigurowane jako *10* minut dla grupy granic *A*, i *130* minut dla grupy granic *B*. Gdy klient nie może nawiązać jego ostatnim punktem aktualizacji oprogramowania znanego dobrego:
    -   Klient próbuje osiągnąć jego oryginalny serwer dalej 120 minut.  Po 10 minutach punktów z grupą granic, są dodawane do puli serwerów dostępnych aktualizacji oprogramowania. Klient nie może jednak próbę skontaktowania się z ich lub na innym serwerze przed upływem okresu wstępnego 120 minut połączyć się ponownie z oryginalnego serwera.
    -   Po próbuje zlokalizować tego oryginalnego punktu aktualizacji oprogramowania na 120 minut, klient może rozszerzyć poszukiwania. W tym czasie serwerów w bieżącej grupie granic klienta i wszelkie sąsiada grup granic, które są skonfigurowane do 120 minut lub mniej, są dodawane do dostępnej puli punktów aktualizacji oprogramowania. Dotyczy to serwery A grupy granic, które zostały wcześniej dodane do puli dostępnych serwerów.
    -       Po 10 minutach (130 minut całkowity czas po klient najpierw nie może połączyć się jego ostatnim punktem aktualizacji oprogramowania znanego dobrego) klient rozszerza wyszukiwania w celu uwzględnienia punktów aktualizacji oprogramowania z grupy granic B.  

#### <a name="prior-to-version-1706"></a>Przed wersją 1706
Poprzedzające wersję 1706 rezerwowej konfiguracji punktów aktualizacji oprogramowania nie obsługują można skonfigurować czas w minutach. Zamiast tego zachowania alternatywnego jest ograniczona do:

  - **Rezerwowy czas (w minutach):**  Ta opcja jest niedostępny dla punktów aktualizacji oprogramowania i nie można skonfigurować. Jest ustawiona na 120 minut.
  -     **Nigdy nie rezerwowej:** Możesz zablokować używane dla punktu aktualizacji oprogramowania do grupy granic sąsiada używania tej konfiguracji.

Gdy klient, który ma już punkt aktualizacji oprogramowania nie można uzyskać do niej dostęp, klient może następnie powrotu można znaleźć innego. Korzystając z metody rezerwowej, klient odbiera listę wszystkich punktów aktualizacji oprogramowania z jego bieżącej grupy granic. W przypadku niepowodzenia można znaleźć dostępnego serwera na 120 minut zostanie następnie powrotu do jego grupę granic sąsiada i domyślnej grupy granic lokacji. Powrót do obu grup granic odbywa się w tym samym czasie, ponieważ punkty rezerwowy czas sąsiada grup jest ustawiona na 120 minut i nie można zmienić aktualizacji oprogramowania. 120 minut jest również domyślny okres używane powrotu do domyślnej grupy granic lokacji. Gdy klient powraca do obu sąsiada i domyślnej grupy granic lokacji, klient próbuje skontaktować się z punktów aktualizacji oprogramowania z grupy granic sąsiada przed podjęciem próby użycia jednej z domyślnej grupy granic lokacji.

### <a name="manually-switch-to-a-new-software-update-point"></a>Ręcznie przełączać się do nowego punktu aktualizacji oprogramowania
Oprócz używania rezerwowego, można użyć *powiadomienie klienta* ręcznie wymusić urządzenia, aby przełączyć się do nowego punktu aktualizacji oprogramowania.

Przełączenie do nowego serwera urządzenia używają rezerwowego do znajdowania ten nowy serwer. W związku z tym Przejrzyj konfiguracji grupy granic i upewnij się, że punkty aktualizacji oprogramowania znajdują się w grupach granic poprawne przed rozpoczęciem tej zmiany.

Aby uzyskać więcej informacji, zobacz [ręcznie przełączać klientów do nowego punktu aktualizacji oprogramowania](/sccm/sum/plan-design/plan-for-software-updates#manually-switch-clients-to-a-new-software-update-point).


## <a name="preferred-management-points"></a>Preferowane punkty zarządzania

 Preferowane punkty zarządzania umożliwiają klientom identyfikowanie punktów zarządzania skojarzonych z ich bieżącą lokalizacją sieciową (granicą).  

-   Klienci podejmują próbę użycia preferowanego punktu zarządzania z przypisanej do niego lokacji, zanim użyją punktów zarządzania z przypisanej lokacji, który nie jest skonfigurowany jako preferowane.  
-   Aby użyć tej opcji, możesz ją włączyć w hierarchii, a następnie skonfiguruj grup granic w poszczególnych lokacjach głównych w celu uwzględnienia punktów zarządzania, które powinny być skojarzone ze skojarzonymi granicami tej grupy granic.  
-   Gdy preferowane punkty zarządzania są skonfigurowane, a klient organizuje swoją listę punktów zarządzania, klient umieszcza preferowane punkty zarządzania u góry listy przypisanych punktów zarządzania (zawierającej wszystkie punkty zarządzania z przypisanej lokacji klienta).  

> [!NOTE]  
>  Gdy klient przemieszcza się (co oznacza, że zmienia lokalizację sieciową, np. laptop pojawia się w lokalizacji biura zdalnego), może w nowej lokalizacji używać punktu zarządzania (lub punktu zarządzania serwera proxy) z lokacji lokalnej przed podjęciem próby użycia punktu zarządzania z przypisanej lokacji (która obejmuje preferowane punkty zarządzania).  Zobacz [zrozumieć, jak klienci znajdują zasoby i usługi programu System Center Configuration Manager lokacji](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md) Aby uzyskać więcej informacji.  

### <a name="overlapping-boundaries"></a>Nakładanie się granic  
 Program Configuration Manager obsługuje nakładających się granic konfiguracje lokalizacji zawartości:  

-   **Gdy klient żąda zawartości**, a lokalizacja sieciowa klienta należy do wielu grup granic, programu Configuration Manager wysyła klientowi listę wszystkich punktów dystrybucji zawierających daną zawartość.  
-   **Gdy klient żąda serwera, aby wysłać lub odebrać informacje o migracji stanu**, a lokalizacja sieciowa klienta należy do wielu grup granic, programu Configuration Manager wysyła klientowi listę punktów migracji stanu skojarzonych z grupą granic zawierającą bieżącą lokalizację sieciową klienta.  

Pozwala to klientowi na wybranie najbliższego serwera, z którego można przetransferować zawartość lub informacje o migracji stanu.  



## <a name="example-of-using-boundary-groups"></a>Przykład użycia grup granic
W poniższym przykładzie użyto wyszukiwanie zawartości z punktu dystrybucji klienta. W tym przykładzie można zastosować do innych ról systemu lokacji, które używają grup granic. Jednak ponieważ dotyczy punktów aktualizacji oprogramowania, należy pamiętać, punktów aktualizacji oprogramowania nie obsługuje konfiguracji czas w minutach powrotu do grupy sąsiada czy należy zawsze używać 120 minut.

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






### <a name="update-existing-boundary-groups-to-the-new-model"></a>Aktualizowanie istniejących grup granic do nowego modelu
Podczas aktualizacji do wersji przed 1610 następujące konfiguracje zostaną zastosowane automatycznie. Są one przeznaczone do upewnij się, że Twoje bieżące działanie rezerwowe pozostaje dostępna, dopóki nie skonfigurujesz nowych grup granic i relacje.

-   Grupy granic lokacji domyślnej jest tworzona dla każdej lokacji głównej, nazwa jest ***domyślna--grupy granic lokacji —&lt;kod lokacji >.***
  - Punkty dystrybucji z *Zezwalaj na rezerwową lokalizację źródła zawartości* zaznaczone i punktów migracji stanu w lokacjach głównych są dodawane do *domyślna--grupy granic lokacji&lt;kod lokacji >* grupy granic w tej lokacji.
  - Począwszy od wersji 1702, punkty aktualizacji oprogramowania są dodawane do każdej lokacji *domyślna--grupy granic lokacji&lt;kod lokacji >*.
-   Kopia składa się z każdej istniejącej grupy granic, która obejmuje serwer lokacji skonfigurowany z wolnego połączenia. Nazwa nowej grupy jest *** &lt;oryginalna nazwa grupy granic >-&lt;pierwotny identyfikator grupy granic >***:  
    -   Systemy lokacji, które mają szybkiego połączenia są pozostawiane w oryginalnej grupy granic.
    -   Kopię systemy lokacji (punkty dystrybucji, punkty zarządzania), które mają wolne połączenia są dodawane do kopii grupy granic. Systemy lokacji oryginalnej skonfigurowana jako niska pozostają w jego oryginalnej grup granic w celu zgodności z poprzednimi wersjami, ale nie są używane z tych grup granic.
    - Ta kopia grupy granic nie ma granicach skojarzonych z nim. Jednak tworzone jest połączenie rezerwowy między oryginalnej grupy i nową kopię grupy granic o czasie rezerwowy ustawić na zero.  


- **Specyficzne dla dodatkowej lokacji:**
  - Grupy granic jest tworzony, jeśli Lokacja pomocnicza ma co najmniej jeden punkt z dystrybucji *Zezwalaj na rezerwową lokalizację źródła zawartości* punktu migracji zaznaczone lub stanu. Nazwa grupy granic to ***pomocniczy-witryny-sąsiada — Tmp&lt;kod lokacji >.***
  - Punkty dystrybucji wszystkich z *Zezwalaj na rezerwową lokalizację źródła zawartości* zaznaczone i punktów migracji stanu zostaną dodane do tej grupy granic nowo utworzony lokacji dodatkowej.
  - Tworzone jest połączenie rezerwowy między oryginalnej grupy granic i grupy granic sąsiada nowo utworzony i czas rezerwowego jest ustawiony na zero.


 W poniższej tabeli przedstawiono nowe działanie rezerwowe można spodziewać się z kombinacji oryginalne ustawienia wdrożenia i punktu dystrybucji konfiguracje:

Oryginalna konfiguracja wdrożenia "Nie należy uruchamiać program" w wolnej sieci  |Punkt dystrybucji oryginalnej konfiguracji "Client Zezwalaj na użycie rezerwowej lokalizacji źródła zawartości"  |Nowe działanie rezerwowe  
---------|---------|---------
Wybrane     |  Wybrane    |  **Rezerwowe nie** -punktów dystrybucji należy używać tylko w bieżącej grupie granic       
Wybrane     |  Nie wybrano|  **Rezerwowe nie** -punktów dystrybucji należy używać tylko w bieżącej grupie granic       
Nie wybrano |  Nie wybrano|  **Powrót do sąsiada** — używać punktów dystrybucji w bieżącej grupie granic, a następnie dodaj punkty dystrybucji z grupy granic sąsiedniego. Chyba że jawne łącze do domyślnej grupy granic lokacji jest skonfigurowany, klienci nie będą powrotu do tej grupy.    
Nie wybrano | Wybrane     |   **Normalne powrotu** -używać punktów dystrybucji w bieżącej grupie granic, a następnie od sąsiada i lokacji domyślnych grup granic

 Wszystkie konfiguracje wdrożenia powoduje **normalne powrotu**.  




## <a name="changes-from-prior-versions-for-ui-and-behavior-for-content-locations"></a>Zmiany z wcześniejszych wersji interfejsu użytkownika i zachowanie dla lokalizacji zawartości
Poniżej przedstawiono zmiany klucza do grupy granic i jak klienci znajdują zawartości. Zmiany zostaną wprowadzone w wersji 1610. Wiele z tych zmian i pojęcia współdziałają ze sobą.


-   **Konfiguracje dla Fast lub wolno zostaną usunięte:** Można już konfigurować poszczególne punkty dystrybucji można dużą lub małą.  Zamiast tego jest traktowany każdego systemu lokacji skojarzone z grupą granic takie same. Z powodu tej zmiany **odwołania** na karcie właściwości grupy granic już nie obsługuje konfiguracji Fast lub niska.
-   **Nową grupę granic domyślne w każdej lokacji:**  Każda lokacja główna ma nowej grupy granic domyślny o nazwie ***domyślna--grupy granic lokacji&lt;kod lokacji >***.  Gdy klient nie jest w lokalizacji sieciowej, która jest przypisana do grupy granic, klient użyje systemy lokacji skojarzone z domyślnej grupy z przypisanej lokacji. Zaplanuj użycie tej grupy granic w zastępstwie koncepcję rezerwowej lokalizacji zawartości.      
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

    - Jeśli klient nie może znaleźć lokalizację poprawne źródło zawartości z jego *bieżącego* puli przed okresem powrotu do *sąsiada* osiągnięciu grupy granic, klient następnie dodaje punktów dystrybucji niż *sąsiada* grupy w celu jego bieżącej listy i będzie wyszukiwać rozwiniętej grupy lokalizacje źródłowe zawiera punkty dystrybucji z obu tych grup granic.

        > [!TIP]  
        > Podczas tworzenia wyraźnego związku z bieżącej grupy granic do domyślnej grupy granic lokacji i rezerwowy czasu, która jest mniejsza niż rezerwowy czasu dla łącza do grupy granic sąsiada, klienci rozpocznie się wyszukiwanie źródła lokalizacji do domyślnej grupy granic lokacji przed dołączeniem grupy sąsiedniego.

    - Gdy klient nie można pobrać zawartości z ostatniego serwera w puli, rozpoczyna proces ponownie.


## <a name="procedures-for-boundary-groups"></a>Procedury dotyczące grup granic
Poniższe procedury dotyczą wersji 1610 lub nowszej. Jeśli używasz wersji przed 1610, zapoznaj się z procedurami w [grup granic dla programu System Center Configuration Manager w wersji 1511, 1602 i 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606).


### <a name="to-create-a-boundary-group"></a>Aby utworzyć grupę granic  
1.  W konsoli programu Configuration Manager kliknij **administracji** > **Konfiguracja hierarchii** >  **grup granic**.  

2.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz grupę granicę**.  

3.  W oknie dialogowym **Utwórz grupę granicę** wybierz kartę **Ogólne** i określ **nazwę** tej grupy granic.  

4.  Kliknij przycisk **OK** , aby zapisać nową grupę granic.  


### <a name="to-configure-a-boundary-group"></a>Aby skonfigurować grupę granic  
 1.  W konsoli programu Configuration Manager kliknij **administracji** > **Konfiguracja hierarchii** >  **grup granic**.  

 2.  Wybierz grupę granic, którą chcesz zmodyfikować.  

 3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

 4.  W oknie dialogowym **Właściwości** dla grupy granic wybierz kartę **Ogólne** , aby zmodyfikować granice należące do tej grupy granic:  

     -   Aby dodać granice, kliknij przycisk **Dodaj**, zaznacz pole wyboru przynajmniej jednej granicy, a następnie kliknij przycisk **OK**.  

     -   Aby usunąć granicę, wybierz granicę i kliknij przycisk **Usuń**.  

 5.  Wybierz kartę **Odwołania** , aby zmodyfikować konfigurację przypisania lokacji i konfigurację skojarzonego serwera systemu lokacji:  

     -   Aby umożliwić użycie tej grupy granic przez klientów do przypisania lokacji, zaznacz pole wyboru **Użyj tej grupy granic do przypisania lokacji**, a następnie wypisz lokację z listy rozwijanej **Przypisana lokacja** .  

     -   Aby skonfigurować dostępne serwery systemu lokacji, które będą skojarzone z tą grupą granic:  

     1.  Kliknij przycisk **Dodaj**, a następnie zaznacz pole wyboru dla przynajmniej jednego serwera. Serwery zostaną dodane jako skojarzone serwery systemu lokacji dla tej grupy granic. Dostępne będą tylko serwery, na których zainstalowano obsługiwaną rolę systemu lokacji.  

         > [!NOTE]  
         >  Można wybrać dowolną kombinację dostępnych systemów lokacji z dowolnej lokacji w hierarchii. Wybrane systemy lokacji są wyświetlane na karcie **Systemy lokacji** we właściwościach wszystkich granic należących do tej grupy granic.  

     2.  Aby usunąć serwer z grupy granic, wybierz serwer i kliknij przycisk **Usuń**.  

         > [!NOTE]  
         >  Aby przestać używać tej grupy granic na potrzeby kojarzenia systemów lokacji, należy usunąć wszystkie serwery wyświetlane jako skojarzone serwery systemu lokacji.  

 6.  Wybierz **relacje** kartę, aby skonfigurować działanie rezerwowe:  

     - Kliknij przycisk **Dodaj**, a następnie wybierz grupę granic, w której chcesz skonfigurować.

     - Ustaw czas rezerwowy dla punktów dystrybucji. Po tym okresie klienci w grupie granic, konfigurowanej relacji, będzie można rozpocząć wyszukiwanie zawartości z punktów dystrybucji do grupy granic, który dodajesz.

     - Aby zapobiec powrotu do określonej grupy, łącznie z *domyślnej grupy granic lokacji* jest domyślnie skonfigurowany, wybierz grupę granic, a następnie zaznacz pole wyboru, aby uzyskać **nigdy rezerwowy**.   

 7.  Kliknij przycisk **OK** , aby zamknąć właściwości grupy granic i zapisać konfigurację.  

#### <a name="to-associate-a-site-systme-server-with-a-boundary-group"></a>Aby skojarzyć z grupą granic serwera systemu lokacji  
 1.  W konsoli programu Configuration Manager kliknij **administracji** > **Konfiguracja hierarchii** >  **grup granic**.  

 2.  Wybierz grupę granic, którą chcesz zmodyfikować.  

 3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

 4.  W oknie dialogowym **Właściwości** dla grupy granic wybierz kartę **Odwołania** .  

 5.  W sekcji **Wybierz serwery systemu lokacji**kliknij przycisk **Dodaj**, zaznacz pola wyboru dla serwerów systemu lokacji, które chcesz skojarzyć z tą grupą granic, a następnie kliknij przycisk **OK**.  

 6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe i zapisać konfigurację grupy granic.  


#### <a name="to-configure-a-fallback-site-for-automatic-site-assignment"></a>Aby skonfigurować lokację rezerwową na użytek automatycznego przypisywania lokacji  

  1.  W konsoli programu Configuration Manager kliknij **administracji** > **konfiguracja lokacji** >  **witryny**.  

  2.  Na karcie **Narzędzia główne** w grupie **Lokacje** kliknij przycisk **Ustawienia hierarchii**.  

  3.  Na karcie **Ogólne** zaznacz pole wyboru **Użyj lokacji rezerwowej**, a następnie wybierz lokację z listy rozwijanej **Lokacja rezerwowa** .  

  4.  Kliknij przycisk **OK** , aby zapisać konfigurację.  

#### <a name="to-enable-use-of-preferred-management-points"></a>Aby włączyć korzystanie z preferowanych punktów zarządzania  

 1.  W konsoli programu Configuration Manager kliknij **administracji** > **konfiguracja lokacji** > **witryny**, a następnie na **Home** wybierz pozycję **ustawienia hierarchii**.  

 2.  Na karcie **Ogólne** w obszarze Ustawienia hierarchii wybierz pozycję **Klienci wolą używać punktów zarządzania określonych w grupach granic**.  

 3.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe i zapisać konfigurację.  
