---
title: "Valeurs de colonne XML SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# Valeurs de colonne XML SQL
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] prend en charge le type de données `xml` et les développeurs peuvent extraire des ensembles de résultats incluant ce type à l'aide d'un comportement standard de la classe <xref:System.Data.SqlClient.SqlCommand>.  Une colonne `xml` peut être extraite comme toute colonne \(par exemple, dans un <xref:System.Data.SqlClient.SqlDataReader>\) mais si vous souhaitez utiliser le contenu de la colonne comme XML, vous devez utiliser un <xref:System.Xml.XmlReader>.  
  
## Exemple  
 L'application console suivante sélectionne deux lignes contenant chacune une colonne `xml` dans la table **Sales.Store** de la base de données **AdventureWorks** pour une instance de <xref:System.Data.SqlClient.SqlDataReader>.  Pour chaque ligne, la valeur de la colonne `xml` est lue à l'aide de la méthode <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> de <xref:System.Data.SqlClient.SqlDataReader>.  La valeur est stockée dans un <xref:System.Xml.XmlReader>.  Notez que vous devez utiliser la méthode <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> plutôt que la méthode <xref:System.Data.IDataRecord.GetValue%2A> si vous souhaitez définir le contenu comme une variable <xref:System.Data.SqlTypes.SqlXml> ; <xref:System.Data.IDataRecord.GetValue%2A> retourne la valeur de la colonne `xml` comme chaîne.  
  
> [!NOTE]
>  L'exemple de base de données **AdventureWorks** n'est pas installé par défaut lorsque vous installez [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  Vous pouvez l'installer en exécutant le programme d'installation de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## Voir aussi  
 <xref:System.Data.SqlTypes.SqlXml>   
 [Données XML dans SQL Server](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)