---
title: "Appel de fonctions dans les requ&#234;tes LINQ to Entities | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Appel de fonctions dans les requ&#234;tes LINQ to Entities
Les rubriques de cette section expliquent comment appeler des fonctions dans les requêtes LINQ to Entities.  
  
 Les classes <xref:System.Data.Objects.SqlClient.SqlFunctions> et <xref:System.Data.Objects.EntityFunctions> donnent accès à des fonctions canoniques et de base de données dans le cadre d'Entity Framework.  Pour plus d’informations, consultez [Procédure : appeler des fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) et [Procédure : appeler des fonctions de base de données](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).  
  
 L'appel d'une fonction personnalisée passe par trois étapes de base obligatoires :  
  
1.  Définissez une fonction dans votre modèle conceptuel ou déclarez\-la dans votre modèle de stockage.  
  
2.  Ajoutez une méthode à votre application et mappez\-la à la fonction du modèle avec un objet <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.  
  
3.  Appelez la fonction dans une requête LINQ to Entities.  
  
 Pour plus d'informations, consultez les rubriques de cette section.  
  
## Dans cette section  
 [Procédure : appeler des fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [Procédure : appeler des fonctions de base de données](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [Procédure : appeler les fonctions de base de données personnalisées](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [Procédure : appeler des fonctions définies par modèle dans des requêtes](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [Procédure : appeler des fonctions définies par modèle comme des méthodes d'objet](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## Voir aussi  
 [Requêtes dans LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)   
 [Fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)   
 [.edmx File Overview](http://msdn.microsoft.com/fr-fr/f4c8e7ce-1db6-417e-9759-15f8b55155d4)   
 [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/fr-fr/0dad7b8b-58f6-4271-b238-f34810d68e5f)