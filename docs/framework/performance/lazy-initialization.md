---
title: "Lazy Initialization | Microsoft Docs"
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
  - "lazy initialization in .NET, introduction"
ms.assetid: 56b4ae5c-4745-44ff-ad78-ffe4fcde6b9b
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 20
---
# Lazy Initialization
L'*initialisation tardive* d'un objet signifie que sa création est différée jusqu'à sa première utilisation. \(Pour cette rubrique, les termes *initialisation tardive* et *instanciation tardive* sont synonymes.\) L'initialisation tardive est principalement utilisée pour améliorer les performances, éviter les excès de calcul et réduire les exigences en mémoire des programmes.  Voici les scénarios les plus courants :  
  
-   Lorsque vous possédez un objet difficile à créer et que le programme risque de ne pas l'utiliser.  Par exemple, supposez que vous avez en mémoire un objet `Customer` qui possède une propriété `Orders` contenant un grand tableau d'objets `Order` qui, pour être initialisé, requiert une connexion de base de données.  Si l'utilisateur ne demande jamais d'afficher les commandes ou d'utiliser les données dans un calcul, il n'y a aucune raison d'utiliser la mémoire système ou les cycles de calcul pour le créer.  En utilisant `Lazy<Orders>` pour déclarer l'objet `Orders` pour une initialisation tardive, vous pouvez éviter de gaspiller des ressources système lorsque l'objet n'est pas utilisé.  
  
-   Lorsque vous disposez d'un objet difficile à créer et que vous souhaitez différer sa création après la réalisation d'autres opérations complexes.  Par exemple, supposez que votre programme charge plusieurs instances de l'objet lorsqu'il démarre, mais que seules certaines sont requises immédiatement.  Vous pouvez améliorer les performances de démarrage du programme en différant l'initialisation des objets non requis après la création des objets obligatoires.  
  
 Bien que vous puissiez écrire votre propre code pour effectuer l'initialisation tardive, nous vous recommandons d'utiliser plutôt <xref:System.Lazy%601>.  <xref:System.Lazy%601> et ses types associés prennent également en charge la sécurité des threads et fournissent une stratégie cohérente de propagation des exceptions.  
  
 Le tableau suivant répertorie les types que le .NET Framework version 4 fournit pour permettre l'initialisation tardive dans différents scénarios.  
  
|Type|Description|  
|----------|-----------------|  
|<xref:System.Lazy%601>|Classe wrapper qui fournit une sémantique d'initialisation tardive pour toute bibliothèque de classes ou tout type défini par l'utilisateur.|  
|<xref:System.Threading.ThreadLocal%601>|Ressemble à <xref:System.Lazy%601> mais fournit une sémantique d'initialisation tardive sur une base de thread local.  Chaque thread a accès à sa propre valeur unique.|  
|<xref:System.Threading.LazyInitializer>|Fournit des méthodes `static` \(`Shared` en Visual Basic\) avancées pour l'initialisation tardive des objets sans la charge d'une classe.|  
  
