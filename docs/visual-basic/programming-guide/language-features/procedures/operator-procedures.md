---
title: "Procédures d'opérateur (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 865695731dd591b0c48f4416814fa97edf4ea42e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="operator-procedures-visual-basic"></a>Procédures d'opérateur (Visual Basic)
Une procédure d’opérateur est une série de [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] instructions qui définissent le comportement d’un opérateur standard (tel que `*`, `<>`, ou `And`) sur une classe ou une structure que vous avez définie. Également appelé *surcharge d’opérateur*.  
  
## <a name="when-to-define-operator-procedures"></a>Quand définir des procédures d’opérateur  
 Lorsque vous avez défini une classe ou structure, vous pouvez déclarer des variables comme étant du type de cette classe ou structure. Cette variable doit parfois participer à une opération dans le cadre d’une expression. Pour ce faire, il doit être un opérande d’un opérateur.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]définit les opérateurs uniquement sur ses types de données fondamentaux. Vous pouvez définir le comportement d’un opérateur lorsqu’une ou les deux opérandes sont du type de votre classe ou structure.  
  
 Pour plus d’informations, consultez [Operator, instruction](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="types-of-operator-procedure"></a>Types de procédure d’opérateur  
 Une procédure d’opérateur peut être un des types suivants :  
  
-   Définition d’un opérateur unaire où l’argument est du type de votre classe ou structure.  
  
-   Définition d’un opérateur binaire, où au moins un des arguments est du type de votre classe ou structure.  
  
-   Définition d’un opérateur de conversion où l’argument est du type de votre classe ou structure.  
  
-   Définition d’un opérateur de conversion qui retourne le type de votre classe ou structure.  
  
 Les opérateurs de conversion sont toujours unaires, et vous utilisez toujours `CType` comme l’opérateur que vous définissez.  
  
## <a name="declaration-syntax"></a>Syntaxe de déclaration  
 La syntaxe de déclaration d’une procédure d’opérateur est la suivante :  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  *symbole_opérateur* `(` *operand1*`[,`*operand2* `]) As` *type de données*   
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 Vous utilisez la `Widening` ou `Narrowing` mot clé uniquement sur un opérateur de conversion de type. Le symbole d’opérateur est toujours [CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md) pour un opérateur de conversion de type.  
  
 Vous déclarez deux opérandes pour définir un opérateur binaire, et un seul opérande pour définir un opérateur unaire, y compris un opérateur de conversion de type. Tous les opérandes doivent être déclarés `ByVal`.  
  
 Vous déclarez chaque opérande de la même manière que vous déclarez des paramètres pour [procédures Sub](./sub-procedures.md).  
  
### <a name="data-type"></a>Type de données  
 Étant donné que vous définissez un opérateur sur une classe ou une structure que vous avez définie, au moins un des opérandes doit être du type de données de cette classe ou structure. Pour un opérateur de conversion de type, l’opérande ou le type de retour doit être du type de données de la classe ou structure.  
  
 Pour plus d’informations, consultez [Operator, instruction](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="calling-syntax"></a>Syntaxe d’appel  
 Vous appelez une procédure d’opérateur implicitement en utilisant le symbole d’opérateur dans une expression. Vous fournissez les opérandes de la même façon que pour les opérateurs prédéfinis.  
  
 La syntaxe d’un appel implicite à une procédure d’opérateur est la suivante :  
  
 `Dim testStruct As`  *nom_structure*  
  
 `Dim testNewStruct As`  *nom_structure*`= testStruct`*symbole_opérateur*   `10`  
  
### <a name="illustration-of-declaration-and-call"></a>Illustration de déclaration et d’appel  
 La structure suivante stocke une valeur entière 128 bits signée comme parties constitutives de poids fort et de poids faible. Il définit les `+` opérateur pour ajouter deux `veryLong` les valeurs et générer résultant `veryLong` valeur.  
  
 [!code-vb[VbVbcnProcedures#23](./codesnippet/VisualBasic/operator-procedures_1.vb)]  
  
 L’exemple suivant montre un appel classique à la `+` opérateur défini sur `veryLong`.  
  
 [!code-vb[VbVbcnProcedures#24](./codesnippet/VisualBasic/operator-procedures_2.vb)]  
  
 Pour obtenir plus d’informations et des exemples, consultez [Surcharge d’opérateur dans Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)  
 [Procédures Sub](./sub-procedures.md)  
 [Procédures Function](./function-procedures.md)  
 [Procédures de propriété](./property-procedures.md)  
 [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)  
 [Operator (instruction)](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Guide pratique : définir un opérateur](./how-to-define-an-operator.md)  
 [Guide pratique : définir un opérateur de conversion](./how-to-define-a-conversion-operator.md)  
 [Guide pratique : appeler une procédure d’opérateur](./how-to-call-an-operator-procedure.md)  
 [Guide pratique : utiliser une classe qui définit des opérateurs](./how-to-use-a-class-that-defines-operators.md)
