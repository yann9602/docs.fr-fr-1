---
title: "Utilisation d’objets implémentant IDisposable"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fd78c2f99ca5c8ffe3c753e158ceba3e0c458c5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="using-objects-that-implement-idisposable"></a>Utilisation d’objets implémentant IDisposable

Garbage collector du common language runtime récupère la mémoire utilisée par les objets managés, mais les types qui utilisent les ressources non managées implémentent le <xref:System.IDisposable> interface pour permettre à la mémoire allouée à des ressources non managées à être récupéré. Une fois que vous avez fini d'utiliser un objet qui implémente <xref:System.IDisposable>, vous devez appeler l'implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> de l'objet. Vous pouvez le faire de deux façons :  
  
* Avec l’instruction `using`C# ou l’instruction `Using`Visual Basic.  
  
* En implémentant un bloc `try/finally`.  

## <a name="the-using-statement"></a>Instruction using

L’instruction `using`en C# et l’instruction `Using` en Visual Basic simplifient le code que vous devez écrire pour créer et nettoyer un objet. L’instruction `using` obtient une ou plusieurs ressources, exécute les instructions que vous spécifiez, puis supprime automatiquement l’objet. Toutefois, l’instruction `using` est utile uniquement pour les objets utilisés dans la portée de la méthode dans laquelle elles sont construites.  
  
L'exemple suivant utilise l'instruction `using` pour créer et libérer un objet <xref:System.IO.StreamReader?displayProperty=nameWithType>.  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
Notez que, bien que la classe <xref:System.IO.StreamReader> implémente l'interface <xref:System.IDisposable>, ce qui signifie qu'elle utilise une ressource non managée, l'exemple n'appelle pas explicitement la méthode <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType>. Quand le compilateur C# ou Visual Basic rencontre l’instruction `using`, il émet en langage intermédiaire qui est équivalent au code suivant contenant explicitement un bloc `try/finally`.  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
C# `using` instruction vous permet également d’acquérir plusieurs ressources dans une seule instruction, ce qui revient en interne imbriquée `using` instructions. L'exemple suivant instancie deux objets <xref:System.IO.StreamReader> pour lire le contenu de deux fichiers différents.  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Bloc try/finally

Au lieu d’encapsuler un bloc `try/finally` dans une instruction `using`, vous pouvez choisir d’implémenter le bloc `try/finally` directement. Il peut s'agir de votre style personnel en matière de codage, ou vous pouvez procéder ainsi pour l'une des raisons suivantes :  
  
* Pour insérer un bloc `catch` afin de gérer toutes les exceptions levées dans le bloc `try`. Sinon, toutes les exceptions levées par l’instruction `using` ne sont pas gérées, de même que toutes les exceptions levées dans le bloc `using` si un bloc `try/catch` n’est pas présent.  
  
* Pour instancier un objet qui implémente <xref:System.IDisposable> dont la portée n'est pas locale au bloc dans lequel elle est déclarée.  
  
L’exemple suivant est similaire à l’exemple précédent, sauf qu’elle utilise un `try/catch/finally` bloc pour instancier, utiliser et supprimer un <xref:System.IO.StreamReader> objet et de gérer les exceptions levées par le <xref:System.IO.StreamReader> constructeur et ses <xref:System.IO.StreamReader.ReadToEnd%2A> (méthode). Notez que le code du bloc `finally` vérifie que l'objet qui implémente <xref:System.IDisposable> n'est pas `null` avant d'appeler la méthode <xref:System.IDisposable.Dispose%2A>. La non-exécution de cette opération peut générer une <xref:System.NullReferenceException> au moment de l'exécution.  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
Vous pouvez suivre ce modèle de base si vous choisissez d’implémenter ou devez implémenter un `try/finally` bloquer, car votre langage de programmation ne prend pas en charge un `using` instruction mais autorise les appels directs à la <xref:System.IDisposable.Dispose%2A> (méthode). 
  
## <a name="see-also"></a>Voir aussi

[Nettoyage des ressources non managées](../../../docs/standard/garbage-collection/unmanaged.md)   
[à l’aide de l’instruction (référence c#)](~/docs/csharp/language-reference/keywords/using-statement.md)   
[À l’aide de l’instruction (Visual Basic)](~/docs/visual-basic/language-reference/statements/using-statement.md)
