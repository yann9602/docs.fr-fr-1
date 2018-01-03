---
title: Synchronisation DataSet et XmlDataDocument
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
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: acc68fd36d2887e5e951f9ba5adc20e8cfd87fd2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="84391-102">Synchronisation DataSet et XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="84391-102">DataSet and XmlDataDocument Synchronization</span></span>
<span data-ttu-id="84391-103">L'objet <xref:System.Data.DataSet> ADO.NET vous propose une représentation relationnelle des données.</span><span class="sxs-lookup"><span data-stu-id="84391-103">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="84391-104">Pour un accès hiérarchique aux données, vous pouvez utiliser les classes XML disponibles dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="84391-104">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="84391-105">Pour des raisons historiques, ces deux représentations des données ont jusqu'à présent été utilisées séparément.</span><span class="sxs-lookup"><span data-stu-id="84391-105">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="84391-106">Toutefois, le .NET Framework permet un accès synchrone et en temps réel aux représentations relationnelles et hiérarchiques des données via le **DataSet** objet et le <xref:System.Xml.XmlDataDocument> de l’objet, respectivement.</span><span class="sxs-lookup"><span data-stu-id="84391-106">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="84391-107">Lorsqu’un **DataSet** est synchronisé avec un **XmlDataDocument**, les deux objets utilisent un seul jeu de données.</span><span class="sxs-lookup"><span data-stu-id="84391-107">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="84391-108">Cela signifie que si une modification est apportée à la **DataSet**, la modification est répercutée dans le **XmlDataDocument**et vice versa.</span><span class="sxs-lookup"><span data-stu-id="84391-108">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="84391-109">La relation entre la **DataSet** et **XmlDataDocument** crée une grande souplesse en permettant à une application unique, à l’aide d’un seul jeu de données, pour accéder à l’ensemble de services intégrés autour de la **DataSet** (par exemple, les contrôles Web Forms et Windows Forms et les concepteurs Visual Studio .NET), ainsi que de la suite de services XML, y compris la feuille de style XSL (Extensible Language), XSLT (XSL Transformations) et chemin d’accès XML Language (XPath).</span><span class="sxs-lookup"><span data-stu-id="84391-109">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="84391-110">Vous n'avez pas à choisir l'ensemble de services que l'application devra utiliser, puisque les deux sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="84391-110">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="84391-111">Il existe plusieurs méthodes que vous pouvez synchroniser un **DataSet** avec un **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="84391-111">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="84391-112">Vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="84391-112">You can:</span></span>  
  
