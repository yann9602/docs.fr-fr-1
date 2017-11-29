---
title: FilterInputMessage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b3a0e58c7485d46f004db7ea52215be60340b68
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="filterinputmessage"></a>FilterInputMessage
Appelé par PresentationHost.exe chaque fois qu'un message est reçu, à moins que E_NOTIMPL soit retourné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pMsg`  
  
 [in] Message WM_INPUT envoyé à la fenêtre qui obtient l'entrée brute.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 HRESULT :  
  
 S_OK : le filtre n'a pas traité le message et le traitement peut se poursuivre.  
  
 S_FALSE : le filtre a traité ce message et aucun autre traitement ne doit se produire.  
  
 E_NOTIMPL – si cette valeur est retournée, [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) n’est pas appelée à nouveau. Cette valeur peut être retournée par une application hôte qui cherche seulement à fournir une progression personnalisée et des interfaces utilisateur d'erreur à PresentationHost.exe, mais pas à se faire transférer des messages d'entrée brute depuis PresentationHost.exe.  
  
## <a name="remarks"></a>Remarques  
 PresentationHost.exe est la cible de divers périphériques d'entrée brute, notamment les claviers, les souris et les télécommandes. Le comportement de l'application hôte est parfois dépendant de l'entrée qui serait autrement consommée par PresentationHost.exe. Par exemple, une application hôte peut être tributaire de la réception de certains messages d'entrée pour déterminer s'il faut ou non afficher des éléments d'interface utilisateur spécifiques.  
  
 Pour autoriser l’application hôte de recevoir les messages d’entrée nécessaires pour fournir ces comportements, PresentationHost.exe transfère des messages d’entrée brutes appropriés à l’application hébergée en appelant [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).  
  
 L’application hébergée reçoit des messages d’entrée brutes en inscrivant avec l’ensemble des périphériques d’entrée brutes (périphériques d’Interface utilisateur) retourné par [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Notification de WM_INPUT](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputmessages/wm_input.asp)
