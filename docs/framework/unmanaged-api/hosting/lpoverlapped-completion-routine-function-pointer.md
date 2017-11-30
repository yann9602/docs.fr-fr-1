---
title: LPOVERLAPPED_COMPLETION_ROUTINE (pointeur fonction)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LPOVERLAPPED_COMPLETION_ROUTINE
api_location: mscoree.dll
api_type: COM
f1_keywords: LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords: LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4d50f2058796d4c5c900474cdcbe71d8a5a911ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a><span data-ttu-id="73851-102">LPOVERLAPPED_COMPLETION_ROUTINE (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="73851-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>
<span data-ttu-id="73851-103">Pointe vers une fonction qui avertit l’hôte lorsqu’un chevauchement (autrement dit, asynchrone) e/s sur un périphérique est terminée.</span><span class="sxs-lookup"><span data-stu-id="73851-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="73851-104">Ce pointeur de fonction a été déconseillé dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="73851-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73851-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73851-105">Syntax</span></span>  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73851-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="73851-106">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="73851-107">[in] Une valeur qui est un code d’erreur si l’appareil a été fermé ; Sinon, cette valeur est zéro.</span><span class="sxs-lookup"><span data-stu-id="73851-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="73851-108">Fermeture d’un périphérique entraîne tout en attente d’e/s sur le périphérique pour être exécutée immédiatement.</span><span class="sxs-lookup"><span data-stu-id="73851-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="73851-109">[in] Le nombre d’octets transférés par l’opération d’e/s.</span><span class="sxs-lookup"><span data-stu-id="73851-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="73851-110">[in] Pointeur vers une structure qui contient des informations à utiliser pour effectuer la demande d’e/s.</span><span class="sxs-lookup"><span data-stu-id="73851-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73851-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="73851-111">Remarks</span></span>  
 <span data-ttu-id="73851-112">La fonction à laquelle `LPOVERLAPPED_COMPLETION_ROUTINE` points est une fonction de rappel et doit être implémentée par le writer de l’application d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="73851-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="73851-113">La fonction de rappel permet à l’hôte traiter la demande d’e/s achevée.</span><span class="sxs-lookup"><span data-stu-id="73851-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73851-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="73851-114">Requirements</span></span>  
 <span data-ttu-id="73851-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73851-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73851-116">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="73851-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="73851-117">**Bibliothèque :** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="73851-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="73851-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73851-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73851-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73851-119">See Also</span></span>  
 [<span data-ttu-id="73851-120">Fonctions d’hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="73851-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
