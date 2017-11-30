---
title: "CreateIDispatchSTAForwarder (fonction) (référence des API non managées WPF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: CreateIDispatchSTAForwarder
api_location: PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63195ce2a47add2606f528b18d0d1d58ab0d968c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="c75dd-102">CreateIDispatchSTAForwarder (fonction) (référence des API non managées WPF)</span><span class="sxs-lookup"><span data-stu-id="c75dd-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="c75dd-103">Cette API prend en charge l’infrastructure de Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement depuis votre code.</span><span class="sxs-lookup"><span data-stu-id="c75dd-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="c75dd-104">Utilisée par l’infrastructure de Windows Presentation Foundation (WPF) pour la gestion des threads et de windows.</span><span class="sxs-lookup"><span data-stu-id="c75dd-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c75dd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c75dd-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c75dd-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c75dd-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="c75dd-107">Valeur de propriété/valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c75dd-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="c75dd-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="c75dd-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="c75dd-109">Un pointeur vers un `IDispatch` interface.</span><span class="sxs-lookup"><span data-stu-id="c75dd-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="c75dd-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="c75dd-110">ppForwarder</span></span>  
 <span data-ttu-id="c75dd-111">Un pointeur vers l’adresse d’un `IDispatch` interface.</span><span class="sxs-lookup"><span data-stu-id="c75dd-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c75dd-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c75dd-112">Requirements</span></span>  
 <span data-ttu-id="c75dd-113">**Plateformes :** consultez [configuration système requise du .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c75dd-113">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c75dd-114">**DLL :**</span><span class="sxs-lookup"><span data-stu-id="c75dd-114">**DLL:**</span></span>  
  
 <span data-ttu-id="c75dd-115">Dans le .NET Framework 3.0 et 3.5 : PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="c75dd-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="c75dd-116">Dans le .NET Framework 4 et versions ultérieures : PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="c75dd-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="c75dd-117">**Version du .NET framework :**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c75dd-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c75dd-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c75dd-118">See Also</span></span>  
 [<span data-ttu-id="c75dd-119">Référence des API non managées WPF</span><span class="sxs-lookup"><span data-stu-id="c75dd-119">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
