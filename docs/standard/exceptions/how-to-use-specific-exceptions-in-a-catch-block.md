---
title: "Comment&#160;: utiliser des exceptions sp&#233;cifiques dans un bloc catch | Microsoft Docs"
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
  - "catch (blocs)"
  - "exceptions, try/catch (blocs)"
  - "try/catch (blocs)"
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: utiliser des exceptions sp&#233;cifiques dans un bloc catch
Lorsqu'une exception se produit, elle remonte la pile et chaque bloc catch a la possibilité de la traiter.  L'ordre des instructions catch est important.  Placez les blocs catch ciblés pour des exceptions spécifiques avant un bloc catch d'exception général, sinon le compilateur pourrait émettre une erreur.  Le bloc catch approprié est déterminé par la mise en correspondance du type de l'exception et du nom de l'exception spécifié dans le bloc catch.  Si aucun bloc catch spécifique n'existe, l'exception est interceptée par un bloc catch général, le cas échéant.  
  
 L'exemple de code suivant utilise un bloc try\/catch pour intercepter une exception <xref:System.InvalidCastException>.  L'exemple crée une classe appelée `Employee` avec une propriété unique pour le niveau de l'employé \(`Emlevel`\).  Une méthode`, PromoteEmployee`, prend un objet et incrément le niveau de l'employé.  Une exception **InvalidCastException** se produit quand une instance <xref:System.DateTime> est passée à la méthode `PromoteEmployee`.  
  
## Exemple  
 [!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
 [!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
 [!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)]  
  
 Le Common Language Runtime intercepte des exceptions qui ne sont pas interceptées par un bloc catch.  Selon la configuration du runtime, une boîte de dialogue de débogage apparaît ou l'exécution du programme s'arrête et une boîte de dialogue contenant des informations sur les exceptions s'ouvre.  Pour des informations sur le débogage, consultez [Débogage et profilage d'applications](../../../docs/framework/debug-trace-profile/index.md).  
  
## Voir aussi  
 [Comment : utiliser le bloc try\/catch pour intercepter des exceptions](../../../docs/standard/exceptions/how-to-use-the-try-catch-block-to-catch-exceptions.md)   
 [Comment : lever explicitement des exceptions](../../../docs/standard/exceptions/how-to-explicitly-throw-exceptions.md)   
 [Comment : créer des exceptions définies par l'utilisateur](../../../docs/standard/exceptions/how-to-create-user-defined-exceptions.md)   
 [Comment : utiliser des blocs finally](../../../docs/standard/exceptions/how-to-use-finally-blocks.md)   
 [Classe et propriétés d'exception](../../../docs/standard/exceptions/exception-class-and-properties.md)   
 [Notions de base de la gestion des exceptions](../../../docs/standard/exceptions/exception-handling-fundamentals.md)