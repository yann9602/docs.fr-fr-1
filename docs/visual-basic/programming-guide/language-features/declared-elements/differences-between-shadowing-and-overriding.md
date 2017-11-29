---
title: "Différences entre l'occultation et la substitution (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d67486d9c6af96d314abad7142ba86779d74f5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>Différences entre l'occultation et la substitution (Visual Basic)
Lorsque vous définissez une classe qui hérite d’une classe de base, vous souhaitez parfois redéfinir une ou plusieurs des éléments de la classe de base dans la classe dérivée. Occultation et substitution sont disponibles à cet effet.  
  
## <a name="comparison"></a>Comparaison  
 Occultation et substitution sont utilisés lorsqu’une classe dérivée hérite d’une classe de base et redéfinissent un élément déclaré par un autre. Mais il existe des différences significatives entre les deux.  
  
 Le tableau suivant compare l’occultation et substitution.  
  
||||  
|---|---|---|  
|Point de comparaison|Clichés instantanés|Substitution|  
|Objectif|Protège contre une modification de classe de base suivante qui introduit un membre que vous avez déjà défini dans votre classe dérivée|Atteint le polymorphisme en définissant une implémentation différente d’une procédure ou une propriété avec la même séquence d’appel<sup>1</sup>|  
|Élément redéfini|Un type d’élément déclaré|Seule une procédure (`Function`, `Sub`, ou `Operator`) ou une propriété|  
|Élément redéfinissant|Un type d’élément déclaré|Seulement une procédure ou une propriété avec la séquence d’appel identiques<sup>1</sup>|  
|Niveau d’accès de l’élément redéfinissant|Niveau d’accès|Impossible de modifier le niveau d’accès de l’élément substitué|  
|Lecture et écriture de l’élément redéfinissant|N’importe quelle combinaison|Impossible de changer la lisibilité ou écriture de la propriété substituée|  
|Contrôle sur la redéfinition|Élément de la classe de base ne peut pas appliquer ou interdire l’occultation|Élément de la classe de base peut spécifier `MustOverride`, `NotOverridable`, ou`Overridable`|  
|Utilisation du mot clé|`Shadows`recommandé dans la classe dérivée ; `Shadows` pris par défaut si aucune `Shadows` ni `Overrides` spécifié<sup>2</sup>|`Overridable`ou `MustOverride` requis dans la classe de base ; `Overrides` requis dans la classe dérivée|  
|Héritage de l’élément redéfinissant par les classes dérivées de votre classe dérivée|Occultation d’élément héritée en plus des classes dérivées ; élément occulté toujours masqué<sup>3</sup>|Élément substituant hérité en plus des classes dérivées ; élément substitué toujours substitué|  
  
 <sup>1</sup> le *la séquence d’appel* se compose du type d’élément (`Function`, `Sub`, `Operator`, ou `Property`), nom de la liste de paramètres et type de retour. Vous ne pouvez pas substituer une procédure avec une propriété ou l’autre sens. Vous ne pouvez pas remplacer un genre de procédure (`Function`, `Sub`, ou `Operator`) avec un autre type.  
  
 <sup>2</sup> si vous ne spécifiez pas `Shadows` ou `Overrides`, le compilateur émet un message d’avertissement pour vous aider à vérifier le genre de redéfinition que vous souhaitez utiliser. Si vous ignorez l’avertissement, le mécanisme d’occultation est utilisé.  
  
 <sup>3</sup> si l’élément d’occultation est inaccessible dans une classe plus dérivée, l’occultation n’est pas hérité. Par exemple, si vous déclarez l’élément d’occultation comme `Private`, une classe dérivant de votre classe dérivée hérite de l’élément d’origine au lieu de l’élément d’occultation.  
  
## <a name="guidelines"></a>Recommandations  
 Vous utilisez normalement la substitution dans les cas suivants :  
  
-   Vous définissez des classes dérivées polymorphes.  
  
-   Vous souhaitez que la sécurité du compilateur appliquer le type d’élément identiques et la séquence d’appel.  
  
 Vous utilisez normalement l’occultation dans les cas suivants :  
  
-   Vous pensez que votre classe de base peut être modifiée et définir un élément à l’aide du même nom que le vôtre.  
  
-   Vous souhaitez que la possibilité de modifier le type d’élément ou de la séquence d’appel.  
  
## <a name="see-also"></a>Voir aussi  
 [Références aux éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Occultation dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Guide pratique : masquer une variable portant le même nom que votre variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [Guide pratique : masquer une variable héritée](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [Guide pratique : accéder à une variable masquée par une classe dérivée](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
