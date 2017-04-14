---
title: "Chargement d&#39;un DataSet &#224; partir de XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Chargement d&#39;un DataSet &#224; partir de XML
Le contenu d'un objet <xref:System.Data.DataSet> ADO.NET peut être recréé à partir d'un flux ou d'un document XML.  En outre, le .NET Framework vous offre une grande souplesse en ce qui concerne les informations qui seront chargées à partir de XML et le mode de création du schéma ou de la structure relationnelle de l'objet <xref:System.Data.DataSet>.  
  
 Pour remplir un objet <xref:System.Data.DataSet> de données provenant de XML, utilisez la méthode **ReadXml** de l'objet <xref:System.Data.DataSet>.  La méthode **ReadXml** lit un fichier, un flux ou un **XmlReader** et prend comme arguments la source du XML et un argument **XmlReadMode** facultatif.  \(Pour plus d'informations sur la méthode **XmlReader**, voir [NIB: Reading XML Data with XmlTextReader](http://msdn.microsoft.com/fr-fr/762c069b-b50c-41b8-936e-39eacfb0d540).\) La méthode **ReadXml** lit le contenu du flux ou du document XML et remplit l'objet <xref:System.Data.DataSet> de données.  Elle créera également le schéma relationnel de l'objet <xref:System.Data.DataSet> en fonction du **XmlReadMode** spécifié et selon que ce schéma est ou non déjà défini.  
  
 Le tableau suivant décrit les options de l'argument **XmlReadMode**.  
  
|Option|Description|  
|------------|-----------------|  
|**Auto**|Il s'agit de la valeur par défaut.  Examine le XML et choisit l'option la mieux appropriée, dans l'ordre suivant :<br /><br /> -   Si le XML est un DiffGram, c'est l'option **DiffGram** qui est retenue.<br />-   Si l'objet <xref:System.Data.DataSet> contient un schéma ou si le XML contient un schéma inline, c'est l'option **ReadSchema** qui est utilisée.<br />-   Si l'objet <xref:System.Data.DataSet> ne contient pas de schéma et si le XML ne contient pas de schéma inline, c'est l'option **InferSchema** qui est utilisée.<br /><br /> Si vous connaissez le format du XML lu, il est préférable, pour obtenir de meilleures performances, que vous définissiez un **XmlReadMode** explicite plutôt que d'accepter l'option par défaut **Auto**.|  
|**ReadSchema**|Lit les schémas inline et charge les données et les schémas.<br /><br /> Si l'objet <xref:System.Data.DataSet> contient déjà un schéma, les nouvelles tables sont ajoutées du schéma inline au schéma existant dans l'objet <xref:System.Data.DataSet>.  Si des tables du schéma inline existent déjà dans l'objet <xref:System.Data.DataSet>, une exception est levée.  Vous ne pourrez pas modifier le schéma d'une table existante à l'aide de **XmlReadMode.ReadSchema**.<br /><br /> Si l'objet <xref:System.Data.DataSet> ne contient pas de schéma et qu'il n'existe pas de schéma inline, les données ne sont pas lues.<br /><br /> Un schéma inline peut être défini à l'aide d'un schéma en langage XSD \(XML Schema Definition\).  Pour plus d'informations sur l'écriture d'un schéma inline sous forme de schéma XML, voir [Dérivation de la structure relationnelle d'un DataSet à partir d'un schéma XML \(XSD\)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).|  
|**IgnoreSchema**|Ignore les schémas inline et charge les données dans le schéma existant de l'objet <xref:System.Data.DataSet>.  Toute donnée ne correspondant pas au schéma existant est ignorée.  S'il n'existe pas de schéma dans l'objet <xref:System.Data.DataSet>, aucune donnée n'est chargée.<br /><br /> Si les données sont un DiffGram, **IgnoreSchema** a la même fonctionnalité que **DiffGram** *.*|  
|**InferSchema**|Ignore tout schéma inline et déduit le schéma de la structure des données XML, puis charge les données.<br /><br /> Si le <xref:System.Data.DataSet> contient déjà un schéma, le schéma en cours est étendu par l'ajout de colonnes dans les tables existantes.  Des tables supplémentaires ne seront pas ajoutées s'il n'existe pas de tables.  Une exception est levée si une table déduite existe déjà avec un autre espace de noms, ou en cas de conflit entre des colonnes inférées et des colonnes existantes.<br /><br /> Pour plus d'informations sur la façon dont **ReadXmlSchema** déduit un schéma à partir d'un document XML, voir [Inférence de la structure relationnelle d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).|  
|**DiffGram**|Lit un DiffGram et ajoute les données au schéma en cours.  **DiffGram** fusionne les nouvelles lignes avec les lignes existantes lorsqu'elles ont le même identificateur unique.  Voir « Fusion de données provenant de XML » à la fin de cette rubrique.  Pour plus d'informations sur DiffGrams, voir [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).|  
|**Fragment**|Poursuit la lecture de plusieurs fragments XML jusqu'à ce que la fin du flux soit atteinte.  Les fragments qui correspondent au schéma de l'objet <xref:System.Data.DataSet> sont ajoutés aux tables appropriées.  Les fragments qui ne correspondent pas au schéma <xref:System.Data.DataSet> sont écartés.|  
  
> [!NOTE]
>  Si vous passez à **ReadXml** un **XmlReader** situé dans un document XML, **ReadXml** lira jusqu'au nœud d'élément suivant, qu'il considérera comme étant l'élément racine et ne poursuivra sa lecture que jusqu'à la fin de ce nœud d'élément.  Cette règle ne s'applique pas si vous spécifiez **XmlReadMode.Fragment**.  
  
## Entités DTD  
 Si votre XML contient des entités définies dans un schéma DTD \(Document Type Definition\), une exception sera levée si vous tentez de charger un objet <xref:System.Data.DataSet> en passant un nom de fichier, un flux ou un **XmlReader** non validant à **ReadXml**.  Pour éviter cela, vous devez créer un **XmlValidatingReader**, avec un **EntityHandling** ayant pour valeur **EntityHandling.ExpandEntities**, et passer votre **XmlValidatingReader** à **ReadXml**.  Le **XmlValidatingReader** développera les entités avant la lecture par l'objet <xref:System.Data.DataSet>.  
  
 Les exemples de code suivants montrent comment charger un objet <xref:System.Data.DataSet> à partir d'un flux XML.  Le premier illustre le cas d'un nom de fichier passé à la méthode **ReadXml**.  Le second illustre le cas d'une chaîne contenant le XML chargé à l'aide d'un objet <xref:System.IO.StringReader>.  
  
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
>  Si vous appelez **ReadXml** pour charger un fichier très volumineux, il est possible que vous constatiez une dégradation des performances.  Pour garantir les meilleures performances lorsque **ReadXml** est utilisé avec un fichier volumineux, appelez la méthode <xref:System.Data.DataTable.BeginLoadData%2A> pour chaque table de l'objet <xref:System.Data.DataSet>, puis **ReadXml**.  Enfin, appelez <xref:System.Data.DataTable.EndLoadData%2A> pour chaque table de l'objet <xref:System.Data.DataSet>, comme le montre l'exemple suivant.  
  
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
>  Si le schéma XSD de votre objet <xref:System.Data.DataSet> inclut un **targetNamespace**, les données risquent de ne pas être lues. Cela peut entraîner la levée d'exceptions lors de l'appel à **ReadXml** pour le chargement de l'objet <xref:System.Data.DataSet> avec des données XML contenant des éléments qui ne sont pas qualifiés à l'aide d'un espace de noms.  Dans ce cas, pour lire les éléments non qualifiés, définissez pour **elementFormDefault** une valeur égale à « qualified » dans votre schéma XSD.  Par exemple :  
  
```  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## Fusion de données provenant de XML  
 Si l'objet <xref:System.Data.DataSet> contient déjà des données, les nouvelles données provenant de XML sont ajoutées aux données déjà présentes dans l'objet <xref:System.Data.DataSet>.  **ReadXml** ne fusionne pas les informations de ligne avec les clés primaires correspondantes du XML vers l'objet <xref:System.Data.DataSet>.  Pour remplacer les informations de ligne existantes par de nouvelles informations provenant de XML, utilisez **ReadXml** pour créer un nouvel objet <xref:System.Data.DataSet>, puis <xref:System.Data.DataSet.Merge%2A> le nouvel objet <xref:System.Data.DataSet> dans l'objet <xref:System.Data.DataSet> existant.  Notez que charger un DiffGram en utilisant **ReadXML** avec un argument **XmlReadMode** ayant pour valeur **DiffGram** fusionnera les lignes qui ont le même identificateur unique.  
  
## Voir aussi  
 <xref:System.Data.DataSet.Merge%2A?displayProperty=fullName>   
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)   
 [Dérivation de la structure relationnelle d'un DataSet à partir d'un schéma XML \(XSD\)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)   
 [Inférence de la structure relationnelle d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [Chargement des informations de schéma d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)