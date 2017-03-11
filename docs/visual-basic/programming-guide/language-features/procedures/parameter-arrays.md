---
title: "Parameter Arrays (Visual Basic) | Microsoft Docs"
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
  - "parameter arrays, about parameter arrays"
  - "ParamArray keyword, parameter arrays"
  - "Visual Basic code, procedures"
  - "parameters, parameter arrays"
  - "arguments [Visual Basic], parameter arrays"
  - "procedures, indefinite number of argument values"
  - "arrays [Visual Basic], parameter arrays"
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
caps.latest.revision: 26
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 26
---
# Parameter Arrays (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

En règle générale, vous ne pouvez pas appeler une procédure avec un nombre d'arguments supérieur à celui de la déclaration de procédure.  Lorsque vous avez besoin d'un nombre indéfini d'arguments, vous pouvez déclarer un *tableau de paramètres*, lequel permet à la procédure d'accepter un tableau de valeurs comme paramètre.  Il n'est pas nécessaire de connaître le nombre d'éléments contenus dans le tableau de paramètres lorsque vous définissez la procédure.  La taille du tableau est déterminée individuellement par chaque appel à la procédure.  
  
## Déclaration d'un ParamArray  
 Vous devez utiliser le mot clé [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) pour désigner un tableau de paramètres dans la liste des paramètres.  Les règles suivantes s'appliquent :  
  
-   Une procédure ne peut définir qu'un tableau de paramètres, qui doit représenter le dernier paramètre dans la définition de la procédure.  
  
-   Le tableau de paramètres doit être passé par valeur.  En programmation, il est conseillé d'inclure explicitement le mot clé [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) dans la définition de la procédure.  
  
-   Le tableau de paramètres est automatiquement facultatif.  Sa valeur par défaut est un tableau unidimensionnel vide dont le type d'élément est tableau de paramètres.  
  
-   Tous les paramètres précédant le tableau de paramètres sont requis.  Le tableau de paramètres doit être le seul paramètre facultatif.  
  
## Appel d'un ParamArray  
 Lorsque vous appelez une procédure qui définit un tableau de paramètres, vous pouvez fournir l'argument de l'une des manières suivantes:  
  
-   Aucune valeur, ce qui signifie que vous pouvez omettre l'argument [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md).  Dans ce cas, un tableau vide est passé à la procédure.  Vous pouvez également passer le mot clé [Nothing](../../../../visual-basic/language-reference/nothing.md), qui produit le même effet.  
  
-   Liste d'un nombre arbitraire d'arguments séparés par des virgules.  Le type de données de chaque argument doit être implicitement convertible en type d'élément `ParamArray`.  
  
-   Tableau avec le même type d'élément que celui du tableau de paramètres.  
  
 Dans tous les cas, le code de la procédure traite le tableau de paramètres comme un tableau unidimensionnel dont chaque élément est du même type de données que le type de données `ParamArray`.  
  
> [!IMPORTANT]
>  Si vous travaillez dans un tableau dont la taille peut être indéfinie, vous risquez de saturer la capacité interne de votre application.  Si vous acceptez un tableau de paramètres, vous devez tester la taille du tableau auquel le code appelant est passé.  Effectuez des étapes appropriées si le tableau est trop grand pour votre application.  Pour plus d'informations, consultez [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## Exemple  
 l'exemple suivant définit et appelle la fonction `calcSum`.  Le modificateur d' `ParamArray` pour le paramètre `args` permet à la fonction d'accepter un nombre variable d'arguments.  
  
 [!code-vb[VbVbalrStatements#26](../../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/parameter-arrays_1.vb)]  
  
 L'exemple suivant définit une procédure avec un tableau de paramètres, et renvoie les valeurs de tous les éléments de tableau passés au tableau de paramètres.  
  
 [!code-vb[VbVbcnProcedures#48](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/parameter-arrays_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#49](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/parameter-arrays_3.vb)]  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>   
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)