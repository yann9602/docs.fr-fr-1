---
title: "propriété de navigation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f5af52532dc534d793e7e8ce72a08c2f7229569b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="navigation-property"></a><span data-ttu-id="ed0c1-102">propriété de navigation</span><span class="sxs-lookup"><span data-stu-id="ed0c1-102">navigation property</span></span>
<span data-ttu-id="ed0c1-103">A *propriété de navigation* est une propriété facultative sur un [type d’entité](../../../../docs/framework/data/adonet/entity-type.md) qui permet de naviguer d’une [fin](../../../../docs/framework/data/adonet/association-end.md) d’un [association](../../../../docs/framework/data/adonet/association-type.md) à l’autre extrémité.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-103">A *navigation property* is an optional property on an [entity type](../../../../docs/framework/data/adonet/entity-type.md) that allows for navigation from one [end](../../../../docs/framework/data/adonet/association-end.md) of an [association](../../../../docs/framework/data/adonet/association-type.md) to the other end.</span></span> <span data-ttu-id="ed0c1-104">Contrairement à d’autres [propriétés](../../../../docs/framework/data/adonet/property.md), les propriétés de navigation n’acheminent pas de données.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-104">Unlike other [properties](../../../../docs/framework/data/adonet/property.md), navigation properties do not carry data.</span></span>  
  
 <span data-ttu-id="ed0c1-105">Une définition de propriété de navigation comprend les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="ed0c1-105">A navigation property definition includes the following:</span></span>  
  
-   <span data-ttu-id="ed0c1-106">Nom.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-106">A name.</span></span> <span data-ttu-id="ed0c1-107">(Requis)</span><span class="sxs-lookup"><span data-stu-id="ed0c1-107">(Required)</span></span>  
  
-   <span data-ttu-id="ed0c1-108">Association faisant l'objet de la navigation.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-108">The association that it navigates.</span></span> <span data-ttu-id="ed0c1-109">(Requis)</span><span class="sxs-lookup"><span data-stu-id="ed0c1-109">(Required)</span></span>  
  
-   <span data-ttu-id="ed0c1-110">Terminaisons de l'association faisant l'objet de la navigation.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-110">The ends of the association that it navigates.</span></span> <span data-ttu-id="ed0c1-111">(Requis)</span><span class="sxs-lookup"><span data-stu-id="ed0c1-111">(Required)</span></span>  
  
 <span data-ttu-id="ed0c1-112">Notez que les propriétés de navigation sont facultatives sur les deux types d'entités au niveau des terminaisons d'une association.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-112">Note that navigation properties are optional on both entity types at the ends of an association.</span></span> <span data-ttu-id="ed0c1-113">Si vous définissez une propriété de navigation sur un type d'entité au niveau de la terminaison d'une association, il n'est pas nécessaire de définir une propriété de navigation sur le type d'entité à l'autre terminaison de l'association.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-113">If you define a navigation property on one entity type at the end of an association, you do not have to define a navigation property on the entity type at the other end of the association.</span></span>  
  
 <span data-ttu-id="ed0c1-114">Le type de données d’une propriété de navigation est déterminé par le [multiplicité](../../../../docs/framework/data/adonet/association-end-multiplicity.md) de sa distance [end d’association](../../../../docs/framework/data/adonet/association-end.md).</span><span class="sxs-lookup"><span data-stu-id="ed0c1-114">The data type of a navigation property is determined by the [multiplicity](../../../../docs/framework/data/adonet/association-end-multiplicity.md) of its remote [association end](../../../../docs/framework/data/adonet/association-end.md).</span></span> <span data-ttu-id="ed0c1-115">Par exemple, considérez une propriété de navigation, `OrdersNavProp`, qui existe sur un type d'entité `Customer` et qui navigue dans une association un-à-plusieurs entre `Customer` et `Order`.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-115">For example, suppose a navigation property, `OrdersNavProp`, exists on a `Customer` entity type and navigates a one-to-many association between `Customer` and `Order`.</span></span> <span data-ttu-id="ed0c1-116">Étant donné que la terminaison d'association distante pour la propriété de navigation a une multiplicité égale à plusieurs (\*), son type de données est une collection (d'`Order`).</span><span class="sxs-lookup"><span data-stu-id="ed0c1-116">Because the remote association end for the navigation property has multiplicity of many (\*), its data type is a collection (of `Order`).</span></span> <span data-ttu-id="ed0c1-117">De même, si une propriété de navigation, `CustomerNavProp`, existe sur le type d'entité `Order`, son type de données est `Customer`, car la multiplicité de la terminaison distante est un (1).</span><span class="sxs-lookup"><span data-stu-id="ed0c1-117">Similarly, if a navigation property, `CustomerNavProp`, exists on the `Order` entity type, its data type would be `Customer`, because the multiplicity of the remote end is one (1).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed0c1-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="ed0c1-118">Example</span></span>  
 <span data-ttu-id="ed0c1-119">Le diagramme suivant montre un modèle conceptuel avec trois types d'entités : `Book`, `Publisher` et `Author`.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="ed0c1-120">Les propriétés de navigation, `Publisher` et `Authors`, sont définies sur le type d'entité Book.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-120">Navigation properties, `Publisher` and `Authors`, are defined on the Book entity type.</span></span> <span data-ttu-id="ed0c1-121">La propriété de navigation `Books` est définie sur le type d'entité Publisher et le type d'entité `Author`.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-121">Navigation property `Books` is defined on both the Publisher entity type and the `Author` entity type.</span></span>  
  
 <span data-ttu-id="ed0c1-122">![Modèle avec propriétés de Navigation](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")</span><span class="sxs-lookup"><span data-stu-id="ed0c1-122">![Model with Navigation Properties](../../../../docs/framework/data/adonet/media/modelwithnavprops.gif "ModelWithNavProps")</span></span>  
  
 <span data-ttu-id="ed0c1-123">Le [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-123">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="ed0c1-124">Le CSDL suivant définit le type d'entité `Book` présenté dans le diagramme ci-dessus :</span><span class="sxs-lookup"><span data-stu-id="ed0c1-124">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="ed0c1-125">Notez que des attributs XML sont utilisés pour communiquer les informations nécessaires pour définir une propriété de navigation. L'attribut `Name` contient le nom de la propriété, `Relationship` contient le nom de l'association faisant l'objet de la navigation, et `FromRole` et `ToRole` contiennent les terminaisons de l'association.</span><span class="sxs-lookup"><span data-stu-id="ed0c1-125">Note that XML attributes are used to communicate the information necessary to define a navigation property: The attribute `Name` contains the name of the property, `Relationship` contains the name of the association it navigates, and `FromRole` and `ToRole` contain the ends of the association.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed0c1-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed0c1-126">See Also</span></span>  
 [<span data-ttu-id="ed0c1-127">Concepts clés d’Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="ed0c1-127">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="ed0c1-128">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="ed0c1-128">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
