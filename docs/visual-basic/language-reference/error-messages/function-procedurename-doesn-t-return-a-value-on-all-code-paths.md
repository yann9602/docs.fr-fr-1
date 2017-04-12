---
title: "Fonction &quot;&lt;NomProcédure&gt;&quot; ne retourne pas une valeur pour tous les chemins de code | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42105
- vbc42105
dev_langs:
- VB
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
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
ms.openlocfilehash: 288fdf7c4845b20283681d9eb3504ac314f1ddd2
ms.lasthandoff: 03/13/2017

---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a>Fonction '&lt;NomProcédure&gt;' ne retourne pas une valeur pour tous les chemins de code
Fonction '\<NomProcédure >' ne retourne pas une valeur pour tous les chemins de code. Une instruction 'Return' est-elle manquante ?  
  
 Un `Function` procédure possède au moins un chemin d’accès possible via son code qui ne retourne pas de valeur.  
  
 Vous pouvez retourner une valeur depuis une `Function` procédure dans une des manières suivantes :  
  
-   Inclure la valeur dans un [instruction Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
-   Attribuez la valeur à la `Function` procédure nom, puis effectuez une `Exit Function` instruction.  
  
-   Attribuez la valeur à la `Function` procédure nom, puis effectuez la `End Function` instruction.  
  
 Si le contrôle passe à `Exit Function` ou `End Function` et que vous n’avez affecté une valeur pour le nom de la procédure, la procédure retourne la valeur par défaut du type de données de retour. Pour plus d’informations, consultez « Comportement » dans [Function, instruction](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements comme des erreurs, consultez la page [configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC42105  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Vérifiez votre logique de flux de contrôle et veillez à qu'attribuer une valeur avant chaque instruction qui provoque un retour.  
  
     Il est plus facile de garantir que chaque retour de la procédure retourne une valeur si vous utilisez toujours la `Return` instruction. Dans ce cas, la dernière instruction avant `End Function` doit être un `Return` instruction.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures Function](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Page Compiler, Concepteur de projet (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
