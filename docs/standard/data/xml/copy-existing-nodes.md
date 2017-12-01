---
title: "Copie de nœuds existants"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 11f3915dfebd7ad9d3144c9bedcd7f42b4754359
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="copy-existing-nodes"></a>Copie de nœuds existants
Il existe des nombreuses méthodes et propriétés dans l’objet modèle DOM (Document XML) vous pouvez utiliser pour sélectionner un nœud, tel que **SelectSingleNode**, **ChildNodes [int i]**, **attributs [int i]**. Une fois le nœud sélectionné, vous pouvez l’insérer dans l’arborescence à l’aide de l’une des méthodes d’insertion adaptées à ce type de nœud particulier. La seule restriction à l'insertion d'un nœud dans l'arborescence est que cette opération ne doit pas compromettre la validité du format du document. Quand un nœud existant est inséré dans l’arborescence DOM, il est supprimé de sa position d’origine et ajouté à sa position de destination.  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
