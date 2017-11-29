---
title: "Comment : personnaliser des classes d'entité à l'aide de l'éditeur de code"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec28332f-9f3c-4e0a-baca-60f9141a68c0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d5586e28e784c43488245db814abf32d863232fc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-customize-entity-classes-by-using-the-code-editor"></a><span data-ttu-id="401bd-102">Comment : personnaliser des classes d'entité à l'aide de l'éditeur de code</span><span class="sxs-lookup"><span data-stu-id="401bd-102">How to: Customize Entity Classes by Using the Code Editor</span></span>
<span data-ttu-id="401bd-103">Les développeurs qui utilisent [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] peuvent créer ou personnaliser leurs classes d'entité à l'aide du [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="401bd-103">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create or customize their entity classes.</span></span>  
  
 <span data-ttu-id="401bd-104">Vous pouvez également utiliser l'éditeur de code [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)] pour écrire votre propre code de mappage ou personnaliser du code qui a déjà été généré.</span><span class="sxs-lookup"><span data-stu-id="401bd-104">You can also use the [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)] code editor to write your own mapping code or to customize code that has already been generated.</span></span> <span data-ttu-id="401bd-105">Pour plus d’informations, consultez [mappage basé sur l’attribut](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="401bd-105">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
 <span data-ttu-id="401bd-106">Les rubriques de cette section décrivent comment personnaliser votre modèle objet.</span><span class="sxs-lookup"><span data-stu-id="401bd-106">The topics in this section describe how to customize your object model.</span></span>  
  
 [<span data-ttu-id="401bd-107">Comment : spécifier des noms de base de données</span><span class="sxs-lookup"><span data-stu-id="401bd-107">How to: Specify Database Names</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-names.md)  
 <span data-ttu-id="401bd-108">Explique comment utiliser <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="401bd-108">Describes how to use <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
 [<span data-ttu-id="401bd-109">Comment : représenter des Tables en tant que Classes</span><span class="sxs-lookup"><span data-stu-id="401bd-109">How to: Represent Tables as Classes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-tables-as-classes.md)  
 <span data-ttu-id="401bd-110">Explique comment utiliser <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="401bd-110">Describes how to use <xref:System.Data.Linq.Mapping.TableAttribute>.</span></span>  
  
 [<span data-ttu-id="401bd-111">Comment : représenter des colonnes en tant que membres de classe</span><span class="sxs-lookup"><span data-stu-id="401bd-111">How to: Represent Columns as Class Members</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-class-members.md)  
 <span data-ttu-id="401bd-112">Explique comment utiliser <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="401bd-112">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span></span>  
  
 [<span data-ttu-id="401bd-113">Comment : représenter les clés primaires</span><span class="sxs-lookup"><span data-stu-id="401bd-113">How to: Represent Primary Keys</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-primary-keys.md)  
 <span data-ttu-id="401bd-114">Explique comment utiliser <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="401bd-114">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
 [<span data-ttu-id="401bd-115">Comment : mapper des relations de base de données</span><span class="sxs-lookup"><span data-stu-id="401bd-115">How to: Map Database Relationships</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md)  
 <span data-ttu-id="401bd-116">Fournit des exemples d'utilisation de l'attribut <xref:System.Data.Linq.Mapping.AssociationAttribute>.</span><span class="sxs-lookup"><span data-stu-id="401bd-116">Provides examples of using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span>  
  
 [<span data-ttu-id="401bd-117">Comment : représenter des colonnes en tant que la base de données générée</span><span class="sxs-lookup"><span data-stu-id="401bd-117">How to: Represent Columns as Database-Generated</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-database-generated.md)  
 <span data-ttu-id="401bd-118">Explique comment utiliser <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="401bd-118">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
 [<span data-ttu-id="401bd-119">Comment : représenter des colonnes en tant que colonnes Timestamp ou Version</span><span class="sxs-lookup"><span data-stu-id="401bd-119">How to: Represent Columns as Timestamp or Version Columns</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-timestamp-or-version-columns.md)  
 <span data-ttu-id="401bd-120">Explique comment utiliser <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="401bd-120">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 [<span data-ttu-id="401bd-121">Comment : spécifier les Types de données de base de données</span><span class="sxs-lookup"><span data-stu-id="401bd-121">How to: Specify Database Data Types</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-data-types.md)  
 <span data-ttu-id="401bd-122">Explique comment utiliser <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="401bd-122">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
 [<span data-ttu-id="401bd-123">Comment : représenter des colonnes calculées</span><span class="sxs-lookup"><span data-stu-id="401bd-123">How to: Represent Computed Columns</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-computed-columns.md)  
 <span data-ttu-id="401bd-124">Explique comment utiliser <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="401bd-124">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
 [<span data-ttu-id="401bd-125">Comment : spécifier des champs de stockage privés</span><span class="sxs-lookup"><span data-stu-id="401bd-125">How to: Specify Private Storage Fields</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-private-storage-fields.md)  
 <span data-ttu-id="401bd-126">Explique comment utiliser <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span><span class="sxs-lookup"><span data-stu-id="401bd-126">Describes how to use <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
 [<span data-ttu-id="401bd-127">Comment : représenter des colonnes comme autorisant les valeurs Null</span><span class="sxs-lookup"><span data-stu-id="401bd-127">How to: Represent Columns as Allowing Null Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-allowing-null-values.md)  
 <span data-ttu-id="401bd-128">Explique comment utiliser <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="401bd-128">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
 [<span data-ttu-id="401bd-129">Comment : mapper des hiérarchies d’héritage</span><span class="sxs-lookup"><span data-stu-id="401bd-129">How to: Map Inheritance Hierarchies</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md)  
 <span data-ttu-id="401bd-130">Décrit les mappages requis pour spécifier une hiérarchie d'héritage.</span><span class="sxs-lookup"><span data-stu-id="401bd-130">Describes the mappings required to specify an inheritance hierarchy.</span></span>  
  
 [<span data-ttu-id="401bd-131">Comment : spécifier la vérification de conflits d’accès concurrentiel</span><span class="sxs-lookup"><span data-stu-id="401bd-131">How to: Specify Concurrency-Conflict Checking</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-concurrency-conflict-checking.md)  
 <span data-ttu-id="401bd-132">Explique comment utiliser <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="401bd-132">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="401bd-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="401bd-133">See Also</span></span>  
 [<span data-ttu-id="401bd-134">SqlMetal.exe (outil de génération de code)</span><span class="sxs-lookup"><span data-stu-id="401bd-134">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
