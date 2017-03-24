---
title: "Nullable type inference is not supported in this context | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc36629"
  - "bc36629"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36629"
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 5
---
# Nullable type inference is not supported in this context
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Les types valeur et les structures peuvent être déclarés nullables.  
  
```vb#  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 Toutefois, vous ne pouvez pas utiliser la déclaration nullable en association avec l'inférence de type.  Les exemples suivants provoquent cette erreur.  
  
```vb#  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **ID d'erreur :** BC36629  
  
### Pour corriger cette erreur  
  
-   Utilisez une clause `As` pour déclarer la variable nullable.  
  
## Voir aussi  
 [Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)