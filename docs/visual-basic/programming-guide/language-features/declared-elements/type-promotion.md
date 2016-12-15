---
title: "Type Promotion (Visual Basic) | Microsoft Docs"
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
  - "declared elements, scope"
  - "visibility, declared elements"
  - "Partial keyword, unexpected results with type promotion"
  - "scope, declared elements"
  - "scope, Visual Basic"
  - "type promotion"
  - "declared elements, visibility"
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Type Promotion (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Lorsque vous déclarez un élément de programmation dans un module, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] élève sa portée vers l'espace de noms contenant le module.  Ce concept porte le nom de *promotion de type*.  
  
 L'exemple suivant montre une définition squelette d'un module et de deux membres de ce module.  
  
 [!code-vb[VbVbalrDeclaredElements#1](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]  
  
 Dans `projModule`, les éléments de programmation déclarés au niveau du module sont promus vers `projNamespace`.  Dans l'exemple précédent, `basicEnum` et `innerClass` sont promus, mais `numberSub` ne l'est pas, parce qu'il n'est pas déclaré au niveau du module.  
  
## Effet de la promotion de type  
 Grâce à la promotion de type, une chaîne de qualification n'a pas besoin d'inclure le nom du module.  L'exemple suivant effectue deux appels à la procédure de l'exemple précédent.  
  
 [!code-vb[VbVbalrDeclaredElements#2](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]  
  
 Dans l'exemple précédent, le premier appel utilise des chaînes de qualification complètes.  Toutefois, cela n'est pas nécessaire du fait de la promotion de type.  Le deuxième appel accède également aux membres du module sans inclure `projModule` dans les chaînes de qualification.  
  
## Invalidation de la promotion de type  
 Si l'espace de noms possède déjà un membre portant le même nom qu'un membre de module, la promotion de type est invalidée pour ce membre de module.  L'exemple suivant montre une définition squelette d'une énumération et d'un module dans le même espace de noms.  
  
 [!code-vb[VbVbalrDeclaredElements#3](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]  
  
 Dans l'exemple précédent, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne peut pas promouvoir la classe `abc` vers `thisNameSpace` parce qu'il existe déjà une énumération du même nom au niveau de l'espace de noms.  Pour accéder à `abcSub`, vous devez utiliser la chaîne de qualification complète `thisNamespace.thisModule.abc.abcSub`.  Toutefois, la classe `xyz` est promue et vous pouvez accéder à `xyzSub` à l'aide de la chaîne de qualification plus courte `thisNamespace.xyz.xyzSub`.  
  
### Invalidation de la promotion de type pour les types partiels  
 Si une classe ou une structure à l'intérieur d'un module utilise le mot clé [Partial](../../../../visual-basic/language-reference/modifiers/partial.md), la promotion de type est automatiquement invalidée pour cette classe ou cette structure, que l'espace de noms possède ou non un membre du même nom.  D'autres éléments dans le module restent disponibles pour la promotion de type.  
  
 **Conséquences.** L'invalidation de la promotion de type d'une définition partielle peut provoquer des résultats inattendus et même des erreurs de compilation.  L'exemple suivant montre des définitions squelettes partielles d'une classe, dont l'une se trouve à l'intérieur d'un module.  
  
 [!code-vb[VbVbalrDeclaredElements#4](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]  
  
 Dans l'exemple précédent, le développeur peut s'attendre à ce que le compilateur fusionne les deux définitions partielles de `sampleClass`.  Toutefois, le compilateur n'envisage pas de promotion pour la définition partielle à l'intérieur de `sampleModule`.  En conséquence, il essaie de compiler deux classes distinctes et séparées, intitulées `sampleClass`, mais avec des chemins d'accès de qualification différents.  
  
 Le compilateur fusionne des définitions partielles uniquement lorsque leurs chemins qualifiés complets sont identiques.  
  
## Recommandations  
 Les recommandations suivantes correspondent à une bonne approche en matière de programmation.  
  
-   **Noms uniques.** Lorsque vous contrôlez totalement l'attribution des noms aux éléments de programmation, il est toujours recommandé d'utiliser des noms uniques partout.  Les noms identiques requièrent une qualification supplémentaire et peuvent compliquer la lecture de votre code.  Ils sont également la source de petites erreurs et de résultats inattendus.  
  
-   **Qualification complète.** Lorsque vous travaillez avec des modules et d'autres éléments dans le même espace de noms, l'approche la plus sûre consiste à toujours utiliser la qualification complète pour tous les éléments de programmation.  Si la promotion de type est invalidée pour un membre de module et que vous n'appliquez pas une qualification complète à ce membre, vous pouvez accéder par inadvertance à un élément de programmation différent.  
  
## Voir aussi  
 [Module Statement](../../../../visual-basic/language-reference/statements/module-statement.md)   
 [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [How to: Control the Scope of a Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)