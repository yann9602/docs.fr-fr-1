---
title: "IMetaDataEmit::MergeEnd, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.MergeEnd
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 265fc007b5817e8dffd5846738a7a0003bbddf9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitmergeend-method"></a><span data-ttu-id="d3836-102">IMetaDataEmit::MergeEnd, méthode</span><span class="sxs-lookup"><span data-stu-id="d3836-102">IMetaDataEmit::MergeEnd Method</span></span>
<span data-ttu-id="d3836-103">Fusionne dans la portée actuelle toutes les portées de métadonnées spécifiées par un ou plusieurs appels précédents à [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).</span><span class="sxs-lookup"><span data-stu-id="d3836-103">Merges into the current scope all the metadata scopes specified by one or more prior calls to [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3836-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3836-104">Syntax</span></span>  
  
```  
HRESULT MergeEnd ();  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3836-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d3836-105">Parameters</span></span>  
 <span data-ttu-id="d3836-106">Cette méthode ne prend aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="d3836-106">This method takes no parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3836-107">Notes</span><span class="sxs-lookup"><span data-stu-id="d3836-107">Remarks</span></span>  
 <span data-ttu-id="d3836-108">Cette routine déclenche la fusion réelle des métadonnées, de toutes les portées spécifiées en faisant précéder les appels à d’importation `IMetaDataEmit::Merge`, dans la portée actuelle de la sortie.</span><span class="sxs-lookup"><span data-stu-id="d3836-108">This routine triggers the actual merge of metadata, of all import scopes specified by preceding calls to `IMetaDataEmit::Merge`, into the current output scope.</span></span>  
  
 <span data-ttu-id="d3836-109">Les conditions spéciales suivantes s’appliquent à la fusion :</span><span class="sxs-lookup"><span data-stu-id="d3836-109">The following special conditions apply to the merge:</span></span>  
  
-   <span data-ttu-id="d3836-110">Identificateur de version de module (MVID) n’est jamais importé, car il est propre aux métadonnées dans la portée d’importation.</span><span class="sxs-lookup"><span data-stu-id="d3836-110">A module version identifier (MVID) is never imported, because it is unique to the metadata in the import scope.</span></span>  
  
-   <span data-ttu-id="d3836-111">Aucune propriété de module existante n’est remplacée.</span><span class="sxs-lookup"><span data-stu-id="d3836-111">No existing module-wide properties are overwritten.</span></span>  
  
     <span data-ttu-id="d3836-112">Si les propriétés du module ont été déjà définies pour l’étendue actuelle, aucune propriété de module n’est importées.</span><span class="sxs-lookup"><span data-stu-id="d3836-112">If module properties were already set for the current scope, no module properties are imported.</span></span> <span data-ttu-id="d3836-113">Toutefois, si les propriétés de module n’ont pas été définies dans la portée actuelle, ils sont importés qu’une seule fois, quand ils sont tout d’abord rencontrés.</span><span class="sxs-lookup"><span data-stu-id="d3836-113">However, if module properties have not been set in the current scope, they are imported only once, when they are first encountered.</span></span> <span data-ttu-id="d3836-114">Si ces propriétés de module sont de nouveau rencontrées, ils sont des doublons.</span><span class="sxs-lookup"><span data-stu-id="d3836-114">If those module properties are encountered again, they are duplicates.</span></span> <span data-ttu-id="d3836-115">Si les valeurs de toutes les propriétés de module (sauf MVID) sont comparées et aucun doublon n’est trouvé, une erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="d3836-115">If the values of all module properties (except MVID) are compared and no duplicates are found, an error is raised.</span></span>  
  
-   <span data-ttu-id="d3836-116">Pour les définitions de type (`TypeDef`), sans doublons sont fusionnées dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="d3836-116">For type definitions (`TypeDef`), no duplicates are merged into the current scope.</span></span> <span data-ttu-id="d3836-117">`TypeDef`vérifie les doublons sur chacun des objets *nom d’objet complet* + *GUID* + *numéro de version*.</span><span class="sxs-lookup"><span data-stu-id="d3836-117">`TypeDef` objects are checked for duplicates against each *fully-qualified object name* + *GUID* + *version number*.</span></span> <span data-ttu-id="d3836-118">S’il existe une correspondance sur le nom ou le GUID et l’une des deux autres éléments est différent, une erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="d3836-118">If there is a match on either name or GUID, and any of the other two elements is different, an error is raised.</span></span> <span data-ttu-id="d3836-119">Sinon, si les trois éléments correspondent, `MergeEnd` effectue une vérification rapide pour vérifier que les entrées sont des doublons ; sinon, une erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="d3836-119">Otherwise, if all three items match, `MergeEnd` does a cursory check to ensure the entries are indeed duplicates; if not, an error is raised.</span></span> <span data-ttu-id="d3836-120">Cette vérification rapide recherche :</span><span class="sxs-lookup"><span data-stu-id="d3836-120">This cursory check looks for:</span></span>  
  
    -   <span data-ttu-id="d3836-121">Les mêmes déclarations de membre, qui se produisent dans le même ordre.</span><span class="sxs-lookup"><span data-stu-id="d3836-121">The same member declarations, occurring in the same order.</span></span> <span data-ttu-id="d3836-122">Les membres qui sont signalés en tant que `mdPrivateScope` (consultez la [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) énumération) ne sont pas inclus dans ce contrôle ; ils sont fusionnés spécialement.</span><span class="sxs-lookup"><span data-stu-id="d3836-122">Members that are flagged as `mdPrivateScope` (see the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration) are not included in this check; they are merged specially.</span></span>  
  
    -   <span data-ttu-id="d3836-123">La même disposition de classe.</span><span class="sxs-lookup"><span data-stu-id="d3836-123">The same class layout.</span></span>  
  
     <span data-ttu-id="d3836-124">Cela signifie qu’un `TypeDef` objet doit toujours être complète et cohérente défini dans chaque portée de métadonnées dans laquelle elle est déclarée ; si ses implémentations de membres (pour une classe) sont réparties sur plusieurs unités de compilation, la définition complète est censée pour être dans chaque portée et incrémentielle pour chaque étendue.</span><span class="sxs-lookup"><span data-stu-id="d3836-124">This means that a `TypeDef` object must always be fully and consistently defined in every metadata scope in which it is declared; if its member implementations (for a class) are spread across multiple compilation units, the full definition is assumed to be present in every scope and not incremental to each scope.</span></span> <span data-ttu-id="d3836-125">Par exemple, si les noms de paramètres sont pertinents pour le contrat, ils doivent être émis la même manière dans chaque portée ; Si elles ne sont pas pertinentes, ils ne doivent pas être émis dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d3836-125">For example, if parameter names are relevant to the contract, they must be emitted the same way into every scope; if they are not relevant, they should not be emitted into metadata.</span></span>  
  
     <span data-ttu-id="d3836-126">L’exception est qu’un `TypeDef` objet peut avoir des membres incrémentiels signalés comme `mdPrivateScope`.</span><span class="sxs-lookup"><span data-stu-id="d3836-126">The exception is that a `TypeDef` object can have incremental members flagged as `mdPrivateScope`.</span></span> <span data-ttu-id="d3836-127">Lorsqu’il les rencontre, `MergeEnd` les ajoute de façon incrémentielle à l’étendue actuelle sans tenir compte des doublons.</span><span class="sxs-lookup"><span data-stu-id="d3836-127">On encountering these, `MergeEnd` incrementally adds them to the current scope without regard for duplicates.</span></span> <span data-ttu-id="d3836-128">Étant donné que le compilateur comprend la portée privée, le compilateur doit être responsable de l’application de règles.</span><span class="sxs-lookup"><span data-stu-id="d3836-128">Because the compiler understands the private scope, the compiler must be responsible for enforcing rules.</span></span>  
  
-   <span data-ttu-id="d3836-129">Les adresses virtuelles relatives (RVA) ne sont pas importées ou fusionnées ; le compilateur doit émettre de nouveau ces informations.</span><span class="sxs-lookup"><span data-stu-id="d3836-129">Relative virtual addresses (RVAs) are not imported or merged; the compiler is expected to re-emit this information.</span></span>  
  
-   <span data-ttu-id="d3836-130">Attributs personnalisés sont fusionnés uniquement lorsque l’élément auquel ils sont associés est fusionné.</span><span class="sxs-lookup"><span data-stu-id="d3836-130">Custom attributes are merged only when the item to which they are attached is merged.</span></span> <span data-ttu-id="d3836-131">Par exemple, les attributs personnalisés associés à une classe sont fusionnées lors de la classe est rencontrée pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="d3836-131">For example, custom attributes associated with a class are merged when the class is first encountered.</span></span> <span data-ttu-id="d3836-132">Si les attributs personnalisés sont associés un `TypeDef` ou `MemberDef` qui est spécifique à l’unité de compilation (par exemple, l’horodatage d’une compilation membre), ils ne sont pas fusionnées et il incombe au compilateur de les supprimer ou mettre à jour ces métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d3836-132">If custom attributes are associated with a `TypeDef` or `MemberDef` that is specific to the compilation unit (such as the time stamp of a member compile), they are not merged and it is up to the compiler to remove or update such metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3836-133">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d3836-133">Requirements</span></span>  
 <span data-ttu-id="d3836-134">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3836-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3836-135">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d3836-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d3836-136">**Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d3836-136">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3836-137">**Versions du .NET framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3836-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3836-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3836-138">See Also</span></span>  
 [<span data-ttu-id="d3836-139">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="d3836-139">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="d3836-140">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="d3836-140">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
