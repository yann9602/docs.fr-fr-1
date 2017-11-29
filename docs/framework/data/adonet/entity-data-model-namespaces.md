---
title: "Entity Data Model : espaces de noms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3e473453576f04e89b58806c5140e29855d7d022
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="entity-data-model-namespaces"></a><span data-ttu-id="79b2b-102">Entity Data Model : espaces de noms</span><span class="sxs-lookup"><span data-stu-id="79b2b-102">Entity Data Model: Namespaces</span></span>
<span data-ttu-id="79b2b-103">Un espace de noms dans le modèle EDM (Entity Data Model) est un conteneur abstrait pour [types d’entités](../../../../docs/framework/data/adonet/entity-type.md), [types complexes](../../../../docs/framework/data/adonet/complex-type.md), et [associations](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="79b2b-103">A namespace in the Entity Data Model (EDM) is an abstract container for [entity types](../../../../docs/framework/data/adonet/entity-type.md), [complex types](../../../../docs/framework/data/adonet/complex-type.md), and [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="79b2b-104">Les espaces de noms dans le modèle EDM sont semblables aux espaces de noms dans un langage de programmation : ils fournissent le contexte pour les objets qu'ils contiennent et offrent un moyen de lever l'ambiguïté entre les objets qui portent le même nom (mais qui sont contenus dans des espaces de noms différents).</span><span class="sxs-lookup"><span data-stu-id="79b2b-104">Namespaces in the EDM are similar to namespaces in a programming language: they provide context for the objects that they contain and they provide a way to disambiguate objects that have the same name (but are contained in different namespaces).</span></span>  
  
## <a name="example"></a><span data-ttu-id="79b2b-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="79b2b-105">Example</span></span>  
 <span data-ttu-id="79b2b-106">Le [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) utilise un langage spécifique à un domaine (DSL) appelé conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) pour définir des modèles conceptuels.</span><span class="sxs-lookup"><span data-stu-id="79b2b-106">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="79b2b-107">Le CSDL suivant utilise un espace de noms pour identifier un type défini dans un modèle conceptuel différent.</span><span class="sxs-lookup"><span data-stu-id="79b2b-107">The following CSDL code uses a namespace to identify a type that is defined in a different conceptual model.</span></span> <span data-ttu-id="79b2b-108">L'exemple définit un type d'entité (`Publisher`) qui a une propriété de type complexe (`Address`) importée à partir de l'espace de noms `ExtendedBooksModel`.</span><span class="sxs-lookup"><span data-stu-id="79b2b-108">The example defines an entity type (`Publisher`) that has a complex type property (`Address`) that is imported from the `ExtendedBooksModel` namespace.</span></span> <span data-ttu-id="79b2b-109">Notez que l'élément `Using` indique qu'un espace de noms a été importé.</span><span class="sxs-lookup"><span data-stu-id="79b2b-109">Note that the `Using` element indicates that a namespace has been imported.</span></span> <span data-ttu-id="79b2b-110">Notez également que le type de la propriété `Address` est défini à l'aide de son nom qualifié complet (`ExtendedBooksModel.Address`), ce qui indique que ce type est défini dans l'espace de noms `ExtendedBooksModel`.</span><span class="sxs-lookup"><span data-stu-id="79b2b-110">Also note that the type of the `Address` property is defined by using its fully qualified name (`ExtendedBooksModel.Address`), indicating that this type is defined in the `ExtendedBooksModel` namespace.</span></span>  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a><span data-ttu-id="79b2b-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79b2b-111">See Also</span></span>  
 [<span data-ttu-id="79b2b-112">Concepts clés du modèle de données Entity</span><span class="sxs-lookup"><span data-stu-id="79b2b-112">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="79b2b-113">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="79b2b-113">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
