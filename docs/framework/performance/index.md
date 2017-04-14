---
title: ".NET Framework Performance | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "performance [.NET Framework]"
  - "reliability [.NET Framework]"
ms.assetid: c1676cca-3f1a-41ec-b469-9029566074fc
caps.latest.revision: 20
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 20
---
# .NET Framework Performance
Si vous voulez créer des applications dotées de hautes performances, vous devez concevoir et planifier les performances comme vous concevez n'importe quelle autre fonctionnalité de votre application.  Vous pouvez utiliser les outils fournis par Microsoft pour mesurer les performances de votre application et, si nécessaire, apporter des améliorations à l'utilisation de la mémoire, au débit de code et à la réactivité.  Cette rubrique répertorie les outils d'analyse de performance fournis par Microsoft et fournit des liens vers d'autres rubriques qui couvrent les performances dans des domaines spécifiques du développement d'applications.  
  
## Conception et planification des performances  
 Pour créer une application présentant d'excellentes performances, vous devez concevoir les performances dans votre application comme si vous conceviez n'importe quelle autre fonctionnalité.  Vous devez déterminer les scénarios où les performances sont essentielles, définir des objectifs de performances et mesurer régulièrement les performances dans ces scénarios d'application.  Comme chaque application est différente et possède différents chemins d'exécution aux performances critiques, le fait de déterminer précocement ces chemins et de concentrer vos efforts vous permet de maximiser votre productivité.  
  
 Il n'est pas nécessaire que votre plateforme cible vous soit complètement familière pour créer une application à hautes performances.  Toutefois, vous devez chercher à comprendre quelles parties de votre plateforme cible sont coûteuses en termes de performances.  Pour cela, vous pouvez mesurer les performances tôt dans votre processus de développement.  
  
 Pour déterminer les domaines essentiels pour les performances et pour établir vos objectifs de performances, prenez toujours en compte l'expérience utilisateur.  Le temps de démarrage et la réactivité sont deux domaines clés qui affectent la perception qu'a l'utilisateur de votre application.  Si votre application utilise beaucoup de mémoire, elle peut sembler lente à l'utilisateur ou affecter d'autres applications qui s'exécutent sur le système, ou, dans certains cas, elle peut échouer au test de soumission du Windows Store ou du Windows Phone Store.  De plus, si vous déterminez quelles parties de votre code s'exécutent le plus fréquemment, vous pouvez veiller à l'optimisation de ces parties de code.  
  
## Analyse des performances  
 Dans le cadre de votre plan de développement global, définissez des points durant le développement où mesurer les performances de votre application et comparer les résultats aux objectifs que vous avez définis précédemment.  Mesurez votre application dans l'environnement et avec le matériel que posséderont selon vous les utilisateurs.  En analysant les performances de votre application tôt et régulièrement, vous pouvez changer les décisions architecturales qui seraient coûteuses à corriger ultérieurement dans le cycle de développement.  Les sections suivantes décrivent les outils de performance que vous pouvez utiliser pour analyser vos applications et traitent du suivi d'événements, qui est utilisé par ces outils.  
  
### Outils d'analyse des performances  
 Voici certains outils de performance que vous pouvez utiliser avec vos applications .NET Framework.  
  
