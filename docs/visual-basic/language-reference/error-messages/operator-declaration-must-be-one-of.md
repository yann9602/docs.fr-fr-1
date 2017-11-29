---
title: "Déclaration d’opérateur doit être de type : +,-, *,-, -, ^, &amp;, Like, Mod et, Or, Xor, pas &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;=, &gt; , &gt;=, CType, IsTrue ou IsFalse"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords: BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 80c8358dd13105c18e73e94735a51b02d5bd22c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a>Déclaration d’opérateur doit être de type : +,-, *,\,/, ^, &amp;, Like, Mod et, Or, Xor, pas &lt; &lt;, &gt; &gt;...
Vous pouvez déclarer uniquement un opérateur qui n’est éligible pour la surcharge. Le tableau suivant répertorie les opérateurs que vous pouvez déclarer.  
  
|Type|Opérateurs|  
|----------|---------------|  
|Unaire|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binaire|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Conversion (unaire)|`CType`|  
  
 Notez que le `=` opérateur dans la liste binaire est l’opérateur de comparaison, pas l’opérateur d’assignation.  
  
 **ID d’erreur :** BC33000  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Sélectionnez un opérateur dans le jeu d’opérateurs surchargeables.  
  
2.  Si vous avez besoin des fonctionnalités de surcharge d’un opérateur que vous ne pouvez pas surcharger directement, créez une procédure `Function` qui accepte les paramètres appropriés et retourne la valeur adéquate.  
  
## <a name="see-also"></a>Voir aussi  
 [Operator (instruction)](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Guide pratique : définir un opérateur](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Guide pratique : définir un opérateur de conversion](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)
