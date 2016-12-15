---
title: "Structures and Classes (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "classes [Visual Basic], vs. structures"
  - "structures"
  - "classes [Visual Basic]"
  - "structures, compared to classes"
  - "structures, structure variables"
  - "structure variables"
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Structures and Classes (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] unifie la syntaxe des structures et des classes, ce qui permet aux deux entités de prendre en charge quasiment les mêmes fonctionnalités.  Toutefois, il traite également des principales différences existant entre les classes et les structures.  
  
 Les classes ont l'avantage d'être des types référence \(il est plus efficace de passer une référence qu'une variable de structure avec toutes ses données\).  D'un autre côté, les structures n'exigent pas d'allocation de mémoire dans le tas global.  
  
 Parce que vous ne pouvez pas hériter d'elles, les structures ne doivent être utilisées que pour les objets qui n'ont pas besoin d'être étendus.  Utilisez les structures lorsque l'objet que vous souhaitez créer a une taille d'instance réduite et tenez compte des caractéristiques de performances des classes par rapport à celles des structures.  
  
## Similitudes  
 Les structures et les classes sont identiques à plusieurs égards :  
  
-   elles représentent des types *conteneurs*, ce qui signifie qu'elles peuvent contenir d'autres types comme membres ;  
  
-   elles ont des membres qui peuvent comprendre des constructeurs, des méthodes, des propriétés, des champs, des constantes, des énumérations, des événements et des gestionnaires d'événements ;  Toutefois, ne confondez pas ces membres avec les *éléments* déclarés d'une structure ;  
  
-   leurs membres peuvent présenter des niveaux d'accès individualisés.  Par exemple, un membre peut être déclaré `Public` et un autre `Private` ;  
  
-   elles peuvent implémenter des interfaces ;  
  
-   elles peuvent avoir des constructeurs partagés, avec ou sans paramètres.  
  
-   elles peuvent exposer une *propriété par défaut*, à condition que celle\-ci accepte au moins un paramètre ;  
  
-   elles peuvent déclarer et déclencher des événements, et déclarer des délégués.  
  
## Différences  
 Les structures et les classes diffèrent à plusieurs égards :  
  
-   les structures sont des *types valeur* ; les classes sont des *types référence*.  Une variable d'un type structure contient les données de la structure, plutôt qu'une référence aux données comme le fait un type classe ;  
  
-   les structures utilisent l'allocation de la pile, les classes l'allocation de tas ;  
  
-   tous les éléments de structure sont `Public` par défaut, les variables et les constantes de classe sont `Private` par défaut, tandis que les autres membres de classe sont `Public` par défaut.  Ce comportement pour les membres de classe assure la compatibilité avec le système de valeurs par défaut Visual Basic 6.0 ;  
  
-   une structure doit contenir au moins une variable non partagée ou un élément événement non personnalisé et non partagé, alors qu'une classe peut être entièrement vide ;  
  
-   les éléments de structure ne peuvent pas être déclarés comme `Protected`, contrairement aux membres de classe ;  
  
-   Une procédure de structure peut gérer des événements uniquement s'il s'agit d'une procédure [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` et qu'elle utilise l'[AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) ; toute procédure de classe peut gérer des événements avec le mot clé [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) ou l'instruction `AddHandler`.  Pour plus d'informations, consultez [Events](../../../../visual-basic/programming-guide/language-features/events/events.md).  
  
-   les déclarations de variable de structure ne peuvent pas spécifier d'initialiseurs ni les tailles initiales des tableaux, contrairement aux déclarations de variable de classe ;  
  
-   les structures héritent implicitement de la classe <xref:System.ValueType?displayProperty=fullName> et ne peuvent pas hériter d'un autre type, tandis que les classes peuvent hériter d'une ou plusieurs classes autres que <xref:System.ValueType?displayProperty=fullName> ;  
  
-   il est possible d'hériter des classes, mais pas des structures ;  
  
-   les structures n'étant jamais arrêtées, le Common Language Runtime \(CLR\) n'appelle jamais la méthode <xref:System.Object.Finalize%2A> sur une structure ; les classes sont arrêtées par le « garbage collector », qui appelle <xref:System.Object.Finalize%2A> sur une classe lorsqu'il ne détecte aucune référence active restante ;  
  
-   une structure n'exige pas de constructeur, contrairement à une classe ;  
  
-   les structures peuvent avoir des constructeurs non partagés uniquement lorsqu'ils acceptent des paramètres, les classes peuvent en accepter avec ou sans paramètre.  
  
 Chaque structure possède un constructeur public implicite sans paramètres.  Ce constructeur initialise toutes les éléments de données de la structure en leur attribuant leurs valeurs par défaut.  Vous ne pouvez pas modifier ce comportement.  
  
## Instances et variables  
 Puisque les structures sont des types valeur, chaque variable de structure est définitivement liée à une instance de structure individuelle.  En revanche, les classes sont des types référence, et une variable d'objet peut faire référence à plusieurs instances de classe à différents moments.  Cette distinction affecte votre utilisation de structures et de classes de diverses façons :  
  
-   **Initialisation.** Une variable de structure comprend implicitement une initialisation des éléments à l'aide du constructeur sans paramètre de la structure.  En conséquence, `Dim s As struct1` équivaut à `Dim s As struct1 = New struct1()`.  
  
-   **Assignation de variables.** Lorsque vous assignez une variable de structure à une autre ou que vous passez une instance de structure à un argument de procédure, les valeurs actuelles de tous les éléments de variable sont copiés à la nouvelle structure.  Lorsque vous assignez une variable d'objet à une autre ou que vous passez une variable d'objet à une procédure, seul le pointeur de référence est copié.  
  
-   **Assignation de Nothing.** Vous pouvez assigner la valeur [Nothing](../../../../visual-basic/language-reference/nothing.md) à une variable de structure, mais l'instance continue à être associée à la variable.  Vous pouvez toujours appeler ses méthodes et accéder à ses éléments de données, même si les éléments de variable sont réinitialisés par l'assignation.  
  
     En revanche, si vous attribuez la valeur `Nothing` à une variable d'objet, vous la dissociez d'une instance de classe et vous ne pouvez pas accéder aux membres par l'intermédiaire de la variable jusqu'à ce que vous lui assigniez une autre instance.  
  
-   **Instances multiples.** Une variable objet peut avoir diverses instances de classe qui lui sont assignées à des moments différents et plusieurs variables objet peuvent faire référence simultanément à la même instance de classe.  Les modifications apportées aux valeurs des membres de classe affectent ces membres lorsque vous y accédez par l'intermédiaire d'une autre variable pointant vers la même instance.  
  
     Cependant, les éléments de structure sont isolés dans leur propre instance.  Les modifications apportées à leurs valeurs ne sont pas réfléchies dans d'autres variables de structure, même dans d'autres instances de la même déclaration `Structure`.  
  
-   **Égalité.** Un test d'égalité de deux structures doit être effectué sur un élément après l'autre.  Deux variables objet peuvent être comparées à l'aide de la méthode <xref:System.Object.Equals%2A>.  <xref:System.Object.Equals%2A> indique si les deux variables pointent sur la même instance.  
  
## Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Structures and Other Programming Elements](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)