---
title: "Comment&#160;: lever explicitement des exceptions | Microsoft Docs"
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
  - "exceptions, lever"
  - "exceptions, try/catch (blocs)"
  - "FileNotFoundException (classe)"
  - "lever des exceptions de manière implicite"
  - "try/catch (blocs)"
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: lever explicitement des exceptions
Vous pouvez lever explicitement une exception à l'aide de l'instruction `throw`.  Vous pouvez aussi lever de nouveau une exception interceptée à l'aide de l'instruction `throw`.  L'ajout d'informations à une exception qui est levée de nouveau pour fournir un complément d'information lors du débogage constitue une bonne pratique de programmation.  
  
 L'exemple de code suivant utilise un bloc try\/catch pour intercepter une exception <xref:System.IO.FileNotFoundException> possible.  Le bloc try est suivi d'un bloc catch qui intercepte <xref:System.IO.FileNotFoundException>et copie un message vers la console si le fichier de données est introuvable.  L'instruction suivante est l'instruction throw qui lève de nouveau <xref:System.IO.FileNotFoundException> et ajoute des informations de texte à l'exception.  
  
## Exemple  
 [!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
 [!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  
  
## Voir aussi  
 [Comment : utiliser le bloc try\/catch pour intercepter des exceptions](../../../docs/standard/exceptions/how-to-use-the-try-catch-block-to-catch-exceptions.md)   
 [Comment : utiliser des exceptions spécifiques dans un bloc catch](../../../docs/standard/exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)   
 [Comment : utiliser des blocs finally](../../../docs/standard/exceptions/how-to-use-finally-blocks.md)   
 [Notions de base de la gestion des exceptions](../../../docs/standard/exceptions/exception-handling-fundamentals.md)