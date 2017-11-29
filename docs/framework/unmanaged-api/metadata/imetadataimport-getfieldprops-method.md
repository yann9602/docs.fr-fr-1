---
title: "IMetaDataImport::GetFieldProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetFieldProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d5874169e0f8c452b177309702444ea84858557e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="c0399-102">IMetaDataImport::GetFieldProps, méthode</span><span class="sxs-lookup"><span data-stu-id="c0399-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="c0399-103">Obtient les métadonnées associées au champ référencé par le jeton FieldDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="c0399-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0399-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0399-104">Syntax</span></span>  
  
```  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,   
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0399-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c0399-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="c0399-106">[in] Jeton FieldDef qui représente le champ pour lequel obtenir les métadonnées associées.</span><span class="sxs-lookup"><span data-stu-id="c0399-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="c0399-107">[out] Pointeur vers un jeton TypeDef qui représente le type de la classe à laquelle appartient le champ.</span><span class="sxs-lookup"><span data-stu-id="c0399-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="c0399-108">[out] Le nom du champ.</span><span class="sxs-lookup"><span data-stu-id="c0399-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="c0399-109">[in] La taille en caractères larges de la mémoire tampon pour *szField*.</span><span class="sxs-lookup"><span data-stu-id="c0399-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="c0399-110">[out] La taille réelle de la mémoire tampon retournée.</span><span class="sxs-lookup"><span data-stu-id="c0399-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="c0399-111">[out] Indicateurs associés aux métadonnées du champ.</span><span class="sxs-lookup"><span data-stu-id="c0399-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="c0399-112">[in] Pointeur vers la valeur de métadonnées binaires qui décrit le champ.</span><span class="sxs-lookup"><span data-stu-id="c0399-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="c0399-113">[out] La taille en octets de `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="c0399-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="c0399-114">[out] Indicateur qui spécifie le type de valeur du champ.</span><span class="sxs-lookup"><span data-stu-id="c0399-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c0399-115">[out] Valeur de constante pour le champ.</span><span class="sxs-lookup"><span data-stu-id="c0399-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="c0399-116">[out] La taille en caractères de `ppValue`, ou zéro si aucune chaîne n’existe.</span><span class="sxs-lookup"><span data-stu-id="c0399-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0399-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c0399-117">Requirements</span></span>  
 <span data-ttu-id="c0399-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0399-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0399-119">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c0399-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c0399-120">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c0399-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c0399-121">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0399-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0399-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0399-122">See Also</span></span>  
 [<span data-ttu-id="c0399-123">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="c0399-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="c0399-124">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="c0399-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
