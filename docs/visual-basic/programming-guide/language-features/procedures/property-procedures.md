---
title: "Procédures Property (Visual Basic) | Documents Microsoft"
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
- Set statement, Property procedures
- Visual Basic code, procedures
- return values, Property procedures
- syntax, Property procedures
- procedures, property
- Visual Basic code, properties
- procedures, calling
- properties [Visual Basic], custom
- property procedures
- Get statement, property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
caps.latest.revision: 22
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f21d4c7d9bd8f14bbe7284bc08399e7ba6b466c3
ms.lasthandoff: 03/13/2017

---
# <a name="property-procedures-visual-basic"></a>Procédures de propriété (Visual Basic)
Une procédure de propriété est une série de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] instructions qui manipulent une propriété personnalisée d’un module, classe ou structure. Procédures de propriété sont également appelées *accesseurs de propriété*.  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Fournit des procédures de propriété suivantes :  
  
-   Un `Get` procédure retourne la valeur d’une propriété. Il est appelé lorsque vous accédez à la propriété dans une expression.  
  
-   Un `Set` procédure définit une propriété sur une valeur, y compris une référence d’objet. Il est appelé lorsque vous affectez une valeur à la propriété.  
  
 Procédures de propriété sont généralement définies par paires, à l’aide de la `Get` et `Set` les instructions, mais vous pouvez définir chaque procédure uniquement si la propriété est en lecture seule ([instruction Get](../../../../visual-basic/language-reference/statements/get-statement.md)) ou en écriture seule ([instruction Set](../../../../visual-basic/language-reference/statements/set-statement.md)).  
  
 Vous pouvez omettre le `Get` et `Set` procédure lors de l’utilisation d’une propriété implémentée automatiquement. Pour plus d’informations, consultez [auto-Implemented Properties](./auto-implemented-properties.md).  
  
 Vous pouvez définir des propriétés dans les classes, structures et les modules. Les propriétés sont `Public` par défaut, ce qui signifie que vous pouvez les appeler depuis n’importe où dans votre application qui peut accéder au conteneur de la propriété.  
  
 Pour une comparaison des propriétés et des variables, consultez [différences entre les propriétés et les Variables en Visual Basic](./differences-between-properties-and-variables.md).  
  
## <a name="declaration-syntax"></a>Syntaxe de déclaration  
 Une propriété est définie par un bloc de code contenu dans le [Property, instruction](../../../../visual-basic/language-reference/statements/property-statement.md) et `End Property` instruction. À l’intérieur de ce bloc, chaque procédure property s’affiche sous forme de bloc interne délimité par une instruction de déclaration (`Get` ou `Set`) et la mise en correspondance `End` déclaration.  
  
 La syntaxe de déclaration d’une propriété et ses procédures est la suivante :  
  
```  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 Le `Modifiers` peut spécifier de niveau d’accès et les informations concernant la surcharge, la substitution, le partage et l’occultation, ainsi que si la propriété est en lecture seule ou en écriture seule. Le `AccessLevel` sur la `Get` ou `Set` procédure peut être n’importe quel niveau est plus restrictif que le niveau d’accès spécifié pour la propriété proprement dite. Pour plus d’informations, consultez [Property, instruction](../../../../visual-basic/language-reference/statements/property-statement.md).  
  
### <a name="data-type"></a>Type de données  
 Un type de données et le niveau d’accès principal sont définis dans la `Property` instruction, pas dans les procédures de propriété. Une propriété peut avoir uniquement un type de données. Par exemple, vous ne pouvez pas définir une propriété pour stocker une `Decimal` valeur mais récupérer un `Double` valeur.  
  
### <a name="access-level"></a>Niveau d’accès  
 Toutefois, vous pouvez définir un niveau d’accès principal d’une propriété et restreindre davantage le niveau d’accès de l’une de ses procédures de propriété. Par exemple, vous pouvez définir un `Public` propriété, puis définissez un `Private Set` procédure. Le `Get` procédure reste `Public`. Vous pouvez modifier le niveau d’accès dans l’une des procédures de la propriété, et vous pouvez uniquement le rendre plus restrictif que le niveau d’accès principal. Pour plus d’informations, consultez [Comment : déclarer une propriété avec des niveaux d’accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md).  
  
## <a name="parameter-declaration"></a>Déclaration de paramètre  
 Vous déclarez chaque paramètre de la même façon que pour [procédures Sub](./sub-procedures.md), sauf que le mécanisme de passage doit être `ByVal`.  
  
 La syntaxe de chaque paramètre dans la liste des paramètres est la suivante :  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 Si le paramètre est facultatif, vous devez également fournir une valeur par défaut dans le cadre de sa déclaration. La syntaxe de spécification d’une valeur par défaut est la suivante :  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a>Valeur de propriété  
 Dans un `Get` procédure, la valeur de retour est fournie à l’expression appelante en tant que la valeur de la propriété.  
  
 Dans un `Set` procédure, la nouvelle valeur de propriété est passée au paramètre de la `Set` instruction. Si vous déclarez explicitement un paramètre, vous devez la déclarer avec le même type de données que la propriété. Si vous ne déclarez pas d’argument, le compilateur utilise le paramètre implicite `Value` pour représenter la nouvelle valeur à assigner à la propriété.  
  
## <a name="calling-syntax"></a>Syntaxe d’appel  
 Vous appelez une procédure de propriété implicitement en faisant référence à la propriété. Utiliser le nom de la propriété de la même façon, vous devez utiliser le nom d’une variable, sauf que vous devez fournir des valeurs pour tous les arguments qui ne sont pas facultatifs, et vous devez placer la liste d’arguments entre parenthèses. Si aucun argument n’est fourni, vous pouvez omettre les parenthèses.  
  
 La syntaxe d’un appel implicite à une `Set` comme suit :  
  
 `propertyname[(argumentlist)] = expression`  
  
 La syntaxe d’un appel implicite à une `Get` comme suit :  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a>Illustration de déclaration et d’appel  
 La propriété suivante stocke un nom complet comme deux noms constitutifs, le prénom et le nom de famille. Lorsque le code appelant lit `fullName`, le `Get` procédure combine les deux noms constitutifs et retourne le nom complet. Lorsque le code appelant assigne un nouveau nom complet, le `Set` procédure essaie de la décomposer en deux noms constitutifs. S’il ne trouve pas d’un espace, elle est stockée sous la forme Prénom.  
  
 [!code-vb[VbVbcnProcedures n °&8;](./codesnippet/VisualBasic/property-procedures_1.vb)]  
  
 L’exemple suivant montre des appels typiques aux procédures de propriété `fullName`.  
  
 [!code-vb[VbVbcnProcedures&#9;](./codesnippet/VisualBasic/property-procedures_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)   
 [Procédures Function](./function-procedures.md)   
 [Procédures d’opérateur](./operator-procedures.md)   
 [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md)   
 [Différences entre les propriétés et les Variables en Visual Basic](./differences-between-properties-and-variables.md)   
 [Comment : créer une propriété](./how-to-create-a-property.md)   
 [Comment : appeler une procédure de propriété](./how-to-call-a-property-procedure.md)   
 [Comment : déclarer et appeler une propriété par défaut en Visual Basic](./how-to-declare-and-call-a-default-property.md)   
 [Comment : placer une valeur dans une propriété](./how-to-put-a-value-in-a-property.md)   
 [Guide pratique : obtenir une valeur d’une propriété](./how-to-get-a-value-from-a-property.md)
