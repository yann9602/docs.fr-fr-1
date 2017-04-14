---
title: "Cr&#233;ation d&#39;assemblys satellites pour les applications bureautiques | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "déploiement d’applications (.NET Framework), ressources"
  - "fichiers de ressources, déploiement"
  - "hub and spoke (modèle de déploiement de ressources)"
  - "fichiers de ressources, création de packages"
  - "ressources d’application, création de packages"
  - "clés publiques, obtention"
  - "assemblys satellites"
  - "assemblys (.NET Framework), signature"
  - "ressources d’application, déploiement"
  - "Al.exe"
  - "Global Assembly Cache (GAC), assemblys satellites"
  - "Assembly Linker"
  - "emplacement du répertoire pour les assemblys satellites"
  - "Global Assembly Cache, assemblys satellites"
  - "empaqueter des ressources d'application"
  - "compiler des assemblys satellites"
  - "signer à nouveau des assemblys"
ms.assetid: 8d5c6044-2919-41d2-8321-274706b295ac
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Cr&#233;ation d&#39;assemblys satellites pour les applications bureautiques
Les fichiers de ressources jouent un rôle centrales dans les applications hébergées.  Ils permettent à une application en chaînes d'affichage, aux images, ainsi que d'autres données de la langue et la culture de l'utilisateur, et fournir d'autres données si les ressources de langue ou de culture de l'utilisateur ne sont pas disponibles.  Le .NET Framework utilise un modèle « hub\-and\-spoke » pour localiser et récupérer ces ressources.  Le hub est l'assembly principal qui contient le code exécutable non localisé et les ressources pour une culture, qui est appelée la culture neutre ou par défaut.  La culture par défaut est la culture de secours de l'application ; elle est utilisée si aucune ressource localisée n'est disponible.  Vous utilisez l'attribut <xref:System.Resources.NeutralResourcesLanguageAttribute> pour indiquer la culture de la culture par défaut de l'application.  Chaque spoke se connecte à un assembly satellite qui contient les ressources pour une culture localisée, mais ne contient pas de code.  Dans la mesure où les assemblys satellites ne font pas partie de l'assembly principal, vous pouvez facilement remplacer ou mettre à jour les ressources correspondant à une culture spécifique sans remplacer l'assembly principal de l'application.  
  
> [!NOTE]
>  Les ressources de la culture par défaut d'une application peuvent aussi être stockées dans un assembly satellite.  Pour cela, vous affectez à l'attribut <xref:System.Resources.NeutralResourcesLanguageAttribute> la valeur de <xref:System.Resources.UltimateResourceFallbackLocation?displayProperty=fullName>.  
  
## Nom et emplacement de l'assembly satellite  
 Le modèle "hub\-and\-spoke" requiert que vous placiez les ressources dans des emplacements spécifiques, afin qu'elles soient facilement trouvées et utilisées.  Si vous ne compilez pas et ne nommez pas les ressources comme prévu ou si vous ne les placez pas aux endroits corrects, le Common Language Runtime ne sera pas en mesure de les trouver et utilisera les ressources de la culture par défaut à la place.  Le gestionnaire de ressources du .NET Framework, représenté par un objet <xref:System.Resources.ResourceManager>, est utilisé pour accéder automatiquement aux ressources localisé.  Le gestionnaire de ressources requiert des valeurs suivantes :  
  
-   Un seul assembly satellite doit inclure toutes les ressources de la culture particulière.  En d'autres termes, vous devez compiler plusieurs .txt ou les fichiers de .resx dans un seul fichier binaire .resources.  
  
