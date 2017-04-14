---
title: "Comment&#160;: utiliser des blocs finally | Microsoft Docs"
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
  - "ArgumentOutOfRangeException (classe)"
  - "exceptions, finally (blocs)"
  - "exceptions, try/catch (blocs)"
  - "finally (blocs)"
  - "try/catch (blocs)"
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: utiliser des blocs finally
Lorsqu'une exception se produit, l'exécution s'arrête et le contrôle passe au gestionnaire d'exceptions le plus proche.  Cela signifie souvent que des lignes de code qui sont normalement toujours appelées ne sont pas exécutées.  Certaines opérations de nettoyage de ressources, telles que la fermeture d'un fichier, doivent toujours être exécutées même si une exception est levée.  Pour ce faire, vous pouvez utiliser un bloc finally.  Un bloc finally est toujours exécuté, avec ou sans condition d'exception.  
  
 L'exemple de code suivant utilise un bloc try\/catch pour intercepter une exception <xref:System.ArgumentOutOfRangeException>.  La méthode `Main` crée deux tableaux et tente de copier l'un dans l'autre.  Cette action génère une **ArgumentOutOfRangeException** et l'erreur est envoyée à la console.  Le bloc finally s'exécute indépendamment du résultat de l'opération de copie.  
  
## Exemple  
 [!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
 [!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
 [!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  
  
## Voir aussi  
 [Comment : utiliser le bloc try\/catch pour intercepter des exceptions](../../../docs/standard/exceptions/how-to-use-the-try-catch-block-to-catch-exceptions.md)   
 [Comment : lever explicitement des exceptions](../../../docs/standard/exceptions/how-to-explicitly-throw-exceptions.md)   
 [Comment : créer des exceptions définies par l'utilisateur](../../../docs/standard/exceptions/how-to-create-user-defined-exceptions.md)   
 [Notions de base de la gestion des exceptions](../../../docs/standard/exceptions/exception-handling-fundamentals.md)