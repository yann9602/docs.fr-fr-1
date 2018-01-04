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
ms.workload: dotnet
ms.openlocfilehash: 7e76f9863b68d5c7c34bca8adc872210527d6c17
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="filterinputmessage"></a><span data-ttu-id="83d1e-102">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="83d1e-102">FilterInputMessage</span></span>
<span data-ttu-id="83d1e-103">Appelé par PresentationHost.exe chaque fois qu'un message est reçu, à moins que E_NOTIMPL soit retourné.</span><span class="sxs-lookup"><span data-stu-id="83d1e-103">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83d1e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83d1e-104">Syntax</span></span>  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83d1e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="83d1e-105">Parameters</span></span>  
 `pMsg`  
  
 <span data-ttu-id="83d1e-106">[in] Message WM_INPUT envoyé à la fenêtre qui obtient l'entrée brute.</span><span class="sxs-lookup"><span data-stu-id="83d1e-106">[in] The WM_INPUT message sent to the window that is getting raw input.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="83d1e-107">Valeur de propriété/valeur de retour</span><span class="sxs-lookup"><span data-stu-id="83d1e-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="83d1e-108">HRESULT :</span><span class="sxs-lookup"><span data-stu-id="83d1e-108">HRESULT:</span></span>  
  
 <span data-ttu-id="83d1e-109">S_OK : le filtre n'a pas traité le message et le traitement peut se poursuivre.</span><span class="sxs-lookup"><span data-stu-id="83d1e-109">S_OK - The filter did not process the message and further processing may occur.</span></span>  
  
 <span data-ttu-id="83d1e-110">S_FALSE : le filtre a traité ce message et aucun autre traitement ne doit se produire.</span><span class="sxs-lookup"><span data-stu-id="83d1e-110">S_FALSE - The filter processed this message and no further processing should occur.</span></span>  
  
 <span data-ttu-id="83d1e-111">E_NOTIMPL – si cette valeur est retournée, [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) n’est pas appelée à nouveau.</span><span class="sxs-lookup"><span data-stu-id="83d1e-111">E_NOTIMPL – If this value is returned, [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) is not called again.</span></span> <span data-ttu-id="83d1e-112">Cette valeur peut être retournée par une application hôte qui cherche seulement à fournir une progression personnalisée et des interfaces utilisateur d'erreur à PresentationHost.exe, mais pas à se faire transférer des messages d'entrée brute depuis PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="83d1e-112">This might be returned from a host application that is only interested in providing custom progress and error user interfaces to PresentationHost.exe is not interested in being forwarded raw input messages from PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83d1e-113">Notes</span><span class="sxs-lookup"><span data-stu-id="83d1e-113">Remarks</span></span>  
 <span data-ttu-id="83d1e-114">PresentationHost.exe est la cible de divers périphériques d'entrée brute, notamment les claviers, les souris et les télécommandes.</span><span class="sxs-lookup"><span data-stu-id="83d1e-114">PresentationHost.exe is the target of various raw input devices, including keyboard, mice, and remote controls.</span></span> <span data-ttu-id="83d1e-115">Le comportement de l'application hôte est parfois dépendant de l'entrée qui serait autrement consommée par PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="83d1e-115">Sometimes, behavior in the host application is dependent on input that would otherwise be consumed by PresentationHost.exe.</span></span> <span data-ttu-id="83d1e-116">Par exemple, une application hôte peut être tributaire de la réception de certains messages d'entrée pour déterminer s'il faut ou non afficher des éléments d'interface utilisateur spécifiques.</span><span class="sxs-lookup"><span data-stu-id="83d1e-116">For example, a host application may depend on receiving certain input messages to determine whether or not to display specific user interface elements.</span></span>  
  
 <span data-ttu-id="83d1e-117">Pour autoriser l’application hôte de recevoir les messages d’entrée nécessaires pour fournir ces comportements, PresentationHost.exe transfère des messages d’entrée brutes appropriés à l’application hébergée en appelant [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).</span><span class="sxs-lookup"><span data-stu-id="83d1e-117">To allow the host application to receive the necessary input messages to provide these behaviors, PresentationHost.exe forwards appropriate raw input messages to the hosted application by calling [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).</span></span>  
  
 <span data-ttu-id="83d1e-118">L’application hébergée reçoit des messages d’entrée brutes en inscrivant avec l’ensemble des périphériques d’entrée brutes (périphériques d’Interface utilisateur) retourné par [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).</span><span class="sxs-lookup"><span data-stu-id="83d1e-118">The hosted application receives raw input messages by registering with the set of raw input devices (Human Interface Devices) returned by [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83d1e-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83d1e-119">See Also</span></span>  
 [<span data-ttu-id="83d1e-120">Notification de WM_INPUT</span><span class="sxs-lookup"><span data-stu-id="83d1e-120">WM_INPUT Notification</span></span>](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputmessages/wm_input.asp)
