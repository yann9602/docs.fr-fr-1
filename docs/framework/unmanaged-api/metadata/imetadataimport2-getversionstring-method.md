---
title: "IMetaDataImport2::GetVersionString, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetVersionString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccf168473c1182e4b7d57d52930d90084eaa2dd8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="53c88-102">IMetaDataImport2::GetVersionString, méthode</span><span class="sxs-lookup"><span data-stu-id="53c88-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="53c88-103">Obtient le numéro de version du runtime qui a été utilisé pour générer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="53c88-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53c88-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53c88-104">Syntax</span></span>  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53c88-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="53c88-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="53c88-106">[out] Un tableau pour stocker la chaîne qui spécifie la version.</span><span class="sxs-lookup"><span data-stu-id="53c88-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="53c88-107">[in] La taille, en caractères larges, de le `pwzBuf` tableau.</span><span class="sxs-lookup"><span data-stu-id="53c88-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="53c88-108">[out] Le nombre de caractères larges, y compris une marque de fin null, retournés dans le `pwzBuf` tableau.</span><span class="sxs-lookup"><span data-stu-id="53c88-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53c88-109">Notes</span><span class="sxs-lookup"><span data-stu-id="53c88-109">Remarks</span></span>  
 <span data-ttu-id="53c88-110">Le `GetVersionString` méthode obtient la version propre à la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="53c88-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="53c88-111">Si l’étendue n’a jamais été enregistré, il n’a pas une version intégrée pour, et une chaîne vide est retournée.</span><span class="sxs-lookup"><span data-stu-id="53c88-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53c88-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="53c88-112">Requirements</span></span>  
 <span data-ttu-id="53c88-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53c88-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53c88-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="53c88-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="53c88-115">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="53c88-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="53c88-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53c88-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53c88-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53c88-117">See Also</span></span>  
 [<span data-ttu-id="53c88-118">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="53c88-118">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="53c88-119">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="53c88-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
