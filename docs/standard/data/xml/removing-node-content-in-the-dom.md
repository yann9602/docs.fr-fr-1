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
# <a name="removing-node-content-in-the-dom"></a>Suppression du contenu d'un nœud dans le DOM
Pour les types de nœuds héritant de l'objet <xref:System.Xml.XmlCharacterData>, à savoir les types de nœuds <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace> et <xref:System.Xml.XmlSignificantWhitespace>, vous pouvez supprimer des caractères à l'aide de la méthode <xref:System.Xml.XmlCharacterData.DeleteData%2A>, qui supprime une série de caractères du nœud. Pour supprimer intégralement le contenu, vous devez supprimer le nœud en question. Pour conserver le nœud, alors que son contenu est incorrect, vous devez modifier le contenu. Pour plus d’informations sur la modification du contenu d’un nœud, consultez [modification de nœuds, de contenu et de valeurs dans un Document XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
