---
title: "Empaquetage et d&#233;ploiement de ressources dans des applications de bureau | Microsoft Docs"
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
  - "fichiers de ressources, empaquetage"
  - "ressources d’application, empaquetage"
  - "assembly de ressources unique"
  - "assemblys satellites"
  - "culture par défaut pour les applications"
  - "noms (.NET Framework), ressources"
  - "processus de secours pour les ressources"
  - "regrouper des cultures"
  - "ressources d’application, déploiement"
  - "ressources d’application, conventions d’affectation des noms"
  - "culture, empaquetage et déploiement de ressources"
  - "fichiers de ressources, conventions d’affectation des noms"
  - "empaqueter des ressources d'application"
  - "ressources d’application, processus de secours"
  - "fichiers de ressources, processus de secours"
  - "localiser des ressources"
  - "cultures neutres"
ms.assetid: b224d7c0-35f8-4e82-a705-dd76795e8d16
caps.latest.revision: 26
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 26
---
# Empaquetage et d&#233;ploiement de ressources dans des applications de bureau
Les applications s'appuient sur le gestionnaire de ressources du .NET Framework, représenté par la classe <xref:System.Resources.ResourceManager>, pour extraire les ressources localisé.  Le gestionnaire de ressources suppose qu'un modèle de concentrateur et de rai permet de package et déployer des ressources.  Le hub est l'assembly principal qui contient le code exécutable non localisé et les ressources pour une culture, appelée la culture neutre ou par défaut.  La culture par défaut est la culture de secours de l'application ; il s'agit de la culture dont les ressources sont utilisées si les ressources localisé ne peuvent pas être trouvées.  Chaque spoke se connecte à un assembly satellite qui contient les ressources pour une culture, mais ne contient pas de code.  
  
 Ce modèle comprend plusieurs avantages :  
  
-   Vous pouvez ajouter de façon incrémentielle des ressources pour de nouvelles cultures après avoir déployé une application.  Dans la mesure où le développement ultérieur de ressources spécifiques à une culture peut nécessiter du temps, cela vous permet de libérer d'abord votre application principale, puis de proposer des ressources spécifiques à une culture ultérieurement.  
  
-   Vous pouvez mettre à jour et changer les assemblys satellites d'une application sans recompiler l'application.  
  
-   Une application a besoin de charger uniquement les assemblys satellites qui contiennent les ressources nécessaires pour une culture spécifique.  Cela peut diminuer de manière importante l'utilisation des ressources système.  
  
 Cependant, ce modèle a également des inconvénients :  
  
-   Vous devez gérer plusieurs ensembles de ressources.  
  
-   Le coût initial du test d'une application augmente, car vous devez tester plusieurs configurations.  À longue échéance, il sera plus facile et moins coûteux de tester une application principale et plusieurs satellites, que de tester et de tenir à jour en parallèle plusieurs versions internationales.  
  
## Conventions d'affectation de noms pour les ressources  
 Lorsque vous empaquetez les ressources de votre application, vous devez les nommer en utilisant les conventions d'affectation de noms que le Common Language Runtime attend.  Le runtime identifie une ressource par son nom de culture.  Chaque culture a un nom unique, qui est en général une combinaison d'un nom de culture de deux lettres en minuscules associé à une langue, et si nécessaire, un nom de sous\-culture en majuscules à deux lettres associé à un pays ou une région.  Le nom de la sous\-culture suit le nom de la culture, séparé par un tiret \(\-\).  Les exemples incluent le ja\- JP du Japonais comme parlé au Japon, aux états\-unis en\- pour l'anglais comme parlé aux états\-unis, le de\-de pour l'Allemand comme parlé en Allemagne, ou le de\-at pour l'Allemand comme parlé en Autriche.  Consultez [Référence de l'API de \(NLS\) de prise en charge de la langue nationale](http://go.microsoft.com/fwlink/?LinkId=200048) au centre global d'accéder pour obtenir la liste complète des noms de culture.  
  
> [!NOTE]
>  Pour plus d'informations sur la création des fichiers de ressources, consultez [Création de fichiers de ressources](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md) et le [Création d'assemblys satellites](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md) dans MSDN Library.  
  
