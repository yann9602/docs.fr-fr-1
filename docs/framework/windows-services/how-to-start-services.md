---
title: "Comment : démarrer des services"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
caps.latest.revision: "16"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: e4f93da8a2a5be00d798d64caba0f54bfd71ceb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-start-services"></a>Comment : démarrer des services
Une fois un service est installé, il doit être démarré. Appelez le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> méthode sur la classe de service. En règle générale, le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> méthode définit le travail utile effectué par le service. Après le démarrage d’un service, il reste actif jusqu'à ce qu’il est suspendu ou arrêté.  
  
 Services peuvent être configurés pour démarrer automatiquement ou manuellement. Un service qui démarre automatiquement démarrera lorsque l’ordinateur sur lequel il est installé est tension ou redémarré. Un utilisateur doit démarrer un service qui démarre manuellement.  
  
> [!NOTE]
>  Par défaut, les services créés avec [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] sont configurés pour démarrer manuellement.  
  
 Il existe plusieurs façons, vous pouvez démarrer manuellement un service — à partir de **l’Explorateur de serveurs**, à partir de la **Gestionnaire de contrôle des Services**, ou à partir du code à l’aide d’un composant appelé le <xref:System.ServiceProcess.ServiceController>.  
  
 Vous définissez la <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> propriété sur la <xref:System.ServiceProcess.ServiceInstaller> classe pour déterminer si un service doit être démarré manuellement ou automatiquement.  
  
### <a name="to-specify-how-a-service-should-start"></a>Pour spécifier la manière dont un service doit démarrer.  
  
1.  Après avoir créé votre service, ajoutez les programmes d’installation nécessaires pour celui-ci. Pour plus d’informations, consultez [Comment : ajouter des programmes d’installation à votre Application de Service](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
2.  Dans le concepteur, cliquez sur le programme d’installation de service pour le service que vous utilisez.  
  
3.  Dans le **propriétés** , configurez le <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> propriété à une des opérations suivantes :  
  
    |Pour installer votre service|Définissez cette valeur|  
    |----------------------------------|--------------------|  
    |Lorsque l’ordinateur est redémarré.|**Automatique**|  
    |Lorsqu’une action explicite de l’utilisateur démarre le service|**Manuelle**|  
  
    > [!TIP]
    >  Pour empêcher le démarrage du tout votre service, vous pouvez définir le <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> propriété **désactivé**. Vous pouvez procéder de la sorte si vous prévoyez de redémarrer un serveur plusieurs fois et que vous souhaitez gagner du temps en empêchant les services qui seraient normalement de démarrer.  
  
    > [!NOTE]
    >  Ces autres propriétés et peuvent être modifiées après l’installation du service.  
  
     Il existe plusieurs façons de démarrer un service qui a son <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> processus défini sur **manuel** : à partir de **l’Explorateur de serveurs**, à partir de la **Gestionnaire de contrôle des Services Windows**, ou à partir du code. Il est important de noter que toutes ces méthodes démarrent le service dans le contexte de la **Gestionnaire de contrôle des Services**; **L’Explorateur de serveurs** et méthodes de démarrage du service par programmation agissent en réalité sur le contrôleur.  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a>Pour démarrer manuellement un service à partir de l’Explorateur de serveurs  
  
1.  Dans **l’Explorateur de serveurs**, ajoutez le serveur souhaité s’il n’est pas déjà répertorié. Pour plus d’informations, consultez Comment : accès et initialiser l’Explorateur de base de données de l’Explorateur de serveurs.  
  
2.  Développez le **Services** nœud, puis recherchez le service que vous souhaitez démarrer.  
  
3.  Cliquez sur le nom du service, puis cliquez sur **Démarrer**.  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a>Pour démarrer manuellement un service de gestionnaire de contrôle des Services  
  
1.  Ouvrez le **Gestionnaire de contrôle des Services** en effectuant l’une des opérations suivantes :  
  
    -   Dans Windows XP et 2000 Professionnel, avec le bouton droit **poste** sur le bureau, puis cliquez sur **gérer**. Dans la boîte de dialogue qui s’affiche, développez le **Services et Applications** nœud.  
  
         \- ou -  
  
    -   Dans Windows Server 2003 et Windows 2000 Server, cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **outils d’administration**, puis cliquez sur **Services**.  
  
        > [!NOTE]
        >  Dans Windows NT version 4.0, vous pouvez ouvrir cette boîte de dialogue à partir de **le panneau de configuration**.  
  
     Vous devez maintenant voir votre service répertorié dans le **Services** section de la fenêtre.  
  
2.  Sélectionnez votre service dans la liste, faites un clic droit, puis cliquez sur **Démarrer**.  
  
### <a name="to-manually-start-a-service-from-code"></a>Pour démarrer manuellement un service à partir du code  
  
1.  Créez une instance de la <xref:System.ServiceProcess.ServiceController> classe et le configurer pour interagir avec le service que vous souhaitez administrer.  
  
2.  Appelez la méthode <xref:System.ServiceProcess.ServiceController.Start%2A> pour démarrer le service.  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction aux Applications de Service Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Comment : créer des Services Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Comment : ajouter des programmes d’installation à votre Application de Service](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
