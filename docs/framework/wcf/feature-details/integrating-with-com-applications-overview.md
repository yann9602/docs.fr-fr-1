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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6ae704ad9542c162b1c37f3eb9edf31f864cd42e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="integrating-with-com-applications-overview"></a>Vue d'ensemble de l'intégration à des applications COM
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] offre aux développeurs de code managé un environnement riche qui facilite la création d'applications connectées. Toutefois, si vous avez beaucoup investi dans un code COM non managé et que vous ne souhaitez pas effectuer de migration, vous pouvez toujours intégrer les services Web [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] directement dans ce code grâce au moniker de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Le moniker de service peut être utilisé à partir d'une large gamme d'environnements de développement COM, tels qu'Office VBA, Visual Basic 6.0 ou Visual C++ 6.0.  
  
> [!NOTE]
>  Le moniker de service utilise un canal de communication [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour toutes les communications. Les mécanismes de sécurité et d'identification de ce canal diffèrent de ceux utilisés sur les proxys standard COM et DCOM. En outre, le moniker de service utilisant un canal de communication [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], le délai par défaut est d'une seconde pour tous les appels.  
  
 Le moniker de service est utilisé avec la fonction `GetObject` afin d'offrir au développeur de code non managé une approche fortement typée, spécifique au COM permettant d'appeler des services Web [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Ces appels nécessitent une définition locale, visible par COM du contrat de service Web [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ainsi que la liaison à utiliser. Comme les autres clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], le moniker de service doit construire un canal typé pour le service considéré, bien que cette construction devienne visible par le programmeur COM lors du premier appel de la méthode.  
  
 À l'instar des autres clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], lors de l'utilisation du moniker, les applications spécifient l'adresse, la liaison et le contrat pour pouvoir communiquer avec le service requis. Le contrat peut être spécifié (au choix) comme suit :  
  
-   Contrat typé : le contrat est enregistré sur l'ordinateur client sous la forme d'un type visible par COM.  
  
-   Contrat WSDL : le contrat est fourni sous forme de document WSDL.  
  
-   Contrat MEX : le contrat est récupéré pendant l'exécution depuis un point de terminaison d'échange de métadonnées (Metadata Exchange, MEX).  
  
## <a name="parameters-supported-by-the-service-moniker"></a>Paramètres pris en charge par le moniker de service  
 Le tableau suivant contient les paramètres pris en charge par le moniker de service.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`address`|Adresse URL du service.|  
|`binding`|Nom de la section de liaison à partir de la configuration d’application.|  
|`bindingConfiguration`|Instance de liaison nommée à partir de la section de liaison nommée.|  
|`contract`|Identificateur d'interface (IID) qui représente le contrat de service ou le nom de contrat (obtenu à partir de l'échange MEX).|  
|`wsdl`|Document WSDL qui offre une autre définition pour le contrat.|  
|`spnIdentity`|Identité de nom principal de serveur (Server Principal Name, SPN) à utiliser pour communiquer avec le service.|  
|`upnIdentity`|Identité de nom principal d'utilisateur (User Principal Name, UPN) à utiliser pour communiquer avec le service.|  
|`dnsIdentity`|Identité DNS à utiliser pour communiquer avec le service.|  
|`mexAddress`|Adresse URL du point de terminaison MEX du service.|  
|`mexBinding`|Nom de section de liaison depuis la configuration d’application avec laquelle se connecter au point de terminaison MEX.|  
|`mexBindingConfiguration`|Instance de liaison nommée à partir de la section de liaison nommée avec laquelle se connecter au point de terminaison MEX.|  
|`bindingNamespace`|Espace de noms du nom de section de liaison obtenu à partir de l’échange MEX récupéré.|  
|`contractNamespace`|Espace de noms du contrat obtenu à partir de l'échange MEX récupéré.|  
|`mexSpnIdentity`|Identité SPN à utiliser pour communiquer avec le point de terminaison MEX.|  
|`mexUpnIdentity`|Identité UPN à utiliser pour communiquer avec le point de terminaison MEX.|  
|`mexDnsIdentity`|Identité DNS à utiliser pour communiquer avec le point de terminaison MEX.|  
|`serializer`|Indiquez le type de sérialiseur utilisé : « xml » ou « contrat de données ».|  
  
> [!NOTE]
>  Même lorsqu'il est utilisé avec des clients entièrement COM, le moniker de service nécessite que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et le .NET Framework 2.0 pris en charge soient installés sur l'ordinateur client. Il est également essentiel que les applications clientes qui utilisent le moniker de service chargent la version appropriée de l'exécution .NET Framework. Lorsque le moniker de service est utilisé dans le cadre d'applications Office, un fichier de configuration peut s'avérer nécessaire afin d'assurer la chargement de la version d'infrastructure adéquate. Par exemple, pour Excel, vous devez insérer le texte suivant dans un fichier Excel.exe.config, puis enregistrer ce fichier dans le même répertoire que le fichier Excel.exe :  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  `<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : inscrire et configurer un Moniker de Service](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
