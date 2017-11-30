---
title: Conseils relatifs aux performances .NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- C# language, performance
- performance [C#]
- Visual Basic, performance
- performance [Visual Basic]
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
caps.latest.revision: "36"
author: BillWagner
ms.author: wiwagn
manager: wpickett
ms.openlocfilehash: 93db69b67bfac3bcefbc818032aae64df0fd47b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="net-performance-tips"></a>Conseils relatifs aux performances .NET
Le terme *performances* désigne généralement la vitesse d’exécution d’un programme. Vous pouvez parfois augmenter la vitesse d’exécution en suivant certaines règles de base dans votre code source. Dans certains programmes, il est important d’examiner attentivement le code et d’utiliser des profileurs pour garantir que le programme s’exécute aussi rapidement que possible. Dans d’autres programmes, vous n’avez pas à effectuer une telle optimisation, car le code, tel qu’il est écrit, est suffisamment rapide. Cet article répertorie les zones dont les performances sont fréquemment impactées, et fournit des conseils d’amélioration, ainsi que des liens vers d’autres rubriques relatives aux performances. Pour plus d’informations sur la planification et la mesure des performances, consultez [Performances](../../../docs/framework/performance/index.md)  
  
## <a name="boxing-and-unboxing"></a>Conversion boxing et unboxing  
 Il est préférable de ne pas utiliser de types valeur lorsque ceux-ci doivent être convertis (boxed) de nombreuses fois, par exemple, dans les classes de collections non génériques comme <xref:System.Collections.ArrayList?displayProperty=nameWithType>. Vous pouvez éviter le boxing des types valeur en utilisant des collections génériques comme <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Le boxing et l’unboxing sont des processus qui coûtent cher en calcul. Lorsqu’un type valeur est converti (boxed), un tout nouvel objet doit être créé. Cela peut être 20 fois plus long qu’une simple assignation de référence. Lors d’une conversion unboxing, le processus de cast peut être quatre fois plus long que celui d’une assignation. Pour plus d’informations, consultez [Conversion boxing et unboxing](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## <a name="strings"></a>Chaînes  
 Lorsque vous concaténez un grand nombre de variables de chaîne, par exemple, dans une boucle serrée, utilisez <xref:System.Text.StringBuilder?displayProperty=nameWithType> au lieu de [l’opérateur +](~/docs/csharp/language-reference/operators/addition-operator.md) C# ou des [opérateurs de concaténation](~/docs/visual-basic/language-reference/operators/concatenation-operators.md) Visual Basic. Pour plus d’informations, consultez [Guide pratique pour concaténer plusieurs chaînes](~/docs/csharp/programming-guide/strings/how-to-concatenate-multiple-strings.md) et [Opérateurs de concaténation (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).  
  
## <a name="destructors"></a>Destructeurs  
 Les destructeurs vides ne doivent pas être utilisés. Quand une classe contient un destructeur, une entrée est créée dans la file d’attente Finalize. Quand le destructeur est appelé, le récupérateur de mémoire est appelé pour traiter la file d’attente. Si le destructeur est vide, cela ne fait que dégrader les performances. Pour plus d’informations, consultez [Destructeurs](~/docs/csharp/programming-guide/classes-and-structs/destructors.md) et [Durée de vie d’un objet : création et destruction des objets](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
## <a name="other-resources"></a>Autres ressources  
  
-   [Writing Faster Managed Code: Know What Things Cost](http://go.microsoft.com/fwlink/?LinkId=99294)  
  
-   [Writing High-Performance Managed Applications: A Primer](http://go.microsoft.com/fwlink/?LinkId=99295)  
  
-   [Garbage Collector Basics and Performance Hints](http://go.microsoft.com/fwlink/?LinkId=99296)  
  
-   [Performance Tips and Tricks in .NET Applications](http://go.microsoft.com/fwlink/?LinkId=99297)  
  
-   [Inside Diagnostic Tools for .NET](http://go.microsoft.com/fwlink/?LinkId=112407)  
  
-   [Rico Mariani’s Performance Tidbits](http://go.microsoft.com/fwlink/?LinkId=115679) (Blog de Rico Mariani sur les performances)  
  
## <a name="see-also"></a>Voir aussi  
 [Performances](../../../docs/framework/performance/index.md)  
 [Concepts de programmation](http://msdn.microsoft.com/library/65c12cca-af4f-4017-886e-2dbc00a189d6)  
 [Guide de programmation Visual Basic](../../visual-basic/programming-guide/index.md)  
 [Guide de programmation C#](http://msdn.microsoft.com/library/ac0f23a2-6bf3-4077-be99-538ae5fd3bc5)
