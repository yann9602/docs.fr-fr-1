---
title: "Attribution d'un nouveau nom à un service WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c2ecd78a7d72b86460f4d1972c42c8550010f02
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="85336-102">Attribution d'un nouveau nom à un service WCF</span><span class="sxs-lookup"><span data-stu-id="85336-102">Renaming a WCF Service</span></span>
<span data-ttu-id="85336-103">Cette rubrique décrit comment renommer un service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85336-103">This topic describes how you can rename a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="85336-104">Attribution d'un nouveau nom à un service WCF</span><span class="sxs-lookup"><span data-stu-id="85336-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="85336-105">Effectuez les étapes suivantes pour renommer un service dans un modèle [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85336-105">Perform the following steps to rename a service in a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] template,</span></span>  
  
-   <span data-ttu-id="85336-106">Modifiez le nom de la classe qui implémente le service.</span><span class="sxs-lookup"><span data-stu-id="85336-106">Change the name of the class that implements the service.</span></span>  
  
-   <span data-ttu-id="85336-107">Dans le fichier de configuration du service, remplacez le nom du service par celui que vous avez choisi, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="85336-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="85336-108">Selon votre modèle d'hébergement, le fichier de configuration sera app.config ou web.config.</span><span class="sxs-lookup"><span data-stu-id="85336-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   <span data-ttu-id="85336-109">Si votre service est hébergé sur le Web, il utilise un fichier *.svc.</span><span class="sxs-lookup"><span data-stu-id="85336-109">If your service is webhosted, it uses an *.svc file.</span></span> <span data-ttu-id="85336-110">Ouvrez le fichier svc et modifiez le nom de votre service comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="85336-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="85336-111">Cette étape n'est pas nécessaire pour les applications auto-hébergées, puisqu'il n'y a pas de fichier svc.</span><span class="sxs-lookup"><span data-stu-id="85336-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="85336-112">Attribution d'un nouveau nom à un contrat de service WCF</span><span class="sxs-lookup"><span data-stu-id="85336-112">Renaming a WCF Service Contract</span></span>  
  
-   <span data-ttu-id="85336-113">Effectuez les étapes suivantes pour renommer le contrat de service</span><span class="sxs-lookup"><span data-stu-id="85336-113">Perform the following steps to rename the service contract,</span></span>  
  
-   <span data-ttu-id="85336-114">Modifiez le nom du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="85336-114">Change the name of the service contract.</span></span>  
  
-   <span data-ttu-id="85336-115">Dans le fichier de configuration du service, remplacez le nom du contrat de service par le celui que vous avez choisi, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="85336-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="85336-116">Selon votre modèle d'hébergement, le fichier de configuration sera app.config ou web.config.</span><span class="sxs-lookup"><span data-stu-id="85336-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
