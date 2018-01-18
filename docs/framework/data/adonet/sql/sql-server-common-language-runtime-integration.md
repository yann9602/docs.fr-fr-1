---
title: "Intégration CLR SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 06c1f2909658c140b1ad84f3b0ed5d3abdafb6c6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-common-language-runtime-integration"></a>Intégration CLR SQL Server
SQL Server 2005 a introduit l'intégration du composant Common Language Runtime (CLR) de .NET Framework pour Microsoft Windows. Cela signifie que vous pouvez écrire des procédures stockées, des déclencheurs, des types définis par l'utilisateur, des fonctions définies par l'utilisateur, des agrégats définis par l'utilisateur et des fonctions de flux évaluées par une table, en utilisant tout langage .NET Framework, notamment Microsoft Visual Basic .NET et Microsoft Visual C#. L'espace de noms <xref:Microsoft.SqlServer.Server> contient un ensemble de nouvelles API permettant au code managé d'interagir avec l'environnement Microsoft SQL Server.  
  
 Cette section décrit les fonctions et les comportements spécifiques à l'intégration de CLR dans SQL Server et aux extensions spécifiques au mode in-process SQL Server pour ADO.NET.  
  
 Cette section a uniquement pour but de fournir les informations indispensables pour commencer à programmer avec l'intégration de CLR dans SQL Server et n'est nullement exhaustive. Pour obtenir des informations plus détaillées, voir la documentation en ligne de SQL Server pour la version de SQL Server que vous utilisez.  
  
 **Documentation en ligne de SQL Server**  
  
1.  [Concepts de programmation Integration Common Language Runtime (CLR)](http://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a>Dans cette section  
 [Introduction à l’intégration CLR SQL Server](../../../../../docs/framework/data/adonet/sql/introduction-to-sql-server-clr-integration.md)  
 Fournit une présentation de l'intégration de CLR dans SQL Server. Fournit des liens vers d'autres rubriques.  
  
 [Fonctions CLR définies par l’utilisateur](../../../../../docs/framework/data/adonet/sql/clr-user-defined-functions.md)  
 Décrit comment implémenter et utiliser les différents types de fonctions CLR : fonctions table, fonctions scalaires et fonctions d'agrégation définies par l'utilisateur.  
  
 [Types CLR définis par l’utilisateur](../../../../../docs/framework/data/adonet/sql/clr-user-defined-types.md)  
 Décrit comment implémenter et utiliser des types CLR définis par l'utilisateur. Fournit des liens vers d'autres rubriques.  
  
 [Procédures stockées CLR](../../../../../docs/framework/data/adonet/sql/clr-stored-procedures.md)  
 Décrit comment implémenter et utiliser des procédures stockées CLR. Fournit des liens vers d'autres rubriques.  
  
 [Déclencheurs CLR](../../../../../docs/framework/data/adonet/sql/clr-triggers.md)  
 Décrit comment implémenter et utiliser des déclencheurs CLR. Fournit des liens vers d'autres rubriques.  
  
 [Connexion de contexte](../../../../../docs/framework/data/adonet/sql/the-context-connection.md)  
 Décrit la connexion de contexte.  
  
 [Comportement SQL Server spécifique au processus d’ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-in-process-specific-behavior-of-adonet.md)  
 Décrit les extensions spécifiques au mode in-process SQL Server pour ADO.NET et la connexion de contexte. Fournit des liens vers d'autres rubriques.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server et ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [Création d’objets SQL Server 2005 dans le Code managé](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
