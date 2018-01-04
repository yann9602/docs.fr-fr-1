---
title: "Utilisation des outils de développement WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d253f38fab21496dd305cc67e7b6e84846579f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="9ae31-102">Utilisation des outils de développement WCF</span><span class="sxs-lookup"><span data-stu-id="9ae31-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="9ae31-103">Cette section décrit la [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] des outils de développement qui peuvent vous aider à développer votre [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]service.</span><span class="sxs-lookup"><span data-stu-id="9ae31-103">This section describes the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)][!INCLUDE[indigo1](../../../includes/indigo1-md.md)] development tools that can assist you in developing your [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]service.</span></span>  
  
 <span data-ttu-id="9ae31-104">Vous pouvez utiliser la [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] modèles comme base pour créer rapidement votre propre service, puis utilisez [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hôte de Service et [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Client Test pour déboguer et tester votre service.</span><span class="sxs-lookup"><span data-stu-id="9ae31-104">You can use the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] templates as a foundation to quickly build your own service, then use [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host and [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client to debug and test your service.</span></span> <span data-ttu-id="9ae31-105">Ces outils offrent un cycle de débogage et de test rapide et transparent tout en supprimant l’obligation de se limiter à un modèle d’hébergement à un stade précoce.</span><span class="sxs-lookup"><span data-stu-id="9ae31-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="9ae31-106">Outils WCF Developer</span><span class="sxs-lookup"><span data-stu-id="9ae31-106">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="9ae31-107">Modèles Visual Studio WCF</span><span class="sxs-lookup"><span data-stu-id="9ae31-107">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 <span data-ttu-id="9ae31-108">Vous pouvez utiliser les [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] les modèles de projet et d’élément dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] pour générer rapidement [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services et applications s’y rapportant.</span><span class="sxs-lookup"><span data-stu-id="9ae31-108">You can use the predefined [!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] project and item templates in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] to quickly build [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="9ae31-109">WCF Service Host (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="9ae31-109">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="9ae31-110">L'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (WcfSvcHost.exe) vous permet de lancer le débogueur [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] (F5) pour héberger et tester automatiquement un service que vous avez implémenté.</span><span class="sxs-lookup"><span data-stu-id="9ae31-110">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host (WcfSvcHost.exe) allows you to launch the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="9ae31-111">Vous pouvez ensuite tester le service à l'aide du client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (WcfTestClient.exe) ou de votre propre client, afin de rechercher et de résoudre les erreurs potentielles.</span><span class="sxs-lookup"><span data-stu-id="9ae31-111">You can then test the service using the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="9ae31-112">Client test WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="9ae31-112">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="9ae31-113">Le client test [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (WcfTestClient.exe) est un outil GUI qui permet d'entrer des paramètres de types arbitraires, d'envoyer ces entrées au service et d'afficher la réponse que le service renvoie.</span><span class="sxs-lookup"><span data-stu-id="9ae31-113">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="9ae31-114">Il offre des conditions de test de service transparentes lorsqu'il est associé à l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9ae31-114">It provides a seamless service testing experience when combined with [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host.</span></span>  
  
 [<span data-ttu-id="9ae31-115">Génération de classes de type de données à partir de XML</span><span class="sxs-lookup"><span data-stu-id="9ae31-115">Generating Data Type Classes from XML</span></span>](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="9ae31-116">Les données XML stockées dans le presse-papiers peuvent être collées dans une page de codes.</span><span class="sxs-lookup"><span data-stu-id="9ae31-116">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="9ae31-117">Les classes définies dans les données sont converties en types de codes.</span><span class="sxs-lookup"><span data-stu-id="9ae31-117">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="9ae31-118">Utilisation des outils sans privilège d'administrateur</span><span class="sxs-lookup"><span data-stu-id="9ae31-118">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="9ae31-119">Pour permettre aux utilisateurs qui ne disposent pas de privilèges d'administrateur de développer des services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], une liste de contrôle d'accès (ACL, Access Control List) est créée pour l'espace de noms http://+:8731/Design_Time_Addresses pendant l'installation de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9ae31-119">To enable users without administrator privilege to develop [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="9ae31-120">La liste ACL a la valeur (UI), qui inclut tous les utilisateurs interactifs ayant ouvert une session sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9ae31-120">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="9ae31-121">Les administrateurs peuvent ajouter ou supprimer des utilisateurs de cette liste ACL ou ouvrir des ports supplémentaires. Cette liste ACL permet aux modèles WCF ou WF d'envoyer et de recevoir des données dans leur configuration par défaut.</span><span class="sxs-lookup"><span data-stu-id="9ae31-121">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="9ae31-122">Elle permet également aux utilisateurs d'utiliser l'Hôte de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (wcfSvcHost.exe) sans leur accorder de privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="9ae31-122">It also enables users to use the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="9ae31-123">Vous pouvez modifier l'accès à l'aide de l'outil Netsh.exe dans [!INCLUDE[wv](../../../includes/wv-md.md)] par le biais du compte d'administrateur supérieur.</span><span class="sxs-lookup"><span data-stu-id="9ae31-123">You can modify access using the Netsh.exe tool in [!INCLUDE[wv](../../../includes/wv-md.md)] under the elevated administrator account.</span></span> <span data-ttu-id="9ae31-124">L'utilisation de Netsh.exe est illustrée dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9ae31-124">The following is an example of using Netsh.exe.</span></span>  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="9ae31-125">Netsh.exe, consultez [comment utiliser l’outil Netsh.exe et les commutateurs de ligne de commande](http://go.microsoft.com/fwlink/?LinkId=97877).</span><span class="sxs-lookup"><span data-stu-id="9ae31-125"> Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](http://go.microsoft.com/fwlink/?LinkId=97877).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ae31-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ae31-126">See Also</span></span>  
 [<span data-ttu-id="9ae31-127">Modèles Visual Studio WCF</span><span class="sxs-lookup"><span data-stu-id="9ae31-127">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [<span data-ttu-id="9ae31-128">WCF Service Host (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="9ae31-128">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [<span data-ttu-id="9ae31-129">Client test WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="9ae31-129">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
