---
title: "Extension du système de métadonnées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aca7a7aba7ef4a40100e9858561d197916b71544
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-metadata-system"></a><span data-ttu-id="e4453-102">Extension du système de métadonnées</span><span class="sxs-lookup"><span data-stu-id="e4453-102">Extending the Metadata System</span></span>
<span data-ttu-id="e4453-103">Le système des métadonnées [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] est un groupe de classes et d'interfaces qui représentent les métadonnées requises pour implémenter des applications basées sur un service.</span><span class="sxs-lookup"><span data-stu-id="e4453-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="e4453-104">Modifiez ou étendez les classes ou implémentez et configurez les interfaces pour exporter et importer des métadonnées personnalisées telles que les extensions WSDL (Web Services Description Language) ou des assertions WS-PolicyAttachments personnalisées.</span><span class="sxs-lookup"><span data-stu-id="e4453-104">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e4453-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e4453-105">In This Section</span></span>  
 [<span data-ttu-id="e4453-106">Exportation de métadonnées personnalisées pour une extension WCF</span><span class="sxs-lookup"><span data-stu-id="e4453-106">Exporting Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="e4453-107">Décrit comment implémenter et utiliser l'interface <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> pour incorporer des assertions de stratégie personnalisées dans des documents WSDL.</span><span class="sxs-lookup"><span data-stu-id="e4453-107">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface to embed custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="e4453-108">Importation de métadonnées personnalisées pour une extension WCF</span><span class="sxs-lookup"><span data-stu-id="e4453-108">Importing Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="e4453-109">Décrit comment implémenter et utiliser l'interface <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> pour lire et répondre à des assertions de stratégie personnalisées dans des documents WSDL.</span><span class="sxs-lookup"><span data-stu-id="e4453-109">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface to read and respond to custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="e4453-110">Publication et récupération de métadonnées sur une liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="e4453-110">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 <span data-ttu-id="e4453-111">Décrit comment échanger des métadonnées sur des liaisons personnalisées.</span><span class="sxs-lookup"><span data-stu-id="e4453-111">Describes how to exchange metadata over custom bindings.</span></span>
