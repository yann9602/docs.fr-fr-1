---
title: "Conservation des références d'entité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 770c714e8f5942ea733c417ae9b06f69e4acf1a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="entity-references-are-preserved"></a>Conservation des références d'entité
Une fois que la référence d’entité n’est pas développée, mais préservée, le modèle d’objet Document (DOM) XML crée un **XmlEntityReference** nœud lorsqu’il rencontre une référence d’entité.  
  
 À l'aide du code XML suivant,  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 le DOM crée un **XmlEntityReference** nœud lorsqu’il rencontre le `&publisher;` référence. Le **XmlEntityReference** contient des nœuds enfants copiés à partir du contenu dans la déclaration d’entité. L’exemple de code précédent contient du texte dans la déclaration d’entité, par conséquent, un **XmlText** nœud est créé en tant que le nœud enfant du nœud de référence d’entité.  
  
 ![Arborescence pour références d’entité préservées](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")  
Structure d’arborescence avec références d’entité préservées  
  
 Les nœuds enfants de la **XmlEntityReference** sont des nœuds créés à partir de copies de tous les enfants du **XmlEntity** nœud lors de la déclaration d’entité a été rencontrée.  
  
> [!NOTE]
>  Les nœuds copiés à partir de la **XmlEntity** ne sont pas toujours des copies exactes une fois placés sous le nœud de référence d’entité. Il peut y avoir des espaces de noms qui sont dans la portée au niveau du nœud de référence d'entité et qui ont une incidence sur la configuration finale des nœuds enfants.  
  
 Par défaut, des entités générales telles que `&abc;` sont conservés et **XmlEntityReference** nœuds toujours créés.  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
