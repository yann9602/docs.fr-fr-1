---
title: Valeurs des colonnes SQL XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c31ec6ae2b50870da7b999e20cd8ae44f1d42e03
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-xml-column-values"></a>Valeurs des colonnes SQL XML
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] prend en charge le type de données `xml` et les développeurs peuvent extraire des ensembles de résultats incluant ce type à l'aide d'un comportement standard de la classe <xref:System.Data.SqlClient.SqlCommand>. Une colonne `xml` peut être extraite comme toute colonne (par exemple, dans un <xref:System.Data.SqlClient.SqlDataReader>) mais si vous souhaitez utiliser le contenu de la colonne comme XML, vous devez utiliser un <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Exemple  
 L’application console suivante sélectionne deux lignes, chacune contenant une `xml` colonne, à partir de la **Sales.Store** table le **AdventureWorks** de base de données à un <xref:System.Data.SqlClient.SqlDataReader> instance. Pour chaque ligne, la valeur de la colonne `xml` est lue à l'aide de la méthode <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> de <xref:System.Data.SqlClient.SqlDataReader>. La valeur est stockée dans un <xref:System.Xml.XmlReader>. Notez que vous devez utiliser la méthode <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> plutôt que la méthode <xref:System.Data.IDataRecord.GetValue%2A> si vous souhaitez définir le contenu comme une variable <xref:System.Data.SqlTypes.SqlXml> ; <xref:System.Data.IDataRecord.GetValue%2A> retourne la valeur de la colonne `xml` comme chaîne.  
  
> [!NOTE]
>  Le **AdventureWorks** base de données exemple n’est pas installé par défaut lorsque vous installez [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. Vous pouvez l'installer en exécutant le programme d'installation de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.SqlTypes.SqlXml>  
 [Données XML dans SQL Server](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
