---
title: "Appel d'une propriété ou méthode à l'aide d'un nom de chaîne (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- passing operators [Visual Basic]
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls [Visual Basic], strings
- methods [Visual Basic], calling with string names
- calling methods [Visual Basic], string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c5974257fb82fe83c66a480225da200c14338898
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>Appel d'une propriété ou méthode à l'aide d'un nom de chaîne (Visual Basic)
Dans la plupart des cas, vous pouvez découvrir les propriétés et méthodes d’un objet au moment du design et écrire du code pour les gérer. Toutefois, dans certains cas vous ne pouvez pas savoir sur les propriétés et les méthodes d’un objet à l’avance, ou vous devez la flexibilité de l’utilisateur spécifier des propriétés ou méthodes d’exécution au moment de l’exécution.  
  
## <a name="callbyname-function"></a>Fonction CallByName  
 Considérons, par exemple, une application cliente qui évalue des expressions entrées par l’utilisateur en passant un opérateur pour un composant COM. Supposons que vous ajoutez en permanence nouvelles fonctions pour le composant qui nécessitent de nouveaux opérateurs. Lorsque vous utilisez des techniques d’accès standard, vous devez recompiler et redistribuer l’application cliente avant qu’il puisse utiliser les nouveaux opérateurs. Pour éviter ce problème, vous pouvez utiliser la `CallByName` (fonction) pour passer les nouveaux opérateurs en tant que chaînes, sans modifier l’application.  
  
 Le `CallByName` fonction vous permet d’utiliser une chaîne pour spécifier une propriété ou méthode en cours d’exécution. La signature pour le `CallByName` fonction ressemble à ceci :  
  
 *Résultat* = `CallByName`(*objet*, *Nom_procédure*, *CallType*, *Arguments*())  
  
 Le premier argument, *objet*, prend le nom de l’objet que vous voulez agir. Le *Nom_procédure* argument accepte une chaîne qui contient le nom de la procédure de propriété ou méthode à appeler. Le *CallType* argument accepte une constante qui représente le type de procédure à appeler : une méthode (`Microsoft.VisualBasic.CallType.Method`), une propriété de lecture (`Microsoft.VisualBasic.CallType.Get`), ou un jeu de propriétés (`Microsoft.VisualBasic.CallType.Set`). Le *Arguments* argument, qui est facultatif, accepte un tableau de type `Object` qui contient les arguments à la procédure.  
  
 Vous pouvez utiliser `CallByName` avec les classes dans votre solution actuelle, mais il est souvent utilisé pour accéder aux objets COM ou des objets à partir de [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblys.  
  
 Supposons que vous ajoutez une référence à un assembly qui contient une classe nommée `MathClass`, qui a une fonction nommée `SquareRoot`, comme illustré dans le code suivant :  
  
 [!code-vb[VbVbalrOOP#53](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]  
  
 Votre application peut utiliser des contrôles de zone de texte pour le contrôle sur lequel la méthode sera appelée et de ses arguments. Par exemple, si `TextBox1` contient l’expression à évaluer, et `TextBox2` est utilisé pour entrer le nom de la fonction, vous pouvez utiliser le code suivant pour appeler le `SquareRoot` fonction à l’expression de `TextBox1`:  
  
 [!code-vb[VbVbalrOOP#54](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]  
  
 Si vous entrez « 64 » dans `TextBox1`, « SquareRoot » dans `TextBox2`, puis appelez le `CallMath` procédure, la racine carrée du nombre figurant dans `TextBox1` est évaluée. Le code dans l’exemple appelle la `SquareRoot` la fonction (qui prend une chaîne qui contient l’expression à évaluer comme un argument obligatoire) et retourne « 8 » dans `TextBox1` (la racine carrée de 64). Bien entendu, si l’utilisateur entre une chaîne non valide dans `TextBox2`si la chaîne contient le nom d’une propriété au lieu d’une méthode, ou si la méthode possède un argument obligatoire supplémentaire, une erreur d’exécution se produit. Vous devez ajouter le code fiable de gestion des erreurs lorsque vous utilisez `CallByName` afin d’anticiper les autres erreurs.  
  
> [!NOTE]
>  Alors que le `CallByName` fonction peut être utile dans certains cas, vous devez peser son utilité par rapport à l’impact sur les performances, à l’aide de `CallByName` pour appeler une procédure est légèrement plus lente qu’un appel à liaison tardive. Si vous appelez une fonction qui est appelée à plusieurs reprises, tel que dans une boucle, `CallByName` peut avoir un impact négatif sur les performances.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>  
 [Détermination du type Object](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)
