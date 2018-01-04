---
title: Prise en charge de plusieurs liaisons de site IIS
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8dcd6a5e6204b1a629c1ee1e2ddfb9b263fa8054
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="supporting-multiple-iis-site-bindings"></a>Prise en charge de plusieurs liaisons de site IIS
Lorsque vous hébergez un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dans les services IIS 7.0 (Internet Information Services), vous souhaitez peut-être fournir plusieurs adresses de base utilisant le même protocole sur le même site. Cela permet au même service de répondre à plusieurs URI différents. C'est utile lorsque vous souhaitez héberger un service qui écoute sur http://www.contoso.com et http://contoso.com. Il est également utile de créer un service qui a une adresse de base pour les utilisateurs internes et une autre adresse de base pour les utilisateurs externes. Par exemple : http://internal.contoso.com et http://www.contoso.com.  
  
> [!NOTE]
>  Ces fonctionnalités ne sont disponibles qu'en utilisant le protocole HTTP.  
  
## <a name="multiple-base-addresses"></a>Plusieurs adresses de base  
 Cette fonctionnalité n'est disponible qu'aux services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergés sous IIS. Cette fonction n'est pas activée par défaut. Pour l’activer, vous devez ajouter le `multipleSiteBindingsEnabled` d’attribut à la <`serviceHostingEnvironment`> élément dans votre fichier Web.config du fichier et affectez-lui la valeur `true`, comme illustré dans l’exemple suivant.  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 Lors de l'hébergement d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans les services IIS, IIS crée une adresse de base automatiquement, basée sur l'URI du répertoire virtuel qui contient l'application. Vous pouvez ajouter des adresses de base supplémentaires utilisant le même protocole, à l'aide du gestionnaire des services IIS pour ajouter une ou plusieurs liaisons à votre site Web. Pour chaque liaison, spécifiez un protocole (HTTP ou HTTPS), une adresse IP, un port et un nom d’hôte. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]à l’aide du Gestionnaire des Services Internet, consultez [Gestionnaire des services Internet (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164057). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]l’ajout de liaisons à un site, consultez [créer un Site Web (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164060)  
  
 La spécification de plusieurs adresses de base pour le même site affecte le contenu de la page d'aide [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], le schéma d'importation et les informations WSDL/MEX générées par le service. La page d'aide [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] affiche la ligne de commande à utiliser pour générer un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui peut communiquer avec le service. Cette ligne de commande contient uniquement la première adresse spécifiée dans la liaison IIS pour le site web. De même, lors de l'importation du schéma, seule la première adresse de base spécifiée dans la liaison IIS est utilisée. Les données WSDL et MEX contiennent toutes les adresses de base spécifiées dans les liaisons IIS.  
  
> [!WARNING]
>  Cela signifie que si un service possède deux adresses de base, une pour les utilisateurs internes et l'autre pour les utilisateurs externes, les deux sont spécifiées dans les informations WSDL/MEX générées par le service.
