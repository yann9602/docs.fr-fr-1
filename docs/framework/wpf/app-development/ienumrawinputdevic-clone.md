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
ms.openlocfilehash: 35f3c00f3a0efd41c425ba29f8465a73e78d624c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
Crée un autre énumérateur de périphériques d'entrée brute avec le même état que l'énumérateur actif pour itérer au sein de la même liste.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppenum`  
  
 [out] Adresse de variable de sortie qui reçoit le [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) pointeur d’interface. Si la méthode échoue, la valeur de cette variable de sortie est non définie.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 HRESULT : Cette méthode prend en charge les valeurs de retournés E_INVALIDARG et E_OUTOFMEMORY E_UNEXPECTED standard.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode rend possible l’enregistrement d’un point dans la séquence d’énumération afin de retourner à ce point à une date ultérieure. L’appelant doit libérer ce nouvel énumérateur séparément à partir du premier énumérateur.
