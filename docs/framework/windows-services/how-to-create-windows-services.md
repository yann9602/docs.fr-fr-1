---
title: "Comment : créer des services Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
caps.latest.revision: "18"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 7d93f8543b9e6e370827f5a666315d562e28ee76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-windows-services"></a>Comment : créer des services Windows
Lorsque vous créez un service, vous pouvez utiliser un modèle de projet Visual Studio appelé **Service Windows**. Ce modèle accomplit automatiquement pour vous une grande part du travail : il référence les classes et les espaces de noms appropriés, définit l'héritage à partir de la classe de base des services et substitue les méthodes que vous êtes le plus susceptible de vouloir substituer.  
  
> [!WARNING]
>  Le modèle de projet Services Windows n'est pas disponible dans l'édition Express de Visual Studio.  
  
 Pour créer un service fonctionnel, vous devez, au minimum :  
  
-   définir la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> ;  
  
-   ajouter les programmes d'installation nécessaires à votre application de service ;  
  
-   substituer et spécifier le code des méthodes <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et <xref:System.ServiceProcess.ServiceBase.OnStop%2A> pour personnaliser le comportement de votre service.  
  
### <a name="to-create-a-windows-service-application"></a>Pour créer une application de service Windows  
  
1.  Créer un **Windows Service** projet.  
  
    > [!NOTE]
    >  Pour obtenir des instructions sur l’écriture d’un service sans utiliser le modèle, consultez [Comment : écrire des Services par programmation](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).  
  
2.  Dans le **propriétés** , configurez le <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> propriété pour votre service.  
  
     ![Définissez la propriété ServiceName. ] (../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")  
  
    > [!NOTE]
    >  La valeur de la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> doit toujours correspondre au nom enregistré dans les classes Installer. Si vous modifiez cette propriété, vous devez également mettre à jour la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> des classes Installer.  
  
3.  Définissez le fonctionnement de votre service à l'aide des propriétés suivantes.  
  
    |Propriété|Paramètre|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|`True` pour indiquer que le service acceptera des demandes d'arrêt ; `false` pour empêcher tout arrêt du service.|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|`True` pour indiquer que le service doit recevoir une notification en cas d'arrêt de l'ordinateur sur lequel il s'exécute, ce qui lui permet d'appeler la procédure <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>.|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|`True` pour indiquer que le service acceptera les demandes de suspension ou de redémarrage ; `false` pour empêcher une suspension et un redémarrage du service.|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|`True`pour indiquer que le service peut gérer la notification des modifications apportées à l’état d’alimentation de l’ordinateur ; `false` pour empêcher le service d’être notifié de ces modifications.|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|`True` pour écrire des entrées à caractère informatif dans le journal des événements de l'application lorsque votre service effectue une action ; `false` pour désactiver cette fonctionnalité. Pour plus d’informations, consultez [Comment : journal des informations sur les Services](../../../docs/framework/windows-services/how-to-log-information-about-services.md). **Remarque :** par défaut, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> a la valeur `true`.|  
  
    > [!NOTE]
    >  Lorsque <xref:System.ServiceProcess.ServiceBase.CanStop%2A> ou <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> sont définies sur `false`, le **Service Control Manager** désactive les options de menu correspondant à arrêter, suspendre ou reprendre le service.  
  
4.  Accédez à l'éditeur de code et indiquez le traitement souhaité pour les procédures <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et <xref:System.ServiceProcess.ServiceBase.OnStop%2A>.  
  
5.  Substituez toutes les autres méthodes pour lesquelles vous voulez définir des fonctionnalités.  
  
6.  Ajoutez les programmes d'installation nécessaires à votre application de service. Pour plus d’informations, consultez [Comment : ajouter des programmes d’installation à votre Application de Service](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
7.  Générez votre projet en sélectionnant **générer la Solution** à partir de la **générer** menu.  
  
    > [!NOTE]
    >  N'appuyez pas sur la touche F5 pour exécuter votre projet : vous ne pouvez pas exécuter un projet de service de cette manière.  
  
8.  Installez le service. Pour plus d'informations, consultez [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction aux applications de service Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Guide pratique pour écrire les services par programmation](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)  
 [Guide pratique pour ajouter des programmes d’installation à votre application de service](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Guide pratique pour enregistrer des informations relatives aux services](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [Guide pratique pour démarrer des services](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Guide pratique pour spécifier le contexte de sécurité des services](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)  
 [Guide pratique pour installer et désinstaller des services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Procédure pas à pas : création d’une application de service Windows dans le Concepteur de composants](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
