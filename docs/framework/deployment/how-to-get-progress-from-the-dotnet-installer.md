---
title: "Comment&#160;: obtenir la progression &#224; partir du programme d&#39;installation du .NET Framework&#160;4.5 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - ".NET Framework, installer"
  - "informations sur la progression, programme d'installation du .NET Framework"
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
caps.latest.revision: 30
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 30
---
# Comment&#160;: obtenir la progression &#224; partir du programme d&#39;installation du .NET Framework&#160;4.5
Le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] est un runtime redistribuable.  Si vous développez des applications pour cette version de .NET Framework, incluez \(chaînez\) le processus d'installation [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] comme une partie pré\-requise par l'installation de votre application.  Si vous voulez offrir une expérience d'installation personnalisée ou unifiée, vous pouvez lancer en arrière plan l'installation de [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] et en suivre la progression tout en affichant celle de l'installation de votre propre application.  Pour activer le suivi discret, l'installation de [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] \(qui peut être surveillée\) définit un protocole utilisant un segment mappé en mémoire d'E\/S \(MMIO\) pour communiquer avec votre installation \(l'observateur ou le programme de chaînage\).  Ce protocole définit un moyen d'un programme de chaînage obtenir les informations de progression, d'obtenir des résultats détaillés, de répondre aux messages, et d'annuler l'installation de [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  
  
-   **Appel**.  Pour appeler le processus d'installation de [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] et recevoir les informations de progression de la section MMIO, votre programme d'installation doit effectuer les opérations suivantes :  
  
    1.  Appelez le programme redistribuable [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] :  
  
        ```  
        dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name  
        ```  
  
         où *section name* correspond à un nom que vous souhaitez utiliser pour identifier votre application. L'installation de .NET Framework lit et écrit dans la section MMIO de façon asynchrone, donc il peut être utile d'utiliser des événements et des messages pendant ce temps.  Dans l'exemple, le processus d'installation de .NET Framework est créé par un constructeur qui alloue la section MMIO \(`TheSectionName`\) et définit un événement \(`TheEventName`\) :  
  
        ```  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")  
        ```  
  
         Remplacez ces noms par des noms uniques à votre programme d'installation.  
  
    2.  Lisez à partir de la section MMIO.  Dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], les opérations d'installation et de téléchargement sont simultanées : un partie du .NET Framework peut s'installer pendant le téléchargement d'un autre.  Par conséquent, la progression est renvoyée \(autrement dit, écrite\) dans la section MMIO comme deux nombres \(`m_downloadSoFar` et `m_installSoFar`\) qui augmentent de 0 à 255.  Lorsque 255 est écrit et que l'exécution de .NET Framework s'achève, l'installation est terminée.  
  
-   **Codes de sortie**.  Les codes de sortie suivants de la commande pour appeler le programme redistribuable de [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] indiquent si l'installation s'est terminée avec succès ou a échoué :  
  
    -   0 \- L'installation s'est terminée avec succès.  
  
    -   3010 \- L'installation s'est terminée avec succès ; un redémarrage du système est requis.  
  
    -   1602 – L'installation a été annulée.  
  
    -   Tous les autres codes \- Le programme d'installation a rencontré des erreurs ; examinez les fichiers journaux créés dans%temp% pour plus d'informations.  
  
-   **Annulation de l'installation**.  Vous pouvez annuler l'installation à tout moment à l'aide de la méthode `Abort` pour définir les indicateurs `m_downloadAbort` et `m_ installAbort` dans la section MMIO.  
  
## Exemple de programme de chaînage  
 L'exemple de programme de chaînage lance et suit discrètement l'installation de [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] en affichant la progression.  Cet exemple est similaire à l'exemple de programme de chaînage fourni pour .NET Framework 4.  Toutefois, en outre, il peut éviter le redémarrage du système en contrôlant la boîte de dialogue pour fermer les applications de .NET Framework 4.  Pour plus d'informations sur cette boîte de dialogue, consultez [Reducing System Restarts During .NET Framework 4.5 Installations](../../../docs/framework/deployment/reducing-system-restarts.md).  Vous pouvez utiliser cet exemple avec le programme d'installation de .NET Framework 4 ; dans ce cas, le message n'est simplement pas envoyé.  
  
