---
title: "Vérification des noms d'attribut et d'élément XML lors de la création de nœuds"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c041d5d2830222f3fae09a39f1ea10eb08772388
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>Vérification des noms d'attribut et d'élément XML lors de la création de nœuds
Le DOM (Document Object Model) XML contrôle la validité des noms lors de la création de nœuds d'élément ou d'attribut. Si ces noms contiennent des caractères non conformes, une exception est levée. Pour garantir que les noms sont valides et encodés correctement, vous devez utiliser le **XmlConvert** classe pour coder le nom et le décoder à nouveau au niveau de l’application. Le **XmlWriter** possède des méthodes qui effectuent des opérations supplémentaires pour garantir le XML bien formé est généré.  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
