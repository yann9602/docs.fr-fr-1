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
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a><span data-ttu-id="7cba4-102">Lecture de déclarations d'entité et de références d'entité vers le DOM</span><span class="sxs-lookup"><span data-stu-id="7cba4-102">Reading Entity Declarations and Entity References into the DOM</span></span>
<span data-ttu-id="7cba4-103">Une entité est une déclaration établissant qu'un certain nom doit être utilisé dans les données XML en lieu et place d'un contenu ou d'un balisage donné.</span><span class="sxs-lookup"><span data-stu-id="7cba4-103">An entity is a declaration that states a name to be used in the XML in place of content or markup.</span></span> <span data-ttu-id="7cba4-104">Une entité présente deux aspects.</span><span class="sxs-lookup"><span data-stu-id="7cba4-104">There are two parts to entities.</span></span> <span data-ttu-id="7cba4-105">D'une part, vous devez associer un nom au contenu de remplacement, au moyen d'une déclaration d'entité.</span><span class="sxs-lookup"><span data-stu-id="7cba4-105">First, you must tie a name to the replacement content using an entity declaration.</span></span> <span data-ttu-id="7cba4-106">Une déclaration d'entité est créée au moyen de la syntaxe `<!ENTITY name "value">` dans une DTD ou un schéma XML.</span><span class="sxs-lookup"><span data-stu-id="7cba4-106">An entity declaration is created by using the `<!ENTITY name "value">` syntax in a document type definition (DTD) or XML schema.</span></span> <span data-ttu-id="7cba4-107">D'autre part, le nom défini dans la déclaration d'entité est utilisé par la suite dans les données XML.</span><span class="sxs-lookup"><span data-stu-id="7cba4-107">Secondly, the name defined in the entity declaration is subsequently used in the XML.</span></span> <span data-ttu-id="7cba4-108">Ce nom, une fois employé dans le code XML, est appelé référence d'entité.</span><span class="sxs-lookup"><span data-stu-id="7cba4-108">When used in the XML, it is called an entity reference.</span></span> <span data-ttu-id="7cba4-109">Par exemple, la déclaration d'entité suivante déclare une entité portant le nom `publisher` associé au contenu de « Microsoft Press ».</span><span class="sxs-lookup"><span data-stu-id="7cba4-109">For example, the following entity declaration declares an entity of the name `publisher` being associated with the content of "Microsoft Press".</span></span>  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 <span data-ttu-id="7cba4-110">L'exemple suivant illustre l'utilisation de cette déclaration d'entité dans le code XML en tant que référence d'entité.</span><span class="sxs-lookup"><span data-stu-id="7cba4-110">The following example shows the use of this entity declaration in XML as an entity reference.</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="7cba4-111">Certains analyseurs développent automatiquement des entités lors du chargement d'un document en mémoire.</span><span class="sxs-lookup"><span data-stu-id="7cba4-111">Some parsers automatically expand entities when a document is loaded into memory.</span></span> <span data-ttu-id="7cba4-112">Dès lors, lorsque le code XML est lu et chargé en mémoire, les déclarations d'entité sont mémorisées et enregistrées.</span><span class="sxs-lookup"><span data-stu-id="7cba4-112">Therefore, when the XML is being read into memory, entity declarations are remembered and saved.</span></span> <span data-ttu-id="7cba4-113">Ensuite, quand l'analyseur rencontre des caractères `&;` qui identifient une référence d'entité générale, il recherche ce nom dans une table de déclaration d'entité.</span><span class="sxs-lookup"><span data-stu-id="7cba4-113">When the parser subsequently encounters `&;` characters, which identify a general entity reference, the parser looks up that name in an entity declaration table.</span></span> <span data-ttu-id="7cba4-114">La référence, `&publisher;`, est remplacée par le contenu qu'elle représente.</span><span class="sxs-lookup"><span data-stu-id="7cba4-114">The reference, `&publisher;` is replaced by the content that it represents.</span></span> <span data-ttu-id="7cba4-115">À l'aide du code XML suivant,</span><span class="sxs-lookup"><span data-stu-id="7cba4-115">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="7cba4-116">le développement de la référence d'entité et le remplacement de `&publisher;` par le contenu Microsoft Press produit les données XML développées suivantes :</span><span class="sxs-lookup"><span data-stu-id="7cba4-116">expanding the entity reference and replacing the `&publisher;` with the Microsoft Press content gives the following expanded XML.</span></span>  
  
 <span data-ttu-id="7cba4-117">**Sortie**</span><span class="sxs-lookup"><span data-stu-id="7cba4-117">**Output**</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 <span data-ttu-id="7cba4-118">Il existe diverses sortes d'entités.</span><span class="sxs-lookup"><span data-stu-id="7cba4-118">There are many kinds of entities.</span></span> <span data-ttu-id="7cba4-119">Le diagramme suivant montre la répartition des types d'entité et leur terminologie.</span><span class="sxs-lookup"><span data-stu-id="7cba4-119">The following diagram shows the breakdown of entity types and terminology.</span></span>  
  
 <span data-ttu-id="7cba4-120">![Organigramme de la hiérarchie de type d’entité](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="7cba4-120">![flow chart of entity type hierarchy](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span></span>  
  
 <span data-ttu-id="7cba4-121">La valeur par défaut pour l’implémentation de Microsoft .NET Framework de l’objet de modèle DOM (Document XML) consiste à conserver les références d’entités et ne développe pas les entités lors du chargement du XML.</span><span class="sxs-lookup"><span data-stu-id="7cba4-121">The default for the Microsoft .NET Framework implementation of the XML Document Object Model (DOM) is to preserve the entities references and not expand the entities when the XML is loaded.</span></span> <span data-ttu-id="7cba4-122">La conséquence de cela est que lorsqu’un document est chargé dans le DOM, un **XmlEntityReference** nœud contenant la variable de référence `&publisher;` est créée, avec des nœuds enfants représentant le contenu de l’entité déclarée dans la DTD.</span><span class="sxs-lookup"><span data-stu-id="7cba4-122">The implication of this is that as a document is loaded in the DOM, an **XmlEntityReference** node containing the reference variable `&publisher;` is created, with child nodes representing the content in the entity declared in the DTD.</span></span>  
  
 <span data-ttu-id="7cba4-123">À l’aide de la `<!ENTITY publisher "Microsoft Press">` déclaration d’entité, le diagramme suivant illustre la **XmlEntity** et **XmlText** nœuds créés à partir de cette déclaration.</span><span class="sxs-lookup"><span data-stu-id="7cba4-123">Using the `<!ENTITY publisher "Microsoft Press">` entity declaration, the following diagram shows the **XmlEntity** and **XmlText** nodes created from this declaration.</span></span>  
  
 <span data-ttu-id="7cba4-124">![nœuds créés à partir de la déclaration d’entité](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span><span class="sxs-lookup"><span data-stu-id="7cba4-124">![nodes created from entity declaration](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span></span>  
  
 <span data-ttu-id="7cba4-125">Les différences qu’il existe entre les références d’entité développées et non développées concernent les nœuds qui sont générés dans l’arborescence DOM en mémoire.</span><span class="sxs-lookup"><span data-stu-id="7cba4-125">The differences when entity references are expanded and when they are not makes a difference in what nodes are generated in the DOM tree, in memory.</span></span> <span data-ttu-id="7cba4-126">La différence dans les nœuds générés est expliquée dans les rubriques [conservation des références d’entité](../../../../docs/standard/data/xml/entity-references-are-preserved.md) et [références d’entité sont développement sans conservation des](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span><span class="sxs-lookup"><span data-stu-id="7cba4-126">The difference in the nodes that are generated is explained in the topics [Entity References are Preserved](../../../../docs/standard/data/xml/entity-references-are-preserved.md) and [Entity References are Expanded and Not Preserved](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cba4-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7cba4-127">See Also</span></span>  
 [<span data-ttu-id="7cba4-128">Document Object Model (DOM) XML</span><span class="sxs-lookup"><span data-stu-id="7cba4-128">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
