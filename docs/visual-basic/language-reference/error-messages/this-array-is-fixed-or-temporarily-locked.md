---
title: "Ce tableau est prédéfini ou est temporairement verrouillé (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: adff10d4ae61e45402df64ebaa3baf146371ff9e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>Ce tableau est prédéfini ou est temporairement verrouillé (Visual Basic)
Cette erreur a les causes possibles suivantes :  
  
-   À l’aide de `ReDim` pour modifier le nombre d’éléments d’un tableau de taille fixe.  
  
-   Redimensionnement d’un tableau dynamique au niveau du module, dans lequel un élément a été passé en tant qu’argument à une procédure. Si un élément est passé, le tableau est verrouillé pour empêcher la désallocation de mémoire pour le paramètre de référence dans la procédure.  
  
-   Tentative d’affecter une valeur à un `Variant` variable contenant un tableau, mais la `Variant` est actuellement verrouillé.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Rendez le tableau d’origine dynamique et non fixe en le déclarant avec `ReDim` (si le tableau est déclaré dans une procédure), ou en la déclarant sans spécifier le nombre d’éléments (si le tableau est déclaré au niveau du module.  
  
2.  Déterminer s’il faut vraiment passer l’élément, car il est visible dans toutes les procédures dans le module.  
  
3.  Déterminez ce qui verrouille le `Variant` et y remédier.  
  
## <a name="see-also"></a>Voir aussi  
 [Tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md)
