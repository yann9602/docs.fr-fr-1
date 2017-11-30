---
title: "Navigation dans la collection de nœuds à l’aide de XPathNavigator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9ac0135227599d6a72813bcf57b209705545da66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="node-set-navigation-using-xpathnavigator"></a><span data-ttu-id="11471-102">Navigation dans la collection de nœuds à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="11471-102">Node Set Navigation Using XPathNavigator</span></span>
<span data-ttu-id="11471-103">Vous pouvez parcourir les nœuds d'un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> à l'aide des méthodes de navigation entre les collections de nœuds de la classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="11471-103">You can navigate over nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="11471-104">Vous pouvez parcourir tous ces nœuds ou certaines collections de nœuds retournées par l'une des méthodes de sélection de la classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="11471-104">You can navigate over all the nodes or over a selected set of nodes returned by one of the selection methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="element-node-set-navigation"></a><span data-ttu-id="11471-105">Navigation entre les collections de nœuds d'éléments</span><span class="sxs-lookup"><span data-stu-id="11471-105">Element Node Set Navigation</span></span>  
 <span data-ttu-id="11471-106">La classe <xref:System.Xml.XPath.XPathNavigator> fournit plusieurs méthodes de navigation entre les nœuds d'élément.</span><span class="sxs-lookup"><span data-stu-id="11471-106">The <xref:System.Xml.XPath.XPathNavigator> class provides several methods used to navigate element nodes.</span></span> <span data-ttu-id="11471-107">Le tableau suivant indique les méthodes de navigation disponibles et donne une description de leur mode de déplacement, mais ne comprend pas les méthodes permettant de naviguer entre les nœuds d'attribut et d'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="11471-107">The following table shows the navigation methods available and a description of how they move; this does not include methods used to navigate attribute and namespace nodes.</span></span>  
  
 <span data-ttu-id="11471-108">Pour plus d’informations sur la sélection des nœuds dans un <xref:System.Xml.XPath.XPathNavigator> d’objets, consultez [sélection, évaluation et mise en correspondance les données XML à l’aide de XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="11471-108">For more information about selecting nodes in an <xref:System.Xml.XPath.XPathNavigator> object, see [Selecting, Evaluating and Matching XML Data using XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span></span> <span data-ttu-id="11471-109">Pour plus d’informations sur la navigation dans les nœuds d’attribut et d’espace de noms, consultez [attribut et Namespace Node Navigation à l’aide de XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="11471-109">For more information about navigating attribute and namespace nodes, see [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span></span>  
  
|<span data-ttu-id="11471-110">Méthode</span><span class="sxs-lookup"><span data-stu-id="11471-110">Method</span></span>|<span data-ttu-id="11471-111">Description</span><span class="sxs-lookup"><span data-stu-id="11471-111">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|<span data-ttu-id="11471-112">Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers la même position que l'objet <xref:System.Xml.XPath.XPathNavigator> spécifié.</span><span class="sxs-lookup"><span data-stu-id="11471-112">Moves the <xref:System.Xml.XPath.XPathNavigator> to the same position of the <xref:System.Xml.XPath.XPathNavigator> specified.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|<span data-ttu-id="11471-113">Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers un nœud enfant du nœud actuel.</span><span class="sxs-lookup"><span data-stu-id="11471-113">Moves the <xref:System.Xml.XPath.XPathNavigator> to a child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|<span data-ttu-id="11471-114">Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers le premier nœud frère du nœud actuel.</span><span class="sxs-lookup"><span data-stu-id="11471-114">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|<span data-ttu-id="11471-115">Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers le premier nœud enfant du nœud actuel.</span><span class="sxs-lookup"><span data-stu-id="11471-115">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|<span data-ttu-id="11471-116">Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers l'élément spécifié dans l'ordre du document.</span><span class="sxs-lookup"><span data-stu-id="11471-116">Moves the <xref:System.Xml.XPath.XPathNavigator> to the specified element in document order.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|<span data-ttu-id="11471-117">Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers le nœud possédant un attribut de type `ID` avec une valeur correspondant à l'objet <xref:System.String> donné.</span><span class="sxs-lookup"><span data-stu-id="11471-117">Moves the <xref:System.Xml.XPath.XPathNavigator> to the node that has an attribute of type `ID` with a value that matches the given <xref:System.String>.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|<span data-ttu-id="11471-118">Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers le nœud frère suivant du nœud actuel.</span><span class="sxs-lookup"><span data-stu-id="11471-118">Moves the <xref:System.Xml.XPath.XPathNavigator> to the next sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|<span data-ttu-id="11471-119">Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers le nœud parent du nœud actuel.</span><span class="sxs-lookup"><span data-stu-id="11471-119">Moves the <xref:System.Xml.XPath.XPathNavigator> to the parent node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|<span data-ttu-id="11471-120">Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers le nœud frère précédent du nœud actuel.</span><span class="sxs-lookup"><span data-stu-id="11471-120">Moves the <xref:System.Xml.XPath.XPathNavigator> to the previous sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|<span data-ttu-id="11471-121">Déplace l'objet <xref:System.Xml.XPath.XPathNavigator> vers le nœud racine du document XML.</span><span class="sxs-lookup"><span data-stu-id="11471-121">Moves the <xref:System.Xml.XPath.XPathNavigator> to the root node of the XML document.</span></span>|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a><span data-ttu-id="11471-122">Commentaires et instructions de traitement de la navigation entre les nœuds</span><span class="sxs-lookup"><span data-stu-id="11471-122">Comments and Processing Instruction Node Navigation</span></span>  
 <span data-ttu-id="11471-123">Les méthodes suivantes de la classe <xref:System.Xml.XPath.XPathNavigator> sont valide pour le déplacement de commentaires ou d'instructions de traitement d'autres nœuds dans un document XML.</span><span class="sxs-lookup"><span data-stu-id="11471-123">The following <xref:System.Xml.XPath.XPathNavigator> class methods are valid for moving to comments or processing instructions from other nodes in an XML document.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a><span data-ttu-id="11471-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11471-124">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="11471-125">Traitement des données XML à l’aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="11471-125">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="11471-126">Attribut et la navigation entre les nœuds de Namespace à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="11471-126">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [<span data-ttu-id="11471-127">Extraire des données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="11471-127">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="11471-128">L’accès à fortement typée des données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="11471-128">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
