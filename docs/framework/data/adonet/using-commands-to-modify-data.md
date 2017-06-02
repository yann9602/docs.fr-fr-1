---
title: "Utilisation de commandes pour modifier des donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Utilisation de commandes pour modifier des donn&#233;es
À l'aide d'un fournisseur de données .NET Framework, vous pouvez exécuter des procédures stockées ou des instructions DDL \(CREATE TABLE et ALTER COLUMN, par exemple\) pour effectuer une manipulation de schéma sur une base de données ou un catalogue.  Ces commandes ne retournent pas des lignes comme une requête le ferait, donc l'objet **Command** fournit une méthode **ExecuteNonQuery** pour les traiter.  
  
 Vous pouvez utiliser la méthode **ExecuteNonQuery** pour modifier le schéma mais utiliser cette méthode pour traiter les instructions SQL qui modifient les données mais ne retournent pas de lignes telles que INSERT, UPDATE et DELETE.  
  
 Bien que la méthode **ExecuteNonQuery** ne retourne pas de lignes, les paramètres d'entrée et de sortie et les valeurs de retour peuvent être passés et retournés via la collection **Parameters** de l'objet **Command**.  
  
## Dans cette section  
 [Mise à jour des données dans une source de données](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 Décrit l'exécution de commandes ou de procédures stockées qui modifient les données dans une base de données.  
  
 [Exécution d'opérations de catalogue](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 Décrit l'exécution des commandes qui modifient le schéma de base de données.  
  
## Voir aussi  
 [Extraction et modification de données dans ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [Commandes et paramètres](../../../../docs/framework/data/adonet/commands-and-parameters.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)