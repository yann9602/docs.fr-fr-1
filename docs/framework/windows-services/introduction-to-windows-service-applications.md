---
title: "Introduction to Windows Service Applications | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ServiceController"
helpviewer_keywords: 
  - "Windows Service applications, deploying"
  - "OnStop method"
  - "OnPause method"
  - "services, about services"
  - "Service class, Windows Service applications"
  - "framework services, creating services"
  - "ServiceController components, about Windows services"
  - "Win32OwnProcess service type"
  - "services, lifetime"
  - "OnContinue method"
  - "Windows Service applications, about Windows Service applications"
  - "services, states"
  - "service states"
  - "WaitForStatus method"
  - "Win32ShareProcess service type"
  - "Windows Service applications, lifetime"
ms.assetid: 1b1b5e67-3ff3-40c0-8154-322cfd6ef0ae
caps.latest.revision: 17
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 17
---
# Introduction to Windows Service Applications
Les services Microsoft Windows, précédemment appelés « services NT », vous permettent de créer des applications à durée d'exécution longue s'exécutant dans leurs propres sessions Windows.  Ces services peuvent être automatiquement démarrés en même temps que l'ordinateur, suspendus puis redémarrés et ne présentent pas d'interface utilisateur.  Ces fonctionnalités rendent ces services parfaitement adaptés à une utilisation sur un serveur ou lorsque vous avez besoin d'une fonctionnalité à période d'activité longue n'interférant pas avec les autres utilisateurs travaillant sur le même ordinateur.  Vous pouvez également exécuter des services dans le contexte de sécurité d'un compte d'utilisateur particulier, autre que celui de l'utilisateur connecté ou de l'ordinateur par défaut.  Pour plus d'informations sur les services et sessions Windows, consultez la documentation du kit de développement SDK Windows dans MSDN Library.  
  
 Vous pouvez aisément concevoir des services en créant une application que vous installerez en tant que service.  Supposons que vous souhaitez surveiller le compteur de performance et réagir au dépassement de certains seuils.  Vous pouvez écrire une application de service Windows surveillant ce compteur, la déployer et commencer à collecter et à analyser des données.  
  
 Créez votre service en tant que projet Microsoft Visual Studio et définissez\-y du code contrôlant les commandes pouvant être envoyées au service et les actions à effectuer lors de la réception de ces commandes.  Les commandes pouvant être envoyées sont celles qui déclenchent le démarrage, l'interruption, le redémarrage et l'arrêt du service, ainsi que celles qui déclenchent l'exécution de commandes personnalisées.  
  
 Une fois l'application créée et générée, vous pouvez l'installer en exécutant l'utilitaire de ligne de commande InstallUtil.exe et en transmettant le chemin d'accès au fichier exécutable du service.  Vous pouvez ensuite utiliser le **Gestionnaire de contrôle des services** pour démarrer, arrêter, interrompre, redémarrer et configurer le service.  Vous pouvez également effectuer un grand nombre de ces tâches dans le nœud **Services** de l'**Explorateur de serveurs**, ou en faisant appel à la classe <xref:System.ServiceProcess.ServiceController>.  
  
## Applications de service et autres applications Visual Studio  
 Les applications de service présentent, par rapport à beaucoup d'autres types de projets, les différences de fonctionnement suivantes :  
  
-   Le fichier exécutable compilé qui est créé par un projet d'application de service doit être installé sur le serveur pour que le projet puisse fonctionner correctement.  Vous ne pouvez ni déboguer ni exécuter une application de service en appuyant sur F5 ou F11 ; vous ne pouvez ni exécuter un service, ni entrer dans son code de manière immédiate.  Vous devez d'abord installer et démarrer le service, puis attacher un débogueur à son processus.  Pour plus d'informations, consultez [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md).  
  
