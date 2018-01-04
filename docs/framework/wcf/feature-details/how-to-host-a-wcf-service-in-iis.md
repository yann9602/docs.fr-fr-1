---
title: "Comment : héberger un service WCF dans IIS"
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
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3b23d3f69d52299fcf3ca8b5ff56d0c4673026b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>Comment : héberger un service WCF dans IIS
Cette rubrique décrit les étapes de base requises pour créer un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hébergé dans les services IIS (Internet Information Services). Dans cette rubrique, on suppose que vous connaissez IIS et que vous comprenez la manière d'utiliser l'outil d'administration IIS pour créer et gérer des applications IIS. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]IIS voir [Internet Information Services](http://go.microsoft.com/fwlink/?LinkId=132449). Un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exécuté dans l'environnement IIS tire totalement parti des fonctionnalités IIS telles que le recyclage de processus, l'arrêt en cas d'inactivité, le contrôle d'état de processus et l'activation basée sur message. Cette option d'hébergement requiert que les services IIS soient configurés correctement, mais n'exige pas l'écriture d'un code d'hébergement dans le cadre de l'application. Vous pouvez utiliser l'hébergement IIS uniquement avec un transport HTTP.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Comment [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] interagir, consultez [Services WCF et ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]configuration de la sécurité, consultez [sécurité](../../../../docs/framework/wcf/feature-details/security.md).  
  
 Pour la copie de la source de cet exemple, consultez [d’hébergement à l’aide en ligne de Code IIS](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).  
  
### <a name="to-create-a-service-hosted-by-iis"></a>Pour créer un service hébergé par IIS  
  
1.  Vérifiez que les services IIS sont installés et s'exécutent sur votre ordinateur. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]installation et configuration d’IIS voir [installation et configuration d’IIS 7.0](http://go.microsoft.com/fwlink/?LinkID=132128)  
  
2.  Créez un dossier pour vos fichiers d'application, appelé « IISHostedCalcService », assurez-vous que [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] a accès au contenu du dossier et utilisez l'outil d'administration IIS pour créer une application IIS située physiquement dans ce répertoire d'application. Lors de la création d'un alias pour le répertoire de l'application, utilisez « IISHostedCalc ».  
  
3.  Créez un fichier appelé « service.svc » dans le répertoire de l'application. Modifiez ce fichier en ajoutant le code suivant @ServiceHost élément.  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4.  Créez un sous-répertoire App_Code dans le répertoire de l'application.  
  
5.  Créez un fichier de code nommé Service.cs dans le sous-répertoire App_Code.  
  
6.  Ajoutez les instructions using suivantes en tête du fichier Service.cs.  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7.  Ajoutez la déclaration d'espace de noms suivante à la suite des instructions using.  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8.  Définissez le contrat de service à l'intérieur de la déclaration d'espace de noms, tel qu'indiqué dans le code suivant.  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. Implémentez le contrat de service après la définition du contrat de service, tel qu'indiqué dans le code suivant.  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. Créez un fichier nommé « Web.config » dans le répertoire de l'application et ajoutez le code de configuration suivant dans le fichier. Au moment de l'exécution, l'infrastructure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise les informations pour construire un point de terminaison avec lequel les applications clientes peuvent communiquer.  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     L'exemple spécifie explicitement les points de terminaison dans le fichier de configuration. Si vous n'ajoutez pas de points de terminaison au service, le runtime ajoute les points de terminaison par défaut. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]voir de points de terminaison, les liaisons et comportements par défaut [Configuration simplifiée](../../../../docs/framework/wcf/simplified-configuration.md) et [simplifié la Configuration des Services WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
11. Pour vous assurer que le service est hébergé correctement, ouvrez une instance d'Internet Explorer et naviguez jusqu'à l'URL du service : `http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>Exemple  
 L'intégralité du code pour le service de calculatrice hébergé IIS est présentée ci-dessous.  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>Voir aussi  
 [Hébergement dans les services IIS (Internet Information Services)](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Hébergement de services](../../../../docs/framework/wcf/hosting-services.md)  
 [Services WCF et ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [Sécurité](../../../../docs/framework/wcf/feature-details/security.md)  
 [Fonctionnalités d’hébergement de Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
