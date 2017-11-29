---
title: Variable &#39; &lt;variablename&gt;&#39; masque une variable dans un bloc englobant
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords: BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2af570cd002b4be4e15a7c03b0ffc2ff84ba3982
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a>Variable &#39; &lt;variablename&gt;&#39; masque une variable dans un bloc englobant
Une variable dans un bloc a le même nom qu’une autre variable locale.  
  
 **ID d’erreur :** BC30616  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Renommez la variable du bloc englobé afin qu’il ne soit pas le même que toute autre variable locale. Exemple :  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   Une cause courante de cette erreur est l’utilisation de `Catch e As Exception` à l’intérieur d’un gestionnaire d’événements. Si c’est le cas, un nom de la `Catch` la variable de bloc `ex` plutôt que `e`.  
  
-   Une autre source courante de cette erreur est une tentative d’accéder à une variable locale déclarée dans un `Try` bloquer dans une fonction `Catch` bloc. Pour corriger ce problème, déclarez la variable en dehors de la `Try...Catch...Finally` structure.  
  
## <a name="see-also"></a>Voir aussi  
 [Try...Catch...Finally (instruction)](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Déclaration de variable](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
