---
title: IEnumRAWINPUTDEVIC:Clone
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db218ec824dfe163946b0c1bd412efd0f78f4ad8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="eb31e-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="eb31e-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="eb31e-103">Crée un autre énumérateur de périphériques d'entrée brute avec le même état que l'énumérateur actif pour itérer au sein de la même liste.</span><span class="sxs-lookup"><span data-stu-id="eb31e-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb31e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb31e-104">Syntax</span></span>  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb31e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eb31e-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="eb31e-106">[out] Adresse de variable de sortie qui reçoit le [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) pointeur d’interface.</span><span class="sxs-lookup"><span data-stu-id="eb31e-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="eb31e-107">Si la méthode échoue, la valeur de cette variable de sortie est non définie.</span><span class="sxs-lookup"><span data-stu-id="eb31e-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="eb31e-108">Valeur de propriété/valeur de retour</span><span class="sxs-lookup"><span data-stu-id="eb31e-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="eb31e-109">HRESULT : Cette méthode prend en charge les valeurs de retournés E_INVALIDARG et E_OUTOFMEMORY E_UNEXPECTED standard.</span><span class="sxs-lookup"><span data-stu-id="eb31e-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb31e-110">Notes</span><span class="sxs-lookup"><span data-stu-id="eb31e-110">Remarks</span></span>  
 <span data-ttu-id="eb31e-111">Cette méthode rend possible l’enregistrement d’un point dans la séquence d’énumération afin de retourner à ce point à une date ultérieure.</span><span class="sxs-lookup"><span data-stu-id="eb31e-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="eb31e-112">L’appelant doit libérer ce nouvel énumérateur séparément à partir du premier énumérateur.</span><span class="sxs-lookup"><span data-stu-id="eb31e-112">The caller must release this new enumerator separately from the first enumerator.</span></span>
