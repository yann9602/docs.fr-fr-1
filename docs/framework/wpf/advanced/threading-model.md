---
title: "Mod&#232;le de thread | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "texte des boutons, mise à jour"
  - "traitement du message, imbriquées"
  - "opérations de blocage"
  - "Dispatcher (classe)"
  - "Common Language Runtime (CLR), mécanisme de verrouillage"
  - "mécanisme de verrouillage du Common Language Runtime (CLR)"
  - "modèle de thread"
  - "classes, DependencyObject"
  - "Word, la vérification d’orthographe"
  - "bouton de texte, mise à jour"
  - "vérifier l'orthographe dans Word"
  - "comportement asynchrone, exposant"
  - "DependencyObject (classe)"
  - "messages imbriqués (traitement)"
  - "classes de répartiteur"
  - "réentrance"
ms.assetid: 02d8fd00-8d7c-4604-874c-58e40786770b
caps.latest.revision: 33
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 32
---
# Mod&#232;le de thread
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]est conçu pour épargner aux développeurs les difficultés de threading. Par conséquent, la majorité des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les développeurs auront pas à écrire une interface qui utilise plusieurs threads. Programmes multithread sont complexes et difficiles à déboguer, ils doivent être évités lorsque des solutions monothread existent.  
  
 Aucune question comment bien ne conçu, toutefois, aucune [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] framework sera toujours en mesure de fournir une solution monothread pour chaque type de problème.              [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]s’en rapproche, mais il existe toujours des situations où plusieurs threads améliorent [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] performances ou la réactivité des applications. Après avoir discuté des informations d’ordre général, ce document explore certaines de ces situations et puis se termine par une discussion sur certains détails de niveau inférieur.  
  
   
  
> [!NOTE]
>  Cette rubrique étudie les threads à l’aide de la <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> méthode pour les appels asynchrones. Vous pouvez également effectuer des appels asynchrones en appelant le <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> (méthode), qui prennent un <xref:System.Action> ou <xref:System.Func%601> en tant que paramètre.  Le <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> méthode renvoie un <xref:System.Windows.Threading.DispatcherOperation> ou <xref:System.Windows.Threading.DispatcherOperation%601>, qui a un <xref:System.Windows.Threading.DispatcherOperation.Task%2A> propriété. Vous pouvez utiliser la `await` mot clé soit le <xref:System.Windows.Threading.DispatcherOperation> ou associé <xref:System.Threading.Tasks.Task>. Si vous devez attendre de manière synchrone pour le <xref:System.Threading.Tasks.Task> qui est retourné par une <xref:System.Windows.Threading.DispatcherOperation> ou <xref:System.Windows.Threading.DispatcherOperation%601>, appelez le <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> méthode d’extension.  Appel de <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=fullName> entraîne un blocage. Pour plus d’informations sur l’utilisation d’un <xref:System.Threading.Tasks.Task> pour effectuer des opérations asynchrones, consultez le parallélisme des tâches.  Le <xref:System.Windows.Threading.Dispatcher.Invoke%2A> méthode a également des surcharges qui prennent un <xref:System.Action> ou <xref:System.Func%601> en tant que paramètre.  Vous pouvez utiliser la <xref:System.Windows.Threading.Dispatcher.Invoke%2A> méthode pour rendre synchrone appelle en passant un délégué, <xref:System.Action> ou <xref:System.Func%601>.  
  
