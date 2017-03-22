---
title: Structures et Classes (Visual Basic) | Documents Microsoft
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
- classes [Visual Basic], vs. structures
- structures
- classes [Visual Basic]
- structures, compared to classes
- structures, structure variables
- structure variables
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
caps.latest.revision: 21
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
ms.openlocfilehash: e7402ec0fcfc279470d39a4919d3b5ec8b5d9dff
ms.lasthandoff: 03/13/2017

---
# <a name="structures-and-classes-visual-basic"></a>Structures et classes (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]unifie la syntaxe des structures et des classes, avec pour conséquence que les deux entités prennent en charge les mêmes fonctionnalités. Toutefois, il existe également des différences importantes entre les classes et structures.  
  
 Classes ont l’avantage d’être des types référence, en passant une référence est plus efficace de passer une variable de structure avec toutes ses données. En revanche, les structures ne nécessitent pas l’allocation de mémoire sur le tas global.  
  
 Car il ne peut pas hériter d’une structure, structures doivent être utilisées uniquement pour les objets qui ne doivent pas être étendu. Utilisez les structures lorsque l’objet que vous souhaitez créer a une taille d’instance réduite et prendre en compte les caractéristiques de performances des classes et structures.  
  
## <a name="similarities"></a>Points communs  
 Les classes et les structures sont similaires aux points suivants :  
  
-   Les deux sont *conteneur* types, ce qui signifie qu’ils contiennent d’autres types en tant que membres.  
  
-   Elles ont des membres comprenant des constructeurs, méthodes, propriétés, champs, des constantes, énumérations, événements et gestionnaires d’événements. Toutefois, ne confondez pas ces membres avec les déclaré *éléments* d’une structure.  
  
-   Leurs membres peuvent avoir individualisée des niveaux d’accès. Par exemple, un membre peut être déclaré `Public` et un autre `Private`.  
  
-   Les deux peuvent implémenter des interfaces.  
  
-   Les deux peuvent avoir des constructeurs partagés, avec ou sans paramètres.  
  
-   Elles peuvent exposer une *propriété par défaut*, sous réserve que la propriété prenne au moins un paramètre.  
  
-   Elles peuvent déclarer et déclencher des événements, et déclarer des délégués.  
  
## <a name="differences"></a>Différences  
 Structures et classes diffèrent dans les indications suivantes :  
  
-   Les structures sont *des types valeur*; les classes sont *types référence*. Une variable d’un type structure contient les données de la structure, plutôt que contenant une référence aux données comme un type de classe.  
  
-   Les structures utilisent l’allocation de pile ; les classes utilisent l’allocation de tas.  
  
-   Tous les éléments de structure sont `Public` par défaut ; classe variables et constantes sont `Private` par défaut, tandis que d’autres membres de classe sont `Public` par défaut. Ce comportement pour les membres de classe assure la compatibilité avec le système de Visual Basic 6.0 de valeurs par défaut.  
  
-   Une structure doit contenir au moins un non partagé, ou variable non partagée élément d’événement ; une classe peut être entièrement vide.  
  
-   Éléments de structure ne peuvent pas être déclarés en tant que `Protected`; peuvent des membres de classe.  
  
