---
title: "IMetaDataImport::GetParamForMethodIndex, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetParamForMethodIndex
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetParamForMethodIndex
helpviewer_keywords:
- IMetaDataImport::GetParamForMethodIndex method [.NET Framework metadata]
- GetParamForMethodIndex method [.NET Framework metadata]
ms.assetid: ec3bfa95-1920-4511-932e-3ff23d76fcb8
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0cedc993e6b8794a15ff9927b06ff650ed76b79e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="a8309-102">IMetaDataImport::GetParamForMethodIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="a8309-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="a8309-103">Obtient le jeton qui représente un paramètre spécifié de la méthode représentée par le jeton MethodDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="a8309-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8309-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8309-104">Syntax</span></span>  
  
```  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a8309-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a8309-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="a8309-106">[in] Un jeton qui représente la méthode pour retourner le jeton de paramètre.</span><span class="sxs-lookup"><span data-stu-id="a8309-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="a8309-107">[in] La position ordinale dans la liste de paramètres où se produit le paramètre demandé.</span><span class="sxs-lookup"><span data-stu-id="a8309-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="a8309-108">Les paramètres sont numérotées à partir d’un, avec la valeur de retour à la position zéro.</span><span class="sxs-lookup"><span data-stu-id="a8309-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="a8309-109">[out] Pointeur vers un jeton ParamDef qui représente le paramètre demandé.</span><span class="sxs-lookup"><span data-stu-id="a8309-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8309-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a8309-110">Requirements</span></span>  
 <span data-ttu-id="a8309-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8309-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8309-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a8309-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a8309-113">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a8309-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a8309-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8309-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8309-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8309-115">See Also</span></span>  
 [<span data-ttu-id="a8309-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="a8309-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a8309-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="a8309-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
