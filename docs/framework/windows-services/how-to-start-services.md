---
title: "How to: Start Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows Service applications, starting"
  - "services, starting"
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
caps.latest.revision: 16
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 14
---
# How to: Start Services
Une fois le service installé, il doit être démarré.  Pour ce faire, appelez la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> de la classe de service.  En général, la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> définit le travail utile effectué par le service.  Une fois démarré, un service reste actif jusqu'à ce qu'il soit suspendu ou arrêté.  
  
 Les services peuvent être configurés pour démarrer automatiquement ou manuellement.  Un service à démarrage automatique est lancé lorsque l'ordinateur sur lequel il est installé est mis sous tension ou redémarré.  Un service à démarrage manuel doit être démarré par un utilisateur.  
  
> [!NOTE]
>  Par défaut, les services créés avec [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] sont configurés pour démarrer manuellement.  
  
 Il existe plusieurs manières de démarrer manuellement un service — à partir de l'**Explorateur de serveurs**, à partir du **Gestionnaire de contrôle des services** ou à partir du code à l'aide d'un composant appelé <xref:System.ServiceProcess.ServiceController>.  
  
 Pour déterminer si un service doit démarrer automatiquement ou manuellement, définissez la propriété <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> de la classe <xref:System.ServiceProcess.ServiceInstaller>.  
  
### Pour spécifier le mode de démarrage d'un service  
  
1.  Après avoir créé le service, ajoutez les programmes d'installation nécessaires.  Pour plus d'informations, consultez [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
2.  Dans le Concepteur, cliquez sur le programme d'installation de service correspondant à votre service.  
  
3.  Dans la fenêtre **Propriétés**, attribuez à la propriété <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> l'une des valeurs suivantes :  
  
    |Pour installer votre service|Indiquez la valeur|  
    |----------------------------------|------------------------|  
    |Au redémarrage de l'ordinateur.|**Automatique**|  
    |Lorsque l'utilisateur accomplit une action précise.|**Manual**|  
  
    > [!TIP]
    >  Pour inhiber le démarrage de votre service, définissez la propriété <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> en lui attribuant la valeur **Disabled**.  Par exemple, si vous prévoyez de redémarrer plusieurs fois un serveur, vous gagnerez du temps en inhibant le démarrage des services qui devraient normalement démarrer.  
  
    > [!NOTE]
    >  Cette propriété, au même titre que d'autres, peut être modifiée après l'installation du service.  
  
     Il existe plusieurs manières de démarrer un service dont le processus <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> est défini avec la valeur **Manual** : à partir de l'**Explorateur de serveurs**, à partir du **Gestionnaire de contrôle des services Windows** ou à partir du code.  Il est important de noter que toutes ces méthodes démarrent le service dans le contexte du **Gestionnaire de contrôle des services** ; l'**Explorateur de serveurs** et les méthodes de démarrage par programmation agissent en réalité sur le contrôleur.  
  
### Pour démarrer manuellement un service à partir de l'Explorateur de serveurs  
  
1.  Dans l'**Explorateur de serveurs**, ajoutez le serveur souhaité s'il ne figure pas déjà dans la liste.  Pour plus d'informations, consultez [How to: Access and Initialize Server Explorer\/Database Explorer](../Topic/How%20to:%20Access%20and%20Initialize%20Server%20Explorer-Database%20Explorer.md).  
  
2.  Développez le nœud **Services et localisez le service à démarrer**.  
  
3.  Cliquez avec le bouton droit sur le nom du service, puis cliquez sur **Démarrer**.  
  
### Pour démarrer manuellement un service à partir du Gestionnaire de contrôle des services  
  
1.  Ouvrez le **Gestionnaire de contrôle des services** en utilisant l'une des méthodes suivantes :  
  
    -   Dans Windows XP et 2000 Professionnel, cliquez avec le bouton droit sur **Poste de travail** sur le Bureau, puis cliquez sur **Gérer**.  Dans la boîte de dialogue qui s'affiche, développez le nœud **Services et applications**.  
  
         \- ou \-  
  
    -   Dans Windows 2000 Server et Windows Server 2003, cliquez sur **Démarrer**, pointez sur **Programmes**, cliquez sur **Outils d'administration**, puis sur **Services**.  
  
        > [!NOTE]
        >  Dans Windows NT version 4.0, vous pouvez ouvrir cette boîte de dialogue à partir du **Panneau de configuration**.  
  
     Votre service devrait maintenant apparaître dans la liste affichée dans la section **Services** de la fenêtre.  
  
2.  Sélectionnez votre service dans la liste, cliquez dessus avec le bouton droit, puis cliquez sur **Démarrer**.  
  
### Pour démarrer manuellement un service à partir du code  
  
1.  Créez une instance de la classe <xref:System.ServiceProcess.ServiceController> et configurez\-la pour qu'elle interagisse avec le service à administrer.  
  
2.  Appelez la méthode <xref:System.ServiceProcess.ServiceController.Start%2A> pour démarrer le service.  
  
## Voir aussi  
 [Introduction to Windows Service Applications](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)   
 [How to: Create Windows Services](../../../docs/framework/windows-services/how-to-create-windows-services.md)   
 [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)   
 [How to: Access and Initialize Server Explorer\/Database Explorer](../Topic/How%20to:%20Access%20and%20Initialize%20Server%20Explorer-Database%20Explorer.md)