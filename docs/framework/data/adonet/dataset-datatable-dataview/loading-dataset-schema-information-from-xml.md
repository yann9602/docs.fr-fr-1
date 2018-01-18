---
title: "Chargement des informations de schéma de DataSet à partir de XML"
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
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8b814715782710994f18163ccfcd3db342199145
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="c03b8-102">Chargement des informations de schéma de DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="c03b8-102">Loading DataSet Schema Information from XML</span></span>
<span data-ttu-id="c03b8-103">Le schéma d’un <xref:System.Data.DataSet> (ses tables, colonnes, relations et contraintes) peuvent être définis par programme, créé par le **remplir** ou **FillSchema** méthodes d’un <xref:System.Data.Common.DataAdapter>, ou chargé à partir d’un Document XML.</span><span class="sxs-lookup"><span data-stu-id="c03b8-103">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="c03b8-104">Pour charger **DataSet** informations de schéma à partir d’un document XML, vous pouvez utiliser la **ReadXmlSchema** ou **InferXmlSchema** méthode de la **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="c03b8-104">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="c03b8-105">**ReadXmlSchema** vous permet de charger ou de déduire **DataSet** les informations de schéma à partir du document contenant le schéma de langage (XSD XML) de définition de schéma XML ou un document XML avec le schéma XML inline.</span><span class="sxs-lookup"><span data-stu-id="c03b8-105">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="c03b8-106">**InferXmlSchema** vous permet de déduire le schéma à partir du document XML tout en ignorant certains espaces de noms XML que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="c03b8-106">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c03b8-107">Classement des tables dans un **DataSet** risquent de ne pas être conservés lorsque vous utilisez des services Web ou la sérialisation XML pour transférer un **DataSet** qui a été créé en mémoire à l’aide de constructions XSD (telles que des relations imbriquées).</span><span class="sxs-lookup"><span data-stu-id="c03b8-107">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="c03b8-108">Par conséquent, le destinataire de la **DataSet** ne doit pas dépendre classement des tables dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="c03b8-108">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="c03b8-109">Toutefois, classement des tables est toujours préservé si le schéma de la **DataSet** transféré a été lu à partir des fichiers XSD, au lieu d’être créé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="c03b8-109">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="c03b8-110">ReadXmlSchema</span><span class="sxs-lookup"><span data-stu-id="c03b8-110">ReadXmlSchema</span></span>  
 <span data-ttu-id="c03b8-111">Pour charger le schéma d’un **DataSet** à partir d’un document XML sans charger les données, vous pouvez utiliser la **ReadXmlSchema** méthode de la **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="c03b8-111">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="c03b8-112">**ReadXmlSchema** crée **DataSet** schéma à l’aide du schéma de langage (XSD XML) de définition de schéma XML.</span><span class="sxs-lookup"><span data-stu-id="c03b8-112">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="c03b8-113">Le **ReadXmlSchema** méthode accepte un seul argument d’un nom de fichier, un flux de données, ou un **XmlReader** contenant le document XML à charger.</span><span class="sxs-lookup"><span data-stu-id="c03b8-113">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="c03b8-114">Le document XML peut contenir uniquement le schéma ou contenir le schéma inline avec des éléments XML contenant des données.</span><span class="sxs-lookup"><span data-stu-id="c03b8-114">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="c03b8-115">Pour plus d’informations sur l’écriture du schéma inline sous forme de schéma XML, consultez [dérivant Structure relationnelle des DataSet à partir de XSD (XML Schema)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="c03b8-115">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="c03b8-116">Si le document XML passé à **ReadXmlSchema** ne contient aucune information de schéma inline, **ReadXmlSchema** déduira le schéma à partir des éléments dans le document XML.</span><span class="sxs-lookup"><span data-stu-id="c03b8-116">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="c03b8-117">Si le **DataSet** contient déjà un schéma, le schéma en cours sera étendu en ajoutant de nouvelles tables si elles n’existent pas déjà.</span><span class="sxs-lookup"><span data-stu-id="c03b8-117">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="c03b8-118">De nouvelles colonnes ne seront pas ajoutées aux tables existantes.</span><span class="sxs-lookup"><span data-stu-id="c03b8-118">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="c03b8-119">Si une colonne ajoutée déjà existe dans le **DataSet** mais a un type incompatible avec la colonne trouvée dans le XML, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="c03b8-119">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="c03b8-120">Pour plus d’informations sur la façon **ReadXmlSchema** déduit un schéma à partir d’un document XML, consultez [déduction Structure relationnelle des DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c03b8-120">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="c03b8-121">Bien que **ReadXmlSchema** charge ou déduit uniquement le schéma d’un **DataSet**, le **ReadXml** méthode de la **DataSet** charge ou déduit les deux le schéma et les données contenues dans le document XML.</span><span class="sxs-lookup"><span data-stu-id="c03b8-121">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="c03b8-122">Pour plus d’informations, consultez [chargement d’un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c03b8-122">For more information, see [Loading a DataSet from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="c03b8-123">Les exemples de code suivants montrent comment charger un **DataSet** schéma à partir d’un document XML ou un flux.</span><span class="sxs-lookup"><span data-stu-id="c03b8-123">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="c03b8-124">Le premier exemple montre un nom de fichier de schéma XML passé à la **ReadXmlSchema** (méthode).</span><span class="sxs-lookup"><span data-stu-id="c03b8-124">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="c03b8-125">Le second exemple illustre un **System.IO.StreamReader**.</span><span class="sxs-lookup"><span data-stu-id="c03b8-125">The second example shows a **System.IO.StreamReader**.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As System.IO.StreamReader = New System.IO.StreamReader ("schema.xsd");  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema(xmlStream)  
xmlStream.Close()  
```  
  
```csharp  
System.IO.StreamReader xmlStream = new System.IO.StreamReader("schema.xsd");  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema(xmlStream);  
xmlStream.Close();  
```  
  
## <a name="inferxmlschema"></a><span data-ttu-id="c03b8-126">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="c03b8-126">InferXmlSchema</span></span>  
 <span data-ttu-id="c03b8-127">Vous pouvez également demander à le **DataSet** déduise son schéma à partir d’un document XML à l’aide du **InferXmlSchema** méthode de la **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="c03b8-127">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="c03b8-128">**InferXmlSchema** fonctionne de la même manière que **ReadXml** avec un **XmlReadMode** de **InferSchema** (charge les données comme déduit le schéma) et  **ReadXmlSchema** si le document lu ne contient pas de schéma inline.</span><span class="sxs-lookup"><span data-stu-id="c03b8-128">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="c03b8-129">Toutefois, **InferXmlSchema** fournit la plus la possibilité de vous permet de spécifier des espaces de noms XML qui doivent être ignorés lorsque le schéma est déduit.</span><span class="sxs-lookup"><span data-stu-id="c03b8-129">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="c03b8-130">**InferXmlSchema** prend deux arguments requis : l’emplacement du document XML, spécifié par un nom de fichier, un flux de données, ou un **XmlReader**; un tableau de chaînes d’espaces de noms XML doivent être ignorés par l’opération.</span><span class="sxs-lookup"><span data-stu-id="c03b8-130">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="c03b8-131">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="c03b8-131">For example, consider the following XML:</span></span>  
  
```xml  
<NewDataSet xmlns:od="urn:schemas-microsoft-com:officedata">  
<Categories>  
  <CategoryID od:adotype="3">1</CategoryID>   
  <CategoryName od:maxLength="15" od:adotype="130">Beverages</CategoryName>   
  <Description od:adotype="203">Soft drinks and teas</Description>   
</Categories>  
<Products>  
  <ProductID od:adotype="20">1</ProductID>   
  <ReorderLevel od:adotype="3">10</ReorderLevel>   
  <Discontinued od:adotype="11">0</Discontinued>   
</Products>  
</NewDataSet>  
```  
  
 <span data-ttu-id="c03b8-132">En raison des attributs spécifiés pour les éléments dans le document XML précédent, à la fois le **ReadXmlSchema** (méthode) et le **ReadXml** méthode avec un **XmlReadMode** de **InferSchema** créerait des tables pour chaque élément dans le document : **catégories**, **CategoryID**, **CategoryName**, **Description**, **produits**, **ProductID**, **ReorderLevel**, et **abandonnées**.</span><span class="sxs-lookup"><span data-stu-id="c03b8-132">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="c03b8-133">(Pour plus d’informations, consultez [déduction Structure relationnelle des DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) Toutefois, une structure plus appropriée serait pour créer uniquement les **catégories** et **produits** tables, puis de créer **CategoryID**, **CategoryName** , et **Description** colonnes dans le **catégories** table, et **ProductID**, **ReorderLevel**, et **Discontinued** colonnes dans le **produits** table.</span><span class="sxs-lookup"><span data-stu-id="c03b8-133">(For more information, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="c03b8-134">Pour vous assurer que le schéma déduit ignore les attributs spécifiés dans les éléments XML, utilisez la **InferXmlSchema** (méthode) et spécifiez l’espace de noms XML **officedata** doivent être ignorés, comme indiqué dans les exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c03b8-134">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="c03b8-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c03b8-135">See Also</span></span>  
 [<span data-ttu-id="c03b8-136">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="c03b8-136">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="c03b8-137">Dérivation de la structure relationnelle des DataSets à partir du schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="c03b8-137">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [<span data-ttu-id="c03b8-138">Inférence de la structure relationnelle d’un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="c03b8-138">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="c03b8-139">Chargement d’un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="c03b8-139">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="c03b8-140">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="c03b8-140">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="c03b8-141">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="c03b8-141">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
