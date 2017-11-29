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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: db507bf4f90d875960408857c7e6b1e3aa145730
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="e0a0d-102">Chargement d'un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="e0a0d-102">Loading a DataSet from XML</span></span>
<span data-ttu-id="e0a0d-103">Le contenu d'un objet <xref:System.Data.DataSet> ADO.NET peut être recréé à partir d'un flux ou d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-103">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="e0a0d-104">En outre, le .NET Framework vous offre une grande souplesse en ce qui concerne les informations qui seront chargées à partir de XML et le mode de création du schéma ou de la structure relationnelle de l'objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-104">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="e0a0d-105">Pour remplir un <xref:System.Data.DataSet> avec des données à partir de XML, utilisez la **ReadXml** méthode de la <xref:System.Data.DataSet> objet.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-105">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="e0a0d-106">Le **ReadXml** méthode lit à partir d’un fichier, un flux, ou une **XmlReader**et prend comme arguments la source du XML et éventuellement une **XmlReadMode** argument.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-106">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="e0a0d-107">(Pour plus d’informations sur la **XmlReader**, consultez [NIB : lire des données XML avec XmlTextReader](http://msdn.microsoft.com/en-us/762c069b-b50c-41b8-936e-39eacfb0d540).) Le **ReadXml** méthode lit le contenu du flux XML ou du document et charge le <xref:System.Data.DataSet> avec des données.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-107">(For more information about the **XmlReader**, see [NIB: Reading XML Data with XmlTextReader](http://msdn.microsoft.com/en-us/762c069b-b50c-41b8-936e-39eacfb0d540).) The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="e0a0d-108">Elle créera également le schéma relationnel de la <xref:System.Data.DataSet> selon la **XmlReadMode** spécifié et un schéma relationnel existe déjà ou non.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-108">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="e0a0d-109">Le tableau suivant décrit les options pour le **XmlReadMode** argument.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-109">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="e0a0d-110">Option</span><span class="sxs-lookup"><span data-stu-id="e0a0d-110">Option</span></span>|<span data-ttu-id="e0a0d-111">Description</span><span class="sxs-lookup"><span data-stu-id="e0a0d-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e0a0d-112">**Auto**</span><span class="sxs-lookup"><span data-stu-id="e0a0d-112">**Auto**</span></span>|<span data-ttu-id="e0a0d-113">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-113">This is the default.</span></span> <span data-ttu-id="e0a0d-114">Examine le XML et choisit l'option la mieux appropriée, dans l'ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="e0a0d-114">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="e0a0d-115">-Si le XML est un DiffGram, **DiffGram** est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-115">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="e0a0d-116">-If le <xref:System.Data.DataSet> contient un schéma ou le code XML contient un schéma inline, **ReadSchema** est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-116">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="e0a0d-117">-If le <xref:System.Data.DataSet> ne contient pas de schéma et le code XML ne contient pas de schéma inline, **InferSchema** est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-117">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="e0a0d-118">Si vous connaissez le format du XML en cours de lecture, pour de meilleures performances qu’il est recommandé de définir explicite **XmlReadMode**, plutôt que d’accepter les **automatique** par défaut.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-118">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|<span data-ttu-id="e0a0d-119">**ReadSchema**</span><span class="sxs-lookup"><span data-stu-id="e0a0d-119">**ReadSchema**</span></span>|<span data-ttu-id="e0a0d-120">Lit les schémas inline et charge les données et les schémas.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-120">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="e0a0d-121">Si l'objet <xref:System.Data.DataSet> contient déjà un schéma, les nouvelles tables sont ajoutées du schéma inline au schéma existant dans l'objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-121">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e0a0d-122">Si des tables du schéma inline existent déjà dans l'objet <xref:System.Data.DataSet>, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-122">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="e0a0d-123">Vous ne pourrez pas modifier le schéma d’une table existante en utilisant **XmlReadMode.ReadSchema**.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-123">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="e0a0d-124">Si l'objet <xref:System.Data.DataSet> ne contient pas de schéma et qu'il n'existe pas de schéma inline, les données ne sont pas lues.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-124">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="e0a0d-125">Un schéma inline peut être défini à l'aide d'un schéma en langage XSD (XML Schema Definition).</span><span class="sxs-lookup"><span data-stu-id="e0a0d-125">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="e0a0d-126">Pour plus d’informations sur l’écriture du schéma inline sous forme de schéma XML, consultez [dérivant Structure relationnelle des DataSet à partir de XSD (XML Schema)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="e0a0d-126">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|<span data-ttu-id="e0a0d-127">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="e0a0d-127">**IgnoreSchema**</span></span>|<span data-ttu-id="e0a0d-128">Ignore les schémas inline et charge les données dans le schéma existant de l'objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-128">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="e0a0d-129">Toute donnée ne correspondant pas au schéma existant est ignorée.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-129">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="e0a0d-130">S'il n'existe pas de schéma dans l'objet <xref:System.Data.DataSet>, aucune donnée n'est chargée.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-130">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="e0a0d-131">Si les données sont un DiffGram, **IgnoreSchema** a les mêmes fonctionnalités que **DiffGram** *.*</span><span class="sxs-lookup"><span data-stu-id="e0a0d-131">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|<span data-ttu-id="e0a0d-132">**InferSchema**</span><span class="sxs-lookup"><span data-stu-id="e0a0d-132">**InferSchema**</span></span>|<span data-ttu-id="e0a0d-133">Ignore tout schéma inline et déduit le schéma de la structure des données XML, puis charge les données.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-133">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="e0a0d-134">Si le <xref:System.Data.DataSet> contient déjà un schéma, le schéma en cours est étendu par l'ajout de colonnes dans les tables existantes.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-134">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="e0a0d-135">Des tables supplémentaires ne seront pas ajoutées s'il n'existe pas de tables.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-135">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="e0a0d-136">Une exception est levée si une table déduite existe déjà avec un autre espace de noms, ou en cas de conflit entre des colonnes inférées et des colonnes existantes.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-136">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="e0a0d-137">Pour plus d’informations sur la façon **ReadXmlSchema** déduit un schéma à partir d’un document XML, consultez [déduction Structure relationnelle des DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e0a0d-137">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|<span data-ttu-id="e0a0d-138">**DiffGram**</span><span class="sxs-lookup"><span data-stu-id="e0a0d-138">**DiffGram**</span></span>|<span data-ttu-id="e0a0d-139">Lit un DiffGram et ajoute les données au schéma en cours.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-139">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="e0a0d-140">**DiffGram** fusionne les nouvelles lignes avec les lignes existantes lorsqu’elles ont l’identificateur unique.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-140">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="e0a0d-141">Voir « Fusion de données provenant de XML » à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-141">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="e0a0d-142">Pour plus d’informations sur les DiffGrams, consultez [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="e0a0d-142">For more information about DiffGrams, see [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span></span>|  
|<span data-ttu-id="e0a0d-143">**Fragment**</span><span class="sxs-lookup"><span data-stu-id="e0a0d-143">**Fragment**</span></span>|<span data-ttu-id="e0a0d-144">Poursuit la lecture de plusieurs fragments XML jusqu'à ce que la fin du flux soit atteinte.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-144">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="e0a0d-145">Les fragments qui correspondent au schéma de l'objet <xref:System.Data.DataSet> sont ajoutés aux tables appropriées.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-145">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="e0a0d-146">Les fragments qui ne correspondent pas au schéma <xref:System.Data.DataSet> sont écartés.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-146">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="e0a0d-147">Si vous passez un **XmlReader** à **ReadXml** qui est positionné au cours de le dans un document XML, **ReadXml** lira jusqu’au nœud d’élément suivant et qui traitera comme racine élément, la lecture jusqu'à la fin du nœud d’élément uniquement.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-147">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="e0a0d-148">Cela ne s’applique pas si vous spécifiez **XmlReadMode.Fragment**.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-148">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="e0a0d-149">Entités DTD</span><span class="sxs-lookup"><span data-stu-id="e0a0d-149">DTD Entities</span></span>  
 <span data-ttu-id="e0a0d-150">Si votre XML contient des entités définies dans un schéma DTD (définition) de type de document, une exception est levée si vous tentez de charger un <xref:System.Data.DataSet> en passant un fichier de nom, de flux ou de non validant **XmlReader** à  **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-150">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="e0a0d-151">Au lieu de cela, vous devez créer un **XmlValidatingReader**, avec **EntityHandling** la valeur **EntityHandling.ExpandEntities**et passer votre  **XmlValidatingReader** à **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-151">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="e0a0d-152">Le **XmlValidatingReader** développera les entités avant la lecture par le <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-152">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="e0a0d-153">Les exemples de code suivants montrent comment charger un objet <xref:System.Data.DataSet> à partir d'un flux XML.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-153">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="e0a0d-154">Le premier exemple montre un nom de fichier passé à la **ReadXml** (méthode).</span><span class="sxs-lookup"><span data-stu-id="e0a0d-154">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="e0a0d-155">Le second illustre le cas d'une chaîne contenant le XML chargé à l'aide d'un objet <xref:System.IO.StringReader>.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-155">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
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
>  <span data-ttu-id="e0a0d-156">Si vous appelez **ReadXml** pour charger un fichier très volumineux, vous pouvez rencontrer le ralentissement des performances.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-156">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="e0a0d-157">Pour garantir des performances optimales pour **ReadXml**, sur un fichier volumineux, appelez le <xref:System.Data.DataTable.BeginLoadData%2A> méthode pour chaque table dans la <xref:System.Data.DataSet>, puis appelez **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-157">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="e0a0d-158">Enfin, appelez <xref:System.Data.DataTable.EndLoadData%2A> pour chaque table de l'objet <xref:System.Data.DataSet>, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-158">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="e0a0d-159">Si le schéma XSD de votre <xref:System.Data.DataSet> inclut un **targetNamespace**, les données ne peuvent pas être lues et vous pouvez rencontrer des exceptions, lors de l’appel **ReadXml** pour charger le <xref:System.Data.DataSet> XML qui contient éléments sans espace de noms qualifiant.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-159">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="e0a0d-160">Pour lire des éléments non qualifiés dans ce cas, définissez **elementFormDefault** égal sur « qualified » dans votre schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-160">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="e0a0d-161">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e0a0d-161">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="e0a0d-162">Fusion de données provenant de XML</span><span class="sxs-lookup"><span data-stu-id="e0a0d-162">Merging Data from XML</span></span>  
 <span data-ttu-id="e0a0d-163">Si l'objet <xref:System.Data.DataSet> contient déjà des données, les nouvelles données provenant de XML sont ajoutées aux données déjà présentes dans l'objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-163">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e0a0d-164">**ReadXml** ne fusionne pas du code XML dans le <xref:System.Data.DataSet> les informations de ligne avec des clés primaires correspondantes.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-164">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="e0a0d-165">Pour remplacer les informations de ligne existantes avec de nouvelles informations à partir de XML, utilisez **ReadXml** pour créer un nouveau <xref:System.Data.DataSet>, puis <xref:System.Data.DataSet.Merge%2A> nouveau <xref:System.Data.DataSet> dans existants <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-165">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e0a0d-166">Notez que charger un DiffGram en utilisant **ReadXML** avec un **XmlReadMode** de **DiffGram** fusionnera les lignes qui ont le même identificateur unique.</span><span class="sxs-lookup"><span data-stu-id="e0a0d-166">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0a0d-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0a0d-167">See Also</span></span>  
 <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="e0a0d-168">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="e0a0d-168">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="e0a0d-169">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="e0a0d-169">DiffGrams</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [<span data-ttu-id="e0a0d-170">Structure relationnelle des DataSet qui dérivent de schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="e0a0d-170">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [<span data-ttu-id="e0a0d-171">Déduire la Structure relationnelle des DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="e0a0d-171">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="e0a0d-172">Chargement des informations de schéma d’un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="e0a0d-172">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="e0a0d-173">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="e0a0d-173">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="e0a0d-174">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="e0a0d-174">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
