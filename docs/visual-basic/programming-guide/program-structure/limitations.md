---
title: "Visual Basic Limitations | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "limits"
  - "limitations, Visual Basic"
  - "limitations"
  - "limits, Visual Basic code"
  - "Visual Basic code, limitations"
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Visual Basic Limitations
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les versions précédentes de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] imposaient des limites pour le code, par exemple pour la longueur des noms de variables, le nombre de variables autorisé dans les modules et la taille des modules.  Dans [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)], ces restrictions ont été allégées et vous donnent une plus grande latitude dans l'écriture et l'organisation de votre code.  
  
 Les limites physiques dépendent plus de la mémoire au moment de l'exécution que des aspects pris en compte au moment de la compilation.  Si vous utilisez des applications pratiques de programmation prudentes, et divisez de grandes applications en classes et modules multiples, il y a peu de risque de rencontrer une limitation [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] interne.  
  
 Les éléments suivants constituent quelques limitations que vous pouvez rencontrer dans des cas extrêmes :  
  
-   **Longueur du nom.** Il existe un nombre maximal de caractères pour chaque élément de programmation déclaré.  Ce maximum s'applique à une chaîne de qualification entière si le nom d'élément est qualifié.  Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   **Longueur de ligne.** 65535 caractères au maximum peuvent être utilisés dans une ligne physique de code source.  La ligne du code source logique peut être plus longue si vous utilisez des caractères de continuation de ligne.  Consultez [Procédure : diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
-   **Dimensions du tableau.** Il existe un nombre maximal de dimensions que vous pouvez déclarer pour un tableau.  Cela limite le nombre d'index que vous pouvez utiliser pour spécifier un élément de tableau.  Consultez [Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
-   **Longueur de chaîne.** Il existe un nombre maximal de caractères Unicode que vous pouvez stocker dans une chaîne unique.  Consultez [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
-   **Longueur de chaîne d'environnement.** Il existe 32768 caractères au maximum pour toute chaîne d'environnement utilisée comme un argument de ligne de commande.  Cette limitation existe sur toutes les plateformes.  
  
## Voir aussi  
 [Structure de programme et conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)