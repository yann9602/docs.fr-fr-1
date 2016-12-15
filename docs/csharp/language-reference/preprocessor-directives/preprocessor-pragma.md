---
title: "#pragma (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#pragma"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#pragma (directive C#)"
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #pragma (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`#pragma` donne des instructions spéciales au compilateur pour la compilation du fichier dans lequel il apparaît.  Les instructions doivent être prises en charge par le compilateur.  En d'autres termes, vous ne pouvez pas utiliser `#pragma` pour créer des instructions de prétraitement personnalisées.  Le compilateur Microsoft C\# prend en charge les deux instructions `#pragma` suivantes :  
  
 [\#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [checksum \#pragma](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## Syntaxe  
  
```  
#pragma pragma-name pragma-arguments  
```  
  
#### Paramètres  
 `pragma-name`  
 Nom d'un pragma reconnu.  
  
 `pragma-arguments`  
 Arguments pragma spécifiques.  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Directives de préprocesseur C\#](../../../csharp/language-reference/preprocessor-directives/index.md)   
 [\#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)   
 [checksum \#pragma](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)