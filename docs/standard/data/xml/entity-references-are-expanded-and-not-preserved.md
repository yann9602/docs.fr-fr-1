---
title: "Développement sans conservation des références d’entité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffd97806-ab43-4538-8de2-5828bfbbde57
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 069d3b94a0269917400e75fdbe975ec39dcfdb71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="entity-references-are-expanded-and-not-preserved"></a>Développement sans conservation des références d’entité
Lors de la référence d’entité est développée et remplacée par le texte qu’elle représente, le **XmlEntityReference** nœud n’est pas créé. Au lieu de cela, la déclaration d’entité est analysée et les nœuds créés à partir du contenu de la déclaration sont copiés à la place de la **XmlEntityReference**. Par conséquent, dans le `&publisher;` exemple, le `&publisher;` n’est pas enregistré, mais au lieu de cela, une **XmlText** nœud est créé.  
  
 ![développé arborescence](../../../../docs/standard/data/xml/media/xmlentityref-expanded-nodes.gif "xmlentityref_expanded_nodes")  
Structure d’arborescence avec références d’entité développées  
  
 Les entités de caractère, telles que `B` ou `<`, ne sont pas conservées. En revanche, elles sont toujours développées et représentées sous la forme de nœuds de texte.  
  
 Pour conserver **XmlEntityReference** nœuds ainsi que les nœuds enfants de la référence d’entité joint, affectez le **EntityHandling** indicateur **ExpandCharEntities**. Sinon, laissez le **EntityHandling** indicateur la valeur par défaut, qui consiste à **ExpandEntities**. Dans ce cas, le DOM ne comprendra pas de nœud de référence d'entité. Ces nœuds sont remplacés par ceux qui constituent des copies des nœuds enfants de la déclaration d'entité.  
  
 La non-conservation des références d'entité présente un effet pervers : lorsque le document est enregistré et passé à une autre application, cette application réceptrice ne sait pas que les nœuds ont été générés par une référence d'entité. Toutefois, lorsque les références d'entité sont préservées, une application réceptrice voit une référence d'entité et lit les nœuds enfants. Il est manifeste que les nœuds enfants représentent les informations qui figuraient dans la déclaration d'entité. Par exemple, en théorie, le DOM possède la structure suivante s'il existe une conservation des références d'entité.  
  
 XmlElement : éditeur  
  
 XmlEntityReference : `&publisher;`  
  
 XmlText : Microsoft Press  
  
 Si des références d'entité sont développées dans le DOM (ce qui constitue la méthode par défaut), la structure possède ce type d'arborescence :  
  
 XmlElement : éditeur  
  
 XmlText : Microsoft Press  
  
 Notez que le nœud de référence d’entité, et l’application de réception ne peut pas déterminer que le **XmlText** nœud contenant « Microsoft Press » a été créé à partir d’une déclaration d’entité.  
  
 Si vous utilisez un lecteur qui ne peut pas résoudre les entités, les **charge** méthode lève une exception lorsqu’elle rencontre une référence d’entité.  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
