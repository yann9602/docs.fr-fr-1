---
title: "Chiffrement des données dans SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83b992f7-b351-4678-b4b9-f4ffd58134cc
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4ea062a65f250a3532249783b0c7b147ed460317
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="data-encryption-in-sql-server"></a>Chiffrement des données dans SQL Server
SQL Server fournit des fonctions de chiffrement et déchiffrement de données à l'aide d'un certificat, d'une clé asymétrique ou d'une clé symétrique. Il gère tous ces éléments dans un magasin de certificats interne. Le magasin utilise une hiérarchie de chiffrement qui sécurise les certificats et les clés sur un niveau à l'aide de la couche située au-dessus dans la hiérarchie. Ce domaine de fonctionnalités de SQL Server est appelé stockage secret.  
  
 Le chiffrement à clé symétrique est le mode le plus rapide pris en charge par les fonctions de chiffrement. Ce mode est approprié pour la gestion de volumes importants de données. Les clés symétriques peuvent être chiffrées par des certificats, des mots de passe ou d'autres clés symétriques.  
  
## <a name="keys-and-algorithms"></a>Clés et algorithmes  
 SQL Server prend en charge plusieurs algorithmes de chiffrement à clé symétrique, notamment DES, Triple DES, RC2, RC4, RC4 128 bits, DESX, AES 128 bits, AES 192 bits et AES 256 bits. Les algorithmes sont implémentés à l'aide de l'API de chiffrement Windows.  
  
 Dans l'étendue d'une connexion de base de données, SQL Server peut gérer plusieurs clés symétriques ouvertes. Une clé ouverte est récupérée du magasin et est disponible pour le déchiffrement des données. Lorsqu'une donnée est déchiffrée, il est inutile de spécifier la clé symétrique à utiliser. Chaque valeur chiffrée contient l'identificateur (GUID clé) de la clé utilisée pour la chiffrer. Le moteur met en correspondance le flux d'octets chiffrés avec une clé symétrique ouverte, si la clé correcte a été déchiffrée et est ouverte. Cette clé est ensuite utilisée pour procéder au déchiffrement et retourner les données. Si la clé correcte n'est pas ouverte, la valeur NULL est retournée.  
  
 Pour obtenir un exemple qui montre comment utiliser les données chiffrées dans une base de données, consultez [Comment : chiffrer une colonne de données](http://go.microsoft.com/fwlink/?LinkID=128559) dans la documentation en ligne de SQL Server.  
  
## <a name="external-resources"></a>Ressources externes  
 Pour plus d'informations sur le chiffrement des données, voir les ressources suivantes.  
  
|||  
|-|-|  
|[Chiffrement SQL Server](http://msdn.microsoft.com/library/bb510663.aspx) dans la documentation en ligne de SQL Server|Fournit une vue d'ensemble du chiffrement dans SQL Server. Cette rubrique fournit des liens vers des rubriques et procédures supplémentaires. |  
|[Hiérarchie de chiffrement](http://msdn.microsoft.com/library/ms189586.aspx) et [rubriques de procédures de chiffrement](http://msdn.microsoft.com/library/aa337557.aspx) dans la documentation en ligne de SQL Server|Fournit une vue d'ensemble du chiffrement dans SQL Server. Cette rubrique fournit des liens vers des rubriques et procédures supplémentaires. |  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation des applications ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scénarios de sécurité des applications dans SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Authentification dans SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [Serveur et rôles de base de données dans SQL Server](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [Propriété et séparation des schémas utilisateur dans SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [Autorisation et permissions dans SQL Server](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
