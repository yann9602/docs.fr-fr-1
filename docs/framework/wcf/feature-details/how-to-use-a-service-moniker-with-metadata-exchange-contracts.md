---
title: "Comment : utiliser un moniker de service avec des contrats d'échange de métadonnées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed6ce9b87a5e2d8945a57110c02cce8024439f14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="23fa4-102">Comment : utiliser un moniker de service avec des contrats d'échange de métadonnées</span><span class="sxs-lookup"><span data-stu-id="23fa4-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="23fa4-103">Après avoir développé de nouveaux services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vous pouvez décider que vous souhaitez être en mesure d'appeler ces services à partir d'un script ou d'une application Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="23fa4-103">After developing some new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="23fa4-104">Une méthode consisterait à générer un assembly client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], à inscrire l'assembly avec COM, à installer l'assembly dans le Global Assembly Cache (GAC), puis à référencer les types COM à partir de votre code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="23fa4-104">One method would be to generate a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="23fa4-105">Lors de la distribution de l'application, vous devrez distribuer également l'assembly client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="23fa4-105">When you distribute the application, you will have to distribute the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Client assembly as well.</span></span> <span data-ttu-id="23fa4-106">L'utilisateur devra ensuite inscrire l'assembly client WCF avec COM et le placer dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="23fa4-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> <span data-ttu-id="23fa4-107">COM Interop [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vous permet également d'effectuer les mêmes appels de service sans reposer sur un assembly client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="23fa4-107">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] COM Interop also allows you to make the same service calls without relying on a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly.</span></span> <span data-ttu-id="23fa4-108">Le moniker [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vous permet d'appeler tout service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à partir de tout langage compatible avec COM (Visual Basic, VBScript, Visual Basic pour applications (VBA), et ainsi de suite) en spécifiant un URI de point de terminaison d'échange de métadonnées (Mex) que le moniker de service utilise pour extraire des informations de type à propos du service.</span><span class="sxs-lookup"><span data-stu-id="23fa4-108">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker allows you to call any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="23fa4-109">Cette rubrique décrit comment appeler l'exemple [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de Mise en route à l'aide d'un moniker [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui spécifie un point de terminaison Mex.</span><span class="sxs-lookup"><span data-stu-id="23fa4-109">This topic describes how to call the Getting Started [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23fa4-110">Les types définis par l'assembly client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne sont jamais réellement instanciés.</span><span class="sxs-lookup"><span data-stu-id="23fa4-110">The types defined by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly are never actually instantiated.</span></span> <span data-ttu-id="23fa4-111">L'assembly est utilisé uniquement pour les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="23fa4-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="23fa4-112">Utilisation du moniker de service avec une adresse Mex</span><span class="sxs-lookup"><span data-stu-id="23fa4-112">Using the service moniker with a Mex address</span></span>  
  
1.  <span data-ttu-id="23fa4-113">Générez l'exemple de Mise en route et utilisez Internet Explorer pour naviguer jusqu'à son URL (http://localhost/ServiceModelSamples/Service.svc) afin de vous assurer que le service fonctionne.</span><span class="sxs-lookup"><span data-stu-id="23fa4-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2.  <span data-ttu-id="23fa4-114">Créez un script Visual Basic ou une application Visual Basic qui contient le code suivant :</span><span class="sxs-lookup"><span data-stu-id="23fa4-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  <span data-ttu-id="23fa4-115">Exécutez l'application ou le script Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="23fa4-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="23fa4-116">Le service que vous appelez doit exposer un point de terminaison Mex pour que le moniker soit en mesure de lire les métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="23fa4-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="23fa4-117">Pour plus d’informations, consultez [Comment : publier les métadonnées pour un Service à l’aide d’un fichier de Configuration](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="23fa4-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="23fa4-118">Si le moniker est mal formé ou si le service n'est pas disponible, l'appel à `GetObject` retourne une erreur indiquant que la syntaxe n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="23fa4-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="23fa4-119">Si vous recevez cette erreur, assurez-vous que le moniker que vous utilisez est correct et que le service est disponible.</span><span class="sxs-lookup"><span data-stu-id="23fa4-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23fa4-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23fa4-120">See Also</span></span>  
 [<span data-ttu-id="23fa4-121">Comment : utiliser le Moniker de Service Windows Communication Foundation sans inscription</span><span class="sxs-lookup"><span data-stu-id="23fa4-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [<span data-ttu-id="23fa4-122">Comment : utiliser un Moniker de Service avec des contrats WSDL</span><span class="sxs-lookup"><span data-stu-id="23fa4-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
