---
title: IEnumRAWINPUTDEVIC:Skip
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 216be1bc48a140bdd326010a87899cc342feb41d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="ienumrawinputdevicskip"></a><span data-ttu-id="be216-102">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="be216-102">IEnumRAWINPUTDEVIC:Skip</span></span>
<span data-ttu-id="be216-103">Fait en sorte que l’énumérateur d’ignorer la prochaine `celt` éléments dans l’énumération afin que le prochain appel à [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) ne retourne pas ces éléments.</span><span class="sxs-lookup"><span data-stu-id="be216-103">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) will not return those elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be216-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be216-104">Syntax</span></span>  
  
```  
HRESULT Skip( [in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be216-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="be216-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="be216-106">[in] Nombre d’éléments à ignorer.</span><span class="sxs-lookup"><span data-stu-id="be216-106">[in] Number of elements to be skipped.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="be216-107">Valeur de propriété/valeur de retour</span><span class="sxs-lookup"><span data-stu-id="be216-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="be216-108">HRESULT : S_OK si le nombre d'éléments fournis est `celt` ; sinon, S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="be216-108">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
