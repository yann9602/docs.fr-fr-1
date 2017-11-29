---
title: "Les constantes doivent être de type intrinsèque ou énuméré, et non de type classe, structure, paramètre de type ou tableau"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords: BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 702472751810c2d2bd08ece944ef0ffafc2049b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>Les constantes doivent être de type intrinsèque ou énuméré, et non de type classe, structure, paramètre de type ou tableau
Vous avez tenté de déclarer une constante comme une classe, une structure ou un type de tableau, ou comme un paramètre de type défini par un type générique conteneur.  
  
 Les constantes doivent être de type intrinsèque (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, ou `UShort`), ou un `Enum` type basé sur l’un des types intégraux.  
  
 **ID d’erreur :** BC30424  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Déclarez la constante en tant qu’intrinsèque ou `Enum` type.  
  
2.  Une constante peut également être une valeur spéciale, tel que `True`, `False`, ou `Nothing`. Le compilateur considère que ces valeurs prédéfinies sont du type intrinsèque approprié.  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes et énumérations](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [Types de données](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Types de données](../../../visual-basic/language-reference/data-types/data-type-summary.md)
