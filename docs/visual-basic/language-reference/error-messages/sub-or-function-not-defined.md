---
title: "Sub ou Function non défini (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID35
dev_langs:
- VB
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7d32bc9c8f13b245e6333c4460cab541f6e9409e
ms.lasthandoff: 03/13/2017

---
# <a name="sub-or-function-not-defined-visual-basic"></a>Sub ou Function non défini (Visual Basic)
A `Sub` ou `Function` doit être définie pour être appelée. Cette erreur peut avoir plusieurs causes :  
  
-   Faute d’orthographe du nom de la procédure.  
  
-   Essayez d’appeler une procédure depuis un autre projet sans ajouter explicitement une référence au projet dans le **références** boîte de dialogue.  
  
-   Spécification d’une procédure qui n’est pas visible pour la procédure appelante.  
  
-   La déclaration d’une routine de bibliothèque de liens dynamiques (DLL) de Windows ou d’une routine de ressource de code Macintosh qui n’est pas dans la ressource de bibliothèque ou de code spécifiée.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Assurez-vous que le nom de la procédure est correctement orthographié.  
  
2.  Recherchez le nom du projet contenant la procédure que vous voulez appeler dans le **références** boîte de dialogue. Si elle n’apparaît pas, cliquez sur le **Parcourir** bouton de recherche. Activez la case à cocher à gauche du nom du projet, puis cliquez sur **OK**.  
  
3.  Vérifiez le nom de la routine.  
  
## <a name="see-also"></a>Voir aussi  
 [Types d’erreurs](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [Gestion des références dans un projet](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)   
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)
