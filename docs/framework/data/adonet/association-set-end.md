---
title: terminaison d'ensemble d'associations
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ddb7dc758de8d40a2c80a09f93d44600b7c75b56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="association-set-end"></a><span data-ttu-id="100a2-102">terminaison d'ensemble d'associations</span><span class="sxs-lookup"><span data-stu-id="100a2-102">association set end</span></span>
<span data-ttu-id="100a2-103">Une *ensemble d’associations* identifie le [type d’entité](../../../../docs/framework/data/adonet/entity-type.md) et le [jeu d’entités](../../../../docs/framework/data/adonet/entity-set.md) à la fin d’une [ensemble d’associations](../../../../docs/framework/data/adonet/association-set.md).</span><span class="sxs-lookup"><span data-stu-id="100a2-103">An *association set end* identifies the [entity type](../../../../docs/framework/data/adonet/entity-type.md) and the [entity set](../../../../docs/framework/data/adonet/entity-set.md) at the end of an [association set](../../../../docs/framework/data/adonet/association-set.md).</span></span> <span data-ttu-id="100a2-104">Les terminaisons d'ensemble d'associations sont définies dans le cadre d'un ensemble d'associations ; un ensemble d'associations doit avoir exactement deux terminaisons d'ensemble d'associations.</span><span class="sxs-lookup"><span data-stu-id="100a2-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="100a2-105">Une définition de terminaison d'ensemble d'associations contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="100a2-105">An association set end definition contains the following information:</span></span>  
  
-   <span data-ttu-id="100a2-106">Un des types d'entité impliqués dans l'ensemble d'associations.</span><span class="sxs-lookup"><span data-stu-id="100a2-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="100a2-107">(Requis)</span><span class="sxs-lookup"><span data-stu-id="100a2-107">(Required)</span></span>  
  
-   <span data-ttu-id="100a2-108">Jeu d'entités pour le type d'entité impliqué dans l'ensemble d'associations.</span><span class="sxs-lookup"><span data-stu-id="100a2-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="100a2-109">(Requis)</span><span class="sxs-lookup"><span data-stu-id="100a2-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="100a2-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="100a2-110">Example</span></span>  
 <span data-ttu-id="100a2-111">Le diagramme suivant montre un modèle conceptuel avec deux associations : `WrittenBy` et `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="100a2-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 <span data-ttu-id="100a2-112">![Exemple de modèle](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="100a2-112">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="100a2-113">Le diagramme suivant montre un ensemble d'associations (`PublishedBy`) et deux jeux d'entités (`Books` et `Publishers`) selon le modèle conceptuel présenté ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="100a2-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="100a2-114">Les terminaisons d'ensemble d'associations sont les jeux d'entités `Books` et `Publishers`.</span><span class="sxs-lookup"><span data-stu-id="100a2-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="100a2-115">BI dans le `Books` jeu d’entités représente une instance de la `Book` type d’entité en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="100a2-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="100a2-116">De même, Pj représente un `Publisher` d’instance dans le `Publishers` jeu d’entités.</span><span class="sxs-lookup"><span data-stu-id="100a2-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="100a2-117">BiPj représente une instance de la `PublishedBy` association dans le `PublishedBy` ensemble d’associations.</span><span class="sxs-lookup"><span data-stu-id="100a2-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 <span data-ttu-id="100a2-118">![Définit l’exemple](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span><span class="sxs-lookup"><span data-stu-id="100a2-118">![Sets Example](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span></span>  
  
 <span data-ttu-id="100a2-119">Le [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage DSL, appelé langage de définition de schéma conceptuel ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="100a2-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="100a2-120">Le CSDL suivant définit un conteneur d'entités avec un ensemble d'associations pour chaque association dans le diagramme ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="100a2-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="100a2-121">Notez que les terminaisons d'ensemble d'associations sont définies dans le cadre de chaque définition d'ensemble d'associations.</span><span class="sxs-lookup"><span data-stu-id="100a2-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="100a2-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="100a2-122">See Also</span></span>  
 [<span data-ttu-id="100a2-123">Concepts clés d’Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="100a2-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="100a2-124">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="100a2-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
