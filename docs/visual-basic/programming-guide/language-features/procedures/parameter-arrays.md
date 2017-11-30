---
title: "Tableaux de paramètres (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8ca2b5f02ac4fb3eb613488c8a9852eb2aa4ce5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="parameter-arrays-visual-basic"></a>Tableaux de paramètres (Visual Basic)
En règle générale, vous ne pouvez pas appeler une procédure avec plus d’arguments que la déclaration de procédure spécifie. Lorsque vous avez besoin d’un nombre indéfini d’arguments, vous pouvez déclarer un *tableau de paramètres*, ce qui permet d’accepter un tableau de valeurs pour un paramètre d’une procédure. Il est inutile de connaître le nombre d’éléments dans le tableau de paramètres lorsque vous définissez la procédure. La taille du tableau est déterminée individuellement par chaque appel à la procédure.  
  
## <a name="declaring-a-paramarray"></a>Déclaration d’un paramètre ParamArray  
 Vous utilisez la [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) (mot clé) pour désigner un tableau de paramètres dans la liste de paramètres. Les règles suivantes s'appliquent :  
  
-   Une procédure peut définir qu’un seul tableau de paramètres, et il doit être le dernier paramètre dans la définition de procédure.  
  
-   Le tableau de paramètres doit être passé par valeur. Il est conseillé d’inclure explicitement le [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mot clé dans la définition de procédure.  
  
-   Le tableau de paramètres est automatiquement facultatif. Sa valeur par défaut est un tableau unidimensionnel vide du type d’élément du tableau de paramètres.  
  
-   Tous les paramètres précédant le tableau de paramètres doivent être obligatoires. Le tableau de paramètres doit être le seul paramètre facultatif.  
  
## <a name="calling-a-paramarray"></a>Appel d’un ParamArray  
 Lorsque vous appelez une procédure qui définit un tableau de paramètres, vous pouvez fournir l’argument dans l’une des manières suivantes :  
  
-   Aucune valeur, ce qui signifie que vous pouvez omettre le [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument. Dans ce cas, un tableau vide est passé à la procédure. Vous pouvez également passer le [rien](../../../../visual-basic/language-reference/nothing.md) (mot clé), avec le même effet.  
  
-   Une liste d’un nombre arbitraire d’arguments, séparés par des virgules. Le type de données de chaque argument doit être implicitement convertible en le `ParamArray` le type d’élément.  
  
-   Un tableau avec le même type d’élément en tant que type d’élément du tableau de paramètres.  
  
 Dans tous les cas, le code de la procédure traite le tableau de paramètres comme un tableau unidimensionnel avec des éléments du même type de données en tant que le `ParamArray` type de données.  
  
> [!IMPORTANT]
>  Si vous travaillez dans un tableau qui peut être indéfiniment volumineux, il existe un risque de saturer la capacité interne de votre application. Si vous acceptez un tableau de paramètres, vous devez tester la taille du tableau passé le code appelant. Prenez les mesures appropriées si elle est trop grande pour votre application. Pour plus d’informations, consultez [tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit et appelle la fonction `calcSum`. Le `ParamArray` modificateur du paramètre `args` permet à la fonction d’accepter un nombre variable d’arguments.  
  
 [!code-vb[VbVbalrStatements#26](../../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-arrays_1.vb)]  
  
 L’exemple suivant définit une procédure avec un tableau de paramètres et renvoie les valeurs de tous les éléments du tableau passés au tableau de paramètres.  
  
 [!code-vb[VbVbcnProcedures#48](./codesnippet/VisualBasic/parameter-arrays_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#49](./codesnippet/VisualBasic/parameter-arrays_3.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [Procédures](./index.md)  
 [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)  
 [Passage d’un argument par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)  
 [Passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md)  
 [Paramètres facultatifs](./optional-parameters.md)  
 [Surcharge de procédure](./procedure-overloading.md)  
 [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
