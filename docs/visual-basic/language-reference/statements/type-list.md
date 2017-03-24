---
title: "Type List (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "StructureConstraint"
  - "vb.StructureConstraint"
  - "ClassConstraint"
  - "vb.ClassConstraint"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "class constraint"
  - "constraints, Visual Basic generic types"
  - "generic parameters"
  - "generics [Visual Basic], constraints"
  - "generics [Visual Basic], type list"
  - "structure constraint"
  - "constraints, in type parameters"
  - "generics [Visual Basic], generic types"
  - "parameters, type"
  - "constraints, Structure keyword"
  - "type parameters, constraints"
  - "types [Visual Basic], generic"
  - "parameters, generic"
  - "generics [Visual Basic], type parameters"
  - "type parameters"
  - "constraints, Class keyword"
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
caps.latest.revision: 33
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 33
---
# Type List (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie les *paramètres de type* pour un élément de programmation *générique*.  Les paramètres, lorsqu'il y en a plusieurs, sont séparés par des virgules.  La syntaxe pour un paramètre de type est la suivante.  
  
## Syntaxe  
  
```  
  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`genericmodifier`|Facultatif.  Peut être utilisé uniquement dans les interfaces et les délégués génériques.  Vous pouvez déclarer un covariant de type en utilisant le mot clé [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) ou un contravariant en utilisant le mot clé  [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md).  Consultez [Covariance et contravariance](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md).|  
|`typename`|Obligatoire.  Nom du paramètre de type.  C'est un espace réservé, à remplacer par un type défini fourni par l'argument de type correspondant.|  
|`constraintlist`|Facultatif.  Liste des configurations requises qui contraignent le type de données qui peut être fourni pour `typename`.  Si vous avez plusieurs contraintes, placez\-les entre accolades \(`{ }`\) et séparez\-les avec des virgules.  Vous devez introduire la liste des contraintes avec le mot clé [As](../../../visual-basic/language-reference/statements/as-clause.md).  Utilisez `As` une seule fois, au début de la liste.|  
  
## Notes  
 Chaque élément de programmation générique doit au moins prendre un paramètre de type.  Un paramètre de type est un espace réservé pour un type spécifique \(un *élément construit*\) que le code client spécifie lorsqu'il crée une instance du type générique.  Vous pouvez définir une classe, une structure, une interface, une procédure ou un délégué générique.  
  
 Pour plus d'informations sur le moment où un type générique doit être défini, consultez [Types génériques Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).  Pour plus d'informations sur les noms de paramètres de type, consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## Règles  
  
-   **Parenthèses.** Si vous fournissez une liste de paramètres de type, vous devez la placer entre parenthèses, et vous devez introduire la liste avec le mot clé [Of](../../../visual-basic/language-reference/statements/of-clause.md).  Utilisez `Of` une seule fois, au début de la liste.  
  
-   **Contraintes.** Une liste de  *contraintes* sur un paramètre de type peut inclure les éléments suivants selon n'importe quelle combinaison :  
  
    -   N'importe quel nombre d'interfaces.  Le type fourni doit implémenter toutes les interfaces de cette liste.  
  
    -   Une classe au plus.  Le type fourni doit hériter de cette classe.  
  
    -   Le mot clé `New`.  Le type fourni doit exposer un constructeur sans paramètre auquel votre type générique peut accéder.  Cette opération est utile si vous contraignez un paramètre de type par une ou plusieurs interfaces.  Un type qui implémente des interfaces n'expose pas nécessairement de constructeur, et selon le niveau d'accès d'un constructeur, il est possible que le code dans le type générique ne puisse pas y accéder.  
  
    -   Le mot clé `Class` ou `Structure`.  Le mot clé `Class` contraint un paramètre de type générique à requérir que tout argument de type qui lui est passé soit un type référence, par exemple une chaîne, un tableau ou un délégué, ou un objet créé à partir d'une classe.  Le mot clé `Structure` contraint un paramètre de type générique à requérir que tout argument de type qui lui est passé soit un type valeur, par exemple une structure, une énumération ou un type de données élémentaire.  Vous ne pouvez pas inclure à la fois `Class` et `Structure` dans le même `constraintlist`.  
  
     Le type fourni doit satisfaire chaque configuration requise que vous incluez dans `constraintlist`.  
  
     Les contraintes sur chaque paramètre de type sont indépendantes des contraintes sur les autres paramètres de type.  
  
## Comportement  
  
-   **Substitution au moment de la compilation.** Lorsque vous créez un type construit à partir d'un élément de programmation générique, fournissez un type défini pour chaque paramètre de type.  Le compilateur Visual Basic substitue ce type fourni pour chaque occurrence de `typename` dans l'élément générique.  
  
-   **Absence de contraintes.** Si vous ne spécifiez pas de contraintes sur un paramètre de type, votre code est limité aux opérations et aux membres pris en charge par le [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md) pour ce paramètre.  
  
## Exemple  
 L'exemple suivant affiche une définition squelette d'une classe de dictionnaire générique, y compris une fonction squelette pour ajouter une nouvelle entrée au dictionnaire.  
  
 [!code-vb[VbVbalrStatements#3](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_1.vb)]  
  
## Exemple  
 Étant donné que `dictionary` est générique, le code qui l'utilise peut créer divers objets à partir de celui\-ci, chacun disposant des mêmes fonctionnalités, mais agissant sur un type de données différent.  L'exemple suivant affiche une ligne de code qui crée un objet `dictionary` avec les entrées `String` et les clés `Integer`.  
  
 [!code-vb[VbVbalrStatements#4](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_2.vb)]  
  
## Exemple  
 L'exemple suivant affiche la définition squelette équivalente générée par l'exemple précédent.  
  
 [!code-vb[VbVbalrStatements#5](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_3.vb)]  
  
## Voir aussi  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)   
 [New Operator](../../../visual-basic/language-reference/operators/new-operator.md)   
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Comment : utiliser une classe générique](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Covariance et contravariance](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)   
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)