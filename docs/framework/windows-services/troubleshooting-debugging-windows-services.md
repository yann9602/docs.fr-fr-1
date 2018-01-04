---
title: "Résolution des problèmes : débogage des services Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- troubleshooting service applications
- services, troubleshooting
- troubleshooting debugging, Windows Services
- Windows Service applications, debugging
- services, debugging
- Windows Service applications, troubleshooting
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: f38e65e93d4e6668795bf254573993d5100e2328
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-debugging-windows-services"></a>Résolution des problèmes : débogage des services Windows
Lorsque vous déboguez une application de service Windows, votre service et le **Gestionnaire des services Windows** interagir. Le **Service Manager** démarre votre service en appelant le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> (méthode), puis attend 30 secondes pour le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> retour de méthode. Si la méthode ne retourne pas dans cette période, le gestionnaire affiche une erreur que le service ne peut pas être démarré.  
  
 Lorsque vous déboguez le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> méthode décrite dans [Comment : déboguer des Applications de Service Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), vous devez être conscient de ce délai de 30 secondes. Si vous placez un point d’arrêt dans le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> (méthode) et ne pas à pas détaillé dans les 30 secondes, le gestionnaire ne démarre pas le service.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour déboguer les applications de service Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Introduction aux applications de service Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
