---
title: "Sub ou Function non défini (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6237ca26b06bdffa06499607e634b3222725c189
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sub-or-function-not-defined-visual-basic"></a>Sub ou Function non défini (Visual Basic)
A `Sub` ou `Function` doit être défini afin d’être appelée. Cette erreur peut avoir plusieurs causes :  
  
-   Faute d’orthographe dans le nom de la procédure.  
  
-   Essayez d’appeler une procédure à partir d’un autre projet sans ajouter explicitement une référence à ce projet dans le **références** boîte de dialogue.  
  
-   Spécification d’une procédure qui n’est pas visible à la procédure appelante.  
  
-   Déclaration d’une routine de bibliothèque de liens dynamiques (DLL) de Windows ou d’une routine de ressource de code Macintosh qui n’est pas dans la ressource de bibliothèque ou de code spécifiée.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Assurez-vous que le nom de la procédure est correctement orthographié.  
  
2.  Rechercher le nom du projet contenant la procédure que vous voulez appeler dans le **références** boîte de dialogue. Si elle n’apparaît pas, cliquez sur le **Parcourir** bouton pour le rechercher. Activez la case à cocher à gauche du nom du projet, puis cliquez sur **OK**.  
  
3.  Vérifiez le nom de la routine.  
  
## <a name="see-also"></a>Voir aussi  
 [Types d’erreurs](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project)  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)
