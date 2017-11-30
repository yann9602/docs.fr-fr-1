---
title: "Fonction imbriquée n’a pas une signature compatible avec le délégué &#39; &lt;nom_délégué&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords: BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 60cf15343023110561da3e3fcf202bd00394127a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a>Fonction imbriquée n’a pas une signature compatible avec le délégué &#39; &lt;nom_délégué&gt;&#39;
Une expression lambda a été assignée à un délégué qui a une signature incompatible. Par exemple, dans le code suivant, le délégué `Del` a deux paramètres entiers.  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 L’erreur est déclenchée si une expression lambda avec un argument est déclarée comme type `Del`:  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 **ID d’erreur :** BC36532  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Ajustez la définition de délégué ou l’expression lambda assignée afin que les signatures sont compatibles.  
  
## <a name="see-also"></a>Voir aussi  
 [Conversion simplifiée des délégués](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Expressions lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
