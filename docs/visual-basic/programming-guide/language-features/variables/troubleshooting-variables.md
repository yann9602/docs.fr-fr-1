---
title: "Dépannage des Variables en Visual Basic | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- troubleshooting [Visual Basic], variables
- variables [Visual Basic], troubleshooting
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 9cddf7ced50c42514ebc9a613f49adee31edde0b
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-variables-in-visual-basic"></a>Dépannage des variables en Visual Basic
Cette page répertorie quelques problèmes courants qui peuvent se produire lorsque vous travaillez avec des variables dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## <a name="unable-to-access-members-of-an-object"></a>Impossible d’accéder aux membres d’un objet  
 Si votre code tente d’accéder à une propriété ou à une méthode sur un objet, il existe deux résultats possibles en cas d’erreur :  
  
-   Le compilateur peut générer un message d’erreur si vous déclarez la variable objet comme étant d’un type spécifique et que vous faites ensuite référence à un membre non défini par ce type.  
  
-   Une exécution <xref:System.MemberAccessException>se produit lorsque l’objet assigné à une variable objet n’expose pas le membre que votre code tente d’accéder.</xref:System.MemberAccessException> Dans le cas d’une variable de [Type de données Object](../../../../visual-basic/language-reference/data-types/object-data-type.md), vous pouvez également obtenir cette exception si le membre n’est pas `Public`. Cela est dû au fait que la liaison tardive autorise l’accès uniquement aux membres `Public` .  
  
 Lors de la [Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md) définit la vérification de type `On`, une variable objet peut accéder qu’aux méthodes et propriétés de la classe avec laquelle vous la déclarez. L'exemple suivant illustre ce comportement.  

 [!code-vb[VbVbalrVariables n °&2;](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/troubleshooting-variables_1.vb)]  
  
 Dans cet exemple, `p` peut utiliser uniquement les membres de la <xref:System.Object>classe elle-même, qui n’incluent pas le `Left` propriété.</xref:System.Object> En revanche, `q` a été déclaré comme étant de type <xref:System.Windows.Forms.Label>, donc il peut utiliser toutes les méthodes et propriétés de la <xref:System.Windows.Forms.Label>classe dans le <xref:System.Windows.Forms>espace de noms.</xref:System.Windows.Forms> </xref:System.Windows.Forms.Label> </xref:System.Windows.Forms.Label>  
  
### <a name="correct-approach"></a>Approche correcte  
 Pour pouvoir accéder à tous les membres d’un objet d’une classe particulière, déclarez la variable objet comme étant du type de cette classe dans la mesure du possible. Si vous ne pouvez pas cela, par exemple, si vous ne connaissez pas l’objet de type au moment de la compilation, vous devez définir `Option Strict` à `Off` et déclarez la variable de la [Type de données Object](../../../../visual-basic/language-reference/data-types/object-data-type.md). Cela permet d’affecter des objets de tout type à la variable, et vous devez prendre les mesures nécessaires pour vous assurer que l’objet actuellement affecté est d’un type acceptable. Vous pouvez utiliser la [TypeOf, opérateur](../../../../visual-basic/language-reference/operators/typeof-operator.md) pour effectuer cette détermination.  
  
## <a name="other-components-cannot-access-your-variable"></a>D’autres composants ne peuvent pas accéder à votre variable  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]les noms sont *pas la casse*. Si deux noms diffèrent uniquement par la casse, le compilateur les interprète comme étant identiques. Par exemple, il considère que `ABC` et `abc` font référence au même élément déclaré.  
  
 Toutefois, le Common Language Runtime (CLR) utilise la liaison *qui respecte la casse* . Ainsi, quand vous générez un assembly ou une DLL et que vous le mettez à disposition d’autres assemblys, la casse de vos noms est respectée. Par exemple, si vous définissez une classe avec un élément nommé `ABC`et que d’autres assemblys utilisent votre classe par le biais du Common Language Runtime, ils doivent faire référence à l’élément en tant que `ABC`. Si, par la suite, vous recompilez votre classe et que vous changez le nom de l’élément en `abc`, les autres assemblys qui utilisent votre classe ne peuvent plus accéder à cet élément. Ainsi, quand vous publiez une version mise à jour d’un assembly, vous ne devez pas modifier la casse des éléments publics.  
  
 Pour plus d’informations, consultez [Common Language Runtime](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482).  
  
### <a name="correct-approach"></a>Approche correcte  
 Pour permettre à d’autres composants d’accéder à vos variables, traitez leurs noms comme s’ils respectaient la casse. Quand vous testez votre classe ou module, vérifiez que les autres assemblys se lient aux variables prévues. Une fois que vous avez publié un composant, ne modifiez pas les noms de variables existants, notamment leur casse.  
  
## <a name="wrong-variable-being-used"></a>Variable incorrecte utilisée  
 Lorsque vous avez plusieurs variables portant le même nom, le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur tente de résoudre chaque référence à ce nom. Si les variables ont une portée différente, le compilateur résout une référence à la déclaration dont la portée est la plus petite. Si elles ont la même portée, la résolution échoue et le compilateur signale une erreur. Pour plus d’informations, consultez [références aux éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
### <a name="correct-approach"></a>Approche correcte  
 Évitez d’utiliser des variables ayant le même nom mais une portée différente. Si vous utilisez d’autres assemblys ou projets, évitez d’utiliser des noms définis dans ces composants externes. Si plusieurs variables ont le même nom, n’oubliez pas de qualifier chaque référence à celui-ci. Pour plus d’informations, consultez [références aux éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Déclaration des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Comment : accéder aux membres d’un objet](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)   
 [Valeurs des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [Comment : déterminer le Type désigné par une Variable objet](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)   
 [Références aux éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Noms d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
