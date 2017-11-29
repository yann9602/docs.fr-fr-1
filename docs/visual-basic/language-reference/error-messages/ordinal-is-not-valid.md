---
title: Nombre non valide
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d31d0fba19cc16004c0b56786af30603d0c509ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ordinal-is-not-valid"></a>Nombre non valide
Votre appel à une bibliothèque de liens dynamiques (DLL) indiqué à utiliser un nombre au lieu d’un nom de procédure, à l’aide de la `#num` syntaxe. Cette erreur a les causes possibles suivantes :  
  
-   Une tentative de convertir le `#num` expression à un nombre a échoué.  
  
-   Le `#num` spécifié n’indique pas de fonction dans la DLL.  
  
-   Une bibliothèque de types possède une déclaration non valide, ce qui provoque une utilisation interne d’un nombre ordinal non valide.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Assurez-vous que l’expression représente un nombre valide ou appelez la procédure par nom.  
  
2.  Assurez-vous que `#num` identifie une fonction valide dans la DLL.  
  
3.  Isoler la cause du problème en supprimant le code de l’appel de procédure. Écrire un `Declare` instruction de la procédure et signalez le problème au fournisseur de la bibliothèque de types.  
  
## <a name="see-also"></a>Voir aussi  
 [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)
