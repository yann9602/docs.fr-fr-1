---
title: "How to: Specify the Security Context for Services | Microsoft Docs"
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
  - "Windows Service applications, security"
  - "security [Visual Studio], contexts"
  - "contexts, Visual Studio security"
  - "security [Visual Studio], service applications"
  - "ServiceProcessInstaller class, security context"
  - "services, security"
  - "ServiceInstaller class, security context"
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
caps.latest.revision: 10
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 10
---
# How to: Specify the Security Context for Services
Par défaut, les services s'exécutent dans un contexte de sécurité différent de celui de l'utilisateur connecté.  Les services s'exécutent dans le contexte du compte système par défaut, appelé `LocalSystem`, qui leur confère des privilèges d'accès aux ressources système différents de ceux qui sont accordés à l'utilisateur.  Vous pouvez modifier ce comportement en spécifiant un compte d'utilisateur différent de celui dans lequel votre service devrait normalement s'exécuter.  
  
 Pour définir le contexte de sécurité, utilisez la propriété <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> du processus dans lequel s'exécute le service.  Cette propriété vous permet d'attribuer au service l'un des quatre types de comptes suivants :  
  
-   `User`, qui indique au système qu'il doit demander un nom d'utilisateur et un mot de passe valides lorsque le service est installé et s'exécute dès lors qu'un compte est spécifié par un utilisateur unique sur le réseau ;  
  
-   `LocalService`, qui s'exécute dans le contexte d'un compte agissant en tant qu'utilisateur non privilégié sur l'ordinateur local, et qui présente les informations d'identification anonymes à un serveur distant quelconque ;  
  
-   `LocalSystem`, qui s'exécute dans le contexte d'un compte qui fournit des privilèges locaux étendus, et présente les informations d'identification de l'ordinateur à un serveur distant quelconque ;  
  
-   `NetworkService`, qui s'exécute dans le contexte d'un compte agissant en tant qu'utilisateur non privilégié sur l'ordinateur local, et qui présente les informations d'identification de l'ordinateur à un serveur distant quelconque.  
  
 Pour plus d'informations, consultez l'énumération <xref:System.ServiceProcess.ServiceAccount>.  
  
### Pour spécifier le contexte de sécurité d'un service  
  
1.  Après avoir créé le service, ajoutez les programmes d'installation nécessaires.  Pour plus d’informations, consultez [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
2.  Dans le Concepteur, accédez à la classe `ProjectInstaller` et cliquez sur le programme d'installation de processus de service correspondant à votre service.  
  
    > [!NOTE]
    >  Pour chaque application de service, la classe `ProjectInstaller` comprend au moins deux composants d'installation : un qui installe les processus pour tous les services du projet et un autre pour chaque service contenu dans l'application.  Dans le cas présent, vous voulez sélectionner <xref:System.ServiceProcess.ServiceProcessInstaller>.  
  
3.  Dans la fenêtre **Propriétés**, affectez la valeur appropriée à <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A>.  
  
## Voir aussi  
 [Introduction to Windows Service Applications](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)   
 [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)   
 [How to: Create Windows Services](../../../docs/framework/windows-services/how-to-create-windows-services.md)