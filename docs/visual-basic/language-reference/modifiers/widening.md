---
title: "Widening (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.widening"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "conversions, type"
  - "type conversion"
  - "conversions, data type"
  - "Widening keyword"
  - "data type conversion"
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Widening (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Indique qu'un opérateur de conversion \(`CType`\) convertit une classe ou une structure en un type qui peut contenir toutes les valeurs possibles de la classe ou de la structure d'origine.  
  
## Conversion avec le mot clé Widening  
 La procédure de conversion doit spécifier `Public Shared` en plus de `Widening`.  
  
 Les conversions étendues réussissent toujours au moment de l'exécution et sans jamais aucune perte de données.  Les exemples sont `Single` en `Double`, `Char` en `String` et un type dérivé en un type de base.  Cette dernière conversion est étendue parce que le type dérivé contient tous les membres du type de base et qu'il s'agit, par conséquent, d'une instance du type de base.  
  
 Le code utilisateur ne doit pas utiliser `CType` pour les conversions étendues, même si `Option Strict` est `On`.  
  
 Le mot clé `Widening` peut être utilisé dans le contexte suivant :  
  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 Pour obtenir des définitions des opérateurs de conversion étendue et  restrictive, consultez [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## Voir aussi  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [CType, fonction](../../../visual-basic/language-reference/functions/ctype-function.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)