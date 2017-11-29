---
title: "Création de services pouvant interagir avec le profil Basic Profile 1.1 de WS-I"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a725f1cbe50bcad5247e727efcffbad62985a01a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="3abef-102">Création de services pouvant interagir avec le profil Basic Profile 1.1 de WS-I</span><span class="sxs-lookup"><span data-stu-id="3abef-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="3abef-103">Pour configurer un point de terminaison de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] afin qu'il puisse interagir avec les clients du service Web [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="3abef-103">To configure a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service endpoint to be interoperable with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients:</span></span>  
  
-   <span data-ttu-id="3abef-104">Utilisez le type <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> comme type de liaison pour votre point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="3abef-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
-   <span data-ttu-id="3abef-105">N'utilisez pas les fonctionnalités de rappel et de contrat de session, ni les comportements de transaction sur votre point de terminaison de service</span><span class="sxs-lookup"><span data-stu-id="3abef-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
 <span data-ttu-id="3abef-106">Vous pouvez éventuellement activer la prise en charge du protocole HTTPS et de l'authentification du client au niveau du transport sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="3abef-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
 <span data-ttu-id="3abef-107">Les fonctionnalités suivantes de la classe <xref:System.ServiceModel.BasicHttpBinding> requièrent des fonctionnalités qui dépassent le profil Basic Profile 1.1 de WS-I :</span><span class="sxs-lookup"><span data-stu-id="3abef-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
-   <span data-ttu-id="3abef-108">Encodage des messages MTOM (Message Transmission Optimisation Mechanism) contrôlé par la propriété <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3abef-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="3abef-109">Conservez la valeur par défaut de cette propriété, à savoir <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> pour ne pas utiliser MTOM.</span><span class="sxs-lookup"><span data-stu-id="3abef-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
-   <span data-ttu-id="3abef-110">La sécurité du message contrôlée par la valeur <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> fournit une prise en charge de WS-Security conforme à WS-I Basic Security Profile 1.0.</span><span class="sxs-lookup"><span data-stu-id="3abef-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="3abef-111">Conservez la valeur par défaut de cette propriété, à savoir <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> pour ne pas utiliser WS-Security.</span><span class="sxs-lookup"><span data-stu-id="3abef-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
 <span data-ttu-id="3abef-112">Pour rendre les métadonnées un [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service disponible pour [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], utilisez les outils de génération de client de service Web : [Web Services Description Language Tool (Wsdl.exe)](http://msdn.microsoft.com/en-us/b9210348-8bc2-4367-8c91-d1a04b403e88), [Web Services Discovery Tool () Disco.exe)](http://msdn.microsoft.com/en-us/acd88078-c581-42bc-94ca-6633e2851979)et le `Add Web Reference` fonctionnalité dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]; vous devez activer la publication de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="3abef-112">To make the metadata for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service available to [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](http://msdn.microsoft.com/en-us/b9210348-8bc2-4367-8c91-d1a04b403e88), [Web Services Discovery Tool (Disco.exe)](http://msdn.microsoft.com/en-us/acd88078-c581-42bc-94ca-6633e2851979), and the `Add Web Reference` feature in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]; you must enable metadata publication.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="3abef-113">[Points de terminaison de métadonnées de publication](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="3abef-113"> [Publishing Metadata Endpoints](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3abef-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="3abef-114">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="3abef-115">Description</span><span class="sxs-lookup"><span data-stu-id="3abef-115">Description</span></span>  
 <span data-ttu-id="3abef-116">L’exemple de code suivant montre comment ajouter un [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] point de terminaison qui est compatible avec [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] les clients du service dans le code, ainsi que dans un fichier de configuration Web.</span><span class="sxs-lookup"><span data-stu-id="3abef-116">The following example code demonstrates how to add a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] endpoint that is compatible with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3abef-117">Code</span><span class="sxs-lookup"><span data-stu-id="3abef-117">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3abef-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3abef-118">See Also</span></span>  
 [<span data-ttu-id="3abef-119">Interopérabilité avec les Services Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3abef-119">Interoperability with ASP.NET Web Services</span></span>](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
