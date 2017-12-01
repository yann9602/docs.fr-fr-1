---
title: "Création de nouvelles références d'entité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 22e9b66f58275141cf9da154573ca43a0b90affc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-new-entity-references"></a>Création de nouvelles références d'entité
Le **CreateEntityReference** méthode crée un nouvel **XmlEntityReference** nœud. Le DOM (Document Object Model) XML vérifie si le nom de l'entité référencée a déjà été déclaré. S’il a, les nœuds enfants du **XmlEntityReference** nœud sont copiés à partir du nœud de déclaration d’entité. Si aucune déclaration d'entité ne correspond, un nœud de texte vide est joint en tant qu'unique enfant du nœud de référence d'entité. Étant donné que les nœuds enfants de la **XmlEntityReference** nœud sont des copies d’autres nœuds, les nœuds enfants sont en lecture seule et ne peut pas être modifiées.  
  
 Lorsque les nœuds sont copiés, il est possible qu'un espace de noms soit dans la portée à la position de la référence d'entité. Cet espace de noms a une incidence sur la configuration de tous les nœuds d'élément ou d'attribut générés.  
  
> [!NOTE]
>  Le DOM ajoute des nœuds enfants à la **EntityReference** uniquement lorsque vous insérez le **EntityReference** nœud dans le document. Qui vient d’être créé **EntityReference** nœuds ne comporter aucun des nœuds enfants.  
  
 Bien que le **XmlDataDocument** est une classe dérivée de la **XmlDocument**, le **XmlDataDocument** ne prend pas en charge la création de références d’entité. C’est parce que **EntityReference** enfants sont en lecture seule. Les enfants d’un **EntityReference** nœud peut s’étendre sur plusieurs régions. Dans ce cas, partie d’une ligne associée à la région qui contient une partie d’un **EntityReference** seront en lecture seule.  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
