---
title: "Déploiement d'un projet de bibliothèque WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 04567b0b06ef5c8f105e866e150bfaa221d64057
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="deploying-a-wcf-library-project"></a><span data-ttu-id="3f36b-102">Déploiement d'un projet de bibliothèque WCF</span><span class="sxs-lookup"><span data-stu-id="3f36b-102">Deploying a WCF Library Project</span></span>
<span data-ttu-id="3f36b-103">Cette rubrique décrit comment déployer un projet de bibliothèque du service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f36b-103">This topic describes how you can deploy a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Service Library Project.</span></span>  
  
## <a name="deploying-a-wcf-service-library"></a><span data-ttu-id="3f36b-104">Déploiement d'une bibliothèque du service WCF</span><span class="sxs-lookup"><span data-stu-id="3f36b-104">Deploying a WCF Service Library</span></span>  
 <span data-ttu-id="3f36b-105">Une bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est une bibliothèque de liens dynamiques (DLL).</span><span class="sxs-lookup"><span data-stu-id="3f36b-105">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library is a dynamic-link library (DLL).</span></span> <span data-ttu-id="3f36b-106">À ce titre, elle ne peut pas être exécutée seule.</span><span class="sxs-lookup"><span data-stu-id="3f36b-106">As such, it cannot be executed on its own.</span></span> <span data-ttu-id="3f36b-107">Elle doit être déployée dans un environnement d'hébergement.</span><span class="sxs-lookup"><span data-stu-id="3f36b-107">It needs to be deployed into a hosting environment.</span></span> <span data-ttu-id="3f36b-108">Pour plus d’informations sur ce processus, consultez [hébergement et utilisation des Services WCF](http://go.microsoft.com/fwlink/?LinkId=99932).</span><span class="sxs-lookup"><span data-stu-id="3f36b-108">For more information about this process, see [Hosting and Consuming WCF Services](http://go.microsoft.com/fwlink/?LinkId=99932).</span></span>  
  
 <span data-ttu-id="3f36b-109">Une bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] peut être déployée comme tout autre service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f36b-109">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library can be deployed like any other [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="3f36b-110">Sachez toutefois que [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ne prend pas en charge de configuration pour les DLL.</span><span class="sxs-lookup"><span data-stu-id="3f36b-110">However, be aware that [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] does not support configuration for DLLs.</span></span> <span data-ttu-id="3f36b-111"><xref:System.Configuration> prend en charge un fichier de configuration par domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="3f36b-111"><xref:System.Configuration> supports one configuration file per app-domain.</span></span> <span data-ttu-id="3f36b-112">Le projet de bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] contourne cette limitation en fournissant un fichier App.config pour la bibliothèque pendant la phase de développement.</span><span class="sxs-lookup"><span data-stu-id="3f36b-112">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library project alleviates this limitation by providing an App.config file for the library during development.</span></span> <span data-ttu-id="3f36b-113">Toutefois, le fichier App.config n'est pas reconnu après le déploiement.</span><span class="sxs-lookup"><span data-stu-id="3f36b-113">However, the App.config file is not recognized after deployment.</span></span>  
  
 <span data-ttu-id="3f36b-114">Vous devez placer votre code de configuration dans le fichier de configuration reconnu par votre environnement d'hébergement.</span><span class="sxs-lookup"><span data-stu-id="3f36b-114">You have to move your configuration code into the configuration file recognized by your hosting environment.</span></span> <span data-ttu-id="3f36b-115">Pour l'auto-hébergement, vous devez copier le contenu du fichier App.config dans le fichier App.config de l'exécutable d'hébergement.</span><span class="sxs-lookup"><span data-stu-id="3f36b-115">For self-hosting, you should copy the contents of the App.config file into the App.config file of the hosting executable.</span></span> <span data-ttu-id="3f36b-116">Si vous utilisez IIS pour héberger votre service, vous devez copier le contenu du fichier App.config dans le fichier Web.config du répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="3f36b-116">If you use IIS to host your service, you should copy the contents of the App.config file into the Web.config file of the virtual directory.</span></span>