<a name="threading_overview"></a>   
## <a name="overview-and-the-dispatcher"></a>Vue d’ensemble et répartiteur  
 En règle générale, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications démarrent avec deux threads : un pour gérer le rendu et l’autre pour la gestion de la [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Le thread de rendu s’exécute efficacement masqué en arrière-plan pendant que le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread reçoit l’entrée, gère les événements, peint l’écran et exécute le code de l’application. La plupart des applications utilisent une seule [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread, bien que dans certaines situations, il est préférable d’utiliser plusieurs. Nous aborderons ce avec un exemple plus loin.  
  
 Le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] opérations de files d’attente du thread à l’intérieur d’un objet appelé un <xref:System.Windows.Threading.Dispatcher>. Le <xref:System.Windows.Threading.Dispatcher> sélectionne les éléments de travail en priorité et exécute chacun d’eux.  Chaque [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread doit avoir au moins un <xref:System.Windows.Threading.Dispatcher>et chaque <xref:System.Windows.Threading.Dispatcher> peut exécuter les éléments de travail dans un seul thread.  
  
 L’astuce pour générer des applications conviviales et réactives consiste à optimiser le <xref:System.Windows.Threading.Dispatcher> débit en conservant les éléments de travail des petites. Les éléments de cette façon jamais périmés dans la <xref:System.Windows.Threading.Dispatcher> file d’attente de traitement. Tout délai perceptible entre entrée et réponse peut frustrer un utilisateur.  
  
 Comment sont [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications supposées pour gérer les opérations volumineuses ? Que se passe-t-il si votre code implique un grand calcul ou doit interroger une base de données sur un serveur distant ? En règle générale, la solution consiste à gérer l’opération volumineuse dans un thread séparé, en laissant le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread libre pour gérer les éléments dans le <xref:System.Windows.Threading.Dispatcher> file d’attente. Lorsque l’opération volumineuse est terminée, il peut indiquer son résultat à le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread pour l’affichage.  
  
 Historiquement, [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] permet [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] éléments accessibles uniquement par le thread qui les a créés. Cela signifie qu’un thread d’arrière-plan chargé des tâches longues ne peut pas mettre à jour une zone de texte lorsqu’elle est terminée.                  [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]Pour cela, pour garantir l’intégrité de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] composants. Une zone de liste pourrait sembler étrange si son contenu ont été mis à jour par un thread d’arrière-plan au cours de la peinture.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]possède un mécanisme d’exclusion mutuelle qui applique cette coordination. La plupart des classes dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dérivent <xref:System.Windows.Threading.DispatcherObject>. Lors de la construction, un <xref:System.Windows.Threading.DispatcherObject> stocke une référence à la <xref:System.Windows.Threading.Dispatcher> lié au thread en cours d’exécution. En effet, le <xref:System.Windows.Threading.DispatcherObject> associe au thread qui le crée. Pendant l’exécution du programme, un <xref:System.Windows.Threading.DispatcherObject> peut appeler son public <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> méthode.                  <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> examine les <xref:System.Windows.Threading.Dispatcher> associé au thread actuel et le compare à la <xref:System.Windows.Threading.Dispatcher> stockée pendant la construction de référence. Si elles ne correspondent pas, <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> lève une exception.                  <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> est destinée à être appelée au début de chaque méthode qui appartient à un <xref:System.Windows.Threading.DispatcherObject>.  
  
 Si seul un thread peut modifier le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], comment les threads d’arrière-plan interagir avec l’utilisateur ? Un thread d’arrière-plan peut demander le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread pour effectuer une opération en son nom. Pour ce faire, il enregistre un élément de travail avec le <xref:System.Windows.Threading.Dispatcher> de la [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread. Le <xref:System.Windows.Threading.Dispatcher> classe fournit deux méthodes d’enregistrement des éléments de travail : <xref:System.Windows.Threading.Dispatcher.Invoke%2A> et <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>. Ces deux méthodes planifient un délégué pour l’exécution.                  <xref:System.Windows.Threading.Dispatcher.Invoke%2A> est un appel synchrone, autrement dit, il ne retourne pas tant que le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread a réellement terminé l’exécution du délégué.                  <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> est asynchrone et retourne immédiatement.  
  
 Le <xref:System.Windows.Threading.Dispatcher> trie les éléments dans sa file d’attente par priorité. Il y a dix niveaux qui peuvent être spécifiées lors de l’ajout d’un élément à la <xref:System.Windows.Threading.Dispatcher> file d’attente. Ces priorités sont maintenues dans le <xref:System.Windows.Threading.DispatcherPriority> (énumération). Des informations détaillées sur <xref:System.Windows.Threading.DispatcherPriority> niveaux se trouve dans le [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)] documentation.  
  
<a name="samples"></a>   
## <a name="threads-in-action-the-samples"></a>Threads en Action : exemples  
  
