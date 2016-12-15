---
title: "Type arguments could not be inferred from the delegate | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36564"
  - "vbc36564"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36564"
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Type arguments could not be inferred from the delegate
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une instruction d'assignation utilise `AddressOf` pour assigner l'adresse d'une procédure générique à un délégué, mais elle ne fournit pas d'arguments de type à la procédure générique.  
  
 En général, lorsque vous appelez un type générique, vous fournissez un argument de type pour chaque paramètre de type défini par le type générique.  Si vous ne fournissez pas d'arguments de type, le compilateur essaie de déduire les types à passer aux paramètres de type.  Si le contexte ne fournit pas assez d'informations pour permettre au compilateur de déduire les types, une erreur est générée.  
  
 **ID d'erreur :** BC36564  
  
### Pour corriger cette erreur  
  
-   Spécifiez les arguments de type de la procédure générique dans l'expression `AddressOf`.  
  
## Voir aussi  
 [Types génériques Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Generic Procedures in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)   
 [Type List](../../../visual-basic/language-reference/statements/type-list.md)   
 [méthodes d'extension.](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)