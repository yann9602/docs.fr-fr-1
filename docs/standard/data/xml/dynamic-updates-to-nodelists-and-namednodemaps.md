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
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>Mises à jour dynamiques de NodeList et NamedNodeMap
Étant donné que la **XmlNodeList** et **XmlNamedNodeMap** contiennent un ensemble de nœuds, mais où le document XML est chargé en mémoire et est modifié, le World Wide Web Consortium (W3C) indique que ces objets qui contiennent des ensembles de nœuds doivent être dynamiques. Dès lors, si le document sous-jacent change, les données figurant dans ces deux objets doivent changer également. Par conséquent, si vous avez un **XmlNodeList** qui contient tous les éléments enfants d’un élément particulier (par exemple, l’élément X), puis vous ajoutez un élément supplémentaire, l’élément Q, au document sous l’élément X. Le **XmlNodeList** doit également avoir le nouvel élément Q ajouté à sa collection. L'inverse est vrai également. Si un nœud est ajouté à la **XmlNodeList**, le document sous-jacent est également mis à jour.  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
