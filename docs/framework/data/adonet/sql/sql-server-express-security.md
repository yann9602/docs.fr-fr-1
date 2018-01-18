---
title: "Sécurité SQL Server Express"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf9cf6d9-4b05-43e9-ac7b-6cefbfcd6d4e
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6593e075d1a9d672f414cfa0cd8652f760b084e1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-express-security"></a>Sécurité SQL Server Express
Microsoft SQL Server Express Edition (SQL Server Express) repose sur Microsoft SQL Server et prend en charge la plupart des fonctionnalités du moteur de base de données. Il est conçu de telle manière que les fonctionnalités non essentielles et la connectivité réseau sont désactivées par défaut afin de réduire la surface d'exposition susceptible d'être attaquée par un utilisateur malveillant.  
  
 SQL Server Express est généralement installé en tant qu'instance nommée. Le nom par défaut de cette instance est `SQLExpress`. Une instance nommée est identifiée par le nom de réseau de l'ordinateur auquel est ajouté le nom d'instance spécifié au cours de l'installation.  
  
## <a name="network-access"></a>Accès réseau  
 Pour des raisons de sécurité, les protocoles réseau sont désactivés par défaut dans SQL Server Express. Cela évite les attaques d'utilisateurs extérieurs qui risquent de compromettre l'ordinateur hébergeant l'instance de SQL Server Express. Vous devez activer explicitement la connectivité réseau et démarrer le service SQL Server Browser pour vous connecter à une instance SQL Server Express à partir d'un autre ordinateur.  
  
 Une fois la connectivité réseau activée, une instance SQL Server Express utilise les mêmes spécifications de sécurité que les autres éditions de SQL Server.  
  
## <a name="user-instances"></a>Instances utilisateur  
 Une instance utilisateur est une instance distincte du moteur de base de données SQL Server Express qui est générée par une instance parente de SQL Server Express. Une instance utilisateur a pour objectif principal de permettre aux utilisateurs exécutant Windows sous un compte d'utilisateur disposant de privilèges minimum de profiter de privilèges d'administrateur système (`sysadmin`) sur l'instance SQL Server Express qui se trouve sur leur ordinateur local. Les instances utilisateur ne s'adressent pas aux utilisateurs qui sont des administrateurs système sur leurs propres ordinateurs.  
  
 Une instance utilisateur est générée à partir d'une instance principale de SQL Server ou de SQL Server Express au nom d'un utilisateur. Elle s'exécute en tant que processus utilisateur dans le contexte de sécurité Windows de l'utilisateur, et non en tant que service. Les connexions SQL Server ne sont pas autorisées ; seules les connexions Windows sont prises en charge. Cela empêche un logiciel s'exécutant sur une instance utilisateur d'apporter des modifications à l'échelle du système que l'utilisateur ne serait pas autorisé à effectuer. Une instance utilisateur est également appelée instance enfant ou instance cliente, et est parfois référencée par l'acronyme RANU (« run as normal user »).  
  
 Chaque instance utilisateur est isolée de son instance parente et des autres instances utilisateur s'exécutant sur un même ordinateur. Les bases de données installées sur des instances utilisateur sont ouvertes en mode mono-utilisateur uniquement ; plusieurs utilisateurs ne peuvent pas s'y connecter. La réplication, les requêtes distribuées et les connexions distantes sont désactivées pour les instances utilisateur. Les utilisateurs connectés à une instance utilisateur ne disposent pas de privilèges spéciaux sur l'instance SQL Server Express parente.  
  
## <a name="external-resources"></a>Ressources externes  
 Pour plus d'informations sur SQL Server Express, consultez les ressources répertoriées ci-dessous.  
  
|||  
|-|-|  
|[Documentation en ligne de SQL Server](http://msdn.microsoft.com/library/bb543165.aspx)|Contient la documentation relative à SQL Server Express.|  
|[Connexion à SQL Server Express](http://msdn.microsoft.com/library/ms165679.aspx) dans la documentation en ligne de SQL Server|Décrit comment utiliser SQL Server Express Edition sur un réseau.|  
|[Documentation en ligne de Microsoft SQL Server 2005 Express Edition](http://msdn.microsoft.com/library/ms165706.aspx)|Documentation complète relative à SQL Server 2005 Express Edition.|  
|[Les Instances d’utilisateur pour les non-administrateurs](http://msdn.microsoft.com/library/ms143684.aspx) dans la documentation en ligne de SQL Server|Décrit comment créer et déployer des instances utilisateur.|  
|[Instances utilisateur SQL Server Express](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)|Décrit les fonctionnalités des instances utilisateur dans une application ADO.NET. Fournit des informations sur l'activation d'une interface utilisateur, la connexion à une instance utilisateur à l'aide d'un <xref:System.Data.SqlClient.SqlConnection>, la durée de vie d'une instance utilisateur et des scénarios d'instance utilisateur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [Instances utilisateur SQL Server Express](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
