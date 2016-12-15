---
title: "Static (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Static"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "static modifier"
  - "Static keyword"
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Static (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie qu'une ou plusieurs variables locales déclarées doivent continuer à exister et conservent leurs valeurs les plus récentes après l'arrêt de la procédure dans laquelle elles sont déclarées.  
  
## Notes  
 Normalement, une variable locale dans une procédure cesse d'exister dès que la procédure s'arrête.  Une variable statique continue à exister et conserve sa valeur la plus récente.  La prochaine fois que votre code appellera la procédure, la variable ne sera pas réinitialisée et elle contiendra encore la valeur la plus récente que vous lui aviez assignée.  Une variable statique continue à exister pendant toute la durée de vie de la classe ou du module dans lequel elle est définie.  
  
## Règles  
  
-   **Contexte de déclaration.** Vous pouvez utiliser uniquement `Static` sur les variables locales.  Cela signifie que le contexte de déclaration pour une variable `Static` doit être une procédure ou un bloc dans une procédure et ne peut pas être un fichier source, un espace de noms, une classe, une structure ou un module.  
  
     Vous ne pouvez pas utiliser `Static` à l'intérieur d'une procédure de structure.  
  
-   Les types de données des variables locales `Static` ne peuvent pas être déduits.  Pour plus d'informations, consultez [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
-   **Modificateurs combinés.** Vous ne pouvez pas spécifier `Static` avec `ReadOnly`, `Shadows` ou `Shared` dans la même déclaration.  
  
## Comportement  
 Lorsque vous déclarez une variable statique dans une procédure d' `Shared` , une seule copie de la variable statique est disponible pour l'application entière.  Vous appelez une procédure d' `Shared` à l'aide de le nom de la classe, et non une variable qui pointe vers une instance de la classe.  
  
 Lorsque vous déclarez une variable statique dans une procédure qui n'est pas `Shared`, une seule copie de la variable est disponible pour chaque instance de la classe.  Vous appelez une procédure non partagé en utilisant une variable qui pointe vers une instance spécifique de la classe.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation du mot clé `Static` :  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 La variable `Static` `totalSales` est initialisée une seule fois sur 0.  Chaque fois que vous entrez `updateSales`, `totalSales` a encore la valeur la plus récente que vous avez calculé pour lui.  
  
 Le modificateur `Static` peut être utilisé dans le contexte suivant :  
  
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## Voir aussi  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)   
 [Lifetime in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Déclaration de variable](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)