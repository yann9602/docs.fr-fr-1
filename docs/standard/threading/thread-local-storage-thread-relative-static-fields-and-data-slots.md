---
title: "Thread Local Storage: Thread-Relative Static Fields and Data Slots | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "threading [.NET Framework], local storage"
  - "threading [.NET Framework], thread-relative static fields"
  - "local thread storage"
  - "TLS"
ms.assetid: c633a4dc-a790-4ed1-96b5-f72bd968b284
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# Thread Local Storage: Thread-Relative Static Fields and Data Slots
Vous pouvez utiliser le stockage local des threads managés \(TLS, Thread Local Storage\) pour stocker des données spécifiques à un thread et à un domaine d'application.  Le .NET Framework offre deux moyens d'utiliser le TLS managé : champs statiques relatifs à un thread et emplacements de données.  
  
-   Utilisez des champs statiques relatifs à un thread \(champs `Shared` relatifs à un thread dans Visual Basic\) si vous pouvez anticiper vos besoins précis au moment de la compilation.  Les champs statiques relatifs à un thread fournissent la meilleure performance.  Ils vous offrent également les avantages de la vérification de type au moment de la compilation.  
  
-   Utilisez les emplacements de données lorsque vos spécifications réelles peuvent être découvertes uniquement au moment de l'exécution.  Les emplacements de données sont plus lents et plus maladroits à l'utilisation que les champs statiques relatifs à un thread, et les données sont stockées comme type <xref:System.Object>, ce qui fait que vous devez effectuer un cast au type correct avant utilisation.  
  
 Dans le code C\+\+ non managé, vous utilisez `TlsAlloc` pour allouer dynamiquement des emplacements et `__declspec(thread)` pour déclarer qu'une variable doit être allouée dans le stockage relatif aux threads.  Les champs statiques relatifs à thread et les emplacement de données fournissent la version managée de ce comportement.  
  
 Dans le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], vous pouvez utiliser la classe <xref:System.Threading.ThreadLocal%601?displayProperty=fullName> pour créer des objets locaux thread initialisés tardivement lorsque l'objet est utilisé pour la première fois.  Pour plus d'informations, consultez [Lazy Initialization](../../../docs/framework/performance/lazy-initialization.md).  
  
## Unicité de données dans TLS managé  
 Que vous utilisiez des champs statiques relatifs à un thread ou des emplacements de données, les données dans TLS managé sont uniques à la combinaison de thread et au domaine d'application.  
  
-   Dans un domaine d'application, un thread ne peut pas modifier de données d'un autre thread, même lorsque les deux threads utilisent le même champ ou emplacement.  
  
-   Lorsqu'un thread accède au même champ ou emplacement à partir de plusieurs domaines d'application, une valeur séparée est maintenue dans chaque domaine d'application.  
  
 Par exemple, si un thread définit la valeur d'un champ statique relatif à un thread, accède à un autre domaine d'application, puis récupère la valeur du champ, la valeur récupérée dans le deuxième domaine d'application diffère de la valeur dans le premier domaine d'application.  La définition d'une nouvelle valeur pour le champ dans le deuxième domaine d'application n'affecte pas la valeur du champ dans le premier domaine d'application.  
  
 De la même façon, lorsqu'un thread obtient le même emplacement de données nommé dans deux domaines d'application différents, les données dans le premier domaine d'application restent indépendantes des données dans le deuxième domaine d'application.  
  
## Champs statiques relatifs à un thread  
 Si vous savez que certaines données sont toujours uniques à un thread et combinaison de domaines d'application, appliquez l'attribut <xref:System.ThreadStaticAttribute> au champ statique.  Utilisez le champ comme vous utiliseriez tout autre champ statique.  Les données dans le champ sont uniques à chaque thread qui les utilise.  
  
 Les champs statiques relatifs à un thread fournissent des performances supérieures à celles de l'emplacement des données et offrent l'avantage de la vérification de type au moment de la compilation.  
  
 Sachez que tout code de constructeur de classe s'exécutera sur le premier thread dans le premier contexte qui accède au champ.  Dans tous les autres threads ou contextes dans le même domaine d'application, les champs sont initialisés avec la valeur `null` \(`Nothing` dans Visual Basic\) s'il s'agit de types référence ou avec leur valeur par défaut s'il s'agit de types valeur.  En conséquence, vous ne devriez pas vous reposer sur les constructeurs de classe pour initialiser des champs statiques relatifs à un thread.  Au contraire, évitez d'initialiser les champs statiques relatifs à un thread et supposez qu'ils sont initialisés avec la valeur `null` \(`Nothing`\) ou avec leurs valeurs par défaut.  
  
## Emplacements des données  
 Le .NET Framework fournit des emplacements de données dynamiques spécifiques à une combinaison d'un thread et d'une combinaison application\-domaine.  Il existe deux types d'emplacements de données : les emplacements nommés et les emplacements sans nom.  Les deux sont implémentés en utilisant la structure <xref:System.LocalDataStoreSlot>.  
  
-   Pour créer un emplacement de données nommé, utilisez le <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=fullName> ou la méthode <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=fullName>.  Pour obtenir une référence à un emplacement nommé existant, passez son nom à la méthode <xref:System.Threading.Thread.GetNamedDataSlot%2A>.  
  
-   Pour créer un emplacement de données sans nom, utilisez la méthode <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=fullName>.  
  
 Pour les emplacements nommés et sans nom, utilisez les méthodes <xref:System.Threading.Thread.SetData%2A?displayProperty=fullName> et <xref:System.Threading.Thread.GetData%2A?displayProperty=fullName> pour définir et récupérer les informations dans l'emplacement.  Ce sont des méthodes statiques qui toujours agissent sur les données pour le thread qui les exécute actuellement.  
  
 Les emplacements nommés peuvent être commodes, parce que vous pouvez récupérer l'emplacement lorsque vous en avez besoin en passant son nom à la méthode <xref:System.Threading.Thread.GetNamedDataSlot%2A>, au lieu de maintenir une référence à un emplacement sans nom.  Toutefois, si un autre composant utilise le même nom pour son stockage relatif à un thread et qu'un thread exécute du code à partir de votre composant et de l'autre composant, chaque composant risque d'endommager les données de l'autre. \(Ce scénario suppose que les deux composants s'exécutent dans le même domaine d'application, et qu'ils ne sont pas conçus pour partager les mêmes données.\)  
  
## Voir aussi  
 <xref:System.ContextStaticAttribute>   
 <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=fullName>   
 <xref:System.ThreadStaticAttribute>   
 <xref:System.Runtime.Remoting.Messaging.CallContext>   
 [Threading](../../../docs/standard/threading/index.md)