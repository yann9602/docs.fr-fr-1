---
title: "G&#233;n&#233;ration de profils d&#39;ex&#233;cution | Microsoft Docs"
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
  - "compteurs de performance"
  - "Common Language Runtime, profiler"
  - "Perfmon.exe"
  - "Moniteur système"
  - "profils"
  - "runtime, profiler"
  - "profiler des applications"
  - "console de performance"
ms.assetid: ccd68284-f3a8-47b8-bc3f-92e5fe3a1640
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 22
---
# G&#233;n&#233;ration de profils d&#39;ex&#233;cution
Le profilage est une méthode de collecte de données de performance dans le cadre d’un scénario de développement ou de déploiement. Cette section s’adresse aux développeurs et administrateurs système qui souhaitent recueillir des informations sur les performances d’une application.  
  
## Suivi des performances à l’aide de l’analyseur de performances \(Perfmon.exe\)  
 L’analyseur de performances est l’outil le plus simple à utiliser pour profiler votre application [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. L’analyseur de performances représente graphiquement les données trouvées dans les compteurs de performances .NET Framework qui sont installés avec le Common Language Runtime et le [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]. Ces compteurs permettent de tout surveiller, de la gestion de la mémoire jusqu’aux performances du compilateur juste\-à\-temps \(JIT\). Ils vous renseignent sur les ressources que votre application utilise, ce qui est une mesure indirecte des performances de votre application. Ces compteurs s’avèrent utiles pour comprendre le fonctionnement interne de votre application.  
  
#### Pour exécuter Perfmon.exe sur Windows Vista et les versions ultérieures  
  
1.  À l'invite de commandes, entrez **perfmon**. La console **Analyseur de performances** apparaît.  
  
2.  Dans le dossier **Outils d’analyse**, cliquez sur **Analyseur de performances**.  
  
3.  Dans la barre d’outils de l’analyseur de performances, cliquez sur l’icône **Ajouter** \(signe plus\), si elle est présente. À défaut, cliquez avec le bouton droit dans la fenêtre de l’analyseur et sélectionnez l’option **Ajouter des compteurs**.  
  
     La boîte de dialogue **Ajouter des compteurs** s’ouvre. La zone de liste **Compteurs disponibles** présente les objets de performance disponibles. Il existe plusieurs objets prédéfinis pour les applications .NET Framework, notamment ceux qui touchent à la gestion de la mémoire \(**.NET CLR Memory**\), à l’interopérabilité \(**.NET CLR Interop**\), à la gestion des exceptions \(**.NET CLR Exceptions**\) et au multithreading \(**.NET CLR LocksAndThreads**\). Chaque objet de performance comprend un certain nombre de compteurs de performances individuels. Pour obtenir la liste des compteurs de performances disponibles dans l’analyseur de performances, consultez [Performance Counters](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
4.  Cochez la case en regard du nom d’un objet de performance pour afficher la liste des compteurs de performances individuels qu’il prend en charge.  
  
5.  Cliquez sur le compteur de performances que vous voulez afficher.  
  
6.  Dans la zone de liste **Instances de l’objet sélectionné**, cliquez sur **\<Toutes les instances\>** pour spécifier que vous voulez analyser le compteur de performances pour le Common Language Runtime dans sa globalité \(c’est\-à\-dire, à l’échelle du système\).  
  
     ou  
  
     Dans la zone de liste **Instances de l’objet sélectionné**, cliquez sur le nom d’une application pour analyser le compteur de performances de cette application.  
  
     Pour différencier plusieurs versions du runtime ou pour lever toute ambiguïté quant aux applications qui ont le même nom, vous devez aussi modifier une clé de Registre. Pour plus d'informations, consultez [Performance Counters and In\-Process Side\-By\-Side Applications](../../../docs/framework/debug-trace-profile/performance-counters-and-in-process-side-by-side-applications.md).  
  
> [!NOTE]
>  Si des compteurs de performances nouveaux sont installés pendant l’exécution de la console de performances, arrêtez et redémarrez la console de performances pour les rendre visibles.  
  
 Si vous voulez profiler un assembly qui existe dans une zone ou sur un partage distant, assurez\-vous que l’assembly distant bénéficie d’une confiance totale sur l’ordinateur qui exécute les compteurs de performances. Si l’assembly n’a pas un niveau de confiance suffisant, les compteurs de performances ne fonctionnent pas. Pour plus d’informations sur la façon d’accorder la confiance à différentes zones, consultez [Caspol.exe \(Code Access Security Policy Tool\)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).  
  
> [!NOTE]
>  Sur les systèmes où le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] est installé, il se peut que l’analyseur de performances n’affiche pas de données pour les compteurs de performances de certaines catégories, telles que **.NET CLR Data** et **.NET CLR Networking**, pour les applications développées à l’aide du [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)]. Si c’est le cas, vous pouvez configurer l’analyseur de performances pour qu’il affiche ces données en ajoutant l’élément [\<forcePerformanceCounterUniqueSharedMemoryReads\>](../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) au fichier de configuration de l’application.  
  
## Lecture et création de compteurs de performances par programmation  
 Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] propose des classes qui vous permettent d’accéder par programmation aux mêmes informations de performances que celles qui sont disponibles dans la console de performances. Vous pouvez aussi utiliser ces classes pour créer des compteurs de performances personnalisés. Le tableau suivant décrit quelques\-unes des classes d’analyse de performances proposées dans le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
|Classe|Description|  
|------------|-----------------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=fullName>|Représente un composant de compteur de performances Windows NT. Cette classe permet de lire les compteurs prédéfinis ou personnalisés existants et de publier \(écrire\) des données de performance dans des compteurs personnalisés.|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=fullName>|Propose plusieurs méthodes permettant d’interagir avec les compteurs et les catégories de compteurs de l’ordinateur.|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=fullName>|Spécifie un programme d’installation pour le composant `PerformanceCounter`.|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=fullName>|Spécifie la formule de calcul de la méthode `NextValue` pour un `PerformanceCounter`.|  
  
## Voir aussi  
 [Performance Counters](../../../docs/framework/debug-trace-profile/performance-counters.md)