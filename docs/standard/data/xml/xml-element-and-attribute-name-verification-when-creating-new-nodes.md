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
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="c56c6-102">Vérification des noms d'attribut et d'élément XML lors de la création de nœuds</span><span class="sxs-lookup"><span data-stu-id="c56c6-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="c56c6-103">Le DOM (Document Object Model) XML contrôle la validité des noms lors de la création de nœuds d'élément ou d'attribut.</span><span class="sxs-lookup"><span data-stu-id="c56c6-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="c56c6-104">Si ces noms contiennent des caractères non conformes, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="c56c6-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="c56c6-105">Pour garantir que les noms sont valides et encodés correctement, vous devez utiliser le **XmlConvert** classe pour coder le nom et le décoder à nouveau au niveau de l’application.</span><span class="sxs-lookup"><span data-stu-id="c56c6-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="c56c6-106">Le **XmlWriter** possède des méthodes qui effectuent des opérations supplémentaires pour garantir le XML bien formé est généré.</span><span class="sxs-lookup"><span data-stu-id="c56c6-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c56c6-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c56c6-107">See Also</span></span>  
 [<span data-ttu-id="c56c6-108">Document Object Model (DOM) XML</span><span class="sxs-lookup"><span data-stu-id="c56c6-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
