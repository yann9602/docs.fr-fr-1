---
title: "CorGenericParamAttr, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorGenericParamAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorGenericParamAttr
helpviewer_keywords: CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e40613d790baed5bd89bee1e1f5ca57043bfe76a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="10d05-102">CorGenericParamAttr, énumération</span><span class="sxs-lookup"><span data-stu-id="10d05-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="10d05-103">Contient des valeurs qui décrivent le <xref:System.Type> paramètres pour les types génériques, comme utilisés lors d’appels à [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="10d05-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10d05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10d05-104">Syntax</span></span>  
  
```  
typedef enum CorGenericParamAttr {  
  
    gpVarianceMask                     =   0x0003,  
    gpNonVariant                       =   0x0000,   
    gpCovariant                        =   0x0001,  
    gpContravariant                    =   0x0002,  
  
    gpSpecialConstraintMask            =   0x001C,  
    gpNoSpecialConstraint              =   0x0000,  
    gpReferenceTypeConstraint          =   0x0004,   
    gpNotNullableValueTypeConstraint   =   0x0008,  
    gpDefaultConstructorConstraint     =   0x0010  
  
} CorGenericParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="10d05-105">Membres</span><span class="sxs-lookup"><span data-stu-id="10d05-105">Members</span></span>  
  
|<span data-ttu-id="10d05-106">Membre</span><span class="sxs-lookup"><span data-stu-id="10d05-106">Member</span></span>|<span data-ttu-id="10d05-107">Description</span><span class="sxs-lookup"><span data-stu-id="10d05-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="10d05-108">Variance du paramètre s’applique uniquement aux paramètres génériques pour les interfaces et délégués.</span><span class="sxs-lookup"><span data-stu-id="10d05-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="10d05-109">Indique l’absence de variation.</span><span class="sxs-lookup"><span data-stu-id="10d05-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="10d05-110">Indique la covariance.</span><span class="sxs-lookup"><span data-stu-id="10d05-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="10d05-111">Indique la contravariance.</span><span class="sxs-lookup"><span data-stu-id="10d05-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="10d05-112">Les contraintes spéciales peuvent s’appliquer à tout <xref:System.Type> paramètre.</span><span class="sxs-lookup"><span data-stu-id="10d05-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="10d05-113">Indique qu’aucune contrainte s’applique à la <xref:System.Type> paramètre.</span><span class="sxs-lookup"><span data-stu-id="10d05-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="10d05-114">Indique que le <xref:System.Type> paramètre doit être un type référence.</span><span class="sxs-lookup"><span data-stu-id="10d05-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="10d05-115">Indique que le <xref:System.Type> paramètre doit être un type valeur qui ne peut pas être une valeur null.</span><span class="sxs-lookup"><span data-stu-id="10d05-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="10d05-116">Indique que le <xref:System.Type> paramètre doit avoir un constructeur public par défaut qui ne prend aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="10d05-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="10d05-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="10d05-117">Requirements</span></span>  
 <span data-ttu-id="10d05-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10d05-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10d05-119">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="10d05-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="10d05-120">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10d05-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10d05-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10d05-121">See Also</span></span>  
 [<span data-ttu-id="10d05-122">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="10d05-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
