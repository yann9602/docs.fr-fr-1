---
title: ISymUnmanagedReader2, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2
helpviewer_keywords: ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 93f4b88d891d7b5c1d92006276a290841372aad7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="e059d-102">ISymUnmanagedReader2, interface</span><span class="sxs-lookup"><span data-stu-id="e059d-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="e059d-103">Représente un lecteur de symboles qui fournit l’accès aux documents, des méthodes et des variables dans un magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="e059d-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="e059d-104">Cette interface étend la [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="e059d-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e059d-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e059d-105">Methods</span></span>  
  
|<span data-ttu-id="e059d-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="e059d-106">Method</span></span>|<span data-ttu-id="e059d-107">Description</span><span class="sxs-lookup"><span data-stu-id="e059d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e059d-108">GetMethodByVersionPreRemap, méthode</span><span class="sxs-lookup"><span data-stu-id="e059d-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="e059d-109">Obtenir une méthode de lecteur de symboles, étant donné un jeton de méthode et un numéro de version modifier et continuer.</span><span class="sxs-lookup"><span data-stu-id="e059d-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="e059d-110">GetMethodsInDocument, méthode</span><span class="sxs-lookup"><span data-stu-id="e059d-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="e059d-111">Obtient chaque méthode qui a des informations de ligne dans le document fourni.</span><span class="sxs-lookup"><span data-stu-id="e059d-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="e059d-112">GetSymAttributePreRemap, méthode</span><span class="sxs-lookup"><span data-stu-id="e059d-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="e059d-113">Obtient un attribut personnalisé en fonction de son nom.</span><span class="sxs-lookup"><span data-stu-id="e059d-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e059d-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e059d-114">Requirements</span></span>  
 <span data-ttu-id="e059d-115">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e059d-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e059d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e059d-116">See Also</span></span>  
 [<span data-ttu-id="e059d-117">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="e059d-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="e059d-118">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="e059d-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