## Initialisation tardive de base  
 Pour définir un type initié tardivement, par exemple, `MyType`, utilisez `Lazy<MyType>` \(`Lazy(Of MyType)` en Visual Basic\), comme indiqué dans l'exemple suivant.  Si aucun délégué n'est passé dans le constructeur <xref:System.Lazy%601>, le type inclus dans un wrapper est créé à l'aide de <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> lorsque la propriété de valeur fait l'objet d'un premier accès.  Si le type ne possède pas de constructeur par défaut, une exception runtime est levée.  
  
 Dans l'exemple suivant, supposez que `Orders` est une classe qui contient un tableau d'objets `Order` extraits d'une base de données.  Un objet `Customer` contient une instance de `Orders`, mais les données de l'objet `Orders` peuvent ne pas être requises, en fonction des actions utilisateur.  
  
 [!code-csharp[Lazy#1](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#1)]
 [!code-vb[Lazy#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#1)]  
  
 Vous pouvez également passer un délégué dans le constructeur <xref:System.Lazy%601> qui appelle une surcharge de constructeur spécifique sur le type inclus dans un wrapper au moment de la création, et effectuer toutes les autres étapes d'initialisation requises, comme indiqué dans l'exemple suivant.  
  
 [!code-csharp[Lazy#2](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#2)]
 [!code-vb[Lazy#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#2)]  
  
 Une fois l'objet tardif créé, aucune instance de `Orders` n'est créée jusqu'à ce que la propriété <xref:System.Lazy%601.Value%2A> de la variable tardive ne fasse l'objet d'un premier accès.  Au premier accès, le type inclus dans un wrapper est créé et retourné, puis stocké pour tout accès futur.  
  
 [!code-csharp[Lazy#3](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#3)]
 [!code-vb[Lazy#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#3)]  
  
 Un objet <xref:System.Lazy%601> retourne toujours le même objet \(ou la même valeur\) avec lequel il a été initialisé.  Par conséquent, la propriété <xref:System.Lazy%601.Value%2A> est en lecture seule.  Si <xref:System.Lazy%601.Value%2A> stocke un type référence, vous ne pouvez pas lui assigner de nouvel objet. \(Toutefois, vous pouvez modifier la valeur de ses champs publics et propriétés définissables.\) Si <xref:System.Lazy%601.Value%2A> stocke un type valeur, vous ne pouvez pas modifier sa valeur.  Néanmoins, vous pouvez créer une variable en appelant à nouveau le constructeur de variable à l'aide des nouveaux arguments.  
  
 [!code-csharp[Lazy#4](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#4)]
 [!code-vb[Lazy#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#4)]  
  
 La nouvelle instance tardive, comme celle d'avant, n'instancie pas `Orders` tant que sa propriété <xref:System.Lazy%601.Value%2A> ne fait pas l'objet d'un accès.  
  
### Initialisation thread\-safe  
 Par défaut, les objets <xref:System.Lazy%601> sont thread\-safe.  Autrement dit, si le constructeur ne spécifie pas le type de cohérence de thread, les objets <xref:System.Lazy%601> qu'il crée sont thread\-safe.  Dans les scénarios multithreads, le premier thread qui accède à la propriété <xref:System.Lazy%601.Value%2A> d'un objet <xref:System.Lazy%601> thread\-safe l'initialise pour tous les accès suivants sur tous les threads et tous les threads partagent les mêmes données.  Par conséquent, le thread qui initialise l'objet n'a pas d'importance, et les conditions de concurrence sont bénignes.  
  
> [!NOTE]
>  Vous pouvez étendre cette cohérence aux conditions d'erreur à l'aide de la mise en cache d'exceptions.  Pour plus d'informations, consultez la section, [Exceptions des objets tardifs](../../../docs/framework/performance/lazy-initialization.md#ExceptionsInLazyObjects).  
  
 L'exemple suivant montre que la même instance de `Lazy<int>` a la même valeur pour trois threads séparés.  
  
 [!code-csharp[Lazy#8](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#8)]
 [!code-vb[Lazy#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#8)]  
  
 Si vous avez besoin de données distinctes sur chaque thread, utilisez le type <xref:System.Threading.ThreadLocal%601>, comme décrit ultérieurement dans cette rubrique.  
  
 Certains constructeurs <xref:System.Lazy%601> disposent d'un paramètre booléen nommé `isThreadSafe` utilisé pour indiquer si la propriété <xref:System.Lazy%601.Value%2A> fait l'objet d'accès à partir de plusieurs threads.  Si vous projetez d'accéder à la propriété à partir d'un seul thread, passez `false` de façon à profiter d'un petit avantage en matière de performances.  Si vous prévoyez d'accéder à la propriété à partir de plusieurs threads, passez `true` pour indiquer à l'instance <xref:System.Lazy%601> de gérer correctement les conditions de concurrence dans lesquelles un thread lève une exception au moment de l'initialisation.  
  
 Certains constructeurs <xref:System.Lazy%601> ont un paramètre <xref:System.Threading.LazyThreadSafetyMode> nommé `mode`.  Ces constructeurs fournissent un mode de cohérence de thread supplémentaire.  Le tableau suivant montre la manière dont la cohérence de thread d'un objet <xref:System.Lazy%601> est affectée par les paramètres du constructeur qui spécifient la cohérence de thread.  Chaque constructeur a au maximum un de ces paramètres.  
  
|Cohérence de thread de l'objet|Paramètre `LazyThreadSafetyMode` `mode`|Paramètre `isThreadSafe` booléen|Aucun paramètre de cohérence de thread|  
|------------------------------------|---------------------------------------------|--------------------------------------|--------------------------------------------|  
|Intégralement thread\-safe, un seul thread à la fois tente d'initialiser la valeur.|<xref:System.Threading.LazyThreadSafetyMode>|`true`|Oui.|  
|N'est pas thread\-safe.|<xref:System.Threading.LazyThreadSafetyMode>|`false`|Non applicable.|  
|Intégralement thread\-safe, les threads sont en concurrence pour initialiser la valeur.|<xref:System.Threading.LazyThreadSafetyMode>|Non applicable.|Non applicable.|  
  
 Comme indiqué dans le tableau, spécifier <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> pour le paramètre `mode` revient à spécifier la valeur `true` pour le paramètre `isThreadSafe` et spécifier <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> revient à spécifier la valeur `false`.  
  
 La spécification de <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> permet à plusieurs threads d'essayer d'initialiser l'instance <xref:System.Lazy%601>.  Un seul thread peut gagner cette course et tous les autres threads reçoivent la valeur initialisée par le thread qui a réussi.  Si une exception est levée sur un thread pendant l'initialisation, ce thread ne reçoit pas la valeur définie par le thread qui a réussi.  Les exceptions ne sont pas mises en cache, donc une tentative ultérieure d'accéder à la propriété <xref:System.Lazy%601.Value%2A> peut aboutir à une initialisation réussie.  Cela diffère de la façon dont les exceptions sont traitées dans d'autres modes, ce qui est décrit dans la section suivante.  Pour plus d'informations, consultez l'énumération <xref:System.Threading.LazyThreadSafetyMode>.  
  
<a name="ExceptionsInLazyObjects"></a>   
## Exceptions des objets tardifs  
 Comme indiqué précédemment, un objet <xref:System.Lazy%601> retourne toujours le même objet ou valeur avec lequel il a été initialisé et par conséquent, la propriété <xref:System.Lazy%601.Value%2A> est en lecture seule.  Si vous activez la mise en cache d'exceptions, cette immuabilité s'étend également au comportement des exceptions.  Si un objet initialisé de façon tardive a la mise en cache d'exceptions activée et lève une exception à partir de sa méthode d'initialisation lorsque la propriété <xref:System.Lazy%601.Value%2A> fait l'objet d'un premier accès, cette même exception est levée à chaque tentative suivante d'accès à la propriété <xref:System.Lazy%601.Value%2A>.  En d'autres termes, le constructeur du type inclus dans un wrapper n'est jamais rappelé, même dans des scénarios multithreads.  Par conséquent, l'objet <xref:System.Lazy%601> ne peut pas lever une exception lors d'un accès et retourner une valeur lors d'un accès suivant.  
  
 La mise en cache d'exceptions est activée lorsque vous utilisez un constructeur <xref:System.Lazy%601?displayProperty=fullName> qui accepte une méthode d'initialisation \(paramètre`valueFactory` \) ; par exemple, elle est activée lorsque vous utilisez le constructeur `Lazy(T)(Func(T))`.  Si le constructeur prend également une valeur <xref:System.Threading.LazyThreadSafetyMode> \(paramètre`mode` \), spécifiez <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> ou <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName>.  La spécification d'une méthode d'initialisation active la mise en cache d'exceptions pour ces deux modes.  La méthode d'initialisation peut être très simple.  Par exemple, elle peut appeler le constructeur par défaut pour `T` : `new Lazy<Contents>(() => new Contents(), mode)` dans C\# ou `New Lazy(Of Contents)(Function() New Contents())` dans Visual Basic.  Si vous utilisez un constructeur <xref:System.Lazy%601?displayProperty=fullName> qui ne spécifie pas une méthode d'initialisation, les exceptions qui sont levées par le constructeur par défaut pour `T` ne sont pas mises en cache.  Pour plus d'informations, consultez l'énumération <xref:System.Threading.LazyThreadSafetyMode>.  
  
> [!NOTE]
>  Si vous créez un objet <xref:System.Lazy%601> avec le paramètre de constructeur `isThreadSafe` défini sur `false` ou le paramètre de constructeur `mode` défini sur <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName>, vous devez accéder à l'objet <xref:System.Lazy%601> à partir d'un thread unique ou fournir votre propre synchronisation.  Cela s'applique à tous les aspects de l'objet, y compris la mise en cache d'exceptions.  
  
 Comme indiqué dans la section précédente, les objets <xref:System.Lazy%601> créés en spécifiant <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> traitent les exceptions différemment.  Avec <xref:System.Threading.LazyThreadSafetyMode>, plusieurs threads peuvent entrer en compétition pour initialiser l'instance <xref:System.Lazy%601>.  Dans ce cas, les exceptions ne sont pas mises en cache et les tentatives d'accéder à la propriété <xref:System.Lazy%601.Value%2A> peuvent continuer jusqu'à ce que l'initialisation soit réussie.  
  
 Le tableau suivant résume la façon dont les constructeurs <xref:System.Lazy%601> contrôlent la mise en cache d'exceptions.  
  
|Constructeur|Mode de sécurité des threads|Utilise la méthode d'initialisation|Les exceptions sont mises en cache|  
|------------------|----------------------------------|-----------------------------------------|----------------------------------------|  
|Lazy\(T\)\(\)|\(<xref:> System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?qualifyHint=False&autoUpgrade=True\)|Non|Non|  
|Lazy\(T\)\(Func\(T\)\)|\(<xref:> System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?qualifyHint=False&autoUpgrade=True\)|Oui|Oui|  
|Lazy\(T\)\(Boolean\)|`True` \(<xref:> System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?qualifyHint=False&autoUpgrade=True\) ou `false` \(<xref:> System.Threading.LazyThreadSafetyMode.None?qualifyHint=False&autoUpgrade=True\)|Non|Non|  
|Lazy\(T\)\(Func\(T\), Boolean\)|`True` \(<xref:> System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?qualifyHint=False&autoUpgrade=True\) ou `false` \(<xref:> System.Threading.LazyThreadSafetyMode.None?qualifyHint=False&autoUpgrade=True\)|Oui|Oui|  
|Lazy\(T\)\(LazyThreadSafetyMode\)|Spécifié par l'utilisateur|Non|Non|  
|Lazy\(T\)\(Func\(T\), LazyThreadSafetyMode\)|Spécifié par l'utilisateur|Oui|Non si l'utilisateur spécifie <xref:> System.Threading.LazyThreadSafetyMode.PublicationOnly?qualifyHint=False&autoUpgrade=True ; sinon, oui.|  
  
## Implémentation d'une propriété initialisée tardivement  
 Pour implémenter une propriété publique à l'aide de l'initialisation tardive, définissez le champ de stockage de la propriété en tant que <xref:System.Lazy%601> et retournez la propriété <xref:System.Lazy%601.Value%2A> de l'accesseur `get` de la propriété.  
  
 [!code-csharp[Lazy#5](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#5)]
 [!code-vb[Lazy#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#5)]  
  
 La propriété <xref:System.Lazy%601.Value%2A> est en lecture seule ; par conséquent, la propriété qui l'expose n'a aucun accesseur `set`.  Si vous avez besoin d'une propriété en lecture\/écriture stockée par un objet <xref:System.Lazy%601>, l'accesseur `set` doit créer un objet <xref:System.Lazy%601> et l'assigner au magasin de stockage.  L'accesseur `set` doit créer une expression lambda qui retourne la nouvelle valeur de propriété passée à l'accesseur `set` et passe cette expression lambda au constructeur pour le nouvel objet <xref:System.Lazy%601>.  L'accès suivant de la propriété <xref:System.Lazy%601.Value%2A> provoque l'initialisation du nouveau <xref:System.Lazy%601> et sa propriété <xref:System.Lazy%601.Value%2A> retourne par la suite la nouvelle valeur assignée à la propriété.  La raison de cette disposition complexe est de conserver les protections de multithreading intégrées à <xref:System.Lazy%601>.  Sinon, les accesseurs de propriété devront mettre en cache la première valeur retournée par la propriété <xref:System.Lazy%601.Value%2A> et uniquement modifier la valeur mise en cache et vous devrez écrire votre propre code thread\-safe pour ce faire.  Les performances risquent de ne pas être acceptables à cause des initialisations supplémentaires requises par une propriété en lecture\/écriture stockée par un objet <xref:System.Lazy%601>.  En outre, selon le scénario spécifique, la coordination supplémentaire peut être requise pour éviter des conditions de concurrence entre accesseurs Set et accesseurs Get.  
  
## Initialisation tardive de thread local  
 Dans certains scénarios multithreads, vous pouvez souhaiter donner à chaque thread ses propres données privées.  Ces données sont appelées *données locales de thread*.  Dans le .NET Framework version 3.5 et versions antérieures, vous pouviez appliquer l'attribut `ThreadStatic` à une variable statique pour en faire un thread local.  Cependant, l'utilisation de l'attribut `ThreadStatic` peut générer de petites erreurs.  Par exemple, même des instructions d'initialisation de base entraîneront l'initialisation de la variable uniquement sur le premier thread qui y accède, comme indiqué dans l'exemple suivant.  
  
 [!code-csharp[Lazy#6](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#6)]
 [!code-vb[Lazy#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#6)]  
  
 Sur tous les autres threads, la variable sera initialisée à l'aide de sa valeur par défaut \(zéro\).  Dans le .NET Framework version 4, vous pouvez utiliser le type <xref:System.Threading.ThreadLocal%601?displayProperty=fullName> pour créer une variable de thread locale basée sur une instance, initialisée sur tous les threads par le délégué <xref:System.Action%601> que vous fournissez.  Dans l'exemple suivant, tous les threads qui accèdent à `counter` voient sa valeur de départ définie sur 1.  
  
 [!code-csharp[Lazy#7](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#7)]
 [!code-vb[Lazy#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#7)]  
  
 <xref:System.Threading.ThreadLocal%601> inclut dans un wrapper son objet à peu près de la même façon que <xref:System.Lazy%601>, avec ces différences essentielles :  
  
-   Chaque thread initialise la variable de thread locale à l'aide de ses propres données privées qui ne sont pas accessibles à partir des autres threads.  
  
-   La propriété <xref:System.Threading.ThreadLocal%601.Value%2A?displayProperty=fullName> est en lecture\-écriture et peut être modifiée aussi souvent que nécessaire.  Ceci peut affecter la propagation des exceptions. Par exemple, une opération `get` peut lever une exception, tandis que la suivante peut initialiser la valeur avec succès.  
  
-   Si aucun délégué d'initialisation n'est fourni, <xref:System.Threading.ThreadLocal%601> initialisera son type inclus dans un wrapper à l'aide de la valeur par défaut du type.  À cet égard, <xref:System.Threading.ThreadLocal%601> est cohérent avec l'attribut <xref:System.ThreadStaticAttribute>.  
  
 L'exemple suivant montre que chaque thread qui accède à l'instance `ThreadLocal<int>` obtient sa propre copie unique des données.  
  
 [!code-csharp[Lazy#9](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#9)]
 [!code-vb[Lazy#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#9)]  
  
## Variables de thread locales dans Parallel.For et ForEach  
 Lorsque vous utilisez la méthode <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> ou <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> pour itérer au sein des sources de données en parallèle, vous pouvez utiliser les surcharges avec prise en charge intégrée pour les données de thread locales.  Dans ces méthodes, l'emplacement des threads est obtenu à l'aide de délégués locaux qui créent les données, y accèdent et les nettoient.  Pour plus d’informations, consultez [How to: Write a Parallel.For Loop with Thread\-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) et [How to: Write a Parallel.ForEach Loop with Thread\-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md).  
  
## Utilisation de l'initialisation tardive pour des scénarios de faible charge  
 Dans les scénarios où vous devez initialiser tardivement un grand nombre d'objets, vous pouvez décider que l'inclusion dans un wrapper de chaque objet dans un <xref:System.Lazy%601> requiert trop de mémoire ou trop de ressources de calcul.  Vous pouvez également posséder des exigences strictes à propos de la façon dont l'initialisation tardive est exposée.  Dans les tels cas, vous pouvez utiliser les méthodes `static` `Shared` en Visual Basic\) de la classe <xref:System.Threading.LazyInitializer?displayProperty=fullName> pour initialiser de façon tardive chaque objet sans l'inclure dans un wrapper dans une instance de <xref:System.Lazy%601>.  
  
 Dans l'exemple suivant, supposez que, au lieu d'inclure dans un wrapper un objet `Orders` entier dans un objet <xref:System.Lazy%601>, vous avez des objets `Order` individuels initialisés tardivement uniquement s'ils sont requis.  
  
 [!code-csharp[Lazy#10](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#10)]
 [!code-vb[Lazy#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#10)]  
  
 Dans cet exemple, remarquez que la procédure d'initialisation est appelée sur chaque itération de la boucle.  Dans les scénarios multithreads, le premier thread à appeler la procédure d'initialisation est celui dont la valeur est vue par tous les threads.  Les threads suivants appellent également la procédure d'initialisation, mais leurs résultats ne sont pas utilisés.  Si ce genre de condition de concurrence potentielle n'est pas acceptable, utilisez la surcharge de <xref:System.Threading.LazyInitializer.EnsureInitialized%2A?displayProperty=fullName> qui utilise un argument booléen et un objet de synchronisation.  
  
## Voir aussi  
 [Managed Threading Basics](../../../docs/standard/threading/managed-threading-basics.md)   
 [Threads and Threading](../../../docs/standard/threading/threads-and-threading.md)   
 [Task Parallel Library \(TPL\)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)   
 [How to: Perform Lazy Initialization of Objects](../../../docs/framework/performance/how-to-perform-lazy-initialization-of-objects.md)