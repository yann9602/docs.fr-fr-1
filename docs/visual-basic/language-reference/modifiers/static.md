---
title: Static (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e08f46076281e766a5bc0b99cd61fee9cd41ece5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="static-visual-basic"></a>Static (Visual Basic)
Spécifie qu’une ou plusieurs variables locales déclarées doivent continuer d’exister et conservent leurs valeurs les plus récentes après l’arrêt de la procédure dans laquelle elles sont déclarées.  
  
## <a name="remarks"></a>Remarques  
 Normalement, une variable locale dans une procédure cesse d’exister dès que la procédure s’arrête. Une variable statique continue à exister et conserve sa valeur la plus récente. La prochaine fois que votre code appelle la procédure, la variable n’est pas réinitialisée, et elle contient toujours la valeur la plus récente que vous avez attribué à ce dernier. Une variable statique continue à exister pendant la durée de vie de la classe ou le module qui est défini dans.  
  
## <a name="rules"></a>Règles  
  
-   **Contexte de déclaration.** Vous pouvez utiliser `Static` uniquement sur les variables locales. Cela signifie que le contexte de déclaration pour une `Static` variable doit être une procédure ou un bloc dans une procédure, et il ne peut pas être un fichier source, un espace de noms, une classe, une structure ou un module.  
  
     Vous ne pouvez pas utiliser `Static` à l’intérieur d’une procédure de structure.  
  
-   Les types de données de `Static` variables locales ne peut pas être déduits. Pour plus d’informations, consultez [l’inférence de Type Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
-   **Modificateurs combinés.** Vous ne pouvez pas spécifier `Static` avec `ReadOnly`, `Shadows`, ou `Shared` dans la même déclaration.  
  
## <a name="behavior"></a>Comportement  
 Lorsque vous déclarez une variable statique dans un `Shared` procédure, une seule copie de la variable statique est disponible pour l’application entière. Vous appelez un `Shared` nom de la procédure à l’aide de la classe, pas une variable qui pointe vers une instance de la classe.  
  
 Lorsque vous déclarez une variable statique dans une procédure qui n’est pas `Shared`, seule une copie de la variable est disponible pour chaque instance de la classe. Vous appelez une procédure non partagée à l’aide d’une variable qui pointe vers une instance spécifique de la classe.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre l'utilisation de `Static`.  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 Le `Static` variable `totalSales` est initialisée à 0 qu’une seule fois. Chaque fois que vous entrez `updateSales`, `totalSales` a encore la valeur la plus récente que vous avez calculé pour lui.  
  
 Le `Static` modificateur peut être utilisé dans ce contexte :  
  
 [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Durée de vie dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Déclaration de variable](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Inférence de type local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Objets et classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
