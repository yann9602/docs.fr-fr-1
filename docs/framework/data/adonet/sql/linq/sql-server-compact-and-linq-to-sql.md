---
title: "SQL Server Compact et LINQ to SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# SQL Server Compact et LINQ to SQL
SQL Server Compact est la base de données par défaut installée avec Visual Studio. Pour plus d'informations, consultez [PAVE OVER Using SQL Server Compact \(Visual Studio\)](http://msdn.microsoft.com/fr-fr/13320dd1-94e5-4077-bf76-8df253695ccc).  
  
 Cette rubrique présente les différences principales en termes d'utilisation, de configuration, d'ensembles de fonctionnalités et de portée du support [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
## Caractéristiques de SQL Server Compact par rapport à LINQ to SQL  
 Par défaut, SQL Server Compact est installé pour toutes les éditions de [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]. Il est donc disponible sur l'ordinateur de développement pour une utilisation avec [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  Cependant, le déploiement d'une application qui utilise SQL Server Compact et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] diffère du déploiement d'une application [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].  SQL Server Compact ne fait pas partie du .NET Framework et doit par conséquent être fourni avec l'application ou téléchargé séparément depuis le site Microsoft.  
  
 Notez les caractéristiques suivantes :  
  
-   SQL Server Compact est fourni comme une DLL qui peut être utilisée directement sur les fichiers de base de données \(extension .sdf\).  
  
-   SQL Server Compact s'exécute au cours du même processus que l'application cliente.  L'efficacité de la communication avec SQL Server Compact peut être beaucoup plus importante que la communication avec [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].  En revanche, SQL Server Compact requiert l'interopérabilité entre le code managé et le code non managé avec ses coûts connexes.  
  
-   La taille de la DLL SQL Server Compact est faible.  Cette fonctionnalité réduit la taille globale de l'application.  
  
-   Le runtime de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et l'outil en ligne de commande SQLMetal prennent en charge SQL Server Compact.  
  
-   [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ne prend pas en charge SQL Server Compact.  
  
## Jeu de fonctionnalités  
 Le jeu de fonctionnalités de SQL Server Compact est beaucoup plus simple que celui de [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] en termes d'influence sur les applications [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dans les domaines suivants :  
  
-   SQL Server Compact ne prend pas en charge de procédures stockées ou de vues.  
  
-   SQL Server Compact prend en charge uniquement un sous\-ensemble de types de données et de fonctions SQL.  
  
-   SQL Server Compact prend en charge uniquement un sous\-ensemble de constructions SQL.  
  
-   SQL Server Compact fournit uniquement un optimiseur minimal.  Il est possible que certaines requêtes expirent.  
  
-   SQL Server Compact ne prend pas en charge la confiance partielle.  
  
## Voir aussi  
 [Reference](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)