-   Une procédure de structure peut gérer des événements uniquement s’il est un [partagé](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` procédure et uniquement au moyen de la [AddHandler, instruction](../../../../visual-basic/language-reference/statements/addhandler-statement.md); toute procédure de classe peut gérer des événements à l’aide la [gère](../../../../visual-basic/language-reference/statements/handles-clause.md) (mot clé) ou le `AddHandler` instruction. Pour plus d’informations, consultez [événements](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
-   Les déclarations de variable de structure ne peut pas spécifier initialiseurs ni les tailles initiales des tableaux ; les déclarations de variable de classe peuvent.  
  
-   Les structures héritent implicitement de la <xref:System.ValueType?displayProperty=fullName>classe et ne peut pas hériter d’un autre type ; classes peuvent hériter d’une classe ou d’une classe autre que <xref:System.ValueType?displayProperty=fullName>.</xref:System.ValueType?displayProperty=fullName> </xref:System.ValueType?displayProperty=fullName>  
  
-   Structures ne sont pas héritées ; les classes sont.  
  
-   Les structures n’étant jamais arrêtées, le common language runtime (CLR) n’appelle jamais la <xref:System.Object.Finalize%2A>méthode sur une structure ; les classes sont arrêtées par le garbage collector (GC), qui appelle <xref:System.Object.Finalize%2A>sur une classe lorsqu’il ne détecte aucune référence active restante.</xref:System.Object.Finalize%2A> </xref:System.Object.Finalize%2A>  
  
-   Une structure ne nécessite pas un constructeur ; une classe fait.  
  
-   Les structures peuvent avoir des constructeurs non partagés uniquement lorsqu’ils acceptent des paramètres. classes peuvent avoir leur avec ou sans paramètres.  
  
 Chaque structure possède un constructeur public implicite sans paramètres. Ce constructeur initialise les éléments de données de toute la structure à leurs valeurs par défaut. Vous ne pouvez pas modifier ce comportement.  
  
## <a name="instances-and-variables"></a>Instances et Variables  
 Étant donné que les structures sont des types valeur, chaque variable de structure est définitivement liée à une instance de structure individuelle. Mais les classes sont des types référence, et une variable objet peut faire référence à plusieurs instances de classe à des moments différents. Cette distinction affecte votre utilisation de structures et les classes de plusieurs façons :  
  
-   **Initialisation.** Une variable de structure comprend implicitement une initialisation des éléments à l’aide du constructeur sans paramètre de la structure. Par conséquent, `Dim s As struct1` équivaut à `Dim s As struct1 = New struct1()`.  
  
-   **Assignation de Variables.** Lorsque vous assignez une variable de structure à une autre, ou passez une instance de structure à un argument de procédure, les valeurs actuelles de tous les éléments de variable sont copiés à la nouvelle structure. Lorsque vous assignez une variable d’objet à un autre, ou passez une variable objet à une procédure, seul le pointeur de la référence est copié.  
  
-   **Assignation de Nothing.** Vous pouvez affecter la valeur [rien](../../../../visual-basic/language-reference/nothing.md) à une structure variable, mais l’instance continue à associer à la variable. Vous pouvez toujours appeler ses méthodes et accéder à ses éléments de données, bien que les éléments de variable sont réinitialisés par l’assignation.  
  
     En revanche, si vous définissez une variable objet à `Nothing`, vous lui assigniez à partir de n’importe quelle instance de classe et vous ne pouvez pas accéder aux membres via la variable jusqu'à ce que vous lui affectez une autre instance.  
  
-   **Plusieurs Instances.** Une variable objet peut avoir diverses instances de classe attribués à des moments différents, et plusieurs variables d’objet peuvent faire référence à la même instance de classe en même temps. Modifications apportées aux valeurs des membres de classe affectent ces membres lorsque pour accéder à une autre variable pointant vers la même instance.  
  
     Toutefois, les éléments de structure, sont isolés dans leur propre instance. Modifications apportées à leurs valeurs ne sont pas répercutées dans d’autres variables de structure, même dans les autres instances du même `Structure` déclaration.  
  
-   **Égalité.** Tester l’égalité de deux structures doit être effectué sur un élément par élément. Deux variables d’objet peuvent être comparées à l’aide de la <xref:System.Object.Equals%2A>méthode.</xref:System.Object.Equals%2A> <xref:System.Object.Equals%2A>Indique si les deux variables pointent vers la même instance.</xref:System.Object.Equals%2A>  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Types de données composites](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Types valeur et Types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Dépannage des Types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Structures et autres éléments de programmation](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)   
 [Objets et classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
