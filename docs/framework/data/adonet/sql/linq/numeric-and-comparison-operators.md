---
title: "Opérateurs de comparaison et opérateurs numériques"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0b89555bc71d95291c096d2e694c315720cfb41c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="numeric-and-comparison-operators"></a>Opérateurs de comparaison et opérateurs numériques
Les opérateurs arithmétiques et de comparaison fonctionnent conformément aux attentes dans le Common Language Runtime (CLR), à l'exception des points suivants :  
  
-   SQL ne prend pas en charge l'opérateur modulo sur les nombres à virgule flottante.  
  
-   SQL ne prend pas en charge l'arithmétique non contrôlée.  
  
-   Les opérateurs d'incrémentation et de décrémentation ne sont pas pris en charge car ils présentent des effets secondaires lorsqu'ils sont utilisés dans des expressions qui ne peuvent pas être répliquées dans SQL.  
  
## <a name="supported-operators"></a>Opérateurs pris en charge  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prend en charge les opérateurs suivants.  
  
-   Opérateurs arithmétiques de base :  
  
    -   `+`  
  
    -   `-` (soustraction)  
  
    -   `*`  
  
    -   `/`  
  
    -   Division d'entier Visual Basic (`\`)  
  
    -   `%` (`Mod` Visual Basic)  
  
    -   `<<`  
  
    -   `>>`  
  
    -   `-` (négation unaire)  
  
-   Opérateurs de comparaison de base :  
  
    -   `=` Visual Basic et `==` C#  
  
    -   `<>` Visual Basic et `!=` C#  
  
    -   Visual Basic `Is/IsNot`  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et types de données](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [Opérateurs C#](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [Opérateurs](../../../../../visual-basic/language-reference/operators/index.md)
