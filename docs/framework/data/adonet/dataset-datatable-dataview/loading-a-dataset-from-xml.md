---
title: "Chargement d'un DataSet à partir de XML"
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
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1d17bb97811bb3a2ae979e5a05b8d39baf2b9c63
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="loading-a-dataset-from-xml"></a>Chargement d'un DataSet à partir de XML
Le contenu d'un objet <xref:System.Data.DataSet> ADO.NET peut être recréé à partir d'un flux ou d'un document XML. En outre, le .NET Framework vous offre une grande souplesse en ce qui concerne les informations qui seront chargées à partir de XML et le mode de création du schéma ou de la structure relationnelle de l'objet <xref:System.Data.DataSet>.  
  
 Pour remplir un <xref:System.Data.DataSet> avec des données à partir de XML, utilisez la **ReadXml** méthode de la <xref:System.Data.DataSet> objet. Le **ReadXml** méthode lit à partir d’un fichier, un flux, ou une **XmlReader**et prend comme arguments la source du XML et éventuellement une **XmlReadMode** argument. (Pour plus d’informations sur la **XmlReader**, consultez [NIB : lire des données XML avec XmlTextReader](http://msdn.microsoft.com/library/762c069b-b50c-41b8-936e-39eacfb0d540).) Le **ReadXml** méthode lit le contenu du flux XML ou du document et charge le <xref:System.Data.DataSet> avec des données. Elle créera également le schéma relationnel de la <xref:System.Data.DataSet> selon la **XmlReadMode** spécifié et un schéma relationnel existe déjà ou non.  
  
 Le tableau suivant décrit les options pour le **XmlReadMode** argument.  
  
|Option|Description|  
|------------|-----------------|  
|**Auto**|Il s'agit de la valeur par défaut. Examine le XML et choisit l'option la mieux appropriée, dans l'ordre suivant :<br /><br /> -Si le XML est un DiffGram, **DiffGram** est utilisé.<br />-If le <xref:System.Data.DataSet> contient un schéma ou le code XML contient un schéma inline, **ReadSchema** est utilisé.<br />-If le <xref:System.Data.DataSet> ne contient pas de schéma et le code XML ne contient pas de schéma inline, **InferSchema** est utilisé.<br /><br /> Si vous connaissez le format du XML en cours de lecture, pour de meilleures performances qu’il est recommandé de définir explicite **XmlReadMode**, plutôt que d’accepter les **automatique** par défaut.|  
|**ReadSchema**|Lit les schémas inline et charge les données et les schémas.<br /><br /> Si l'objet <xref:System.Data.DataSet> contient déjà un schéma, les nouvelles tables sont ajoutées du schéma inline au schéma existant dans l'objet <xref:System.Data.DataSet>. Si des tables du schéma inline existent déjà dans l'objet <xref:System.Data.DataSet>, une exception est levée. Vous ne pourrez pas modifier le schéma d’une table existante en utilisant **XmlReadMode.ReadSchema**.<br /><br /> Si l'objet <xref:System.Data.DataSet> ne contient pas de schéma et qu'il n'existe pas de schéma inline, les données ne sont pas lues.<br /><br /> Un schéma inline peut être défini à l'aide d'un schéma en langage XSD (XML Schema Definition). Pour plus d’informations sur l’écriture du schéma inline sous forme de schéma XML, consultez [dérivant Structure relationnelle des DataSet à partir de XSD (XML Schema)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).|  
|**IgnoreSchema**|Ignore les schémas inline et charge les données dans le schéma existant de l'objet <xref:System.Data.DataSet>. Toute donnée ne correspondant pas au schéma existant est ignorée. S'il n'existe pas de schéma dans l'objet <xref:System.Data.DataSet>, aucune donnée n'est chargée.<br /><br /> Si les données sont un DiffGram, **IgnoreSchema** a les mêmes fonctionnalités que **DiffGram** *.*|  
|**InferSchema**|Ignore tout schéma inline et déduit le schéma de la structure des données XML, puis charge les données.<br /><br /> Si le <xref:System.Data.DataSet> contient déjà un schéma, le schéma en cours est étendu par l'ajout de colonnes dans les tables existantes. Des tables supplémentaires ne seront pas ajoutées s'il n'existe pas de tables. Une exception est levée si une table déduite existe déjà avec un autre espace de noms, ou en cas de conflit entre des colonnes inférées et des colonnes existantes.<br /><br /> Pour plus d’informations sur la façon **ReadXmlSchema** déduit un schéma à partir d’un document XML, consultez [déduction Structure relationnelle des DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).|  
|**DiffGram**|Lit un DiffGram et ajoute les données au schéma en cours. **DiffGram** fusionne les nouvelles lignes avec les lignes existantes lorsqu’elles ont l’identificateur unique. Voir « Fusion de données provenant de XML » à la fin de cette rubrique. Pour plus d’informations sur les DiffGrams, consultez [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).|  
|**Fragment**|Poursuit la lecture de plusieurs fragments XML jusqu'à ce que la fin du flux soit atteinte. Les fragments qui correspondent au schéma de l'objet <xref:System.Data.DataSet> sont ajoutés aux tables appropriées. Les fragments qui ne correspondent pas au schéma <xref:System.Data.DataSet> sont écartés.|  
  
> [!NOTE]
>  Si vous passez un **XmlReader** à **ReadXml** qui est positionné au cours de le dans un document XML, **ReadXml** lira jusqu’au nœud d’élément suivant et qui traitera comme racine élément, la lecture jusqu'à la fin du nœud d’élément uniquement. Cela ne s’applique pas si vous spécifiez **XmlReadMode.Fragment**.  
  
## <a name="dtd-entities"></a>Entités DTD  
 Si votre XML contient des entités définies dans un schéma DTD (définition) de type de document, une exception est levée si vous tentez de charger un <xref:System.Data.DataSet> en passant un fichier de nom, de flux ou de non validant **XmlReader** à  **ReadXml**. Au lieu de cela, vous devez créer un **XmlValidatingReader**, avec **EntityHandling** la valeur **EntityHandling.ExpandEntities**et passer votre  **XmlValidatingReader** à **ReadXml**. Le **XmlValidatingReader** développera les entités avant la lecture par le <xref:System.Data.DataSet>.  
  
 Les exemples de code suivants montrent comment charger un objet <xref:System.Data.DataSet> à partir d'un flux XML. Le premier exemple montre un nom de fichier passé à la **ReadXml** (méthode). Le second illustre le cas d'une chaîne contenant le XML chargé à l'aide d'un objet <xref:System.IO.StringReader>.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema);  
```  
  
```vb  
Dim dataSet As DataSet = New DataSet  
Dim dataTable As DataTable = New DataTable("table1")  
dataTable.Columns.Add("col1", Type.GetType("System.String"))  
dataSet.Tables.Add(dataTable)  
  
Dim xmlData As String = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>"  
  
Dim xmlSR As System.IO.StringReader = New System.IO.StringReader(xmlData)  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
DataTable dataTable = new DataTable("table1");  
dataTable.Columns.Add("col1", typeof(string));  
dataSet.Tables.Add(dataTable);  
  
string xmlData = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>";  
  
System.IO.StringReader xmlSR = new System.IO.StringReader(xmlData);  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema);  
```  
  
> [!NOTE]
>  Si vous appelez **ReadXml** pour charger un fichier très volumineux, vous pouvez rencontrer le ralentissement des performances. Pour garantir des performances optimales pour **ReadXml**, sur un fichier volumineux, appelez le <xref:System.Data.DataTable.BeginLoadData%2A> méthode pour chaque table dans la <xref:System.Data.DataSet>, puis appelez **ReadXml**. Enfin, appelez <xref:System.Data.DataTable.EndLoadData%2A> pour chaque table de l'objet <xref:System.Data.DataSet>, comme le montre l'exemple suivant.  
  
```vb  
Dim dataTable As DataTable  
  
