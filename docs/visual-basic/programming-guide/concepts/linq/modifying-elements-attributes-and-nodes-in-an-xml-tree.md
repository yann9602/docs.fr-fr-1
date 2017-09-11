---
title: "Modification d’éléments, attributs et nœuds dans un Tree1 XML | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 88531f2af88074f4406c4859354860829efda69f
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="17cf2-102">Modification d’éléments, d’attributs et de nœuds dans une arborescence XML</span><span class="sxs-lookup"><span data-stu-id="17cf2-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="17cf2-103">Le tableau suivant résume les méthodes et propriétés que vous pouvez utiliser pour modifier un élément, ses éléments enfants ou ses attributs.</span><span class="sxs-lookup"><span data-stu-id="17cf2-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="17cf2-104">Les méthodes suivantes modifient un <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="17cf2-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="17cf2-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="17cf2-105">Method</span></span>|<span data-ttu-id="17cf2-106">Description</span><span class="sxs-lookup"><span data-stu-id="17cf2-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="17cf2-107"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="17cf2-107"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span></span>|<span data-ttu-id="17cf2-108">Remplace un élément par du code XML analysé.</span><span class="sxs-lookup"><span data-stu-id="17cf2-108">Replaces an element with parsed XML.</span></span>|  
|<span data-ttu-id="17cf2-109"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="17cf2-109"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span></span>|<span data-ttu-id="17cf2-110">Supprime tout le contenu (nœuds enfants et attributs) d'un élément.</span><span class="sxs-lookup"><span data-stu-id="17cf2-110">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<span data-ttu-id="17cf2-111"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="17cf2-111"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="17cf2-112">Supprime les attributs d'un élément.</span><span class="sxs-lookup"><span data-stu-id="17cf2-112">Removes the attributes of an element.</span></span>|  
|<span data-ttu-id="17cf2-113"><xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="17cf2-113"><xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=fullName></span></span>|<span data-ttu-id="17cf2-114">Remplace tout le contenu (nœuds enfants et attributs) d'un élément.</span><span class="sxs-lookup"><span data-stu-id="17cf2-114">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<span data-ttu-id="17cf2-115"><xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="17cf2-115"><xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="17cf2-116">Remplace les attributs d'un élément.</span><span class="sxs-lookup"><span data-stu-id="17cf2-116">Replaces the attributes of an element.</span></span>|  
|<span data-ttu-id="17cf2-117"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="17cf2-117"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="17cf2-118">Définit la valeur d'un attribut.</span><span class="sxs-lookup"><span data-stu-id="17cf2-118">Sets the value of an attribute.</span></span> <span data-ttu-id="17cf2-119">Crée l'attribut s'il n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="17cf2-119">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="17cf2-120">Si la valeur est définie à `null`, supprime l'attribut.</span><span class="sxs-lookup"><span data-stu-id="17cf2-120">If the value is set to `null`, removes the attribute.</span></span>|  
|<span data-ttu-id="17cf2-121"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="17cf2-121"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="17cf2-122">Définit la valeur d'un élément enfant.</span><span class="sxs-lookup"><span data-stu-id="17cf2-122">Sets the value of a child element.</span></span> <span data-ttu-id="17cf2-123">Crée l'élément s'il n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="17cf2-123">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="17cf2-124">Si la valeur est définie à `null`, supprime l'élément.</span><span class="sxs-lookup"><span data-stu-id="17cf2-124">If the value is set to `null`, removes the element.</span></span>|  
|<span data-ttu-id="17cf2-125"><xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="17cf2-125"><xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName></span></span>|<span data-ttu-id="17cf2-126">Remplace le contenu (nœuds enfants) d'un élément par le texte spécifié.</span><span class="sxs-lookup"><span data-stu-id="17cf2-126">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<span data-ttu-id="17cf2-127"><xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="17cf2-127"><xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="17cf2-128">Définit la valeur d'un élément.</span><span class="sxs-lookup"><span data-stu-id="17cf2-128">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="17cf2-129">Les méthodes suivantes modifient un <xref:System.Xml.Linq.XAttribute>.</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="17cf2-129">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="17cf2-130">Méthode</span><span class="sxs-lookup"><span data-stu-id="17cf2-130">Method</span></span>|<span data-ttu-id="17cf2-131">Description</span><span class="sxs-lookup"><span data-stu-id="17cf2-131">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="17cf2-132"><xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="17cf2-132"><xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName></span></span>|<span data-ttu-id="17cf2-133">Définit la valeur d'un attribut.</span><span class="sxs-lookup"><span data-stu-id="17cf2-133">Sets the value of an attribute.</span></span>|  
|<span data-ttu-id="17cf2-134"><xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="17cf2-134"><xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="17cf2-135">Définit la valeur d'un attribut.</span><span class="sxs-lookup"><span data-stu-id="17cf2-135">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="17cf2-136">Les méthodes suivantes modifient un <xref:System.Xml.Linq.XNode>(y compris un <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>).</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="17cf2-136">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="17cf2-137">Méthode</span><span class="sxs-lookup"><span data-stu-id="17cf2-137">Method</span></span>|<span data-ttu-id="17cf2-138">Description</span><span class="sxs-lookup"><span data-stu-id="17cf2-138">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="17cf2-139"><xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="17cf2-139"><xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=fullName></span></span>|<span data-ttu-id="17cf2-140">Remplace un nœud par du nouveau contenu.</span><span class="sxs-lookup"><span data-stu-id="17cf2-140">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="17cf2-141">Les méthodes suivantes modifient un <xref:System.Xml.Linq.XContainer>(un <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>).</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XContainer></span><span class="sxs-lookup"><span data-stu-id="17cf2-141">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="17cf2-142">Méthode</span><span class="sxs-lookup"><span data-stu-id="17cf2-142">Method</span></span>|<span data-ttu-id="17cf2-143">Description</span><span class="sxs-lookup"><span data-stu-id="17cf2-143">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="17cf2-144"><xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="17cf2-144"><xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="17cf2-145">Remplace les nœuds enfants par du nouveau contenu.</span><span class="sxs-lookup"><span data-stu-id="17cf2-145">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17cf2-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17cf2-146">See Also</span></span>  
 [<span data-ttu-id="17cf2-147">Modification d’arborescences XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17cf2-147">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
