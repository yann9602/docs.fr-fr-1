---
title: Les profileurs CLR et les applications du Windows Store
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: csharp
applies_to:
- Windows 10
- Windows 8
helpviewer_keywords:
- profiling API
- profiling API [.NET Framework]
- profiling managed code
- profiling managed code [Windows Store Apps]
ms.assetid: 1c8eb2e7-f20a-42f9-a795-71503486a0f5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db1152e82edde34dc8dbaba09f20b9f769dffbca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="clr-profilers-and-windows-store-apps"></a>Les profileurs CLR et les applications du Windows Store
Cette rubrique explique ce que vous devez tenir compte lorsque les outils de diagnostic de l’écriture qui analysent géré du code exécuté dans une application Windows Store.  Il fournit également des instructions pour modifier vos outils de développement existants afin qu’ils continuer de fonctionner lorsque vous les exécutiez sur les applications du Windows Store.  Pour comprendre ces informations, il est préférable de que si vous êtes familiarisé avec l’API de profilage de Common Language Runtime, vous avez déjà utilisé cette API dans un outil de diagnostic que s’exécute correctement sur les applications de bureau Windows et que vous êtes maintenant intéressé par la modification de l’outil Pour exécuter correctement sur les applications du Windows Store.  
  
 Cette rubrique contient les sections suivantes :  
  
 [Introduction](#Intro)  
 [Architecture et la terminologie](#Arch)  
 [Périphériques Windows RT](#RT)  
[Utilisation des API Windows Runtime](#Consuming)  
[Le chargement de la DLL du profileur](#Loading)  
 [Considérations courantes de démarrage et d’attachement charges](#Common)  
 [Chargement au démarrage](#Startup)  
 [Attachement de charge](#Attach)  
[En cours d’exécution à l’intérieur de l’application du Windows Store](#Running)  
 [Respectez les API d’application du Windows Store](#APIs)  
 [Autorisations réduites](#Permissions)  
 [Communication entre processus](#Interprocess)  
 [Aucune notification d’arrêt](#Shutdown)  
[Fichiers de métadonnées Windows Runtime](#Metadata)  
 [WinMDs managé et non managé](#WMDs)  
 [Fichiers WinMD ressembler à des modules CLR](#CLRModules)  
 [La lecture des métadonnées à partir des fichiers Winmd](#Reading)  
 [Modification des métadonnées à partir des fichiers Winmd](#Modifying)  
 [Résolution des références d’assembly avec WinMDs](#Resolving)  
[Profileurs de mémoire](#Profilers)  
 [ForceGC crée un thread managé](#ForceGC)  
 [ConditionalWeakTableReferences](#WeakTable)  
[Conclusion](#Conclusion)  
[Ressources](#Resources)  
  
<a name="Intro"></a>   
## <a name="introduction"></a>Introduction  
 Si vous l’avez fait après le paragraphe d’introduction, vous êtes familiarisé avec l’API de profilage CLR.  Vous avez déjà écrit un outil de diagnostic qui fonctionne correctement sur les applications de bureau managées.  Vous pouvez désormais obtenir des informations que faire pour que votre outil fonctionne avec une application gérée par Windows Store.  Vous avez peut-être déjà essayé résoudre ce problème et a découvert qu’il n’est pas une tâche simple.  En effet, il existe des considérations qui ne soit pas évident pour tous les développeurs d’outils.  Exemple :  
  
-   Applications du Windows Store s’exécutent dans un contexte avec autorisations réduites gravement.  
  
-   Fichiers de métadonnées Windows ont des caractéristiques uniques par rapport à des modules managés traditionnels.  
  
-   Applications du Windows Store ont l’habitude d’interruption eux-mêmes lors de l’interactivité tombe en panne.  
  
-   Vos mécanismes de communication inter-processus ne fonctionnent plus pour diverses raisons.  
  
 Cette rubrique répertorie les éléments que vous devez être conscient des et comment traiter correctement.  
  
 Si vous utilisez l’API de profilage CLR, passez à des ressources à la fin de cette rubrique pour trouver des informations de mieux.  
  
 En fournissant des détails sur les API Windows spécifiques et comment ils doivent être utilisées est également à l’extérieur de la portée de cette rubrique.  Envisagez de cette rubrique, un point de départ et reportez-vous à MSDN pour en savoir plus sur les API Windows référencée ici.  
  
<a name="Arch"></a>   
## <a name="architecture-and-terminology"></a>Architecture et la terminologie  
 En règle générale, un outil de diagnostic possède une architecture semblable à celui indiqué dans l’illustration suivante. Il utilise le terme « profileur », mais beaucoup de ces outils aller au-delà de performances standard ou de profilage de mémoire dans des zones telles que la couverture du code, simuler les infrastructures d’objets, débogage, l’application de surveillance et ainsi de suite-voyage.  Par souci de simplicité, cette rubrique continue faire référence à tous ces outils comme les profileurs.  
  
 La terminologie suivante est utilisée tout au long de cette rubrique :  
  
 Application  
 Il s’agit de l’application qui analyse le profileur.  En règle générale, le développeur de cette application est maintenant en utilisant le Générateur de profils pour aider à diagnostiquer les problèmes liés à l’application.  En règle générale, cette application est une application de bureau Windows, mais dans cette rubrique, nous nous intéressons à des applications du Windows Store.  
  
 DLL du profileur  
 Il s’agit de composant qui charge dans l’espace de processus de l’application en cours d’analyse.  Ce composant, également connu sous le profileur « agent », implémente la [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)[ICorProfilerCallback Interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)(2, 3, etc.) des interfaces et consomme le [ ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)(2, 3, etc.) interfaces pour collecter des données relatives à l’application analysée et potentiellement modifier des aspects du comportement de l’application.  
  
 Interface utilisateur du profileur  
 Il s’agit de l’utilisateur de profileur interagit avec une application de bureau.  Il est responsable de l’affichage de l’état de l’application à l’utilisateur et de donner les moyens permettant de contrôler le comportement de l’application analysée à l’utilisateur.  Ce composant s’exécute toujours dans son propre espace de processus séparé à partir de l’espace de processus de l’application en cours de profilage.  L’interface utilisateur du Générateur de profils peuvent également fonctionner comme la « liaison » déclencheur, qui est le processus qui appelle la [ICLRProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) méthode, l’application analysée charger la DLL du profileur dans les cas où la DLL du profileur n’a pas charger au démarrage.  
  
> [!IMPORTANT]
>  Votre interface utilisateur du Générateur de profils doit rester une application de bureau Windows, même quand il est utilisé pour le contrôle et les rapports sur une application Windows Store.  Ne prévoyez pas l’être en mesure de package et de distribuer votre outil de diagnostic dans le Windows Store.  L’outil doit effectuer les opérations que les applications du Windows Store ne peuvent pas faire et que ces opérations se trouvent à l’intérieur de votre interface utilisateur du Générateur de profils.  
  
 Dans ce document, l’exemple de code suppose que :  
  
-   Votre DLL de profileur est écrit en C++, car il doit être une DLL native, conformément à la configuration requise de l’API de profilage CLR.  
  
-   Votre interface utilisateur du Générateur de profils est écrit en c#.  Cela n’est pas nécessaire, mais, car il n’existe aucune exigence de la langue pour les processus de l’interface utilisateur de votre profileur, pourquoi ne pas choisir une langue qui est simple et concise ?  
  
<a name="RT"></a>   
### <a name="windows-rt-devices"></a>Périphériques Windows RT  
 Périphériques Windows RT sont assez verrouillés.  Les profileurs de tiers ne peut pas être simplement chargés sur ces appareils.  Ce document se concentre sur les PC Windows 8.  
  
<a name="Consuming"></a>   
## <a name="consuming-windows-runtime-apis"></a>Utilisation des API Windows Runtime  
 Dans un nombre de scénarios présentés dans les sections suivantes, votre application de bureau de l’interface utilisateur du Générateur de profils doit consommer les nouvelles APIs Windows Runtime.  Que vous souhaitez consulter la documentation pour comprendre lesquelles API Windows Runtime peuvent être utilisées à partir d’applications de bureau, et si leur comportement différent quand appelé à partir du Windows Store et les applications de bureau applications.  
  
 Si votre interface utilisateur du Générateur de profils est écrit en code managé, il y a quelques étapes, que vous devez faire pour que la consommation de ces APIs Windows Runtime simple.  Consultez le [géré des applications de bureau et Windows Runtime](http://go.microsoft.com/fwlink/?LinkID=271858) article pour plus d’informations.  
  
<a name="Loading"></a>   
## <a name="loading-the-profiler-dll"></a>Le chargement de la DLL du profileur  
 Cette section décrit comment votre interface utilisateur du Générateur de profils entraîne l’application du Windows Store charger la DLL du profileur.  Le code présenté dans cette section appartienne dans votre application de bureau de l’interface utilisateur du Générateur de profils et par conséquent implique l’utilisation des API Windows qui sont sécurisés pour les applications de bureau, mais pas nécessairement sécurisés pour les applications du Windows Store.  
  
 Votre interface utilisateur du Générateur de profils peut entraîner la DLL de profileur doit être chargé dans l’espace de processus de l’application de deux manières :  
  
-   Au démarrage de l’application, car la contrôlée par les variables d’environnement.  
  
-   En attachant à l’application après le démarrage est terminée en appelant le [ICLRProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) (méthode).  
  
 Parmi votre première obstacles sera prise en charge de démarrage et de chargement par attachement de la DLL du profileur pour fonctionner correctement avec les applications du Windows Store.  Les deux formes de chargement ont en commun des considérations particulières pour commencer, intéressons-nous avec eux.  
  
<a name="Common"></a>   
### <a name="common-considerations-for-startup-and-attach-loads"></a>Considérations courantes de démarrage et d’attachement charges  
 **Signature de votre DLL de profileur**  
 Lorsque Windows tente de charger la DLL de profileur, il vérifie que votre DLL de profileur est correctement signé.  Si ce n’est pas le cas, le chargement échoue par défaut. Il existe deux façons d'effectuer cette opération :  
  
-   Assurez-vous que votre DLL de profileur est signé.  
  
-   Indiquez à votre utilisateur que vous devez installer une licence de développeur sur leur ordinateur Windows 8 avant d’utiliser votre outil.  Procéder automatiquement à partir de Visual Studio, ou manuellement à partir d’une invite de commandes.  Pour plus d’informations, consultez [obtenir une licence de développeur](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx).  
  
 **Autorisations de système de fichiers**  
 L’application du Windows Store doit avoir l’autorisation pour charger et exécuter votre DLL de profileur à partir de l’emplacement sur le système de fichiers dans lequel il réside.  Par défaut, l’application du Windows Store ne dispose pas cette autorisation sur la plupart des répertoires, et toute tentative de charger la DLL du profileur a échoué produira une entrée dans le journal des événements Application Windows qui ressemble à ceci :  
  
```Output  
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].  
```  
  
 En règle générale, les applications du Windows Store sont uniquement autorisées à accéder à un ensemble limité d’emplacements sur le disque.  Chaque application du Windows Store permettre accéder à ses propres dossiers de données d’application, ainsi que quelques autres zones du système de fichiers pour lequel toutes les applications du Windows Store sont autorisées à accéder.  Il est préférable d’installer votre DLL de profileur et ses dépendances quelque part sous Program Files ou Program Files (x86), étant donné que toutes les applications du Windows Store ont lu et il les autorisations d’exécution par défaut.  
  
<a name="Startup"></a>   
### <a name="startup-load"></a>Chargement au démarrage  
 En règle générale, dans une application de bureau, votre interface utilisateur du Générateur de profils vous invite à entrer une charge de démarrage de votre DLL de profileur en initialisant un bloc d’environnement qui contient les variables d’environnement API de profilage CLR requis (par exemple, `COR_PROFILER`, `COR_ENABLE_PROFILING`, et `COR_PROFILER_PATH`), et puis en créant un nouveau processus avec ce bloc d’environnement.  Va de même pour les applications du Windows Store, mais les mécanismes sont différentes.  
  
 **Ne pas exécuter avec élévation de privilèges**  
 Si le processus tente de lancer l’application du Windows Store B de processus, le processus A doit être exécuté avec une intégrité moyenne niveau, pas au niveau de haut niveau d’intégrité (c'est-à-dire, pas élevé).  Cela signifie que votre interface utilisateur du Générateur de profils doit être en cours d’exécution au niveau de l’intégrité des moyennes, ou il doit générer un autre processus au niveau de l’intégrité des moyennes pour prendre en charge du lancement de l’application du Windows Store.  
  
 **Choix d’une application du Windows Store au profil**  
 Tout d’abord, que vous souhaitez demander des applications du Windows Store pour lancer votre utilisateur du Générateur de profils.  Pour les applications de bureau, par exemple, vous affichez une boîte de dialogue Parcourir et l’utilisateur aurait rechercher et sélectionner un fichier .exe.  Mais les applications du Windows Store sont différents, et à l’aide d’une boîte de dialogue Parcourir n’a aucune signification.  Au lieu de cela, il est préférable d’afficher la liste des applications du Windows Store installée pour cet utilisateur à sélectionner à partir de l’utilisateur.  
  
 Vous pouvez utiliser la [PackageManager classe](https://msdn.microsoft.com/library/windows/apps/windows.management.deployment.packagemanager.aspx) pour générer cette liste.  `PackageManager`est une classe Windows Runtime qui est disponible pour les applications de bureau, et il est en fait *uniquement* disponibles pour les applications de bureau.  
  
 L’exemple suivant d’ode à partir d’une interface de profileur hypothétique écrite sous la forme d’une application de bureau dans c# yses le `PackageManager` pour générer une liste des applications Windows :  
  
```csharp  
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();  
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();  
PackageManager packageManager = new PackageManager();  
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);  
```  
  
 **En spécifiant le bloc d’environnement personnalisées**  
 Une nouvelle interface COM, [IPackageDebugSettings](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx), vous permet de personnaliser le comportement d’exécution d’une application du Windows Store pour simplifier certaines formes de diagnostics.  Une de ses méthodes, [EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=vs.85\).aspx), vous permet de passer un bloc d’environnement à l’application du Windows Store, lorsqu’elle est lancée, ainsi que d’autres effets utiles telles que la désactivation de suspension de processus automatique.  Le bloc d’environnement est important car il s’agit d’où vous devez spécifier les variables d’environnement (`COR_PROFILER`, `COR_ENABLE_PROFILING`, et `COR_PROFILER_PATH)`) utilisé par le CLR pour charger la DLL du profileur.  
  
 Considérez l’extrait de code suivant :  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, debuggerCommandLine,   
                                                                 (IntPtr)fixedEnvironmentPzz);  
```  
  
 Il existe deux éléments, que vous devez correctement :  
  
-   `packageFullName`peut être déterminée lors de l’itération sur les packages et en saisissant `package.Id.FullName`.  
  
-   `debuggerCommandLine`est un peu plus intéressante.  Pour transmettre le bloc environnement personnalisé à l’application du Windows Store, vous devez écrire votre propre, débogueur factice simpliste.  Génère de Windows l’application du Windows Store suspendu, puis l’attache le débogueur en lançant votre débogueur de ligne de commande, comme dans cet exemple :  
  
    ```Output  
    MyDummyDebugger.exe -p 1336 -tid 1424  
    ```  
  
     où `-p 1336` signifie que l’application du Windows Store a 1336 d’ID de processus, et `-tid 1424` signifie 1424 d’ID de Thread est le thread est suspendu.  Votre débogueur factice serait analyser l’ID de thread à partir de la ligne de commande, reprendre ce thread, puis quittez.  
  
     Voici quelques exemples de code C++ pour ce faire (veillez à ajouter à la vérification des erreurs !) :  
  
    ```cpp  
    int wmain(int argc, wchar_t* argv[])  
    {      
        // …  
        // Parse command line here  
        // …  
  
        HANDLE hThread = OpenThread(THREAD_SUSPEND_RESUME,   
                                                                  FALSE /* bInheritHandle */, nThreadID);  
        ResumeThread(hThread);  
        CloseHandle(hThread);  
        return 0;  
    }  
    ```  
  
     Vous devrez déployer ce débogueur factice dans le cadre de votre installation de l’outil de diagnostic, puis spécifiez le chemin d’accès à ce débogueur dans le `debuggerCommandLine` paramètre.  
  
 **Lancement de l’application du Windows Store**  
 Le moment pour lancer l’application du Windows Store est enfin arrivé. Si vous avez déjà déjà essayé de faire vous-même, vous avez peut-être remarqué que [CreateProcess](https://msdn.microsoft.com/library/windows/desktop/ms682425\(v=vs.85\).aspx) pas comment vous créer un processus d’application du Windows Store.  Au lieu de cela, vous devez utiliser le [IApplicationActivationManager::ActivateApplication](https://msdn.microsoft.com/library/windows/desktop/Hh706903\(v=vs.85\).aspx) (méthode).  Pour ce faire, vous devez obtenir l’ID de modèle d’application utilisateur de l’application du Windows Store que vous lancez.  Et cela signifie que vous devez effectuer quelques investigations permettent par le manifeste.  
  
 Lors de l’itération sur vos packages (consultez la section « Choix d’un Windows Store à profil d’application » dans le [chargement au démarrage](#Startup) section précédemment), que vous souhaitez récupérer l’ensemble des applications contenues dans le manifeste du package en cours :  
  
```csharp  
string manifestPath = package.InstalledLocation.Path + "\\AppxManifest.xml";  
  
AppxPackaging.IStream manifestStream;  
SHCreateStreamOnFileEx(  
                    manifestPath,  
                    0x00000040,     // STGM_READ | STGM_SHARE_DENY_NONE  
                    0,              // file creation attributes  
                    false,          // fCreate  
                    null,           // reserved  
                    out manifestStream);  
  
IAppxManifestReader manifestReader = appxFactory.CreateManifestReader(manifestStream);  
  
IAppxManifestApplicationsEnumerator appsEnum = manifestReader.GetApplications();  
```  
  
 Oui, un package peut avoir plusieurs applications, et chaque application possède son propre ID de modèle d’Application utilisateur.  Par conséquent, que vous souhaitez demander à votre utilisateur quelle application au profil et saisissez l’ID de modèle Application utilisateur à partir de cette application :  
  
```csharp  
while (appsEnum.GetHasCurrent() != 0)  
{  
    IAppxManifestApplication app = appsEnum.GetCurrent();  
    string appUserModelId = app.GetAppUserModelId();  
…  
```  
  
 Enfin, vous avez maintenant ce que vous devez lancer l’application du Windows Store :  
  
```csharp  
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();  
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);  
```  
  
 **N’oubliez pas d’appeler DisableDebugging**  
 Lorsque vous avez appelé [IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx), vous avez apportées à une promesse que vous devez nettoyer après vous-même en appelant le [IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx) (méthode), veillez à réaliser que lorsque la session de profilage terminée.  
  
<a name="Attach"></a>   
### <a name="attach-load"></a>Attachement de charge  
 Lorsque votre interface utilisateur du profileur souhaite attacher la DLL du profileur à une application qui a déjà démarré, il utilise [ICLRProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md).  Il en va de même avec les applications du Windows Store.  Mais en plus des considérations courantes répertoriées plus haut, assurez-vous que l’application du Windows Store cible n’est pas interrompue.  
  
 **EnableDebugging**  
 Comme avec la charge de démarrage, appelez le [IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx) (méthode).  Vous n’en avez besoin pour le passage d’un bloc d’environnement, mais vous devez une de ses autres fonctionnalités : la désactivation de suspension de processus automatique.  Sinon, lorsque votre interface utilisateur du Générateur de profils appelle [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md), l’application du Windows Store cible peut être interrompue.  En fait, il est probable si l’utilisateur est maintenant interagir avec votre interface utilisateur du Générateur de profils et de l’application du Windows Store n’est pas active sur un des écrans de l’utilisateur.  Et si le Windows Store de l’application est interrompue, elle ne sera pas en mesure de répondre à certaines indiquent que le CLR lui envoie pour attacher votre DLL de profileur.  
  
 Par conséquent, vous devrez procéder comme suit :  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, null /* debuggerCommandLine */,   
                                                                 IntPtr.Zero /* environment */);  
```  
  
 Il s’agit de la même appel que serait dans le cas de charge de démarrage, mais vous ne spécifiez pas une ligne de commande du débogueur ou un bloc d’environnement.  
  
 **DisableDebugging**  
 Comme toujours, n’oubliez pas d’appeler [IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx) lorsque votre session de profilage est terminée.  
  
<a name="Running"></a>   
## <a name="running-inside-the-windows-store-app"></a>En cours d’exécution à l’intérieur de l’application du Windows Store  
 Par conséquent, l’application du Windows Store a chargé enfin votre DLL de profileur.  À présent votre DLL de profileur doit être appris à lire par les différentes règles requis par les applications du Windows Store, y compris les API autorisées et comment exécuter avec des autorisations réduites.  
  
<a name="APIs"></a>   
### <a name="stick-to-the-windows-store-app-apis"></a>Respectez les API d’application du Windows Store  
 Lorsque vous parcourez l’API Windows, vous remarquerez que toutes les API est documenté comme étant applicables aux applications de bureau, les applications du Windows Store ou les deux.  Par exemple, le **exigences** section de la documentation pour le [InitializeCriticalSectionAndSpinCount](https://msdn.microsoft.com/library/windows/desktop/ms683476\(v=vs.85\).aspx) fonction indique que la fonction s’applique aux applications de bureau uniquement. En revanche, le [InitializeCriticalSectionEx](https://msdn.microsoft.com/library/windows/desktop/ms683477\(v=vs.85\).aspx) fonction est disponible pour les applications de bureau et les applications du Windows Store.  
  
 Lorsque vous développez votre DLL de profileur, traiter comme s’il s’agit d’une application du Windows Store et utilisent uniquement des API qui est décrits comme étant disponibles pour les applications du Windows Store.  Analyser vos dépendances (par exemple, vous pouvez exécuter `link /dump /imports` par rapport à votre DLL de profileur d’audit), puis recherchez la documentation pour voir quels vos dépendances sont OK et qui ne sont pas.  Dans la plupart des cas, votre violations peuvent être résolues simplement en les remplaçant par une forme plus récente de l’API est documenté en tant que safe (par exemple, en remplaçant [InitializeCriticalSectionAndSpinCount](https://msdn.microsoft.com/library/windows/desktop/ms683476\(v=vs.85\).aspx) avec [ InitializeCriticalSectionEx](https://msdn.microsoft.com/library/windows/desktop/ms683477\(v=vs.85\).aspx)).  
  
 Vous pouvez remarquer que votre DLL de profileur appelle des API qui s’appliquent aux applications de bureau uniquement, et encore ils semblent fonctionner même lorsque votre DLL de profileur est chargée à l’intérieur d’une application Windows Store.  Sachez qu’il est risqué d’utiliser les API non documenté pour une utilisation avec les applications du Windows Store dans votre DLL de profileur lors du chargement dans un processus d’application du Windows Store :  
  
-   Ces API n’est pas garanties pour fonctionner lorsqu’elle est appelée dans le contexte unique qui exécutent des applications du Windows Store dans.  
  
-   Ces API peut ne pas fonctionne de manière cohérente lorsqu’elle est appelée à partir de différents processus d’application du Windows Store.  
  
-   Ces API peut-être sembler fonctionner correctement à partir d’applications du Windows Store dans la version actuelle de Windows, mais peut interrompre ou désactivé dans les versions futures de Windows.  
  
 L’idéal consiste à résoudre toutes les violations de votre et éviter le risque.  
  
 Vous constaterez peut-être que vous ne pouvez pas faire sans une API particulière absolument et ne peut pas trouver un remplacement adapté aux applications du Windows Store.  Dans ce cas, au minimum :  
  
-   Test, tester, tester les daylights vivant en dehors de l’utilisation de cette API.  
  
-   Comprendre que l’API peut subitement break ou disparaître si elle est appelée à partir du Windows Store à l’intérieur d’applications dans les futures versions de Windows.  Cela ne soit considéré comme un problème de compatibilité par Microsoft, et l’utilisation de la prise en charge ne sera pas une priorité.  
  
<a name="Permissions"></a>   
### <a name="reduced-permissions"></a>Autorisations réduites  
 Il est en dehors de la portée de cette rubrique pour répertorier toutes les méthodes qui diffèrent des autorisations d’application du Windows Store à partir d’applications de bureau.  Mais certainement le comportement sera différent chaque fois que votre DLL de profileur (lorsqu’il est chargé dans une application Windows Store par rapport à une application de bureau) tente d’accéder aux ressources.  Le système de fichiers est l’exemple le plus courant.  Il existe, mais quelques place sur le disque une application du Windows Store donnée est autorisée à accéder (consultez [accès et les autorisations de fichiers (applications Windows Runtime](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)), et se trouvent sous les mêmes restrictions de votre DLL de profileur.  Testez votre code entièrement.  
  
<a name="Interprocess"></a>   
### <a name="inter-process-communication"></a>Communication entre processus  
 Comme indiqué dans le diagramme au début de cet article, votre DLL de profileur (chargés dans l’espace de processus d’application du Windows Store) aurez probablement besoin de communiquer avec votre profileur interface utilisateur (en cours d’exécution dans un espace de processus d’application de bureau distinct) via votre propre processus entre personnalisé canal de communication (IPC).  L’interface utilisateur du Générateur de profils envoie des signaux à la DLL du profileur pour modifier son comportement et la DLL de profileur envoie des données à partir de l’application du Windows Store analysée à l’interface utilisateur de générateur de profils de post-traitement et d’affichage à l’utilisateur du Générateur de profils.  
  
 La plupart des profileurs doivent fonctionner de cette façon, mais vos choix pour les mécanismes IPC est plus limitées lorsque votre DLL de profileur sont chargée dans une application Windows Store.  Par exemple, ce canaux nommés ne font pas partie de l’application du Windows Store SDK, vous ne pouvez pas les utiliser.  
  
 Mais bien évidemment, les fichiers sont toujours dans, et ce de façon plus limitée.  Les événements sont également disponibles.  
  
 **Communication via des fichiers**  
 La plupart de vos données est probablement passer entre la DLL de profileur et l’interface utilisateur du Générateur de profils via des fichiers.  La clé est de choisir un emplacement de fichier que votre DLL de profileur (dans le contexte d’une application du Windows Store) et l’interface utilisateur du Générateur de profils disposent de lecture et d’un accès en écriture à.  Par exemple, le chemin d’accès du dossier temporaire est un emplacement accessible par votre DLL de profileur et l’interface utilisateur du Générateur de profils, mais aucun autre package d’application du Windows Store ne permettre accéder (ce qui le protège les informations que vous vous connectez à partir d’autres packages d’application du Windows Store).  
  
 Votre interface utilisateur du Générateur de profils et les DLL de profileur peuvent déterminer ce chemin d’accès indépendamment.  Votre interface utilisateur du Générateur de profils, lorsqu’il itère tous les packages installés pour l’utilisateur actuel (voir l’exemple de code plus haut), obtient l’accès à la `PackageId` classe, à partir de laquelle le chemin d’accès du dossier temporaire peut être dérivée avec un code similaire à cet extrait de code.  (Comme toujours, la vérification des erreurs est omise par souci de concision.)  
  
```csharp  
// C# code for the Profiler UI.  
ApplicationData appData =  
    ApplicationDataManager.CreateForPackageFamily(  
        packageId.FamilyName);  
  
tempDir = appData.TemporaryFolder.Path;  
```  
  
 Pendant ce temps, votre DLL de profileur peut faire essentiellement la même chose, s’il le pouvait plus facilement accéder à la [ApplicationData](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.aspx) classe à l’aide de la [ApplicationData.Current](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.current.aspx) propriété.  
  
 **Communiquant via des événements**  
 Si vous souhaitez la sémantique de signalisation simple entre votre interface utilisateur du Générateur de profils et de la DLL de profileur, vous pouvez utiliser des événements dans les applications du Windows Store, ainsi que des applications de bureau.  
  
 À partir de votre DLL de profileur, vous pouvez simplement appeler le [CreateEventEx](https://msdn.microsoft.com/library/windows/desktop/ms682400\(v=vs.85\).aspx) fonction permettant de créer un événement nommé avec n’importe quel nom de votre choix.  Exemple :  
  
```cpp  
// Profiler DLL in Windows Store app (C++).  
CreateEventEx(   
    NULL,  // Not inherited  
    "MyNamedEvent"  
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */  
    EVENT_ALL_ACCESS);  
```  
  
 Votre interface utilisateur du Générateur de profils doit ensuite rechercher cet événement nommé sous l’espace de noms de l’application du Windows Store.  Par exemple, votre interface utilisateur du profileur peut appeler [CreateEventEx](https://msdn.microsoft.com/library/windows/desktop/ms682400\(v=vs.85\).aspx), en spécifiant le nom de l’événement en tant que  
  
 `AppContainerNamedObjects\<acSid>\MyNamedEvent`  
  
 `<acSid>`est AppContainer SID de l’application du Windows Store.  Une section précédente de cette rubrique vous a montré comment itérer sur les packages installés pour l’utilisateur actuel.  Dans cet exemple de code, vous pouvez obtenir l’ID de package.  Et à partir de l’ID de package, vous pouvez obtenir le `<acSid>` avec du code semblable au suivant :  
  
```csharp  
IntPtr acPSID;  
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);  
  
string acSid;  
ConvertSidToStringSid(acPSID, out acSid);  
  
string acDir;  
GetAppContainerFolderPath(acSid, out acDir);  
```  
  
<a name="Shutdown"></a>   
### <a name="no-shutdown-notifications"></a>Aucune notification d’arrêt  
 Lors de l’exécution à l’intérieur d’une application Windows Store, votre DLL de profileur ne doit pas dépendre soit [ICorProfilerCallback::Shutdown](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md) ou même [DllMain](https://msdn.microsoft.com/library/windows/desktop/ms682583\(v=vs.85\).aspx) (avec `DLL_PROCESS_DETACH`) qui est appelé pour avertir de votre DLL de profileur que l’application du Windows Store est en cours de fermeture.  En fait, vous devez prévoir qu’ils ne seront jamais appelés.  Historiquement, plusieurs DLL de profileur a utilisé ces notifications comme emplacement pratique vider les caches de disque, de fermer les fichiers, envoyer des notifications à l’interface utilisateur du Générateur de profils, etc.  Mais maintenant votre DLL de profileur doit être organisée en un peu différemment.  
  
 Votre DLL de profileur doivent être des informations de journalisation lorsqu’il passe.  Pour des raisons de performances, vous souhaiterez traiter par lot des informations en mémoire et sur le disque à mesure que le lot augmente la taille au-delà d’un seuil de vidage.  Mais supposons que toutes les informations ont pas encore été vidées sur le disque peuvent être perdues.  Cela signifie que vous souhaitez choisir votre seuil judicieusement, et que votre interface utilisateur du Générateur de profils doit être renforcé pour traiter des informations incomplètes écrites par la DLL du profileur.  
  
<a name="Metadata"></a>   
## <a name="windows-runtime-metadata-files"></a>Fichiers de métadonnées Windows Runtime  
 Il est en dehors de la portée de ce document à entrer dans les détails sur les métadonnées Windows Runtime (WinMD) sont des fichiers.    Cette section est limitée à la manière dont l’API de profilage CLR réagit lorsque des fichiers WinMD sont chargés par l’application du Windows Store de que l’analyse de votre DLL de profileur.  
  
<a name="WMDs"></a>   
### <a name="managed-and-non-managed-winmds"></a>WinMDs managé et non managé  
 Si un développeur utilise Visual Studio pour créer un nouveau projet de composant Windows Runtime, une build du projet génère un fichier WinMD qui décrit les métadonnées (les descriptions de type des classes, interfaces, etc.) créée par le développeur.  Si ce projet est un langage managé écrit en c# ou VB, ce même fichier WinMD contient également l’implémentation de ces types (ce qui signifie qu’il contient le langage intermédiaire compilé à partir du code source du développeur).  Ces fichiers sont appelés fichiers WinMD gérés.  Ils sont intéressants, ils contiennent les métadonnées Windows Runtime et l’implémentation sous-jacente.  
  
 En revanche, si un développeur crée un projet de composant Windows Runtime pour C++, une build du projet génère un fichier WinMD qui contient uniquement les métadonnées et l’implémentation est compilée dans une DLL native distincte.  De même, les fichiers WinMD qui sont fournis dans le Kit de développement logiciel Windows contiennent uniquement des métadonnées, avec l’implémentation compilée dans des DLL natives distincts qui font partie de Windows.  
  
 Les informations ci-dessous s’appliquent pour les deux fichiers Winmd managé, qui contiennent les métadonnées et l’implémentation, et Winmd non managé, qui contiennent uniquement des métadonnées.  
  
<a name="CLRModules"></a>   
### <a name="winmd-files-look-like-clr-modules"></a>Fichiers WinMD ressembler à des modules CLR  
 En ce qui concerne le CLR, tous les fichiers WinMD sont des modules.  Par conséquent, l’API de profilage CLR indique votre DLL de profileur lorsque vous chargent des fichiers WinMD et quelles est leurs ModuleID, de la même façon que pour d’autres modules managés.  
  
 Votre DLL de profileur peut distinguer des fichiers WinMD à partir d’autres modules en appelant le [ICorProfilerInfo3::GetModuleInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) (méthode) et en inspectant la `pdwModuleFlags` paramètre de sortie du [COR_PRF_MODULE_WINDOWS_ RUNTIME](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) indicateur.  (Il est défini si et seulement si le ModuleID représente un fichier WinMD).  
  
<a name="Reading"></a>   
### <a name="reading-metadata-from-winmds"></a>La lecture des métadonnées à partir des fichiers Winmd  
 Les fichiers WinMD, tels que des modules standards, contiennent des métadonnées qui peuvent être lues via le [Metadata APIs](../../../../docs/framework/unmanaged-api/metadata/index.md).  Toutefois, le CLR mappe les types Windows Runtime en types .NET Framework lorsqu’il lit que les fichiers WinMD afin que les développeurs de programme dans le code managé et de consomment le fichier WinMD peuvent avoir une expérience en programmation plus naturelle.  Pour obtenir des exemples de ces mappages, consultez [.NET Framework prise en charge pour les applications du Windows Store et Windows Runtime](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).  
  
 Par conséquent, mode dans lequel votre profileur obtiendrez lorsqu’il utilise les API de métadonnées : l’affichage brut de Windows Runtime, ou de la vue de .NET Framework mappée ?  La réponse : c’est à vous.  
  
 Lorsque vous appelez le [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) méthode sur un fichier WinMD pour obtenir une interface de métadonnées, telles que [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), vous pouvez choisir de définir [ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)dans le `dwOpenFlags` paramètre pour désactiver ce mappage.  Sinon, par défaut, le mappage est activé.  En règle générale, un profileur conservera le mappage activé, afin que les chaînes de la DLL de profileur obtient à partir des métadonnées WinMD (par exemple, les noms de types) recherche naturel pour l’utilisateur du Générateur de profils et familiers.  
  
<a name="Modifying"></a>   
### <a name="modifying-metadata-from-winmds"></a>Modification des métadonnées à partir des fichiers Winmd  
 Modification des métadonnées dans des fichiers Winmd n’est pas pris en charge.  Si vous appelez le [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) méthode pour un fichier WinMD fichier et spécifiez [ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) dans les `dwOpenFlags` paramètre ou demandez à une interface de métadonnées accessibles en écriture tels que [ IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md), [GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) échoue.  Cela est particulièrement importante pour les profileurs réécriture en langage intermédiaire, qui ont besoin de modifier les métadonnées pour prendre en charge leur instrumentation (par exemple, pour ajouter AssemblyRefs ou nouvelles méthodes).  Vérifiez donc pour [COR_PRF_MODULE_WINDOWS_RUNTIME](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) tout d’abord (comme indiqué dans la section précédente) et évitez de demander des interfaces de métadonnées accessibles en écriture sur ces modules.  
  
<a name="Resolving"></a>   
### <a name="resolving-assembly-references-with-winmds"></a>Résolution des références d’assembly avec WinMDs  
 Les profileurs de nombreux ont besoin de résoudre des références de métadonnées manuellement à l’aide avec instrumentation ou contrôle de type.  Les profileurs de ce type doivent être conscient de comment le CLR résout les références d’assembly qui pointent vers les fichiers Winmd, étant donné que ces références sont résolues dans une façon complètement différente de celle des références d’assembly standard.  
  
<a name="Profilers"></a>   
## <a name="memory-profilers"></a>Profileurs de mémoire  
 Le garbage collector et le tas managé ne sont pas fondamentalement différents dans une application Windows Store et une application de bureau.  Toutefois, il existe de légères différences qui les auteurs de profileur doivent connaître.  
  
<a name="ForceGC"></a>   
### <a name="forcegc-creates-a-managed-thread"></a>ForceGC crée un thread managé  
 Lorsque vous effectuez le profilage de mémoire, votre DLL de profileur crée généralement un thread séparé à partir de laquelle appeler le [ForceGC, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) méthode.  Cela n’est pas nouveau.  Mais ce qui peut être surprenant est que le fait d’effectuer un garbage collection à l’intérieur d’une application Windows Store peut-être transformer votre thread dans un thread managé (par exemple, un ID de thread API de profilage est créée pour ce thread).  
  
 Pour comprendre les conséquences de cela, il est important de comprendre les différences entre les appels synchrones et asynchrones, comme défini par l’API de profilage CLR. Notez que cela est très différente de la notion d’appels asynchrones dans les applications du Windows Store.  Consultez le blog [pourquoi nous devons CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/) pour plus d’informations.  
  
 Au point est que les appels effectués sur les threads créés par votre profileur sont toujours considérés comme synchrones, même si ces appels sont effectués à partir d’en dehors d’une implémentation de l’un de votre DLL de profileur [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) méthodes.  Au moins, qui permet le cas.  Maintenant que le CLR a activé les threads de votre profileur dans un thread managé en raison de l’appel de [ForceGC, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md), que le thread est considéré ne sont plus comme les threads de votre profileur.  Par conséquent, le CLR applique une définition plus stricte de quelles sont les conditions que synchrone pour ce thread, à savoir qui doit provenir d’un appel à l’intérieur d’un de votre DLL de profileur [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) méthodes pour qualifier comme synchrone.  
  
 Que cela signifie dans la pratique ?  La plupart des [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) méthodes peuvent uniquement être appelée de manière synchrone et immédiatement échoue dans le cas contraire.  Par conséquent, si votre DLL de profileur réutilise votre [ForceGC, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) thread pour d’autres appels généralement effectuées sur les threads de profileur créé (par exemple, pour [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md), [RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md), ou [RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)), vous allez rencontrer des difficultés pour.  Même une fonction asynchrone sécurisé comme [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) possède des règles spéciales lorsqu’elle est appelée à partir de threads managés. (Voir le blog [parcours de pile du profileur : notions de base et ultérieures](https://blogs.msdn.microsoft.com/davbr/2005/10/06/profiler-stack-walking-basics-and-beyond/) pour plus d’informations.)  
  
 Par conséquent, nous recommandons que n’importe quel thread de votre DLL de profileur crée pour appeler [ForceGC, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) doit être utilisé *uniquement* à des fins de déclenchement des catalogues globaux et en répondant aux rappels dans le catalogue global.  Il ne doit pas appeler l’API de profilage pour effectuer d’autres tâches telles que pile d’échantillonnage ou de détachement.  
  
<a name="WeakTable"></a>   
### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences  
 À compter de .NET Framework 4.5, il existe un nouveau rappel GC, [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md), afin d’obtenir le profileur informations plus complètes sur *handles dépendants*. Ces poignées ajouter efficacement une référence à partir d’un objet source à un objet cible à des fins de gestion de durée de vie de catalogue global.  Handles dépendants sont rien de nouveau, et les développeurs qui programment dans du code managé ont été en mesure de créer leurs propres handles dépendants à l’aide de la <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> classe avant même de Windows 8 et le .NET Framework 4.5.  
  
 Toutefois, les applications XAML Windows Store gérées maintenant utilisent beaucoup de handles dépendants.  En particulier, le CLR les utilise pour faciliter la gestion des cycles de référence entre les objets managés et les objets Windows Runtime non managés.  Cela signifie qu’il est désormais plus importe que jamais pour les profileurs de mémoire afin d’être informé ces handles dépendants afin qu’ils peuvent être visualisés avec le reste des bords dans le graphique de segment de mémoire.  Votre DLL de profileur doit utiliser [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md), [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), et [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) pour former une vue complète du graphique de segment de mémoire .  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Conclusion  
 Il est possible d’utiliser l’API de profilage CLR pour analyser le code managé en cours d’exécution à l’intérieur d’applications du Windows Store.  En fait, vous pouvez prendre un profileur existant que vous développez et apporter des modifications spécifiques afin qu’il peut cibler les applications du Windows Store.   Votre interface utilisateur du Générateur de profils doit utiliser les nouvelles API pour l’activation de l’application du Windows Store en mode débogage.  Assurez-vous que votre DLL de profileur consomme des seules API applicable pour les applications du Windows Store.  Le mécanisme de communication entre votre DLL de profileur et l’interface utilisateur du Générateur de profils doit être écrites avec les restrictions de API d’applications du Windows Store à l’esprit et avec la reconnaissance des autorisations restreintes en place pour les applications du Windows Store.  Votre DLL de profileur doit être informé de la façon dont le CLR le traite WinMDs, et comment le comportement du Garbage Collector est différent en ce qui concerne les threads managés.  
  
<a name="Resources"></a>   
## <a name="resources"></a>Ressources  
 **Le Common Language Runtime**  
 -   [Référence des API de profilage CLR](../../../../docs/framework/unmanaged-api/profiling/index.md)  
  
-   [Référence API de métadonnées CLR](../../../../docs/framework/unmanaged-api/metadata/index.md)  
  
 **Interaction du CLR avec le Windows Runtime**  
 [Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
  
 **Applications Windows Store**  
 -   [Accès aux fichiers et les autorisations (applications Windows Runtime](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)  
  
-   [Obtenir une licence de développeur](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx)  
  
-   [Interface de IPackageDebugSettings](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx)  
  
## <a name="see-also"></a>Voir aussi  
 [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)
