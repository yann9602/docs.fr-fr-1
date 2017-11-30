---
title: Assignation des variables objets (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: eb6b53bebddc1c9cf1b9088e96ded36a5e1c5242
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="object-variable-assignment-visual-basic"></a>Assignation des variables objets (Visual Basic)
Vous utilisez une instruction d’assignation normale pour assigner un objet à une variable objet. Vous pouvez affecter une expression d’objet ou le [rien](../../../../visual-basic/language-reference/nothing.md) (mot clé), comme l’exemple suivant illustre.  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 `Nothing`signifie aucun objet actuellement assigné à la variable.  
  
## <a name="initialization"></a>Initialisation  
 Lorsque votre code commence à s’exécuter, votre objet variables sont initialisées à `Nothing`. Ceux dont les déclarations incluent l’initialisation sont réinitialisées avec les valeurs que vous spécifiez lorsque les instructions de déclaration sont exécutées.  
  
 Vous pouvez inclure l’initialisation dans votre déclaration à l’aide de la [nouveau](../../../../visual-basic/language-reference/operators/new-operator.md) (mot clé). Les instructions de déclaration suivantes déclarent des variables objets `testUri` et `ver` et leur attribuer des objets spécifiques. Chacune utilise un des constructeurs surchargés de la classe appropriée pour initialiser l’objet.  
  
```  
Dim testUri As New System.Uri("http://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a>Dissociation  
 Affectation à une variable objet `Nothing` interrompt l’association de la variable et un objet spécifique. Cela vous empêche de modifier accidentellement l’objet en modifiant la variable. Il vous permet également de tester si la variable objet pointe vers un objet valide, comme le montre l’exemple suivant.  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 Si l’objet désigné par votre variable est dans une autre application, ce test ne peut pas déterminer si cette application est arrêtée ou invalider l’objet.  
  
 Une variable objet avec la valeur `Nothing` est également appelé un *référence null*.  
  
## <a name="current-instance"></a>Instance actuelle  
 Le *instance actuelle* d’un objet est celui dans lequel le code est en cours d’exécution. Étant donné que tout le code s’exécute à l’intérieur d’une procédure, l’instance actuelle est celui dans lequel la procédure a été appelée.  
  
 Le `Me` mot clé sert de variable objet faisant référence à l’instance actuelle. Si une procédure n’est pas [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), il peut utiliser le `Me` mot clé à obtenir un pointeur vers l’instance actuelle. Les procédures partagées ne peut pas être associés à une instance spécifique d’une classe.  
  
 À l’aide de `Me` est particulièrement utile pour le passage de l’instance actuelle à une procédure dans un autre module. Par exemple, supposons que vous avez un nombre de documents XML et que vous souhaitez ajouter un texte standard pour tous les. L’exemple suivant définit une procédure pour ce faire.  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 Chaque objet de document XML peut ensuite appeler la procédure et passer son instance en cours en tant qu’argument. Cela est illustré par l'exemple suivant.  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Déclaration des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Valeurs des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Comment : déclarer une Variable objet et lui assigner un objet en Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [Guide pratique : faire en sorte qu'une variable objet ne fasse pas référence à une instance](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)  
 [Me, My, MyBase et MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