<a name="cpconpackagingdeployingresourcesanchor1"></a>   
## Processus de secours pour les ressources  
 Le modèle « hub and spoke » pour l'empaquetage et le déploiement des ressources utilise un processus de secours pour rechercher les ressources adéquates.  Si l'utilisateur d'une application demande une ressource localisée qui n'est pas disponible, le Common Language Runtime recherche dans la hiérarchie des cultures une ressource de secours appropriée, la plus proche de celle demandée par l'utilisateur, et déclenche une exception uniquement en dernier ressort.  À chaque niveau de la hiérarchie, si une ressource appropriée est trouvée, le runtime l'utilise.  Si la ressource n'est pas trouvée, la recherche se poursuit au niveau suivant.  
  
 Pour améliorer les performances de recherche, appliquez l'attribut <xref:System.Resources.NeutralResourcesLanguageAttribute> à votre assembly principal et passez\-lui le nom de la langue neutre qui sera utilisé avec votre assembly principal.  
  
> [!TIP]
>  Vous pourrez utiliser l'élément de configuration de [\<relativeBindForResources\>](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) pour optimiser le processus de secours de ressources et le processus selon lequel l'exécution de test pour les assemblys de ressource.  Pour plus d'informations, consultez la section [Optimisation du processus de secours pour les ressources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#Optimizing).  
  
 Le processus de secours comprend les étapes ci\-après :  
  
1.  Le runtime recherche tout d'abord un assembly qui correspond à la culture demandée dans le [Global Assembly Cache](../../../docs/framework/app-domains/gac.md) pour votre application.  
  
     Le Global Assembly Cache peut stocker des assemblys de ressources partagés par de nombreuses applications.  Cela vous permet de ne pas inclure des ensembles de ressources spécifiques dans la structure de répertoires de chaque application que vous créez.  Si le runtime trouve une référence à l'assembly, il recherche la ressource demandée dans cet assembly.  S'il trouve l'entrée dans l'assembly, il utilise la ressource demandée.  S'il ne trouve pas l'entrée, il continue la recherche.  
  
2.  Le runtime vérifie ensuite le répertoire de l'assembly en cours d'exécution à la recherche d'un répertoire qui correspond à la culture demandée.  S'il trouve le répertoire, il recherche dedans un assembly satellite valide pour la culture demandée.  Le runtime recherche ensuite dans l'assembly satellite la ressource demandée.  S'il trouve la ressource dans l'assembly, il l'utilise.  S'il ne trouve pas la ressource, il continue la recherche.  
  
3.  Les requêtes suivantes d'exécution Windows Installer pour déterminer si l'assembly satellite doivent être installés à la demande.  Dans ce cas, il gère l'installation, charge l'assembly, et il recherche la ressource demandée.  S'il trouve la ressource dans l'assembly, il l'utilise.  S'il ne trouve pas la ressource, il continue la recherche.  
  
4.  L'exécution a déclenché l'événement <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> pour indiquer qu'il ne peut pas trouver l'assembly satellite.  Si vous choisissez de gérer l'événement, le gestionnaire d'événements peut retourner une référence à l'assembly satellite dont les ressources seront utilisées pour la recherche.  Sinon, le gestionnaire d'événements renvoie `null` et la recherche continue.  
  
