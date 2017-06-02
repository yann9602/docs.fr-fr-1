---
title: "Tra&#231;age et instrumentation d&#39;applications | Microsoft Docs"
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
  - "traçage (.NET Framework)"
  - "débogage (.NET Framework), instrumentation"
  - "analyse des performances, instrumentation"
  - "instrumentation, à propos de l’instrumentation"
  - "traçage (.NET Framework), à propos du traçage"
  - "analyse des performances, le code de traçage"
  - "Trace (classe), instrumentation pour les applications .NET"
ms.assetid: 773b6fc4-9013-4322-b728-5dec7a72e743
caps.latest.revision: 21
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 21
---
# Tra&#231;age et instrumentation d&#39;applications
Le traçage vous permet de surveiller le fonctionnement de votre application pendant son exécution. Vous pouvez ajouter l'instrumentation de traçage et de débogage à votre application .NET Framework au moment du développement, et utiliser cette instrumentation pendant le développement de l'application et après son déploiement. Vous pouvez utiliser la <xref:System.Diagnostics.Trace?displayProperty=fullName>, <xref:System.Diagnostics.Debug?displayProperty=fullName>, et <xref:System.Diagnostics.TraceSource?displayProperty=fullName> classes pour enregistrer des informations sur les erreurs et l’exécution d’applications dans des journaux, des fichiers texte ou autres périphériques pour les analyser ultérieurement.  
  
 Le terme *instrumentation* fait référence à la capacité de contrôler ou de mesurer le niveau de performance d’un produit et de diagnostiquer les erreurs. En programmation, c'est la capacité d'une application à incorporer les éléments suivants :  
  
-   **Traçage de code** -réception de messages informatifs sur l’exécution d’une application au moment de l’exécution.  
  
-   **Débogage** : suivi et résolution des erreurs de programmation dans une application en cours de développement. Pour plus d’informations, consultez [débogage](../Topic/Debugging%20in%20Visual%20Studio.md).  
  
