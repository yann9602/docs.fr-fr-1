---
title: "Vue d'ensemble du modèle Factory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0194cd6789ae6ddebeeee65abf1a4fca4a2bc0d6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="factory-model-overview"></a>Vue d'ensemble du modèle Factory
ADO.NET 2.0 a introduit de nouvelles classes de base dans l'espace de noms <xref:System.Data.Common>. Les classes de base sont abstraites, ce qui signifie qu'elles ne peuvent pas être directement instanciées. Il s'agit des classes <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand> et <xref:System.Data.Common.DbDataAdapter> qui sont en outre partagées par les fournisseurs de données .NET Framework, tels que <xref:System.Data.SqlClient> et <xref:System.Data.OleDb>. L'introduction de classes de base simplifie l'ajout de fonctionnalités aux fournisseurs de données .NET Framework sans avoir recours à la création de nouvelles interfaces.  
  
 ADO.NET 2.0 a également introduit des classes de base abstraites pour permettre aux développeurs d'écrire du code générique d'accès aux données qui ne dépend pas d'un fournisseur de données spécifique.  
  
## <a name="the-factory-design-pattern"></a>Modèle de design Factory  
 Le modèle de programmation permettant d'écrire du code indépendant du fournisseur repose sur l'utilisation du modèle de design « Factory ». Ce modèle utilise une seule API pour accéder à des bases de données sur plusieurs fournisseurs. Ce modèle est correctement nommé, puisqu’il invoque l’utilisation d’un objet spécialisé uniquement pour créer d’autres objets, un peu comme un véritable factory. Pour obtenir une description plus détaillée du modèle de design factory, consultez «[l’écriture de Code d’accès aux données générique dans ASP.NET 2.0 et ADO.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=55915)» et « Générique de codage avec le ADO.NET 2.0 Base de Classes et fabriques de » [http:// MSDN.Microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp](http://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp) sur MSDN.  
  
 À partir d'ADO.NET 2.0, la classe <xref:System.Data.Common.DbProviderFactories> fournit des méthodes `static` (ou `Shared` en Visual Basic) pour créer une instance <xref:System.Data.Common.DbProviderFactory>. Cette instance retourne ensuite un objet fortement typé correct reposant sur les informations du fournisseur et la chaîne de connexion fournie au moment de l'exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Obtention d’un DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [DbConnection, DbCommand et DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [Modification des données avec un DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
