---
title: "Using Objects That Implement IDisposable | Microsoft Docs"
ms.custom: ""
ms.date: "04/07/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Dispose method"
  - "try/finally block"
  - "garbage collection, encapsulating resources"
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Using Objects That Implement IDisposable
Le récupérateur de mémoire du Common Language Runtime libère la mémoire utilisée par les objets non managés, mais les types qui utilisent les ressources non managées implémentent l'interface <xref:System.IDisposable> pour permettre à la mémoire non managée d'être récupérée.  Une fois que vous avez fini d'utiliser un objet qui implémente <xref:System.IDisposable>, vous devez appeler l'implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> de l'objet.  Vous pouvez le faire de deux façons :  
  
-   Avec l'instruction C\# **using** ou l'instruction Visual Basic `Using`.  
  
-   En implémentant un bloc `try`\/`finally`.  
  
## Instruction using  
 L'instruction **using** en C\# et l'instruction `Using` en Visual Basic simplifient le code que vous devez écrire pour créer et nettoyer un objet.  L'instruction **using** obtient une ou plusieurs ressources, exécute les instructions que vous spécifiez, puis supprime automatiquement l'objet.  Toutefois, l'instruction **using** est utile uniquement pour les objets utilisés dans le portée de la méthode dans laquelle elles sont construites.  
  
 L'exemple suivant utilise l'instruction `using` pour créer et libérer un objet <xref:System.IO.StreamReader?displayProperty=fullName>.  
  
 [!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
 [!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
 Notez que, bien que la classe <xref:System.IO.StreamReader> implémente l'interface <xref:System.IDisposable>, ce qui signifie qu'elle utilise une ressource non managée, l'exemple n'appelle pas explicitement la méthode <xref:System.IO.StreamReader.Dispose%2A?displayProperty=fullName>.  Lorsque le compilateur C\# ou Visual Basic rencontre l'instruction `using`, il émet en langage intermédiaire qui est équivalent au code suivant contenant explicitement un bloc `try`\/`finally`.  
  
 [!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
 [!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
 L'instruction **using** en C\# vous permet d'acquérir plusieurs ressources dans une seule instruction, ce qui revient en interne à plusieurs instructions **using** imbriquées.  L'exemple suivant instancie deux objets <xref:System.IO.StreamReader> pour lire le contenu de deux fichiers différents.  
  
 [!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]  
  
## Bloc try\/finally  
 Au lieu d'encapsuler un bloc `try`\/`finally` dans une instruction `using`, vous pouvez choisir d'implémenter le bloc `try`\/`finally` directement.  Il peut s'agir de votre style personnel en matière de codage, ou vous pouvez procéder ainsi pour l'une des raisons suivantes :  
  
-   Pour insérer un bloc `catch` afin de gérer toutes les exceptions levées dans le bloc `try`.  Sinon, toutes les exceptions levées par l'instruction `using` ne sont pas gérées, de même que toutes les exceptions levées dans le bloc `using` si un bloc `try`\/`catch` n'est pas présent.  
  
-   Pour instancier un objet qui implémente <xref:System.IDisposable> dont la portée n'est pas locale au bloc dans lequel elle est déclarée.  
  
 L'exemple suivant est similaire à l'exemple précédent, mais il utilise un bloc `try`\/`catch`\/`finally` pour instancier, utiliser et supprimer un objet <xref:System.IO.StreamReader>, ainsi que pour gérer les exceptions levées par le constructeur <xref:System.IO.StreamReader> et sa méthode <xref:System.IO.StreamReader.ReadToEnd%2A>.  Notez que le code du bloc `finally` vérifie que l'objet qui implémente <xref:System.IDisposable> n'est pas `null` avant d'appeler la méthode <xref:System.IDisposable.Dispose%2A>.  La non\-exécution de cette opération peut générer une <xref:System.NullReferenceException> au moment de l'exécution.  
  
 [!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
 [!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
 Vous pouvez suivre ce modèle de base si vous choisissez d'implémenter \(ou que vous devez implémenter\) un bloc `try`\/`finally`, car votre langage de programmation ne prend pas en charge l'instruction `using` mais autorise les appels directs à la méthode <xref:System.IDisposable.Dispose%2A>.  
  
 Si votre langage ne prend pas en charge les appels directs à la méthode <xref:System.IDisposable.Dispose%2A> \(par exemple, en C\+\+\), vous pouvez généralement utiliser la syntaxe du destructeur de votre langage.  
  
## Voir aussi  
 [Cleaning Up Unmanaged Resources](../../../docs/standard/garbage-collection/unmanaged.md)   
 [using, instruction](../Topic/using%20Statement%20\(C%23%20Reference\).md)   
 [Using Statement](../Topic/Using%20Statement%20\(Visual%20Basic\).md)