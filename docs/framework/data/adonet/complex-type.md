---
title: type complexe
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 50b29e5ae0df37238a16ba08898d307918f0b439
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="complex-type"></a><span data-ttu-id="b5ab9-102">type complexe</span><span class="sxs-lookup"><span data-stu-id="b5ab9-102">complex type</span></span>
<span data-ttu-id="b5ab9-103">A *type complexe* est un modèle pour définir des propriétés riches et structurées sur [types d’entités](../../../../docs/framework/data/adonet/entity-type.md) ou d’autres types complexes.</span><span class="sxs-lookup"><span data-stu-id="b5ab9-103">A *complex type* is a template for defining rich, structured properties on [entity types](../../../../docs/framework/data/adonet/entity-type.md) or on other complex types.</span></span> <span data-ttu-id="b5ab9-104">Chaque modèle contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b5ab9-104">Each template contains the following:</span></span>  
  
-   <span data-ttu-id="b5ab9-105">Nom unique.</span><span class="sxs-lookup"><span data-stu-id="b5ab9-105">A unique name.</span></span> <span data-ttu-id="b5ab9-106">(Requis)</span><span class="sxs-lookup"><span data-stu-id="b5ab9-106">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b5ab9-107">Le nom d'un type complexe ne peut pas être le même qu'un nom de type d'entité dans le même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="b5ab9-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
-   <span data-ttu-id="b5ab9-108">Données sous la forme d’un ou plusieurs [propriétés](../../../../docs/framework/data/adonet/property.md).</span><span class="sxs-lookup"><span data-stu-id="b5ab9-108">Data in the form of one or more [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="b5ab9-109">(Facultatif)</span><span class="sxs-lookup"><span data-stu-id="b5ab9-109">(Optional.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b5ab9-110">Une propriété d'un type complexe peut être un autre type complexe.</span><span class="sxs-lookup"><span data-stu-id="b5ab9-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="b5ab9-111">Un type complexe est semblable à un type d'entité en ce sens qu'il peut acheminer une charge utile de données sous la forme de propriétés de type primitif ou d'autres types complexes.</span><span class="sxs-lookup"><span data-stu-id="b5ab9-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="b5ab9-112">Toutefois, il existe des différences clés entre les types complexes et les types d'entités :</span><span class="sxs-lookup"><span data-stu-id="b5ab9-112">However, there are some key differences between complex types and entity types:</span></span>  
  
-   <span data-ttu-id="b5ab9-113">Les types complexes n'ont pas d'identité et, par conséquent, ne peuvent pas exister indépendamment.</span><span class="sxs-lookup"><span data-stu-id="b5ab9-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="b5ab9-114">Les types complexes peuvent uniquement exister en tant que propriétés sur des types d'entités ou d'autres types complexes.</span><span class="sxs-lookup"><span data-stu-id="b5ab9-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
-   <span data-ttu-id="b5ab9-115">Les types complexes ne peuvent pas participer [associations](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="b5ab9-115">Complex types cannot participate in [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="b5ab9-116">Aucune terminaison d’association peut être un type complexe et par conséquent [propriétés de navigation](../../../../docs/framework/data/adonet/navigation-property.md) ne peut pas être définie sur des types complexes.</span><span class="sxs-lookup"><span data-stu-id="b5ab9-116">Neither end of an association can be a complex type, and therefore [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5ab9-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="b5ab9-117">Example</span></span>  
 <span data-ttu-id="b5ab9-118">Le [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="b5ab9-118">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="b5ab9-119">Le CSDL suivant définit un type complexe, Address, avec les propriétés de type primitif `StreetAddress`, `City`, `StateOrProvince`, `Country` et `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="b5ab9-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="b5ab9-120">Pour définir le type complexe `Address` (ci-dessus) en tant que propriété sur un type d'entité, vous devez déclarer le type de propriété dans la définition de type d'entité.</span><span class="sxs-lookup"><span data-stu-id="b5ab9-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="b5ab9-121">Le CSDL suivant déclare la propriété `Address` en tant que type complexe sur un type d'entité (Publisher) :</span><span class="sxs-lookup"><span data-stu-id="b5ab9-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="b5ab9-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5ab9-122">See Also</span></span>  
 [<span data-ttu-id="b5ab9-123">Concepts clés d’Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="b5ab9-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="b5ab9-124">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="b5ab9-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
