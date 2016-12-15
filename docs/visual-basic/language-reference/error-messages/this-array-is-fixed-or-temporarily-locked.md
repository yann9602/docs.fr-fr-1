---
title: "This array is fixed or temporarily locked (Visual Basic) | Microsoft Docs"
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
  - "vbrID10"
dev_langs: 
  - "VB"
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# This array is fixed or temporarily locked (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les causes de cette erreur peuvent être les suivantes :  
  
-   Utilisation de `ReDim` pour modifier le nombre d'éléments d'un tableau de taille fixe.  
  
-   Redimensionnement d'un tableau dynamique au niveau du module, dans lequel un élément a été passé comme argument à une procédure.  Si un élément est passé, le tableau est verrouillé afin d'empêcher la désallocation de mémoire pour le paramètre de référence dans la procédure.  
  
-   Tentative d'assignation d'une valeur à une variable `Variant` contenant un tableau, alors que la variable `Variant` est actuellement verrouillée.  
  
### Pour corriger cette erreur  
  
1.  Rendez le tableau d'origine dynamique et non fixe en le déclarant avec `ReDim` \(si le tableau est déclaré dans une procédure\) ou sans spécifier le nombre d'éléments \(si le tableau est déclaré au niveau du module\).  
  
2.  Déterminez si vous devez réellement passer l'élément, car il est visible dans toutes les procédures du module.  
  
3.  Déterminez l'élément qui verrouille la variable `Variant` et remédiez au problème.  
  
## Voir aussi  
 [Tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md)