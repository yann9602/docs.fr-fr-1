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
# <a name="copy-existing-nodes"></a><span data-ttu-id="20bda-102">Copie de nœuds existants</span><span class="sxs-lookup"><span data-stu-id="20bda-102">Copy Existing Nodes</span></span>
<span data-ttu-id="20bda-103">Il existe des nombreuses méthodes et propriétés dans l’objet modèle DOM (Document XML) vous pouvez utiliser pour sélectionner un nœud, tel que **SelectSingleNode**, **ChildNodes [int i]**, **attributs [int i]**.</span><span class="sxs-lookup"><span data-stu-id="20bda-103">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="20bda-104">Une fois le nœud sélectionné, vous pouvez l’insérer dans l’arborescence à l’aide de l’une des méthodes d’insertion adaptées à ce type de nœud particulier.</span><span class="sxs-lookup"><span data-stu-id="20bda-104">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="20bda-105">La seule restriction à l'insertion d'un nœud dans l'arborescence est que cette opération ne doit pas compromettre la validité du format du document.</span><span class="sxs-lookup"><span data-stu-id="20bda-105">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="20bda-106">Quand un nœud existant est inséré dans l’arborescence DOM, il est supprimé de sa position d’origine et ajouté à sa position de destination.</span><span class="sxs-lookup"><span data-stu-id="20bda-106">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20bda-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20bda-107">See Also</span></span>  
 [<span data-ttu-id="20bda-108">Document Object Model (DOM) XML</span><span class="sxs-lookup"><span data-stu-id="20bda-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
