---
title: SKIP (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f53c84b216c847740f2c093582fd151d5ed0ef63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="skip-entity-sql"></a>SKIP (Entity SQL)
Vous pouvez effectuer une pagination physique à l'aide de la sous-clause SKIP de la clause ORDER BY. La sous-clause SKIP ne peut pas être utilisée séparément de la clause ORDER BY.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ SKIP n ]  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 Nombre d'éléments à ignorer.  
  
## <a name="remarks"></a>Remarques  
 Si une sous-clause d'expression SKIP est présente dans une clause ORDER BY, les résultats sont triés en fonction de la spécification de classement et le jeu de résultats comprend plusieurs lignes immédiatement à la suite de l'expression SKIP. Par exemple, SKIP 5 ignore les cinq premières lignes et retourne la sixième ligne et les suivantes.  
  
> [!NOTE]
>  Une requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] n'est pas valide si le modificateur TOP et la sous-clause SKIP figurent dans la même expression de requête. La requête doit être réécrite en remplaçant l'expression TOP par l'expression LIMIT.  
  
> [!NOTE]
>  Dans [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], l'utilisation de SKIP avec ORDER BY sur des colonnes non-clés peut retourner des résultats incorrects. Le nombre de lignes ignorées peut être supérieur au nombre de lignes spécifié si la colonne non-clé contient des données en double. Cela est dû à la manière dont la sous-clause SKIP est traduite pour [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)]. Par exemple, dans le code suivant plus de cinq lignes pourraient être ignorées si `E.NonKeyColumn` contient des valeurs en double :  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 La requête  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] de [cet](https://msdn.microsoft.com/library/bb738702\(v=vs.100\).aspx#_ESQL) exemple utilise l’opérateur ORDER BY avec SKIP pour spécifier l’ordre de tri utilisé sur les objets retournés dans une instruction SELECT.  
  
## <a name="see-also"></a>Voir aussi  
 [TRIER PAR](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [Comment : résultats de la Page via la requête](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [Pagination](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [RETOUR AU DÉBUT](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
