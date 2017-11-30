---
title: "Suppression de nœuds du DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0885d53e737153448fabfd394d49bfdc793e0599
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="56299-102">Suppression de nœuds du DOM</span><span class="sxs-lookup"><span data-stu-id="56299-102">Removing Nodes from the DOM</span></span>
<span data-ttu-id="56299-103">Pour supprimer un nœud du DOM (Document Object Model) XML, utilisez la méthode <xref:System.Xml.XmlNode.RemoveChild%2A>.</span><span class="sxs-lookup"><span data-stu-id="56299-103">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="56299-104">La méthode supprime le sous-arbre appartenant au nœud en cours de suppression, du moins s'il ne s'agit pas d'un nœud sans descendant.</span><span class="sxs-lookup"><span data-stu-id="56299-104">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="56299-105">Pour supprimer plusieurs nœuds du DOM, utilisez la méthode <xref:System.Xml.XmlNode.RemoveAll%2A>, qui permet de supprimer tous les enfants et attributs (le cas échéant) du nœud actuel.</span><span class="sxs-lookup"><span data-stu-id="56299-105">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="56299-106">Si vous travaillez avec un objet <xref:System.Xml.XmlNamedNodeMap>, vous pouvez supprimer un nœud à l'aide de la méthode <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="56299-106">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="56299-107">Pour supprimer des attributs, consultez [suppression d’attributs d’un nœud d’élément dans le DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="56299-107">To remove attributes, see [Removing Attributes from an Element Node in the DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56299-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56299-108">See Also</span></span>  
 [<span data-ttu-id="56299-109">Document Object Model (DOM) XML</span><span class="sxs-lookup"><span data-stu-id="56299-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