5.  Le runtime recherche ensuite de nouveau dans le Global Assembly Cache, cette fois l'assembly parent de la culture demandée.  Si l'assembly parent existe dans le Global Assembly Cache, le runtime recherche la ressource demandée dans cet assembly.  
  
     La culture parente est définie comme culture de secours appropriée.  Les parents sont les meilleurs candidats de secours; car n'importe quelle ressource est préférable à la levée d'une exception.  Ce processus vous permet de réutiliser les ressources.  Vous devriez inclure une ressource donnée au niveau parent uniquement si la culture enfant n'a pas besoin de localiser la ressource demandée.  Par exemple, si vous fournissez des assemblys satellites pour en \(anglais neutre\), en\-GB \(anglais parlé en Grande\-Bretagne\) et en\-US \(anglais parlé aux États\-Unis\), le satellite en contient la terminologie commune et les satellites en\-GB et en\-US fournissent les substitutions pour les termes qui changent.  
  
6.  Le runtime vérifie ensuite le répertoire de l'assembly en cours d'exécution pour voir s'il contient un répertoire parent.  Si un répertoire parent existe, le runtime recherche un assembly satellite valide pour la culture parente dans le répertoire.  S'il trouve l'assembly, le runtime recherche la ressource demandée dans cet assembly.  S'il trouve la ressource, il l'utilise.  S'il ne trouve pas la ressource, il continue la recherche.  
  
7.  Les requêtes suivantes d'exécution Windows Installer pour déterminer si l'assembly satellite doivent être installés à la demande.  Dans ce cas, il gère l'installation, charge l'assembly, et il recherche la ressource demandée.  S'il trouve la ressource dans l'assembly, il l'utilise.  S'il ne trouve pas la ressource, il continue la recherche.  
  
8.  L'exécution a déclenché l'événement <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> pour indiquer qu'il ne trouve pas une ressource appropriée de secours.  Si vous choisissez de gérer l'événement, le gestionnaire d'événements peut retourner une référence à l'assembly satellite dont les ressources seront utilisées pour la recherche.  Sinon, le gestionnaire d'événements renvoie `null` et la recherche continue.  
  
9. Le runtime recherche ensuite les assemblys parents, comme aux trois étapes précédentes, dans les différents niveaux.  Chaque culture a un parent, défini par la propriété <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=fullName>, mais un parent peut posséder son propre parent.  Rechercher des cultures parent s'arrête lorsque la propriété <xref:System.Globalization.CultureInfo.Parent%2A> d'une culture renvoie <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>; pour le secours des ressources, la culture indifférente n'est pas considérée comme une culture parent ou à une culture qui peuvent avoir des ressources.  
  
10. Si la culture spécifiée à l'origine et tous les parents ont fait l'objet de la recherche et que la ressource est toujours introuvable, la ressource pour la culture par défaut \(de secours\) est utilisée.  En général, les ressources de la culture par défaut sont incluses dans l'assembly d'application principale.  Toutefois, vous pouvez spécifier une valeur <xref:System.Resources.UltimateResourceFallbackLocation> pour la propriété <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> de l'attribut <xref:System.Resources.NeutralResourcesLanguageAttribute> pour indiquer que l'emplacement final de secours des ressources est un assembly satellite, plutôt que l'assembly principal.  
  
    > [!NOTE]
    >  La ressource par défaut est la seule ressource qui peut être compilée avec l'assembly principal.  À moins que vous ne spécifiiez un assembly satellite à l'aide de l'attribut <xref:System.Resources.NeutralResourcesLanguageAttribute>, c'est le secours ultime \(parent définitif\).  C'est pourquoi, il est fortement conseillé d'inclure un ensemble de ressources par défaut dans votre assembly principal.  Cela permet d'éviter aux exceptions d'être levé.  En incluant un fichier de ressources par défaut, vous fournissez une solution de secours pour toutes les ressources, et vous assurez qu'au moins une ressource est toujours présente pour l'utilisateur, même si elle n'est pas spécifique à une culture.  
  
