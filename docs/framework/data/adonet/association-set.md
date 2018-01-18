---
title: jeu d'associations
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fa977f69951184629f4e9555f524f074a09ce96a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="association-set"></a><span data-ttu-id="39912-102">jeu d'associations</span><span class="sxs-lookup"><span data-stu-id="39912-102">association set</span></span>
<span data-ttu-id="39912-103">Un *ensemble d’associations* est un conteneur logique pour [association](../../../../docs/framework/data/adonet/association-type.md) instances du même type.</span><span class="sxs-lookup"><span data-stu-id="39912-103">An *association set* is a logical container for [association](../../../../docs/framework/data/adonet/association-type.md) instances of the same type.</span></span> <span data-ttu-id="39912-104">Un ensemble d'associations n'est pas une construction de modélisation des données ; autrement dit, il ne décrit ni la structure de données ni les relations.</span><span class="sxs-lookup"><span data-stu-id="39912-104">An association set is not a data modeling construct; that is, it does not describe the structure of data or relationships.</span></span> <span data-ttu-id="39912-105">Au lieu de cela, un ensemble d'associations fournit une construction pour un environnement d'hébergement ou de stockage (tel que le Common Language Runtime ou une base de données SQL Server) pour regrouper des instances d'association afin qu'elles puissent être mappées à un magasin de données.</span><span class="sxs-lookup"><span data-stu-id="39912-105">Instead, an association set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group association instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="39912-106">Un ensemble d’associations est défini dans un [conteneur d’entités](../../../../docs/framework/data/adonet/entity-container.md), qui est un regroupement logique de [jeux d’entités](../../../../docs/framework/data/adonet/entity-set.md) et ensembles d’associations.</span><span class="sxs-lookup"><span data-stu-id="39912-106">An association set is defined within an [entity container](../../../../docs/framework/data/adonet/entity-container.md), which is a logical grouping of [entity sets](../../../../docs/framework/data/adonet/entity-set.md) and association sets.</span></span>  
  
 <span data-ttu-id="39912-107">Une définition d'ensemble d'associations contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="39912-107">A definition for an association set contains the following information:</span></span>  
  
-   <span data-ttu-id="39912-108">Nom de l'ensemble d'associations.</span><span class="sxs-lookup"><span data-stu-id="39912-108">The association set name.</span></span> <span data-ttu-id="39912-109">(Requis)</span><span class="sxs-lookup"><span data-stu-id="39912-109">(Required)</span></span>  
  
-   <span data-ttu-id="39912-110">Association dont l'ensemble d'associations contient des instances.</span><span class="sxs-lookup"><span data-stu-id="39912-110">The association of which it will contain instances.</span></span> <span data-ttu-id="39912-111">(Requis)</span><span class="sxs-lookup"><span data-stu-id="39912-111">(Required)</span></span>  
  
-   <span data-ttu-id="39912-112">Deux [terminaisons d’ensemble d’associations](../../../../docs/framework/data/adonet/association-set-end.md).</span><span class="sxs-lookup"><span data-stu-id="39912-112">Two [association set ends](../../../../docs/framework/data/adonet/association-set-end.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="39912-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="39912-113">Example</span></span>  
 <span data-ttu-id="39912-114">Le diagramme suivant montre un modèle conceptuel avec deux associations : `PublishedBy` et `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="39912-114">The diagram below shows a conceptual model with two associations: `PublishedBy`, and `WrittenBy`.</span></span> <span data-ttu-id="39912-115">Bien que les informations sur les ensembles d'associations ne soient pas transmises au diagramme, le diagramme suivant montre un exemple d'ensembles d'associations et de jeux d'entités basés sur ce modèle.</span><span class="sxs-lookup"><span data-stu-id="39912-115">Although information about association sets is not conveyed in the diagram, the next diagram shows an example of association sets and entity sets based on this model.</span></span>  
  
 <span data-ttu-id="39912-116">![Exemple de modèle](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="39912-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="39912-117">L'exemple suivant montre un ensemble d'associations (`PublishedBy`) et deux jeux d'entités (`Books` et `Publishers`) basés sur le modèle conceptuel présenté ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="39912-117">The following example shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="39912-118">BI dans le `Books` jeu d’entités représente une instance de la `Book` type d’entité en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="39912-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="39912-119">De même, Pj représente un `Publisher` d’instance dans le `Publishers` jeu d’entités.</span><span class="sxs-lookup"><span data-stu-id="39912-119">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="39912-120">BiPj représente une instance de la `PublishedBy` association dans le `PublishedBy` ensemble d’associations.</span><span class="sxs-lookup"><span data-stu-id="39912-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 <span data-ttu-id="39912-121">![Définit l’exemple](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span><span class="sxs-lookup"><span data-stu-id="39912-121">![Sets Example](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span></span>  
  
 <span data-ttu-id="39912-122">Le [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="39912-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="39912-123">Le CSDL suivant définit un conteneur d'entités avec un ensemble d'associations pour chaque association dans le diagramme ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="39912-123">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="39912-124">Notez que le nom et l'association pour chaque ensemble d'associations sont définis à l'aide d'attributs XML.</span><span class="sxs-lookup"><span data-stu-id="39912-124">Note that the name and association for each association set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="39912-125">Il est possible de définir plusieurs ensembles d’associations par association, tant qu’aucune deux ensembles d’associations une [ensemble d’associations](../../../../docs/framework/data/adonet/association-set-end.md).</span><span class="sxs-lookup"><span data-stu-id="39912-125">It is possible to define multiple association sets per association, as long as no two association sets share an [association set end](../../../../docs/framework/data/adonet/association-set-end.md).</span></span> <span data-ttu-id="39912-126">Le CSDL suivant définit un conteneur d'entités avec deux ensembles d'associations pour l'association `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="39912-126">The following CSDL defines an entity container with two association sets for the `WrittenBy` association.</span></span> <span data-ttu-id="39912-127">Notez que plusieurs jeux d'entités ont été définis pour les types d'entité `Book` et `Author`, et qu'aucun ensemble d'associations ne partage une terminaison d'ensemble d'associations.</span><span class="sxs-lookup"><span data-stu-id="39912-127">Notice that multiple entity sets have been defined for the `Book` and `Author` entity types and that no association set shares an association set end.</span></span>  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a><span data-ttu-id="39912-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39912-128">See Also</span></span>  
 [<span data-ttu-id="39912-129">Concepts clés d’Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="39912-129">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="39912-130">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="39912-130">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [<span data-ttu-id="39912-131">propriété de clé étrangère</span><span class="sxs-lookup"><span data-stu-id="39912-131">foreign key property</span></span>](../../../../docs/framework/data/adonet/foreign-key-property.md)
