---
title: "Fonctions définies par l'utilisateur (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: df1b2a7c605134d57fcc21f9253373d4e0febb37
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="user-defined-functions-entity-sql"></a>Fonctions définies par l'utilisateur (Entity SQL)
Entity SQL prend en charge l'appel de fonctions définies par l'utilisateur dans une requête. Vous pouvez définir ces fonctions inline avec la requête (voir [Comment : appeler une fonction définie par l’utilisateur](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02)) ou en tant que partie du modèle conceptuel (consultez [Comment : définir des fonctions personnalisées dans le modèle conceptuel](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f)). Fonctions de modèle conceptuel sont définies comme une commande Entity SQL dans le [DefiningExpression](http://msdn.microsoft.com/en-us/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e) élément d’un [fonction](http://msdn.microsoft.com/en-us/dc3beca7-55cf-4977-8db0-5064cdbab134) élément dans le modèle conceptuel.  
  
 Entity SQL permet de définir des fonctions dans la commande de requête elle-même. Le [fonction](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) opérateur définit les fonctions inline. Vous pouvez définir plusieurs fonctions dans une même commande et ces fonctions peuvent avoir le même nom de fonction, tant que les signatures des fonctions sont uniques. Pour plus d'informations, consultez [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
