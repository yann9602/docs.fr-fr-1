---
title: "Mises à jour dynamiques de NodeList et NamedNodeMap"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 459d746ff278ac4affa0318c1fad0aeb6a73e560
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="b43aa-102">Mises à jour dynamiques de NodeList et NamedNodeMap</span><span class="sxs-lookup"><span data-stu-id="b43aa-102">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>
<span data-ttu-id="b43aa-103">Étant donné que la **XmlNodeList** et **XmlNamedNodeMap** contiennent un ensemble de nœuds, mais où le document XML est chargé en mémoire et est modifié, le World Wide Web Consortium (W3C) indique que ces objets qui contiennent des ensembles de nœuds doivent être dynamiques.</span><span class="sxs-lookup"><span data-stu-id="b43aa-103">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="b43aa-104">Dès lors, si le document sous-jacent change, les données figurant dans ces deux objets doivent changer également.</span><span class="sxs-lookup"><span data-stu-id="b43aa-104">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="b43aa-105">Par conséquent, si vous avez un **XmlNodeList** qui contient tous les éléments enfants d’un élément particulier (par exemple, l’élément X), puis vous ajoutez un élément supplémentaire, l’élément Q, au document sous l’élément X. Le **XmlNodeList** doit également avoir le nouvel élément Q ajouté à sa collection.</span><span class="sxs-lookup"><span data-stu-id="b43aa-105">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="b43aa-106">L'inverse est vrai également.</span><span class="sxs-lookup"><span data-stu-id="b43aa-106">The same is true in reverse.</span></span> <span data-ttu-id="b43aa-107">Si un nœud est ajouté à la **XmlNodeList**, le document sous-jacent est également mis à jour.</span><span class="sxs-lookup"><span data-stu-id="b43aa-107">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b43aa-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b43aa-108">See Also</span></span>  
 [<span data-ttu-id="b43aa-109">Document Object Model (DOM) XML</span><span class="sxs-lookup"><span data-stu-id="b43aa-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
