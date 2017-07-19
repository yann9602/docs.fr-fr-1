---
title: "GetRawInputDevices | Microsoft Docs"
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
  - "GetRawInputDevices (méthode)"
  - "entrées brutes (WPF)"
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# GetRawInputDevices
Permet à PresentationHost.exe de découvrir les périphériques d'entrée brute \(périphériques d'interface utilisateur\) qui intéressent l'application hôte.  
  
## Syntaxe  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### Paramètres  
 `ppEnum`  
  
 \[out\] Pointeur vers un [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) pour l'énumération des périphériques d'entrée brute.  
  
## Valeur de propriété\/valeur de retour  
 HRESULT :  
  
 S\_OK \- [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) ne sera utilisé que par PresentationHost.exe si S\_OK est retourné.  
  
 E\_NOTIMPL  
  
## Notes  
 Les périphériques d'entrée brute correspondent à l'ensemble des périphériques d'entrée, notamment les claviers, les souris et, dans une moindre mesure, les périphériques classiques tels que les télécommandes.  
  
 Une fois la liste de périphériques d'entrée brute extraite, PresentationHost.exe s'inscrit auprès des périphériques pour recevoir les messages de notification WM\_INPUT.  
  
## Voir aussi  
 [http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/winui\/winui\/windowsuserinterface\/userinput\/rawinput\/rawinputreference\/rawinputfunctions\/getrawinputdevicelist.asp](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp)   
 [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)