---
title: Conventions d'affectation de noms Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a59139b57568810de80de764388eeffa5f8d7ac9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="visual-basic-naming-conventions"></a>Conventions d'affectation de noms Visual Basic
Lorsque vous nommez un élément dans votre application Visual Basic, le premier caractère de ce nom doit être un caractère alphabétique ou un trait de soulignement. Toutefois, notez que les noms commençant par un trait de soulignement ne sont pas compatibles avec la [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS).  
  
 Les suggestions suivantes s’appliquent aux noms.  
  
-   Commencer chaque mot distinct d’un nom par une lettre majuscule, comme dans `FindLastRecord` et `RedrawMyForm`.  
  
-   Commencer les noms de fonction et de méthode avec un verbe, comme dans `InitNameArray` ou `CloseDialog`.  
  
-   Commencer la classe, structure, module et noms de propriété avec un nom, comme dans `EmployeeName` ou `CarAccessory`.  
  
-   Commencer les noms d’interface avec le préfixe « I », suivi par un nom ou une expression nominale, tel que `IComponent`, ou d’un adjectif décrivant le comportement de l’interface, comme `IPersistable`. Évitez d’utiliser le trait de soulignement et utilisez les abréviations modérément, car les abréviations peuvent entraîner une confusion.  
  
-   Commencer les noms de gestionnaires d’événements avec un nom qui décrit le type d’événement suivi par la «`EventHandler`« de suffixe, comme dans »`MouseEventHandler`».  
  
-   Dans les noms de classes d’argument d’événement, ajoutez le «`EventArgs`» suffixe.  
  
-   Si un événement a un concept de « before » ou « after », utilisez un suffixe dans le présent ou le passé, comme dans «`ControlAdd`« ou »`ControlAdded`».  
  
-   Pour les termes longs ou fréquemment utilisés, utilisez des abréviations pour limiter la longueur, par exemple, « HTML », au lieu de « Hypertext Markup Language ». En général, les noms de variables de plus de 32 caractères sont difficiles à lire sur un écran avec une faible résolution. Assurez-vous également que vos abréviations sont cohérentes dans toute l’application. Basculement de façon aléatoire dans un projet entre « HTML » et « Hypertext Markup Language » peut prêter à confusion.  
  
-   Évitez d’utiliser des noms dans une portée interne qui sont les mêmes que les noms dans une portée externe. Erreurs peuvent résulter si la variable incorrecte est accessible. En cas de conflit entre une variable et le mot clé portant le même nom, vous devez identifier le mot clé en la faisant précéder de la bibliothèque de types appropriée. Par exemple, si vous disposez d’une variable appelée `Date`, vous pouvez utiliser la fonction intrinsèque `Date` fonction uniquement en appelant <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des mots clés comme noms d’éléments dans le code](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 [Me, My, MyBase et MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Structure de programme et conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Informations de référence sur le langage Visual Basic](../../../visual-basic/language-reference/index.md)