|Outil|Description|  
|-----------|-----------------|  
|Analyse des performances Visual Studio|Utilisez cet outil pour analyser l'utilisation de l'UC de vos applications .NET Framework qui seront déployées sur des ordinateurs exécutant le système d'exploitation Windows.<br /><br /> Cet outil est disponible dans le menu **Débogage** de Visual Studio lorsque vous ouvrez un projet.  Pour plus d'informations, voir [Utilisation des outils de profilage](../Topic/Performance%20Explorer.md). **Note:**  Utilisez l'analyse de l'application Windows Phone \(voir ligne suivante\) quand vous ciblez Windows Phone.|  
|Analyse de l'application Windows Phone|Utilisez cet outil pour analyser l'UC et la mémoire, le taux de transfert des données réseau, la réactivité de l'application et la consommation de la batterie dans vos applications Windows Phone.<br /><br /> Cet outil est disponible dans le menu **Débogage** pour un projet Windows Phone dans Visual Studio une fois que vous avez installé [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=265773).  Pour plus d'informations, voir [Profilage d'applications pour Windows Phone](http://msdn.microsoft.com/library/windowsphone/develop/jj215908\(v=vs.105\).aspx).|  
|[PerfView](http://www.microsoft.com/download/details.aspx?id=28567)|Utilisez ces outils pour identifier des problèmes de performances liés à l'UC et à la mémoire.  Cet outil utilise le suivi d'événements pour Windows et des API de profilage du CLR pour assurer des investigations avancées de la mémoire et de l'UC, et pour fournir des informations sur le garbage collection et la compilation JIT.  Pour plus d'informations sur la manière d'utiliser PerfView, consultez le didacticiel et les fichiers d'aide inclus avec l'application, les [didacticiels vidéo de Channel 9](http://channel9.msdn.com/Series/PerfView-Tutorial) et les [billets de blog](http://blogs.msdn.com/b/vancem/archive/tags/perfview/).<br /><br /> Pour des problèmes spécifiques à la mémoire, consultez [Utilisation de PerfView pour des investigations de la mémoire](http://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-9-NET-Memory-Investigation-Basics-of-GC-Heap-Snapshots).|  
|[Analyseur de performance Windows](http://www.microsoft.com/download/details.aspx?id=30652)|Utilisez cet outil pour déterminer les performances globales du système telles que l'utilisation de la mémoire et du stockage par votre application quand plusieurs applications s'exécutent sur le même ordinateur.  Cet outil est disponible à partir du centre de téléchargement dans le cadre du Kit de déploiement et d’évaluation Windows \(Windows ADK\) pour [!INCLUDE[win8](../../../includes/win8-md.md)].  Pour plus d'informations, voir [Analyseur de performance Windows](http://msdn.microsoft.com/library/windows/desktop/hh448170.aspx).|  
  
### Suivi d'événements pour Windows \(ETW\)  
 Le suivi d'événements pour Windows est une technique qui vous permet d'obtenir des informations de diagnostic sur le code en cours d'exécution et qui est essentielle pour un grand nombre des outils de performance mentionnés précédemment.  Il crée des journaux lorsque des événements particuliers sont déclenchés par des applications .NET Framework et par Windows.  Le suivi d'événements pour Windows vous permet d'activer et désactiver la journalisation de façon dynamique, et vous pouvez effectuer un traçage détaillé dans un environnement de production sans redémarrer votre application.  .NET Framework propose la prise en charge des événements ETW, et le suivi d'événements pour Windows est utilisé par de nombreux outils de profilage et de performance pour générer des données de performance.  Ces outils activent et désactivent souvent des événements ETW et il est utile de se familiariser avec eux.  Vous pouvez utiliser des événements ETW spécifiques pour collecter des informations de performance sur des composants particuliers de votre application.  Pour plus d'informations sur la prise en charge du suivi d'événements ETW dans .NET Framework, voir [ETW Events in the Common Language Runtime](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md) et [Événements ETW dans la bibliothèque parallèle de tâches et PLINQ](../../../docs/framework/performance/etw-events-in-task-parallel-library-and-plinq.md).  
  
## Performances par type d'application  
 Chaque type d'application .NET Framework possède ses propres pratiques recommandées, considérations et outils pour évaluer les performances.  Le tableau ci\-dessous propose des liens vers des rubriques liées aux performances pour des types d'applications .NET Framework spécifiques.  
  
|Type d'application|Voir|  
|------------------------|----------|  
|Applications .NET Framework pour toutes les plateformes|[Garbage Collection and Performance](../../../docs/standard/garbage-collection/performance.md)<br /><br /> [Conseils relatifs aux performances](../../../docs/framework/performance/performance-tips.md)|  
|Applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] écrites en C\+\+, C\# et Visual Basic|[Meilleures pratiques pour les performances des applications du Windows Store en C\+\+, C\# et Visual Basic](http://msdn.microsoft.com/library/windows/apps/hh750313.aspx)|  
|Windows Phone|[Considérations sur les performances des applications pour Windows Phone](http://msdn.microsoft.com/library/windowsphone/develop/ff967560\(v=vs.105\).aspx)<br /><br /> [Analyse de l'application Windows Phone](http://msdn.microsoft.com/en-us/library/windowsphone/develop/hh202934\(v=vs.105\).aspx)<br /><br /> [Lancez plus rapidement vos applications Windows Phone sur le marché](http://msdn.microsoft.com/magazine/hh781024.aspx)|  
|Windows Presentation Foundation \(WPF\)|[WPF Performance Suite](../Topic/WPF%20Performance%20Suite.md)|  
|Silverlight|[Conseils liés aux performances](http://msdn.microsoft.com/library/cc189071\(v=vs.95\).aspx)|  
|ASP.NET|[ASP.NET Performance Overview](../Topic/ASP.NET%20Performance%20Overview.md)|  
|Windows Forms|[Conseils pratiques pour améliorer les performances des applications Windows Forms](http://msdn.microsoft.com/magazine/cc163630.aspx)|  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Caching in .NET Framework Applications](../../../docs/framework/performance/caching-in-net-framework-applications.md)|Décrit des techniques de mise en cache des données pour améliorer les performances dans votre application.|  
|[Lazy Initialization](../../../docs/framework/performance/lazy-initialization.md)|Décrit comment initialiser des objets selon vos besoins pour améliorer les performances, notamment au démarrage de l'application.|  
|[Reliability](../../../docs/framework/performance/reliability.md)|Fournit des informations sur la manière d'éviter les exceptions asynchrones dans un environnement serveur.|  
|[Conception d'applications .NET Framework complexes et réactives](../../../docs/framework/performance/writing-large-responsive-apps.md)|Fournit des conseils liés aux performances, rassemblés lors de la réécriture des compilateurs C\# et Visual Basic en code managé, et inclut plusieurs exemples réels issus du compilateur C\#.|