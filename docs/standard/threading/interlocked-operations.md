---
title: "Interlocked Operations | Microsoft Docs"
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
  - "Interlocked class, about Interlocked class"
  - "threading [.NET Framework], Interlocked class"
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# Interlocked Operations
La classe <xref:System.Threading.Interlocked> fournit des méthodes qui synchronisent l'accès à une variable qui est partagée par plusieurs threads.  Les threads de processus différents peuvent utiliser ce mécanisme si la variable est en mémoire partagée.  Les opérations verrouillées sont atomiques \- c'est\-à\-dire que l'opération entière est une unité qui ne peut pas être interrompue par une opération verrouillée sur la même variable.  Cela est important dans les systèmes d'exploitation avec un multithread préemptif, où un thread peut être suspendu après le chargement d'une valeur à partir d'une adresse mémoire, mais avant d'avoir l'opportunité de la modifier et de la stocker.  
  
 La classe <xref:System.Threading.Interlocked> fournit les opérations suivantes :  
  
-   Dans le .NET Framework version 2.0, la méthode <xref:System.Threading.Interlocked.Add%2A> ajoute une valeur entière à une variable et retourne la nouvelle valeur de la variable.  
  
-   Dans le .NET Framework version 2.0, la méthode <xref:System.Threading.Interlocked.Read%2A> lit une valeur entière de 64 bits comme une opération atomique.  Cela utile sur les systèmes d'exploitation de 32 bits, où la lecture d'un entier de 64 bits n'est d'ordinaire pas une opération atomique.  
  
-   Les méthodes <xref:System.Threading.Interlocked.Increment%2A> et <xref:System.Threading.Interlocked.Decrement%2A> incrémentent ou décrémentent une variable et retourne la valeur résultante.  
  
-   La méthode <xref:System.Threading.Interlocked.Exchange%2A> exécute un échange atomique de la valeur dans une variable spécifiée, en retournant cette valeur et la remplaçant par une nouvelle valeur.  Dans le .NET Framework version 2.0, une surcharge générique de cette méthode peut être utilisée pour exécuter cet échange sur une variable de tout type référence.  Consultez <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>.  
  
-   La méthode <xref:System.Threading.Interlocked.CompareExchange%2A> échange également deux valeurs, mais dépend du résultat d'une comparaison.  Dans le .NET Framework version 2.0, une surcharge générique de cette méthode peut être utilisée pour exécuter cet échange sur une variable de tout type référence.  Consultez <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>.  
  
 Sur les processeurs modernes, les méthodes de la classe <xref:System.Threading.Interlocked> peuvent souvent être implémentées par une seule instruction.  Ainsi, elles fournissent d'excellentes performances de synchronisation et peuvent s'utiliser pour générer des mécanismes de synchronisation de niveau plus élevé comme les spin locks.  
  
 Pour obtenir un exemple qui utilise les classes <xref:System.Threading.Monitor> et <xref:System.Threading.Interlocked> dans la combinaison, consultez [Moniteurs](../Topic/Monitors.md).  
  
## Exemple CompareExchange  
 La méthode <xref:System.Threading.Interlocked.CompareExchange%2A> peut être utilisée pour protéger des calculs qui sont plus compliqués que de simples incréments et décréments.  L'exemple suivant montre une méthode thread\-safe qui ajoute à un total cumulé stocké comme un nombre à virgule flottante. \(Pour les entiers, la méthode <xref:System.Threading.Interlocked.Add%2A> est une solution plus simple.\) Pour les exemples de code complets, consultez les surcharges de <xref:System.Threading.Interlocked.CompareExchange%2A> qui acceptent des arguments de nombre à virgule flottante simple précision et double précision \(<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> et <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>\).  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## Surcharges non typées d'Exchange et de CompareExchange  
 Les méthodes <xref:System.Threading.Interlocked.Exchange%2A> et <xref:System.Threading.Interlocked.CompareExchange%2A> ont des surcharges qui acceptent des arguments de type <xref:System.Object>.  Le premier argument de chacune de ces surcharges est `ref Object` \(`ByRef … As Object` en Visual Basic\), et la sécurité de type requiert la variable passée à cet argument à taper strictement comme <xref:System.Object> ; vous ne pouvez pas simplement effectuer de cast sur le premier argument à taper <xref:System.Object> lors de l'appel de ces méthodes.  
  
> [!NOTE]
>  Dans le .NET Framework version 2.0, utilisez les surcharges génériques des méthodes <xref:System.Threading.Interlocked.Exchange%2A> et <xref:System.Threading.Interlocked.CompareExchange%2A> pour échanger des variables fortement typées.  
  
 L'exemple de code suivant affiche une propriété de type `ClassA` qui peut être définie uniquement une fois, comme elle peut être implémentée dans la version 1.0 ou 1.1 du .NET Framework.  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## Voir aussi  
 <xref:System.Threading.Interlocked>   
 <xref:System.Threading.Monitor>   
 [Threading](../../../docs/standard/threading/index.md)   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)