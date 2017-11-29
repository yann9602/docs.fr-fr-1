---
title: "ISymUnmanagedSourceServerModule::GetSourceServerData, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSourceServerModule.GetSourceServerData
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5774e46f69a7c38943314697575c7aef67b96693
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="4e658-102">ISymUnmanagedSourceServerModule::GetSourceServerData, méthode</span><span class="sxs-lookup"><span data-stu-id="4e658-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="4e658-103">Retourne les données du serveur source pour le module.</span><span class="sxs-lookup"><span data-stu-id="4e658-103">Returns the source server data for the module.</span></span> <span data-ttu-id="4e658-104">L’appelant doit libérer des ressources à l’aide de `CoTaskMemFree`.</span><span class="sxs-lookup"><span data-stu-id="4e658-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e658-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e658-105">Syntax</span></span>  
  
```  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4e658-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4e658-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="4e658-107">[out] Un pointeur vers un `ULONG32` qui reçoit la taille, en octets, les source des données du serveur.</span><span class="sxs-lookup"><span data-stu-id="4e658-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="4e658-108">[out] Un pointeur vers retourné `pDataByteCount` valeur.</span><span class="sxs-lookup"><span data-stu-id="4e658-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e658-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4e658-109">Return Value</span></span>  
 <span data-ttu-id="4e658-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="4e658-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e658-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4e658-111">Requirements</span></span>  
 <span data-ttu-id="4e658-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4e658-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e658-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e658-113">See Also</span></span>  
 [<span data-ttu-id="4e658-114">ISymUnmanagedSourceServerModule (Interface)</span><span class="sxs-lookup"><span data-stu-id="4e658-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
