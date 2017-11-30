---
title: "Suppression d'attributs d'un nœud d'élément dans le DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b4ca08d8080c2116ce05634a544c91780869b165
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a><span data-ttu-id="0e701-102">Suppression d'attributs d'un nœud d'élément dans le DOM</span><span class="sxs-lookup"><span data-stu-id="0e701-102">Removing Attributes from an Element Node in the DOM</span></span>
<span data-ttu-id="0e701-103">Il existe plusieurs manières de supprimer des attributs.</span><span class="sxs-lookup"><span data-stu-id="0e701-103">There are many ways to remove attributes.</span></span> <span data-ttu-id="0e701-104">L'une des techniques consiste à les supprimer de la collection d'attributs.</span><span class="sxs-lookup"><span data-stu-id="0e701-104">One technique is to remove them from the attribute collection.</span></span> <span data-ttu-id="0e701-105">Pour ce faire, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="0e701-105">To do this, the following steps are performed:</span></span>  
  
1.  <span data-ttu-id="0e701-106">Obtenez la collection d'attributs à partir de l'élément à l'aide de `XmlAttributeCollection attrs = elem.Attributes;`.</span><span class="sxs-lookup"><span data-stu-id="0e701-106">Get the attribute collection from the element using `XmlAttributeCollection attrs = elem.Attributes;`.</span></span>  
  
2.  <span data-ttu-id="0e701-107">Supprimez l'attribut de la collection d'attributs à l'aide d'une des trois méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="0e701-107">Remove the attribute from the attribute collection using one of three methods:</span></span>  
  
    -   <span data-ttu-id="0e701-108">Utilisez la méthode <xref:System.Xml.XmlAttributeCollection.Remove%2A> pour supprimer un attribut spécifique.</span><span class="sxs-lookup"><span data-stu-id="0e701-108">Use <xref:System.Xml.XmlAttributeCollection.Remove%2A> to remove a specific attribute.</span></span>  
  
    -   <span data-ttu-id="0e701-109">Utilisez la méthode <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> pour supprimer tous les attributs de la collection et conserver l'élément sans attribut.</span><span class="sxs-lookup"><span data-stu-id="0e701-109">Use <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> to remove all attributes from the collection and leave the element with no attributes.</span></span>  
  
    -   <span data-ttu-id="0e701-110">Utilisez la méthode <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> pour supprimer un attribut d'une collection d'attributs à l'aide de son numéro d'index.</span><span class="sxs-lookup"><span data-stu-id="0e701-110">Use <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> to remove an attribute from the attribute collection by using its index number.</span></span>  
  
 <span data-ttu-id="0e701-111">Les méthodes suivantes suppriment des attributs du nœud d'élément.</span><span class="sxs-lookup"><span data-stu-id="0e701-111">The following methods remove attributes from the element node.</span></span>  
  
-   <span data-ttu-id="0e701-112">Utilisez la méthode <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> pour supprimer la collection d'attributs.</span><span class="sxs-lookup"><span data-stu-id="0e701-112">Use <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> to remove the attribute collection.</span></span>  
  
-   <span data-ttu-id="0e701-113">Utilisez la méthode <xref:System.Xml.XmlElement.RemoveAttribute%2A> pour supprimer de la collection un attribut spécifique par son nom.</span><span class="sxs-lookup"><span data-stu-id="0e701-113">Use <xref:System.Xml.XmlElement.RemoveAttribute%2A> to remove a single attribute by name from the collection.</span></span>  
  
