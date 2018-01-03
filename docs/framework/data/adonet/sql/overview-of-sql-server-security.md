---
title: "Vue d'ensemble de la sécurité SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ff0a78a852bdbf2fa1eb075273cad317c21fb182
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="overview-of-sql-server-security"></a>Vue d'ensemble de la sécurité SQL Server
Une stratégie de défense en profondeur avec chevauchement des couches de sécurité est le meilleur moyen de contrer les menaces de sécurité. SQL Server propose une architecture de sécurité conçue pour permettre aux administrateurs et aux développeurs de bases de données de créer des applications de base de données sécurisées et de contrer les menaces. Chaque version de SQL Server offre des améliorations par rapport aux versions précédentes avec l'introduction de nouvelles fonctions et fonctionnalités. Pour autant, il ne peut exister de plan de sécurité prêt à l'emploi. Chaque application a des spécifications de sécurité uniques. Les développeurs doivent comprendre quelle combinaison de fonctions et fonctionnalités est la plus adéquate pour contrer les menaces identifiées et pour anticiper les menaces qui risquent de voir le jour dans l'avenir.  
  
 Une instance SQL Server contient une collection hiérarchique d'entités, qui commence par le serveur. Chaque serveur contient plusieurs bases de données et chaque base de données contient une collection d’objets sécurisables. Chaque élément sécurisable de SQL Server est associé à *autorisations* qui peuvent être accordées à un *principal*, qui est un groupe individuel, ou processus autorisé à accéder à SQL Server. L’infrastructure de sécurité de SQL Server gère l’accès aux entités sécurisables via *authentification* et *autorisation*.  
  
-   L'authentification est le processus de connexion à SQL Server dans lequel une principal de sécurité demande l'accès en soumettant des informations d'identification qui sont évaluées par le serveur. L'authentification établit l'identité de l'utilisateur ou du processus en cours d'authentification.  
  
-   L'autorisation est le processus consistant à déterminer les ressources sécurisables auxquelles une principal de sécurité peut accéder et les opérations qui sont autorisées pour ces ressources.  
  
 Les rubriques de cette section présentent les concepts fondamentaux de la sécurité SQL Server et fournissent des liens vers la version appropriée de la documentation complète en ligne de SQL Server.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Authentification dans SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 Décrit les connexions et l'authentification dans SQL Server et fournit des liens vers des ressources supplémentaires.  
  
 [Serveur et rôles de base de données dans SQL Server](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 Décrit le rôle serveur fixe et le rôle de base de données fixe, les rôles de base de données personnalisés et les comptes intégrés, et fournit des liens vers des ressources supplémentaires.  
  
 [Propriété et séparation des schémas utilisateur dans SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 Décrit la propriété d'objet et la séparation utilisateur-schéma, et fournit des liens vers des ressources supplémentaires.  
  
 [Autorisation et permissions dans SQL Server](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 Décrit l'octroi d'autorisations selon le principe des privilèges minimum et fournit des liens vers des ressources supplémentaires.  
  
 [Chiffrement des données dans SQL Server](../../../../../docs/framework/data/adonet/sql/data-encryption-in-sql-server.md)  
 Décrit les options de chiffrement de données dans SQL Server et fournit des liens vers des ressources supplémentaires.  
  
 [Sécurité de l’intégration du CLR dans SQL Server](../../../../../docs/framework/data/adonet/sql/clr-integration-security-in-sql-server.md)  
 Fournit des liens vers les ressources de sécurité d'intégration de CLR.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation des applications ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Sécurité SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [Scénarios de sécurité des applications dans SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