<a name="prime_number"></a>   
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>Une Application à thread unique et un calcul de longue  
 La plupart des [!INCLUDE[TLA#tla_gui#plural](../../../../includes/tlasharptla-guisharpplural-md.md)] consacrer une grande partie de leur temps inactif en attendant des événements qui sont générés en réponse aux interactions de l’utilisateur. Programmation soignée cette durée d’inactivité peut être utilisée de manière constructive, sans affecter la réactivité de le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modèle de thread ne permet pas d’entrée d’interrompre une opération qui se produit dans le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread. Cela signifie que vous devez être sûr de revenir à la <xref:System.Windows.Threading.Dispatcher> régulièrement à des processus en attente d’événements d’entrée avant qu’ils deviennent périmés.  
  
 Prenons l'exemple suivant :  
  
 ![Capture d’écran : nombres premiers](../../../../docs/framework/wpf/advanced/media/threadingprimenumberscreenshot.PNG "ThreadingPrimeNumberScreenShot")  
  
 Cette application simple compte vers le haut à partir de trois, en recherchant des nombres premiers. Lorsque l’utilisateur clique sur le **Démarrer** bouton, la recherche commence. Lorsque le programme trouve un nombre premier, il met à jour l’interface utilisateur avec sa découverte. À tout moment, l’utilisateur peut arrêter la recherche.  
  
 Bien qu’assez simple, la recherche de nombres premiers peut être illimitée, ce qui présente des difficultés.  Si nous avions géré l’intégralité de la recherche à l’intérieur du Gestionnaire d’événements click du bouton, nous n’aurions jamais le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread une chance de traiter d’autres événements. Le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] est incapable de répondre à l’entrée ou de traiter les messages. Il serait jamais repeindre et jamais répondre aux clics de bouton.  
  
 Nous aurions pu effectuer la recherche de nombres premiers dans un thread distinct, mais nous devrions faire face aux problèmes de synchronisation. Avec une approche monothread, nous pouvons mettre à jour directement l’étiquette qui répertorie le plus grand nombre premier trouvé.  
  
 Si nous divisons la tâche de calcul en segments maniables, nous pouvons périodiquement retourner à la <xref:System.Windows.Threading.Dispatcher> et traiter des événements. Nous pouvons [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] une opportunité à redessiner et traiter l’entrée.  
  
 La meilleure façon de fractionner le traitement entre calcul et gestion des événements consiste à gérer le calcul à partir de la <xref:System.Windows.Threading.Dispatcher>. À l’aide de la <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (méthode), nous pouvons planifier des vérifications de nombres premiers dans la même file d’attente qui [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] événements sont retirées. Dans notre exemple, nous planifions uniquement une vérification des nombres premiers unique à la fois. Une fois que le contrôle de nombre premier est terminé, nous planifions immédiatement le prochain contrôle. Cette vérification se déroule uniquement après avoir en attente [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] événements ont été traités.  
  
 ![Illustration de la file d’attente Dispatcher](../../../../docs/framework/wpf/advanced/media/threadingdispatcherqueue.PNG "ThreadingDispatcherQueue")  
  
 [!INCLUDE[TLA#tla_word](../../../../includes/tlasharptla-word-md.md)]passe le correcteur orthographique à l’aide de ce mécanisme. La correction orthographique est effectuée en arrière-plan à l’aide de la durée d’inactivité de le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread. Examinons le code.  
  
 L’exemple suivant montre le code XAML qui crée l’interface utilisateur.  
  
 [!code-xml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]  
  
 L’exemple suivant montre le code-behind.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]  
  
 L’exemple suivant montre le Gestionnaire d’événements pour le <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]  
  
 Outre la mise à jour le texte sur le <xref:System.Windows.Controls.Button>, ce gestionnaire est chargé de planifier le premier nombre premier en ajoutant un délégué pour le <xref:System.Windows.Threading.Dispatcher> file d’attente. Après que ce gestionnaire d’événements a terminé son travail, le <xref:System.Windows.Threading.Dispatcher> sélectionne ce délégué pour l’exécution.  
  
 Comme nous l’avons mentionné précédemment, <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> est la <xref:System.Windows.Threading.Dispatcher> membre utilisé pour planifier un délégué pour l’exécution. Dans ce cas, nous choisissons le <xref:System.Windows.Threading.DispatcherPriority> priorité. Le <xref:System.Windows.Threading.Dispatcher> exécutera ce délégué uniquement s’il n’y a aucuns événements importants à traiter.                          [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]temps de réponse est plus importante que le contrôle de nombre. Nous passons également un nouveau délégué qui représente la routine de contrôle de nombre.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]  
  
 Cette méthode vérifie si le nombre impair suivant est un nombre premier. S’il est le premier, la méthode met à jour directement les `bigPrime` <xref:System.Windows.Controls.TextBlock> pour refléter sa découverte. Pour ce faire, car le calcul se produit dans le même thread que celui ayant servi à créer le composant. Si nous avions choisi d’utiliser un thread séparé pour le calcul, nous devrions utilisent un mécanisme de synchronisation plus compliqué et exécuter la mise à jour dans le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread. Nous illustrerons ensuite cette situation.  
  
 Pour le code source complet pour cet exemple, consultez la [Single-Threaded Application avec Long-Running Calculation Sample](http://go.microsoft.com/fwlink/?LinkID=160038)  
  
<a name="weather_sim"></a>   
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>Gestion d’une opération bloquante avec un Thread d’arrière-plan  
 La gestion des opérations de blocage dans une application graphique peuvent être difficile. Nous ne voulons pas appeler des méthodes bloquantes de gestionnaires d’événements, car l’application apparaîtra figée. Nous pouvons utiliser un thread séparé pour gérer ces opérations, mais lorsque nous avons terminé, nous devons effectuer une synchronisation avec la [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de threads, car nous ne pouvons pas modifier directement le [!INCLUDE[TLA2#tla_gui](../../../../includes/tla2sharptla-gui-md.md)] de notre thread de travail. Nous pouvons utiliser <xref:System.Windows.Threading.Dispatcher.Invoke%2A> ou <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> pour insérer des délégués dans le <xref:System.Windows.Threading.Dispatcher> de la [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread. Finalement, ces délégués seront exécutés avec l’autorisation de modifier [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] éléments.  
  
 Dans cet exemple, nous imiter un appel de procédure distante qui Récupère une prévision météorologique. Nous utilisons un thread de travail distinct pour exécuter cet appel, et nous planifions une méthode de mise à jour dans le <xref:System.Windows.Threading.Dispatcher> de la [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread lorsque nous avons fini.  
  
 ![Capture d’écran de l’interface utilisateur de Weather](../../../../docs/framework/wpf/advanced/media/threadingweatheruiscreenshot.png "ThreadingWeatherUIScreenShot")  
  
 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]  
  
 Voici quelques-uns des détails à noter.  
  
-   Création du Gestionnaire de bouton  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]  
  
 Lorsque le bouton est cliqué, nous afficher le dessin d’horloge et commençons à l’animer. Nous désactivons le bouton. Nous appelons la `FetchWeatherFromServer` méthode dans un nouveau thread, puis nous retour, ce qui permet la <xref:System.Windows.Threading.Dispatcher> pour traiter des événements pendant que nous attendons pour recueillir la prévision météorologique.  
  
-   Extraction du temps  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]  
  
 Pour simplifier les choses, nous n’avez pas réellement de code de mise en réseau dans cet exemple. Au lieu de cela, nous simuler le délai d’accès réseau en plaçant notre nouveau thread en veille pendant quatre secondes. Pendant ce temps, l’original [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread est toujours en cours d’exécution et répond aux événements. Pour illustrer, que nous avons laissé une animation en cours d’exécution et la réduction et optimiser les boutons également continuent à travailler.  
  
 Lorsque le délai est terminé et que nous avons aléatoirement sélectionné nos prévisions météorologiques, il est temps pour notifier à le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread. Pour cela, nous planifions un appel à `UpdateUserInterface` dans les [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de threads à l’aide de ce thread <xref:System.Windows.Threading.Dispatcher>. Nous passons une chaîne décrivant la météo à cet appel de méthode planifié.  
  
-   Mise à jour le[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]  
  
 Lors de la <xref:System.Windows.Threading.Dispatcher> dans les [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread ait le temps, il exécute l’appel planifié pour `UpdateUserInterface`. Cette méthode arrête l’animation d’horloge et choisit une image pour décrire le temps. Il affiche cette image et restaure le bouton « d’extraction de prévisions ».  
  
<a name="multi_browser"></a>   
### <a name="multiple-windows-multiple-threads"></a>Plusieurs fenêtres, plusieurs Threads  
 Certains [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications requièrent plusieurs fenêtres de niveau supérieur. Il est parfaitement acceptable pour un Thread / <xref:System.Windows.Threading.Dispatcher> combinaison de gérer plusieurs fenêtres, mais parfois, plusieurs threads préférables. Cela est particulièrement vrai que si il y a un risque que l’une des fenêtres de monopoliser le thread.  
  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]Explorer fonctionne de cette manière. Chaque nouvelle fenêtre d’Explorateur appartient au processus d’origine, mais il est créé sous le contrôle d’un thread indépendant.  
  
 En utilisant un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Frame> contrôle, nous pouvons afficher des pages Web. Nous pouvons facilement créer un simple [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] remplacer. Nous allons commencer avec une fonctionnalité importante : la possibilité d’ouvrir une nouvelle fenêtre d’Explorateur. Lorsque l’utilisateur clique sur « nouvelle fenêtre » bouton, nous lançons une copie de notre fenêtre dans un thread séparé. De cette façon, les opérations longues ou blocages dans Windows ne verrouilleront toutes les autres fenêtres.  
  
 En réalité, le modèle de navigateur Web a son propre modèle de thread complexe. Nous l’avons choisi car il doit être familier à la plupart des lecteurs.  
  
 L’exemple suivant montre le code.  
  
 [!code-xml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]  
  
 Les segments de threads suivants de ce code sont les plus intéressants pour nous dans ce contexte :  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]  
  
 Cette méthode est appelée lorsque la « nouvelle fenêtre » du bouton. Il crée un nouveau thread et démarre de façon asynchrone.  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]  
  
 Cette méthode est le point de départ pour le nouveau thread. Nous créons une nouvelle fenêtre sous le contrôle de ce thread.                          [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]crée automatiquement un nouveau <xref:System.Windows.Threading.Dispatcher> pour gérer le nouveau thread. Il nous suffit pour rendre la fenêtre fonctionnelle consiste à démarrer la <xref:System.Windows.Threading.Dispatcher>.  
  
<a name="stumbling_points"></a>   
## <a name="technical-details-and-stumbling-points"></a>Détails techniques et Points d’entrave  
  
### <a name="writing-components-using-threading"></a>Écriture de composants à l’aide de threads  
 Le [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] Guide du développeur décrit un modèle expliquant comment un composant peut exposer un comportement asynchrone à ses clients (voir [Event-based Asynchronous Pattern Overview](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)). Par exemple, supposons que nous souhaitions empaqueter la `FetchWeatherFromServer` méthode dans un composant réutilisable non graphique. La norme [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] modèle, cela se présenterait comme suit.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]  
  
 `GetWeatherAsync`utiliserait l’une des techniques décrites précédemment, telles que la création d’un thread d’arrière-plan, faire le travail de façon asynchrone, ne bloque ne pas le thread appelant.  
  
 Une des parties plus importantes de ce modèle appelle le *MethodName* `Completed` méthode sur le même thread qui a appelé le *MethodName* `Async` méthode commence par. Vous pouvez le faire à l’aide de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assez facilement, en stockant <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>, mais ensuite le composant non graphique pourrait uniquement être utilisé dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, pas dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] programmes.  
  
 Le <xref:System.Windows.Threading.DispatcherSynchronizationContext> classe répond à ce besoin, considérez-le comme une version simplifiée de <xref:System.Windows.Threading.Dispatcher> qui fonctionne avec d’autres [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] frameworks.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]  
  
