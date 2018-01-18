---
title: "Appel de fonctions dans les requêtes LINQ to Entities"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: dd81543f3a89f4f673f999b1fa80575de6d64654
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>Appel de fonctions dans les requêtes LINQ to Entities
Les rubriques de cette section expliquent comment appeler des fonctions dans les requêtes LINQ to Entities.  
  
 Les classes <xref:System.Data.Objects.EntityFunctions> et <xref:System.Data.Objects.SqlClient.SqlFunctions> donnent accès à des fonctions canoniques et de base de données dans le cadre d'Entity Framework. Pour plus d’informations, consultez [Comment : appeler des fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) et [Comment : appeler des fonctions de base de données](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).  
  
 L'appel d'une fonction personnalisée passe par trois étapes de base obligatoires :  
  
1.  Définissez une fonction dans votre modèle conceptuel ou déclarez-la dans votre modèle de stockage.  
  
2.  Ajoutez une méthode à votre application et mappez-la à la fonction du modèle avec un objet <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.  
  
3.  Appelez la fonction dans une requête LINQ to Entities.  
  
 Pour plus d'informations, consultez les rubriques de cette section.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour appeler des fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [Guide pratique pour appeler des fonctions de base de données](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [Guide pratique pour appeler des fonctions de base de données personnalisées](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [Guide pratique pour appeler des fonctions définies par modèle dans les requêtes](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [Guide pratique pour appeler des fonctions définies par modèle comme méthodes d’objet](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Requêtes dans LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [Fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)  
 [vue d’ensemble du fichier .edmx](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Comment : définir des fonctions personnalisées dans le modèle conceptuel](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f)
