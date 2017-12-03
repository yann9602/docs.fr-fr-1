---
title: Liaisons WS-MetadataExchange
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a7267fa8e71a7bbe202bce9897ea09079307be50
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="f27c4-102">Liaisons WS-MetadataExchange</span><span class="sxs-lookup"><span data-stu-id="f27c4-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="f27c4-103">Cette rubrique décrit comment les liaisons d’échange de métadonnées par défaut sont construites pour les divers transports.</span><span class="sxs-lookup"><span data-stu-id="f27c4-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="f27c4-104">Liaisons par défaut</span><span class="sxs-lookup"><span data-stu-id="f27c4-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="f27c4-105">Nom de la liaison par défaut</span><span class="sxs-lookup"><span data-stu-id="f27c4-105">Default Binding Name</span></span>|<span data-ttu-id="f27c4-106">Construction de la liaison</span><span class="sxs-lookup"><span data-stu-id="f27c4-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="f27c4-107">MexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="f27c4-107">MexHttpBinding</span></span>|<span data-ttu-id="f27c4-108"><xref:System.ServiceModel.WSHttpBinding> avec la sécurité au niveau du transport désactivée.</span><span class="sxs-lookup"><span data-stu-id="f27c4-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="f27c4-109">MexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="f27c4-109">MexHttpsBinding</span></span>|<span data-ttu-id="f27c4-110"><xref:System.ServiceModel.WSHttpBinding> qui prend en charge la sécurité au niveau du transport.</span><span class="sxs-lookup"><span data-stu-id="f27c4-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="f27c4-111">MexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="f27c4-111">MexNamedPipeBinding</span></span>|<span data-ttu-id="f27c4-112"><xref:System.ServiceModel.Channels.CustomBinding> avec <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> en utilisant les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="f27c4-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="f27c4-113">MexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="f27c4-113">MexTcpBinding</span></span>|<span data-ttu-id="f27c4-114"><xref:System.ServiceModel.Channels.CustomBinding> avec <xref:System.ServiceModel.Channels.TcpTransportBindingElement> en utilisant les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="f27c4-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
