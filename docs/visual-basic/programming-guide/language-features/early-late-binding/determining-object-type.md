---
title: "Determining Object Type (Visual Basic) | Microsoft Docs"
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
  - "classes [Visual Basic], discovering which an object belongs to"
  - "types [Visual Basic], determining Visual Basic object types"
  - "object variables, testing values"
  - "TypeOf...Is expression, object type at run time"
  - "TypeName function"
  - "objects [Visual Basic], type determining"
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Determining Object Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Les variables objets génériques \(c'est\-à\-dire les variables que vous déclarez comme étant de type `Object`\) peuvent contenir les objets de n'importe quelle classe.  Lorsque vous utilisez des variables de type `Object`, vous devez peut\-être prendre des mesures différentes selon la classe de l'objet ; certains objets peuvent ne pas prendre en charge une propriété particulière ou méthode, par exemple.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] offre deux moyens de déterminer quel type d'objet est stocké dans une variable objet : la fonction `TypeName` et l'opérateur `TypeOf...Is`.  
  
## TypeName et TypeOf…Is  
 La fonction `TypeName` retourne une chaîne et représente le meilleur choix lorsque vous devez stocker ou afficher le nom de classe d'un objet, comme illustré dans le fragment de code suivant :  
  
 [!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#92)]  
  
 L'opérateur `TypeOf...Is` représente le meilleur choix lorsqu'il s'agit de tester le type d'un objet, car il est beaucoup plus rapide qu'une comparaison de chaînes équivalente à l'aide de la fonction `TypeName`.  Le fragment de code suivant utilise `TypeOf...Is` dans une instruction `If...Then...Else`.  
  
 [!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#93)]  
  
 Néanmoins, il convient d'apporter certaines précisions.  L'opérateur `TypeOf...Is` retourne `True` si l'objet est d'un type spécifique ou s'il est dérivé d'un type spécifique.  Quasiment toutes vos actions dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] reposent sur l'utilisation d'objets, y compris des éléments qui ne sont pas forcément perçues comme des objets, par exemple les chaînes et les entiers.  Ces objets sont dérivés et héritent des méthodes de <xref:System.Object>.  Lorsqu'un `Integer` lui est passé et qu'il est évalué avec `Object`, l'opérateur `TypeOf...Is` retourne `True`.  L'exemple suivant indique que le paramètre `InParam` est à la fois du type `Object` et `Integer` :  
  
 [!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#94)]  
  
 L'exemple suivant utilise à la fois `TypeOf...Is` et `TypeName` pour déterminer le type d'objet passé dans l'argument `Ctrl`.  La procédure `TestObject` appelle `ShowType` à l'aide de trois sortes de contrôles différents.  
  
#### Pour exécuter l'exemple  
  
1.  Créez un projet Application Windows et ajoutez un contrôle <xref:System.Windows.Forms.Button>, un contrôle <xref:System.Windows.Forms.CheckBox> et un contrôle <xref:System.Windows.Forms.RadioButton> au formulaire.  
  
2.  À partir du bouton situé sur votre formulaire, appelez la procédure `TestObject`.  
  
3.  Ajoutez le code suivant à votre formulaire :  
  
     [!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#95)]  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Information.TypeName%2A>   
 [Calling a Property or Method Using a String Name](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md)   
 [Integer Data Type](../../../../visual-basic/language-reference/data-types/integer-data-type.md)