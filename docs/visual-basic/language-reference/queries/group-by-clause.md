---
title: Group By, clause (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement [Visual Basic]
- Group By clause [Visual Basic]
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b719bfa2ebe4c324acf82a03e215e481283845fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="group-by-clause-visual-basic"></a>Group By, clause (Visual Basic)
Regroupe les éléments d'un résultat de requête. Peut aussi être utilisée pour appliquer des fonctions d’agrégation à chaque groupe. L’opération de regroupement est basée sur une ou plusieurs clés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a>Composants  
  
-   `listField1`, `listField2`  
  
     Facultatif. Un ou plusieurs champs de la ou des variables de requête qui identifient explicitement les champs à inclure dans le résultat groupé. Si aucun champ n’est spécifié, tous les champs de la ou des variables de requête sont inclus dans le résultat groupé.  
  
-   `keyExp1`  
  
     Obligatoire. Expression qui identifie la clé à utiliser pour déterminer les groupes d’éléments. Vous pouvez spécifier plusieurs clés pour spécifier une clé composite.  
  
-   `keyExp2`  
  
     Facultatif. Une ou plusieurs clés supplémentaires combinées à `keyExp1` pour créer une clé composite.  
  
-   `aggregateList`  
  
     Obligatoire. Une ou plusieurs expressions qui identifient la façon dont les groupes sont agrégés. Pour identifier un nom de membre pour les résultats groupés, utilisez le mot clé `Group` , qui peut prendre l’une des formes suivantes :  
  
    ```  
    Into Group  
    ```  
  
     ou  
  
    ```  
    Into <alias> = Group  
    ```  
  
     Vous pouvez aussi inclure des fonctions d’agrégation à appliquer au groupe.  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez utiliser la clause `Group By` pour décomposer les résultats d’une requête en groupes. Le regroupement est basé sur une clé ou une clé composite constituée de plusieurs clés. Les éléments associés à des valeurs de clé correspondantes sont inclus dans le même groupe.  
  
 Utilisez le paramètre `aggregateList` de la clause `Into` et le mot clé `Group` pour identifier le nom de membre servant à référencer le groupe. Vous pouvez aussi inclure des fonctions d’agrégation dans la clause `Into` pour calculer les valeurs des éléments groupés. Pour une liste des fonctions d’agrégation standard, consultez [Aggregate, Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant regroupe une liste de clients en fonction de leur situation (pays) et indique le nombre de clients dans chaque groupe. Les résultats sont triés par nom de pays. Les résultats groupés sont organisés par nom de ville.  
  
 [!code-vb[VbSimpleQuerySamples#11](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-by-clause_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Requêtes](../../../visual-basic/language-reference/queries/queries.md)  
 [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From (clause)](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By (clause)](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Aggregate (clause)](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Group Join (clause)](../../../visual-basic/language-reference/queries/group-join-clause.md)