11. Enfin, si le runtime ne trouve pas une ressource pour une culture \(de secours\) par défaut, une exception <xref:System.Resources.MissingManifestResourceException> <xref:System.Resources.MissingSatelliteAssemblyException> est levée indiquant que la ressource est introuvable.  
  
 Par exemple, supposez que les demandes d'applications d'une ressource a localisées pour l'Espagnol \(mexique\) \(la culture es\- MX\).  Le runtime recherche d'abord le Global Assembly Cache de l'assembly qui correspond à l'es\- MX, mais ne cherche pas.  Le runtime recherche alors dans le répertoire de l'assembly en cours d'exécution un répertoire « es\-MX ».  Une fois que cela échoue, le runtime recherche ensuite de nouveau dans le Global Assembly Cache un assembly parent reflètant la culture de secours appropriée, dans ce cas « es » \(Espagnol\).  Si l'assembly parent est introuvable, le runtime recherche dans tous les niveaux potentiels des assemblys parents la culture « es\-MX » jusqu'à ce qu'une ressource correspondante soit trouvée.  Si une ressource n'est pas trouvée, le runtime utilise la ressource de la culture par défaut.  
  
<a name="Optimizing"></a>   
### Optimisation du processus de secours pour les ressources  
 Dans les conditions suivantes, vous pouvez optimiser le processus selon lequel l'exécution trouve des ressources dans les assemblys satellites  
  
-   Les assemblys satellites sont déployés dans le même emplacement que l'assembly de code.  Si l'assembly de code est installé dans [Global Assembly Cache](../../../docs/framework/app-domains/gac.md), les assemblys satellites sont également installés dans le Global Assembly Cache.  Si l'assembly de code est installé dans un répertoire, les assemblys satellites sont installés dans les dossiers spécifiques à la culture de ce répertoire.  
  
-   Les assemblys satellites ne sont pas installés à la demande.  
  
-   Le code d'application ne gère pas l'événement <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName>.  
  
 Pour optimiser le test des assemblys satellites en incluant l'élément [\<relativeBindForResources\>](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) et définissez son attribut `enabled` à `true` dans le fichier de configuration de l'application, comme le montre l'exemple suivant.  
  
