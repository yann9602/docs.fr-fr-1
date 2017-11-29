---
title: "ICLRDataTarget3::GetExceptionContextRecord, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICLRDataTarget3.GetContextRecord
api_location: mscordbi.dll
api_type: COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c2e645222553f4000b300fa4f010ff81ff44d23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="6d08f-102">ICLRDataTarget3::GetExceptionContextRecord, méthode</span><span class="sxs-lookup"><span data-stu-id="6d08f-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="6d08f-103">Appelée par les services d'accès aux données du CLR (Common Langage Runtime) pour récupérer l'enregistrement de contexte associé au processus cible.</span><span class="sxs-lookup"><span data-stu-id="6d08f-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="6d08f-104">Par exemple, pour une cible d’image mémoire, ceci serait équivalent à l’enregistrement de contexte transmis le `ExceptionParam` l’argument de la [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) fonction dans le Windows déboguer bibliothèque d’aide (DbgHelp).</span><span class="sxs-lookup"><span data-stu-id="6d08f-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d08f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d08f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d08f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6d08f-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="6d08f-107">[en entrée] La taille de la mémoire tampon d'entrée, en octets.</span><span class="sxs-lookup"><span data-stu-id="6d08f-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="6d08f-108">Elle doit être d'une taille suffisante pour contenir l'enregistrement de contexte.</span><span class="sxs-lookup"><span data-stu-id="6d08f-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="6d08f-109">[en sortie] Un pointeur vers un type `ULONG32` qui reçoit le nombre d'octets réellement écrits dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="6d08f-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="6d08f-110">[en sortie] Un pointeur vers une mémoire tampon qui reçoit une copie de l'enregistrement de contexte.</span><span class="sxs-lookup"><span data-stu-id="6d08f-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="6d08f-111">L’enregistrement d’exception est retourné comme un [contexte](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) type.</span><span class="sxs-lookup"><span data-stu-id="6d08f-111">The exception record is returned as a [CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d08f-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6d08f-112">Return Value</span></span>  
 <span data-ttu-id="6d08f-113">La valeur de retour est `S_OK` en cas de réussite ou un code d'échec `HRESULT` en cas d'échec.</span><span class="sxs-lookup"><span data-stu-id="6d08f-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="6d08f-114">Les codes `HRESULT` peuvent comprendre, sans y être limités, ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="6d08f-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="6d08f-115">Code de retour</span><span class="sxs-lookup"><span data-stu-id="6d08f-115">Return code</span></span>|<span data-ttu-id="6d08f-116">Description</span><span class="sxs-lookup"><span data-stu-id="6d08f-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="6d08f-117">La méthode a réussi.</span><span class="sxs-lookup"><span data-stu-id="6d08f-117">Method succeeded.</span></span> <span data-ttu-id="6d08f-118">L'enregistrement de contexte a été copié dans la mémoire tampon de sortie.</span><span class="sxs-lookup"><span data-stu-id="6d08f-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="6d08f-119">Aucun enregistrement de contexte n'est associé à la cible.</span><span class="sxs-lookup"><span data-stu-id="6d08f-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="6d08f-120">La taille de la mémoire tampon d'entrée est insuffisante pour contenir l'enregistrement de contexte.</span><span class="sxs-lookup"><span data-stu-id="6d08f-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d08f-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="6d08f-121">Remarks</span></span>  
 <span data-ttu-id="6d08f-122">[CONTEXTE](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) est une structure spécifique à la plateforme définie dans les en-têtes fournis par le Kit de développement logiciel Windows.</span><span class="sxs-lookup"><span data-stu-id="6d08f-122">[CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="6d08f-123">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="6d08f-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d08f-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6d08f-124">Requirements</span></span>  
 <span data-ttu-id="6d08f-125">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d08f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d08f-126">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="6d08f-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="6d08f-127">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d08f-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d08f-128">**Versions du .NET framework :**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d08f-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d08f-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d08f-129">See Also</span></span>  
 [<span data-ttu-id="6d08f-130">Iclrdatatarget3, Interface</span><span class="sxs-lookup"><span data-stu-id="6d08f-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="6d08f-131">Getexceptionrecord, méthode</span><span class="sxs-lookup"><span data-stu-id="6d08f-131">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)  
 [<span data-ttu-id="6d08f-132">Getexceptionthreadid, méthode</span><span class="sxs-lookup"><span data-stu-id="6d08f-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
