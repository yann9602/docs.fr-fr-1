---
title: "Vue d'ensemble de l'intégration à des applications COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4e995fc66a925cb0ebe272c9dceca1ba63b9459d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="91cd3-102">Vue d'ensemble de l'intégration à des applications COM</span><span class="sxs-lookup"><span data-stu-id="91cd3-102">Integrating with COM Applications Overview</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="91cd3-103"> offre aux développeurs de code managé un environnement riche qui facilite la création d'applications connectées.</span><span class="sxs-lookup"><span data-stu-id="91cd3-103"> provides the managed code developer with a rich environment for creating connected applications.</span></span> <span data-ttu-id="91cd3-104">Toutefois, si vous avez beaucoup investi dans un code COM non managé et que vous ne souhaitez pas effectuer de migration, vous pouvez toujours intégrer les services Web [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] directement dans ce code grâce au moniker de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="91cd3-104">However, if you have a substantial investment in unmanaged COM-based code and do not want to migrate, you can still integrate [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web services directly into your existing code by using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker.</span></span> <span data-ttu-id="91cd3-105">Le moniker de service peut être utilisé à partir d'une large gamme d'environnements de développement COM, tels qu'Office VBA, Visual Basic 6.0 ou Visual C++ 6.0.</span><span class="sxs-lookup"><span data-stu-id="91cd3-105">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91cd3-106">Le moniker de service utilise un canal de communication [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour toutes les communications.</span><span class="sxs-lookup"><span data-stu-id="91cd3-106">The service moniker uses a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] communication channel for all communication.</span></span> <span data-ttu-id="91cd3-107">Les mécanismes de sécurité et d'identification de ce canal diffèrent de ceux utilisés sur les proxys standard COM et DCOM.</span><span class="sxs-lookup"><span data-stu-id="91cd3-107">The security and identity mechanisms for that channel differ from those used in standard COM and DCOM proxies.</span></span> <span data-ttu-id="91cd3-108">En outre, le moniker de service utilisant un canal de communication [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], le délai par défaut est d'une seconde pour tous les appels.</span><span class="sxs-lookup"><span data-stu-id="91cd3-108">In addition, because the service moniker uses a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] communication channel the default timeout period is one minute for all calls.</span></span>  
  
 <span data-ttu-id="91cd3-109">Le moniker de service est utilisé avec la fonction `GetObject` afin d'offrir au développeur de code non managé une approche fortement typée, spécifique au COM permettant d'appeler des services Web [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="91cd3-109">The service moniker is used with the `GetObject` function to provide the unmanaged developer with a strongly-typed, COM-specific approach for calling [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web services.</span></span> <span data-ttu-id="91cd3-110">Ces appels nécessitent une définition locale, visible par COM du contrat de service Web [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ainsi que la liaison à utiliser.</span><span class="sxs-lookup"><span data-stu-id="91cd3-110">This requires a local, COM-visible definition of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web service contract and the binding that is to be used.</span></span> <span data-ttu-id="91cd3-111">Comme les autres clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], le moniker de service doit construire un canal typé pour le service considéré, bien que cette construction devienne visible par le programmeur COM lors du premier appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="91cd3-111">Like other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients, the service moniker must construct a typed channel to the service, though this channel construction occurs transparently to the COM programmer on the first method call.</span></span>  
  
 <span data-ttu-id="91cd3-112">À l'instar des autres clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], lors de l'utilisation du moniker, les applications spécifient l'adresse, la liaison et le contrat pour pouvoir communiquer avec le service requis.</span><span class="sxs-lookup"><span data-stu-id="91cd3-112">In common with other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients, when using the moniker, applications specify the address, binding and contract to communicate with a service.</span></span> <span data-ttu-id="91cd3-113">Le contrat peut être spécifié (au choix) comme suit :</span><span class="sxs-lookup"><span data-stu-id="91cd3-113">The contract can be specified in one of the following ways:</span></span>  
  
-   <span data-ttu-id="91cd3-114">Contrat typé : le contrat est enregistré sur l'ordinateur client sous la forme d'un type visible par COM.</span><span class="sxs-lookup"><span data-stu-id="91cd3-114">Typed contract – the contract is registered as a COM visible type on the client machine.</span></span>  
  
-   <span data-ttu-id="91cd3-115">Contrat WSDL : le contrat est fourni sous forme de document WSDL.</span><span class="sxs-lookup"><span data-stu-id="91cd3-115">WSDL contract – the contract is supplied in the form of a WSDL document.</span></span>  
  
-   <span data-ttu-id="91cd3-116">Contrat MEX : le contrat est récupéré pendant l'exécution depuis un point de terminaison d'échange de métadonnées (Metadata Exchange, MEX).</span><span class="sxs-lookup"><span data-stu-id="91cd3-116">MEX contract – the contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="parameters-supported-by-the-service-moniker"></a><span data-ttu-id="91cd3-117">Paramètres pris en charge par le moniker de service</span><span class="sxs-lookup"><span data-stu-id="91cd3-117">Parameters Supported by the Service Moniker</span></span>  
 <span data-ttu-id="91cd3-118">Le tableau suivant contient les paramètres pris en charge par le moniker de service.</span><span class="sxs-lookup"><span data-stu-id="91cd3-118">The following table shows the parameters that are supported by the service moniker.</span></span>  
  
|<span data-ttu-id="91cd3-119">Paramètre</span><span class="sxs-lookup"><span data-stu-id="91cd3-119">Parameter</span></span>|<span data-ttu-id="91cd3-120">Description</span><span class="sxs-lookup"><span data-stu-id="91cd3-120">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="91cd3-121">Adresse URL du service.</span><span class="sxs-lookup"><span data-stu-id="91cd3-121">URL location of the service.</span></span>|  
|`binding`|<span data-ttu-id="91cd3-122">Nom de la section de liaison à partir de la configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="91cd3-122">Binding section name from the application configuration.</span></span>|  
|`bindingConfiguration`|<span data-ttu-id="91cd3-123">Instance de liaison nommée à partir de la section de liaison nommée.</span><span class="sxs-lookup"><span data-stu-id="91cd3-123">Named binding instance from within the named binding section.</span></span>|  
|`contract`|<span data-ttu-id="91cd3-124">Identificateur d'interface (IID) qui représente le contrat de service ou le nom de contrat (obtenu à partir de l'échange MEX).</span><span class="sxs-lookup"><span data-stu-id="91cd3-124">Interface identifier (IID) that represents the service contract or the contract name (from MEX).</span></span>|  
|`wsdl`|<span data-ttu-id="91cd3-125">Document WSDL qui offre une autre définition pour le contrat.</span><span class="sxs-lookup"><span data-stu-id="91cd3-125">WSDL document that provides an alternative form of contract definition.</span></span>|  
|`spnIdentity`|<span data-ttu-id="91cd3-126">Identité de nom principal de serveur (Server Principal Name, SPN) à utiliser pour communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="91cd3-126">Server principal name (SPN) identity to be used to communicate with the service.</span></span>|  
|`upnIdentity`|<span data-ttu-id="91cd3-127">Identité de nom principal d'utilisateur (User Principal Name, UPN) à utiliser pour communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="91cd3-127">User principal name (UPN) identity to be used to communicate with the service.</span></span>|  
|`dnsIdentity`|<span data-ttu-id="91cd3-128">Identité DNS à utiliser pour communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="91cd3-128">DNS identity to be used to communicate with the service.</span></span>|  
|`mexAddress`|<span data-ttu-id="91cd3-129">Adresse URL du point de terminaison MEX du service.</span><span class="sxs-lookup"><span data-stu-id="91cd3-129">URL location of the Metadata Exchange (MEX) endpoint of the service.</span></span>|  
|`mexBinding`|<span data-ttu-id="91cd3-130">Nom de section de liaison depuis la configuration d’application avec laquelle se connecter au point de terminaison MEX.</span><span class="sxs-lookup"><span data-stu-id="91cd3-130">Binding section name from the application configuration to connect with the MEX endpoint.</span></span>|  
|`mexBindingConfiguration`|<span data-ttu-id="91cd3-131">Instance de liaison nommée à partir de la section de liaison nommée avec laquelle se connecter au point de terminaison MEX.</span><span class="sxs-lookup"><span data-stu-id="91cd3-131">Named binding instance from within the named binding section to connect with the MEX endpoint.</span></span>|  
|`bindingNamespace`|<span data-ttu-id="91cd3-132">Espace de noms du nom de section de liaison obtenu à partir de l’échange MEX récupéré.</span><span class="sxs-lookup"><span data-stu-id="91cd3-132">Namespace of the binding section name from the retrieved MEX.</span></span>|  
|`contractNamespace`|<span data-ttu-id="91cd3-133">Espace de noms du contrat obtenu à partir de l'échange MEX récupéré.</span><span class="sxs-lookup"><span data-stu-id="91cd3-133">Namespace of the contract from the retrieved MEX.</span></span>|  
|`mexSpnIdentity`|<span data-ttu-id="91cd3-134">Identité SPN à utiliser pour communiquer avec le point de terminaison MEX.</span><span class="sxs-lookup"><span data-stu-id="91cd3-134">Server principal name (SPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexUpnIdentity`|<span data-ttu-id="91cd3-135">Identité UPN à utiliser pour communiquer avec le point de terminaison MEX.</span><span class="sxs-lookup"><span data-stu-id="91cd3-135">User principal name (UPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexDnsIdentity`|<span data-ttu-id="91cd3-136">Identité DNS à utiliser pour communiquer avec le point de terminaison MEX.</span><span class="sxs-lookup"><span data-stu-id="91cd3-136">DNS identity to be used to communicate with the MEX endpoint.</span></span>|  
|`serializer`|<span data-ttu-id="91cd3-137">Indiquez le type de sérialiseur utilisé : « xml » ou « contrat de données ».</span><span class="sxs-lookup"><span data-stu-id="91cd3-137">Specify the use of either the "xml" or "datacontract" serializer.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="91cd3-138">Même lorsqu'il est utilisé avec des clients entièrement COM, le moniker de service nécessite que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et le .NET Framework 2.0 pris en charge soient installés sur l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="91cd3-138">Even when used with entirely COM-based clients, the service moniker requires [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and the supporting .NET Framework 2.0 to be installed on the client computer.</span></span> <span data-ttu-id="91cd3-139">Il est également essentiel que les applications clientes qui utilisent le moniker de service chargent la version appropriée de l'exécution .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="91cd3-139">It is also critical that client applications that use the service moniker load the appropriate version of the .NET Framework runtime.</span></span> <span data-ttu-id="91cd3-140">Lorsque le moniker de service est utilisé dans le cadre d'applications Office, un fichier de configuration peut s'avérer nécessaire afin d'assurer la chargement de la version d'infrastructure adéquate.</span><span class="sxs-lookup"><span data-stu-id="91cd3-140">When using the moniker within Office applications, a configuration file may be required to ensure that the correct framework version is loaded.</span></span> <span data-ttu-id="91cd3-141">Par exemple, pour Excel, vous devez insérer le texte suivant dans un fichier Excel.exe.config, puis enregistrer ce fichier dans le même répertoire que le fichier Excel.exe :</span><span class="sxs-lookup"><span data-stu-id="91cd3-141">For example, with Excel, the following text should be placed in a file called Excel.exe.config in the same directory as the Excel.exe file:</span></span>  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  <span data-ttu-id="91cd3-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span><span class="sxs-lookup"><span data-stu-id="91cd3-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span></span>  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a><span data-ttu-id="91cd3-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91cd3-143">See Also</span></span>  
 [<span data-ttu-id="91cd3-144">Comment : inscrire et configurer un Moniker de Service</span><span class="sxs-lookup"><span data-stu-id="91cd3-144">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
