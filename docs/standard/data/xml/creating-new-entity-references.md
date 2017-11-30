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
# <a name="creating-new-entity-references"></a><span data-ttu-id="f33b6-102">Création de nouvelles références d'entité</span><span class="sxs-lookup"><span data-stu-id="f33b6-102">Creating New Entity References</span></span>
<span data-ttu-id="f33b6-103">Le **CreateEntityReference** méthode crée un nouvel **XmlEntityReference** nœud.</span><span class="sxs-lookup"><span data-stu-id="f33b6-103">The **CreateEntityReference** method creates a new **XmlEntityReference** node.</span></span> <span data-ttu-id="f33b6-104">Le DOM (Document Object Model) XML vérifie si le nom de l'entité référencée a déjà été déclaré.</span><span class="sxs-lookup"><span data-stu-id="f33b6-104">The XML Document Object Model (DOM) looks to see if the entity name being referenced has already been declared.</span></span> <span data-ttu-id="f33b6-105">S’il a, les nœuds enfants du **XmlEntityReference** nœud sont copiés à partir du nœud de déclaration d’entité.</span><span class="sxs-lookup"><span data-stu-id="f33b6-105">If it has, the child nodes of **XmlEntityReference** node are copied from the entity declaration node.</span></span> <span data-ttu-id="f33b6-106">Si aucune déclaration d'entité ne correspond, un nœud de texte vide est joint en tant qu'unique enfant du nœud de référence d'entité.</span><span class="sxs-lookup"><span data-stu-id="f33b6-106">If there is no entity declaration that matches, an empty text node is attached as the only child of the entity reference node.</span></span> <span data-ttu-id="f33b6-107">Étant donné que les nœuds enfants de la **XmlEntityReference** nœud sont des copies d’autres nœuds, les nœuds enfants sont en lecture seule et ne peut pas être modifiées.</span><span class="sxs-lookup"><span data-stu-id="f33b6-107">Because the child nodes of the **XmlEntityReference** node are copies of other nodes, these child nodes are read-only and cannot be modified.</span></span>  
  
 <span data-ttu-id="f33b6-108">Lorsque les nœuds sont copiés, il est possible qu'un espace de noms soit dans la portée à la position de la référence d'entité.</span><span class="sxs-lookup"><span data-stu-id="f33b6-108">When the nodes are copied, there may be a namespace in scope at the point of the entity reference.</span></span> <span data-ttu-id="f33b6-109">Cet espace de noms a une incidence sur la configuration de tous les nœuds d'élément ou d'attribut générés.</span><span class="sxs-lookup"><span data-stu-id="f33b6-109">This namespace affects the configuration of any element or attribute nodes generated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f33b6-110">Le DOM ajoute des nœuds enfants à la **EntityReference** uniquement lorsque vous insérez le **EntityReference** nœud dans le document.</span><span class="sxs-lookup"><span data-stu-id="f33b6-110">The DOM adds child nodes to the **EntityReference** only when you insert the **EntityReference** node to the document.</span></span> <span data-ttu-id="f33b6-111">Qui vient d’être créé **EntityReference** nœuds ne comporter aucun des nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="f33b6-111">Newly created **EntityReference** nodes have no child nodes.</span></span>  
  
 <span data-ttu-id="f33b6-112">Bien que le **XmlDataDocument** est une classe dérivée de la **XmlDocument**, le **XmlDataDocument** ne prend pas en charge la création de références d’entité.</span><span class="sxs-lookup"><span data-stu-id="f33b6-112">Even though the **XmlDataDocument** is a derived class of the **XmlDocument**, the **XmlDataDocument** does not support the creation of entity references.</span></span> <span data-ttu-id="f33b6-113">C’est parce que **EntityReference** enfants sont en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="f33b6-113">This is because **EntityReference** children are read-only.</span></span> <span data-ttu-id="f33b6-114">Les enfants d’un **EntityReference** nœud peut s’étendre sur plusieurs régions.</span><span class="sxs-lookup"><span data-stu-id="f33b6-114">The children of an **EntityReference** node can span more than one region.</span></span> <span data-ttu-id="f33b6-115">Dans ce cas, partie d’une ligne associée à la région qui contient une partie d’un **EntityReference** seront en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="f33b6-115">In this case, part of a row associated with the region that contains a part of an **EntityReference** will be read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f33b6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f33b6-116">See Also</span></span>  
 [<span data-ttu-id="f33b6-117">Document Object Model (DOM) XML</span><span class="sxs-lookup"><span data-stu-id="f33b6-117">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
