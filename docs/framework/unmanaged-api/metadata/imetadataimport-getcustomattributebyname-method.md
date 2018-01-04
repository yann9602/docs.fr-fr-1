---
title: "IMetaDataImport::GetCustomAttributeByName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetCustomAttributeByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d234a58d95203a26e8b1cab2cb936e6ee50c2fa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="26bc9-102">IMetaDataImport::GetCustomAttributeByName, méthode</span><span class="sxs-lookup"><span data-stu-id="26bc9-102">IMetaDataImport::GetCustomAttributeByName Method</span></span>
<span data-ttu-id="26bc9-103">Obtient l’attribut personnalisé, en fonction de son nom et le propriétaire.</span><span class="sxs-lookup"><span data-stu-id="26bc9-103">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26bc9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26bc9-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26bc9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="26bc9-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="26bc9-106">[in] Un jeton de métadonnées représentant l’objet qui possède l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="26bc9-106">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="26bc9-107">[in] Le nom de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="26bc9-107">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="26bc9-108">[out] Pointeur vers un tableau de données qui est la valeur de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="26bc9-108">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="26bc9-109">[out] La taille en octets des données retournées dans *`ppData`.</span><span class="sxs-lookup"><span data-stu-id="26bc9-109">[out] The size in bytes of the data returned in *`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26bc9-110">Notes</span><span class="sxs-lookup"><span data-stu-id="26bc9-110">Remarks</span></span>  
 <span data-ttu-id="26bc9-111">Il est permis de définir plusieurs attributs personnalisés pour le même propriétaire ; ils peuvent même avoir le même nom.</span><span class="sxs-lookup"><span data-stu-id="26bc9-111">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="26bc9-112">Toutefois, `GetCustomAttributeByName` ne retourne qu’une seule instance.</span><span class="sxs-lookup"><span data-stu-id="26bc9-112">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="26bc9-113">(`GetCustomAttributeByName` retourne la première instance qu’il rencontre.) Pour rechercher toutes les instances d’un attribut personnalisé, appelez le [IMetaDataImport::EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="26bc9-113">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26bc9-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="26bc9-114">Requirements</span></span>  
 <span data-ttu-id="26bc9-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26bc9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26bc9-116">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="26bc9-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="26bc9-117">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="26bc9-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="26bc9-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26bc9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26bc9-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26bc9-119">See Also</span></span>  
 [<span data-ttu-id="26bc9-120">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="26bc9-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="26bc9-121">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="26bc9-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
