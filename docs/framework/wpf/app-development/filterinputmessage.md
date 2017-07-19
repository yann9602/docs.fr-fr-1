---
title: "FilterInputMessage | Microsoft Docs"
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
  - "FilterInputMessage (méthode)"
  - "entrées brutes (WPF)"
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# FilterInputMessage
Appelé par PresentationHost.exe chaque fois qu'un message est reçu, à moins que E\_NOTIMPL soit retourné.  
  
## Syntaxe  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### Paramètres  
 `pMsg`  
  
 \[in\] Message WM\_INPUT envoyé à la fenêtre qui obtient l'entrée brute.  
  
## Valeur de propriété\/valeur de retour  
 HRESULT :  
  
 S\_OK : le filtre n'a pas traité le message et le traitement peut se poursuivre.  
  
 S\_FALSE : le filtre a traité ce message et aucun autre traitement ne doit se produire.  
  
 E\_NOTIMPL : si cette valeur est retournée, [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) n'est pas rappelé.  Cette valeur peut être retournée par une application hôte qui cherche seulement à fournir une progression personnalisée et des interfaces utilisateur d'erreur à PresentationHost.exe, mais pas à se faire transférer des messages d'entrée brute depuis PresentationHost.exe.  
  
## Notes  
 PresentationHost.exe est la cible de divers périphériques d'entrée brute, notamment les claviers, les souris et les télécommandes.  Le comportement de l'application hôte est parfois dépendant de l'entrée qui serait autrement consommée par PresentationHost.exe.  Par exemple, une application hôte peut être tributaire de la réception de certains messages d'entrée pour déterminer s'il faut ou non afficher des éléments d'interface utilisateur spécifiques.  
  
 Pour permettre à l'application hôte de recevoir les messages d'entrée nécessaires pour fournir ces comportements, PresentationHost.exe transfère les messages d'entrée brute appropriés à l'application hébergée en appelant [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).  
  
 L'application hébergée reçoit les messages d'entrée brute en s'inscrivant auprès du jeu de périphériques d'entrée brute \(périphériques d'interface utilisateur\) retourné par [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).  
  
## Voir aussi  
 [Notification WM\_INPUT](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputmessages/wm_input.asp)