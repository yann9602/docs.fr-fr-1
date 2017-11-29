---
title: "&#39; #Region &#39; et &#39; #End Region &#39; les instructions ne sont pas valides dans les expressions lambda multiligne de corps de méthode"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords: BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 614d0c7324bfbf07bc5736c799e8b54937ead081
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>&#39; #Region &#39; et &#39; #End Region &#39; les instructions ne sont pas valides dans les expressions lambda multiligne corps de méthode
Le `#Region` bloc doit être déclaré au niveau de la classe, module ou d’espace de noms. Une zone réductible peut inclure une ou plusieurs procédures, mais il ne peut pas commencer ou se terminer à l’intérieur d’une procédure.  
  
 **ID d’erreur :** BC32025  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Assurez-vous que la procédure précédente est correctement terminée avec un `End Function` ou `End Sub` instruction.  
  
2.  Vérifiez que le `#Region` et `#End Region` sont des directives dans le même bloc de code.  
  
## <a name="see-also"></a>Voir aussi  
 [#Region (directive)](../../../visual-basic/language-reference/directives/region-directive.md)