-   Il doit y avoir un sous\-répertoire distinct dans le répertoire de l'application pour chaque culture localisée qui stocke les ressources de la culture.  Le nom du sous\-répertoire doit être identique au nom de culture.  Ou bien, vous pouvez stocker vos assemblys satellites dans le Global Assembly Cache.  Dans ce cas, le composant des informations de culture du nom fort de l'assembly doit indiquer sa culture. \(Consultez la section " [Installer des assemblys satellites dans le Global Assembly Cache](#SN) plus loin dans cette rubrique.\)  
  
    > [!NOTE]
    >  Si votre application comporte des ressources pour les cultures secondaires, placez chaque culture secondaire dans un sous\-répertoire distinct dans le répertoire de l'application.  Ne placez pas les sous\-cultures dans des sous\-répertoires du répertoire de la culture principale.  
  
-   L'assembly satellite doivent avoir le même nom que l'application, et doit utiliser l'extension de nom de fichier « .resources.dll ».  Par exemple, si une application est nommée Example.exe, le nom de chaque assembly satellite doivent être Example.resources.dll.  Notez que le nom de l'assembly satellite ne contient pas la culture de ses fichiers de ressources.  Toutefois, l'assembly satellite apparaît dans un répertoire qui spécifie la culture.  
  
-   Des informations sur la culture de l'assembly satellite doivent être incluses dans les métadonnées de l'assembly.  Pour enregistrer le nom de culture dans les métadonnées de l'assembly satellite, vous spécifiez l'option `/culture` lorsque vous utilisez [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md) pour inclure des ressources dans l'assembly satellite.  
  
 L'illustration suivante propose un exemple de structure de répertoires et de la configuration requise pour les emplacements des applications que vous n'installez pas dans le [Global Assembly Cache](../../../docs/framework/app-domains/gac.md).  Les éléments avec les extensions .txt et .resources ne seront pas fournis avec l'application finale.  Il s'agit des fichiers de ressources intermédiaires utilisés pour créer des assemblys de ressources satellites finaux.  Dans cet exemple, vous pouvez remplacer les fichiers .resx par des fichiers .txt.  Pour plus d'informations, consultez [Empaquetage et déploiement de ressources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).  
  
 ![Assemblys satellites](../../../docs/framework/resources/media/satelliteassemblydir.gif "satelliteassemblydir")  
Répertoire de l'assembly satellite  
  
## Compilation d'assemblys satellites  
 Vous utilisez [Resource File Generator\) \(Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) pour compiler les fichiers texte ou des fichiers XML \(.resx\) qui contiennent des ressources aux fichiers binaires de .resources.  Utilisez ensuite l'utilitaire [Assembly Linker \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md) pour compiler les fichiers .resources en assemblys satellites.  Al.exe crée un assembly à partir des fichiers .resources que vous spécifiez.  Les assemblys satellites peuvent contenir que des ressources ; ils ne peuvent contenir aucun code exécutable.  
  
 La commande suivante de Al.exe crée un assembly satellite pour l'application `Example` à partir du fichier de ressources Allemand strings.de.resources.  
  
```  
al /target:lib /embed:strings.de.resources /culture:de /out:Example.resources.dll  
```  
  
 La commande suivante de Al.exe crée également un assembly satellite pour l'application `Example` à partir du fichier strings.de.ressources.  L'option **\/template** fait hériter l'assembly satellite de toutes les métadonnées de l'assembly à l'exception des informations de culture de l'assembly parent \(Example.dll\).  
  
```  
al /target:lib /embed:strings.de.resources /culture:de /out:Example.resources.dll /template:Example.dll  
```  
  
 Le tableau suivant décrit en détail les options de Al.exe utilisées dans ces commandes avec plus de détails.  
  
|Option|Description|  
|------------|-----------------|  
|**\/target:**lib|Spécifie que votre assembly satellite est compilé dans un fichier de bibliothèque \(.dll\).  Étant donné qu'un assembly satellite ne contient pas de code exécutable et n'est pas l'assembly principal d'une application, vous devez enregistrer les assemblys satellites en tant que DLL.|  
|**\/embed:**strings.de.resources|Spécifie le nom du fichier ressource à inclure lorsque Al.exe compile l'assembly.  Vous pouvez inclure plusieurs fichiers de .resources dans un assembly satellite, mais si vous suivez le modèle de concentrateur\-et\- rai, vous devez compiler un assembly satellite pour chaque culture.  Cependant, vous pouvez créer des fichiers .resources séparés pour des chaînes et des objets.|  
|**\/culture:**de|Spécifie la culture de la ressource à compiler.  Le runtime language courant utilise ces informations lorsqu'il recherche les ressources pour une culture spécifique.  Si vous omettez cette option, Al.exe continuera de compiler quand même la ressource, mais le runtime n'est pas en mesure de la trouver lorsqu'un utilisateur la demande.|  
|**\/out:**Example.resources.dll|Spécifie le nom du fichier de sortie.  Ce nom doit suivre les conventions d'appellation standard *baseName*.resources.*extension*, où *baseName* est le nom de l'assembly principal, et *extension* est une extension valide \(telle que .dll\).  Notez que l'exécution ne peut pas déterminer la culture d'un assembly satellite selon son nom du fichier de sortie ; vous devez utiliser l'option de **\/culture** de la définir.|  
|**\/template:**Example.dll|Spécifie un assembly à partir duquel l'assembly satellite va hériter de toutes les métadonnées de l'assembly, à l'exception du champ culture.  Cette option affecte les assemblys satellites que si vous spécifiez un assembly qui a [nom fort](../../../docs/framework/app-domains/strong-named-assemblies.md).|  
  
 Pour obtenir une liste complète des options disponibles avec Al.exe, consultez [Assembly Linker \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
## Assemblys satellites : Un exemple  
 Voici « hello un exemple simple du monde » qui affiche un message qui contient une salutation localisée.  L'exemple contient des ressources pour les cultures anglais \(états\-unis\), de en français \(France\), et russes \(la Russie\), et sa culture de secours est l'anglais.  Pour créer cet exemple, procédez comme suit :  
  
1.  Créez un fichier de ressources nommé Greeting.resx ou Greeting.txt pour contenir des ressources de la culture par défaut.  Enregistrez une chaîne unique nommée `HelloString` dont la valeur est « hello world \! » dans ce fichier.  
  
2.  Pour indiquer que English \(en\) est la culture par défaut de l'application, vous devez également ajouter l'attribut <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> suivant au fichier AssemblyInfo de l'application ou à un des fichiers de code source principaux qui seront compilés dans l'assembly de principal de l'application.  
  
     [!code-csharp[Conceptual.Resources.Locating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
     [!code-vb[Conceptual.Resources.Locating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]  
  
3.  Prenez en charge des cultures supplémentaires \( en\-US », « fr\-FR », et « ru\-RU \) comme suit :  
  
    -   Pour prendre en charge la culture « en\-US » ou Anglais \(États\-Unis\), créez un fichier de ressources nommé Greeting.en\-US.txt et stockez\-le dans une chaîne unique nommée `HelloString` dont la valeur est « Hi world\! ».  
  
    -   Pour prendre en charge la culture « fr\-FR » ou Français \(France\), créez un fichier de ressources nommé Greeting.fr\-FR.txt et stockez\-le dans une chaîne unique nommée `HelloString` dont la valeur est «Salut tout le monde\! ».  
  
    -   Pour prendre en charge la culture « ru\-RU » ou Russe \(Russie\), créez un fichier de ressources nommé Greeting.ru\-RU.txt et stockez\-le dans une chaîne unique nommée `HelloString` dont la valeur est « Всем привет\! ».  
  
4.  Utilisez [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) pour compiler chaque texte ou un fichier de ressources XML dans un fichier binaire du .resources.  La sortie est un groupe de fichiers ayant le même nom de fichier racine que les fichiers de .resx ou .txt, mais d'une extension de .resources.  Si vous créez l'exemple dans Visual Studio, le processus de compilation est effectuée automatiquement.  Si vous n'utilisez pas Visual Studio, exécutez les commandes suivantes pour compiler les fichiers de .resx dans des fichiers de .resources :  
  
    ```  
  
    resgen Greeting.resx  
    resgen Greeting.en-us.resx  
    resgen Greeting.fr-FR.resx  
    resgen Greeting.ru-RU.resx  
  
    ```  
  
     Si les ressources sont des fichiers texte au lieu des fichiers XML, remplacez l'extension de .resx par .txt.  
  
5.  Compilez le code source suivant avec les ressources de la culture par défaut dans l'assembly principal de l'application :  
  
    > [!IMPORTANT]
    >  Si vous utilisez la ligne de commande au lieu de Visual Studio pour créer l'exemple, vous devez modifier l'appel au constructeur de la classe <xref:System.Resources.ResourceManager> comme suit : `ResourceManager rm = new ResourceManager("Greetings",``typeof(Example).Assembly);`  
  
     [!code-csharp[Conceptual.Resources.Locating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
     [!code-vb[Conceptual.Resources.Locating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]  
  
     Si l'application est nommée EXEMPLE et vous compilez de la ligne de commande, la commande du compilateur c est :  
  
    ```  
    csc Example.cs /res:Greeting.resources  
    ```  
  
     La commande correspondante du compilateur Visual Basic est :  
  
    ```  
    vbc Example.vb /res:Greeting.resources  
    ```  
  
6.  Créer un sous\-répertoire dans le répertoire de l'application principal pour chaque culture localisée prise en charge par l'application.  Vous devez créer des en\- états\-unis, un franc\- fr, et un sous\-répertoire RU\- RU.  Visual Studio crée les sous\-répertoires automatiquement dans le cadre du processus de compilation.  
  
7.  Incluez des fichiers spécifiques à la culture de .resources dans des assemblys satellites et enregistrez\-les dans le répertoire approprié.  La commande d'effectuer cette opération pour chaque fichier de .resources est :  
  
    ```  
    al /target:lib /embed:Greeting.culture.resources /culture:culture /out:culture\Example.resources.dll  
    ```  
  
     où *culture* nom de la culture dont les ressources l'assembly satellite contient.  Visual Studio exécute ce processus automatiquement.  
  
 Vous pouvez ensuite exécuter l'exemple.  Il fera de l'une des cultures prend en charge la culture actuelle et affiche une salutation localisée.  
  
<a name="SN"></a>   
## Installation d'un assembly satellite dans le Global Assembly Cache  
 Au lieu d'installer des assemblys dans un sous\-répertoire local d'application, vous pouvez les configurer dans le Global Assembly Cache.  Cela est particulièrement utile si vous avez des bibliothèques de classes et les assemblys de ressource bibliothèque de classes utilisées par plusieurs applications.  
  
 Configuration des assemblys dans le Global Assembly Cache requiert qu'ils aient des noms forts.  Les assemblys avec nom fort sont signés avec une paire de clés publique\/privée valide.  Ils contiennent des informations de version que le runtime utilise pour déterminer l'assembly à utiliser afin de répondre à la demande de liaison.  Pour plus d'informations sur les noms forts et le versioning, consultez [Versioning des assemblys](../../../docs/framework/app-domains/assembly-versioning.md).  Pour plus d'informations sur les noms forts, consultez [Assemblys avec nom fort](../../../docs/framework/app-domains/strong-named-assemblies.md).  
  
 Lorsque vous développez une application, il est peu probable que vous puissiez accéder à la paire de clés publique\/privée finale.  Afin d'installer un assembly satellite dans le Global Assembly Cache et de vous assurer qu'il fonctionne comme prévu, vous pouvez utiliser une technique appelée signature différée.  Lorsque vous différez la signature d'un assembly, au moment de la construction vous réservez un espace dans le fichier pour la signature de nom fort au moment de la compilation.  La signature réelle est différée jusqu'à une date ultérieure, lorsque la paire de clés publique\/privée finale est disponible.  Pour plus d'informations sur la signature différée, consultez [Signature différée d'un assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
### Obtention de la clé publique  
 Pour différer la signature d'un assembly, vous devez avoir accès à la clé publique.  Vous pouvez soit obtenir la clé publique réelle à partir de l'organisation dans votre société qui effectuera la signature, soit créer une clé publique en utilisant l'outil [Strong Name Tool \(Sn.exe\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).  
  
 La commande suivante pour Sn.exe crée une paire de clés publique\/privée de test.  L'option de **–k** spécifie que Sn.exe doit créer une nouvelle paire de clés et l'enregistrer dans un fichier nommé TestKeyPair.snk.  
  
```  
sn –k TestKeyPair.snk   
```  
  
 Vous pouvez extraire la clé publique du fichier contenant la paire de clés de test.  La commande suivante extrait la clé publique de TestKeyPair.snk et les stocke dans PublicKey.snk :  
  
```  
sn –p TestKeyPair.snk PublicKey.snk  
```  
  
### Signature différée d'un assembly  
 Une fois que vous avez obtenu ou créé la clé publique, servez\-vous de l'utilitaire [Assembly Linker \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md) pour compiler l'assembly et spécifier la signature différée.  
  
 La commande suivante de Al.exe crée un assembly satellite avec nom fort pour l'application Librairie de Chaîne à partir du fichier strings.ja.resources:  
  
```  
al /target:lib /embed:strings.ja.resources /culture:ja /out:StringLibrary.resources.dll /delay+ /keyfile:PublicKey.snk  
```  
  
 L'option de **\/delay\+** spécifie que l'Assembly Linker doit retarder le signe l'assembly.  L'option **\/keyfile** spécifie le nom du fichier de clé contenant la clé publique à utiliser pour différer la signature de l'assembly.  
  
### Nouvelle signature d'un assembly  
 Avant de déployer votre application, vous devez à nouveau signer l'assembly satellite signé avec la vraie valeur de paire de clés.  Vous pouvez effectuer cette action en utilisant Sn.exe.  
  
 La commande Sn.exe suivante signe StringLibrary.resources.dll avec la vraie paire de clés stockée dans le fichier RealKeyPair.snk.  L'option **–R** spécifie qu'une assembly déjà signé ou dont la signature a été différée doit être signé à nouveau.  
  
```  
sn –R StringLibrary.resources.dll RealKeyPair.snk   
```  
  
### Installation d'un assembly satellite dans le Global Assembly Cache  
 Lorsque le runtime recherche les ressources dans le processus de secours, il cherche d'abord dans le [global assembly cache](../../../docs/framework/app-domains/gac.md). \-Pour plus d'informations, consultez la section « Processus de secours pour les ressources » de la rubrique [Empaquetage et déploiement de ressources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) \). Dès qu'un assembly satellite est signé avec un nom fort, il peut être installé dans le Global Assembly Cache à l'aide de [Outil Global Assembly Cache \(Gacutil.exe\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
 La commande suivante de Gacutil.exe installe StringLibrary.resources.dll dans le Global Assembly Cache :  
  
```  
gacutil /i:StringLibrary.resources.dll  
```  
  
 L'option **\/i** spécifie que Gacutil.exe devrait installer l'assembly spécifié dans le Global Assembly Cache.  Une fois l'assembly satellite installé dans le cache, les ressources qu'il contient deviennent disponible pour toutes les applications conçues pour utiliser l'assembly satellite.  
  
### Ressources dans le Global Assembly Cache : Un exemple  
 L'exemple suivant utilise une méthode dans une bibliothèque de classes. NET Framework pour extraire et retourner une salutation localisée dans un fichier de ressources.  La bibliothèque et ses ressources sont stockées dans le Global Assembly Cache.  L'exemple contient des ressources pour l'anglais \(états\-unis\), le Français \(France\), le Russe \(Russie\), et les cultures en anglais.  L'anglais est la culture par défaut ; ses ressources sont stockées dans l'assembly principal.  L'exemple retardent initialement les signes la bibliothèque et ses assemblys satellites avec une clé publique, puis nouveau signe ils avec une paire de clés publique\/privée.  Pour créer cet exemple, procédez comme suit :  
  
1.  Si vous n'utilisez pas Visual Studio, utilisez la commande suivante pour [Outil Strong NAME Tool \(Sn.exe\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) pour créer une paire de clés publique\/privée nommée ResKey.snk :  
  
    ```  
    sn –k ResKey.snk  
    ```  
  
     Si vous utilisez Visual Studio, utilisez l'onglet **Signature** de la boîte de dialogue **Propriétés** de projet pour générer le fichier de clé.  
  
2.  Utilisez la commande suivante pour [Outil Strong NAME Tool \(Sn.exe\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) pour créer un fichier de clé publique nommée PublicKey.snk :  
  
    ```  
    sn –p ResKey.snk PublicKey.snk  
    ```  
  
3.  Créez un fichier de ressources nommé Strings.resx pour contenir des ressources de la culture par défaut.  Enregistrez une chaîne unique nommée `Greeting` dont la valeur est « comment allez\-vous ? » dans ce fichier.  
  
4.  Pour indiquer que « en » est la culture par défaut de l'application, vous devez également ajouter l'attribut <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> suivant au fichier AssemblyInfo de l'application ou à un des fichiers de code source principaux qui seront compilés dans l'assembly de principal de l'application.  
  
     [!code-csharp[Conceptual.Resources.Satellites#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
     [!code-vb[Conceptual.Resources.Satellites#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]  
  
5.  Prenez en charge des cultures supplémentaires \( en\-US », « fr\-FR », et « ru\-RU \) comme suit :  
  
    -   Pour prendre en charge la culture « en\-US » ou Anglais \(États\-Unis\), créez un fichier de ressources nommé Strings.en\-US.resx or Strings.en\-US.txt et stockez\-le dans une chaîne unique nommée `Greeting` dont la valeur est «Hello\!».  
  
    -   Pour prendre en charge la culture « fr\-FR » ou Français \(France\), créez un fichier de ressources nommé Strings.fr\-FR.resx or Strings.fr\-FR.txt et stockez\-le dans une chaîne unique nommée `Greeting` dont la valeur est «Bonjour\!».  
  
    -   Pour prendre en charge la culture « ru\-RU » ou Russe \(Russie\), créez un fichier de ressources nommé Strings.ru\-RU.resx or Strings.ru\-RU.txt et stockez\-le dans une chaîne unique nommée `Greeting` dont la valeur est "Привет\!".  
  
6.  Utilisez [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) pour compiler chaque texte ou un fichier de ressources XML dans un fichier binaire du .resources.  La sortie est un groupe de fichiers ayant le même nom de fichier racine que les fichiers de .resx ou .txt, mais d'une extension de .resources.  Si vous créez l'exemple dans Visual Studio, le processus de compilation est effectuée automatiquement.  Si vous n'utilisez pas Visual Studio, exécutez les commandes suivantes pour compiler les fichiers de .resx dans des fichiers de .resources :  
  
    ```  
    resgen filename  
    ```  
  
     où *filename* est le chemin d'accès, le nom de fichier, l'extension facultatifs de .resx ou du fichier texte.  
  
7.  Compilez le code source suivant pour StringLibrary.vb ou StringLibrary.cs avec les ressources de la culture par défaut dans une bibliothèque signée par délai StringLibrary.dll intitulé assembly :  
  
    > [!IMPORTANT]
    >  Si vous utilisez la ligne de commande au lieu de Visual Studio pour créer l'exemple, vous devez modifier l'appel au constructeur de la classe <xref:System.Resources.ResourceManager> comme suit         `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`.  
  
     [!code-csharp[Conceptual.Resources.Satellites#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
     [!code-vb[Conceptual.Resources.Satellites#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]  
  
     La commande pour le compilateur C\# est:  
  
    ```  
    csc /t:library /resource:Strings.resources /delaysign+ /keyfile:publickey.snk StringLibrary.cs  
    ```  
  
     La commande correspondante du compilateur Visual Basic est :  
  
    ```  
    vbc /t:library /resource:Strings.resources /delaysign+ /keyfile:publickey.snk StringLibrary.vb  
    ```  
  
8.  Créer un sous\-répertoire dans le répertoire de l'application principal pour chaque culture localisée prise en charge par l'application.  Vous devez créer des en\- états\-unis, un franc\- fr, et un sous\-répertoire RU\- RU.  Visual Studio crée les sous\-répertoires automatiquement dans le cadre du processus de compilation.  Tous les assemblys satellites ont le même nom de fichier, les sous\-répertoires permettent de stocker des assemblys satellites spécifiques à la culture jusqu'à ce qu'ils soient signés avec une paire de clés publique\/privée.  
  
9. Incluez des fichiers spécifiques à la culture de .resources dans des assemblys satellites à signature différés et enregistrez\-les dans le répertoire approprié.  La commande d'effectuer cette opération pour chaque fichier de .resources est :  
  
    ```  
    al /target:lib /embed:Strings.culture.resources /culture:culture /out:culture\StringLibrary.resources.dll /delay+ /keyfile:publickey.snk  
    ```  
  
     où *culture* nom de la culture.  Dans cet exemple, les noms de culture sont les en\- états\-unis, les franc\- francs, et RU\- RU.  
  
10. Nouveau signe StringLibrary.dll à l'aide de [Outil Strong NAME Tool \(Sn.exe\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) comme suit :  
  
    ```  
    sn –R StringLibrary.dll RealKeyPair.snk  
    ```  
  
11. Signez de nouveau les assemblys satellites.  Pour cela, utilisez [Outil Strong NAME Tool \(Sn.exe\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) comme suit pour chaque assembly satellite :  
  
    ```  
    sn –R StringLibrary.resources.dll RealKeyPair.snk  
    ```  
  
12. Enregistrez StringLibrary.dll et de ses assemblys satellites dans le Global Assembly Cache à l'aide de la commande suivante :  
  
    ```  
    gacutil /i filename  
    ```  
  
     où *filename* représente le nom du fichier à enregistrer.  
  
13. Si vous utilisez Visual Studio, créez un projet de **Application console** nommé `Example`, ajoutez une référence à StringLibrary.dll et le code source suivant à lui, et les compilez.  
  
     [!code-csharp[Conceptual.Resources.Satellites#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
     [!code-vb[Conceptual.Resources.Satellites#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]  
  
     Pour compiler depuis la ligne de commande, utilisez la commande suivante pour le compilateur C\# :  
  
    ```  
    csc Example.cs /r:StringLibrary.dll   
    ```  
  
     La ligne de commande pour le compilateur de Visual Basic est:  
  
    ```  
    vbc Example.vb /r:StringLibrary.dll   
    ```  
  
14. Exécutez Exemple.exe  
  
## Voir aussi  
 [Empaquetage et déploiement de ressources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)   
 [Temporisation de signature d'un assembly](../../../docs/framework/app-domains/delay-sign-assembly.md)   
 [Al.exe \(Assembly Linker\)](../../../docs/framework/tools/al-exe-assembly-linker.md)   
 [Sn.exe \(Strong Name Tool\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)   
 [Gacutil.exe \(Global Assembly Cache Tool\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)   
 [Ressources dans des applications de bureau](../../../docs/framework/resources/index.md)