---
title: "Operacje i Obsługa raportowania | Dokumentacja firmy Microsoft"
description: "Dowiedz się, szczegółowe informacje o zarządzaniu raportami i subskrypcjami raportów w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b89bcfbf-f5b6-4fb1-bb5e-a5cc18ec0c78
caps.latest.revision: "5"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: df572cd0c64c82e25164430a53e1b893b3ba3cf5
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="operations-and-maintenance-for-reporting-in-system-center-configuration-manager"></a>Operacje i Obsługa raportowania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Po odpowiedniej infrastruktury w celu raportowania w programie System Center Configuration Manager, istnieje wiele operacji wykonywanych zwykle do zarządzania raportami i subskrypcjami raportów.  

##  <a name="BKMK_ManageReports"></a>Zarządzanie raportami programu Configuration Manager  
 Configuration Manager udostępnia ponad 400 wstępnie zdefiniowanych raportów, które ułatwiają gromadzić, organizować i prezentować informacje o użytkownikach, sprzętu i spisu oprogramowania, aktualizacje oprogramowania, aplikacje, stan lokacji i innych operacji programu Configuration Manager w organizacji. Za pomocą wstępnie zdefiniowanych raportów, ponieważ są one lub zmodyfikować raport, zgodnie z wymaganiami. Można również tworzyć niestandardowe modelu\-na podstawie i SQL\-na podstawie raportów zgodnie z wymaganiami. Poniższe sekcje umożliwiają pomocne w zarządzaniu raportami programu Configuration Manager.  

###  <a name="BKMK_RunReport"></a>Uruchamianie raportu programu Configuration Manager  
 Raporty w programie Configuration Manager są przechowywane w usługach SQL Server Reporting Services, a dane renderowane w raporcie są pobierane z bazy danych lokacji programu Configuration Manager. Dostępne raporty w konsoli programu Configuration Manager lub za pomocą Menedżera raportów, otwieranego w przeglądarce sieci web. Możesz otworzyć raporty na dowolnym komputerze, który ma dostęp do komputera, na którym działa program SQL Server Reporting Services, a musi mieć wystarczające uprawnienia do wyświetlania raportów. Po uruchomieniu raportu, tytuł, opis i kategoria są wyświetlane w języku lokalnego systemu operacyjnego.  

> [!NOTE]  
>  W niektórych z systemem innym niż\-angielski języków, znaki mogą być wyświetlane prawidłowo w raportach.  W takim przypadku raporty można wyświetlać przy użyciu sieci web\-na podstawie Menedżera raportów lub za pośrednictwem zdalnej konsoli administratora.  

> [!WARNING]  
>  Aby uruchamiać raporty, musisz mieć **odczytu** prawa dla **lokacji** uprawnień i **Uruchom raport** skonfigurowane pod kątem konkretnych obiektów.  

> [!IMPORTANT]    
> Musi istnieć zaufanie dwukierunkowe dla użytkowników z innej domeny niż konto punktu Servicies raportowania do pomyślnego uruchomienia raportów.

