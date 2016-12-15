---
title: "Declared Element Names (Visual Basic) | Microsoft Docs"
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
  - "declared elements, case sensitivity"
  - "names, Visual Basic rules"
  - "naming conventions"
  - "element names"
  - "declared elements, identifiers"
  - "declarations, elements"
  - "declared elements, valid names"
  - "[] escape characters [Visual Basic]"
  - "names, elements"
  - "declaration statements, declared elements"
  - "declaring elements"
  - "identifiers, declared elements"
  - "case sensitivity, declared element names"
  - "escape characters"
  - "names, declared elements"
  - "declared elements, about declared elements"
  - "escaped names"
  - "declared elements, names"
  - "names, naming conventions"
  - "identifiers, elements"
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Declared Element Names (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Chaque élément déclaré a un nom, également appelé *identificateur*, utilisé par le code pour faire référence à l'élément déclaré.  
  
## Règles  
 En [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], un nom d'élément doit respecter les règles suivantes :  
  
-   commencer par un caractère alphabétique ou un trait de soulignement \(`_`\) ;  
  
-   contenir uniquement des caractères alphabétiques, des chiffres décimaux et des traits de soulignement ;  
  
-   comprendre au moins un caractère alphabétique ou un chiffre décimal s'il commence par un trait de soulignement ;  
  
-   être inférieur ou égal à 1 023 caractères.  
  
 La longueur maximale de 1 023 caractères s'applique également à un nom qualifié complet, tel que : `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.  
  
 Vous trouverez ci\-dessous des exemples de noms d'éléments valides.  
  
 `aB123__45`  
  
 `_567`  
  
 Vous trouverez ci\-dessous des exemples de noms d'éléments non valides.  Le premier contient uniquement un trait de soulignement, le second commence par un chiffre décimal et le troisième contient un caractère non valide \($\).  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  Les noms d'élément commençant par un trait de soulignement \(`_`\) ne font pas partie de la spécification CLS \([Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)\) ; par conséquent, le code conforme CLS ne peut pas utiliser de composant qui définit ce type de noms.  Toutefois, un trait de soulignement inséré à toute autre position dans un nom d'élément est conforme à la spécification CLS.  
  
### Indications sur la longueur du nom  
 D'un point de vue pratique, votre nom doit être aussi court que possible tout en identifiant clairement la nature de l'élément.  La lisibilité de votre code s'en trouve améliorée, et la justification et la taille de fichier source réduites.  
  
 En revanche, votre nom ne doit pas être court au point de ne pas décrire suffisamment ce que l'élément représente et comment votre code l'utilise.  Cette considération est importante pour la lisibilité de votre code.  Si une autre personne essaie de le comprendre ou si vous l'examinez longtemps après l'avoir écrit, des noms d'éléments appropriés peuvent vous faire gagner un temps précieux.  
  
## Noms d'échappement  
 En règle générale, un nom d'élément ne doit correspondre à aucun des mots clés réservés par [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], tels que `Case` ou `Friend`.  Toutefois, vous pouvez définir un *nom d'échappement* placé entre crochets \(`[ ]`\).  Un nom d'échappement peut correspondre à n'importe quel mot clé [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] puisque la présence des crochets lève toute ambiguïté.  Vous pouvez également utiliser les crochets lorsque vous faites référence au nom ultérieurement dans votre code.  
  
 En général, vous devez utiliser des noms échappés uniquement dans les cas suivants :  
  
-   Votre code a migré à partir d'une version antérieure de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] qui n'a pas réservé le mot clé utilisé comme nom ou  
  
-   vous utilisez du code écrit dans un autre langage dans lequel le mot clé donné n'est pas réservé.  
  
 Sinon, vous devez envisager de renommer l'élément si son nom est en conflit avec un mot clé.  L'environnement de développement intégré \(IDE\) offre un moyen simple d'effectuer cette opération.  Pour plus d'informations, consultez [Refactorisation et boîte de dialogue Renommer](../../../../visual-basic/developing-apps/using-ide/refactoring-and-rename-dialog-box.md).  
  
## Respect de la casse dans les noms  
 En [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], les noms d'éléments ne respectent pas la casse.  En d'autres termes, lorsque le compilateur compare deux noms qui ne se distinguent que par la casse, il les interprète comme un seul et même nom.  Il considère, par exemple, que `ABC` et `abc` font référence au même élément déclaré.  
  
 Néanmoins, le Common Language Runtime \(CLR\) utilise des liaisons qui respectent la casse.  En conséquence, lorsque vous générez un assembly ou une DLL et que vous les mettez à la disposition d'autres assemblys, vos noms respectent alors la casse.  Par exemple, si vous définissez une classe avec un élément appelé `ABC` et que d'autres assemblys utilisent votre classe via le Common Language Runtime, ils doivent faire référence à l'élément sous la forme `ABC`.  Si, par la suite, vous recompilez votre classe et que vous changez le nom de l'élément en `abc`, les autres assemblys qui utilisent votre classe ne peuvent plus accéder à cet élément.  Dès lors, lorsque vous libérez une version mise à jour d'un assembly, évitez de modifier la casse des éléments publics.  
  
## Noms et paramètres régionaux  
 La comparaison de noms est indépendante des paramètres régionaux.  Si deux noms correspondent dans des paramètres régionaux spécifiques, ils correspondent dans tous.  
  
## Voir aussi  
 [Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)   
 [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Statements](../../../../visual-basic/language-reference/statements/index.md)