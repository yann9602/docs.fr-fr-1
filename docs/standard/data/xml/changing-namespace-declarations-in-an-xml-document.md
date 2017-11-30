---
title: "Modification des déclarations d'espace de noms dans un document XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 627882efcbc41310ee177cba984e4add5b07bd15
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a><span data-ttu-id="74cb2-102">Modification des déclarations d'espace de noms dans un document XML</span><span class="sxs-lookup"><span data-stu-id="74cb2-102">Changing Namespace Declarations in an XML Document</span></span>
<span data-ttu-id="74cb2-103">Le **XmlDocument** expose des déclarations d’espace de noms et **xmlns** attributs en tant que partie du modèle objet de document.</span><span class="sxs-lookup"><span data-stu-id="74cb2-103">The **XmlDocument** exposes namespace declarations and **xmlns** attributes as part of the document object model.</span></span> <span data-ttu-id="74cb2-104">Ils sont stockés dans le **XmlDocument**, de sorte que lorsque vous enregistrez le document, il peut préserver l’emplacement de ces attributs.</span><span class="sxs-lookup"><span data-stu-id="74cb2-104">These are stored in the **XmlDocument**, so when you save the document, it can preserve the location of those attributes.</span></span> <span data-ttu-id="74cb2-105">Modifier ces attributs n’a aucun effet sur le **nom**, **NamespaceURI**, et **préfixe** propriétés d’autres nœuds figurant déjà dans l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="74cb2-105">Changing these attributes has no affect on the **Name**, **NamespaceURI**, and **Prefix** properties of other nodes already in the tree.</span></span> <span data-ttu-id="74cb2-106">Par exemple, si vous chargez le document suivant, puis le `test` élément a **NamespaceURI**`123.`</span><span class="sxs-lookup"><span data-stu-id="74cb2-106">For example, if you load the following document, then the `test` element has **NamespaceURI** `123.`</span></span>  
  
```xml  
<test xmlns="123"/>  
```  
  
 <span data-ttu-id="74cb2-107">Si vous supprimez le `xmlns` d’attribut, procédez comme suit le `test` élément a toujours la **NamespaceURI** de `123`.</span><span class="sxs-lookup"><span data-stu-id="74cb2-107">If you remove the `xmlns` attribute as follows, then the `test` element still has the **NamespaceURI** of `123`.</span></span>  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 <span data-ttu-id="74cb2-108">De même, si vous ajoutez un autre `xmlns` attribut le `doc` élément comme suit, puis le `test` élément a toujours **NamespaceURI** `123`.</span><span class="sxs-lookup"><span data-stu-id="74cb2-108">Likewise, if you add a different `xmlns` attribute to the `doc` element as follows, then the `test` element still has **NamespaceURI** `123`.</span></span>  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 <span data-ttu-id="74cb2-109">Par conséquent, la modification `xmlns` attributs n’a aucun effet jusqu'à ce que vous enregistrerez et recharger le **XmlDocument** objet.</span><span class="sxs-lookup"><span data-stu-id="74cb2-109">Therefore, changing `xmlns` attributes will have no affect until you save and reload the **XmlDocument** object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74cb2-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74cb2-110">See Also</span></span>  
 [<span data-ttu-id="74cb2-111">Document Object Model (DOM) XML</span><span class="sxs-lookup"><span data-stu-id="74cb2-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
