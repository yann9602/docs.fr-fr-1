---
title: Entity Data Model
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 69b72a824e6f9468c9b3d86073243d506382e766
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="entity-data-model"></a><span data-ttu-id="eeee0-102">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="eeee0-102">Entity Data Model</span></span>
<span data-ttu-id="eeee0-103">Le modèle EDM (Entity Data Model) est un jeu de concepts qui décrivent la structure des données, indépendamment de la forme sous laquelle elles sont stockées.</span><span class="sxs-lookup"><span data-stu-id="eeee0-103">The Entity Data Model (EDM) is a set of concepts that describe the structure of data, regardless of its stored form.</span></span> <span data-ttu-id="eeee0-104">Inspiré du modèle entité-relation décrit par Peter Chen en 1976, le modèle EDM le complète et étend ses utilisations traditionnelles.</span><span class="sxs-lookup"><span data-stu-id="eeee0-104">The EDM borrows from the Entity-Relationship Model described by Peter Chen in 1976, but it also builds on the Entity-Relationship Model and extends its traditional uses.</span></span>  
  
 <span data-ttu-id="eeee0-105">Le modèle EDM aborde les difficultés qui se présentent lors du stockage de données sous plusieurs formes.</span><span class="sxs-lookup"><span data-stu-id="eeee0-105">The EDM addresses the challenges that arise from having data stored in many forms.</span></span> <span data-ttu-id="eeee0-106">Par exemple, prenons une entreprise qui stocke des données dans des bases de données relationnelles, des fichiers texte, des fichiers XML, des feuilles de calcul et des rapports.</span><span class="sxs-lookup"><span data-stu-id="eeee0-106">For example, consider a business that stores data in relational databases, text files, XML files, spreadsheets, and reports.</span></span> <span data-ttu-id="eeee0-107">Cette diversité pose des problèmes importants en termes de modélisation des données, de conception d'application et d'accès aux données.</span><span class="sxs-lookup"><span data-stu-id="eeee0-107">This presents significant challenges in data modeling, application design, and data access.</span></span> <span data-ttu-id="eeee0-108">Lors de la conception d'une application orientée données, l'écriture de code efficace et gérable sans nuire à l'efficacité de l'accès aux données, du stockage et de l'évolutivité relève du défi.</span><span class="sxs-lookup"><span data-stu-id="eeee0-108">When designing a data-oriented application, the challenge is to write efficient and maintainable code without sacrificing efficient data access, storage, and scalability.</span></span> <span data-ttu-id="eeee0-109">Lorsque les données ont une structure relationnelle, l'accès aux données, le stockage et l'évolutivité sont très efficaces, mais l'écriture de code efficace et gérable devient plus difficile.</span><span class="sxs-lookup"><span data-stu-id="eeee0-109">When data has a relational structure, data access, storage, and scalability are very efficient, but writing efficient and maintainable code becomes more difficult.</span></span> <span data-ttu-id="eeee0-110">Lorsque les données ont une structure objet, la tendance est inversée : l'écriture de code efficace et gérable vient au détriment de l'efficacité de l'accès aux données, du stockage et de l'évolutivité.</span><span class="sxs-lookup"><span data-stu-id="eeee0-110">When data has an object structure, the trade-offs are reversed: Writing efficient and maintainable code comes at the cost of efficient data access, storage, and scalability.</span></span> <span data-ttu-id="eeee0-111">Même s'il est possible de trouver un juste équilibre entre ces deux aspects, de nouvelles difficultés se présentent lorsque des données passent d'une forme à une autre.</span><span class="sxs-lookup"><span data-stu-id="eeee0-111">Even if the right balance between these trade-offs can be found, new challenges arise when data is moved from one form to another.</span></span> <span data-ttu-id="eeee0-112">Le modèle Entity Data Model aborde ces difficultés en décrivant la structure des données en termes d'entités et de relations qui sont indépendantes de tout schéma de stockage.</span><span class="sxs-lookup"><span data-stu-id="eeee0-112">The Entity Data Model addresses these challenges by describing the structure of data in terms of entities and relationships that are independent of any storage schema.</span></span> <span data-ttu-id="eeee0-113">La forme sous laquelle les données sont stockées n'a alors plus aucune incidence sur la conception et le développement de l'application.</span><span class="sxs-lookup"><span data-stu-id="eeee0-113">This makes the stored form of data irrelevant to application design and development.</span></span> <span data-ttu-id="eeee0-114">Par ailleurs, comme les entités et les relations décrivent la structure des données telles qu'elles sont utilisées dans une application (et non la forme sous laquelle elles sont stockées), elles peuvent évoluer parallèlement à une application.</span><span class="sxs-lookup"><span data-stu-id="eeee0-114">And, because entities and relationships describe the structure of data as it is used in an application (not its stored form), they can evolve as an application evolves.</span></span>  
  
 <span data-ttu-id="eeee0-115">Un `conceptual model` est une représentation spécifique de la structure des données sous forme d'entités et de relations. Il est en général défini dans un langage spécifique à un domaine (DSL) qui implémente les concepts du modèle EDM.</span><span class="sxs-lookup"><span data-stu-id="eeee0-115">A `conceptual model` is a specific representation of the structure of data as entities and relationships, and is generally defined in a domain-specific language (DSL) that implements the concepts of the EDM.</span></span> <span data-ttu-id="eeee0-116">[Langage de définition de schéma conceptuel (CSDL)](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) est un exemple d’un langage spécifique à un domaine.</span><span class="sxs-lookup"><span data-stu-id="eeee0-116">[Conceptual schema definition language (CSDL)](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) is an example of such a domain-specific language.</span></span> <span data-ttu-id="eeee0-117">Les entités et les relations décrites dans un modèle conceptuel peuvent être considérées comme des abstractions d'objets et d'associations dans une application.</span><span class="sxs-lookup"><span data-stu-id="eeee0-117">Entities and relationships described in a conceptual model can be thought of as abstractions of objects and associations in an application.</span></span> <span data-ttu-id="eeee0-118">Cela permet aux développeurs de se concentrer sur le modèle conceptuel sans se soucier du schéma de stockage, et d'écrire du code en favorisant son efficacité et sa maintenabilité.</span><span class="sxs-lookup"><span data-stu-id="eeee0-118">This allows developers to focus on the conceptual model without concern for the storage schema, and allows them to write code with efficiency and maintainability in mind.</span></span> <span data-ttu-id="eeee0-119">Pendant ce temps, les concepteurs de schémas de stockage peuvent se concentrer sur l'efficacité de l'accès aux données, du stockage et de l'évolutivité.</span><span class="sxs-lookup"><span data-stu-id="eeee0-119">Meanwhile storage schema designers can focus on the efficiency of data access, storage, and scalability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eeee0-120">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="eeee0-120">In This Section</span></span>  
 <span data-ttu-id="eeee0-121">Les rubriques de cette section décrivent les concepts du modèle EDM.</span><span class="sxs-lookup"><span data-stu-id="eeee0-121">Topics in this section describe the concepts of the Entity Data Model.</span></span> <span data-ttu-id="eeee0-122">Tout langage DSL qui implémente le modèle EDM doit inclure les concepts décrits ici.</span><span class="sxs-lookup"><span data-stu-id="eeee0-122">Any DSL that implements the EDM should include the concepts described here.</span></span> <span data-ttu-id="eeee0-123">Notez que la [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise le langage CSDL pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="eeee0-123">Note that the [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses CSDL to define conceptual models.</span></span> <span data-ttu-id="eeee0-124">Pour plus d’informations, consultez [spécification CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).</span><span class="sxs-lookup"><span data-stu-id="eeee0-124">For more information, see [CSDL Specification](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).</span></span>  
  
 [<span data-ttu-id="eeee0-125">Concepts clés du modèle de données Entity</span><span class="sxs-lookup"><span data-stu-id="eeee0-125">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
  
 [<span data-ttu-id="eeee0-126">Entity Data Model : espaces de noms</span><span class="sxs-lookup"><span data-stu-id="eeee0-126">Entity Data Model: Namespaces</span></span>](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)  
  
 [<span data-ttu-id="eeee0-127">Entity Data Model : Types de données primitifs</span><span class="sxs-lookup"><span data-stu-id="eeee0-127">Entity Data Model: Primitive Data Types</span></span>](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)  
  
 [<span data-ttu-id="eeee0-128">Entity Data Model : héritage</span><span class="sxs-lookup"><span data-stu-id="eeee0-128">Entity Data Model: Inheritance</span></span>](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)  
  
 [<span data-ttu-id="eeee0-129">terminaison d’association</span><span class="sxs-lookup"><span data-stu-id="eeee0-129">association end</span></span>](../../../../docs/framework/data/adonet/association-end.md)  
  
 [<span data-ttu-id="eeee0-130">multiplicité de terminaison d’association</span><span class="sxs-lookup"><span data-stu-id="eeee0-130">association end multiplicity</span></span>](../../../../docs/framework/data/adonet/association-end-multiplicity.md)  
  
 [<span data-ttu-id="eeee0-131">ensemble d’associations</span><span class="sxs-lookup"><span data-stu-id="eeee0-131">association set</span></span>](../../../../docs/framework/data/adonet/association-set.md)  
  
 [<span data-ttu-id="eeee0-132">ensemble d’associations</span><span class="sxs-lookup"><span data-stu-id="eeee0-132">association set end</span></span>](../../../../docs/framework/data/adonet/association-set-end.md)  
  
 [<span data-ttu-id="eeee0-133">type d’association</span><span class="sxs-lookup"><span data-stu-id="eeee0-133">association type</span></span>](../../../../docs/framework/data/adonet/association-type.md)  
  
 [<span data-ttu-id="eeee0-134">type complexe</span><span class="sxs-lookup"><span data-stu-id="eeee0-134">complex type</span></span>](../../../../docs/framework/data/adonet/complex-type.md)  
  
 [<span data-ttu-id="eeee0-135">conteneur d’entités</span><span class="sxs-lookup"><span data-stu-id="eeee0-135">entity container</span></span>](../../../../docs/framework/data/adonet/entity-container.md)  
  
 [<span data-ttu-id="eeee0-136">clé d’entité</span><span class="sxs-lookup"><span data-stu-id="eeee0-136">entity key</span></span>](../../../../docs/framework/data/adonet/entity-key.md)  
  
 [<span data-ttu-id="eeee0-137">jeu d’entités</span><span class="sxs-lookup"><span data-stu-id="eeee0-137">entity set</span></span>](../../../../docs/framework/data/adonet/entity-set.md)  
  
 [<span data-ttu-id="eeee0-138">type d’entité</span><span class="sxs-lookup"><span data-stu-id="eeee0-138">entity type</span></span>](../../../../docs/framework/data/adonet/entity-type.md)  
  
 [<span data-ttu-id="eeee0-139">facet</span><span class="sxs-lookup"><span data-stu-id="eeee0-139">facet</span></span>](../../../../docs/framework/data/adonet/facet.md)  
  
 [<span data-ttu-id="eeee0-140">propriété de clé étrangère</span><span class="sxs-lookup"><span data-stu-id="eeee0-140">foreign key property</span></span>](../../../../docs/framework/data/adonet/foreign-key-property.md)  
  
 [<span data-ttu-id="eeee0-141">fonction déclarée par modèle</span><span class="sxs-lookup"><span data-stu-id="eeee0-141">model-declared function</span></span>](../../../../docs/framework/data/adonet/model-declared-function.md)  
  
 [<span data-ttu-id="eeee0-142">fonction définie par modèle</span><span class="sxs-lookup"><span data-stu-id="eeee0-142">model-defined function</span></span>](../../../../docs/framework/data/adonet/model-defined-function.md)  
  
 [<span data-ttu-id="eeee0-143">propriété de navigation</span><span class="sxs-lookup"><span data-stu-id="eeee0-143">navigation property</span></span>](../../../../docs/framework/data/adonet/navigation-property.md)  
  
 [<span data-ttu-id="eeee0-144">propriété</span><span class="sxs-lookup"><span data-stu-id="eeee0-144">property</span></span>](../../../../docs/framework/data/adonet/property.md)  
  
 [<span data-ttu-id="eeee0-145">contrainte d’intégrité référentielle</span><span class="sxs-lookup"><span data-stu-id="eeee0-145">referential integrity constraint</span></span>](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)  
  
## <a name="see-also"></a><span data-ttu-id="eeee0-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eeee0-146">See Also</span></span>  
 [<span data-ttu-id="eeee0-147">Outils ADO.NET Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="eeee0-147">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [<span data-ttu-id="eeee0-148">vue d’ensemble du fichier .edmx</span><span class="sxs-lookup"><span data-stu-id="eeee0-148">.edmx File Overview</span></span>](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="eeee0-149">Spécification CSDL</span><span class="sxs-lookup"><span data-stu-id="eeee0-149">CSDL Specification</span></span>](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)