-   **Les compteurs de performance** -composants qui vous permettent de suivre les performances de votre application. Pour plus d’informations, consultez [les compteurs de Performance](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
-   **Journaux des événements** -composants qui vous permettent de recevoir et suivre les principaux événements de l’exécution de votre application. Pour plus d’informations, consultez la <xref:System.Diagnostics.EventLog> classe.  
  
 L'instrumentation de votre application, en plaçant des instructions de trace à des endroits stratégiques de votre code, est particulièrement utile pour les applications distribuées. Avec les instructions de trace, vous pouvez instrumenter une application pour afficher des informations en cas de problème, mais aussi pour surveiller les performances d'exécution de l'application.  
  
 Le <xref:System.Diagnostics.TraceSource> classe fournit des fonctionnalités de suivi améliorées et peut être utilisé à la place des méthodes statiques des anciennes <xref:System.Diagnostics.Trace> et <xref:System.Diagnostics.Debug> classes de traçage. La version classique <xref:System.Diagnostics.Trace> et <xref:System.Diagnostics.Debug> classes sont toujours largement utilisées, mais la <xref:System.Diagnostics.TraceSource> classe est recommandée pour les nouvelles commandes de traçage, telles que <xref:System.Diagnostics.TraceSource.TraceEvent%2A> et <xref:System.Diagnostics.TraceSource.TraceData%2A>.  
  
 Le <xref:System.Diagnostics.Trace> et <xref:System.Diagnostics.Debug> classes sont identiques, sauf que les procédures et fonctions de la <xref:System.Diagnostics.Trace> classe sont compilées par défaut dans les versions release, mais celles de la <xref:System.Diagnostics.Debug> classe ne sont pas.  
  
 Le <xref:System.Diagnostics.Trace> et <xref:System.Diagnostics.Debug> classes permettent de surveiller et analyser les performances de l’application lors du développement ou après le déploiement. Par exemple, vous pouvez utiliser la <xref:System.Diagnostics.Trace> classe pour effectuer le suivi des actions dans une application déployée particulières qu’elles se produisent (par exemple, la création de nouvelles connexions de base de données) et ainsi contrôler l’efficacité de l’application.  
  
## <a name="code-tracing-and-debugging"></a>Traçage et débogage de code  
 Pendant le développement, vous pouvez utiliser les méthodes de sortie de la <xref:System.Diagnostics.Debug> classe pour afficher les messages dans la fenêtre Sortie de l’environnement de développement intégré (IDE) Visual Studio. Exemple :  
  
```vb  
Trace.WriteLine("Hello World!")  
Debug.WriteLine("Hello World!")  
  
```  
  
```csharp  
System.Diagnostics.Trace.WriteLine("Hello World!");  
System.Diagnostics.Debug.WriteLine("Hello World!");  
  
```  
  
 Chacun de ces exemples affiche « Hello World ! » dans la fenêtre Sortie lorsque l’application est exécutée dans le débogueur.  
  
 Cela vous permet de déboguer vos applications et d'optimiser leurs performances en fonction de leur comportement dans votre environnement de test. Vous pouvez déboguer votre application dans votre version debug en activant le <xref:System.Diagnostics.Debug> attribut conditionnel afin que vous recevez toutes les sorties de débogage. Lorsque votre application est prête à être publiée, vous pouvez compiler votre version Release sans activer la <xref:System.Diagnostics.Debug> attribut conditionnel, afin que le compilateur n’inclura pas votre code de débogage dans le fichier exécutable final. Pour plus d’informations, consultez [Comment : compilation conditionnelle avec Trace et Debug](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md). Pour plus d’informations sur les différentes configurations de build pour votre application, consultez la page [compilation et génération de](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md).  
  
 Vous pouvez aussi tracer l’exécution de code dans une application installée en utilisant des méthodes de la <xref:System.Diagnostics.Trace> classe. En plaçant [des commutateurs de traçage](../../../docs/framework/debug-trace-profile/trace-switches.md) dans votre code, vous pouvez contrôler si le traçage se produit et jusqu'à quel point. Vous pouvez ainsi surveiller l'état de votre application dans un environnement de production, ce qui est particulièrement important dans le cas d'une application professionnelle qui utilise plusieurs composants exécutés sur différents ordinateurs. Vous pouvez contrôler la manière dont les commutateurs sont utilisés après le déploiement par le biais du fichier de configuration. Pour plus d’informations, consultez [Comment : créer, initialiser et configurer des commutateurs de traçage](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
 Quand vous développez une application pour laquelle vous envisagez d'utiliser la fonctionnalité de traçage, vous incluez généralement des messages de traçage et de débogage dans le code de l'application. Lorsque vous êtes prêt à déployer l’application, vous pouvez compiler votre version Release sans activer la **Debug** attribut conditionnel. Toutefois, vous pouvez activer la **Trace** attribut conditionnel afin que le compilateur inclue votre code de traçage dans le fichier exécutable. Pour plus d’informations, consultez [Comment : compilation conditionnelle avec Trace et Debug](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).  
  
### <a name="phases-of-code-tracing"></a>Phases du traçage de code  
 Le traçage de code comprend les trois phases suivantes :  
  
1.  **Instrumentation** — vous ajoutez le code de traçage à votre application.  
  
2.  **Suivi** : le code de traçage écrit les informations dans la cible spécifiée.  
  
3.  **Analyse** — vous évaluez les informations de traçage pour identifier et comprendre les problèmes dans l’application.  
  
 Durant le développement, toutes les méthodes de sortie de débogage et de traçage écrivent les informations par défaut dans la fenêtre Sortie de Visual Studio. Dans une application déployée, les méthodes écrivent les informations de traçage vers les cibles de votre choix. Pour plus d’informations sur la spécification d’une cible de sortie pour le traçage ou le débogage, consultez [écouteurs de traçage](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 La section suivante décrit les principales étapes généralement suivies lors du traçage pour analyser et corriger des problèmes potentiels dans des applications déployées. Pour plus d'informations sur ces étapes, voir les liens appropriés.  
  
##### <a name="to-use-tracing-in-an-application"></a>Pour utiliser le traçage dans une application  
  
1.  Déterminez la sortie de traçage que vous souhaitez obtenir sur place après avoir déployé l'application.  
  
2.  Créez un jeu de commutateurs. Pour plus d’informations, consultez [Comment : configurer des commutateurs de traçage](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
3.  Ajoutez les instructions de trace au code de l'application.  
  
4.  Déterminez l'emplacement d'affichage de la sortie de traçage et ajoutez les écouteurs appropriés. Pour plus d’informations, consultez [création et initialisation des écouteurs de traçage](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md).  
  
5.  Testez et déboguez votre application ainsi que le code de trace qu'elle contient.  
  
6.  Compilez l'application en code exécutable, en suivant l'une des procédures ci-dessous :  
  
    -   Utilisez le **Build** menu avec le **déboguer** page de la **Pages de propriétés** boîte de dialogue de **l’Explorateur de solutions**. Procédez ainsi pour compiler votre application dans Visual Studio.  
  
         \- ou -  
  
    -   Utilisez le **Trace** et **Debug** directives de compilateur pour la méthode de ligne de commande de compilation. Pour plus d’informations, consultez [compilation conditionnelle avec Trace et Debug](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md). Procédez ainsi pour compiler votre application à partir d'une ligne de commande.  
  
7.  Si un problème survient au moment de l'exécution, activez le commutateur de trace approprié. Pour plus d’informations, consultez [configuration des commutateurs de traçage](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
     Le code de trace écrit les messages de traçage vers la cible spécifiée (par exemple, un écran, un fichier texte ou un journal des événements). Le type d’écouteur que vous avez inclus dans le **Trace.Listeners** collection détermine la cible.  
  
8.  Analysez les messages de traçage pour identifier et comprendre les problèmes potentiels dans l'application.  
  
## <a name="trace-instrumentation-and-distributed-applications"></a>Instrumentation de traçage pour les applications distribuées  
 Pendant la phase de création d'une application distribuée, il peut être difficile de tester l'application dans des conditions d'utilisation réelles. Les équipes de développement ont rarement la possibilité de tester toutes les combinaisons de systèmes d'exploitation ou de navigateurs web (y compris toutes les versions localisées) ou de simuler un nombre élevé d'utilisateurs qui accéderont simultanément à l'application. Vous ne pouvez donc pas tester la manière dont une application distribuée répondra à un fort trafic, à des configurations différentes et aux comportements propres à chaque utilisateur final. Par ailleurs, vous ne pouvez pas interagir directement avec toutes les parties de l'application distribuée, ni afficher leur activité, car beaucoup d'entre elles ne possèdent pas l'interface utilisateur nécessaire.  
  
 Cependant, vous pourrez pallier cette en permettant aux applications distribuées de décrire certains événements intéressants aux administrateurs système, en particulier les problèmes incorrect, par *instrumentation* l’application, autrement dit, en plaçant des instructions de traçage à des endroits stratégiques de votre code. Ainsi, si l'application a un comportement inattendu au moment de l'exécution (par exemple, un temps de réponse très lent), vous pouvez en déterminer la cause probable.  
  
 Grâce aux instructions de trace, vous ne perdez pas de temps à analyser, modifier et recompiler le code source d'origine, ni à essayer de reproduire l'erreur d'exécution dans l'environnement de débogage. Rappelez-vous que l'instrumentation d'une application est utile pour afficher les erreurs, mais aussi pour surveiller les performances.  
  
## <a name="strategic-placement-of-trace-statements"></a>Placement stratégique des instructions de trace  
 Choisissez avec soin les endroits où vous allez placer les instructions de trace qui seront utilisées au moment de l'exécution. Vous devez déterminer quelles informations de traçage seront les plus utiles dans une application déployée afin que tous les scénarios de traçage probables soient traités de manière adéquate. Les applications utilisant la fonctionnalité de traçage étant très diverses, il n'existe pas d'instructions générales pour placer stratégiquement des instructions de trace. Pour plus d’informations sur le placement des instructions de traçage, consultez [Comment : ajouter des instructions de traçage au Code d’Application](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md).  
  
## <a name="output-from-tracing"></a>Sortie de trace  
 Sortie de trace est collectée par des objets appelés *écouteurs*. Un écouteur est un objet qui reçoit la sortie de trace et qui l'écrit dans une cible de sortie (généralement une fenêtre, un journal ou un fichier texte). Lorsqu’un écouteur de la trace est créé, il est généralement ajouté à la <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=fullName> collection, ce qui permet de l’écouteur de recevoir toutes les sorties de trace.  
  
 Les informations de traçage sont écrites toujours au moins à la valeur par défaut <xref:System.Diagnostics.Trace> cible de sortie, le <xref:System.Diagnostics.DefaultTraceListener>. Si pour une raison quelconque, vous avez supprimé le <xref:System.Diagnostics.DefaultTraceListener> sans ajouter d’autres écouteurs à la <xref:System.Diagnostics.Trace.Listeners%2A> collection, vous ne recevrez pas de messages de trace. Pour plus d’informations, consultez [écouteurs de traçage](../../../docs/framework/debug-trace-profile/trace-listeners.md).  
  
 Les six <xref:System.Diagnostics.Debug> membres et <xref:System.Diagnostics.Trace> méthodes qui écrivent des informations de traçage sont répertoriées dans le tableau suivant.  
  
|Méthode|Sortie|  
|------------|------------|  
|**Assert**|Le texte spécifié ou, si aucun texte n'est spécifié, la pile des appels. La sortie est uniquement écrite si la condition spécifiée en tant qu’argument dans les **Assert** instruction est **false**.|  
|**Échec**|Le texte spécifié ou, si aucun texte n'est spécifié, la pile des appels.|  
|**Écriture**|Le texte spécifié.|  
|**WriteIf**|Le texte spécifié si la condition spécifiée en tant qu’argument dans les **WriteIf** instruction est satisfaite.|  
|**WriteLine**|Le texte spécifié et un retour chariot.|  
|**WriteLineIf**|Le texte spécifié et un retour chariot si la condition spécifiée en tant qu’argument dans les **WriteLineIf** instruction est satisfaite.|  
  
 Tous les écouteurs de la <xref:System.Diagnostics.Trace.Listeners%2A> reçoivent les messages décrits dans le tableau ci-dessus, mais les actions prises peuvent varier en fonction du type d’écouteur qui reçoit le message. Par exemple, le <xref:System.Diagnostics.DefaultTraceListener> affiche une boîte de dialogue d’assertion lorsqu’il reçoit un **échec** ou n’a pas pu **Assert** notification, mais un <xref:System.Diagnostics.TextWriterTraceListener> écrit simplement la sortie dans son flux.  
  
 Vous pouvez générer des résultats personnalisés en implémentant votre propre écouteur. Par exemple, créez un écouteur de la trace personnalisé qui affiche les messages dans une boîte de message ou qui se connecte à une base de données pour ajouter les messages à une table. Tous les écouteurs personnalisés doivent prendre en charge les six méthodes mentionnées ci-dessus. Pour plus d’informations sur la création d’écouteurs définis par le développeur, consultez <xref:System.Diagnostics.TraceListener> dans la documentation .NET Framework.  
  
> [!NOTE]
>  Dans [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], le **Debug.Write**, **Debug.WriteIf**, **Debug.WriteLine**, et **Debug.WriteLineIf** ont remplacé la **Debug.Print** méthode qui était disponible dans les versions antérieures de Visual Basic.  
  
 Le **écrire** et **WriteLine** méthodes écrivent toujours le texte que vous spécifiez. **Assert**, **WriteIf**, et **WriteLineIf** nécessitent un argument Boolean qui contrôle si elles écrivent le texte spécifié ; elles écrivent le texte spécifié uniquement si l’expression est **true** (pour **WriteIf** et **WriteLineIf**), ou **false** (pour **Assert**). Le **échec** méthode écrit toujours le texte spécifié. Pour plus d’informations, consultez [Comment : ajouter des instructions de traçage au Code d’Application](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md) et la documentation .NET Framework.  
  
## <a name="security-concerns"></a>Problèmes de sécurité  
 Si vous ne désactivez pas le traçage et le débogage avant de déployer votre application ASP.NET, celle-ci peut dévoiler des informations exploitables par un programme malveillant. Pour plus d’informations, consultez [Comment : compilation conditionnelle avec Trace et Debug](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md), [compilation et génération de](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md), et [Comment : créer, initialiser et configurer des commutateurs de traçage](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md). Vous pouvez également configurer le débogage via IIS (Internet Information Services).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Diagnostics.Trace>   
 <xref:System.Diagnostics.TraceSource>   
 [Contrats de code](../../../docs/framework/debug-trace-profile/code-contracts.md)   
 [C#, F # et Types de projets Visual Basic](../Topic/Debugging%20Preparation:%20C%23,%20F%23,%20and%20Visual%20Basic%20Project%20Types.md)   
 [Comment : ajouter des instructions de traçage au Code d’Application](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)   
 [Comment : effectuer une compilation conditionnelle avec Trace et Debug](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)   
 [Comment : créer, initialiser et configurer des commutateurs de traçage](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)   
 [Comment : créer et initialiser les Sources de Trace](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)   
 [Comment : utiliser des TraceSource et des filtres avec des écouteurs de traçage](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md)   
 [Écouteurs de traçage](../../../docs/framework/debug-trace-profile/trace-listeners.md)   
 [Commutateurs de traçage](../../../docs/framework/debug-trace-profile/trace-switches.md)