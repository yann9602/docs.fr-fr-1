---
title: Structures et classes (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 08e31481feac7a6184c6b29269d193c749f440ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="structures-and-classes-visual-basic"></a>Structures et classes (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]unifie la syntaxe des structures et des classes, avec le résultat que les deux entités prennent en charge la plupart de ces fonctionnalités. Toutefois, il existe également des différences importantes entre les classes et structures.  
  
 Classes ont l’avantage d’être des types référence, en passant une référence est plus efficace de passer une variable de structure avec toutes ses données. En revanche, les structures ne nécessitent pas d’allocation de mémoire sur le tas global.  
  
 Car il ne peut pas hériter d’une structure, les structures doivent être utilisées uniquement pour les objets qui ne doivent pas être étendu. Structures utilisées lors de l’objet que vous souhaitez créer a une taille de petite instance et prendre en compte les caractéristiques de performances des classes et structures.  
  
## <a name="similarities"></a>Similitudes  
 Structures et les classes sont semblables aux points suivants :  
  
-   Les deux sont *conteneur* types, ce qui signifie que qu’ils contiennent d’autres types en tant que membres.  
  
-   Elles ont des membres qui peuvent inclure des constructeurs, méthodes, propriétés, champs, des constantes, énumérations, événements et gestionnaires d’événements. Toutefois, ne confondez pas de ces membres avec déclaré *éléments* d’une structure.  
  
-   Leurs membres peuvent avoir individualisé niveaux d’accès. Par exemple, un membre peut être déclaré `Public` et un autre `Private`.  
  
-   Les deux peuvent implémenter des interfaces.  
  
-   Les deux peuvent avoir des constructeurs partagés, avec ou sans paramètres.  
  
-   Elles peuvent exposer une *propriété par défaut*, à condition que la propriété prend au moins un paramètre.  
  
-   Elles peuvent déclarer et déclencher des événements, et déclarer des délégués.  
  
## <a name="differences"></a>Différences  
 Structures et classes diffèrent dans les indications suivantes :  
  
-   Les structures sont *types valeur*; les classes sont *types référence*. Une variable d’un type structure contient les données de la structure, plutôt que contenant une référence aux données comme un type de classe.  
  
-   Les structures utilisent l’allocation de pile ; classes utilisent l’allocation de tas.  
  
-   Tous les éléments de structure sont `Public` par défaut ; classe variables et constantes sont `Private` par défaut, tandis que d’autres membres de classe sont `Public` par défaut. Ce comportement pour les membres de classe assure la compatibilité avec le système de Visual Basic 6.0 de valeurs par défaut.  
  
-   Une structure doit avoir au moins un non partagée de variable ou non partagé, élément de l’événement ; une classe peut être entièrement vide.  
  
-   Éléments de structure ne peuvent pas être déclarés en tant que `Protected`; peuvent des membres de classe.  
  
-   Une procédure de structure peut gérer des événements uniquement s’il est un [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` procédure et uniquement à l’aide de la [AddHandler, instruction](../../../../visual-basic/language-reference/statements/addhandler-statement.md); toute procédure de classe peut gérer des événements, en utilisant soit le [ Gère les](../../../../visual-basic/language-reference/statements/handles-clause.md) mot clé ou la `AddHandler` instruction. Pour plus d’informations, consultez [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
-   Les déclarations de variable de structure ne peut pas spécifier initialiseurs ou tailles initiales pour les tableaux ; les déclarations de variable de classe peuvent.  
  
-   Les structures héritent implicitement de la <xref:System.ValueType?displayProperty=nameWithType> de classe et ne peut pas hériter d’un autre type ; les classes peuvent hériter d’une classe ou les classes autre que <xref:System.ValueType?displayProperty=nameWithType>.  
  
-   Structures ne sont pas héritées ; les classes sont.  
  
-   Les structures n’étant jamais arrêtées, le common language runtime (CLR) n’appelle jamais la <xref:System.Object.Finalize%2A> méthode sur une structure ; classes sont terminées par le garbage collector (GC), qui appelle <xref:System.Object.Finalize%2A> sur une classe quand il n’existe aucune référence active restants.  
  
-   Une structure ne nécessite pas un constructeur ; une classe fait.  
  
-   Les structures peuvent avoir des constructeurs non partagés uniquement lorsqu’ils acceptent des paramètres. les classes peuvent avoir les avec ou sans paramètres.  
  
 Chaque structure possède un constructeur public implicite sans paramètres. Ce constructeur initialise les éléments de données de toute la structure à leurs valeurs par défaut. Vous ne pouvez pas modifier ce comportement.  
  
## <a name="instances-and-variables"></a>Instances et Variables  
 Étant donné que les structures sont des types valeur, chaque variable de structure est définitivement lié à une instance de structure individuelle. Mais les classes sont des types référence, et une variable objet peut faire référence à plusieurs instances de classe à des moments différents. Cette distinction affecte votre utilisation de structures et les classes de plusieurs manières :  
  
-   **Initialisation.** Une variable de structure comprend implicitement une initialisation des éléments à l’aide du constructeur sans paramètre de la structure. Par conséquent, `Dim s As struct1` équivaut à `Dim s As struct1 = New struct1()`.  
  
-   **Assignation de Variables.** Lorsque vous assignez une variable de structure à une autre, ou passez une instance de structure à un argument de procédure, les valeurs actuelles de tous les éléments de variable sont copiés vers la nouvelle structure. Lorsque vous assignez une variable objet à une autre, ou passez une variable objet à une procédure, seul le pointeur de la référence est copié.  
  
-   **Assignation de Nothing.** Vous pouvez affecter la valeur [rien](../../../../visual-basic/language-reference/nothing.md) vers une structure de variable, mais l’instance continue à associer à la variable. Vous pouvez toujours appeler ses méthodes et accéder à ses éléments de données, bien que les éléments de variable sont réinitialisés par l’assignation.  
  
     En revanche, si vous définissez une variable objet `Nothing`, vous lui assigniez à partir de n’importe quelle instance de la classe, et vous ne pouvez pas accéder aux membres via la variable jusqu'à ce que vous lui affectez une autre instance.  
  
-   **Plusieurs Instances.** Une variable objet peut avoir diverses instances de classe affectés à des moments différents, et plusieurs variables d’objet peuvent faire référence à la même instance de classe en même temps. Modifications apportées aux valeurs des membres de classe affectent ces membres lors de l’accès via une autre variable pointant vers la même instance.  
  
     Toutefois, les éléments de structure sont isolés dans leur propre instance. Modifications apportées à leurs valeurs ne sont pas reflétées dans d’autres variables de structure, même dans les autres instances du même `Structure` déclaration.  
  
-   **Égalité.** Tester l’égalité de deux structures doit être effectué sur un élément par élément. Deux variables objet peuvent être comparées à l’aide de la <xref:System.Object.Equals%2A> (méthode). <xref:System.Object.Equals%2A>Indique si les deux variables pointent vers la même instance.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Types de données composites](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Dépannage des types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Structures et autres éléments de programmation](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [Objets et classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
