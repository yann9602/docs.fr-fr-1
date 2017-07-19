---
title: "Creating Threads and Passing Data at Start Time | Microsoft Docs"
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
  - "threading [.NET Framework], creating"
  - "threading [.NET Framework], passing data to threads"
  - "threading [.NET Framework], retrieving data from threads"
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# Creating Threads and Passing Data at Start Time
Lors de la création d'un processus de système d'exploitation, le système d'exploitation injecte un thread pour exécuter du code dans ce processus, y compris tout domaine d'application d'origine.  À partir de là, des domaines d'application peuvent être créés et détruits sans nécessairement créer ou détruire des threads de système d'exploitation.  Si le code en cours d'exécution est du code géré, un objet <xref:System.Threading.Thread> pour le thread s'exécutant dans le domaine d'application en cours peut être obtenu en récupérant la propriété statique <xref:System.Threading.Thread.CurrentThread%2A> de type <xref:System.Threading.Thread>.  Cette rubrique décrit la création de thread et présente des alternatives pour passer des données à la procédure de thread.  
  
## Création d'un thread  
 La création d'un objet <xref:System.Threading.Thread> crée un thread managé.  La classe <xref:System.Threading.Thread> a des constructeurs qui prennent un délégué <xref:System.Threading.ThreadStart> ou un délégué <xref:System.Threading.ParameterizedThreadStart> ; le délégué encapsule la méthode qui est appelée par le nouveau thread lorsque vous appelez la méthode <xref:System.Threading.Thread.Start%2A>.  Plusieurs appels <xref:System.Threading.Thread.Start%2A> entraînent la levée d'une <xref:System.Threading.ThreadStateException>.  
  
 La méthode <xref:System.Threading.Thread.Start%2A> retourne immédiatement, souvent avant que le nouveau thread ait réellement commencé.  Vous pouvez utiliser les propriétés <xref:System.Threading.Thread.ThreadState%2A> et <xref:System.Threading.Thread.IsAlive%2A> pour déterminer l'état du thread à tout moment, mais ces propriétés ne doivent jamais être utilisées pour synchroniser les activités de threads.  
  
> [!NOTE]
>  Une fois qu'un thread est démarré, il est inutile de conserver une référence à l'objet <xref:System.Threading.Thread>.  L'exécution du thread se poursuit jusqu'à ce que la procédure de thread soit terminée.  
  
 L'exemple de code suivant crée deux nouveaux threads pour appeler des méthodes statiques et d'instance sur un autre objet.  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## Passage de données aux threads et récupération de données à partir de threads  
 Dans le .NET Framework version 2.0, le délégué <xref:System.Threading.ParameterizedThreadStart> offre un moyen facile de passer un objet contenant des données à un thread lorsque vous appelez la surcharge de méthode <xref:System.Threading.Thread.Start%2A?displayProperty=fullName>.  Consultez <xref:System.Threading.ParameterizedThreadStart> pour obtenir un exemple de code.  
  
 L'utilisation du délégué <xref:System.Threading.ParameterizedThreadStart> n'est pas une manière sécurisée de passer des données parce que la surcharge de méthode <xref:System.Threading.Thread.Start%2A?displayProperty=fullName> accepte n'importe quel objet.  Une alternative consiste à encapsuler la procédure de thread et les données dans une classe d'assistance et à utiliser le délégué <xref:System.Threading.ThreadStart> pour exécuter la procédure de thread.  Cette technique est montrée dans les deux exemples de code qui suivent.  
  
 Aucun de ces délégués n'a de valeur de retour parce qu'il n'y a pas de place pour retourner les données provenant d'un appel asynchrone.  Pour récupérer les résultats d'une méthode de thread, vous pouvez utiliser une méthode de rappel comme démontré dans le deuxième exemple de code.  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### Récupération de données avec les méthodes de rappel  
 L'exemple suivant illustre une méthode de rappel qui récupère des données d'un thread.  Le constructeur de la classe qui contient les données et la méthode de thread accepte également un délégué représentant la méthode de rappel ; avant la fin de la méthode de thread, il appelle le délégué de rappel.  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## Voir aussi  
 <xref:System.Threading.Thread>   
 <xref:System.Threading.ThreadStart>   
 <xref:System.Threading.ParameterizedThreadStart>   
 <xref:System.Threading.Thread.Start%2A?displayProperty=fullName>   
 [Threading](../../../docs/standard/threading/index.md)   
 [Using Threads and Threading](../../../docs/standard/threading/using-threads-and-threading.md)