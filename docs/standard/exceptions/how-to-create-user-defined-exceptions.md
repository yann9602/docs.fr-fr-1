---
title: "Comment&#160;: cr&#233;er des exceptions d&#233;finies par l&#39;utilisateur | Microsoft Docs"
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
  - "exceptions, exemples"
  - "exceptions, définies par l'utilisateur"
  - "exceptions définies par l'utilisateur"
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: cr&#233;er des exceptions d&#233;finies par l&#39;utilisateur
Si vous voulez que les utilisateurs puissent établir une distinction par programme entre certains cas d'erreur, vous pouvez créer vos propres exceptions définies par l'utilisateur.  Le .NET Framework fournit une hiérarchie de classes d'exceptions qui sont en fin de compte dérivées de la classe de base <xref:System.Exception>.  Chacune de ces classes définit une exception spécifique, ce qui fait que dans bien des cas vous n'avez qu'à intercepter l'exception.  Vous pouvez également créer vos propres classes d'exceptions par une dérivation à partir de la classe <xref:System.Exception>.  
  
 Lorsque vous créez vos propres exceptions, vous pouvez vous conformer aux bonnes pratiques de programmation en terminant le nom de classe de l'exception définie par l'utilisateur avec le mot « Exception ». Les bonnes pratiques de programmation incitent aussi à implémenter les trois constructeurs communs recommandés, comme le montre l'exemple suivant.  
  
> [!NOTE]
>  Dans les cas où vous utilisez la communication à distance, vous devez vous assurer que les métadonnées pour d'éventuelles exceptions définies par l'utilisateur sont disponibles sur le serveur \(l'appelé\) et le client \(l'objet proxy ou l'appelant\).  Par exemple, le code qui appelle une méthode dans un domaine d'application séparé doit pouvoir trouver l'assembly contenant une exception levée par un appel distant.  Pour plus d'informations, consultez [Meilleure pratiques pour la gestion des exceptions](../../../docs/standard/exceptions/best-practices-for-exceptions.md).  
  
 Dans l'exemple suivant, une nouvelle classe d'exception, `EmployeeListNotFoundException`, est dérivée de <xref:System.Exception>.  Trois constructeurs sont définis dans la classe, chacun utilisant des paramètres différents.  
  
## Exemple  
 [!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
 [!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
 [!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  
  
## Voir aussi  
 [Comment : utiliser le bloc try\/catch pour intercepter des exceptions](../../../docs/standard/exceptions/how-to-use-the-try-catch-block-to-catch-exceptions.md)   
 [Comment : utiliser des exceptions spécifiques dans un bloc catch](../../../docs/standard/exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)   
 [Meilleures pratiques pour les exceptions](../../../docs/standard/exceptions/best-practices-for-exceptions.md)   
 [Notions de base de la gestion des exceptions](../../../docs/standard/exceptions/exception-handling-fundamentals.md)