> [!WARNING]
>  Vous devez exécuter l'exemple en tant qu'administrateur.  
  
 Téléchargez la solution complète pour Visual Studio de l'[exemple de Chainer .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkId=231345) à partir de la galerie d'exemples MSDN  
  
 Les sections suivantes décrivent les fichiers importants dans cet exemple : MMIOChainer.h, ChainingdotNet4.cpp, et IProgressObserver.h.  
  
#### MMIOChainer.h  
  
-   Le fichier MMIOChainer.h \(lire [le code complet](http://go.microsoft.com/fwlink/?LinkId=231369)\) contient la définition de la structure de données et la classe de base à partir desquelles la classe du programme de chaînage doit être dérivée.  Le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] étend la structure de données MMIO pour manipuler les données dont le programme d'installation de [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a besoin.  Les modifications apportées à la structure MMIO sont à compatibilité descendante, donc un programme de chaînage de .NET Framework 4 peut fonctionner avec le programme d'installation de .NET Framework 4.5 sans nécessiter de recompilation.  Toutefois, ce scénario ne prend pas en charge la fonctionnalité pour réduire les redémarrages du système.  
  
     Un champ de version fournit un moyen d'identifier des révisions sur la structure et le format de message.  L'installation de .NET Framework détermine la version de l'interface du programme de chaînage en appelant la fonction `VirtualQuery` pour déterminer la taille du mappage du fichier.  Si la taille est assez grande pour recevoir le champ de version, l'installation de .NET Framework utilise la valeur spécifiée.  Si le mappage du fichier est trop petit pour contenir un champ de version, ce qui est le cas avec .NET Framework 4, le processus d'installation considère la version 0 \(4\).  Si le programme de chaînage ne prend pas en charge la version du message que l'installation de .NET Framework souhaite envoyer, l'installation de .NET Framework considère une réponse ignorer.  
  
     La structure de données MMIO est définie comme suit.  
  
    ```cpp  
    // MMIO data structure for interprocess communication  
        struct MmioDataStructure  
        {  
            bool m_downloadFinished;               // Is download complete?  
            bool m_installFinished;                // Is installation complete?  
            bool m_downloadAbort;                  // Set to cause downloader to abort.  
            bool m_installAbort;                   // Set to cause installer to abort.  
            HRESULT m_hrDownloadFinished;          // Resulting HRESULT for download.  
            HRESULT m_hrInstallFinished;           // Resulting HRESULT for installation.  
            HRESULT m_hrInternalError;  
            WCHAR m_szCurrentItemStep[MAX_PATH];  
            unsigned char m_downloadSoFar;         // Download progress 0-255 (0-100% done).   
            unsigned char m_installSoFar;          // Installation progress 0-255 (0-100% done).  
            WCHAR m_szEventName[MAX_PATH];         // Event that chainer creates and chainee opens to sync communications.  
  
            BYTE m_version;                        // Version of the data structure, set by chainer:  
                                                   // 0x0: .NET Framework 4   
                                                   // 0x1: .NET Framework 4.5  
  
            DWORD m_messageCode;                   // Current message sent by the chainee; 0 if no message is active.  
            DWORD m_messageResponse;               // Chainer's response to current message; 0 if not yet handled.  
            DWORD m_messageDataLength;             // Length of the m_messageData field, in bytes.  
            BYTE m_messageData[1];                 // Variable-length buffer; content depends on m_messageCode.  
        };  
  
    ```  
  
-   La structure de données `MmioDataStructure` ne doit pas être utilisée directement ; utilisez la classe `MmioChainer` à la place pour implémenter votre programme de chaînage.  Dérivez de la classe `MmioChainer` pour chaîner le package redistribuable [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  
  
#### IProgressObserver.h  
  
-   Le fichier d'IProgressObserver.h implémente un observateur de progression \([consulter le code complet](http://go.microsoft.com/fwlink/?LinkId=231370)\).  L'observateur est averti de la progression du téléchargement et de l'installation \(spécifié avec un `char`non signé, 0\-255, indiquant 1 %\-100 % complet\).  L'observateur est également notifié lorsque l'élément chaîné envoie un message, et l'observateur doit envoyer une réponse.  
  
    ```cpp  
        class IProgressObserver  
        {  
        public:  
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%  
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete    
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent  
        };  
  
    ```  
  
#### ChainingdotNet4.5.cpp  
  
-   Le fichier [ChainingdotNet4.5.cpp](http://go.microsoft.com/fwlink/?LinkId=231368) implémente la classe `Server`, qui dérive de la classe `MmioChainer` et substitue les méthodes appropriées à l'affichage de vos informations de progression.  Le MmioChainer crée une section avec le nom de la section spécifiée et initialise le programme de chaînage avec le nom de l'événement spécifié.  Le nom de l'événement est enregistré dans la structure de données mappée.  Vous devez rendre la section et les noms d'événements uniques.  La classe `Server` dans le code suivant lance le programme d'installation spécifié, surveille sa progression et retourne un code de sortie.  
  
    ```cpp  
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver  
    {  
    public:  
        …………….  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names  
        {}  
  
    ```  
  
     L'installation débute dans la méthode Main.  
  
    ```cpp  
    // Main entry point for program  
    int __cdecl main(int argc, _In_count_(argc) char **_argv)  
    {  
        int result = 0;  
        CString args;  
        if (argc > 1)  
        {  
            args = CString(_argv[1]);  
        }  
  
        if (IsNetFx4Present(NETFX45_RC_REVISION))  
        {  
            printf(".NET Framework 4.5 is already installed");  
        }  
        else  
        {  
            result = Server().Launch(args);  
        }  
  
        return result;  
    }  
  
    ```  
  
-   Avant d'activer l'installation, le programme de chaînage vérifie si [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] est déjà installé en appelant `IsNetFx4Present` :  
  
    ```cpp  
    ///  Checks for presence of the .NET Framework 4.  
    ///    A value of 0 for dwMinimumRelease indicates a check for the .NET Framework 4 full  
    ///    Any other value indicates a check for a specific compatible release of the .NET Framework 4.  
    #define NETFX40_FULL_REVISION 0  
    // TODO: Replace with released revision number  
    #define NETFX45_RC_REVISION MAKELONG(50309, 5)   // .NET Framework 4.5   
    bool IsNetFx4Present(DWORD dwMinimumRelease)  
    {  
        DWORD dwError = ERROR_SUCCESS;  
        HKEY hKey = NULL;  
        DWORD dwData = 0;  
        DWORD dwType = 0;  
        DWORD dwSize = sizeof(dwData);  
  
        dwError = ::RegOpenKeyExW(HKEY_LOCAL_MACHINE, L"SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full", 0, KEY_READ, &hKey);  
        if (ERROR_SUCCESS == dwError)  
        {  
            dwError = ::RegQueryValueExW(hKey, L"Release", 0, &dwType, (LPBYTE)&dwData, &dwSize);  
  
            if ((ERROR_SUCCESS == dwError) && (REG_DWORD != dwType))  
            {  
                dwError = ERROR_INVALID_DATA;  
            }  
            else if (ERROR_FILE_NOT_FOUND == dwError)  
            {  
                // Release value was not found, let's check for 4.0.  
                dwError = ::RegQueryValueExW(hKey, L"Install", 0, &dwType, (LPBYTE)&dwData, &dwSize);  
  
                // Install = (REG_DWORD)1;  
                if ((ERROR_SUCCESS == dwError) && (REG_DWORD == dwType) && (dwData == 1))  
                {  
                    // treat 4.0 as Release = 0  
                    dwData = 0;  
                }  
                else  
                {  
                    dwError = ERROR_INVALID_DATA;  
                }  
            }  
        }  
  
        if (hKey != NULL)  
        {  
            ::RegCloseKey(hKey);  
        }  
  
        return ((ERROR_SUCCESS == dwError) && (dwData >= dwMinimumRelease));  
    }  
  
    ```  
  
-   Vous pouvez modifier le chemin d'accès du fichier exécutable \(Setup.exe dans l'exemple\) dans la méthode `Launch` pour indiquer son emplacement approprié, ou personnaliser le code pour déterminer l'emplacement.  La classe de base `MmioChainer` fournit une méthode de blocage `Run()` que la classe dérivée appelle.  
  
    ```cpp  
  
    bool Launch(const CString& args)  
    {  
    CString cmdline = L"dotNetFx45_Full_x86_x64.exe -pipe TheSectionName " + args; // Customize with name and location of setup .exe that you want to run  
    STARTUPINFO si = {0};  
    si.cb = sizeof(si);  
    PROCESS_INFORMATION pi = {0};  
  
    // Launch the Setup.exe that installs the .NET Framework 4.5  
    BOOL bLaunchedSetup = ::CreateProcess(NULL,   
     cmdline.GetBuffer(),  
     NULL, NULL, FALSE, 0, NULL, NULL,   
     &si,  
     &pi);  
  
    // If successful   
    if (bLaunchedSetup != 0)  
    {  
    IProgressObserver& observer = dynamic_cast<IProgressObserver&>(*this);  
    Run(pi.hProcess, observer);  
  
    ……………………..   
    return (bLaunchedSetup != 0);  
    }  
  
    ```  
  
-   La méthode `Send` intercepte et traite les messages.  Dans cette version de .NET Framework, le seul message pris en charge est le message fermeture de l'application.  
  
    ```cpp  
            // SendMessage  
            //  
            // Send a message and wait for the response.  
            // dwMessage: Message to send  
            // pData: The buffer to copy the data to  
            // dwDataLength: Initially a pointer to the size of pBuffer.  Upon successful call, the number of bytes copied to pBuffer.  
            //--------------------------------------------------------------  
        virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength)  
        {  
            DWORD dwResult = 0;  
            printf("recieved message: %d\n", dwMessage);  
            // Handle message  
            switch (dwMessage)  
            {  
            case MMIO_CLOSE_APPS:  
                {  
                    printf("    applications are holding files in use:\n");  
                    IronMan::MmioCloseApplications* applications = reinterpret_cast<IronMan::MmioCloseApplications*>(pData);  
                    for(DWORD i = 0; i < applications->m_dwApplicationsSize; i++)  
                    {  
                        printf("      %ls (%d)\n", applications->m_applications[i].m_szName, applications->m_applications[i].m_dwPid);  
                    }  
  
                    printf("    should appliations be closed? (Y)es, (N)o, (R)efresh : ");  
                    while (dwResult == 0)  
                    {  
                        switch (toupper(getwchar()))  
                        {  
                        case 'Y':  
                            dwResult = IDYES;  // Close apps  
                            break;  
                        case 'N':  
                            dwResult = IDNO;  
                            break;  
                        case 'R':  
                            dwResult = IDRETRY;  
                            break;  
                        }  
                    }  
                    printf("\n");  
                    break;  
                }  
            default:  
                break;  
            }  
            printf("  response: %d\n  ", dwResult);  
            return dwResult;  
        }  
    };  
  
    ```  
  
-   Les données de progression sont un `char` non signé compris entre 0 \(0%\) et 255 \(100%\).  
  
    ```cpp  
    private: // IProgressObserver  
        virtual void OnProgress(unsigned char ubProgressSoFar)  
        {…………  
       }  
  
    ```  
  
-   Le HRESULT est passé à la méthode `Finished`.  
  
    ```cpp  
    virtual void Finished(HRESULT hr)  
    {  
    // This HRESULT is communicated over MMIO and may be different than process  
    // Exit code of the Chainee Setup.exe itself  
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);  
    }  
  
    ```  
  
    > [!IMPORTANT]
    >  Le redistribuable [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] écrit généralement de nombreux messages de progression et un message unique qui indique l'achèvement \(sur le côté programme de chaînage\).  Il lit également de façon asynchrone, en recherchant des enregistrements `Abort`.  S'il reçoit un enregistrement `Abort`, il annule l'installation, puis écrit un enregistrement terminé avec E\_ABORT comme contenu une fois que l'installation a été interrompue et que les opérations d'installation ont été annulées.  
  
 Un serveur typique crée un nom de fichier MMIO aléatoire, crée le fichier \(comme indiqué dans l'exemple de code précédent, dans `Server::CreateSection`\), et lance le redistribuable en utilisant la méthode `CreateProcess` ainsi qu'en passant le nom de canal avec l'option `-pipe someFileSectionName`.  Le serveur doit implémenter les méthodes `OnProgress`, `Send`, et `Finished` avec le code de l'application spécifique à l'interface utilisateur.  
  
## Voir aussi  
 [Guide de déploiement pour les développeurs](../../../docs/framework/deployment/deployment-guide-for-developers.md)   
 [déploiement](../../../docs/framework/deployment/net-framework-and-applications.md)