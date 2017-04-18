---
title: "Propriété &quot;&lt;propertyname&gt;&quot; ne retourne pas une valeur pour tous les chemins de code | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42107
- vbc42107
dev_langs:
- VB
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
caps.latest.revision: 7
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
ms.openlocfilehash: e7c94d827761ad26d517b44a06734c5db4480a62
ms.lasthandoff: 03/13/2017

---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a>Propriété '&lt;propertyname&gt;' ne retourne pas une valeur pour tous les chemins de code
Propriété '\<propertyname >' ne retourne pas une valeur pour tous les chemins de code. Une exception de référence null peut se produire au moment de l'exécution lorsque le résultat est utilisé.  
  
 Une propriété `Get` procédure possède au moins un chemin d’accès possible via son code qui ne retourne pas de valeur.  
  
 Vous pouvez retourner une valeur d’une propriété `Get` procédure dans une des manières suivantes :  
  
-   Assignez la valeur au nom de propriété, puis exécutez une `Exit Property` instruction.  
  
-   Assignez la valeur au nom de propriété, puis exécutez la `End Get` instruction.  
  
-   Inclure la valeur dans un [instruction Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 Si le contrôle passe à `Exit Property` ou `End Get` et vous n’avez affecté une valeur au nom de propriété, le `Get` procédure retourne la valeur par défaut de la propriété type de données. Pour plus d’informations, consultez « Comportement » dans [Function, instruction](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements comme des erreurs, consultez la page [configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC42107  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Vérifiez votre logique de flux de contrôle et veillez à qu'attribuer une valeur avant chaque instruction qui provoque un retour.  
  
     Il est plus facile de garantir que chaque retour de la procédure retourne une valeur si vous utilisez toujours la `Return` instruction. Dans ce cas, la dernière instruction avant `End Get` doit être un `Return` instruction.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures de propriété](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Get (instruction)](../../../visual-basic/language-reference/statements/get-statement.md)
