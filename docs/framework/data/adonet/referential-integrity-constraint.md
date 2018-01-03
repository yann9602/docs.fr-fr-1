---
title: "contrainte d'intégrité référentielle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 232098a4940e223fd8553eefa4964777b1695c5b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="referential-integrity-constraint"></a><span data-ttu-id="cd6c4-102">contrainte d'intégrité référentielle</span><span class="sxs-lookup"><span data-stu-id="cd6c4-102">referential integrity constraint</span></span>
<span data-ttu-id="cd6c4-103">A *contrainte d’intégrité référentielle* dans le modèle EDM (Entity Data Model) est similaire à une contrainte d’intégrité référentielle dans une base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="cd6c4-103">A *referential integrity constraint* in the Entity Data Model (EDM) is similar to a referential integrity constraint in a relational database.</span></span> <span data-ttu-id="cd6c4-104">De la même façon qu’une colonne (ou les colonnes) à partir d’une table de base de données peuvent faire référence à la clé primaire d’une autre table, un [propriété](../../../../docs/framework/data/adonet/property.md) (ou propriétés) d’un [type d’entité](../../../../docs/framework/data/adonet/entity-type.md) peut faire référence à la [clé d’entité ](../../../../docs/framework/data/adonet/entity-key.md) d’un autre type d’entité.</span><span class="sxs-lookup"><span data-stu-id="cd6c4-104">In the same way that a column (or columns) from a database table can reference the primary key of another table, a [property](../../../../docs/framework/data/adonet/property.md) (or properties) of an [entity type](../../../../docs/framework/data/adonet/entity-type.md) can reference the [entity key](../../../../docs/framework/data/adonet/entity-key.md) of another entity type.</span></span> <span data-ttu-id="cd6c4-105">Le type d’entité référencé est appelé le *fin principal* de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="cd6c4-105">The entity type that is referenced is called the *principal end* of the constraint.</span></span> <span data-ttu-id="cd6c4-106">Le type d’entité qui fait référence à la terminaison principale est appelé le *terminaison dépendante* de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="cd6c4-106">The entity type that references the principal end is called the *dependent end* of the constraint.</span></span>  
  
 <span data-ttu-id="cd6c4-107">Une contrainte d’intégrité référentielle est définie en tant que partie d’un [association](../../../../docs/framework/data/adonet/association-type.md) entre deux types d’entité.</span><span class="sxs-lookup"><span data-stu-id="cd6c4-107">A referential integrity constraint is defined as part of an [association](../../../../docs/framework/data/adonet/association-type.md) between two entity types.</span></span> <span data-ttu-id="cd6c4-108">La définition d'une contrainte d'intégrité référentielle spécifie les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="cd6c4-108">The definition for a referential integrity constraint specifies the following information:</span></span>  
  
-   <span data-ttu-id="cd6c4-109">Terminaison principale de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="cd6c4-109">The principal end of the constraint.</span></span> <span data-ttu-id="cd6c4-110">(Type d'entité dont la clé d'entité est référencée par la terminaison dépendante.)</span><span class="sxs-lookup"><span data-stu-id="cd6c4-110">(An entity type whose entity key is referenced by the dependent end.)</span></span>  
  
-   <span data-ttu-id="cd6c4-111">Clé d'entité de la terminaison principale.</span><span class="sxs-lookup"><span data-stu-id="cd6c4-111">The entity key of the principal end.</span></span>  
  
-   <span data-ttu-id="cd6c4-112">Terminaison dépendante de la contrainte.</span><span class="sxs-lookup"><span data-stu-id="cd6c4-112">The dependent end of the constraint.</span></span> <span data-ttu-id="cd6c4-113">(Type d'entité dont une ou plusieurs propriétés référencent la clé d'entité de la terminaison principale.)</span><span class="sxs-lookup"><span data-stu-id="cd6c4-113">(An entity type that has a property or properties that reference the entity key of the principal end.)</span></span>  
  
-   <span data-ttu-id="cd6c4-114">Propriété ou propriétés de référence de la terminaison dépendante.</span><span class="sxs-lookup"><span data-stu-id="cd6c4-114">The referencing property or properties of the dependent end.</span></span>  
  
 <span data-ttu-id="cd6c4-115">Les contraintes d'intégrité référentielle dans le modèle EDM ont pour objectif de vérifier que des associations valides existent toujours.</span><span class="sxs-lookup"><span data-stu-id="cd6c4-115">The purpose of referential integrity constraints in the EDM is to ensure that valid associations always exist.</span></span> <span data-ttu-id="cd6c4-116">Pour plus d’informations, consultez [propriété de clé étrangère](../../../../docs/framework/data/adonet/foreign-key-property.md).</span><span class="sxs-lookup"><span data-stu-id="cd6c4-116">For more information, see [foreign key property](../../../../docs/framework/data/adonet/foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd6c4-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="cd6c4-117">Example</span></span>  
 <span data-ttu-id="cd6c4-118">Le diagramme suivant montre un modèle conceptuel avec deux associations : `WrittenBy` et `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="cd6c4-118">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span> <span data-ttu-id="cd6c4-119">Le type d'entité `Book` a une propriété, `PublisherId`, qui référence la clé d'entité du type d'entité `Publisher` lorsque vous définissez une contrainte d'intégrité référentielle sur l'association `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="cd6c4-119">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="cd6c4-120">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span><span class="sxs-lookup"><span data-stu-id="cd6c4-120">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span></span>  
  
 <span data-ttu-id="cd6c4-121">Le [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="cd6c4-121">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="cd6c4-122">Le CSDL suivant définit une contrainte d'intégrité référentielle sur l'association `PublishedBy` présentée dans le modèle conceptuel ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="cd6c4-122">The following CSDL defines a referential integrity constraint on the `PublishedBy` association shown in the conceptual model above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="cd6c4-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd6c4-123">See Also</span></span>  
 [<span data-ttu-id="cd6c4-124">Concepts clés d’Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="cd6c4-124">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="cd6c4-125">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="cd6c4-125">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
