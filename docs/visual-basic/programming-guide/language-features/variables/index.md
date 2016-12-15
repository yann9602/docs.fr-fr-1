---
title: "Variables in Visual Basic | Microsoft Docs"
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
  - "variables [Visual Basic]"
  - "values [Visual Basic], storing"
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Variables in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Il est souvent nécessaire de stocker des valeurs lors de l'exécution de calculs avec [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  Par exemple, vous pouvez être amené à calculer plusieurs valeurs, à les comparer et à exécuter différentes opérations sur ces valeurs, en fonction du résultat de la comparaison.  Vous devez conserver les valeurs si vous souhaitez les comparer.  
  
## Utilisation  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], comme la plupart des langages de programmation, utilise des variables pour le stockage des valeurs.  Une *variable* a un nom \(le mot que vous utilisez pour faire référence à la valeur que la variable contient\).  Une variable a également un type de données \(lequel détermine le type des données que la variable peut stocker\).  Une variable peut représenter un tableau si elle doit stocker un ensemble indexé d'éléments de données étroitement liés.  
  
 L'inférence de type de variable locale vous permet de déclarer des variables sans déclarer explicitement un type de données.  À la place, le compilateur déduit le type de la variable à partir du type de l'expression d'initialisation.  Pour plus d'informations, consultez [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) et [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## Assignation de valeurs  
 Vous devez utiliser les instructions d'assignation pour effectuer des calculs et assigner le résultat à une variable, comme indiqué dans l'exemple suivant :  
  
 [!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]  
  
> [!NOTE]
>  Dans cet exemple, le signe égal \(`=`\) représente un opérateur d'assignation, et non un opérateur d'égalité.  La valeur est assignée à la variable `applesSold`.  
  
 Pour plus d'informations, consultez [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).  
  
## Variables et propriétés  
 si l'élément appartient à cette vue de collection ; sinon, .  Toutefois, elle est plus complexe qu'une variable.  Une propriété utilise des blocs de code qui contrôlent la définition et la récupération de sa valeur.  Pour plus d'informations, consultez [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).  
  
## Voir aussi  
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Dépannage des variables](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)   
 [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)