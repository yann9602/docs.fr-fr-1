---
title: "Comparaison des services Web ASP.NET et de WCF en fonction de l'objectif et des normes utilisées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b43fe9cf66fc9ccf72d12c6a617a1b4c0b44def
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a><span data-ttu-id="bcb63-102">Comparaison des services Web ASP.NET et de WCF en fonction de l'objectif et des normes utilisées</span><span class="sxs-lookup"><span data-stu-id="bcb63-102">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>
<span data-ttu-id="bcb63-103">Les services Web ASP.NET ont été développés pour générer des applications qui envoient et reçoivent des messages à l'aide du protocole SOAP (Simple Object Access Protocol) sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="bcb63-103">ASP.NET Web services was developed for building applications that send and receive messages by using the Simple Object Access Protocol (SOAP) over HTTP.</span></span> <span data-ttu-id="bcb63-104">La structure des messages peut être définie à l'aide d'un schéma XML et un outil est fourni pour faciliter la sérialisation des messages vers et à partir d'objets .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bcb63-104">The structure of the messages can be defined using an XML Schema, and a tool is provided to facilitate serializing the messages to and from .NET Framework objects.</span></span> <span data-ttu-id="bcb63-105">La technologie peut générer automatiquement des métadonnées afin de décrire des services Web dans le langage WSDL (Web Services Description Language) et un deuxième outil est fourni pour générer des clients pour les services Web à partir du WSDL.</span><span class="sxs-lookup"><span data-stu-id="bcb63-105">The technology can automatically generate metadata to describe Web services in the Web Services Description Language (WSDL), and a second tool is provided for generating clients for Web services from the WSDL.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="bcb63-106"> permet aux applications .NET Framework d'échanger des messages avec d'autres entités logicielles.</span><span class="sxs-lookup"><span data-stu-id="bcb63-106"> is for enabling .NET Framework applications to exchange messages with other software entities.</span></span> <span data-ttu-id="bcb63-107">SOAP est utilisé par défaut, mais les messages peuvent se présenter sous tout format et sont acheminés en utilisant tout protocole de transport.</span><span class="sxs-lookup"><span data-stu-id="bcb63-107">SOAP is used by default, but the messages can be in any format, and conveyed by using any transport protocol.</span></span> <span data-ttu-id="bcb63-108">La structure des messages peut être définie à l'aide d'un schéma XML et il existe plusieurs options de sérialisation des messages vers et à partir d'objets .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bcb63-108">The structure of the messages can be defined using an XML Schema, and there are various options for serializing the messages to and from .NET Framework objects.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="bcb63-109"> peut générer automatiquement des métadonnées afin de décrire les applications générées à l'aide de la technologie dans WSDL, et il fournit également un outil pour générer des clients pour ces applications à partir du WSDL.</span><span class="sxs-lookup"><span data-stu-id="bcb63-109"> can automatically generate metadata to describe applications built using the technology in WSDL, and it also provides a tool for generating clients for those applications from the WSDL.</span></span>  
  
 <span data-ttu-id="bcb63-110">Les normes prises en charge par les services Web ASP.NET sont documentées dans [les Services Web XML créés à l’aide d’ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94872).</span><span class="sxs-lookup"><span data-stu-id="bcb63-110">The standards supported by ASP.NET Web services are documented in [XML Web Services Created Using ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94872).</span></span> <span data-ttu-id="bcb63-111">La liste plus complète des normes prises en charge par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont répertoriés à [Web Services protocoles pris en charge par les liaisons d’interopérabilité fournies par](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="bcb63-111">The more extensive list of standards supported by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are listed at [Web Services Protocols Supported by System-Provided Interoperability Bindings](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcb63-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcb63-112">See Also</span></span>  
 [<span data-ttu-id="bcb63-113">Comparaison des services web ASP.NET et de WCF du point de vue du développement</span><span class="sxs-lookup"><span data-stu-id="bcb63-113">Comparing ASP.NET Web Services to WCF Based on Development</span></span>](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
