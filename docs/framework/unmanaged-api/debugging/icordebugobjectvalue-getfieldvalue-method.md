---
title: "ICorDebugObjectValue::GetFieldValue, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue.GetFieldValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9fcf53610cf96ef1ab62b4768521e8a2fb7ee6c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a><span data-ttu-id="a85d1-102">ICorDebugObjectValue::GetFieldValue, méthode</span><span class="sxs-lookup"><span data-stu-id="a85d1-102">ICorDebugObjectValue::GetFieldValue Method</span></span>
<span data-ttu-id="a85d1-103">Obtient la valeur du champ spécifié de la classe spécifiée pour la valeur de cet objet.</span><span class="sxs-lookup"><span data-stu-id="a85d1-103">Gets the value of the specified field of the specified class for this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a85d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a85d1-104">Syntax</span></span>  
  
```  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a85d1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a85d1-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="a85d1-106">[in] Pointeur vers un objet « ICorDebugClass » qui représente la classe pour laquelle obtenir la valeur du champ.</span><span class="sxs-lookup"><span data-stu-id="a85d1-106">[in] A pointer to an "ICorDebugClass" object that represents the class for which to get the field value.</span></span>  
  
 `fieldDef`  
 <span data-ttu-id="a85d1-107">[in] Un `mdFieldDef` jeton qui référence les métadonnées décrivant le champ.</span><span class="sxs-lookup"><span data-stu-id="a85d1-107">[in] An `mdFieldDef` token that references the metadata describing the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a85d1-108">[out] Pointeur vers un objet « ICorDebugValue » qui représente la valeur du champ spécifié.</span><span class="sxs-lookup"><span data-stu-id="a85d1-108">[out] A pointer to an "ICorDebugValue" object that represents the value of the specified field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a85d1-109">Notes</span><span class="sxs-lookup"><span data-stu-id="a85d1-109">Remarks</span></span>  
 <span data-ttu-id="a85d1-110">La classe spécifiée dans le `pClass` paramètre doit être dans la hiérarchie de classe de la valeur d’objet, et le champ doit être un champ de cette classe.</span><span class="sxs-lookup"><span data-stu-id="a85d1-110">The class, specified in the `pClass` parameter, must be in the hierarchy of the object value's class, and the field must be a field of that class.</span></span>  
  
 <span data-ttu-id="a85d1-111">Le `GetFieldValue` méthode continuera à aboutir pour les objets génériques et les classes génériques.</span><span class="sxs-lookup"><span data-stu-id="a85d1-111">The `GetFieldValue` method will still succeed for generic objects and generic classes.</span></span> <span data-ttu-id="a85d1-112">Par exemple, si MonDictionnaire\<V > hérite de dictionnaire\<de chaîne, V >, et la valeur de l’objet est de type MonDictionnaire\<int32 >, en passant le `ICorDebugClass` objet dictionnaire\<K, V > sera récupérer un champ de dictionnaire\<string, int32 >.</span><span class="sxs-lookup"><span data-stu-id="a85d1-112">For example, if MyDictionary\<V> inherits from Dictionary\<string,V>, and the object value is of type MyDictionary\<int32>, passing the `ICorDebugClass` object for Dictionary\<K,V> will successfully get a field of Dictionary\<string,int32>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a85d1-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a85d1-113">Requirements</span></span>  
 <span data-ttu-id="a85d1-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a85d1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a85d1-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a85d1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a85d1-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a85d1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a85d1-117">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a85d1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a85d1-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a85d1-118">See Also</span></span>  
    
 
