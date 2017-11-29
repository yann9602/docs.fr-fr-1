---
title: "Comment : utiliser des fonctions scalaires définies par l'utilisateur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ef9e687522e200487e0fc2a661bbd545d4eb4bbf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Comment : utiliser des fonctions scalaires définies par l'utilisateur
Vous pouvez mapper une méthode cliente définie sur une classe à une fonction définie par l'utilisateur à l'aide de l'attribut <xref:System.Data.Linq.Mapping.FunctionAttribute>. Notez que le corps de la méthode construit une expression qui capture l'intention de l'appel de méthode et passe cette expression au <xref:System.Data.Linq.DataContext> pour la traduire et l'exécuter.  
  
> [!NOTE]
>  L'exécution directe se produit uniquement si la fonction est appelée à l'extérieur d'une requête. Pour plus d’informations, consultez [Comment : Call User-Defined les fonctions Inline](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).  
  
## <a name="example"></a>Exemple  
 Le code SQL suivant présente une fonction scalaire `ReverseCustName()` définie par l'utilisateur.  
  
```  
CREATE FUNCTION ReverseCustName(@string varchar(100))  
RETURNS varchar(100)  
AS  
BEGIN  
    DECLARE @custName varchar(100)  
    -- Implementation left as exercise for users.  
    RETURN @custName  
END  
```  
  
 Vous pouvez mapper une méthode cliente telle que la méthode suivante pour ce code :  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions définies par l’utilisateur](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
