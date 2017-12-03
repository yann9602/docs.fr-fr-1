---
title: "Déploiement d'applications WCF à l'aide de ClickOnce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 714e8341c58e5337d8e45bf61b48137d33fa51b9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="0e9e4-102">Déploiement d'applications WCF à l'aide de ClickOnce</span><span class="sxs-lookup"><span data-stu-id="0e9e4-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="0e9e4-103">Les applications clientes qui utilisent [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] peuvent être déployées à l'aide de la technologie ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="0e9e4-103">Client applications using [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="0e9e4-104">Cette technologie leur permet de tirer parti des protections de sécurité d'exécution fournies par la sécurité d'accès du code, sous réserve qu'elles soient signées numériquement avec un certificat approuvé.</span><span class="sxs-lookup"><span data-stu-id="0e9e4-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="0e9e4-105">Le certificat utilisé pour signer l'application ClickOnce doit résider dans le magasin d'éditeurs approuvés, et la stratégie de sécurité locale sur l'ordinateur client doit être configurée pour accorder des autorisations Confiance totale aux applications signées avec le certificat de l'éditeur.</span><span class="sxs-lookup"><span data-stu-id="0e9e4-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="0e9e4-106">Pour plus d’informations sur la configuration des applications ClickOnce et éditeurs approuvés, consultez [configuration d’éditeurs approuvés ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).</span><span class="sxs-lookup"><span data-stu-id="0e9e4-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](http://go.microsoft.com/fwlink/?LinkId=94774).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e9e4-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e9e4-107">See Also</span></span>  
 [<span data-ttu-id="0e9e4-108">Vue d’ensemble du déploiement d’applications approuvées</span><span class="sxs-lookup"><span data-stu-id="0e9e4-108">Trusted Application Deployment Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=94775)  
 [<span data-ttu-id="0e9e4-109">Applications de déploiement de ClickOnce pour les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0e9e4-109">ClickOnce Deployment for Windows Forms Applications</span></span>](http://go.microsoft.com/fwlink/?LinkId=94776)