-   À la différence de certains types de projets, les applications de service imposent de créer des composants d'installation.  Ces composants installent et inscrivent le service sur le serveur et créent pour lui une entrée dans le **Gestionnaire de contrôle des services** Windows.  Pour plus d'informations, consultez [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
-   La méthode `Main` de votre application de service doit émettre la commande Run pour les services contenus dans votre projet.  La méthode `Run` charge les services dans le **Gestionnaire de contrôle des services** du serveur approprié.  Si vous utilisez le modèle de projet **Services Windows**, cette méthode est automatiquement générée pour vous.  Notez que le chargement et le démarrage d'un service sont deux choses différentes.  Pour plus d'informations, consultez la section « Durée de vie d'un service » ci\-dessous.  
  
-   Les applications de service Windows s'exécutent sur une station Windows autre que la station interactive de l'utilisateur connecté.  Une station Windows est un objet sécurisé comprenant un Presse\-papiers, un ensemble d'atomes globaux et un groupe d'objets desktop.  La station du service Windows n'étant pas une station interactive, les boîtes de dialogue appelées à partir d'une application de service Windows ne sont pas visibles et peuvent provoquer un blocage du programme.  De même, les messages d'erreur doivent être enregistrés dans le journal des événements Windows plutôt qu'affichés dans l'interface utilisateur.  
  
     Les classes de service Windows prises en charge par le .NET Framework ne prennent pas en charge l'interaction avec les stations interactives \(c'est\-à\-dire l'utilisateur connecté\).  Le .NET Framework n'inclut pas non plus de classe représentant les stations et les bureaux.  Si votre service Windows doit interagir avec d'autres stations, vous devez accéder à l'interface API Windows non managée.  Pour plus d'informations, consultez la documentation du Kit de développement SDK Windows.  
  
     L'interaction du service Windows avec la station de l'utilisateur ou d'autres stations doit être conçue correctement de façon à inclure des scénarios tels que l'absence d'utilisateur connecté ou la présence d'un ensemble d'objets desktop inattendu.  Dans certains cas, il est préférable d'écrire une application Windows s'exécutant sous le contrôle de l'utilisateur.  
  
-   Les applications de service Windows s'exécutent dans leur propre contexte de sécurité et démarrent avant que l'utilisateur ne se connecte à l'ordinateur Windows sur lequel elles sont installées.  Vous devez sélectionner avec soin le compte d'utilisateur dans lequel s'exécutera le service ; un service s'exécutant dans le compte système dispose de plus de droits et de privilèges qu'un compte d'utilisateur.  
  
## Durée de vie d'un service  
 Un service passe par différents stades pendant son cycle de vie.  D'abord, il est installé dans le système sur lequel il s'exécutera.  Ce processus exécute les programmes d'installation du projet de service et charge le service dans le **Gestionnaire de contrôle des services** de cet ordinateur.  Le **Gestionnaire de contrôle des services** est l'utilitaire central fourni par Windows pour l'administration des services.  
  
 Une fois le service chargé, il doit être démarré.  Le démarrage est une condition préalable indispensable à la mise en fonction du service.  Vous pouvez démarrer un service à partir du **Gestionnaire de contrôle des services**, de l'**Explorateur de serveurs** ou du code en appelant la méthode <xref:System.ServiceProcess.ServiceController.Start%2A>.  La méthode <xref:System.ServiceProcess.ServiceController.Start%2A> transmet le traitement à la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> de l'application et exécute le code que vous y avez défini.  
  
 Un service en exécution peut rester dans cet état jusqu'à ce qu'il soit arrêté ou suspendu ou jusqu'à ce que l'ordinateur soit lui\-même arrêté.  Un service peut prendre les trois états de base suivants : <xref:System.ServiceProcess.ServiceControllerStatus>, <xref:System.ServiceProcess.ServiceControllerStatus> ou <xref:System.ServiceProcess.ServiceControllerStatus>.  Le service peut également signaler l'état d'une commande en attente : <xref:System.ServiceProcess.ServiceControllerStatus>, <xref:System.ServiceProcess.ServiceControllerStatus>, <xref:System.ServiceProcess.ServiceControllerStatus> ou <xref:System.ServiceProcess.ServiceControllerStatus>.  Ces états indiquent qu'une commande a été émise, par exemple une commande de suspension d'un service, mais qu'elle n'a pas encore été exécutée.  Vous pouvez interroger <xref:System.ServiceProcess.ServiceController.Status%2A> pour connaître l'état d'un service ou utiliser <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A> pour effectuer une action lorsque l'un ou l'autre de ces états se manifeste.  
  
 Vous pouvez suspendre, arrêter ou redémarrer un service à partir du **Gestionnaire de contrôle des services**, de l'**Explorateur de serveurs** ou en appelant des méthodes dans le code.  Chacune de ces actions peut appeler une procédure associée du service \(<xref:System.ServiceProcess.ServiceBase.OnStop%2A>, <xref:System.ServiceProcess.ServiceBase.OnPause%2A> ou <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>\), dans laquelle vous pouvez définir un traitement supplémentaire qui s'effectue lorsque le service change d'état.  
  
## Types de services  
 Dans Visual Studio, le .NET Framework permet de créer deux types de services.  Les services qui constituent le seul service d'un processus prennent le type <xref:System.ServiceProcess.ServiceType>.  Les services qui partagent un processus prennent le type <xref:System.ServiceProcess.ServiceType>.  Vous pouvez récupérer le type d'un service en interrogeant la propriété <xref:System.ServiceProcess.ServiceController.ServiceType%2A>.  
  
 Vous pouvez parfois rencontrer d'autres types de services lorsque vous interrogez des services existants qui n'ont pas été créés dans Visual Studio.  Pour plus d'informations sur ce point, consultez <xref:System.ServiceProcess.ServiceType>.  
  
## Services et composant ServiceController  
 Le composant <xref:System.ServiceProcess.ServiceController> permet de se connecter à un service installé et de manipuler son état ; en utilisant un composant <xref:System.ServiceProcess.ServiceController>, vous pouvez démarrer et arrêter un service, suspendre et poursuivre son exécution, et lui envoyer des commandes personnalisées.  Toutefois, vous n'avez pas besoin d'utiliser un composant <xref:System.ServiceProcess.ServiceController> lorsque vous créez une application de service.  En fait, dans la plupart des cas, votre composant <xref:System.ServiceProcess.ServiceController> doit se trouver dans une application séparée de l'application de service Windows définissant votre service.  
  
 Pour plus d'informations, consultez <xref:System.ServiceProcess.ServiceController>.  
  
## Configuration requise  
  
-   Les services doivent être créés dans un projet d'application **Service Windows** ou dans un autre projet compatible .NET Framework qui génère un fichier .exe lorsqu'il est constitué et qui hérite de la classe <xref:System.ServiceProcess.ServiceBase>.  
  
-   Les projets qui contiennent des services Windows doivent disposer de composants d'installation destinés au projet et à ses services.  Cela peut aisément être accompli à partir de la fenêtre **Propriétés**.  Pour plus d'informations, consultez [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
## Voir aussi  
 [Windows Service Applications](../../../docs/framework/windows-services/index.md)   
 [Service Application Programming Architecture](../../../docs/framework/windows-services/service-application-programming-architecture.md)   
 [How to: Create Windows Services](../../../docs/framework/windows-services/how-to-create-windows-services.md)   
 [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)   
 [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md)   
 [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)   
 [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)   
 [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)