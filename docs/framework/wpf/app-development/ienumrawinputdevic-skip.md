---
title: "IEnumRAWINPUTDEVIC:Skip | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Skip (méthode)"
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# IEnumRAWINPUTDEVIC:Skip
Demande à l'énumérateur d'ignorer les éléments `celt` suivants dans l'énumération afin que le prochain appel de [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) ne retourne pas ces éléments.  
  
## Syntaxe  
  
```  
HRESULT Skip( [in] ULONG celt);  
```  
  
#### Paramètres  
 `celt`  
  
 \[in\] Nombre d'éléments à ignorer.  
  
## Valeur de propriété\/valeur de retour  
 HRESULT: S\_OK si le nombre d'éléments fourni est `celt` ; sinon, S\_FALSE.