-   <span data-ttu-id="84391-113">Remplir un **DataSet** avec un schéma (c'est-à-dire une structure relationnelle) et des données, puis le synchroniser avec un nouveau **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="84391-113">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="84391-114">Vous obtenez ainsi une vue hiérarchique des données relationnelles existantes.</span><span class="sxs-lookup"><span data-stu-id="84391-114">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="84391-115">Exemple :</span><span class="sxs-lookup"><span data-stu-id="84391-115">For example:</span></span>  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema and data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema and data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    ```  
  
-   <span data-ttu-id="84391-116">Remplir un **DataSet** avec schéma uniquement (tels que fortement typé **DataSet**), synchroniser avec un **XmlDataDocument**, puis charger le  **XmlDataDocument** à partir d’un document XML.</span><span class="sxs-lookup"><span data-stu-id="84391-116">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="84391-117">Vous obtenez ainsi une vue relationnelle des données hiérarchiques existantes.</span><span class="sxs-lookup"><span data-stu-id="84391-117">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="84391-118">Les noms de table et les noms de colonnes dans votre **DataSet** schéma doit correspondre aux noms des éléments XML que vous voulez les synchroniser.</span><span class="sxs-lookup"><span data-stu-id="84391-118">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="84391-119">Cette mise en correspondance respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="84391-119">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="84391-120">Notez que le schéma de la **DataSet** doit uniquement faire correspondre les éléments XML que vous souhaitez exposer dans votre vue relationnelle.</span><span class="sxs-lookup"><span data-stu-id="84391-120">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="84391-121">De cette façon, vous pouvez disposer d'un document XML très volumineux et d'une toute petite « fenêtre » relationnelle sur ce document.</span><span class="sxs-lookup"><span data-stu-id="84391-121">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="84391-122">Le **XmlDataDocument** conserve le document XML entier même si le **DataSet** n’en expose qu’une petite partie de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="84391-122">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="84391-123">(Pour un exemple détaillé, consultez [synchronisation d’un DataSet avec un XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span><span class="sxs-lookup"><span data-stu-id="84391-123">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="84391-124">L’exemple de code suivant montre les étapes de création d’un **DataSet** remplissage de son schéma, puis sa synchronisation avec un **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="84391-124">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="84391-125">Notez que la **DataSet** schéma uniquement doit correspondre les éléments à partir de la **XmlDataDocument** que vous souhaitez exposer à l’aide la **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="84391-125">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema, but not data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema, but not data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
     <span data-ttu-id="84391-126">Impossible de charger un **XmlDataDocument** s’il est synchronisé avec un **DataSet** qui contient les données.</span><span class="sxs-lookup"><span data-stu-id="84391-126">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="84391-127">Une exception sera levée.</span><span class="sxs-lookup"><span data-stu-id="84391-127">An exception will be thrown.</span></span>  
  
-   <span data-ttu-id="84391-128">Créer un nouveau **XmlDataDocument** et charger à partir d’un document XML, puis accéder à la vue relationnelle des données à l’aide du **DataSet** propriété de la **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="84391-128">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="84391-129">Vous devez définir le schéma de la **DataSet** avant de pouvoir afficher les données dans le **XmlDataDocument** à l’aide de la **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="84391-129">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="84391-130">Là encore, les noms de table et de la colonne de noms dans votre **DataSet** schéma doit correspondre aux noms des éléments XML que vous voulez les synchroniser.</span><span class="sxs-lookup"><span data-stu-id="84391-130">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="84391-131">Cette mise en correspondance respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="84391-131">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="84391-132">L’exemple de code suivant montre comment accéder à la vue relationnelle des données dans un **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="84391-132">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
    ```vb  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument  
    Dim dataSet As DataSet = xmlDoc.DataSet  
  
    ' Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    XmlDataDocument xmlDoc = new XmlDataDocument();  
    DataSet dataSet = xmlDoc.DataSet;  
  
    // Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
 <span data-ttu-id="84391-133">Un autre avantage de la synchronisation d’un **XmlDataDocument** avec un **DataSet** préserver la fidélité d’un document XML.</span><span class="sxs-lookup"><span data-stu-id="84391-133">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="84391-134">Si le **DataSet** est remplie à partir d’un document XML à l’aide **ReadXml**, lorsque les données sont réécrites sous un document XML à l’aide **WriteXml** il peut considérablement différer de le document XML d’origine.</span><span class="sxs-lookup"><span data-stu-id="84391-134">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="84391-135">C’est parce que le **DataSet** ne conserve pas la mise en forme, telles que des espaces blancs ou informations hiérarchiques, comme l’ordre des éléments, à partir du document XML.</span><span class="sxs-lookup"><span data-stu-id="84391-135">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="84391-136">Le **DataSet** ne contient pas les éléments à partir du document XML qui ont été ignorés parce qu’ils ne correspondaient pas le schéma de la **Dataset**.</span><span class="sxs-lookup"><span data-stu-id="84391-136">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="84391-137">Synchroniser un **XmlDataDocument** avec un **DataSet** permet la mise en forme et élément la structure hiérarchique du document XML d’origine soit conservé dans le **XmlDataDocument**, tandis que la **DataSet** contient uniquement des informations données et le schéma appropriées à la **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="84391-137">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="84391-138">Lors de la synchronisation une **DataSet** avec un **XmlDataDocument**, résultats peuvent différer selon si votre <xref:System.Data.DataRelation> objets imbriqués.</span><span class="sxs-lookup"><span data-stu-id="84391-138">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="84391-139">Pour plus d’informations, consultez [d’imbrication de DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="84391-139">For more information, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="84391-140">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="84391-140">In This Section</span></span>  
 [<span data-ttu-id="84391-141">Synchronisation d’un DataSet et d’un XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="84391-141">Synchronizing a DataSet with an XmlDataDocument</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="84391-142">Montre comment synchroniser un fortement typé **DataSet**, avec un schéma minimal, avec un **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="84391-142">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="84391-143">Exécution d’une requête XPath sur un DataSet</span><span class="sxs-lookup"><span data-stu-id="84391-143">Performing an XPath Query on a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="84391-144">Présente l’exécution d’une requête XPath sur le contenu d’un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="84391-144">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="84391-145">Application d’une transformation XSLT à un DataSet</span><span class="sxs-lookup"><span data-stu-id="84391-145">Applying an XSLT Transform to a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="84391-146">Présente l’application d’une transformation XSLT au contenu d’un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="84391-146">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="84391-147">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="84391-147">Related Sections</span></span>  
 [<span data-ttu-id="84391-148">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="84391-148">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="84391-149">Décrit comment la **DataSet** interagit avec XML en tant que source de données, y compris le chargement et la persistance du contenu d’un **DataSet** en tant que données XML.</span><span class="sxs-lookup"><span data-stu-id="84391-149">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="84391-150">Imbrication de DataRelations</span><span class="sxs-lookup"><span data-stu-id="84391-150">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 <span data-ttu-id="84391-151">Explique l’importance des imbriquée **DataRelation** objets pour représenter le contenu d’un **DataSet** en tant que données XML et décrit comment créer ces relations.</span><span class="sxs-lookup"><span data-stu-id="84391-151">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 [<span data-ttu-id="84391-152">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="84391-152">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="84391-153">Décrit la **DataSet** et comment l’utiliser pour gérer les données d’application et d’interagir avec des sources de données, y compris les bases de données relationnelles et XML.</span><span class="sxs-lookup"><span data-stu-id="84391-153">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="84391-154">Contient des informations de référence sur les **XmlDataDocument** classe.</span><span class="sxs-lookup"><span data-stu-id="84391-154">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84391-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84391-155">See Also</span></span>  
 [<span data-ttu-id="84391-156">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="84391-156">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