For Each dataTable In dataSet.Tables  
   dataTable.BeginLoadData()  
Next  
  
dataSet.ReadXml("file.xml")  
  
For Each dataTable in dataSet.Tables  
   dataTable.EndLoadData()  
Next  
```  
  
```csharp  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.BeginLoadData();  
  
dataSet.ReadXml("file.xml");   
  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.EndLoadData();  
```  
  
> [!NOTE]
>  Si le schéma XSD de votre <xref:System.Data.DataSet> inclut un **targetNamespace**, les données ne peuvent pas être lues et vous pouvez rencontrer des exceptions, lors de l’appel **ReadXml** pour charger le <xref:System.Data.DataSet> XML qui contient éléments sans espace de noms qualifiant. Pour lire des éléments non qualifiés dans ce cas, définissez **elementFormDefault** égal sur « qualified » dans votre schéma XSD. Exemple :  
  
```xml  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a>Fusion de données provenant de XML  
 Si l'objet <xref:System.Data.DataSet> contient déjà des données, les nouvelles données provenant de XML sont ajoutées aux données déjà présentes dans l'objet <xref:System.Data.DataSet>. **ReadXml** ne fusionne pas du code XML dans le <xref:System.Data.DataSet> les informations de ligne avec des clés primaires correspondantes. Pour remplacer les informations de ligne existantes avec de nouvelles informations à partir de XML, utilisez **ReadXml** pour créer un nouveau <xref:System.Data.DataSet>, puis <xref:System.Data.DataSet.Merge%2A> nouveau <xref:System.Data.DataSet> dans existants <xref:System.Data.DataSet>. Notez que charger un DiffGram en utilisant **ReadXML** avec un **XmlReadMode** de **DiffGram** fusionnera les lignes qui ont le même identificateur unique.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>  
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [Dérivation de la structure relationnelle des DataSets à partir du schéma XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [Inférence de la structure relationnelle d’un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Chargement des informations de schéma de DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [DataSets, DataTables et DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
