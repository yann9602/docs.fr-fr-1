---
title: "Comment : déclarer et appeler une propriété par défaut en Visual Basic | Documents Microsoft"
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
- defaults, properties
- properties [Visual Basic], default
- procedures, defining
- default properties, in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
caps.latest.revision: 23
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
ms.openlocfilehash: ce98e7fe72a395f6c4cde481feaa60be28c6fcc3
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a>Comment : déclarer et appeler une propriété par défaut en Visual Basic
A *propriété par défaut* est une propriété de classe ou structure que votre code peut accéder sans la spécifier. Lorsque le code appelant nomme une classe ou de structure, mais pas une propriété, et le contexte autorise l’accès à une propriété, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] résout l’accès à cette classe ou de la propriété par défaut de la structure s’il en existe.  
  
 Une classe ou structure peut avoir au plus une propriété par défaut. Toutefois, vous pouvez surcharger une propriété par défaut et avoir plusieurs versions de celui-ci.  
  
 Pour plus d’informations, consultez [par défaut](../../../../visual-basic/language-reference/modifiers/default.md).  
  
### <a name="to-declare-a-default-property"></a>Pour déclarer une propriété par défaut  
  
1.  Déclarez la propriété de façon normale. Ne spécifiez pas le `Shared` ou `Private` (mot clé).  
  
2.  Inclure le `Default` mot clé dans la déclaration de propriété.  
  
3.  Spécifiez au moins un paramètre de la propriété. Vous ne pouvez pas définir une propriété par défaut qui ne prend pas au moins un argument.  
  
     [!code-vb[VbVbcnProcedures&#17;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]  
  
### <a name="to-call-a-default-property"></a>Pour appeler une propriété par défaut  
  
1.  Déclarez une variable du type classe ou la structure conteneur.  
  
     [!code-vb[VbVbcnProcedures&#16;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]  
  
2.  Utilisez le nom de variable seul dans une expression où vous incluriez normalement le nom de propriété.  
  
     [!code-vb[VbVbcnProcedures n °&21;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]  
  
3.  Suivre le nom de variable avec une liste d’arguments entre parenthèses. Une propriété par défaut doit prendre au moins un argument.  
  
     [!code-vb[VbVbcnProcedures&#20;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]  
  
4.  Pour récupérer la valeur de propriété par défaut, utilisez le nom de variable avec une liste d’arguments dans une expression ou après l’égal (`=`) se connecter dans une instruction d’assignation.  
  
     [!code-vb[VbVbcnProcedures&#15;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]  
  
5.  Pour définir la valeur de propriété par défaut, utilisez le nom de variable avec une liste d’arguments, sur le côté gauche d’une instruction d’assignation.  
  
     [!code-vb[VbVbcnProcedures&#14;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]  
  
6.  Vous pouvez toujours spécifier le nom de propriété par défaut avec le nom de variable, comme vous le feriez pour accéder à n’importe quelle autre propriété.  
  
     [!code-vb[VbVbcnProcedures n °&19;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant déclare une propriété par défaut sur une classe.  
  
 [!code-vb[VbVbcnProcedures&#12;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment appeler la propriété par défaut `myProperty` sur la classe `class1`. Stockent des valeurs dans les trois instructions d’assignation `myProperty`et le <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>appel lit les valeurs.</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
  
 [!code-vb[VbVbcnProcedures&#13;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]  
  
 L’utilisation la plus courante d’une propriété par défaut est le <xref:Microsoft.VisualBasic.Collection.Item%2A>propriété sur différentes classes de collection.</xref:Microsoft.VisualBasic.Collection.Item%2A>  
  
## <a name="robust-programming"></a>Programmation fiable  
 Propriétés par défaut peuvent entraîner une légère réduction de caractères de code source, mais ils peuvent rendre votre code plus difficile à lire. Si le code appelant n’est pas familiarisé avec votre classe ou structure, lorsqu’il fait référence au nom de classe ou structure qu’il n’est pas sûr si cette référence accède à la classe ou structure elle-même ou à une propriété par défaut. Cela peut entraîner des erreurs du compilateur ou des erreurs de logique d’exécution subtiles.  
  
 Vous pouvez légèrement réduire le risque d’erreurs de propriété par défaut en utilisant toujours le [Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md) pour définir le contrôle de type de compilateur `On`.  
  
 Si vous envisagez d’utiliser une structure ou classe prédéfini dans votre code, vous devez déterminer s’il possède une propriété par défaut et si tel est le cas, ce que son nom est.  
  
 En raison de ces inconvénients, vous devez envisager de ne pas définir de propriétés par défaut. Pour une meilleure lisibilité du code, vous devez également envisager de toujours faire explicitement référence à toutes les propriétés, même les propriétés par défaut.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures de propriété](./property-procedures.md)   
 [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md)   
 [Property (instruction)](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Par défaut](../../../../visual-basic/language-reference/modifiers/default.md)   
 [Différences entre les propriétés et les Variables en Visual Basic](./differences-between-properties-and-variables.md)   
 [Comment : créer une propriété](./how-to-create-a-property.md)   
 [Comment : déclarer une propriété avec des niveaux d’accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md)   
 [Comment : appeler une procédure de propriété](./how-to-call-a-property-procedure.md)   
 [Comment : placer une valeur dans une propriété](./how-to-put-a-value-in-a-property.md)   
 [Guide pratique : obtenir une valeur d’une propriété](./how-to-get-a-value-from-a-property.md)
