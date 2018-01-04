---
title: Syndication WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: syndication [WCF]
ms.assetid: ebf80384-0fc9-4919-a1e8-23ca2a13e300
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f7f5fd65fc298107a66e2049c059f3cc58b3d44
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-syndication"></a><span data-ttu-id="ba2fa-102">Syndication WCF</span><span class="sxs-lookup"><span data-stu-id="ba2fa-102">WCF Syndication</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="ba2fa-103"> fournit la prise en charge nécessaire pour utiliser facilement les flux de syndication dans Atom, RSS ou d'autres formats personnalisés, ce qui vous permet de les lire et de les créer ainsi que de les exposer sur un point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="ba2fa-103"> provides support to easily work with syndication feeds in Atom, RSS or other custom formats, which allows you to read and create them as well as expose them on a service endpoint.</span></span> <span data-ttu-id="ba2fa-104">Les rubriques de cette section décrivent en détail ce modèle de programmation pour la syndication.</span><span class="sxs-lookup"><span data-stu-id="ba2fa-104">The topics in this section describe this programming model for syndication in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba2fa-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ba2fa-105">In This Section</span></span>  
 [<span data-ttu-id="ba2fa-106">Vue d’ensemble de la syndication WCF</span><span class="sxs-lookup"><span data-stu-id="ba2fa-106">WCF Syndication Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 <span data-ttu-id="ba2fa-107">Fournit une vue d'ensemble de la prise en charge de la syndication par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ba2fa-107">Provides an overview of syndication support provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="ba2fa-108">Architecture de syndication</span><span class="sxs-lookup"><span data-stu-id="ba2fa-108">Architecture of Syndication</span></span>](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)  
 <span data-ttu-id="ba2fa-109">Décrit les classes du modèle objet et l'extensibilité de la syndication.</span><span class="sxs-lookup"><span data-stu-id="ba2fa-109">Describes the classes in the object model and the extensibility of syndication.</span></span>  
  
 [<span data-ttu-id="ba2fa-110">Comment le modèle objet Syndication WCF est mappé à Atom et RSS</span><span class="sxs-lookup"><span data-stu-id="ba2fa-110">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)  
 <span data-ttu-id="ba2fa-111">Décrit de quelle manière les flux sont représentés dans le modèle objet de syndication WCF et comment ils sont convertis en flux RSS et Atom.</span><span class="sxs-lookup"><span data-stu-id="ba2fa-111">Describes how feeds are represented within the WCF Syndication Object Model and how they are converted to RSS and Atom feeds.</span></span>  
  
 [<span data-ttu-id="ba2fa-112">Guide pratique pour créer un flux RSS de base</span><span class="sxs-lookup"><span data-stu-id="ba2fa-112">How to: Create a Basic RSS Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-rss-feed.md)  
 <span data-ttu-id="ba2fa-113">Indique comment créer un service qui rend disponible un flux RSS de base.</span><span class="sxs-lookup"><span data-stu-id="ba2fa-113">Shows how to create a service that makes a basic RSS feed available.</span></span>  
  
 [<span data-ttu-id="ba2fa-114">Guide pratique pour créer un flux Atom de base</span><span class="sxs-lookup"><span data-stu-id="ba2fa-114">How to: Create a Basic Atom Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-atom-feed.md)  
 <span data-ttu-id="ba2fa-115">Indique comment créer un service qui rend disponible un flux ATOM de base.</span><span class="sxs-lookup"><span data-stu-id="ba2fa-115">Shows how to create a service that makes a basic ATOM feed available.</span></span>  
  
 [<span data-ttu-id="ba2fa-116">Guide pratique pour exposer un flux en tant que flux Atom et flux RSS</span><span class="sxs-lookup"><span data-stu-id="ba2fa-116">How to: Expose a Feed as Both Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-expose-a-feed-as-both-atom-and-rss.md)  
 <span data-ttu-id="ba2fa-117">Indique comment créer un service qui rend le même flux disponible avec ATOME et RSS.</span><span class="sxs-lookup"><span data-stu-id="ba2fa-117">Shows how to create a service that makes the same feed available with ATOM and RSS.</span></span>  
  
 [<span data-ttu-id="ba2fa-118">Extensibilité de la syndication</span><span class="sxs-lookup"><span data-stu-id="ba2fa-118">Syndication Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/syndication-extensibility.md)  
 <span data-ttu-id="ba2fa-119">Décrit les méthodes d'ajout d'attributs et d'éléments personnalisés à un flux de syndication.</span><span class="sxs-lookup"><span data-stu-id="ba2fa-119">Describes the methods of adding custom elements and attributes to a syndication feed.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ba2fa-120">Référence</span><span class="sxs-lookup"><span data-stu-id="ba2fa-120">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ba2fa-121">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="ba2fa-121">Related Sections</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba2fa-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba2fa-122">See Also</span></span>  
 [<span data-ttu-id="ba2fa-123">Modèle de programmation HTTP web WCF</span><span class="sxs-lookup"><span data-stu-id="ba2fa-123">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="ba2fa-124">Confiance partielle</span><span class="sxs-lookup"><span data-stu-id="ba2fa-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)
