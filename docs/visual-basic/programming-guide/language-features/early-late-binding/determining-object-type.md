---
title: "Détermination du Type Object (Visual Basic) | Documents Microsoft"
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
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables, testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 2486d989801fc4866a50747aa963b509a627994d
ms.lasthandoff: 03/13/2017

---
# <a name="determining-object-type-visual-basic"></a>Détermination du type Object (Visual Basic)
Les variables objets génériques (autrement dit, les variables que vous déclarez comme `Object`) peuvent contenir les objets à partir de n’importe quelle classe. Lorsque vous utilisez des variables de type `Object`, vous devrez peut-être prendre des mesures différentes selon la classe de l’objet ; par exemple, certains objets ne peuvent pas en charge une propriété ou méthode particulière. [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]offre deux moyens de déterminer quel type d’objet est stocké dans une variable objet : le `TypeName` (fonction) et `TypeOf...Is` (opérateur).  
  
## <a name="typename-and-typeofis"></a>TypeName et TypeOf... Est  
 Le `TypeName` fonction retourne une chaîne et est le meilleur choix lorsque vous devez stocker ou afficher le nom de classe d’un objet, comme illustré dans le fragment de code suivant :  
  
 [!code-vb[VbVbalrOOP&#92;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]  
  
 Le `TypeOf...Is` opérateur est le meilleur choix pour tester le type d’un objet, car il est beaucoup plus rapide qu’une comparaison de chaîne équivalente à l’aide de `TypeName`. Le fragment de code suivant utilise `TypeOf...Is` dans un `If...Then...Else` instruction :  
  
 [!code-vb[VbVbalrOOP&#93;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]  
  
 Un mot de prudence est due ici. Le `TypeOf...Is` opérateur retourne `True` si un objet est d’un type spécifique, ou est dérivé d’un type spécifique. Presque tout ce que vous effectuez avec [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] implique des objets, qui incluent des éléments pas forcément perçues comme des objets, tels que les chaînes et les entiers. Ces objets sont dérivés et héritent des méthodes de <xref:System.Object>.</xref:System.Object> Lorsqu’il est passé un `Integer` et évaluée avec `Object`, le `TypeOf...Is` opérateur retourne `True`. L’exemple suivant indique que le paramètre `InParam` est à la fois un `Object` et une `Integer`:  
  
 [!code-vb[VbVbalrOOP&#94;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]  
  
 L’exemple suivant utilise à la fois `TypeOf...Is` et `TypeName` pour déterminer le type d’objet passé dans le `Ctrl` argument. Le `TestObject` les appels de procédure `ShowType` avec trois différents types de contrôles.  
  
#### <a name="to-run-the-example"></a>Pour exécuter l'exemple  
  
1.  Créez un nouveau projet d’Application Windows et ajoutez un <xref:System.Windows.Forms.Button>contrôle, un <xref:System.Windows.Forms.CheckBox>contrôle et un <xref:System.Windows.Forms.RadioButton>contrôle au formulaire.</xref:System.Windows.Forms.RadioButton> </xref:System.Windows.Forms.CheckBox> </xref:System.Windows.Forms.Button>  
  
2.  À partir du bouton sur votre formulaire, appelez le `TestObject` procédure.  
  
3.  Ajoutez le code suivant à votre formulaire :  
  
     [!code-vb[VbVbalrOOP&#95;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Information.TypeName%2A></xref:Microsoft.VisualBasic.Information.TypeName%2A>   
 [Appel d’une propriété ou méthode à l’aide d’un nom de chaîne](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)   
 [Type de données Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [If... Puis... Else, instruction](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Type de données String](../../../../visual-basic/language-reference/data-types/string-data-type.md)   
 [Integer (type de données)](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
