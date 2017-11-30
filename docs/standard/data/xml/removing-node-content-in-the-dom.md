---
title: "Suppression du contenu d'un nœud dans le DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 76be90829a414b091d3b311b96bf9bab9a2b56ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="removing-node-content-in-the-dom"></a><span data-ttu-id="d0744-102">Suppression du contenu d'un nœud dans le DOM</span><span class="sxs-lookup"><span data-stu-id="d0744-102">Removing Node Content in the DOM</span></span>
<span data-ttu-id="d0744-103">Pour les types de nœuds héritant de l'objet <xref:System.Xml.XmlCharacterData>, à savoir les types de nœuds <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace> et <xref:System.Xml.XmlSignificantWhitespace>, vous pouvez supprimer des caractères à l'aide de la méthode <xref:System.Xml.XmlCharacterData.DeleteData%2A>, qui supprime une série de caractères du nœud.</span><span class="sxs-lookup"><span data-stu-id="d0744-103">For node types that inherit from <xref:System.Xml.XmlCharacterData>, which are the <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, and <xref:System.Xml.XmlSignificantWhitespace> node types, you can remove characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method, which removes a range of characters from the node.</span></span> <span data-ttu-id="d0744-104">Pour supprimer intégralement le contenu, vous devez supprimer le nœud en question.</span><span class="sxs-lookup"><span data-stu-id="d0744-104">If you want to remove content completely, you remove the node that contains the content.</span></span> <span data-ttu-id="d0744-105">Pour conserver le nœud, alors que son contenu est incorrect, vous devez modifier le contenu.</span><span class="sxs-lookup"><span data-stu-id="d0744-105">If you want to keep the node, but the content is incorrect, then modify the content.</span></span> <span data-ttu-id="d0744-106">Pour plus d’informations sur la modification du contenu d’un nœud, consultez [modification de nœuds, de contenu et de valeurs dans un Document XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="d0744-106">For information on modifying the content of a node, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0744-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0744-107">See Also</span></span>  
 [<span data-ttu-id="d0744-108">Document Object Model (DOM) XML</span><span class="sxs-lookup"><span data-stu-id="d0744-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
