---
title: Conversion d'une application NetTcpBinding en une application de canal homologue
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d52b005013e9728cfcdb43ad289984018b90d27c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a><span data-ttu-id="75810-102">Conversion d'une application NetTcpBinding en une application de canal homologue</span><span class="sxs-lookup"><span data-stu-id="75810-102">Converting a NetTcpBinding Application to a Peer Channel Application</span></span>
<span data-ttu-id="75810-103">Vous pouvez créer des connexions entre des clients à l'aide du [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] en utilisant des liaisons qui décrivent les paramètres de la connexion.</span><span class="sxs-lookup"><span data-stu-id="75810-103">You can create connections between clients using the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] by using bindings that describe the parameters of the connection.</span></span> <span data-ttu-id="75810-104">La conversion d'une application du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour utiliser des connexions d'égal à égal requiert une liaison qui prend en charge cette technologie lors de l'établissement des connexions clientes.</span><span class="sxs-lookup"><span data-stu-id="75810-104">Converting a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application to use peer-to-peer connections requires a binding that supports this technology when making client connections.</span></span> <span data-ttu-id="75810-105">Le canal homologue fournit une liaison nommée <xref:System.ServiceModel.NetPeerTcpBinding>, que vous pouvez utiliser de manière semblable à <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="75810-105">Peer Channel provides a binding called <xref:System.ServiceModel.NetPeerTcpBinding>, which you can use in a similar way to the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="75810-106">Les principales différences incluent la spécification d'un service de résolution et la définition de paramètres de sécurité.</span><span class="sxs-lookup"><span data-stu-id="75810-106">Key differences include specifying a resolver service and defining security settings.</span></span>  
  
 <span data-ttu-id="75810-107">Si une application utilise le programme de résolution et les paramètres de sécurité par défaut, la conversion d’une application normale client-serveur pour utiliser le canal homologue implique la modification du nom de la liaison de « NetTcpBinding » en « NetPeerTcpBinding » dans le fichier de configuration de l’application ; il n’est pas nécessaire de modifier la base de code de l’application.</span><span class="sxs-lookup"><span data-stu-id="75810-107">If an application is using the default resolver and security settings, converting a normal client/server-based application to use Peer Channel entails changing the name of the binding from "NetTcpBinding" to "NetPeerTcpBinding" in the application’s configuration file—you do not have to change the application code base.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75810-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75810-108">See Also</span></span>  
 [<span data-ttu-id="75810-109">Création d’une Application de canal homologue</span><span class="sxs-lookup"><span data-stu-id="75810-109">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)  
 [<span data-ttu-id="75810-110">Liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="75810-110">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
