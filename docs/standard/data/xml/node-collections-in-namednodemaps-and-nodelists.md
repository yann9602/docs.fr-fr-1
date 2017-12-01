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
# <a name="node-collections-in-namednodemaps-and-nodelists"></a>Collections de nœuds dans NamedNodeMap et NodeList
Il est possible d’extraire une collection de nœuds et de les placer dans une collection triée ou non. Si vous regroupez une collection de nœuds dans une collection non triée, cet ensemble est appelé NamedNodeMap par le World Wide Web Consortium (W3C). Ce type de collection vous permet d'extraire des données au moyen de leur nom ou de l'index. En revanche, si vous placez une collection de nœuds dans une collection triée, celle-ci est appelée NodeList par le W3C, et ses données peuvent être extraites au moyen d'un index de base zéro. NamedNodeMap et NodeList sont décrits par le W3C. Les implémentations de Microsoft .NET Framework pour NamedNodeMap est la **XmlNamedNodeMap**, et la liste de nœuds est implémenté par le **XmlNodeList**.  
  
 Pour plus d’informations sur la collection non triée, voir [extraction de nœuds non triée par nom ou Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md). Pour plus d’informations sur la collection triée, voir [extraction de nœuds triés par l’Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
