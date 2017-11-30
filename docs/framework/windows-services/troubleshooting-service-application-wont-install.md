---
title: "Résolution des problèmes : Succès d’Application de Service &#39; t installation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 82eb870761a7865385631cd9961ce99e0b0d3502
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="troubleshooting-service-application-won39t-install"></a><span data-ttu-id="4f94f-102">Résolution des problèmes : Succès d’Application de Service &#39; t installation</span><span class="sxs-lookup"><span data-stu-id="4f94f-102">Troubleshooting: Service Application Won&#39;t Install</span></span>
<span data-ttu-id="4f94f-103">Si votre application de service ne s’installe pas correctement, vérifiez que le <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> propriété pour la classe de service est définie sur la même valeur, comme indiqué dans le programme d’installation de ce service.</span><span class="sxs-lookup"><span data-stu-id="4f94f-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="4f94f-104">La valeur doit être le même dans les deux instances dans l’ordre de votre service installer correctement.</span><span class="sxs-lookup"><span data-stu-id="4f94f-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f94f-105">Vous pouvez également consulter les journaux d’installation pour obtenir des commentaires sur le processus d’installation.</span><span class="sxs-lookup"><span data-stu-id="4f94f-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="4f94f-106">Vous devez également vérifier pour déterminer si vous avez un autre service portant le même nom que celui déjà installé.</span><span class="sxs-lookup"><span data-stu-id="4f94f-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="4f94f-107">Les noms de service doivent être uniques pour l’installation réussisse.</span><span class="sxs-lookup"><span data-stu-id="4f94f-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f94f-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f94f-108">See Also</span></span>  
 [<span data-ttu-id="4f94f-109">Introduction aux Applications de Service Windows</span><span class="sxs-lookup"><span data-stu-id="4f94f-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
