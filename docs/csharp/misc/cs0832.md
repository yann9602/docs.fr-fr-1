---
title: "Erreur du compilateur CS0832 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0832"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0832"
ms.assetid: b5527209-a9bd-4f8c-a432-2e89bb1905d1
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0832
Une arborescence de l’expression ne peut pas contenir un opérateur d’assignation.  
  
 Une arborescence d’expression ne conserve pas l’état de la variable ou n’a pas de concept d’emplacement de stockage.  
  
### Pour corriger cette erreur  
  
1.  Supprimez l’opérateur d’assignation de l’expression lambda ou de l’expression de requête.  
  
## Exemple  
 Dans l’exemple de code, comme dans toutes les expressions lambda, `x` est simplement un paramètre d’entrée passé par valeur. Vous ne pouvez pas modifier sa valeur dans une arborescence d’expression. Vous pouvez la modifier dans une expression lambda de délégué.  
  
```  
// cs0843.cs using System; using System.Linq; using System.Linq.Expressions; public class C { public static int Main() { Expression<Func<int, int>> e = x => x += 5; // CS0843 return 1; } }  
```