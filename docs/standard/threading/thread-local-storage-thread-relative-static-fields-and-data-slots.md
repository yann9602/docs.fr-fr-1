---
title: "Stockage local des threads : champs statiques et emplacements de données relatifs à un thread"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], local storage
- threading [.NET Framework], thread-relative static fields
- local thread storage
- TLS
ms.assetid: c633a4dc-a790-4ed1-96b5-f72bd968b284
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 39dd80d378171563f2aadadaa146278e8a417d32
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a>Stockage local des threads : champs statiques et emplacements de données relatifs à un thread
Vous pouvez utiliser managé stockage local des threads (TLS) pour stocker des données qui est unique dans un domaine d’application et de thread. Le .NET Framework fournit deux façons d’utiliser le TLS managé : emplacements de données et les champs statiques relatifs à un thread.  
  
-   Utilisez les champs statiques relatifs à un thread (relatifs à un thread `Shared` champs en Visual Basic) si vous pouvez anticiper vos besoins précis au moment de la compilation. Les champs statiques relatifs à un thread offrent les meilleures performances. Ils vous fournissent également les avantages de la vérification de type au moment de la compilation.  
  
-   Utilisez les emplacements de données lorsque vos besoins réels peuvent être détectées uniquement au moment de l’exécution. Les emplacements de données sont plus lents et plus difficiles à utiliser que les champs statiques relatifs à un thread et les données sont stockées en tant que type <xref:System.Object>, de sorte que vous devez effectuer un cast en type correct avant de l’utiliser.  
  
 Dans C++ non managé, vous utilisez `TlsAlloc` pour allouer dynamiquement des emplacements et `__declspec(thread)` pour déclarer qu’une variable doit être allouée dans le stockage relatifs à un thread. Emplacements de données et les champs statiques relatifs à un thread fournissent la version managée de ce comportement.  
  
 Dans le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], vous pouvez utiliser la <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> classe pour créer des objets locaux de thread initialisés tardivement lorsque l’objet est tout d’abord consommé. Pour plus d’informations, consultez [Initialisation tardive](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="uniqueness-of-data-in-managed-tls"></a>Unicité des données dans TLS managé  
 Si vous utilisez les champs statiques relatifs à un thread ou des emplacements de données, les données dans TLS managé sont uniques à la combinaison du domaine d’application et de thread.  
  
-   Au sein d’un domaine d’application, un thread ne peut pas modifier les données à partir d’un autre thread, même lorsque les deux threads utilisent le même champ ou un emplacement.  
  
-   Lorsqu’un thread accède au même champ ou emplacement à partir de plusieurs domaines d’application, une valeur séparée est maintenue dans chaque domaine d’application.  
  
 Par exemple, si un thread définit la valeur d’un champ static relatifs à un thread, passe à un autre domaine d’application, puis récupère la valeur du champ, la valeur récupérée dans le deuxième domaine d’application est différente de la valeur dans le premier domaine d’application. Définition d’une nouvelle valeur pour le champ dans le deuxième domaine d’application n’affecte pas la valeur du champ dans le premier domaine d’application.  
  
 De même, lorsqu’un thread obtient le même emplacement de données nommé dans deux domaines d’application différents, les données dans le premier domaine d’application restent indépendantes des données dans le deuxième domaine d’application.  
  
## <a name="thread-relative-static-fields"></a>Champs statiques relatifs à un thread  
 Si vous savez qu’un élément de données est toujours unique à un thread et une combinaison de domaines d’application, appliquez le <xref:System.ThreadStaticAttribute> d’attribut dans le champ statique. Utilisez le champ comme vous utiliseriez tout autre champ statique. Les données dans le champ sont uniques à chaque thread qui l’utilise.  
  
 Les champs statiques relatifs à un thread offrent de meilleures performances que les emplacements de données et ont l’avantage de la vérification de type au moment de la compilation.  
  
 N’oubliez pas que tout code de constructeur de classe s’exécutera sur le premier thread dans le premier contexte qui accède au champ. Dans tous les autres threads ou contextes dans le même domaine d’application, les champs sont initialisés à `null` (`Nothing` en Visual Basic) si elles sont des types référence ou à leur valeur par défaut les valeurs si elles sont des types valeur. Par conséquent, vous fiez pas à des constructeurs de classe pour initialiser les champs statiques relatifs à un thread. Au lieu de cela, évitez d’initialiser les champs statiques relatifs à un thread et supposez qu’ils sont initialisés à `null` (`Nothing`) ou à leurs valeurs par défaut.  
  
## <a name="data-slots"></a>Emplacements de données  
 Le .NET Framework fournit les emplacements de données dynamiques qui sont uniques à une combinaison de thread et le domaine d’application. Il existe deux types d’emplacements de données : emplacements nommés et les emplacements sans nom. Les deux sont implémentés à l’aide de la <xref:System.LocalDataStoreSlot> structure.  
  
-   Pour créer un emplacement de données, utilisez la <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> ou <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType> (méthode). Pour obtenir une référence à un emplacement nommé existant, passez son nom à la <xref:System.Threading.Thread.GetNamedDataSlot%2A> (méthode).  
  
-   Pour créer un emplacement de données sans nom, utilisez le <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType> (méthode).  
  
 Pour les nommés et sans nom emplacements, utilisez le <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> et <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType> méthodes pour définir et récupérer les informations contenues dans l’emplacement. Il s’agit des méthodes statiques qui agissent toujours sur les données pour le thread qui les exécute actuellement.  
  
 Les emplacements nommés peuvent être pratiques, car vous pouvez récupérer l’emplacement lorsque vous en avez besoin en passant son nom à la <xref:System.Threading.Thread.GetNamedDataSlot%2A> méthode, au lieu de conserver une référence à un emplacement sans nom. Toutefois, si un autre composant utilise le même nom pour son stockage relatifs à un thread et un thread exécute du code à partir de votre composant et l’autre composant, les deux composants peuvent endommager les données de l’autre. (Ce scénario suppose que les deux composants sont exécutent dans le même domaine d’application, et qu’ils ne sont pas conçus pour partager les mêmes données.)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ContextStaticAttribute>  
 <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>  
 <xref:System.ThreadStaticAttribute>  
 <xref:System.Runtime.Remoting.Messaging.CallContext>  
 [Thread](../../../docs/standard/threading/index.md)
