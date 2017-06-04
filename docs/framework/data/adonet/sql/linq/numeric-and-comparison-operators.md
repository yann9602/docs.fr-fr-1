---
title: "Op&#233;rateurs de comparaison et op&#233;rateurs num&#233;riques | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Op&#233;rateurs de comparaison et op&#233;rateurs num&#233;riques
Les opérateurs arithmétiques et de comparaison fonctionnent conformément aux attentes dans le Common Language Runtime \(CLR\), à l'exception des points suivants :  
  
-   SQL ne prend pas en charge l'opérateur modulo sur les nombres à virgule flottante.  
  
-   SQL ne prend pas en charge l'arithmétique non contrôlée.  
  
-   Les opérateurs d'incrémentation et de décrémentation ne sont pas pris en charge car ils présentent des effets secondaires lorsqu'ils sont utilisés dans des expressions qui ne peuvent pas être répliquées dans SQL.  
  
## Opérateurs pris en charge  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prend en charge les opérateurs suivants.  
  
-   Opérateurs arithmétiques de base :  
  
    -   `+`  
  
    -   `-` \(soustraction\)  
  
    -   `*`  
  
    -   `/`  
  
    -   Division d'entier Visual Basic \(`\`\)  
  
    -   `%` \(`Mod` Visual Basic\)  
  
    -   `<<`  
  
    -   `>>`  
  
    -   `-` \(négation unaire\)  
  
-   Opérateurs de comparaison de base :  
  
    -   `=` Visual Basic et `==` C\#  
  
    -   `<>` Visual Basic et `!=` C\#  
  
    -   Visual Basic `Is/IsNot`  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## Voir aussi  
 [Fonctions et types de données](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)   
 [Opérateurs C\#](../Topic/C%23%20Operators.md)   
 [Operators](../Topic/Operators%20\(Visual%20Basic\).md)