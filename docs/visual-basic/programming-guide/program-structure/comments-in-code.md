---
title: "Comments in Code (Visual Basic) | Microsoft Docs"
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
  - "Uncomment button"
  - "REM statement"
  - "comments, in code"
  - "comments, Visual Basic code"
  - "Comment button"
  - "buttons, Uncomment"
  - "buttons, Comment"
  - "code comments, Visual Basic"
  - "Visual Basic code, comments"
  - "comments"
  - "code comments"
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Comments in Code (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Lorsque vous lisez les exemples de code, vous rencontrez souvent le symbole de commentaire \(`'`\).  Ce symbole indique au compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] d'ignorer le texte qui le suit, c'est\-à\-dire le *commentaire*.  Les commentaires sont de courtes explications destinées à éclairer ceux qui lisent le code.  
  
 En programmation, il est hautement recommandé de faire précéder toutes les procédures d'un commentaire court qui décrit les caractéristiques fonctionnelles de la procédure \(ce qu'elle fait\).  Ceci est utile tant pour l'auteur du code lui\-même que pour toute autre personne amenée à consulter le code.  Vous devez séparer les détails relatifs à l'implémentation \(comment la procédure fait ce qu'elle doit faire\) des commentaires décrivant les caractéristiques fonctionnelles.  Si vous fournissez des informations d'implémentation dans la description, n'oubliez pas de les mettre à jour lors de la mise à jour de la fonction.  
  
 Les commentaires peuvent soit suivre une instruction sur la même ligne, soit occuper une ligne entière.  Ces deux cas sont illustrés par le code suivant :  
  
 [!code-vb[VbVbcnConventions#16](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_1.vb)]  
  
 Si votre commentaire doit occuper plusieurs lignes, utilisez le symbole de commentaire sur chacune d'elles, comme l'exemple ci\-dessous l'illustre.  
  
 [!code-vb[VbVbcnConventions#17](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_2.vb)]  
  
## Recommandations sur le commentaire  
 Le tableau suivant fournit des recommandations générales sur les types de commentaires qui peuvent précéder une section de code.  Il ne s'agit que de suggestions ; [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] n'impose aucune règle concernant l'ajout de commentaires.  Procédez de la façon que vous jugez la plus efficace pour vous et toute personne amenée à lire votre code.  
  
|||  
|-|-|  
|Type de commentaire|Description du commentaire|  
|Objectif|Décrit ce que fait la procédure \(et non comment elle le fait\)|  
|Assumptions \(Hypothèses\)|Répertorie chaque variable externe, contrôle, fichier ouvert ou autre élément auquel la procédure accède.|  
|Effects \(Effets\)|Répertorie chaque variable externe, contrôle ou fichier affecté, ainsi que ses effets \(uniquement si ce n'est pas évident\)|  
|Inputs \(Entrées\)|Spécifie l'objectif attaché à l'argument|  
|Returns \(Retours\)|Explique les valeurs retournées par la procédure.|  
  
 N'oubliez pas :  
  
-   Pour chaque déclaration de variable importante, faites précéder d'un commentaire décrivant son utilisation.  
  
-   Les noms des variables, contrôles et procédures doivent être suffisamment clairs pour que les commentaires servent uniquement à fournir des détails d'implémentation complexes.  
  
-   Vous ne pouvez pas faire suivre une séquence de continuation par un commentaire sur la même ligne.  
  
 Vous pouvez ajouter ou supprimer des symboles de commentaires pour un bloc de code en sélectionnant une ou plusieurs lignes de code et en choisissant les boutons **Commenter la sélection** \(![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.png "vaCommentButton")\) et **Ne pas commenter la sélection** \(![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.png "vaUncommentButton")\) dans la barre d'outils **Éditeur de texte**.  
  
> [!NOTE]
>  Vous pouvez également ajouter des commentaires à votre code en faisant précéder le texte du mot clé `REM`.  Cependant, le symbole `'` et les boutons **Commenter la sélection**\/**Ne pas commenter la sélection** sont plus simples à utiliser et sont moins gourmands en espace et en mémoire.  
  
## Voir aussi  
 [Documenter votre code avec les commentaires XML](http://msdn.microsoft.com/magazine/dd722812.aspx)   
 [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)   
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)   
 [Structure de programme et conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [REM Statement](../../../visual-basic/language-reference/statements/rem-statement.md)