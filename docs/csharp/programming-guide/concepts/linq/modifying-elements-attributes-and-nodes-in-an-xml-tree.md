---
title: "Modification d’éléments, d’attributs et de nœuds dans une arborescence XML3"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: da3b31456bc86b547c5174143620f464dc42f35b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="4967f-102">Modification d’éléments, d’attributs et de nœuds dans une arborescence XML</span><span class="sxs-lookup"><span data-stu-id="4967f-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="4967f-103">Le tableau suivant résume les méthodes et propriétés que vous pouvez utiliser pour modifier un élément, ses éléments enfants ou ses attributs.</span><span class="sxs-lookup"><span data-stu-id="4967f-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="4967f-104">Les méthodes suivantes modifient un objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="4967f-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="4967f-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="4967f-105">Method</span></span>|<span data-ttu-id="4967f-106">Description</span><span class="sxs-lookup"><span data-stu-id="4967f-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="4967f-107">Remplace un élément par du code XML analysé.</span><span class="sxs-lookup"><span data-stu-id="4967f-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="4967f-108">Supprime tout le contenu (nœuds enfants et attributs) d'un élément.</span><span class="sxs-lookup"><span data-stu-id="4967f-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="4967f-109">Supprime les attributs d'un élément.</span><span class="sxs-lookup"><span data-stu-id="4967f-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="4967f-110">Remplace tout le contenu (nœuds enfants et attributs) d'un élément.</span><span class="sxs-lookup"><span data-stu-id="4967f-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="4967f-111">Remplace les attributs d'un élément.</span><span class="sxs-lookup"><span data-stu-id="4967f-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="4967f-112">Définit la valeur d'un attribut.</span><span class="sxs-lookup"><span data-stu-id="4967f-112">Sets the value of an attribute.</span></span> <span data-ttu-id="4967f-113">Crée l'attribut s'il n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="4967f-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="4967f-114">Si la valeur est définie à `null`, supprime l'attribut.</span><span class="sxs-lookup"><span data-stu-id="4967f-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="4967f-115">Définit la valeur d'un élément enfant.</span><span class="sxs-lookup"><span data-stu-id="4967f-115">Sets the value of a child element.</span></span> <span data-ttu-id="4967f-116">Crée l'élément s'il n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="4967f-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="4967f-117">Si la valeur est définie à `null`, supprime l'élément.</span><span class="sxs-lookup"><span data-stu-id="4967f-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="4967f-118">Remplace le contenu (nœuds enfants) d'un élément par le texte spécifié.</span><span class="sxs-lookup"><span data-stu-id="4967f-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="4967f-119">Définit la valeur d'un élément.</span><span class="sxs-lookup"><span data-stu-id="4967f-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="4967f-120">Les méthodes suivantes modifient un objet <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4967f-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="4967f-121">Méthode</span><span class="sxs-lookup"><span data-stu-id="4967f-121">Method</span></span>|<span data-ttu-id="4967f-122">Description</span><span class="sxs-lookup"><span data-stu-id="4967f-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="4967f-123">Définit la valeur d'un attribut.</span><span class="sxs-lookup"><span data-stu-id="4967f-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="4967f-124">Définit la valeur d'un attribut.</span><span class="sxs-lookup"><span data-stu-id="4967f-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="4967f-125">Les méthodes suivantes modifient un objet <xref:System.Xml.Linq.XNode> (y compris un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="4967f-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="4967f-126">Méthode</span><span class="sxs-lookup"><span data-stu-id="4967f-126">Method</span></span>|<span data-ttu-id="4967f-127">Description</span><span class="sxs-lookup"><span data-stu-id="4967f-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="4967f-128">Remplace un nœud par du nouveau contenu.</span><span class="sxs-lookup"><span data-stu-id="4967f-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="4967f-129">Les méthodes suivantes modifient un objet <xref:System.Xml.Linq.XContainer> (un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="4967f-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="4967f-130">Méthode</span><span class="sxs-lookup"><span data-stu-id="4967f-130">Method</span></span>|<span data-ttu-id="4967f-131">Description</span><span class="sxs-lookup"><span data-stu-id="4967f-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="4967f-132">Remplace les nœuds enfants par du nouveau contenu.</span><span class="sxs-lookup"><span data-stu-id="4967f-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4967f-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4967f-133">See Also</span></span>  
 [<span data-ttu-id="4967f-134">Modification d’arborescences XML (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4967f-134">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
