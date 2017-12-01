---
title: "Configuration des services Internet (IIS) 7.0 pour Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 185fa5e641a1834a7c5f7906b5e5cf84dacaa9f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a>Configuration des services Internet (IIS) 7.0 pour Windows Communication Foundation
Les services Internet (IIS) 7.0 sont conçus de manière modulaire vous permettant ainsi d'installer uniquement les composants dont vous avez besoin. Leur conception s'appuie sur la nouvelle technologie multi-composant orientée manifeste, utilisée pour la première fois dans [!INCLUDE[wv](../../../../includes/wv-md.md)]. [!INCLUDE[iisver](../../../../includes/iisver-md.md)] comporte plus de 40 composants autonomes pouvant être installés indépendamment. Cela permet aux professionnels de l'informatique de personnaliser plus facilement leur installation en fonction de leurs besoins. Cette rubrique contient des instructions permettant de configurer [!INCLUDE[iisver](../../../../includes/iisver-md.md)] en vue d'une utilisation avec [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et d'identifier les composants requis.  
  
## <a name="minimal-installation-installing-was"></a>Installation minimale : installation du service WAS  
 L'installation minimale de [!INCLUDE[iisver](../../../../includes/iisver-md.md)] consiste à installer uniquement le service WAS (Windows Process Activation Service). Le service WAS, qui est une fonctionnalité autonome, est la seule fonctionnalité de [!INCLUDE[iisver](../../../../includes/iisver-md.md)] disponible, quel que soit le système d'exploitation [!INCLUDE[wv](../../../../includes/wv-md.md)] utilisé (Home Basic, Home Premium, Business, and Ultimate and Enterprise).  
  
 À partir du Panneau de configuration, cliquez sur **programmes** puis cliquez sur **ou désactiver des fonctionnalités Windows d’activer** sous **programmes et fonctionnalités**, le composant WAS s’affiche dans la liste comme dans l’illustration suivante.  
  
 ![Activer la boîte de dialogue désactiver ou de fonctionnalités sur](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")  
  
 Cette fonctionnalité intègre les sous-composants suivants :  
  
-   Environnement .NET  
  
-   Interfaces API de configuration  
  
-   Modèle de processus  
  
 Si vous sélectionnez le nœud racine WAS, le **modèle de processus** sous-nœud est activée par défaut. Remarque : dans le cadre de la présente installation, seul le service WAS est installé car la prise en charge d’un serveur web n’est pas assurée.  
  
 Pour rendre [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ou n’importe quel [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application fonctionne, vérifiez le **de l’environnement .NET** case à cocher. Cela signifie que tous les composants du service WAS sont requis pour assurer le bon fonctionnement de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et de [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Ces composants sont automatiquement activés dès lors que l'un d'entre eux est installé.  
  
## <a name="iis-70-default-installation"></a>IIS 7.0 : installation par défaut  
 En vérifiant la **Internet Information Services** fonctionnalité, certaines des sous-nœuds sont automatiquement vérifiés comme indiqué dans l’illustration suivante.  
  
 ![Paramètres par défaut pour les fonctionnalités IIS 7.0](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")  
  
 Il s'agit de l'installation par défaut de [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. Dans le cadre de cette installation, vous pouvez utiliser [!INCLUDE[iisver](../../../../includes/iisver-md.md)] pour fournir du contenu statique (pages HTML et autres contenus, par exemple). Toutefois, vous ne pouvez pas exécuter [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ni d'applications CGI ni de services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hôtes.  
  
## <a name="iis-70-installation-with-aspnet-support"></a>IIS 7.0 : installation avec prise en charge ASP.NET  
 Vous devez installer [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pour que [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] fonctionne sur IIS 7.0. Après avoir vérifié **ASP.NET**, votre écran doit ressembler à l’illustration suivante.  
  
 ![Des paramètres obligatoires Asp.NET](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")  
  
 Il s'agit de l'environnement minimal requis permettant aux applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ainsi qu'aux applications [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] de fonctionner dans [!INCLUDE[iisver](../../../../includes/iisver-md.md)].  
  
## <a name="iis-70-installation-with-iis-60-compatibility-components"></a>IIS 7.0 : installation avec les composants de compatibilité IIS 6.0  
 Lors de l’installation [!INCLUDE[iisver](../../../../includes/iisver-md.md)] sur un système avec Visual Studio 2005 ou certaines autres scripts d’automatisation ou certains outils (tels que Adsutil.vbs) qui configurent les applications virtuelles qui utilisent [!INCLUDE[iis601](../../../../includes/iis601-md.md)] métabase API, assurez-vous de vérifier le [!INCLUDE[iis601](../../../../includes/iis601-md.md)]  **Outils de script**. Cette opération vérifie automatiquement les autres sous-nœuds de [!INCLUDE[iis601](../../../../includes/iis601-md.md)] **Management Compatibility**. Cette opération effectuée, votre écran doit se présenter comme illustré sur l'image suivante.  
  
 ![Paramètres de compatibilité IIS 6.0 Management](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")  
  
 Grâce à cette installation, vous disposez de tous les éléments requis pour pouvoir utiliser les fonctionnalités [!INCLUDE[iisver](../../../../includes/iisver-md.md)], [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ainsi que les exemples disponibles sur le Web.  
  
## <a name="request-limits"></a>Limites de la demande  
 Sur [!INCLUDE[wv](../../../../includes/wv-md.md)] avec IIS 7, la valeur par défaut des paramètres `maxUri` et `maxQueryStringSize` a été modifiée. Par défaut, le filtrage de demande dans IIS 7.0 autorise une URL d'une longueur de 4096 caractères et une longueur de chaîne de 2048 caractères. Pour modifier ces valeurs par défaut, ajoutez l'élément XML suivant au fichier App.config.  
  
 `<system.webServer>`  
  
 `<security>`  
  
 `<requestFiltering>`  
  
 `<requestLimits maxUrl="8192" maxQueryString="8192" />`  
  
 `</requestFiltering>`  
  
 `</security>`  
  
 `</system.webServer>`  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture d’Activation WAS](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)  
 [Configuration du service WAS pour une utilisation avec WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [Comment : installer et configurer les composants d’Activation WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)  
 [Fonctionnalités d’hébergement de Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
