---
title: "Scénarios de sécurité des applications dans SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6207bc570dd8182b351a945a36d5f80c14a8dd4c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="application-security-scenarios-in-sql-server"></a>Scénarios de sécurité des applications dans SQL Server
Aucune méthode universelle n'existe pour créer une application cliente SQL Server sécurisée. Chaque application est unique au niveau de sa configuration, de son environnement de déploiement et de ses utilisateurs. Une application relativement sécurisée lors de son déploiement initial peut devenir moins sécurisée avec le temps. Il est impossible d'anticiper avec précision sur les menaces qui peuvent survenir dans le futur.  
  
 SQL Server, en tant que produit, a évolué version après version pour offrir aujourd'hui les fonctionnalités de sécurité les plus récentes permettant aux développeurs de créer des applications de base de données sécurisées. Toutefois, la sécurité n'est pas toujours acquise ; elle requiert une surveillance et des mises à jour constantes.  
  
## <a name="common-threats"></a>Menaces courantes  
 Les développeurs doivent connaître les menaces de sécurité, les outils disponibles pour les contrer et la manière d'éviter les défaillances de sécurité qu'ils se créent eux-mêmes. La sécurité peut être envisagée comme une chaîne dans laquelle un maillon manquant compromet la solidité de l'ensemble. La liste suivante comprend quelques menaces de sécurité courantes évoquées plus en détail dans les rubriques de cette section.  
  
### <a name="sql-injection"></a>injection SQL  
 L'injection SQL est le processus qui permet à un utilisateur malveillant d'entrer des instructions Transact-SQL au lieu d'une entrée valide. Si l'entrée est transmise directement au serveur sans validation et si l'application exécute accidentellement le code injecté, l'attaque risque d'endommager ou de détruire des données. Vous pouvez déjouer les attaques d'injection SQL Server à l'aide de procédures stockées et de commandes paramétrées, en évitant le code SQL dynamique et en limitant les autorisations de tous les utilisateurs.   
  
### <a name="elevation-of-privilege"></a>Élévation de privilège  
 Les attaques d'élévation de privilège se produisent lorsqu'un utilisateur s'empare des privilèges d'un compte approuvé, un administrateur ou un propriétaire par exemple. Exécutez toujours le code sous des comptes d'utilisateurs disposant des privilèges minimum et attribuez uniquement les autorisations nécessaires. Évitez l'utilisation des comptes d'administrateur ou de propriétaire pour l'exécution du code. Ainsi, vous limitez l'étendue des dommages qui peuvent se produire si une attaque réussit. Lorsque vous effectuez des tâches qui nécessitent des autorisations supplémentaires, utilisez la signature de procédure ou l'emprunt d'identité pour la durée de la tâche. Vous pouvez signer les procédures stockées à l'aide de certificats ou utiliser l'emprunt d'identité pour affecter des autorisations de manière temporaire.  
  
### <a name="probing-and-intelligent-observation"></a>Détection des attaques et surveillance intelligente  
 Une attaque de détection peut utiliser des messages d'erreur générés par une application pour rechercher des vulnérabilités dans la sécurité. Implémentez la gestion des erreurs dans tout le code de procédure pour éviter de retourner des informations d'erreurs SQL Server à l'utilisateur final.  
  
### <a name="authentication"></a>Authentification  
 Une attaque par injection de chaîne de connexion peut se produire lors de l'utilisation de connexions SQL Server si une chaîne de connexion basée sur l'entrée d'utilisateur est construite au moment de l'exécution. Si la vérification de paires de mots clés valides n'est pas effectuée au niveau de la chaîne de connexion, un attaquant peut insérer des caractères supplémentaires et accéder éventuellement à des données sensibles ou à d'autres ressources sur le serveur. Utilisez l'authentification Windows lorsque cela est possible. Si vous devez utiliser des connexions SQL Server, utilisez <xref:System.Data.SqlClient.SqlConnectionStringBuilder> pour créer et valider des chaînes de connexion au moment de l'exécution.  
  
### <a name="passwords"></a>Mots de passe  
 De nombreuses attaques réussissent lorsqu'un intrus a su deviner ou se procurer le mot de passe d'un utilisateur privilégié. Les mots de passe représentent la première ligne de défense contre les intrus, la définition de mots de passe forts est donc un élément essentiel de la sécurité de votre système. Créez et appliquez des stratégies de mot de passe pour l'authentification en mode mixte.  
  
 Affectez toujours un mot de passe fort au compte `sa`, même lorsque vous utilisez l'authentification Windows.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Gestion des autorisations avec les procédures stockées dans SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 Décrit comment utiliser des procédures stockées pour gérer les autorisations et contrôler l'accès aux données. L'utilisation des procédures stockées est un moyen efficace pour pallier de nombreuses menaces concernant la sécurité.  
  
 [Écriture de code SQL dynamique sécurisé dans SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 Décrit des techniques permettant d'écrire du code SQL dynamique sécurisé à l'aide de procédures stockées.  
  
 [Signature de procédures stockées dans SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 Décrit comment signer une procédure stockée avec un certificat pour permettre aux utilisateurs de disposer des données auxquelles ils n'ont pas un accès direct. Cela permet aux procédures stockées d'effectuer des opérations que l'appelant n'est pas autorisé à effectuer directement.  
  
 [Personnalisation des autorisations avec l’emprunt d’identité dans SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 Décrit la manière d'utiliser la clause EXECUTE AS pour emprunter l'identité d'un autre utilisateur. L'emprunt d'identité transfère le contexte de l'exécution de l'appelant vers l'utilisateur spécifié.  
  
 [Attribution d’autorisations de niveau ligne dans SQL Server](../../../../../docs/framework/data/adonet/sql/granting-row-level-permissions-in-sql-server.md)  
 Décrit comment implémenter des autorisations au niveau de la ligne pour limiter l'accès aux données.  
  
 [Création de rôles d’application dans SQL Server](../../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md)  
 Décrit les fonctions et les fonctionnalités de rôles d’application.  
  
 [Activation de l’accès entre bases de données dans SQL Server](../../../../../docs/framework/data/adonet/sql/enabling-cross-database-access-in-sql-server.md)  
 Décrit comment activer l'accès aux bases de données croisées sans risque pour la sécurité.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [Vue d’ensemble de la sécurité SQL Server](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Sécurisation des applications ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
