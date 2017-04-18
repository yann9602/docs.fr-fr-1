---
title: "Appel d’une propriété ou une méthode à l’aide d’un nom de chaîne (Visual Basic) | Documents Microsoft"
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
- passing operators
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls, strings
- methods [Visual Basic], calling with string names
- calling methods, string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
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
ms.openlocfilehash: 87af2816ba42e2901c53bec5e9c19f34c676ed5c
ms.lasthandoff: 03/13/2017

---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>Appel d'une propriété ou méthode à l'aide d'un nom de chaîne (Visual Basic)
Dans la plupart des cas, vous pouvez découvrir les propriétés et méthodes d’un objet au moment du design et écrire du code pour les gérer. Toutefois, dans certains cas vous ne pouvez pas savoir sur les propriétés et les méthodes d’un objet à l’avance ou vous voudrez tout simplement la flexibilité de l’activation d’un utilisateur final de spécifier les propriétés et méthodes d’exécution au moment de l’exécution.  
  
## <a name="callbyname-function"></a>CallByName (fonction)  
 Considérons, par exemple, une application cliente qui évalue des expressions entrées par l’utilisateur en passant un opérateur à un composant COM. Supposons que vous voulez constamment ajouter de nouvelles fonctions au composant requérant de nouveaux opérateurs. Lorsque vous utilisez des techniques d’accès standard, vous devez recompiler et redistribuer l’application cliente avant qu’il puisse utiliser les nouveaux opérateurs. Pour éviter ce problème, vous pouvez utiliser la `CallByName` (fonction) pour passer les nouveaux opérateurs en tant que chaînes, sans modifier l’application.  
  
 Le `CallByName` fonction vous permet d’utiliser une chaîne pour spécifier une propriété ou une méthode au moment de l’exécution. La signature pour le `CallByName` fonction ressemble à ceci :  
  
 *Result* = `CallByName`(*Object*, *ProcedureName*, *CallType*, *Arguments*())  
  
 Le premier argument, *objet*, prend le nom de l’objet que vous voulez agir. Le *NomProcédure* argument accepte une chaîne qui contient le nom de la procédure de propriété ou méthode à appeler. Le *CallType* argument accepte une constante qui représente le type de procédure à appeler : une méthode (`Microsoft.VisualBasic.CallType.Method`), une lecture de propriété (`Microsoft.VisualBasic.CallType.Get`), ou un jeu de propriétés (`Microsoft.VisualBasic.CallType.Set`). Le *Arguments* argument, qui est facultatif, accepte un tableau de type `Object` qui contient les arguments à la procédure.  
  
 Vous pouvez utiliser `CallByName` avec les classes de votre solution actuelle, mais elle est généralement utilisée pour accéder aux objets COM ou des objets de [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblys.  
  
 Supposons que vous ajoutez une référence à un assembly qui contient une classe nommée `MathClass`, qui a une nouvelle fonction nommée `SquareRoot`, comme illustré dans le code suivant :  
  
 [!code-vb[VbVbalrOOP&#53;](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]  
  
 Votre application peut utiliser des contrôles de zone de texte pour contrôler quelle méthode sera appelée et ses arguments. Par exemple, si `TextBox1` contient l’expression à évaluer, et `TextBox2` est utilisée pour entrer le nom de la fonction, vous pouvez utiliser le code suivant pour appeler le `SquareRoot` fonction à l’expression de `TextBox1`:  
  
 [!code-vb[VbVbalrOOP&#54;](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]  
  
 Si vous entrez « 64 » dans `TextBox1`, « SquareRoot » dans `TextBox2`, puis appelez le `CallMath` procédure, la racine carrée du nombre contenu dans `TextBox1` est évaluée. Le code dans l’exemple appelle la `SquareRoot` la fonction (qui accepte une chaîne qui contient l’expression à évaluer comme un argument obligatoire) et retourne « 8 » dans `TextBox1` (la racine carrée de 64). Bien entendu, si l’utilisateur entre une chaîne non valide dans `TextBox2`, si la chaîne contient le nom d’une propriété plutôt qu’une méthode ou si la méthode possède un argument obligatoire supplémentaire, une erreur d’exécution se produit. Vous devez ajouter le code robuste de gestion des erreurs lorsque vous utilisez `CallByName` afin d’anticiper les autres erreurs.  
  
> [!NOTE]
>  Bien que le `CallByName` fonction peut être utile dans certains cas, vous devez également considérer son utilité contre les implications en matière de performances, à l’aide de `CallByName` pour appeler une procédure est légèrement plus lent qu’un appel à liaison tardive. Si vous appelez une fonction qui est appelée à plusieurs reprises, par exemple comme dans une boucle, `CallByName` peut avoir un impact négatif sur les performances.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A></xref:Microsoft.VisualBasic.Interaction.CallByName%2A>   
 [Détermination du type Object](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)
