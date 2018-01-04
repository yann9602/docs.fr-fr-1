---
title: "Comment : spécifier le contexte de sécurité des services"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 9ce65358f6d63414dbe6798d3cc2464ee2741980
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-security-context-for-services"></a>Comment : spécifier le contexte de sécurité des services
Par défaut, les services s’exécutent dans un contexte de sécurité autre que celle de l’utilisateur connecté. Les services s’exécutés dans le contexte du compte système par défaut, appelée `LocalSystem`, ce qui leur donne différents privilèges d’accès aux ressources système que l’utilisateur. Vous pouvez modifier ce comportement pour spécifier un autre compte d’utilisateur sous lequel votre service doit s’exécuter.  
  
 Vous définissez le contexte de sécurité en manipulant le <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> propriété du processus dans lequel le service s’exécute. Cette propriété vous permet de définir le service à un des quatre types de comptes :  
  
-   `User`, ce qui entraîne le système demande un nom d’utilisateur valide et un mot de passe lorsque le service est installé et s’exécute dans le contexte d’un compte spécifié par un utilisateur unique sur le réseau ;  
  
-   `LocalService`, qui s’exécute dans le contexte d’un compte qui agit comme un utilisateur non privilégié sur l’ordinateur local et présente des informations d’identification anonymes à tout serveur distant ;  
  
-   `LocalSystem`, qui s’exécute dans le contexte d’un compte qui fournit des privilèges locaux étendus et présente les informations d’identification de l’ordinateur à tout serveur distant ;  
  
-   `NetworkService`, qui s’exécute dans le contexte d’un compte qui agit comme un utilisateur non privilégié sur l’ordinateur local et présente des informations d’identification de l’ordinateur à tout serveur distant.  
  
 Pour plus d’informations, consultez l’énumération <xref:System.ServiceProcess.ServiceAccount>.  
  
### <a name="to-specify-the-security-context-for-a-service"></a>Pour spécifier le contexte de sécurité pour un service  
  
1.  Après avoir créé votre service, ajoutez les programmes d’installation nécessaires pour celui-ci. Pour plus d’informations, consultez [Comment : ajouter des programmes d’installation à votre Application de Service](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
2.  Dans le concepteur, accédez à la `ProjectInstaller` classe, puis cliquez sur le programme d’installation du processus de service pour le service que vous utilisez.  
  
    > [!NOTE]
    >  Pour chaque application de service, il existe au moins deux composants d’installation dans le `ProjectInstaller` classe : un qui installe les processus pour tous les services dans le projet et un programme d’installation pour chaque service de l’application. Dans ce cas, vous souhaitez sélectionner <xref:System.ServiceProcess.ServiceProcessInstaller>.  
  
3.  Dans le **propriétés** , configurez la <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> la valeur appropriée.  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction aux applications de service Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Guide pratique pour ajouter des programmes d’installation à votre application de service](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Guide pratique pour créer des services Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