-   <span data-ttu-id="0e701-114">Utilisez la méthode <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> pour supprimer de la collection un attribut spécifique par son numéro d'index.</span><span class="sxs-lookup"><span data-stu-id="0e701-114">Use <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> to remove a single attribute by index number from the collection.</span></span>  
  
 <span data-ttu-id="0e701-115">Une autre solution consiste à obtenir l'élément, puis l'attribut à partir de la collection d'attributs et de supprimer directement le nœud d'attribut.</span><span class="sxs-lookup"><span data-stu-id="0e701-115">One more alternative is to get the element, get the attribute from the attribute collection, and remove the attribute node directly.</span></span> <span data-ttu-id="0e701-116">Pour obtenir l'attribut à partir de la collection d'attributs, vous pouvez utiliser un nom, `XmlAttribute attr = attrs["attr_name"];`, un index `XmlAttribute attr = attrs[0];` ou donner un nom qualifié à l'espace de noms `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.</span><span class="sxs-lookup"><span data-stu-id="0e701-116">To get the attribute from the attribute collection, you can use a name, `XmlAttribute attr = attrs["attr_name"];`, an index `XmlAttribute attr = attrs[0];`, or by fully qualifying the name with the namespace `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.</span></span>  
  
 <span data-ttu-id="0e701-117">Quelle que soit la méthode utilisée pour la suppression des attributs, la suppression d'attributs définis comme des attributs par défaut dans la DTD (définition de type de document) est sujette à des restrictions spéciales.</span><span class="sxs-lookup"><span data-stu-id="0e701-117">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the document type definition (DTD).</span></span> <span data-ttu-id="0e701-118">Les attributs par défaut ne peuvent pas être supprimés, à moins que l'élément auquel ils appartiennent ne le soit également.</span><span class="sxs-lookup"><span data-stu-id="0e701-118">Default attributes cannot be removed unless the element they belong to is removed.</span></span> <span data-ttu-id="0e701-119">Les attributs par défaut sont toujours présents pour les éléments possédant des attributs par défaut déclarés.</span><span class="sxs-lookup"><span data-stu-id="0e701-119">Default attributes are always present for elements that have default attributes declared.</span></span> <span data-ttu-id="0e701-120">La suppression d'un attribut par défaut d'un objet <xref:System.Xml.XmlAttributeCollection> ou de l'objet <xref:System.Xml.XmlElement> provoque l'insertion d'un attribut de substitution dans l'objet <xref:System.Xml.XmlAttributeCollection> de l'élément, initialisé à la valeur par défaut qui a été déclarée.</span><span class="sxs-lookup"><span data-stu-id="0e701-120">Removing a default attribute from an <xref:System.Xml.XmlAttributeCollection> or from the <xref:System.Xml.XmlElement> results in a replacement attribute inserted into the <xref:System.Xml.XmlAttributeCollection> of the element, initialized to the default value that was declared.</span></span> <span data-ttu-id="0e701-121">Si un élément est défini comme `<book att1="1" att2="2" att3="3"></book>`, un élément `book` possède trois attributs par défaut déclarés.</span><span class="sxs-lookup"><span data-stu-id="0e701-121">If you have an element defined as `<book att1="1" att2="2" att3="3"></book>`, then you have a `book` element with three default attributes declared.</span></span> <span data-ttu-id="0e701-122">L’implémentation du modèle DOM (Document objet Model) XML garantit que tant que cet `book` élément existe, il possède ces trois attributs par défaut `att1`, `att2`, et `att3`.</span><span class="sxs-lookup"><span data-stu-id="0e701-122">The XML Document Object Model (DOM) implementation guarantees that as long as this `book` element exists, it has these three default attributes of `att1`, `att2`, and `att3`.</span></span>  
  
 <span data-ttu-id="0e701-123">Appelée avec un objet <xref:System.Xml.XmlAttribute>, la méthode <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> définit la valeur de l'attribut sur String.Empty, étant donné qu'un attribut ne peut pas exister sans valeur.</span><span class="sxs-lookup"><span data-stu-id="0e701-123">When called with an <xref:System.Xml.XmlAttribute>, the <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> method sets the value of the attribute to String.Empty, as an attribute cannot exist without a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e701-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e701-124">See Also</span></span>  
 [<span data-ttu-id="0e701-125">Document Object Model (DOM) XML</span><span class="sxs-lookup"><span data-stu-id="0e701-125">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
