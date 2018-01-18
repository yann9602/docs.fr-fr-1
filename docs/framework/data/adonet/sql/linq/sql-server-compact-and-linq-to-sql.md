---
title: SQL Server Compact et LINQ to SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9409c17065b0421ec32a61352f9c0b975095ab44
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact et LINQ to SQL
SQL Server Compact est la base de données par défaut installé avec Visual Studio. Pour plus d’informations, consultez [PAVE sur à l’aide de SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/en-us/13320dd1-94e5-4077-bf76-8df253695ccc).  
  
 Cette rubrique décrit les principales différences dans l’utilisation, la configuration, ensembles de fonctionnalités et étendue de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prend en charge.  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>Caractéristiques de SQL Server Compact par rapport à LINQ to SQL  
 Par défaut, SQL Server Compact est installé pour tous les [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] éditions et est par conséquent disponible sur l’ordinateur de développement pour une utilisation avec [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Mais le déploiement d’une application qui utilise SQL Server Compact et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] diffère de celle pour une [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] application. SQL Server Compact ne fait pas partie du .NET Framework et doit par conséquent être fourni avec l'application ou téléchargé séparément depuis le site Microsoft.  
  
 Notez les caractéristiques suivantes :  
  
-   SQL Server Compact est fourni comme une DLL qui peut être utilisée directement sur les fichiers de base de données (extension .sdf).  
  
-   SQL Server Compact s’exécute dans le même processus que l’application cliente. L’efficacité de la communication avec SQL Server Compact peut par conséquent être beaucoup plus importante que la communication avec [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)]. En revanche, SQL Server Compact requiert l’interopérabilité entre le code managé et avec ses coûts connexes.  
  
-   La taille de la DLL SQL Server Compact est faible. Cette fonctionnalité réduit la taille globale de l’application.  
  
-   Le runtime de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et l'outil en ligne de commande SQLMetal prennent en charge SQL Server Compact.  
  
-   [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ne prend pas en charge SQL Server Compact.  
  
## <a name="feature-set"></a>Jeu de fonctionnalités  
 L’ensemble de fonctionnalités SQL Server Compact est beaucoup plus simple que l’ensemble des fonctionnalités de [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] manières suivantes peuvent affecter [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :  
  
-   SQL Server Compact ne prend pas en charge de procédures stockées ou de vues.  
  
-   SQL Server Compact prend en charge uniquement un sous-ensemble de types de données et de fonctions SQL.  
  
-   SQL Server Compact prend en charge uniquement un sous-ensemble de constructions SQL.  
  
-   SQL Server Compact fournit uniquement un optimiseur minimal. Il est possible que certaines requêtes peuvent expirer.  
  
-   SQL Server Compact ne prend pas en charge la confiance partielle.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
