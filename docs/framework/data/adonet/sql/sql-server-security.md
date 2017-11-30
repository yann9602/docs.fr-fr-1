---
title: "Sécurité SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4f41a794916c63672ca0c844f086629f77b90aa0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-security"></a>Sécurité SQL Server
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] possède de nombreuses fonctionnalités qui prennent en charge la création d'applications de base de données sécurisées.  
  
 Les principaux éléments à prendre en compte au niveau de la sécurité, tels que le vol ou l'altération de données, concernent toutes les versions de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. L'intégrité des données doit également être prise en considération comme un problème de sécurité. Si les données ne sont pas protégées, elles peuvent devenir inutilisables si une manipulation ad hoc est autorisée et que les données sont modifiées, par inadvertance ou malveillance, avec des valeurs incorrectes ou entièrement supprimées. Par ailleurs, des exigences juridiques doivent souvent être observées, telles que le stockage correct des informations confidentielles. Le stockage de certains types de données personnelles est totalement interdit, selon les lois en vigueur dans une juridiction donnée.  
  
 Chaque version de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] présente des fonctionnalités de sécurité différentes, comme chaque version de Windows, les versions les plus récentes apportant des améliorations par rapport aux plus anciennes. Il est important de comprendre que les fonctionnalités de sécurité à elles seules ne peuvent pas garantir une application de base de données sécurisée. Chaque application de base de données est unique au niveau de sa configuration, de son environnement d'exécution, de son modèle de déploiement, de son emplacement physique et de ses types d'utilisateurs. Certaines applications de portée locale peuvent se contenter d'une sécurité minimale alors que d'autres applications locales ou déployées sur Internet peuvent nécessiter des mesures de sécurité strictes, ainsi qu'une surveillance et une évaluation permanentes.  
  
 Les exigences de sécurité d'une application de base de données [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] doivent être examinées au moment de la conception, et non pas à une étape ultérieure. L'évaluation des menaces aux premiers stades du cycle de développement vous donne la possibilité d'atténuer les dommages susceptibles de se produire lorsqu'une vulnérabilité est détectée.  
  
 Même si la conception initiale d'une application est fiable, de nouvelles menaces peuvent émerger à mesure que le système évolue. En créant plusieurs lignes de défense autour de vos bases de données, vous pouvez minimiser les dommages induits par une violation de la sécurité. Votre première ligne de défense consiste à réduire la surface d'attaque en n'accordant jamais plus d'autorisations que nécessaire.  
  
 Les rubriques de cette section décrivent brièvement les fonctionnalités de sécurité de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] qui concernent les développeurs et fournissent des liens vers des rubriques pertinentes dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] et d'autres ressources qui fournissent des explications plus détaillées.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble de la sécurité SQL Server](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 Décrit l'architecture et les fonctionnalités de sécurité de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
 [Scénarios de sécurité dans SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 Contient des rubriques présentant différents scénarios de sécurité pour les applications ADO.NET et [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
 [Sécurité SQL Server Express](../../../../../docs/framework/data/adonet/sql/sql-server-express-security.md)  
 Décrit les considérations sur la sécurité de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Express.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Sécurité et Protection (moteur de base de données)](http://msdn2.microsoft.com/library/bb510589\(SQL.100\).aspx.)  
 Rubriques relatives à la sécurité dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
 [Considérations de sécurité pour SQL Server](http://go.microsoft.com/fwlink/?LinkId=98587)  
 Rubriques relatives à la sécurité dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation des applications ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server et ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