### <a name="nested-pumping"></a>Pompage imbriqué  
 Parfois, il n’est pas complètement verrouiller le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread. Prenons l’exemple du <xref:System.Windows.MessageBox.Show%2A> procédé de la <xref:System.Windows.MessageBox> classe.                          <xref:System.Windows.MessageBox.Show%2A> ne retourne pas jusqu'à ce que l’utilisateur clique sur le bouton OK. Toutefois, il crée une fenêtre qui doit avoir une boucle de messages pour être interactive. Pendant que nous attendons que l’utilisateur clique sur OK, la fenêtre d’application d’origine ne répond pas aux entrées d’utilisateur. Il est le cas, toutefois, continuer à traiter les messages de peinture. La fenêtre d’origine se redessine lors couverte et révélée.  
  
 ![MessageBox avec bouton « OK »](../../../../docs/framework/wpf/advanced/media/threadingnestedpumping.png "ThreadingNestedPumping")  
  
 Un thread doit être responsable de la fenêtre de message.                          [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Impossible de créer un thread uniquement pour la fenêtre de message, mais ce thread ne pourra pas peindre les éléments désactivés dans la fenêtre d’origine (n’oubliez pas de la discussion précédente de l’exclusion mutuelle). Au lieu de cela, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise un système de traitement de message imbriqué. Le <xref:System.Windows.Threading.Dispatcher> classe inclut une méthode spéciale appelée <xref:System.Windows.Threading.Dispatcher.PushFrame%2A>, qui stocke les point d’exécution actuel d’une application puis commence une nouvelle boucle de message. Lorsque la boucle de messages imbriquée terminée, l’exécution reprend après l’original <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> appeler.  
  
 Dans ce cas, <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> maintient le contexte du programme dans un appel à <xref:System.Windows.MessageBox>.                         <xref:System.Windows.MessageBox.Show%2A>, et il commence une nouvelle boucle de message pour repeindre la fenêtre d’arrière-plan et gérer l’entrée dans la fenêtre de message. Lorsque l’utilisateur clique sur OK et efface la fenêtre indépendante, la boucle imbriquée prend fin et le contrôle reprend après l’appel à <xref:System.Windows.MessageBox.Show%2A>.  
  
### <a name="stale-routed-events"></a>Événements routés périmés  
 Le système d’événement routé dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] notifie des arborescences entières lorsque les événements sont déclenchés.  
  
 [!code-xml[InputOvw#ThreadingArticleStaticRoutedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]  
  
 Lorsque le bouton gauche de la souris sur l’ellipse, `handler2` est exécutée. Après avoir `handler2` se termine, l’événement est passé à la <xref:System.Windows.Controls.Canvas> object, qui utilise `handler1` pour le traiter. Cela se produit uniquement si `handler2` ne sont pas explicitement marque l’objet d’événement comme étant géré.  
  
 Il est possible que `handler2` prendra beaucoup de temps à traiter cet événement.                          `handler2`peut utiliser <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> pour commencer une boucle de message imbriquée qui ne retourne pas des heures. Si `handler2` ne marque pas l’événement comme géré lorsque cette boucle de message est terminer, l’événement est passé dans l’arborescence, même s’il est très ancien.  
  
### <a name="reentrancy-and-locking"></a>Réentrance et verrouillage  
 Le mécanisme de verrouillage de la [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] ne se comporte exactement comme l’imaginer ; il y paraît cesse complètement l’opération lors de la demande un verrou d’un thread. En réalité, le thread continue à recevoir et traiter les messages de priorité élevée. Cela permet d’empêcher les blocages et rendre des interfaces moins réactives, mais introduit la possibilité de bogues subtils.  La plupart du temps, vous n’avez pas besoin de connaître quoi que ce soit à ce sujet, mais dans de rares circonstances (impliquant généralement [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] messages de fenêtre ou des composants COM STA) cela peut s’avérer utile.  
  
 La plupart des interfaces ne sont pas générés avec la sécurité des threads à l’esprit, car les développeurs partent du principe qu’un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] n’est jamais accessible par plusieurs threads. Dans ce cas, ce thread unique peut apporter des modifications environnementales à des moments inattendus, provoquant des effets négatifs que le <xref:System.Windows.Threading.DispatcherObject> mécanisme d’exclusion mutuelle est supposé pour résoudre. Considérez le pseudo-code suivant :  
  
 ![Diagramme de réentrance des threads](../../../../docs/framework/wpf/advanced/media/threadingreentrancy.png "ThreadingReentrancy")  
  
 La plupart du temps, c’est l’attitude, mais parfois dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] où ce type de réentrance inattendue risque des problèmes. C’est le cas, à certains moments clés, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] appelle <xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A>, qui modifie l’instruction de verrouillage pour ce thread afin d’utiliser le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] verrou exempt de réentrance, au lieu de classiques [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] verrou.  
  
 Alors, pourquoi avez-vous le [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] équipe choisi ce comportement ? Il devait faire avec les objets COM STA et au thread de finalisation. Lorsqu’un objet par le garbage collecté, sa `Finalize` méthode est exécutée sur le thread finaliseur dédié, pas le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread. Et isoler le problème, comme un objet COM STA qui a été créé sur le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread ne peut être supprimé sur le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread. Le [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] fait l’équivalent d’une <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (dans ce cas à l’aide de Win32 `SendMessage`). Cependant, si le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread est occupé, le thread finaliseur est bloqué et l’objet COM STA ne peut pas être supprimé, ce qui crée une fuite de mémoire graves. Par conséquent, le [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] équipe pris la décision difficile pour rendre les verrous travailler comme ils font.  
  
 La tâche pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] consiste à éviter la réentrance inattendue sans réintroduire la fuite de mémoire, c’est pourquoi nous ne bloquons pas la réentrance partout.  
  
## <a name="see-also"></a>Voir aussi  
 [Application monothread avec exemple de calcul longue](http://go.microsoft.com/fwlink/?LinkID=160038)