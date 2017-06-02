---
title: "Utilisation de gestionnaires filtr&#233;s par l&#39;utilisateur | Microsoft Docs"
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
  - "exceptions, filtrées par l'utilisateur"
  - "exceptions filtrées par l'utilisateur"
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# Utilisation de gestionnaires filtr&#233;s par l&#39;utilisateur
Actuellement, Visual Basic prend en charge les exceptions filtrées par l'utilisateur.  Les gestionnaires d'exceptions filtrés par l'utilisateur interceptent et gèrent les exceptions selon des critères que vous définissez pour l'exception.  Ces gestionnaires utilisent l'instruction **Catch** avec le mot clé **When**.  
  
 Cette technique est utile lorsqu'un objet exception particulier correspond à plusieurs erreurs.  En ce cas, l'objet possède généralement une erreur qui contient un code d'erreur spécifique associé à l'erreur.  Vous pouvez utiliser la propriété du code d'erreur dans l'expression pour sélectionner uniquement l'erreur particulière que vous voulez gérer dans cette clause **Catch**.  
  
 L'exemple Visual Basic suivant illustre l'instruction **Catch\/When**.  
  
```  
Try  
      'Try statements.  
   Catch When Err = VBErr_ClassLoadException  
      'Catch statements.  
End Try  
```  
  
 L'expression de la clause filtrée par l'utilisateur n'est pas limitée.  Si une exception se produit pendant l'exécution de l'expression filtrée par l'utilisateur, cette exception est ignorée et l'expression de filtre a la valeur false.  Dans ce cas, le Common Language Runtime continue de rechercher un gestionnaire pour l'exception actuelle.  
  
## Combinaison de l'exception spécifique et des clauses filtrées par l'utilisateur  
 Une instruction catch peut contenir à la fois l'exception spécifique et les clauses filtrées par l'utilisateur.  Le runtime teste l'exception spécifique en premier.  En cas de succès de l'exception spécifique, le runtime exécute le filtre utilisateur.  Le filtre générique peut contenir une référence à la variable déclarée dans le filtre de la classe.  Notez que l'ordre des deux clauses filtre ne peut pas être inversé.  
  
 L'exemple Visual Basic suivant illustre l'exception spécifique `ClassLoadException` dans l'instruction **Catch** ainsi que la clause filtrée par l'utilisateur à l'aide du mot clé **When**.  
  
```  
Try  
      'Try statements.  
   Catch cle As ClassLoadException When cle.IsRecoverable()  
      'Catch statements.  
End Try  
```  
  
## Voir aussi  
 [Comment : utiliser le bloc try\/catch pour intercepter des exceptions](../../../docs/standard/exceptions/how-to-use-the-try-catch-block-to-catch-exceptions.md)   
 [Comment : utiliser des exceptions spécifiques dans un bloc catch](../../../docs/standard/exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)   
 [Meilleures pratiques pour les exceptions](../../../docs/standard/exceptions/best-practices-for-exceptions.md)   
 [Notions de base de la gestion des exceptions](../../../docs/standard/exceptions/exception-handling-fundamentals.md)