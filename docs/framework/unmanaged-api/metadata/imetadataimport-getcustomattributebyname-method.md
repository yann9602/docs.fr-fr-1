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
ms.openlocfilehash: 5b689c54b5e8d741d32bc941b4e78e6674f15e01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="8ef6f-102">IMetaDataImport::GetCustomAttributeByName, méthode</span><span class="sxs-lookup"><span data-stu-id="8ef6f-102">IMetaDataImport::GetCustomAttributeByName Method</span></span>
<span data-ttu-id="8ef6f-103">Obtient l’attribut personnalisé, en fonction de son nom et le propriétaire.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-103">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ef6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ef6f-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ef6f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8ef6f-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="8ef6f-106">[in] Un jeton de métadonnées représentant l’objet qui possède l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-106">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="8ef6f-107">[in] Le nom de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-107">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="8ef6f-108">[out] Pointeur vers un tableau de données qui est la valeur de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-108">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="8ef6f-109">[out] La taille en octets des données retournées dans *`ppData`.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-109">[out] The size in bytes of the data returned in *`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ef6f-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="8ef6f-110">Remarks</span></span>  
 <span data-ttu-id="8ef6f-111">Il est permis de définir plusieurs attributs personnalisés pour le même propriétaire ; ils peuvent même avoir le même nom.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-111">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="8ef6f-112">Toutefois, `GetCustomAttributeByName` ne retourne qu’une seule instance.</span><span class="sxs-lookup"><span data-stu-id="8ef6f-112">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="8ef6f-113">(`GetCustomAttributeByName` retourne la première instance qu’il rencontre.) Pour rechercher toutes les instances d’un attribut personnalisé, appelez le [IMetaDataImport::EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="8ef6f-113">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ef6f-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8ef6f-114">Requirements</span></span>  
 <span data-ttu-id="8ef6f-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ef6f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ef6f-116">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8ef6f-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ef6f-117">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ef6f-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8ef6f-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ef6f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef6f-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ef6f-119">See Also</span></span>  
 [<span data-ttu-id="8ef6f-120">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="8ef6f-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="8ef6f-121">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="8ef6f-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
