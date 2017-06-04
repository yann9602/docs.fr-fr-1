---
title: "IEnumRAWINPUTDEVIC:Next | Microsoft Docs"
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
  - "Méthode Next"
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# IEnumRAWINPUTDEVIC:Next
Énumère les prochaines structures `celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) de la liste de l'énumérateur, en les retournant dans `rgelt` avec le nombre réel d'éléments énumérés dans `pceltFetched`.  
  
## Syntaxe  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### Paramètres  
 `celt`  
  
 \[in\] Nombre de structures [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) retournées dans `rgelt`.  
  
 `rgelt`  
  
 \[out\] Tableau de taille celt \(ou supérieure\) destiné à recevoir les structures RAWINPUTDEVICE énumérées.  
  
 `pceltFetched`  
  
 \[out\] Pointeur vers le nombre d'éléments réellement fournis dans `rgelt`.  L'appelant peut passer `NULL` si `rgelt` a la valeur un.  
  
## Valeur de propriété\/valeur de retour  
 HRESULT : S\_OK si le nombre d'éléments fournis est `celt` ; sinon, S\_FALSE.