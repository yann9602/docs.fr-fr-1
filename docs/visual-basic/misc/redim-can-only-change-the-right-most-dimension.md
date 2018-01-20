---
title: "&#39; ReDim &#39; peut changer que la dimension la plus à droite"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 752e0e54c48b3b348a477787e5e911f1b1777667
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a>&#39; ReDim &#39; peut changer que la dimension la plus à droite
Une instruction `ReDim` a tenté d’utiliser le mot clé `Preserve` pour modifier une dimension d’un tableau qui n’est pas la dernière dimension. Lors de l’utilisation de `Preserve`, vous pouvez redimensionner uniquement la dernière dimension d’un tableau. Pour toutes les autres dimensions, vous devez spécifier la même taille que pour le tableau existant.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Supprimez le mot clé `Preserve` .  
  
## <a name="see-also"></a>Voir aussi  
 [Tableaux en Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [Dimensions du tableau dans Visual Basic](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [ReDim (instruction)](../../visual-basic/language-reference/statements/redim-statement.md)  
 [Dim (instruction)](../../visual-basic/language-reference/statements/dim-statement.md)  
 [Conserver - supprimer](http://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
