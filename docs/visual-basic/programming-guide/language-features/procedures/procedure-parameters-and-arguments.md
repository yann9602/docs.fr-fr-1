---
title: "Paramètres et arguments d’une procédure (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 726667950cfb227a0359bd6238c202883561749c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a>Paramètres et arguments d’une procédure (Visual Basic)
Dans la plupart des cas, une procédure a besoin des informations sur les circonstances dans lesquelles elle a été appelée. Une procédure qui exécute des tâches répétitives ou partagées utilise des informations différentes pour chaque appel. Ces informations se composent des variables, des constantes et des expressions que vous passez à la procédure lorsque vous appelez.  
  
 A *paramètre* représente une valeur de la procédure que vous devez fournir lorsque vous appelez. Déclaration de la procédure définit ses paramètres.  
  
 Vous pouvez définir une procédure sans paramètres, un seul paramètre, ou plusieurs. La partie de la définition de procédure qui spécifie les paramètres est appelée la *liste de paramètres*.  
  
 Un *argument* représente la valeur que vous fournissez à un paramètre de procédure lorsque vous appelez la procédure. Le code appelant fournit les arguments lorsqu’il appelle la procédure. La partie de l’appel de procédure qui spécifie les arguments est appelée la *liste d’arguments*.  
  
 L’illustration suivante montre le code appelant la procédure `safeSquareRoot` à partir de deux emplacements différents. Le premier appel passe la valeur de la variable `x` (4.0) au paramètre `number`et la valeur de retour dans `root` (2.0) est assignée à la variable `y`. Le deuxième appel passe la valeur de littéral 9.0 à `number`et affecte la valeur de retour (3.0) à la variable `z`.  
  
 ![Diagramme graphique du passage d’argument au paramètre](./media/parametersargue.gif "ParametersArgue")  
Passage d’un argument à un paramètre  
  
 Pour plus d’informations, consultez [les différences entre les paramètres et Arguments](./differences-between-parameters-and-arguments.md).  
  
## <a name="parameter-data-type"></a>Type de données de paramètre  
 Vous définissez un type de données pour un paramètre à l’aide de la `As` clause dans sa déclaration. Par exemple, la fonction suivante accepte une chaîne et un entier.  
  
 [!code-vb[VbVbcnProcedures#32](./codesnippet/VisualBasic/procedure-parameters-and-arguments_1.vb)]  
  
 Si le commutateur de la vérification de type ([Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) est `Off,` le `As` clause est facultative, sauf si un paramètre l’utilise, tous les paramètres doivent l’utiliser. Si la vérification de type est `On`, le `As` clause est requise pour tous les paramètres de procédure.  
  
 Si le code appelant s’attend à fournir un argument avec un type de données différent de celui de son paramètre correspondant, tel que `Byte` à un `String` paramètre, il doit exécuter l’une des opérations suivantes :  
  
-   Fournissez uniquement des arguments avec les types de données qui s’étendent au type de données du paramètre ;  
  
-   Définissez `Option Strict Off` pour autoriser les conversions restrictives implicites ; ou  
  
-   Utilisez un mot clé de conversion pour convertir explicitement le type de données.  
  
### <a name="type-parameters"></a>Paramètres de type  
 A *procédure générique* définit également un ou plusieurs *les paramètres de type* en plus de ses paramètres normaux. Une procédure générique permet au code appelant à passer différents types de données chaque fois qu’il appelle la procédure, il peut adapter les types de données sur les exigences de chaque appel individuel. Consultez [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)  
 [Procédures Sub](./sub-procedures.md)  
 [Procédures Function](./function-procedures.md)  
 [Procédures de propriété](./property-procedures.md)  
 [Procédures d’opérateur](./operator-procedures.md)  
 [Guide pratique : définir un paramètre pour une procédure](./how-to-define-a-parameter-for-a-procedure.md)  
 [Guide pratique : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)  
 [Passage d’un argument par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)  
 [Surcharge de procédure](./procedure-overloading.md)  
 [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
