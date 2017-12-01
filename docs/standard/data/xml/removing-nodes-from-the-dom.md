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
# <a name="removing-nodes-from-the-dom"></a>Suppression de nœuds du DOM
Pour supprimer un nœud du DOM (Document Object Model) XML, utilisez la méthode <xref:System.Xml.XmlNode.RemoveChild%2A>. La méthode supprime le sous-arbre appartenant au nœud en cours de suppression, du moins s'il ne s'agit pas d'un nœud sans descendant.  
  
 Pour supprimer plusieurs nœuds du DOM, utilisez la méthode <xref:System.Xml.XmlNode.RemoveAll%2A>, qui permet de supprimer tous les enfants et attributs (le cas échéant) du nœud actuel.  
  
 Si vous travaillez avec un objet <xref:System.Xml.XmlNamedNodeMap>, vous pouvez supprimer un nœud à l'aide de la méthode <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A>.  
  
 Pour supprimer des attributs, consultez [suppression d’attributs d’un nœud d’élément dans le DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
