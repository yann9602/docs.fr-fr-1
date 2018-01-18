---
title: "Déduction de tables"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2c00dd11d4d93e5d3b0e2f1c3b75765056a10cab
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="inferring-tables"></a><span data-ttu-id="f8d24-102">Déduction de tables</span><span class="sxs-lookup"><span data-stu-id="f8d24-102">Inferring Tables</span></span>
<span data-ttu-id="f8d24-103">Lors de l'inférence du schéma d'un objet <xref:System.Data.DataSet> à partir d'un document XML, ADO.NET identifie d'abord les éléments XML qui représentent des tables.</span><span class="sxs-lookup"><span data-stu-id="f8d24-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="f8d24-104">Les structures XML suivantes résulter dans une table pour le **DataSet** schéma :</span><span class="sxs-lookup"><span data-stu-id="f8d24-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="f8d24-105">éléments avec attributs ;</span><span class="sxs-lookup"><span data-stu-id="f8d24-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="f8d24-106">éléments avec éléments enfants ;</span><span class="sxs-lookup"><span data-stu-id="f8d24-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="f8d24-107">éléments qui se répètent.</span><span class="sxs-lookup"><span data-stu-id="f8d24-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="f8d24-108">Éléments avec attributs</span><span class="sxs-lookup"><span data-stu-id="f8d24-108">Elements with Attributes</span></span>  
 <span data-ttu-id="f8d24-109">Les éléments contenant des attributs spécifiés donnent des tables déduites.</span><span class="sxs-lookup"><span data-stu-id="f8d24-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="f8d24-110">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="f8d24-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f8d24-111">Le processus d'inférence produit une table nommée « Element1 ».</span><span class="sxs-lookup"><span data-stu-id="f8d24-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="f8d24-112">**DataSet :** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f8d24-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="f8d24-113">**Table :** Element1</span><span class="sxs-lookup"><span data-stu-id="f8d24-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="f8d24-114">attr1</span><span class="sxs-lookup"><span data-stu-id="f8d24-114">attr1</span></span>|<span data-ttu-id="f8d24-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="f8d24-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="f8d24-116">value1</span><span class="sxs-lookup"><span data-stu-id="f8d24-116">value1</span></span>||  
|<span data-ttu-id="f8d24-117">value2</span><span class="sxs-lookup"><span data-stu-id="f8d24-117">value2</span></span>|<span data-ttu-id="f8d24-118">Text1</span><span class="sxs-lookup"><span data-stu-id="f8d24-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="f8d24-119">Éléments avec éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f8d24-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="f8d24-120">Les éléments possédant des éléments enfants donnent des tables déduites.</span><span class="sxs-lookup"><span data-stu-id="f8d24-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="f8d24-121">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="f8d24-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f8d24-122">Le processus d'inférence produit une table nommée « Element1 ».</span><span class="sxs-lookup"><span data-stu-id="f8d24-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="f8d24-123">**DataSet :** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f8d24-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="f8d24-124">**Table :** Element1</span><span class="sxs-lookup"><span data-stu-id="f8d24-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="f8d24-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="f8d24-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="f8d24-126">Text1</span><span class="sxs-lookup"><span data-stu-id="f8d24-126">Text1</span></span>|  
  
 <span data-ttu-id="f8d24-127">L'élément document, ou racine, donne une table déduite s'il comporte des attributs ou des éléments enfants qui sont inférés en tant que colonnes.</span><span class="sxs-lookup"><span data-stu-id="f8d24-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="f8d24-128">Si l’élément de document ne comporte pas d’attributs et pas d’éléments enfants qui seraient déduits en tant que colonnes, l’élément est déduit en tant qu’un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="f8d24-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="f8d24-129">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="f8d24-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f8d24-130">Le processus d'inférence produit une table nommée « DocumentElement ».</span><span class="sxs-lookup"><span data-stu-id="f8d24-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="f8d24-131">**DataSet :** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="f8d24-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="f8d24-132">**Table :** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f8d24-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="f8d24-133">Element1</span><span class="sxs-lookup"><span data-stu-id="f8d24-133">Element1</span></span>|<span data-ttu-id="f8d24-134">Element2</span><span class="sxs-lookup"><span data-stu-id="f8d24-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="f8d24-135">Text1</span><span class="sxs-lookup"><span data-stu-id="f8d24-135">Text1</span></span>|<span data-ttu-id="f8d24-136">Text2</span><span class="sxs-lookup"><span data-stu-id="f8d24-136">Text2</span></span>|  
  
 <span data-ttu-id="f8d24-137">Examinons également le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="f8d24-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f8d24-138">Le processus d’inférence produit un **DataSet** nommé « DocumentElement » contenant une table nommée « Element1 ».</span><span class="sxs-lookup"><span data-stu-id="f8d24-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="f8d24-139">**DataSet :** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f8d24-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="f8d24-140">**Table :** Element1</span><span class="sxs-lookup"><span data-stu-id="f8d24-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="f8d24-141">attr1</span><span class="sxs-lookup"><span data-stu-id="f8d24-141">attr1</span></span>|<span data-ttu-id="f8d24-142">attr2</span><span class="sxs-lookup"><span data-stu-id="f8d24-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="f8d24-143">value1</span><span class="sxs-lookup"><span data-stu-id="f8d24-143">value1</span></span>|<span data-ttu-id="f8d24-144">value2</span><span class="sxs-lookup"><span data-stu-id="f8d24-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="f8d24-145">Éléments qui se répètent</span><span class="sxs-lookup"><span data-stu-id="f8d24-145">Repeating Elements</span></span>  
 <span data-ttu-id="f8d24-146">Les éléments qui se répètent donnent une seule table déduite.</span><span class="sxs-lookup"><span data-stu-id="f8d24-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="f8d24-147">Examinons, par exemple, le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="f8d24-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f8d24-148">Le processus d'inférence produit une table nommée « Element1 ».</span><span class="sxs-lookup"><span data-stu-id="f8d24-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="f8d24-149">**DataSet :** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f8d24-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="f8d24-150">**Table :** Element1</span><span class="sxs-lookup"><span data-stu-id="f8d24-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="f8d24-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="f8d24-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="f8d24-152">Text1</span><span class="sxs-lookup"><span data-stu-id="f8d24-152">Text1</span></span>|  
|<span data-ttu-id="f8d24-153">Text2</span><span class="sxs-lookup"><span data-stu-id="f8d24-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f8d24-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8d24-154">See Also</span></span>  
 [<span data-ttu-id="f8d24-155">Inférence de la structure relationnelle d’un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="f8d24-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="f8d24-156">Chargement d’un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="f8d24-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="f8d24-157">Chargement des informations de schéma de DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="f8d24-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="f8d24-158">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="f8d24-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="f8d24-159">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="f8d24-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="f8d24-160">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="f8d24-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
