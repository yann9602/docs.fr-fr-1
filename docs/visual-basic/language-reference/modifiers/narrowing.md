---
title: "Narrowing (Visual Basic) | Microsoft Docs"
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
  - "vb.narrowing"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "conversions, type"
  - "type conversion"
  - "conversions, data type"
  - "Narrowing keyword"
  - "data type conversion"
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Narrowing (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Indique qu'un opérateur de conversion \(`CType`\) convertit une classe ou structure en un type qui ne pourra peut\-être pas contenir certaines valeurs possibles de la classe d'origine ou structure.  
  
## Conversion avec le mot clé Narrowing  
 La procédure de conversion doit spécifier `Public Shared` en plus de `Narrowing`.  
  
 Les conversions restrictives ne réussissent pas toujours au moment de l'exécution et peuvent échouer ou entraîner la perte de données.  Les exemples sont `Long` en `Integer`, `String` en `Date` et un type de base en un type dérivé.  Cette dernière conversion est restrictive parce que le type de base ne pourra peut\-être pas contenir tous les membres du type dérivé et donc n'est pas une instance du type dérivé.  
  
 Si `Option Strict` est `On`, le code utilisateur doit utiliser `CType` pour toutes les conversions restrictives.  
  
 Le mot clé `Narrowing` peut être utilisé dans le contexte suivant :  
  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## Voir aussi  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [CType, fonction](../../../visual-basic/language-reference/functions/ctype-function.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)