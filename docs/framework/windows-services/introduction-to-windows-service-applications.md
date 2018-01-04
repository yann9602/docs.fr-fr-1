---
title: Introduction aux applications de service Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ServiceController
helpviewer_keywords:
- Windows Service applications, deploying
- OnStop method
- OnPause method
- services, about services
- Service class, Windows Service applications
- framework services, creating services
- ServiceController components, about Windows services
- Win32OwnProcess service type
- services, lifetime
- OnContinue method
- Windows Service applications, about Windows Service applications
- services, states
- service states
- WaitForStatus method
- Win32ShareProcess service type
- Windows Service applications, lifetime
ms.assetid: 1b1b5e67-3ff3-40c0-8154-322cfd6ef0ae
caps.latest.revision: "17"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 613107a13820ad71b854dcba93f21c41f2a5fa5f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="introduction-to-windows-service-applications"></a>Introduction aux applications de service Windows
Les services Microsoft Windows, anciennement appelés services NT, permettent de créer des applications exécutables longue qui s’exécutent dans leur propre session Windows. Ces services peuvent être démarrés automatiquement au démarrage de l’ordinateur, peut être suspendu et redémarré et n’affichent pas d’interface utilisateur. Ces fonctionnalités rendent services idéale pour une utilisation sur un serveur, ou chaque fois que vous avez besoin de fonctionnalités de durée d’exécution longue qui n’interfèrent pas avec d’autres utilisateurs qui travaillent sur le même ordinateur. Vous pouvez également exécuter des services dans le contexte de sécurité d’un compte d’utilisateur spécifique qui est différent de l’utilisateur connecté ou le compte d’ordinateur par défaut. Pour plus d’informations sur les services et les sessions Windows, consultez la documentation du Kit de développement logiciel Windows.  
  
 Vous pouvez facilement créer des services en créant une application qui est installée en tant que service. Par exemple, supposons que vous souhaitez analyser des données de compteur de performances et de réagir aux valeurs de seuil. Vous pourriez écrire une application de Service Windows qui écoute les données de compteur de performance, déployer l’application et commencer à collecte et à analyse des données.  
  
 Vous créez votre service tel qu’un projet Microsoft Visual Studio, définissez-y du code contrôlant les commandes pouvant être envoyée au service et les actions à effectuer lors de la réception de ces commandes. Incluent des commandes qui peuvent être envoyés à un service démarrage, suspension, reprise et arrêt du service ; Vous pouvez également exécuter des commandes personnalisées.  
  
 Une fois que vous créez et générez l’application, vous pouvez l’installer en exécutant l’utilitaire de ligne de commande InstallUtil.exe et en passant le chemin d’accès au fichier exécutable du service. Vous pouvez ensuite utiliser le **Gestionnaire de contrôle des Services** pour démarrer, arrêter, suspendre, reprendre et configurer votre service. Vous pouvez également exécuter la plupart de ces tâches dans le **Services** nœud **l’Explorateur de serveurs** ou à l’aide de la <xref:System.ServiceProcess.ServiceController> classe.  
  
## <a name="service-applications-vs-other-visual-studio-applications"></a>Les Applications de service vs. Autres Applications Visual Studio  
 Service applications fonctionnent différemment à partir de nombreux autres types de projet de plusieurs façons :  
  
-   Le fichier exécutable compilé créés dans un projet d’application de service doit être installé sur le serveur avant que le projet puisse fonctionner de manière explicite. Vous ne pouvez pas déboguer ou exécuter une application de service en appuyant sur F5 ou F11 ; Vous ne peut pas exécuter immédiatement d’un service ou une étape dans son code. Au lieu de cela, vous devez installer et démarrer votre service et puis attacher un débogueur au processus du service. Pour plus d’informations, consultez [Comment : déboguer des Applications de Service Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md).  
  