> [!NOTE]  
>  Menedżer raportów to sieci web\-narzędzia dostępu i zarządzania raport, który służy do administrowania pojedynczym wystąpieniem serwera raportów w zdalnej lokalizacji za pośrednictwem połączenia HTTP. Służy Menedżer raportów do zadań operacyjnych, na przykład do wyświetlania raportów, modyfikowania właściwości raportu i zarządzanie subskrypcjami raportów skojarzone. W tym temacie przedstawiono procedury wyświetlania raportu i modyfikowania właściwości raportu w Menedżerze raportów, ale więcej informacji o innych opcjach dostępnych w Menedżerze raportów znajduje, zobacz [Menedżera raportów](http://go.microsoft.com/fwlink/p/?LinkId=224916) w dokumentacji SQL Server 2008 — książki Online.  

 Użyj poniższych procedur do uruchamiania raportu programu Configuration Manager.  

##### <a name="to-run-a-report-in-the-configuration-manager-console"></a>Aby uruchomić raport w konsoli programu Configuration Manager  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **raportowania**, a następnie kliknij przycisk **raporty** Aby wyświetlić listę dostępnych raportów.  

    > [!IMPORTANT]  
    >  W tej wersji programu Configuration Manager **całą zawartość** wyświetlają tylko pakiety, nie aplikacje.  

    > [!TIP]  
    >  Jeśli nie są wyświetlane żadne raporty, sprawdź, czy punkt usług raportowania jest zainstalowana i skonfigurowana. Aby uzyskać więcej informacji, zobacz [konfigurowanie raportowania](configuring-reporting.md).  

3.  Wybierz raport, który chcesz uruchomić, a następnie na **Home** karcie **Grupa raportów** , kliknij przycisk **Uruchom** aby otworzyć raport.  

4.  Gdy są wymagane jakieś parametry, określ parametry, a następnie kliknij przycisk **Wyświetl raport**.  

#### <a name="to-run-a-report-in-a-web-browser"></a>Aby uruchomić raport w przeglądarce sieci web  

1.  W przeglądarce sieci web wprowadź adres URL Menedżera raportów, na przykład **http:\/\/serwer1\/raporty**. Adres URL Menedżera raportów możesz ustalić na **adres URL Menedżera raportów** strony w Reporting Services Configuration Manager.  

2.  W Menedżerze raportów kliknij folder raportów dla programu Configuration Manager, na przykład **ConfigMgr\_urzędów certyfikacji**.  

    > [!TIP]  
    >  Jeśli nie są wyświetlane żadne raporty, sprawdź, czy punkt usług raportowania jest zainstalowana i skonfigurowana. Aby uzyskać więcej informacji, zobacz [konfigurowanie raportowania](configuring-reporting.md).  

3.  Kliknij kategorię raportu, który chcesz uruchomić, a następnie kliknij łącze raportu. Raport zostanie otwarty w Menedżerze raportów.  

4.  Gdy są wymagane jakieś parametry, określ parametry, a następnie kliknij przycisk **Wyświetl raport**.  

###  <a name="BKMK_ModifyReportProperties"></a>Modyfikowanie właściwości raportu programu Configuration Manager  
 W konsoli programu Configuration Manager można wyświetlać właściwości raportu, takie jak nazwa i opis, ale aby zmienić właściwości, należy użyć Menedżera raportów. Użyj poniższej procedury można zmodyfikować właściwości raportu programu Configuration Manager.  

#### <a name="to-modify-report-properties-in-report-manager"></a>Aby zmodyfikować właściwości raportu w Menedżerze raportów  

1.  W przeglądarce sieci web wprowadź adres URL Menedżera raportów, na przykład **http:\/\/serwer1\/raporty**. Adres URL Menedżera raportów możesz ustalić na **adres URL Menedżera raportów** strony w Reporting Services Configuration Manager.  

2.  W Menedżerze raportów kliknij folder raportów dla programu Configuration Manager, na przykład **ConfigMgr\_urzędów certyfikacji**.  

    > [!TIP]  
    >  Jeśli nie są wyświetlane żadne raporty, sprawdź, czy punkt usług Reporting Services jest zainstalowana i skonfigurowana. Aby uzyskać więcej informacji, zobacz [konfigurowanie raportowania](configuring-reporting.md)  

3.  Kliknij kategorię raportu, dla której chcesz zmodyfikować właściwości raportu, a następnie kliknij łącze raportu. Raport zostanie otwarty w Menedżerze raportów.  

4.  Kliknij przycisk **właściwości** kartę. Nazwa i opis można zmodyfikować.  

5.  Gdy skończysz, kliknij przycisk **Zastosuj**. Właściwości raportu zostają zapisane na serwerze raportów i konsoli programu Configuration Manager pobiera zaktualizowane właściwości raportu.  

###  <a name="BKMK_EditReport"></a>Edytowanie raportu programu Configuration Manager  
 Jeśli istniejący raport programu Configuration Manager nie pobiera informacje, które muszą mieć albo nie oferuje układu lub struktury, która ma, można edytować raportu w programie Report Builder.  

> [!NOTE]  
>  Istnieje również możliwość Sklonowanie istniejącego raportu, otwierając go w celu edycji, a następnie klikając polecenie **Zapisz jako** ją zapisać jako nowy raport.  

> [!IMPORTANT]  
>  Konto użytkownika musi mieć **modyfikacja lokacji** uprawnień i **modyfikowanie raportu** uprawnienia do konkretnych obiektów skojarzonych z raportem, który chcesz zmodyfikować.  

> [!IMPORTANT]  
>  Po uaktualnieniu programu Configuration Manager do nowszej wersji, nowe raporty zastępują raporty wstępnie zdefiniowane. W przypadku zmodyfikowanego wstępnie zdefiniowanego raportu należy wykonać kopię raportu przed zainstalowanie nowej wersji, a potem Przywróć raport w usługach Reporting Services. Jeśli są istotne zmiany wstępnie zdefiniowanych raportów, należy wziąć pod uwagę zamiast tworzenia nowego raportu. Nowe raporty utworzone przed uaktualniania lokacji nie zostaną zastąpione.  

 Użyj poniższej procedury, aby edytować właściwości raportu programu Configuration Manager.  

#### <a name="to-edit-report-properties"></a>Aby edytować właściwości raportu  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **raportowania**, a następnie kliknij przycisk **raporty** Aby wyświetlić listę dostępnych raportów.  

3.  Wybierz raport, który chcesz zmodyfikować, a następnie na **Home** karcie **Grupa raportów** , kliknij przycisk **Edytuj**. Wprowadź konto użytkownika i hasło, jeśli są monitowani o, a następnie kliknij przycisk **OK**. Jeśli na komputerze nie zainstalowano programu Report Builder, są monit o jej zainstalowanie. Kliknij przycisk **Uruchom** Aby zainstalować program Report Builder, który jest wymagany do modyfikowania i tworzenia raportów.  

4.  W programie Report Builder zmodyfikuj odpowiednie ustawienia raportu, a następnie kliknij przycisk **zapisać** Aby zapisać raport na serwerze raportów.  

###  <a name="BKMK_CreateModelBasedReport"></a>Tworzenie modelu\-na podstawie raportu  
 Model\-na podstawie raportu pozwala interaktywnie wybierać elementy mają zostać uwzględnione w raporcie. Aby uzyskać więcej informacji o tworzeniu niestandardowych modeli raportów, zobacz [Tworzenie niestandardowych modeli raportów programu System Center Configuration Manager w SQL Server Reporting Services](creating-custom-report-models-in-sql-server-reporting-services.md).  

> [!IMPORTANT]  
>  Konto użytkownika musi mieć **modyfikacja lokacji** uprawnienia do tworzenia nowego raportu. Użytkownik może utworzyć raport tylko w folderach, do których użytkownik ma **modyfikowanie raportu** uprawnienia.  

 Poniższa procedura umożliwia utworzenie modelu\-na podstawie raportu programu Configuration Manager.  

#### <a name="to-create-a-model-based-report"></a>Aby utworzyć model\-na podstawie raportu  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **raportowania** i kliknij przycisk **raporty**.  

3.  Na **Home** karcie **Utwórz** , kliknij przycisk **Utwórz raport** otworzyć **Kreatora tworzenia raportu**.  

4.  Na **informacji** skonfiguruj następujące ustawienia:  

    -   **Typ**: Wybierz **modelu\-na podstawie raportu** Aby utworzyć raport w programie Report Builder z wykorzystaniem modelu usług Reporting Services.  

    -   **Nazwa**: Określ nazwę dla raportu.  

    -   **Opis elementu**: Określ opis raportu.  

    -   **Serwer**: Wyświetla nazwę serwera raportów, na którym jest tworzony dany raport.  

    -   **Ścieżka**: Kliknij przycisk **Przeglądaj** Aby określić folder, w którym mają być przechowywane w raporcie.  

     Kliknij przycisk **Dalej**.  

5.  Na **wybór modelu** stronie, wybierz dostępny model z listy używanej do tworzenia tego raportu. Kiedy wybierzesz model raportu **Podgląd** wyświetlą się widoki programu SQL Server i jednostek, które są udostępniane przez wybrany model raportu.  

6.  Na stronie **Podsumowanie** przejrzyj ustawienia. Kliknij przycisk **Wstecz** Aby zmienić ustawienia, lub kliknij przycisk **dalej** Aby utworzyć raport w programie Configuration Manager.  

7.  Na **potwierdzenie** kliknij przycisk **Zamknij** aby zakończyć pracę kreatora, a następnie otwórz program Report Builder, aby skonfigurować ustawienia raportu. Wprowadź konto użytkownika i hasło, jeśli są monitowani o, a następnie kliknij przycisk **OK**. Jeśli na komputerze nie zainstalowano programu Report Builder, są monit o jej zainstalowanie. Kliknij przycisk **Uruchom** Aby zainstalować program Report Builder, który jest wymagany do modyfikowania i tworzenia raportów.  

8.  W programie Microsoft Report Builder Utwórz układ raportu, wybierz dane w dostępnych widokach programu SQL Server Dodaj do raportu parametry i tak dalej. Aby uzyskać więcej informacji na temat do utworzenia nowego raportu przy użyciu programu Report Builder zobacz temat Pomocy programu Report Builder.  

9. Kliknij przycisk **Uruchom** do uruchomienia raportu. Sprawdź, czy raport podaje oczekiwane informacje. Kliknij przycisk **projekt** aby powrócić do widoku projektu i zmodyfikować raport, jeśli to konieczne.  

10. Kliknij przycisk **zapisać** Aby zapisać raport na serwerze raportów. Mogą uruchamiać i modyfikować nowy raport w **raporty** w węźle **monitorowanie** obszaru roboczego.  

###  <a name="BKMK_CreateSQLBasedReport"></a>Utwórz SQL\-na podstawie raportu  
 SQL\-na podstawie raportu pozwala pobierać dane oparte na instrukcji SQL raportu.  

> [!IMPORTANT]  
>  Podczas tworzenia instrukcji SQL dla raportu niestandardowego, nie należy bezpośrednio odwoływać tabel programu SQL Server. Zamiast tego należy odwoływać raportowania widoki programu SQL Server \(wyświetlić nazwy zaczynające się od v\_ \) z bazy danych lokacji. Można także odwoływać się do publicznych procedur składowanych \(przechowywane procedury o nazwach zaczynających sp\_ \) z bazy danych lokacji.  

> [!IMPORTANT]  
>  Konto użytkownika musi mieć **modyfikacja lokacji** uprawnienia do tworzenia nowego raportu. Użytkownik może utworzyć raport tylko w folderach, do których użytkownik ma **modyfikowanie raportu** uprawnienia.  

 Poniższa procedura umożliwia utworzenie SQL\-na podstawie raportu programu Configuration Manager.  

#### <a name="to-create-a-sql-based-report"></a>Aby utworzyć SQL\-na podstawie raportu  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W obszarze roboczym **Monitorowanie** rozwiń węzeł **Raportowanie**, a następnie kliknij przycisk **Raporty**.  

3.  Na **Home** karcie **Utwórz** , kliknij przycisk **Utwórz raport** otworzyć **Kreatora tworzenia raportu**.  

4.  Na **informacji** skonfiguruj następujące ustawienia:  

    -   **Typ**: Wybierz **SQL\-na podstawie raportu** Aby utworzyć raport w programie Report Builder z wykorzystaniem instrukcji SQL.  

    -   **Nazwa**: Określ nazwę dla raportu.  

    -   **Opis elementu**: Określ opis raportu.  

    -   **Serwer**: Wyświetla nazwę serwera raportów, na którym jest tworzony dany raport.  

    -   **Ścieżka**: Kliknij przycisk **Przeglądaj** Aby określić folder, w którym mają być przechowywane w raporcie.  

     Kliknij przycisk **Dalej**.  

5.  Na stronie **Podsumowanie** przejrzyj ustawienia. Kliknij przycisk **Wstecz** Aby zmienić ustawienia, lub kliknij przycisk **dalej** Aby utworzyć raport w programie Configuration Manager.  

6.  Na **potwierdzenie** kliknij przycisk **Zamknij** aby zakończyć działanie kreatora i Otwórz program Report Builder, aby skonfigurować ustawienia raportu. Wprowadź konto użytkownika i hasło, jeśli są monitowani o, a następnie kliknij przycisk **OK**. Jeśli na komputerze nie zainstalowano programu Report Builder, są monit o jej zainstalowanie. Kliknij przycisk **Uruchom** Aby zainstalować program Report Builder, który jest wymagany do modyfikowania i tworzenia raportów.  

7.  W programie Microsoft Report Builder Podaj instrukcję SQL dla raportu lub Skonstruuj instrukcję SQL przy użyciu kolumn w dostępnych widokach programu SQL Server, Dodaj do raportu parametry i tak dalej.  

8.  Kliknij przycisk **Uruchom** do uruchomienia raportu. Sprawdź, czy raport podaje oczekiwane informacje. Kliknij przycisk **projekt** aby powrócić do widoku projektu i zmodyfikować raport, jeśli to konieczne.  

9. Kliknij przycisk **zapisać** Aby zapisać raport na serwerze raportów. Nowy raport możesz uruchamiać **raporty** w węźle **monitorowanie** obszaru roboczego.  

##  <a name="BKMK_ManageReportSubscriptions"></a>Zarządzanie subskrypcjami raportów  
 Subskrypcje raportów w usługach SQL Server Reporting Services pozwalają skonfigurować automatyczne dostarczanie określonych raportów pocztą e-mail lub do udziału plików w zaplanowanych odstępach czasu. Użyj **Kreatora tworzenia subskrypcji** w System Center 2012 Configuration Manager do konfigurowania subskrypcji raportów.  

###  <a name="BKMK_ReportSubscriptionFileShare"></a>Tworzenie subskrypcji raportów w celu dostarczania raportu do udziału plików  
 Podczas tworzenia subskrypcji raportów w celu dostarczania raportu do udziału plików raport jest kopiowany do określonego udziału plików w określonym formacie. Można subskrybować i żądanie dostarczania dla tylko jednego raportu naraz.  

 W przeciwieństwie do raportów, które są obsługiwane i zarządzane przez serwer raportów raporty, które są dostarczane do folderu udostępnionego są plikami statycznymi. Są zdefiniowane dla raportu funkcje interaktywne nie działają w przypadku raportów, które są przechowywane jako pliki w systemie plików. Funkcje interakcji są reprezentowane jako elementy statyczne. Jeśli raport zawiera wykresy, jest używany domyślny sposób ich prezentacji. Jeśli raport zawiera łącza do innego raportu, łącze jest renderowane jako tekst statyczny. Jeśli chcesz zachować funkcje interaktywne, aby w dostarczanym raporcie, należy użyć dostarczania poczty e-mail. Aby uzyskać więcej informacji o dostarczaniu pocztą e-mail, zobacz [Tworzenie subskrypcji raportów w celu dostarczenia raportu pocztą e-mail](#BKMK_ReportSubscriptionEmail) później w tym temacie.  

 Podczas tworzenia subskrypcji, która używa dostarczania udziału pliku należy określić istniejący folder jako folder docelowy. Serwer raportów nie tworzy folderów w systemie plików. Folder, w którym można określić muszą być dostępne za pośrednictwem połączenia sieciowego. Po określeniu folder docelowy w ramach subskrypcji, użyć ścieżki UNC i końcowych ukośników odwrotnych w ścieżce folderu. Na przykład jest prawidłowa ścieżka UNC do folderu docelowego: \\ \\ &lt;servername\>\\reportfiles\\operacji\\2011.  

 Raporty mogą być renderowane w różnych formatach, takich jak MHTML czy Excel. Aby zapisać raport w określonym formacie pliku, należy wybrać ten format renderowania podczas tworzenia subskrypcji. Na przykład wybranie opcji Excel zapisuje raport w formacie programu Microsoft Excel. Chociaż możesz użyć dowolnego z obsługiwanych formatów renderowania, niektóre formaty działają lepiej od innych podczas renderowania do pliku.  

 Poniższa procedura umożliwia utworzenie subskrypcji raportów w celu dostarczania raportu do udziału plików.  

#### <a name="to-create-a-report-subscription-to-deliver-a-report-to-a-file-share"></a>Aby utworzyć subskrypcję raportów w celu dostarczania raportu do udziału plików  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **raportowania** i kliknij przycisk **raporty** Aby wyświetlić listę dostępnych raportów. Można wybrać folder raportów, aby wyświetlić tylko raporty, które są skojarzone z danym folderem.  

3.  Wybierz raport, który chcesz dodać do subskrypcji, a następnie na **Home** karcie **Grupa raportów** , kliknij przycisk **Utwórz subskrypcję** otworzyć **Kreatora tworzenia subskrypcji**.  

4.  Na **dostarczanie subskrypcji** skonfiguruj następujące ustawienia:  

    -   Raport dostarczony przez: Wybierz **udostępnianie plików systemu Windows** aby dostarczyć raport do udziału plików.  

    -   **Nazwa pliku**: Określ nazwę pliku raportu. Domyślnie plik raportu nie zawiera rozszerzenia nazwy pliku. Wybierz **Dodaj rozszerzenie pliku po utworzeniu** można automatycznie dodać rozszerzenie nazwy pliku do tego raportu na podstawie formatu renderowania.  

    -   **Ścieżka**: Określ ścieżkę UNC do istniejącego folderu, w którym chcesz dostarczyć ten raport \(na przykład \\ \\ &lt;nazwy serwera\>\\&lt;udział serwera\>\\&lt;folder raportów\>\).  

        > [!NOTE]  
        >  Nazwa użytkownika określona dalej na tej strony musi mieć dostęp do tego udziału serwera i uprawnienia zapisu do folderu docelowego.  

    -   **Format renderowania**: Wybierz jedną z następujących formatów pliku raportu:  

        -   **Plik XML z danymi raportu**: Raport jest zapisywany w formacie Extensible Markup Language.  

        -   **CSV \(rozdzielany przecinkami\)**: Raport jest zapisywany w przecinkami\-oddzielone\-format wartości.  

        -   **Plik TIFF**: Raport jest zapisywany w formacie Tagged Image File Format.  

        -   **Acrobat \(PDF\) pliku**: Raport jest zapisywany w formacie Acrobat Portable Document Format.  

        -   **HTML 4.0**: Raport jest zapisywany jako strona sieci Web możliwa do wyświetlenia wyłącznie w przeglądarkach obsługujących język HTML 4.0. Internet Explorer 5 i nowsze wersje obsługują język HTML 4.0.  

            > [!NOTE]  
            >  Jeśli w raporcie znajdują się obrazy, format HTML 4.0 nie ma ich w pliku.  

        -   **MHTML \(archiwum sieci web\)**: Raport jest zapisywany w formacie MIME HTML \(mhtml\), która jest możliwa do wyświetlenia w wielu przeglądarkach sieci web.  

        -   **Moduł renderowania RPL**: Raport jest zapisywany w układ strony raportu \(RPL\) format.  

        -   **Excel**: Raport jest zapisywany jako arkusz kalkulacyjny programu Microsoft Excel.  

        -   **Word**: Raport jest zapisywany jako dokument programu Microsoft Word.  

    -   **Nazwa użytkownika**: Określ konto użytkownika systemu Windows z uprawnieniami dostępu do folderu i udziału na serwerze docelowym. Konto użytkownika musi mieć dostęp do tego udziału serwera i uprawnień do zapisu w folderze docelowym.  

    -   **Hasło**: Określ hasło dla konta użytkownika systemu Windows. W **Potwierdź hasło**, re\-wprowadź hasło.  

    -   Wybierz jedną z poniższych opcji, aby skonfigurować działanie, gdy w folderze docelowym istnieje plik o takiej samej nazwie:  

        -   **Zastąp istniejący plik nowszą wersją**: Określa, że jeśli plik raportu już istnieje, zostanie zastąpiony nową wersją go.  

        -   **Nie zastępuj istniejącego pliku**: Określa, jeśli plik raportu już istnieje, nie zostanie żadnej akcji.  

        -   **Zwiększaj przyrostowo nazwy plików w miarę dodawania nowszych wersji**: Określa, jeśli plik raportu już istnieje, nowy raport do nazwy pliku do odróżnienia go od innych wersji jest dodawany numer.  

    -   **Opis elementu**: Określa opis subskrypcji raportów.  

     Kliknij przycisk **Dalej**.  

5.  Na **harmonogram subskrypcji** wybierz jedną z następujących opcji harmonogramu dostaw dla subskrypcji raportów:  

    -   **Użyj harmonogramu współużytkowanego**: Udostępniony harmonogram to uprzednio zdefiniowany harmonogram, które mogą być używane przez inne Subskrypcje raportów. Zaznacz to pole wyboru, a następnie wybierz udostępniony harmonogram na liście, jeśli jest dostępny.  

    -   **Utwórz nowy harmonogram**: Skonfiguruj harmonogram, na którym ten raport jest uruchomiony, w tym interwał, godzinę rozpoczęcia i Data oraz datę zakończenia subskrypcji.  

6.  Na **parametry subskrypcji** Określ parametry tego raportu, które są używane podczas nienadzorowanego uruchamiania. Jeśli nie ma żadnych parametrów dla raportu, ta strona nie jest wyświetlana.  

7.  Na **Podsumowanie** Przejrzyj ustawienia subskrypcji raportów. Kliknij przycisk **Wstecz** Aby zmienić ustawienia, lub kliknij przycisk **dalej** do utworzenia subskrypcji raportu.  

8.  Aby zamknąć kreatora, kliknij na stronie **Ukończenie** przycisk **Zamknij** . Sprawdź, czy subskrypcja raportów została utworzona pomyślnie. Można wyświetlać i modyfikować subskrypcji raportów w **subskrypcje** węźle **raportowania** w **monitorowanie** obszaru roboczego.  

###  <a name="BKMK_ReportSubscriptionEmail"></a>Tworzenie subskrypcji raportów w celu dostarczenia raportu pocztą e-mail  
 Podczas tworzenia subskrypcji raportów w celu dostarczenia raportu pocztą e-mail zostanie wysłana wiadomość e-mail do odbiorców, które można skonfigurować, a raport jest dołączony jako załącznik. Serwer raportów nie weryfikuje adresów e-mail lub uzyskać adresy e-mail z serwera e-mail. Wcześniej należy znać, których chcesz używać adresów e-mail. Domyślnie poczty e-mail raporty na dowolne prawidłowe konta e-mail wewnątrz lub na zewnątrz organizacji. Możesz wybrać jedną lub obie następujące opcje dostawy poczty e-mail:  

-   Wysłanie powiadomienia i hiperłącza do wygenerowanego raportu.  

-   Wysłanie osadzonego lub dołączonego raportu. Format renderowania i przeglądarki sprawdzenia, czy raport jest osadzony dołączony. Jeśli przeglądarka obsługuje język HTML 4.0 i MHTML i wybierz MHTML \(archiwum sieci web\) renderowania format, raport zostanie osadzony jako część komunikatu. Wszystkich pozostałych formatów renderowania \(CSV, PDF, Word, i tak dalej\) dostarczania raportów jako załączniki. Usługi Reporting Services nie sprawdza rozmiaru załącznika ani wiadomości przed wysłaniem raportu. Jeśli załącznik lub wiadomość przekracza maksymalny limit dozwolony przez serwer poczty, raport nie zostanie dostarczony.  

> [!IMPORTANT]  
>  Należy skonfigurować ustawienia poczty e-mail w usługach Reporting Services dla **E-mail** opcja dostawy, które mają być dostępne. Aby uzyskać więcej informacji o konfigurowaniu ustawień poczty e-mail w usługach Reporting Services, zobacz [konfigurowania serwera raportów w celu dostarczania poczty E-mail](http://go.microsoft.com/fwlink/p/?LinkId=226668) w dokumentacji SQL Server — książki Online.  

 Poniższa procedura umożliwia utworzenie subskrypcji raportów w celu dostarczenia raportu za pomocą poczty e-mail.  

#### <a name="to-create-a-report-subscription-to-deliver-a-report-by-email"></a>Aby utworzyć subskrypcję raportów w celu dostarczenia raportu pocztą e-mail  

-   W konsoli programu Configuration Manager kliknij **monitorowanie**.  

-   W **monitorowanie** obszaru roboczego, rozwiń węzeł **raportowania** i kliknij przycisk **raporty** Aby wyświetlić listę dostępnych raportów. Można wybrać folder raportów wyświetlający tylko raporty, które są skojarzone z danym folderem.  

-   Wybierz raport, który chcesz dodać do subskrypcji, a następnie na **Home** karcie **Grupa raportów** , kliknij przycisk **Utwórz subskrypcję** otworzyć **Kreatora tworzenia subskrypcji**.  

-   Na **dostarczanie subskrypcji** skonfiguruj następujące ustawienia:  

    -   **Raport dostarczony przez**: Wybierz **E\-poczty** aby dostarczyć raport jako załącznik do wiadomości e-mail.  

    -   **Aby**: Określ prawidłowy adres e-mail do wysłania tego raportu.  

        > [!NOTE]  
        >  Możesz wprowadzić wielu adresatów wiadomości e-mail, Oddziel poszczególne adresy e-mail średnikami.  

    -   **DW**: Opcjonalnie określ adres e-mail, aby kopia tego raportu.  

    -   **UDW**: Opcjonalnie określ adres e-mail, aby zostać wysłana ukryta kopia tego raportu.  

    -   **Udzielenie odpowiedzi na**: Określ adres zwrotny do użycia, jeśli adresat odpowiedzi do wiadomości e-mail.  

    -   **Temat**: Określ wiersz tematu wiadomości e-mail subskrypcji.  

    -   **Priorytet**: Wybierz flagę priorytetu dla tej wiadomości e-mail. Wybierz **małej**, **normalny**, lub **wysokiej**. Ustawienie priorytetu jest używane przez program Microsoft Exchange do ustawienia flagi informującej o ważności wiadomości e-mail.  

    -   **Komentarz**: Określ tekst, który ma być dodany do treści wiadomości e-mail subskrypcji.  

    -   **Opis elementu**: Określ opis dla tej subskrypcji raportu.  

    -   **Dołącz łącze**: Zawiera adres URL subskrybowanego raportu w treści wiadomości e-mail.  

    -   **Dołącz raport**: Określ, czy raport jest dołączony do e\-wiadomości e-mail. Format dołączany raport został określony w **Format renderowania** listy.  

    -   **Format renderowania**: Wybierz jedną z następujących formatów dla dołączanego raportu:  

        -   **Plik XML z danymi raportu**: Raport jest zapisywany w formacie Extensible Markup Language.  

        -   **CSV \(rozdzielany przecinkami\)**: Raport jest zapisywany w przecinkami\-oddzielone\-format wartości.  

        -   **Plik TIFF**: Raport jest zapisywany w formacie Tagged Image File Format.  

        -   **Acrobat \(PDF\) pliku**: Raport jest zapisywany w formacie Acrobat Portable Document Format.  

        -   **MHTML \(archiwum sieci web\)**: Raport jest zapisywany w formacie MIME HTML \(mhtml\), która jest możliwa do wyświetlenia w wielu przeglądarkach sieci web.  

        -   **Excel**: Raport jest zapisywany jako arkusz kalkulacyjny programu Microsoft Excel.  

        -   **Word**: Raport jest zapisywany jako dokument programu Microsoft Word.  

-   Na **harmonogram subskrypcji** wybierz jedną z następujących opcji harmonogramu dostaw dla subskrypcji raportów:  

    -   **Użyj harmonogramu współużytkowanego**: Udostępniony harmonogram to uprzednio zdefiniowany harmonogram, które mogą być używane przez inne Subskrypcje raportów. Zaznacz to pole wyboru, a następnie wybierz udostępniony harmonogram na liście, jeśli jest dostępny.  

    -   **Utwórz nowy harmonogram**: Skonfiguruj harmonogram uruchamiania tego raportu, w tym interwał, godzinę rozpoczęcia i Data oraz datę zakończenia subskrypcji.  

-   Na **parametry subskrypcji** Określ parametry tego raportu, które są używane podczas nienadzorowanego uruchamiania. Jeśli nie ma żadnych parametrów dla raportu, ta strona nie jest wyświetlana.  

-   Na **Podsumowanie** Przejrzyj ustawienia subskrypcji raportów. Kliknij przycisk **Wstecz** Aby zmienić ustawienia, lub kliknij przycisk **dalej** do utworzenia subskrypcji raportu.  

-   Aby zamknąć kreatora, kliknij na stronie **Ukończenie** przycisk **Zamknij** . Sprawdź, czy subskrypcja raportów została utworzona pomyślnie. Można wyświetlać i modyfikować subskrypcji raportów w **subskrypcje** węźle **raportowania** w **monitorowanie** obszaru roboczego.  
