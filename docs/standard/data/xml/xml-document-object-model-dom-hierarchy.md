---
title: "Hiérarchie du DOM XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6dec61860fba5815b1dae802d280e8df6628ab91
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="48269-102">Hiérarchie du DOM XML</span><span class="sxs-lookup"><span data-stu-id="48269-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="48269-103">L’illustration suivante montre la hiérarchie de classes du DOM (Document Object Model) XML et fournit le nom World Wide Web Consortium (W3C) entre parenthèses en même temps que le nom de la classe lorsque cela est pertinent.</span><span class="sxs-lookup"><span data-stu-id="48269-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="48269-104">![Modèle objet de Document XML &#40; DOM &#41; hiérarchie](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="48269-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="48269-105">Hiérarchie du modèle DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="48269-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="48269-106">Les classes suivantes n’héritent pas de la **XmlNode**:</span><span class="sxs-lookup"><span data-stu-id="48269-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
-   <span data-ttu-id="48269-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="48269-107">**XmlImplementation**</span></span>  
  
-   <span data-ttu-id="48269-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="48269-108">**XmlNamedNodeMap**</span></span>  
  
-   <span data-ttu-id="48269-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="48269-109">**XmlNodeList**</span></span>  
  
-   <span data-ttu-id="48269-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="48269-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="48269-111">Le **XmlImplementation** classe est utilisée pour créer un document XML.</span><span class="sxs-lookup"><span data-stu-id="48269-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="48269-112">Pour plus d’informations, consultez [création d’un Document XML](../../../../docs/standard/data/xml/xml-document-creation.md).</span><span class="sxs-lookup"><span data-stu-id="48269-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="48269-113">Le **XmlNamedNodeMap** classe gère un ensemble non trié de nœuds.</span><span class="sxs-lookup"><span data-stu-id="48269-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="48269-114">Pour plus d’informations, consultez [extraction de nœuds non triée par nom ou Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="48269-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="48269-115">Le **XmlNodeList** classe gère une liste triée de nœuds.</span><span class="sxs-lookup"><span data-stu-id="48269-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="48269-116">Pour plus d’informations, consultez [extraction de nœuds triés par l’Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="48269-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="48269-117">Le **XmlNodeChangedEventArgs** classe gère des gestionnaires d’événements inscrits sur le **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="48269-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="48269-118">Pour plus d’informations, consultez [gestion des événements dans un Document XML à l’aide de XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span><span class="sxs-lookup"><span data-stu-id="48269-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="48269-119">Le **XmlLinkedNode** hérite de la classe **XmlNode**.</span><span class="sxs-lookup"><span data-stu-id="48269-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="48269-120">Son objectif consiste à substituer deux méthodes de **XmlNode**: le **PreviousSibling** et **NextSibling** méthodes.</span><span class="sxs-lookup"><span data-stu-id="48269-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="48269-121">Les méthodes substituées sont ensuite héritées et utilisées par **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, et **XmlProcessingInstruction**, qui sont des classes dotées de frères précédents et suivants.</span><span class="sxs-lookup"><span data-stu-id="48269-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48269-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48269-122">See Also</span></span>  
 [<span data-ttu-id="48269-123">Document Object Model (DOM) XML</span><span class="sxs-lookup"><span data-stu-id="48269-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
