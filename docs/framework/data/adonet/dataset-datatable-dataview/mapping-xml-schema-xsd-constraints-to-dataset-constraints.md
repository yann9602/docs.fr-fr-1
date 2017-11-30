---
title: "Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9ac8e64c02d96450d41233cfbe65e1db839df9e7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="d4f7e-102">Mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="d4f7e-102">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="d4f7e-103">Le langage XSD (XML Schema Definition) permet la spécification de contraintes sur les éléments et attributs qu'il définit.</span><span class="sxs-lookup"><span data-stu-id="d4f7e-103">The XML Schema definition language (XSD) allows constraints to be specified on the elements and attributes it defines.</span></span> <span data-ttu-id="d4f7e-104">Lors du mappage d’un schéma XML au schéma relationnel d’un <xref:System.Data.DataSet>, contraintes de schéma XML sont mappées aux contraintes relationnelles appropriées sur les tables et colonnes dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="d4f7e-104">When mapping an XML Schema to relational schema in a <xref:System.Data.DataSet>, XML Schema constraints are mapped to appropriate relational constraints on the tables and columns within the **DataSet**.</span></span>  
  
 <span data-ttu-id="d4f7e-105">Cette section présente le mappage des contraintes de schéma XML suivantes :</span><span class="sxs-lookup"><span data-stu-id="d4f7e-105">This section discusses the mapping of the following XML Schema constraints:</span></span>  
  
-   <span data-ttu-id="d4f7e-106">Contrainte unique spécifiée à l’aide de la **unique** élément.</span><span class="sxs-lookup"><span data-stu-id="d4f7e-106">The uniqueness constraint specified using the **unique** element.</span></span>  
  
-   <span data-ttu-id="d4f7e-107">La contrainte de clé spécifiée à l’aide de la **clé** élément.</span><span class="sxs-lookup"><span data-stu-id="d4f7e-107">The key constraint specified using the **key** element.</span></span>  
  
-   <span data-ttu-id="d4f7e-108">La contrainte keyref spécifiée à l’aide de la **keyref** élément.</span><span class="sxs-lookup"><span data-stu-id="d4f7e-108">The keyref constraint specified using the **keyref** element.</span></span>  
  
 <span data-ttu-id="d4f7e-109">En utilisant une contrainte sur un élément ou un attribut, vous spécifiez certaines restrictions sur les valeurs de l'élément dans toute instance du document.</span><span class="sxs-lookup"><span data-stu-id="d4f7e-109">By using a constraint on an element or attribute, you specify certain restrictions on the values of the element in any instance of the document.</span></span> <span data-ttu-id="d4f7e-110">Par exemple, une contrainte de clé sur un **CustomerID** élément enfant d’un **client** élément dans le schéma indique que les valeurs de la **CustomerID** élément enfant doit être unique dans toute instance du document, et que les valeurs null ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="d4f7e-110">For example, a key constraint on a **CustomerID** child element of a **Customer** element in the schema indicates that the values of the **CustomerID** child element must be unique in any document instance, and that null values are not allowed.</span></span>  
  
 <span data-ttu-id="d4f7e-111">Des contraintes peuvent également être spécifiées entre les éléments et les attributs figurant dans un document afin d'établir une relation dans ce document.</span><span class="sxs-lookup"><span data-stu-id="d4f7e-111">Constraints can also be specified between elements and attributes in a document, in order to establish a relationship within the document.</span></span> <span data-ttu-id="d4f7e-112">Les contraintes key et keyref sont utilisées dans le schéma pour spécifier les contraintes au sein du document, créant ainsi une relation entre éléments et attributs du document.</span><span class="sxs-lookup"><span data-stu-id="d4f7e-112">The key and keyref constraints are used in the schema to specify the constraints within the document, resulting in a relationship between document elements and attributes.</span></span>  
  
 <span data-ttu-id="d4f7e-113">Le processus de mappage convertit ces contraintes de schéma en contraintes appropriées sur les tables créées dans le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="d4f7e-113">The mapping process converts these schema constraints into appropriate constraints on the tables created within the **DataSet**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d4f7e-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d4f7e-114">In This Section</span></span>  
 [<span data-ttu-id="d4f7e-115">Mapper des contraintes uniques de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="d4f7e-115">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="d4f7e-116">Décrit les éléments de schéma XML utilisés pour créer des contraintes uniques dans un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="d4f7e-116">Describes the XML Schema elements used to create unique constraints in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="d4f7e-117">Clé de mappage des contraintes de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="d4f7e-117">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="d4f7e-118">Décrit les éléments de schéma XML utilisés pour créer des contraintes de clé (contraintes uniques où les valeurs null ne sont pas autorisées) dans un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="d4f7e-118">Describes the XML Schema elements used to create key constraints (unique constraints where null values are not allowed) in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="d4f7e-119">Mapper keyref de schéma XML (XSD) aux contraintes de DataSet</span><span class="sxs-lookup"><span data-stu-id="d4f7e-119">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="d4f7e-120">Décrit les éléments de schéma XML utilisés pour créer des contraintes (clé étrangère) dans keyref un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="d4f7e-120">Describes the XML Schema elements used to create keyref (foreign key) constraints in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d4f7e-121">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="d4f7e-121">Related Sections</span></span>  
 [<span data-ttu-id="d4f7e-122">Structure relationnelle des DataSet qui dérivent de schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="d4f7e-122">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="d4f7e-123">Décrit la structure relationnelle, ou schéma, d’un **DataSet** qui est créé à partir du schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="d4f7e-123">Describes the relational structure, or schema, of a **DataSet** that is created from XSD schema.</span></span>  
  
 [<span data-ttu-id="d4f7e-124">Génération des Relations d’un DataSet à partir de schéma XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="d4f7e-124">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="d4f7e-125">Décrit les éléments de schéma XML utilisés pour créer des relations entre les colonnes de table dans un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="d4f7e-125">Describes the XML Schema elements used to create relations between table columns in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4f7e-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4f7e-126">See Also</span></span>  
 [<span data-ttu-id="d4f7e-127">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="d4f7e-127">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
