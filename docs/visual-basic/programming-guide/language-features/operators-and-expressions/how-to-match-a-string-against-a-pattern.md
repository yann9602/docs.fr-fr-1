---
title: "How to: Match a String against a Pattern (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "comparison operators, comparing strings"
  - "pattern matching"
  - "strings [Visual Basic], comparing"
  - "string comparison [Visual Basic], operators"
  - "Visual Basic code, operators"
  - "pattern matching, string comparison"
  - "string comparison [Visual Basic]"
  - "Like operator [Visual Basic], pattern matching"
  - "pattern matching, empty strings"
  - "operators [Visual Basic], comparison"
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Match a String against a Pattern (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Pour déterminer si une expression du [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) est conforme à un modèle, vous pouvez utiliser le [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
 `Like` accepte deux opérandes.  L'opérande gauche est une expression de chaîne, et l'opérande droite est une chaîne qui contient le modèle à utiliser pour la correspondance.  `Like` retourne une valeur `Boolean` indiquant si l'expression de chaîne est conforme ou non au modèle.  
  
 Vous pouvez faire correspondre chaque caractère de l'expression de chaîne avec un caractère spécifique, un caractère générique, une liste de caractères ou une plage de caractères.  Les positions des spécifications dans la chaîne de masque correspondent aux positions des caractères de correspondance dans l'expression de chaîne.  
  
### Pour faire correspondre un caractère de l'expression de chaîne avec un caractère spécifique  
  
-   Mettez directement le caractère spécifique dans la chaîne de masque.  Certains caractères spéciaux doivent être entourés par des crochets \(`[ ]`\).  Pour plus d'informations, consultez [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
     L'exemple suivant teste si `myString` se compose exactement du caractère unique `H`.  
  
     [!code-vb[VbVbalrOperators#70](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_1.vb)]  
  
### Pour faire correspondre un caractère de l'expression de chaîne avec un caractère générique  
  
-   Mettez un point d'interrogation \(`?`\) dans la chaîne de masque.  Tout caractère valide dans cette position est mis en correspondance.  
  
     L'exemple suivant teste si `myString` se compose du caractère unique `W`, suivi exactement de deux caractères d'une valeur quelconque.  
  
     [!code-vb[VbVbalrOperators#71](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_2.vb)]  
  
### Pour faire correspondre un caractère de l'expression de chaîne avec une liste de caractères  
  
-   Mettez des crochets \(`[ ]`\) dans la chaîne de masque, et insérez la liste de caractères à l'intérieur des crochets.  Ne séparez pas les caractères par des virgules ou tout autre séparateur.  Tout caractère unique de la liste est mis en correspondance.  
  
     L'exemple suivant teste si `myString` se compose d'un caractère valide, suivi exactement de l'un des caractères `A`, `C` ou `E`.  
  
     [!code-vb[VbVbalrOperators#72](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_3.vb)]  
  
     Notez que cette mise en correspondance respecte la casse.  
  
### Pour faire correspondre un caractère de l'expression de chaîne avec une plage de caractères  
  
-   Mettez des crochets \(`[ ]`\) dans la chaîne de masque, et à l'intérieur des crochets, mettez les caractères supérieur et inférieur de la plage, séparés par un trait d'union \(`–`\).  Tout caractère unique de la plage est mis en correspondance.  
  
     L'exemple suivant teste si `myString` se compose des caractères `num`, suivis exactement de l'un des caractères `i`, `j`, `k`, `l`, `m` ou `n`.  
  
     [!code-vb[VbVbalrOperators#73](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_4.vb)]  
  
     Notez que cette mise en correspondance respecte la casse.  
  
## Mise en correspondance de chaînes vides  
 `Like` traite la séquence `[]` comme une chaîne de longueur nulle \(`""`\).  Vous pouvez utiliser `[]` pour tester si l'expression de chaîne entière est vide, mais vous ne pouvez pas l'utiliser pour tester si une position particulière de l'expression de chaîne est vide.  Si une position vide est l'une des options que vous devez tester, vous pouvez utiliser `Like` plusieurs fois.  
  
#### Pour faire correspondre un caractère de l'expression de chaîne avec une liste de caractères ou aucun caractère  
  
1.  Appelez deux fois l'opérateur `Like` la même expression de chaîne et connectez les deux appels avec [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) ou [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
2.  Dans la chaîne de masque de la première clause `Like`, incluez la liste de caractères, entourée par des crochets \(`[ ]`\).  
  
3.  Dans la chaîne de masque de la deuxième clause `Like`, ne mettez pas de caractères à la position concernée.  
  
     L'exemple suivant teste le numéro de téléphone à sept chiffres `phoneNum` pour exactement trois chiffres, suivis d'un espace, d'un trait d'union \(`–`\), d'un point \(`.`\) ou d'aucun caractère, suivi d'exactement quatre chiffres.  
  
     [!code-vb[VbVbalrOperators#74](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_5.vb)]  
  
## Voir aussi  
 [Comparison Operators](../../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Operators and Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md)   
 [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md)