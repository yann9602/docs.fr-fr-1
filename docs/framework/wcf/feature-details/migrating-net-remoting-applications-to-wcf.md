---
title: "Migration d'applications .NET Remoting vers WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 240901f4fa04a2468d5964821680506ea117bf7f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="3639b-102">Migration d'applications .NET Remoting vers WCF</span><span class="sxs-lookup"><span data-stu-id="3639b-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="3639b-103">**Cette rubrique est spécifique à une technologie héritée qui assure la compatibilité descendante avec des applications existantes et n'est pas recommandée en cas de nouveau développement. Les applications distribuées doivent maintenant être développées à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**</span><span class="sxs-lookup"><span data-stu-id="3639b-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**</span></span>  
  
 <span data-ttu-id="3639b-104">Il existe deux manière de tirer parti de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec les applications .NET Remoting existantes : l'intégration et la migration.</span><span class="sxs-lookup"><span data-stu-id="3639b-104">There are two ways to take advantage of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="3639b-105">L'intégration vous permet d'exécuter .Net Remoting 2.0 et [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] côte à côte et ainsi d'exposer les mêmes objets métier sur ces deux technologies simultanément sans avoir à modifier votre code .Net Remoting 2.0 existant.</span><span class="sxs-lookup"><span data-stu-id="3639b-105">Integration allows you to have .Net Remoting 2.0 and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .Net Remoting 2.0 code.</span></span> <span data-ttu-id="3639b-106">L'intégration requiert l'utilisation de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="3639b-106">Integration requires that you are running on [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 or greater.</span></span> <span data-ttu-id="3639b-107">Si vous souhaitez tirer parti des fonctionnalités [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et que la compatibilité des câbles avec les systèmes Remoting 2.0 n'est pas nécessaire, vous pouvez migrer l'ensemble de votre service vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3639b-107">If you want to take advantage of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="3639b-108">La migration de .NET Remoting 2.0 vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requiert la modification de l'interface de l'objet distant et de ses paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="3639b-108">Migration from .NET Remoting 2.0 to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="3639b-109">Deux de ces rubriques sont abordés dans [à partir de la communication à distance de Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).</span><span class="sxs-lookup"><span data-stu-id="3639b-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3639b-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3639b-110">See Also</span></span>  
 [<span data-ttu-id="3639b-111">Vue d’ensemble conceptuelle</span><span class="sxs-lookup"><span data-stu-id="3639b-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
