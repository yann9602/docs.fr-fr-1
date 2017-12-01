---
title: "Opérations verrouillées"
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
- Interlocked class, about Interlocked class
- threading [.NET Framework], Interlocked class
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 122058b7e826e27fe6c60c5b07610f7c63e64f78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="interlocked-operations"></a>Opérations verrouillées
La <xref:System.Threading.Interlocked> classe fournit des méthodes qui synchronisent l’accès à une variable qui est partagée par plusieurs threads. Les threads de processus différents peuvent utiliser ce mécanisme si la variable se trouve dans la mémoire partagée. Les opérations verrouillées sont atomiques, autrement dit, l’opération entière est une unité qui ne peut pas être interrompue par une opération verrouillée sur la même variable. Cela est important dans les systèmes d’exploitation multithreading préemptifs, où un thread peut être suspendu après le chargement d’une valeur à partir d’une adresse de mémoire, mais avant d’avoir la possibilité de la modifier et de la stocker.  
  
 La <xref:System.Threading.Interlocked> classe fournit les opérations suivantes :  
  
-   Dans le .NET Framework version 2.0, le <xref:System.Threading.Interlocked.Add%2A> méthode ajoute une valeur entière à une variable et retourne la nouvelle valeur de la variable.  
  
-   Dans le .NET Framework version 2.0, le <xref:System.Threading.Interlocked.Read%2A> méthode lit un entier 64 bits comme une opération atomique. Cela est utile sur les systèmes d’exploitation 32 bits, où la lecture d’un entier 64 bits n’est en général pas une opération atomique.  
  
-   Le <xref:System.Threading.Interlocked.Increment%2A> et <xref:System.Threading.Interlocked.Decrement%2A> méthodes incrémenter ou décrémenter une variable et retourne la valeur résultante.  
  
-   Le <xref:System.Threading.Interlocked.Exchange%2A> méthode effectue un échange atomique de la valeur dans une variable spécifiée, en retournant cette valeur et les remplace par une nouvelle valeur. Dans .NET Framework version 2.0, une surcharge générique de cette méthode peut être utilisée pour exécuter cet échange sur une variable de tout type de référence. Consultez <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>.  
  
-   Le <xref:System.Threading.Interlocked.CompareExchange%2A> méthode échange également deux valeurs, mais dépend du résultat d’une comparaison. Dans .NET Framework version 2.0, une surcharge générique de cette méthode peut être utilisée pour exécuter cet échange sur une variable de tout type de référence. Consultez <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>.  
  
 Sur les processeurs modernes, les méthodes de la <xref:System.Threading.Interlocked> classe peut souvent être implémentée par une seule instruction. Par conséquent, elles fournissent d’excellentes performances de synchronisation et peuvent être utilisées pour générer des mécanismes de synchronisation de niveau supérieur, comme des verrous de rotation.  
  
 Pour obtenir un exemple qui utilise le <xref:System.Threading.Monitor> et <xref:System.Threading.Interlocked> classes de combinaison, voir [analyses](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
## <a name="compareexchange-example"></a>Exemple de CompareExchange  
 Le <xref:System.Threading.Interlocked.CompareExchange%2A> méthode peut être utilisée pour protéger des calculs plus complexes que de simples incréments et décréments. L’exemple suivant montre une méthode thread-safe qui s’ajoute à un total d’exécution stocké comme nombre à virgule flottante. (Pour les entiers, le <xref:System.Threading.Interlocked.Add%2A> (méthode) est une solution plus simple.) Pour des exemples de code complet, consultez les surcharges de <xref:System.Threading.Interlocked.CompareExchange%2A> qui accepte les arguments à virgule flottante simple précision et double précision (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> et <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a>Surcharges non typées d’Exchange et de CompareExchange  
 Le <xref:System.Threading.Interlocked.Exchange%2A> et <xref:System.Threading.Interlocked.CompareExchange%2A> méthodes ont des surcharges qui acceptent des arguments de type <xref:System.Object>. Le premier argument de chacune de ces surcharges est `ref Object` (`ByRef … As Object` en Visual Basic), et la sécurité de type requiert la variable passée à cet argument afin d’être de type strictement <xref:System.Object>; vous ne peut pas caster simplement le premier argument de type <xref:System.Object> Lorsque vous appelez ces méthodes.  
  
> [!NOTE]
>  Dans le .NET Framework version 2.0, utilisez les surcharges génériques de la <xref:System.Threading.Interlocked.Exchange%2A> et <xref:System.Threading.Interlocked.CompareExchange%2A> variables de méthodes pour échanger fortement typées.  
  
 L’exemple de code suivant montre une propriété de type `ClassA` qui peut être définie une seule fois, dans la mesure où elle pourrait être implémentée dans .NET Framework version 1.0 ou 1.1.  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.Monitor>  
 [Thread](../../../docs/standard/threading/index.md)  
 [Fonctionnalités et objets de threading](../../../docs/standard/threading/threading-objects-and-features.md)
