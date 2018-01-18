---
title: type d'association
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5349889017ea23701a17a92947d9750610a52f59
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="association-type"></a><span data-ttu-id="054c9-102">type d'association</span><span class="sxs-lookup"><span data-stu-id="054c9-102">association type</span></span>
<span data-ttu-id="054c9-103">Un *type d’association* (également appelé association) est le bloc de construction fondamental pour décrire les relations dans le modèle EDM (Entity Data Model).</span><span class="sxs-lookup"><span data-stu-id="054c9-103">An *association type* (also called an association) is the fundamental building block for describing relationships in the Entity Data Model (EDM).</span></span> <span data-ttu-id="054c9-104">Dans un modèle conceptuel, une association représente une relation entre deux [types d’entités](../../../../docs/framework/data/adonet/entity-type.md) (tel que `Customer` et `Order`).</span><span class="sxs-lookup"><span data-stu-id="054c9-104">In a conceptual model, an association represents a relationship between two [entity types](../../../../docs/framework/data/adonet/entity-type.md) (such as `Customer` and `Order`).</span></span> <span data-ttu-id="054c9-105">Dans une application, une instance d'une association représente une association spécifique (comme une association entre une instance de `Customer` et une instance d'`Order`).</span><span class="sxs-lookup"><span data-stu-id="054c9-105">In an application, an instance of an association represents a specific association (such as an association between an instance of `Customer` and an instance of `Order`).</span></span> <span data-ttu-id="054c9-106">Instances d’association sont regroupées logiquement dans un [ensemble d’associations](../../../../docs/framework/data/adonet/association-set.md).</span><span class="sxs-lookup"><span data-stu-id="054c9-106">Association instances are logically grouped in an [association set](../../../../docs/framework/data/adonet/association-set.md).</span></span>  
  
 <span data-ttu-id="054c9-107">Une définition d'association contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="054c9-107">An association definition contains the following information:</span></span>  
  
-   <span data-ttu-id="054c9-108">Nom unique.</span><span class="sxs-lookup"><span data-stu-id="054c9-108">A unique name.</span></span> <span data-ttu-id="054c9-109">(Requis)</span><span class="sxs-lookup"><span data-stu-id="054c9-109">(Required)</span></span>  
  
-   <span data-ttu-id="054c9-110">Deux [terminaisons d’association](../../../../docs/framework/data/adonet/association-end.md), un pour chaque type d’entité dans la relation.</span><span class="sxs-lookup"><span data-stu-id="054c9-110">Two [association ends](../../../../docs/framework/data/adonet/association-end.md), one for each entity type in the relationship.</span></span> <span data-ttu-id="054c9-111">(Requis)</span><span class="sxs-lookup"><span data-stu-id="054c9-111">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="054c9-112">Une association ne peut pas représenter de relation entre plus de deux types d'entité.</span><span class="sxs-lookup"><span data-stu-id="054c9-112">An association cannot represent a relationship among more than two entity types.</span></span> <span data-ttu-id="054c9-113">Toutefois, une association peut définir une relation réciproque en spécifiant le même type d'entité pour chacune de ses terminaisons d'association.</span><span class="sxs-lookup"><span data-stu-id="054c9-113">An association can, however, define a self-relationship by specifying the same entity type for each of its association ends.</span></span>  
  
-   <span data-ttu-id="054c9-114">A [contrainte d’intégrité référentielle](../../../../docs/framework/data/adonet/referential-integrity-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="054c9-114">A [referential integrity constraint](../../../../docs/framework/data/adonet/referential-integrity-constraint.md).</span></span> <span data-ttu-id="054c9-115">(facultatif)</span><span class="sxs-lookup"><span data-stu-id="054c9-115">(Optional)</span></span>  
  
 <span data-ttu-id="054c9-116">Chaque terminaison d’association doit spécifier un [multiplicité de terminaison d’association](../../../../docs/framework/data/adonet/association-end-multiplicity.md) qui indique le nombre d’instances de type d’entité qui peuvent être à l’extrémité de l’association.</span><span class="sxs-lookup"><span data-stu-id="054c9-116">Each association end must specify an [association end multiplicity](../../../../docs/framework/data/adonet/association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="054c9-117">La multiplicité de terminaison d'association peut avoir une valeur égale à un (1), zéro ou un (0..1), ou plusieurs (\*).</span><span class="sxs-lookup"><span data-stu-id="054c9-117">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span> <span data-ttu-id="054c9-118">Instances de type d’entité à une extrémité d’une association est accessible via [propriétés de navigation](../../../../docs/framework/data/adonet/navigation-property.md) ou les clés étrangères si elles sont exposées sur un type d’entité.</span><span class="sxs-lookup"><span data-stu-id="054c9-118">Entity type instances at one end of an association can be accessed through [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) or foreign keys if they are exposed on an entity type.</span></span> <span data-ttu-id="054c9-119">Pour plus d’informations, consultez [Entity Data Model : clés étrangères](../../../../docs/framework/data/adonet/foreign-key-property.md).</span><span class="sxs-lookup"><span data-stu-id="054c9-119">For more information, see [Entity Data Model: Foreign Keys](../../../../docs/framework/data/adonet/foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="054c9-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="054c9-120">Example</span></span>  
 <span data-ttu-id="054c9-121">Le diagramme suivant montre un modèle conceptuel avec deux associations : `PublishedBy` et `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="054c9-121">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="054c9-122">Les terminaisons d'association pour l'association `PublishedBy` sont les types d'entité `Book` et `Publisher`.</span><span class="sxs-lookup"><span data-stu-id="054c9-122">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="054c9-123">La multiplicité de la terminaison `Publisher` est un (1) et celle de la terminaison `Book` est plusieurs (\*), ce qui indique qu'un éditeur publie de nombreux livres et qu'un livre est publié par un seul éditeur.</span><span class="sxs-lookup"><span data-stu-id="054c9-123">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 <span data-ttu-id="054c9-124">![Exemple de modèle](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="054c9-124">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="054c9-125">Le [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="054c9-125">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="054c9-126">Le CSDL suivant définit l'association `PublishedBy` présentée dans le diagramme ci-dessus :</span><span class="sxs-lookup"><span data-stu-id="054c9-126">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="054c9-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="054c9-127">See Also</span></span>  
 [<span data-ttu-id="054c9-128">Concepts clés d’Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="054c9-128">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="054c9-129">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="054c9-129">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
