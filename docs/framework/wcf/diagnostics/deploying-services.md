---
title: "Déploiement de services"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 75069b00fa07078ff0eb2d49e64f046d5415d154
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="deploying-services"></a><span data-ttu-id="a8deb-102">Déploiement de services</span><span class="sxs-lookup"><span data-stu-id="a8deb-102">Deploying Services</span></span>
<span data-ttu-id="a8deb-103">Cette rubrique décrit comment vous pouvez déployer une application [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dans un environnement d'exécution.</span><span class="sxs-lookup"><span data-stu-id="a8deb-103">This topic describes how you can deploy a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="a8deb-104">Choix de l'environnement d'hébergement de votre application</span><span class="sxs-lookup"><span data-stu-id="a8deb-104">Choosing the Hosting Environment for Your Application</span></span>  
 <span data-ttu-id="a8deb-105">Les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont conçus pour s'exécuter dans tout processus Windows qui prend en charge le code managé.</span><span class="sxs-lookup"><span data-stu-id="a8deb-105">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="a8deb-106">Pour devenir actif, un service doit être hébergé dans un environnement d'exécution qui le crée et contrôle son contexte et sa durée de vie.</span><span class="sxs-lookup"><span data-stu-id="a8deb-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="a8deb-107">Les options d'hébergement vont de l'exécution à l'intérieur de l'application console la plus simple à une exécution dans des environnements serveur comme un service Windows et les services Internet (IIS) ou dans un processus de travail géré par WAS (Windows Activation Services).</span><span class="sxs-lookup"><span data-stu-id="a8deb-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="a8deb-108">Pour passer en revue les différentes options d’hébergements de votre [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, consultez [Services d’hébergement](../../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="a8deb-108">To review the different hosting options for your [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, see [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8deb-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8deb-109">See Also</span></span>  
 [<span data-ttu-id="a8deb-110">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="a8deb-110">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)  
 [<span data-ttu-id="a8deb-111">Hébergement de services</span><span class="sxs-lookup"><span data-stu-id="a8deb-111">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
