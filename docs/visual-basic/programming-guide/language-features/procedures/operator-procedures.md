---
title: "Procédures d’opérateur (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, procedures
- procedures, operator
- Visual Basic code, operators
- syntax, Operator procedures
- operators [Visual Basic], overloading
- overloaded operators
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a9e86c9c466ba236cc33153f2f341af35c622de6
ms.lasthandoff: 03/13/2017

---
# <a name="operator-procedures-visual-basic"></a>Procédures d'opérateur (Visual Basic)
Une procédure d’opérateur est une série de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] instructions qui définissent le comportement d’un opérateur standard (tel que `*`, `<>`, ou `And`) sur une classe ou une structure que vous avez définie. Également appelé *la surcharge d’opérateur*.  
  
## <a name="when-to-define-operator-procedures"></a>Quand définir des procédures d’opérateur  
 Lorsque vous avez défini une classe ou structure, vous pouvez déclarer des variables comme étant du type de cette classe ou structure. Cette variable doit parfois participer à une opération dans le cadre d’une expression. Pour ce faire, il doit être un opérande d’un opérateur.  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]définit des opérateurs uniquement sur les types de données fondamentaux. Vous pouvez définir le comportement d’un opérateur lorsqu’une ou les deux opérandes sont du type de votre classe ou structure.  
  
 Pour plus d’informations, consultez [Operator, instruction](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="types-of-operator-procedure"></a>Types de procédure d’opérateur  
 Une procédure d’opérateur peut être un des types suivants :  
  
-   Définition d’un opérateur unaire dans laquelle l’argument est du type de votre classe ou structure.  
  
-   Définition d’un opérateur binaire dans lequel au moins un des arguments est du type de votre classe ou structure.  
  
-   Définition d’un opérateur de conversion où l’argument est du type de votre classe ou structure.  
  
-   Définition d’un opérateur de conversion qui retourne le type de votre classe ou structure.  
  
 Opérateurs de conversion sont toujours unaires, et vous utilisez toujours `CType` comme l’opérateur que vous définissez.  
  
## <a name="declaration-syntax"></a>Syntaxe de déclaration  
 La syntaxe de déclaration d’une procédure d’opérateur est la suivante :  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 Vous utilisez la `Widening` ou `Narrowing` (mot clé) uniquement sur un opérateur de conversion. Le symbole d’opérateur est toujours [CType, fonction](../../../../visual-basic/language-reference/functions/ctype-function.md) pour un opérateur de conversion de type.  
  
 Vous déclarez deux opérandes pour définir un opérateur binaire, et un seul opérande pour définir un opérateur unaire, y compris un opérateur de conversion de type. Tous les opérandes doivent être déclarées `ByVal`.  
  
 Vous déclarez chaque opérande de la même manière que vous déclarez des paramètres pour [procédures Sub](./sub-procedures.md).  
  
### <a name="data-type"></a>Type de données  
 Étant donné que vous définissez un opérateur sur une classe ou une structure que vous avez définie, au moins un des opérandes doit être du type de données de cette classe ou structure. Pour un opérateur de conversion de type, l’opérande ou le type de retour doit être du type de données de la classe ou structure.  
  
 Pour plus d’informations, consultez [Operator, instruction](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="calling-syntax"></a>Syntaxe d’appel  
 Vous appelez une procédure d’opérateur implicitement en utilisant le symbole d’opérateur dans une expression. Vous fournissez les opérandes de la même façon que pour les opérateurs prédéfinis.  
  
 La syntaxe d’un appel implicite à une procédure d’opérateur est la suivante :  
  
 `Dim testStruct As`  *structurename*  
  
 `Dim testNewStruct As`  *structurename*`= testStruct`*operatorsymbol    *  `10`  
  
### <a name="illustration-of-declaration-and-call"></a>Illustration de déclaration et d’appel  
 La structure suivante stocke une valeur entière 128 bits signée comme parties constitutives de poids fort et de poids faible. Il définit les `+` opérateur pour ajouter deux `veryLong` valeurs et générer une issue `veryLong` valeur.  
  
 [!code-vb[VbVbcnProcedures n °&23;](./codesnippet/VisualBasic/operator-procedures_1.vb)]  
  
 L’exemple suivant montre un appel typique à le `+` opérateur défini sur `veryLong`.  
  
 [!code-vb[VbVbcnProcedures&#24;](./codesnippet/VisualBasic/operator-procedures_2.vb)]  
  
 Pour plus d’informations et d’exemples, consultez [surcharge d’opérateur dans Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)   
 [Procédures Sub](./sub-procedures.md)   
 [Procédures Function](./function-procedures.md)   
 [Procédures de propriété](./property-procedures.md)   
 [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md)   
 [Operator (instruction)](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Comment : définir un opérateur](./how-to-define-an-operator.md)   
 [Comment : définir un opérateur de Conversion](./how-to-define-a-conversion-operator.md)   
 [Comment : appeler une procédure d’opérateur](./how-to-call-an-operator-procedure.md)   
 [Guide pratique : utiliser une classe qui définit des opérateurs](./how-to-use-a-class-that-defines-operators.md)
