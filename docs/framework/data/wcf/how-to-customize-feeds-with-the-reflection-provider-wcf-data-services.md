---
title: "Comment : personnaliser les flux avec le fournisseur de réflexion (services de données WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aefa959550f7c5cf2fc189e99eb6f2a36da23ff4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="2a177-102">Comment : personnaliser les flux avec le fournisseur de réflexion (services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="2a177-102">How to: Customize Feeds with the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="2a177-103"> vous permet de personnaliser la sérialisation Atom dans une réponse du service de données pour pouvoir mapper les propriétés d'une entité aux éléments inutilisés définis dans le protocole AtomPub.</span><span class="sxs-lookup"><span data-stu-id="2a177-103"> enables you to customize the Atom serialization in a data service response so that properties of an entity may be mapped to unused elements that are defined in the AtomPub protocol.</span></span> <span data-ttu-id="2a177-104">Cette rubrique indique comment définir des attributs de mappage pour les types d'entité dans un modèle de données défini à l'aide du fournisseur de réflexion.</span><span class="sxs-lookup"><span data-stu-id="2a177-104">This topic shows how to define mapping attributes for the entity types in a data model that is defined by using the reflection provider.</span></span> <span data-ttu-id="2a177-105">Pour plus d’informations, consultez [personnalisation de flux](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="2a177-105">For more information, see [Feed Customization](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="2a177-106">Le modèle de données pour cet exemple est défini dans la rubrique [Comment : créer un Service de données à l’aide du fournisseur de réflexion](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="2a177-106">The data model for this example is defined in the topic [How to: Create a Data Service Using the Reflection Provider](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a177-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="2a177-107">Example</span></span>  
 <span data-ttu-id="2a177-108">Dans l'exemple suivant, les deux propriétés du type `Order` sont mappées aux éléments Atom existants.</span><span class="sxs-lookup"><span data-stu-id="2a177-108">In the following example, both properties of the `Order` type are mapped to existing Atom elements.</span></span> <span data-ttu-id="2a177-109">La propriété `Product` du type `Item` est mappée à un attribut de flux personnalisé dans un espace de noms séparé.</span><span class="sxs-lookup"><span data-stu-id="2a177-109">The `Product` property of the `Item` type is mapped to a custom feed attribute in a separate namespace.</span></span>  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria custom feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria custom feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a><span data-ttu-id="2a177-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="2a177-110">Example</span></span>  
 <span data-ttu-id="2a177-111">L'exemple précédent retourne le résultat suivant pour l'URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span><span class="sxs-lookup"><span data-stu-id="2a177-111">The previous example returns the following result for the URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span></span>  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a><span data-ttu-id="2a177-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a177-112">See Also</span></span>  
 [<span data-ttu-id="2a177-113">Fournisseur de réflexion</span><span class="sxs-lookup"><span data-stu-id="2a177-113">Reflection Provider</span></span>](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
