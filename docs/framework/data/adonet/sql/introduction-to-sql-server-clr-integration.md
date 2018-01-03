---
title: "Introduction à l'intégration CLR SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: fe93dc09019938e86279fd6996cd396b290ea3d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="introduction-to-sql-server-clr-integration"></a>Introduction à l'intégration CLR SQL Server
Le Common Language Runtime (CLR) est au cœur de Microsoft .NET Framework et fournit l'environnement d'exécution pour tout le code .NET Framework. Le code qui s'exécute dans le CLR est appelé code managé. Le CLR fournit divers services et fonctions requis pour l'exécution du programme, notamment la compilation juste-à-temps (JIT), l'allocation et la gestion de mémoire, l'application de sécurité de type, la gestion des exceptions, la gestion des threads et la sécurité.  
  
 Avec le CLR hébergé dans Microsoft SQL Server (intégration de CLR), vous pouvez créer des procédures stockées, des déclencheurs, des fonctions définies par l'utilisateur, des types définis par l'utilisateur et des agrégats définis par l'utilisateur dans un code managé. Comme le code managé est compilé en code natif avant exécution, vous pouvez obtenir des améliorations significatives des performances dans certains scénarios.  
  
 Le code managé utilise la sécurité d'accès du code CAS (Code Access Security), des liaisons de code et des domaines d'application pour empêcher les assemblys d'effectuer certaines opérations. SQL Server utilise CAS pour vous aider à sécuriser le code managé et empêcher toute compromission du système d'exploitation ou du serveur de base de données.  
  
 Cette section a uniquement pour but de fournir les informations indispensables pour commencer à programmer avec l'intégration de CLR dans SQL Server et n'est nullement exhaustive. Pour obtenir des informations plus détaillées, voir la documentation en ligne de SQL Server pour la version de SQL Server que vous utilisez.  
  
 **Documentation en ligne de SQL Server**  
  
-   [Vue d’ensemble de Common Language Runtime (CLR) intégration](http://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a>Activation de l'intégration de CLR  
 La fonction d'intégration de Common Language Runtime (CLR) est désactivée par défaut dans Microsoft SQL Server et doit être activée afin d'utiliser des objets implémentés à l'aide de l'intégration de CLR. Pour activer l'intégration de CLR à l'aide de Transact-SQL, utilisez l'option `clr enabled` de la procédure stockée `sp_configure` comme indiqué :  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 Vous pouvez désactiver l'intégration de CLR en attribuant à l'option `clr enabled` la valeur 0. Lorsque vous désactivez l'intégration de CLR, SQL Server arrête d'exécuter toutes les routines CLR et décharge tous les domaines d'application.  
  
 Pour obtenir des informations plus détaillées, voir la documentation en ligne de SQL Server pour la version de SQL Server que vous utilisez.  
  
 **Documentation en ligne de SQL Server**  
  
-   [Activation de l’intégration du CLR](http://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a>Déploiement d'un assembly CLR  
 Une fois que les méthodes CLR ont été testées et vérifiées sur le serveur de test, elles peuvent être distribuées aux serveurs de production à l'aide d'un script de déploiement. Le script de déploiement peut être généré manuellement ou à l'aide de SQL Server Management Studio. Pour obtenir des informations plus détaillées, voir la documentation en ligne de SQL Server pour la version de SQL Server que vous utilisez.  
  
 **Documentation en ligne de SQL Server**  
  
1.  [Déploiement d’objets de base de données CLR](http://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a>Sécurité d'intégration de CLR  
 Le modèle de sécurité de l'intégration de Microsoft SQL Server avec le CLR Microsoft .NET Framework gère et sécurise l'accès entre différents types d'objets CLR et non CLR s'exécutant avec SQL Server. Ces objets peuvent être appelés par une instruction Transact-SQL ou un autre objet CLR en cours d'exécution sur le serveur.  
  
 Pour obtenir des informations plus détaillées, voir la documentation en ligne de SQL Server pour la version de SQL Server que vous utilisez.  
  
 **Documentation en ligne de SQL Server**  
  
-   [Sécurité d’intégration du CLR](http://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a>Débogage d'un assembly CLR  
 Microsoft SQL Server prend en charge le débogage d'objets Transact-SQL et Common Language Runtime (CLR) dans la base de données. Le débogage fonctionne avec tous les langages : les utilisateurs peuvent accéder sans difficulté à des objets CLR à partir de Transact-SQL et inversement.  
  
 Pour obtenir des informations plus détaillées, voir la documentation en ligne de SQL Server pour la version de SQL Server que vous utilisez.  
  
 **Documentation en ligne de SQL Server**  
  
-   [Débogage d’objets de base de données CLR](http://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’objets SQL Server 2005 dans le Code managé](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [Sécurité d’accès du code et ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
