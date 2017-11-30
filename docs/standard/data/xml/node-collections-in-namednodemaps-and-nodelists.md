---
title: "Collections de nœuds dans NamedNodeMap et NodeList"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 025954b8-7aa8-47c5-a1c1-f81064fb4d65
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7eeed46782eb6c55af23559035fb8b6bcb14301f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="node-collections-in-namednodemaps-and-nodelists"></a><span data-ttu-id="d9e63-102">Collections de nœuds dans NamedNodeMap et NodeList</span><span class="sxs-lookup"><span data-stu-id="d9e63-102">Node Collections in NamedNodeMaps and NodeLists</span></span>
<span data-ttu-id="d9e63-103">Il est possible d’extraire une collection de nœuds et de les placer dans une collection triée ou non.</span><span class="sxs-lookup"><span data-stu-id="d9e63-103">You can retrieve a set of nodes and put it in an ordered or unordered collection.</span></span> <span data-ttu-id="d9e63-104">Si vous regroupez une collection de nœuds dans une collection non triée, cet ensemble est appelé NamedNodeMap par le World Wide Web Consortium (W3C). Ce type de collection vous permet d'extraire des données au moyen de leur nom ou de l'index.</span><span class="sxs-lookup"><span data-stu-id="d9e63-104">When putting a set of nodes into an unordered collection, the set is called a NamedNodeMap by the World Wide Web Consortium (W3C); you can retrieve the data by name or index in this type of collection.</span></span> <span data-ttu-id="d9e63-105">En revanche, si vous placez une collection de nœuds dans une collection triée, celle-ci est appelée NodeList par le W3C, et ses données peuvent être extraites au moyen d'un index de base zéro.</span><span class="sxs-lookup"><span data-stu-id="d9e63-105">Putting a set of nodes in an ordered collection is called a NodeList by the W3C, and the data can be retrieved by a zero-based index.</span></span> <span data-ttu-id="d9e63-106">NamedNodeMap et NodeList sont décrits par le W3C.</span><span class="sxs-lookup"><span data-stu-id="d9e63-106">NamedNodeMaps and NodeLists are described by the W3C.</span></span> <span data-ttu-id="d9e63-107">Les implémentations de Microsoft .NET Framework pour NamedNodeMap est la **XmlNamedNodeMap**, et la liste de nœuds est implémenté par le **XmlNodeList**.</span><span class="sxs-lookup"><span data-stu-id="d9e63-107">The implementations in the Microsoft .NET Framework for the NamedNodeMap is the **XmlNamedNodeMap**, and the NodeList is implemented by the **XmlNodeList**.</span></span>  
  
 <span data-ttu-id="d9e63-108">Pour plus d’informations sur la collection non triée, voir [extraction de nœuds non triée par nom ou Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="d9e63-108">For information on the unordered collection, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span> <span data-ttu-id="d9e63-109">Pour plus d’informations sur la collection triée, voir [extraction de nœuds triés par l’Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="d9e63-109">For information on the ordered collection, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e63-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9e63-110">See Also</span></span>  
 [<span data-ttu-id="d9e63-111">Document Object Model (DOM) XML</span><span class="sxs-lookup"><span data-stu-id="d9e63-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
