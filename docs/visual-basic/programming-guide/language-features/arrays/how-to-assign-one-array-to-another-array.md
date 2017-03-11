---
title: "How to: Assign One Array to Another Array (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "covariance, arrays"
  - "arrays [Visual Basic], assigning"
  - "arrays [Visual Basic], covariance"
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# How to: Assign One Array to Another Array (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Étant donné que les tableaux sont des objets, ils peuvent être utilisés dans des instructions d'assignation comme les autres types d'objets.  Une variable tableau maintient un pointeur vers les données constituant les éléments de tableau et les informations relatives au rang et à la longueur. Une assignation ne copie que ce pointeur.  
  
### Pour assigner un tableau à un autre tableau  
  
1.  Vérifiez que les deux tableaux ont le même rang \(nombre de dimensions\) et des types de données d'élément compatibles.  
  
2.  Utilisez une instruction d'assignation standard pour assigner le tableau source au tableau de destination.  Ne faites pas suivre les noms du tableau de parenthèses.  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 Les règles suivantes s'appliquent lors de l'assignation d'un tableau à un autre :  
  
-   **Rangs identiques.** Le rang \(nombre de dimensions\) du tableau de destination doit être identique à celui du tableau source.  
  
     Si les rangs des deux tableaux sont identiques, les dimensions n'ont pas besoin de l'être.  Le nombre d'éléments dans une dimension donnée peut varier lors de l'assignation.  
  
-   **Types d'éléments.** Les deux tableaux doivent avoir des éléments de *type référence* ou de *type valeur*.  Pour plus d'informations, consultez [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
    -   Si les deux tableaux ont des éléments de type valeur, les types de données d'élément doivent être exactement identiques.  La seule exception est que vous pouvez assigner un tableau d'éléments `Enum` à un tableau du type de base de `Enum`.  
  
    -   Si les deux tableaux ont des éléments de type référence, le type d'élément source doit dériver du type d'élément de destination.  Si c'est le cas, les deux tableaux ont la même relation d'héritage que leurs éléments.  Cette situation s'appelle la *covariance de tableau*.  
  
 Le compilateur signale une erreur si les règles énoncées ci\-dessus ne sont pas respectées ; par exemple, si les types de données ne sont pas compatibles ou si les rangs ne sont pas identiques.  Vous pouvez ajouter une gestion des erreurs à votre code pour vous assurer que les tableaux sont compatibles avant d'effectuer une assignation.  Vous pouvez également faire appel au mot clé [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) si vous souhaitez éviter de lever une exception.  
  
## Voir aussi  
 [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Troubleshooting Arrays](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)   
 [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)