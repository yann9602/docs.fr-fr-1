---
title: Skip, clause (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 508f3c094df4c834305bcb4a78223c1cee82b1c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="skip-clause-visual-basic"></a>Skip, clause (Visual Basic)
Ignore un nombre spécifié d’éléments dans une collection, puis retourne les éléments restants.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Skip count  
```  
  
## <a name="parts"></a>Composants  
 `count`  
 Obligatoire. Une valeur ou une expression qui donne le nombre d’éléments de la séquence à ignorer.  
  
## <a name="remarks"></a>Remarques  
 Le `Skip` clause entraîne une requête à ignorer des éléments au début d’une liste de résultats et retourner les éléments restants. Le nombre d’éléments à ignorer est identifié par le `count` paramètre.  
  
 Vous pouvez utiliser la `Skip` clause avec la `Take` clause pour retourner une plage de données à partir de n’importe quel segment d’une requête. Pour ce faire, passez à l’index du premier élément de la plage à la `Skip` clause et la taille de la plage à la `Take` clause.  
  
 Lorsque vous utilisez la `Skip` clause dans une requête, vous devrez peut-être également vous assurer que les résultats sont retournés dans un ordre qui activera le `Skip` clause pour ignorer les résultats concernés. Pour plus d’informations sur le classement des résultats de la requête, consultez [une Clause Order By](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Vous pouvez utiliser la `SkipWhile` clause pour spécifier que seuls certains éléments sont ignorés, selon une condition fournie.  
  
## <a name="example"></a>Exemple  
 Le code suivant utilise des exemple le `Skip` clause avec la `Take` clause pour retourner des données à partir d’une requête dans des pages. Le `GetCustomers` fonction utilise le `Skip` clause pour ignorer les clients dans la liste jusqu'à ce que le démarrage fourni valeur d’index et utilise le `Take` clause pour retourner une page de clients à partir de cette valeur d’index.  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-clause_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Requêtes](../../../visual-basic/language-reference/queries/queries.md)  
 [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From (clause)](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By (clause)](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Skip While (clause)](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take (clause)](../../../visual-basic/language-reference/queries/take-clause.md)
