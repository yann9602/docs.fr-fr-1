---
title: "Lecture de déclarations d'entité et de références d'entité vers le DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6370db06cbe7ff8d46258b0315059f5c37587fea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a>Lecture de déclarations d'entité et de références d'entité vers le DOM
Une entité est une déclaration établissant qu'un certain nom doit être utilisé dans les données XML en lieu et place d'un contenu ou d'un balisage donné. Une entité présente deux aspects. D'une part, vous devez associer un nom au contenu de remplacement, au moyen d'une déclaration d'entité. Une déclaration d'entité est créée au moyen de la syntaxe `<!ENTITY name "value">` dans une DTD ou un schéma XML. D'autre part, le nom défini dans la déclaration d'entité est utilisé par la suite dans les données XML. Ce nom, une fois employé dans le code XML, est appelé référence d'entité. Par exemple, la déclaration d'entité suivante déclare une entité portant le nom `publisher` associé au contenu de « Microsoft Press ».  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 L'exemple suivant illustre l'utilisation de cette déclaration d'entité dans le code XML en tant que référence d'entité.  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Certains analyseurs développent automatiquement des entités lors du chargement d'un document en mémoire. Dès lors, lorsque le code XML est lu et chargé en mémoire, les déclarations d'entité sont mémorisées et enregistrées. Ensuite, quand l'analyseur rencontre des caractères `&;` qui identifient une référence d'entité générale, il recherche ce nom dans une table de déclaration d'entité. La référence, `&publisher;`, est remplacée par le contenu qu'elle représente. À l'aide du code XML suivant,  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 le développement de la référence d'entité et le remplacement de `&publisher;` par le contenu Microsoft Press produit les données XML développées suivantes :  
  
 **Sortie**  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 Il existe diverses sortes d'entités. Le diagramme suivant montre la répartition des types d'entité et leur terminologie.  
  
 ![Organigramme de la hiérarchie de type d’entité](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")  
  
 La valeur par défaut pour l’implémentation de Microsoft .NET Framework de l’objet de modèle DOM (Document XML) consiste à conserver les références d’entités et ne développe pas les entités lors du chargement du XML. La conséquence de cela est que lorsqu’un document est chargé dans le DOM, un **XmlEntityReference** nœud contenant la variable de référence `&publisher;` est créée, avec des nœuds enfants représentant le contenu de l’entité déclarée dans la DTD.  
  
 À l’aide de la `<!ENTITY publisher "Microsoft Press">` déclaration d’entité, le diagramme suivant illustre la **XmlEntity** et **XmlText** nœuds créés à partir de cette déclaration.  
  
 ![nœuds créés à partir de la déclaration d’entité](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")  
  
 Les différences qu’il existe entre les références d’entité développées et non développées concernent les nœuds qui sont générés dans l’arborescence DOM en mémoire. La différence dans les nœuds générés est expliquée dans les rubriques [conservation des références d’entité](../../../../docs/standard/data/xml/entity-references-are-preserved.md) et [références d’entité sont développement sans conservation des](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
