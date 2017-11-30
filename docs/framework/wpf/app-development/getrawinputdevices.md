---
title: GetRawInputDevices
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e936b4ef2cab65e72ca9edbc3b95281815938983
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="getrawinputdevices"></a><span data-ttu-id="1cbab-102">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="1cbab-102">GetRawInputDevices</span></span>
<span data-ttu-id="1cbab-103">Permet à PresentationHost.exe de découvrir les périphériques d'entrée brute (périphériques d'interface utilisateur) qui intéressent l'application hôte.</span><span class="sxs-lookup"><span data-stu-id="1cbab-103">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cbab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1cbab-104">Syntax</span></span>  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1cbab-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1cbab-105">Parameters</span></span>  
 `ppEnum`  
  
 <span data-ttu-id="1cbab-106">[out] Un pointeur vers un [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) pour l’énumération des périphériques d’entrée brutes.</span><span class="sxs-lookup"><span data-stu-id="1cbab-106">[out] A pointer to an [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) for enumerating the raw input devices.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="1cbab-107">Valeur de propriété/valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1cbab-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="1cbab-108">HRESULT :</span><span class="sxs-lookup"><span data-stu-id="1cbab-108">HRESULT:</span></span>  
  
 <span data-ttu-id="1cbab-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) uniquement servir à PresentationHost.exe si S_OK est retourné.</span><span class="sxs-lookup"><span data-stu-id="1cbab-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) will only be used by PresentationHost.exe if S_OK is returned.</span></span>  
  
 <span data-ttu-id="1cbab-110">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="1cbab-110">E_NOTIMPL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cbab-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="1cbab-111">Remarks</span></span>  
 <span data-ttu-id="1cbab-112">Les périphériques d'entrée brute correspondent à l'ensemble des périphériques d'entrée, notamment les claviers, les souris et, dans une moindre mesure, les périphériques classiques tels que les télécommandes.</span><span class="sxs-lookup"><span data-stu-id="1cbab-112">Raw input devices are the set of input devices that includes keyboards, mice, and less traditional devices like remote controls.</span></span>  
  
 <span data-ttu-id="1cbab-113">Une fois la liste de périphériques d'entrée brute extraite, PresentationHost.exe s'inscrit auprès des périphériques pour recevoir les messages de notification WM_INPUT.</span><span class="sxs-lookup"><span data-stu-id="1cbab-113">Once the list of raw input devices has been retrieved, PresentationHost.exe registers with the devices to receive WM_INPUT notification messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cbab-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1cbab-114">See Also</span></span>  
 [<span data-ttu-id="1cbab-115">http://msdn.Microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.ASP</span><span class="sxs-lookup"><span data-stu-id="1cbab-115">http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp</span></span>](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp)  
 [<span data-ttu-id="1cbab-116">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="1cbab-116">FilterInputMessage</span></span>](../../../../docs/framework/wpf/app-development/filterinputmessage.md)
