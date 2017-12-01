---
title: "Création de threads et passage de données au démarrage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61808dc804cc627ab368a5250414dfcc5f54c87e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>Création de threads et passage de données au démarrage
Lorsqu’un processus de système d’exploitation est créé, le système d’exploitation injecte un thread pour exécuter du code dans ce processus, y compris un domaine d’application d’origine. À ce stade, les domaines d’application peuvent être créés et détruits sans aucun thread de système d’exploitation nécessairement créée ou détruite. Si le code en cours d’exécution est géré code, puis un <xref:System.Threading.Thread> de l’objet pour le thread s’exécutant dans le domaine d’application actuel peut être obtenu en récupérant statiques <xref:System.Threading.Thread.CurrentThread%2A> propriété de type <xref:System.Threading.Thread>. Cette rubrique décrit la création de threads et présente des alternatives pour passer des données à la procédure de thread.  
  
## <a name="creating-a-thread"></a>Création d’un Thread  
 Création d’un nouveau <xref:System.Threading.Thread> objet crée un thread managé. Le <xref:System.Threading.Thread> classe a des constructeurs qui acceptent un <xref:System.Threading.ThreadStart> délégué ou un <xref:System.Threading.ParameterizedThreadStart> déléguer ; le délégué encapsule la méthode qui est appelée par le nouveau thread lorsque vous appelez le <xref:System.Threading.Thread.Start%2A> (méthode). Appel de <xref:System.Threading.Thread.Start%2A> plusieurs fois entraîne un <xref:System.Threading.ThreadStateException> levée.  
  
 Le <xref:System.Threading.Thread.Start%2A> méthode retourne immédiatement, souvent avant que le nouveau thread a réellement démarré. Vous pouvez utiliser la <xref:System.Threading.Thread.ThreadState%2A> et <xref:System.Threading.Thread.IsAlive%2A> propriétés afin de déterminer l’état du thread à tout moment, mais ces propriétés ne doivent jamais être utilisé pour synchroniser les activités de threads.  
  
> [!NOTE]
>  Une fois qu’un thread est démarré, il n’est pas nécessaire de conserver une référence à la <xref:System.Threading.Thread> objet. Le thread continue à s’exécuter jusqu'à la fin de la procédure de thread.  
  
 L’exemple de code suivant crée deux nouveaux threads pour appeler des méthodes statiques et instance sur un autre objet.  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads-and-retrieving-data-from-threads"></a>Passer des données à des Threads et la récupération des données à partir de Threads  
 Dans le .NET Framework version 2.0, le <xref:System.Threading.ParameterizedThreadStart> délégué offre un moyen facile de passer un objet contenant les données à un thread lorsque vous appelez le <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> surcharge de méthode. Pour obtenir un exemple de code, consultez <xref:System.Threading.ParameterizedThreadStart>.  
  
 À l’aide de la <xref:System.Threading.ParameterizedThreadStart> délégué n’est pas de type sécurisé permet de passer des données, car le <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> surcharge de méthode accepte tout objet. Une alternative consiste à encapsuler la procédure de thread et les données dans une classe d’assistance et à utiliser le <xref:System.Threading.ThreadStart> délégué à exécuter la procédure de thread. Cette technique est illustrée dans les deux exemples de code qui suivent.  
  
 Aucune de ces délégués a une valeur de retour, car il n’existe pas de place pour retourner les données à partir d’un appel asynchrone. Pour récupérer les résultats d’une méthode de thread, vous pouvez utiliser une méthode de rappel, comme illustré dans le deuxième exemple de code.  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### <a name="retrieving-data-with-callback-methods"></a>La récupération des données avec les méthodes de rappel  
 L’exemple suivant montre une méthode de rappel qui Récupère des données à partir d’un thread. Le constructeur de la classe qui contient les données et la méthode de thread accepte également un délégué qui représente la méthode de rappel ; avant la fin de la méthode de thread, il appelle le délégué de rappel.  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadStart>  
 <xref:System.Threading.ParameterizedThreadStart>  
 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
 [Thread](../../../docs/standard/threading/index.md)  
 [Utilisation des threads et du threading](../../../docs/standard/threading/using-threads-and-threading.md)