-   Contrairement à certains types de projets, vous devez créer des composants d’installation pour les applications de service. Les composants d’installation installer et inscrire le service sur le serveur et créer une entrée pour votre service avec Windows **Gestionnaire de contrôle des Services**. Pour plus d’informations, consultez [Comment : ajouter des programmes d’installation à votre Application de Service](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
-   Le `Main` méthode pour votre application de service doit émettre la commande Run pour les services de votre projet contient. Le `Run` méthode charge les services dans le **Gestionnaire de contrôle des Services** sur le serveur approprié. Si vous utilisez la **Services Windows** modèle de projet, cette méthode est automatiquement générée pour vous. Notez que le chargement d’un service n’est pas la même chose que le démarrage du service. « Service de durée de vie » ci-dessous pour plus d’informations, consultez.  
  
-   Applications de Service Windows s’exécutent dans une station Windows autre que la station interactive de l’utilisateur connecté. Une station de travail est un objet sécurisé qui contient un Presse-papiers, un ensemble d’atomes globaux et un groupe d’objets de bureau. Car la console du service Windows n’est pas une station interactive, boîtes de dialogue levée depuis une fenêtre d’application de service n’est pas visibles et peut-être provoquer votre programme cesse de répondre. De même, les messages d’erreur doivent être enregistrés dans le journal des événements Windows plutôt que déclenchés dans l’interface utilisateur.  
  
     Les classes de service Windows pris en charge par le .NET Framework ne permettent pas d’interaction avec les stations interactives, autrement dit, l’utilisateur connecté. Également, le .NET Framework n’inclut pas les classes qui représentent des stations et les bureaux. Si votre service Windows doit interagir avec d’autres stations, vous devez accéder à l’API Windows non managée. Pour plus d’informations, consultez la documentation du Kit de développement logiciel Windows.  
  
     L’interaction du service avec l’utilisateur ou d’autres stations doit être conçue avec soin pour inclure des scénarios tels qu’il est sans utilisateur connecté, ou l’utilisateur dispose d’un ensemble inattendu d’objets de bureau Windows. Dans certains cas, il peut être plus approprié d’écrire une application Windows qui s’exécute sous le contrôle de l’utilisateur.  
  
-   Applications de service Windows s’exécutent dans leur propre contexte de sécurité et sont démarrées avant l’utilisateur se connecte à l’ordinateur Windows sur lequel ils sont installés. Vous devez planifier avec soin le compte d’utilisateur pour exécuter le service ; un service s’exécutant sous le compte système possède plus de droits et privilèges à un compte d’utilisateur.  
  
## <a name="service-lifetime"></a>Durée de vie de service  
 Un service passe par plusieurs états internes dans sa durée de vie. Tout d’abord, le service est installé sur le système sur lequel il s’exécutera. Ce processus exécute les programmes d’installation pour le projet de service et charge le service dans le **Gestionnaire de contrôle des Services** pour cet ordinateur. Le **Gestionnaire de contrôle des Services** est l’utilitaire central fourni par Windows pour administrer les services.  
  
 Une fois que le service a été chargé, il doit être démarré. Démarrage du service autorise à commence à fonctionner. Vous pouvez démarrer un service à partir de la **Gestionnaire de contrôle des Services**, à partir de **l’Explorateur de serveurs**, ou à partir du code en appelant le <xref:System.ServiceProcess.ServiceController.Start%2A> (méthode). Le <xref:System.ServiceProcess.ServiceController.Start%2A> méthode transmet le traitement à l’application <xref:System.ServiceProcess.ServiceBase.OnStart%2A> méthode et traite le code que vous avez défini.  
  
 Un service en cours d’exécution peut exister dans cet état indéfiniment jusqu'à ce qu’il soit arrêté ou suspendu ou jusqu'à l’arrêt de l’ordinateur. Un service peut exister dans un des trois états de base : <xref:System.ServiceProcess.ServiceControllerStatus.Running>, <xref:System.ServiceProcess.ServiceControllerStatus.Paused>, ou <xref:System.ServiceProcess.ServiceControllerStatus.Stopped>. Le service peut également signaler l’état d’une commande en attente : <xref:System.ServiceProcess.ServiceControllerStatus.ContinuePending>, <xref:System.ServiceProcess.ServiceControllerStatus.PausePending>, <xref:System.ServiceProcess.ServiceControllerStatus.StartPending>, ou <xref:System.ServiceProcess.ServiceControllerStatus.StopPending>. Ces états indiquent qu’une commande a été émise, telle qu’une commande pour suspendre un service en cours d’exécution, mais n’a pas encore été exécutée. Vous pouvez interroger la <xref:System.ServiceProcess.ServiceController.Status%2A> pour connaître l’état d’un service, ou utilisez le <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A> pour effectuer une action lorsqu’un de ces États se produit.  
  
 Vous pouvez suspendre, arrêter ou redémarrer un service à partir de la **Gestionnaire de contrôle des Services**, à partir de **l’Explorateur de serveurs**, ou en appelant des méthodes dans le code. Chacune de ces actions peut appeler une procédure associée dans le service (<xref:System.ServiceProcess.ServiceBase.OnStop%2A>, <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, ou <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>), dans laquelle vous pouvez définir un traitement supplémentaire à effectuer lorsque le service change d’état.  
  
## <a name="types-of-services"></a>Types de Services  
 Il existe deux types de services, que vous pouvez créer dans Visual Studio à l’aide de .NET Framework. Les services qui sont le seul service dans un processus de type <xref:System.ServiceProcess.ServiceType.Win32OwnProcess>. Les services qui partagent un processus avec un autre service de type <xref:System.ServiceProcess.ServiceType.Win32ShareProcess>. Vous pouvez récupérer le type de service en interrogeant le <xref:System.ServiceProcess.ServiceController.ServiceType%2A> propriété.  
  
 Vous pouvez parfois voir les autres types de service si vous interrogez des services existants qui n’ont pas été créés dans Visual Studio. Pour plus d’informations, consultez le <xref:System.ServiceProcess.ServiceType>.  
  
## <a name="services-and-the-servicecontroller-component"></a>Services et le composant ServiceController  
 Le <xref:System.ServiceProcess.ServiceController> composant est utilisé pour se connecter à un service installé et de manipuler son état ; en utilisant un <xref:System.ServiceProcess.ServiceController> composant, vous pouvez démarrer et arrêter un service, suspendre et poursuivre son exécution et envoyer des commandes personnalisées à un service. Toutefois, vous n’avez pas besoin d’utiliser un <xref:System.ServiceProcess.ServiceController> composant lorsque vous créez une application de service. En fait, dans la plupart des cas votre <xref:System.ServiceProcess.ServiceController> composant doit se trouver dans une application séparée de l’application de service Windows qui définit votre service.  
  
 Pour plus d'informations, consultez <xref:System.ServiceProcess.ServiceController>.  
  
## <a name="requirements"></a>Configuration requise  
  
-   Les services doivent être créés dans un **Service Windows** projet d’application ou un autre projet compatible .NET Framework qui génère un fichier .exe lors de la génération et hérite de la <xref:System.ServiceProcess.ServiceBase> classe.  
  
-   Les projets contenant des services Windows doivent avoir des composants d’installation pour le projet et ses services. Cela peut être accompli facilement à partir de la **propriétés** fenêtre. Pour plus d’informations, consultez [Comment : ajouter des programmes d’installation à votre Application de Service](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Applications de service Windows](../../../docs/framework/windows-services/index.md)  
 [Architecture de programmation d’une application de service](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 [Guide pratique pour créer des services Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Guide pratique pour installer et désinstaller des services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Guide pratique pour démarrer des services](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Guide pratique pour déboguer les applications de service Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Procédure pas à pas : création d’une application de service Windows dans le Concepteur de composants](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 [Guide pratique pour ajouter des programmes d’installation à votre application de service](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
