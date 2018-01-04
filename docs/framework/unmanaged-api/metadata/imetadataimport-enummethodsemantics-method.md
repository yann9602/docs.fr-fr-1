---
title: "IMetaDataImport::EnumMethodSemantics, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMethodSemantics
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 883505076fa9ff4f335c08b069e801ebda1ebb2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="b8e5a-102">IMetaDataImport::EnumMethodSemantics, méthode</span><span class="sxs-lookup"><span data-stu-id="b8e5a-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="b8e5a-103">Énumère les propriétés et les événements de modification de propriétés auxquels la méthode spécifiée est associée.</span><span class="sxs-lookup"><span data-stu-id="b8e5a-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8e5a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8e5a-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,   
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b8e5a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b8e5a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b8e5a-106">[dans, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="b8e5a-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b8e5a-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="b8e5a-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="b8e5a-108">[in] Jeton MethodDef qui limite l’étendue de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="b8e5a-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="b8e5a-109">[out] Tableau utilisé pour stocker les événements ou les propriétés.</span><span class="sxs-lookup"><span data-stu-id="b8e5a-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b8e5a-110">[in] Taille maximale du tableau `rEventProp`.</span><span class="sxs-lookup"><span data-stu-id="b8e5a-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="b8e5a-111">[out] Le nombre d’événements ou de propriétés retourné dans `rEventProp`.</span><span class="sxs-lookup"><span data-stu-id="b8e5a-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8e5a-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b8e5a-112">Return Value</span></span>  
  
|<span data-ttu-id="b8e5a-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b8e5a-113">HRESULT</span></span>|<span data-ttu-id="b8e5a-114">Description</span><span class="sxs-lookup"><span data-stu-id="b8e5a-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b8e5a-115">`EnumMethodSemantics`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="b8e5a-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b8e5a-116">Il n’existe aucun événement ou les propriétés à énumérer.</span><span class="sxs-lookup"><span data-stu-id="b8e5a-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="b8e5a-117">Dans ce cas, `pcEventProp` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="b8e5a-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8e5a-118">Notes</span><span class="sxs-lookup"><span data-stu-id="b8e5a-118">Remarks</span></span>  
 <span data-ttu-id="b8e5a-119">Définissent de nombreux types common language runtime *propriété* `Changed` événements et `On` *propriété* `Changed` méthodes associées à leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="b8e5a-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="b8e5a-120">Par exemple, le <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type définit un <xref:System.Windows.Forms.Control.Font%2A> propriété, un <xref:System.Windows.Forms.Control.FontChanged> événement et un <xref:System.Windows.Forms.Control.OnFontChanged%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="b8e5a-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="b8e5a-121">La méthode d’accesseur set de la <xref:System.Windows.Forms.Control.Font%2A> les appels de propriété <xref:System.Windows.Forms.Control.OnFontChanged%2A> (méthode), qui à son tour déclenche le <xref:System.Windows.Forms.Control.FontChanged> événement.</span><span class="sxs-lookup"><span data-stu-id="b8e5a-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="b8e5a-122">Vous appelleriez `EnumMethodSemantics` à l’aide du MethodDef pour <xref:System.Windows.Forms.Control.OnFontChanged%2A> pour obtenir des références à la <xref:System.Windows.Forms.Control.Font%2A> propriété et la <xref:System.Windows.Forms.Control.FontChanged> événement.</span><span class="sxs-lookup"><span data-stu-id="b8e5a-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8e5a-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b8e5a-123">Requirements</span></span>  
 <span data-ttu-id="b8e5a-124">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8e5a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8e5a-125">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b8e5a-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b8e5a-126">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b8e5a-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b8e5a-127">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8e5a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8e5a-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8e5a-128">See Also</span></span>  
 [<span data-ttu-id="b8e5a-129">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="b8e5a-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b8e5a-130">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="b8e5a-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
