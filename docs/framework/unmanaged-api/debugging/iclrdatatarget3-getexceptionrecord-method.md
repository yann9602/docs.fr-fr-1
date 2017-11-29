---
title: "ICLRDataTarget3::GetExceptionRecord, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICLRDataTarget3.GetExceptionRecord
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f8c9ac4ecc0cffda4038129b1244b81501e9a1f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="c0e75-102">ICLRDataTarget3::GetExceptionRecord, méthode</span><span class="sxs-lookup"><span data-stu-id="c0e75-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>
<span data-ttu-id="c0e75-103">Appelé par les services d'accès aux données du Common Langage Runtime (CLR) pour récupérer l'enregistrement d'exception associé au processus cible.</span><span class="sxs-lookup"><span data-stu-id="c0e75-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="c0e75-104">Par exemple, pour une cible d’image mémoire, ceci serait équivalent à l’enregistrement de l’exception passée le `ExceptionParam` l’argument de la [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360.aspx) fonction dans le Windows déboguer bibliothèque d’aide (DbgHelp).</span><span class="sxs-lookup"><span data-stu-id="c0e75-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360.aspx) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0e75-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0e75-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0e75-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c0e75-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="c0e75-107">[en entrée] La taille de la mémoire tampon d'entrée, en octets.</span><span class="sxs-lookup"><span data-stu-id="c0e75-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="c0e75-108">Cela doit être égal à `sizeof(` [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)`)`.</span><span class="sxs-lookup"><span data-stu-id="c0e75-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="c0e75-109">[en sortie] Un pointeur vers un type `ULONG32` qui reçoit le nombre d'octets réellement écrits dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c0e75-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="c0e75-110">[en sortie] Un pointeur vers une mémoire tampon qui reçoit une copie de l'enregistrement de l'exception.</span><span class="sxs-lookup"><span data-stu-id="c0e75-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="c0e75-111">L’enregistrement d’exception est retourné comme un [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) type.</span><span class="sxs-lookup"><span data-stu-id="c0e75-111">The exception record is returned as a [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0e75-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c0e75-112">Return Value</span></span>  
 <span data-ttu-id="c0e75-113">La valeur de retour est `S_OK` en cas de réussite ou un code d'échec `HRESULT` en cas d'échec.</span><span class="sxs-lookup"><span data-stu-id="c0e75-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="c0e75-114">Les codes `HRESULT` peuvent comprendre, sans y être limités, ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="c0e75-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="c0e75-115">Code de retour</span><span class="sxs-lookup"><span data-stu-id="c0e75-115">Return code</span></span>|<span data-ttu-id="c0e75-116">Description</span><span class="sxs-lookup"><span data-stu-id="c0e75-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="c0e75-117">La méthode a réussi.</span><span class="sxs-lookup"><span data-stu-id="c0e75-117">Method succeeded.</span></span> <span data-ttu-id="c0e75-118">L'enregistrement de l'exception a été copié dans la mémoire tampon de sortie.</span><span class="sxs-lookup"><span data-stu-id="c0e75-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="c0e75-119">Aucun enregistrement d'exception n'est associé à la cible.</span><span class="sxs-lookup"><span data-stu-id="c0e75-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="c0e75-120">La taille de la mémoire tampon d'entrée est différente de `sizeof(MINIDUMP_EXCEPTION)`.</span><span class="sxs-lookup"><span data-stu-id="c0e75-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0e75-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="c0e75-121">Remarks</span></span>  
 <span data-ttu-id="c0e75-122">[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) est une structure définie dans dbghelp.h et Imagehlp.h, dans le SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="c0e75-122">[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="c0e75-123">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="c0e75-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0e75-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c0e75-124">Requirements</span></span>  
 <span data-ttu-id="c0e75-125">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0e75-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0e75-126">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="c0e75-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c0e75-127">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0e75-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0e75-128">**Versions du .NET framework :**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0e75-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e75-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0e75-129">See Also</span></span>  
 [<span data-ttu-id="c0e75-130">Iclrdatatarget3, Interface</span><span class="sxs-lookup"><span data-stu-id="c0e75-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="c0e75-131">Getexceptioncontextrecord, méthode</span><span class="sxs-lookup"><span data-stu-id="c0e75-131">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [<span data-ttu-id="c0e75-132">Getexceptionthreadid, méthode</span><span class="sxs-lookup"><span data-stu-id="c0e75-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
