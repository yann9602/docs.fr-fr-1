---
title: "Special Characters in Code (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.)"
  - "vb.("
  - "vb.colon"
  - "vb.!"
  - "vb.."
  - "vb.:"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "special characters, in code"
  - "parentheses, using in code"
  - "colons (:)"
  - "period character in code"
  - "dot operator (.)"
  - "dictionary access operator"
  - "concatenation operators, special characters in code"
  - "concatenation operators, vs. addition operator"
  - "! operator"
  - "separators, using in code"
  - "operators [Visual Basic], dictionary access"
  - ": separator character"
  - "member access operator"
  - "addition operator"
  - "operators [Visual Basic], member access"
  - ". operator"
  - "exclamation points"
  - "separators"
  - "exclamation point operator (!)"
  - "Visual Basic code, special characters"
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Special Characters in Code (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Vous devez quelquefois utiliser des caractères spéciaux dans votre code, autrement dit, des caractères qui ne sont pas alphabétiques ou numériques.  La ponctuation et les caractères spéciaux du jeu de caractères [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ont plusieurs utilisations, qui varient de l'organisation du texte de programme à la définition des tâches effectuées par le compilateur ou le programme compilé.  Ils ne spécifient pas d'opération à effectuer.  
  
## Parenthèses  
 Vous utilisez des parenthèses lorsque vous définissez une procédure, par exemple un `Sub` ou `Function`.  Vous devez placer les listes des arguments de la procédure entre parenthèses.  Vous utilisez également des parenthèses pour insérer des variables ou des arguments dans des groupes logiques, en particulier pour substituer l'ordre de priorité des opérateurs par défaut dans une expression complexe.  L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbcnConventions#11](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/special-characters-in-code_1.vb)]  
  
 Après l'exécution du code précédent, `d` a la valeur 8.225 et `e` a la valeur 3.  Le calcul de `d` utilise la priorité par défaut de `/` sur `+` et équivaut à `d = b + (c / a)`.  Les parenthèses dans le calcul de `e` substituent la priorité par défaut.  
  
## Séparateurs  
 Comme leur nom l'indique, les séparateurs séparent les différentes sections de code.  En [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)], c'est le signe deux\-points \(`:`\) qui est le caractère séparateur.  Utilisez des séparateurs lorsque vous voulez inclure plusieurs instructions sur une ligne unique au lieu de lignes séparées.  Vous économisez ainsi de l'espace et améliorez la lisibilité de votre code.  Dans l'exemple ci\-dessous, trois instructions sont séparées par un signe deux\-points.  
  
 [!code-vb[VbVbcnConventions#12](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/special-characters-in-code_2.vb)]  
  
 Pour plus d'informations, consultez [Procédure : diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
 Le signe deux\-points \(`:`\) est également utilisé pour identifier une étiquette d'instruction.  Pour plus d'informations, consultez [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
## Concaténation  
 Utilisez l'opérateur `&` pour créer une *concaténation*, c'est\-à\-dire lier plusieurs chaînes.  Ne confondez pas cet opérateur avec l'opérateur `+`, qui permet d'ajouter des valeurs numériques.  Si vous utilisez l'opérateur `+` pour créer une concaténation de valeurs numériques, vous risquez d'obtenir des résultats incorrects.  C'est ce qu'illustre l'exemple suivant.  
  
 [!code-vb[VbVbcnConventions#13](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/special-characters-in-code_3.vb)]  
  
 Après l'exécution du code précédent, `resultA` a la valeur 21.01 et `resultB` a la valeur 10.0111.  
  
## Opérateurs d'accès au membre  
 Pour accéder à un membre d'un type, utilisez le point \(`.`\) ou le point d'exclamation \(`!`\) comme opérateur entre le nom de type et le nom de membre.  
  
### Point \(.\) Opérateur  
 Utilisez l'opérateur `.` sur une classe, une structure, une interface ou une énumération en tant qu'opérateur d'accès au membre.  Le membre peut être un champ, une propriété, un événement ou une méthode.  L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbcnConventions#14](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/special-characters-in-code_4.vb)]  
  
### Point d'exclamation \(\!\) Opérateur  
 Utilisez l'opérateur `!` uniquement dans une classe ou une interface en tant qu'opérateur d'accès de type dictionnaire.  La classe ou l'interface doit avoir une propriété par défaut qui accepte un seul argument `String`.  L'identificateur qui suit immédiatement l'opérateur `!` devient la valeur de l'argument transmis en tant que string pour la propriété par défaut.  C'est ce qu'illustre l'exemple suivant.  
  
 [!code-vb[VbVbcnConventions#15](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/special-characters-in-code_5.vb)]  
  
 Toutes les trois lignes de sortie de `MsgBox` affichent la valeur `32856`.  La première ligne utilise l'accès traditionnel à la propriété `index`, la seconde utilise le fait que `index` est la propriété par défaut de la classe `hasDefault` et la troisième utilise l'accès de type dictionnaire à la classe.  
  
 Notez que le second opérande de l'opérateur `!` doit être un identificateur Visual Basic valide qui n'est pas entouré par des guillemets doubles \(`" "`\).  En d'autres termes, vous ne pouvez pas utiliser un littéral de chaîne ou une variable chaîne.  La modification ci\-dessous à la dernière ligne de l'appel `MsgBox` génère une erreur parce que `"X"` est un littéral de chaîne entouré par des guillemets.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  Les références aux collections par défaut doivent être explicites.  En particulier, vous ne pouvez pas utiliser l'opérateur `!` dans une variable à liaison tardive.  
  
 Le signe `!` est également utilisé comme le caractère de type `Single`.  
  
## Voir aussi  
 [Structure de programme et conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)