```  
  
<configuration>  
   <runtime>  
      <relativeBindForResources enabled="true" />  
   </runtime>  
</configuration>  
  
```  
  
 Le test optimisée pour les assemblys satellites est une fonctionnalité d'exécution.  Autrement dit, l'exécution suit les étapes documentées dans [Processus de secours pour les ressources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#cpconpackagingdeployingresourcesanchor1) sauf si l'élément [\<relativeBindForResources\>](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) est présent dans le fichier de configuration de l'application et son attribut `enabled` a la valeur `true`.  Dans ce cas, le processus de sondage d'un assembly satellite est modifié comme suit :  
  
-   Le Runtime utilise l'emplacement de l'assembly de code parent pour rechercher l'assembly satellite.  Si l'assembly est installé dans le Global Assembly Cache, l'exécution de test dans le cache mais pas dans le répertoire de l'application.  Si l'assembly est installé dans le répertoire d'une application, le Runtime sonde dans le repertoire de l'application mais pas dans le Global Assembly Cache.  
  
-   Le runtime n'interroge pas Windows Installer pour l'installation à la demande de les assemblys satellites.  
  
-   Si le test d'un assembly particulier de ressource échoue, le runtime ne déclenche pas d'événement <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName>.  
  
### Secours ultime à assembly satellite  
 Vous pouvez éventuellement supprimer des ressources de l'assembly principal et les spécifier que l'exécution doit charger les ressources CTP de secours d'un assembly satellite qui correspond à une culture spécifique.  Pour contrôler le processus de secours, vous utilisez le constructeur <xref:System.Resources.NeutralResourcesLanguageAttribute.%23ctor%28System.String%2CSystem.Resources.UltimateResourceFallbackLocation%29?displayProperty=fullName> et fournissez une valeur pour le paramètre <xref:System.Resources.UltimateResourceFallbackLocation> qui spécifie si le gestionnaire de ressources doit extraire les ressources de secours de l'assembly principal ou d'un assembly satellite.  
  
 L'exemple suivant utilise l'attribut <xref:System.Resources.NeutralResourcesLanguageAttribute> pour stocker les ressources de secours d'une application dans un assembly satellite pour la langue française de \(fr\).  L'exemple comporte deux fichiers de ressources textuels définissant une ressource chaîne unique nommée `Greeting`.  Le premier, resources.fr.txt, contient une ressource de langue française.  
  
```  
Greeting=Bon jour!  
```  
  
 Le second, des ressources, ru.txt, contient une ressource linguistique russe.  
  
```  
Greeting=Добрый день  
```  
  
 Ces deux fichiers sont compilés avec les fichiers de .resources en exécutant [générateur de fichier de ressources \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) de la ligne de commande.  Pour la ressource de langue française, la commande est la suivante :  
  
 **resgen.exe resources.fr.txt**  
  
 Pour la ressource de langue russe, la commande est la suivante :  
  
 **resgen.exe resources.ru.txt**  
  
 Les fichiers de .resources sont incorporés dans des bibliothèques de liens dynamiques en exécutant [éditeur de liens d'assembly \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md) de la ligne de commande pour la ressource de langue française comme suit :  
  
 **al \/t:lib \/embed:resources.fr.resources \/culture:fr \/out:fr\\Example1.resources.dll**  
  
 et pour la ressource linguistique russe comme suit :  
  
 **al \/t:lib \/embed:resources.ru.resources \/culture:ru \/out:ru\\Example1.resources.dll**  
  
 Code source d'application réside dans un fichier nommé Example1.cs ou Example1.vb.  Il inclut l'attribut <xref:System.Resources.NeutralResourcesLanguageAttribute> pour indiquer que la ressource par défaut d'application se trouve dans le sous\-répertoire de fr.  Il instancie le gestionnaire de ressources, extrait la valeur de la ressource `Greeting`, et l'affiche sur la console.  
  
 [!code-csharp[Conceptual.Resources.Packaging#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.packaging/cs/example1.cs#1)]
 [!code-vb[Conceptual.Resources.Packaging#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.packaging/vb/example1.vb#1)]  
  
 Vous pouvez compiler le code source C\# de la ligne de commande comme suit :  
  
 **csc Example1.cs**  
  
 La commande du compilateur Visual Basic est très semblable :  
  
 **vbc Example1.vb**  
  
 Étant donné qu'il n'existe aucune ressource incorporé dans l'assembly principal, vous n'avez pas à compiler à l'aide de le commutateur `/resource`.  
  
 Lorsque vous exécutez l'exemple d'un système de la langue est quelque chose d'autre que le Russe, il affiche la sortie suivante :  
  
```  
Bon jour!  
```  
  
## Autre empaquetage suggéré  
 Des raison de temps ou de budgets peuvent vous empêcher de créer un ensemble de ressources pour chaque sous\-culture que votre application prend en charge.  A la place, vous pouvez créer un assembly satellite pour une culture parente qui peut être utilisé par toutes les sous\-cultures apparentées.  Par exemple, vous pouvez fournir un unique assembly satellite anglais \(en\) qui est extrait par les utilisateurs qui demandent des ressources anglaises spécifiques à une région et un assembly satellite allemand \(de\) pour les utilisateurs qui demandent des ressources allemandes spécifiques à une région.  Par exemple, les demandes en allemand pour l'Allemagne \(de\-DE\), allemand pour l'Autriche \(de\-AT\) et en allemand pour la Suisse \(de\-CH\) reviennent à l'assembly satellite allemand \(de\).  Les ressources par défaut sont les ressources de secours final et doivent être les ressources qui seront demandées par la majorité des utilisateurs de votre application, donc choisissez ce ressouces avec precaution.  Cette solution déploie des ressources qui ne sont pas spécifiques à une culture, mais elle peut réduire de manière significative les coûts de localisation de votre application.  
  
## Voir aussi  
 [Ressources dans des applications de bureau](../../../docs/framework/resources/index.md)   
 [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)   
 [Création de fichiers de ressources](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)   
 [Création d'assemblys satellites](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)