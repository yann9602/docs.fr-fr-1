---
title: Cycle de vie de la programmation de base
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f5c45cad0b1e4ae1aa6b1963e9acdab47cd9203
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="basic-programming-lifecycle"></a><span data-ttu-id="61496-102">Cycle de vie de la programmation de base</span><span class="sxs-lookup"><span data-stu-id="61496-102">Basic Programming Lifecycle</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="61496-103"> permet aux applications de communiquer, qu'elles se trouvent sur le même ordinateur, sur Internet ou sur des plateformes d'application différentes.</span><span class="sxs-lookup"><span data-stu-id="61496-103"> enables applications to communicate whether they are on the same computer, across the Internet, or on different application platforms.</span></span> <span data-ttu-id="61496-104">Cette rubrique décrit brièvement les tâches qui sont requises pour générer une application [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="61496-104">This topic outlines the tasks that are required to build a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="61496-105">Pour un exemple d’application fonctionnel, consultez [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="61496-105">For a working sample application, see [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
## <a name="the-basic-tasks"></a><span data-ttu-id="61496-106">Tâches de base</span><span class="sxs-lookup"><span data-stu-id="61496-106">The Basic Tasks</span></span>  
 <span data-ttu-id="61496-107">Les tâches de base à accomplir sont les suivantes, dans l'ordre :</span><span class="sxs-lookup"><span data-stu-id="61496-107">The basic tasks to perform are, in order:</span></span>  
  
1.  <span data-ttu-id="61496-108">Définition du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="61496-108">Define the service contract.</span></span> <span data-ttu-id="61496-109">Un contrat de service spécifie la signature d'un service, les données qu'il échange et les autres données requises contractuellement.</span><span class="sxs-lookup"><span data-stu-id="61496-109">A service contract specifies the signature of a service, the data it exchanges, and other contractually required data.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="61496-110">[Concevoir des contrats de Service](../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="61496-110"> [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
2.  <span data-ttu-id="61496-111">Implémentation du contrat.</span><span class="sxs-lookup"><span data-stu-id="61496-111">Implement the contract.</span></span> <span data-ttu-id="61496-112">Pour implémenter un contrat de service, créez une classe qui implémente le contrat et spécifiez les comportements personnalisés requis pour le runtime.</span><span class="sxs-lookup"><span data-stu-id="61496-112">To implement a service contract, create a class that implements the contract and specify custom behaviors that the runtime should have.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="61496-113">[Implémentation de contrats de Service](../../../docs/framework/wcf/implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="61496-113"> [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md).</span></span>  
  
3.  <span data-ttu-id="61496-114">Configuration du service en spécifiant les informations de points de terminaison et d'autres informations de comportement.</span><span class="sxs-lookup"><span data-stu-id="61496-114">Configure the service by specifying endpoints and other behavior information.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="61496-115">[Configuration des Services](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="61496-115"> [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
4.  <span data-ttu-id="61496-116">Hébergement du service.</span><span class="sxs-lookup"><span data-stu-id="61496-116">Host the service.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="61496-117">[Services d’hébergement](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="61496-117"> [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
5.  <span data-ttu-id="61496-118">Création d'une application cliente.</span><span class="sxs-lookup"><span data-stu-id="61496-118">Build a client application.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="61496-119">[Génération de Clients](../../../docs/framework/wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="61496-119"> [Building Clients](../../../docs/framework/wcf/building-clients.md).</span></span>  
  
 <span data-ttu-id="61496-120">Bien que les rubriques de cette section suivent cet ordre, certains scénarios ne commencent pas au début.</span><span class="sxs-lookup"><span data-stu-id="61496-120">Although the topics in this section follow this order, some scenarios do not start at the beginning.</span></span> <span data-ttu-id="61496-121">Par exemple, si vous souhaitez générer un client pour un service préexistant, démarrez à l'étape 5.</span><span class="sxs-lookup"><span data-stu-id="61496-121">For example, if you want to build a client for a pre-existing service, you start at step 5.</span></span> <span data-ttu-id="61496-122">Autrement, si vous générez un service que d'autres utiliseront, vous pouvez ignorer l'étape 5.</span><span class="sxs-lookup"><span data-stu-id="61496-122">Or if you are building a service that others will use, you may skip step 5.</span></span>  
  
 <span data-ttu-id="61496-123">Une fois que vous êtes familiarisé avec le développement des contrats de service, vous pouvez également lire [Introduction à l’extensibilité](../../../docs/framework/wcf/introduction-to-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="61496-123">Once you are familiar with developing service contracts, you can also read [Introduction to Extensibility](../../../docs/framework/wcf/introduction-to-extensibility.md).</span></span> <span data-ttu-id="61496-124">Si vous rencontrez des problèmes avec votre service, vérifiez [démarrage rapide de résolution des problèmes WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) pour voir si d’autres présentent des problèmes similaires ou identiques.</span><span class="sxs-lookup"><span data-stu-id="61496-124">If you have problems with your service, check [WCF Troubleshooting Quickstart](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) to see whether others have the same or similar problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61496-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61496-125">See Also</span></span>  
 [<span data-ttu-id="61496-126">Implémentation de contrats de service</span><span class="sxs-lookup"><span data-stu-id="61496-126">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
