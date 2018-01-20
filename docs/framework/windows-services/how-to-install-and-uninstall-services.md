---
title: "Comment : installer et désinstaller des services"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, Windows Services
- installation, Windows Services
- uninstalling Windows Services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
caps.latest.revision: "19"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 1fcbc8e7a84b16d244561e0cd69f8661236e63de
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-install-and-uninstall-services"></a>Comment : installer et désinstaller des services
Si vous développez un service Windows à l'aide du .NET Framework, vous pouvez installer rapidement votre application de service à l'aide d'un utilitaire de ligne de commande appelé InstallUtil.exe. Si vous êtes développeur et que vous souhaitez commercialiser un service Windows que les utilisateurs peuvent installer et désinstaller, vous devez utiliser InstallShield. Consultez [déploiement de Windows Installer](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
> [!WARNING]
>  Si vous voulez désinstaller un service de votre ordinateur, ne suivez pas les étapes décrites dans cet article. Au lieu de cela, déterminez quel programme ou package logiciel a installé le service, puis choisissez **Ajout/Suppression de programmes** dans le panneau de configuration pour désinstaller ce programme. Notez que de nombreux services font partie intégrante de Windows. Si vous les supprimez, vous pouvez rendre le système instable.  
  
 Pour utiliser les étapes décrites dans cet article, vous devez d'abord ajouter un programme d'installation de service à votre service Windows. Consultez [procédure pas à pas : création d’une fenêtre de Service Application dans le Concepteur de composants](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
 Les projets de service Windows ne peuvent pas être exécutés directement à partir de l'environnement de développement Visual Studio en appuyant sur F5. C'est pourquoi le service du projet doit être installé avant de pouvoir exécuter le projet.  
  
> [!TIP]
>  Vous pouvez lancer **l’Explorateur de serveurs** et vérifiez que votre service a été installé ou désinstallé. Pour plus d’informations, consultez Comment : accès et initialiser l’Explorateur de base de données de l’Explorateur de serveurs.  
  
### <a name="to-install-your-service-manually"></a>Pour installer votre service manuellement  
  
1.  Sur les fenêtres **Démarrer** menu ou **Démarrer** écran, choisissez **Visual Studio** , **Visual Studio Tools**, **développeur Invite de commandes**.  
  
     Une invite de commandes Visual Studio s'affiche.  
  
2.  Accédez au répertoire dans lequel se trouve le fichier exécutable compilé de votre projet.  
  
3.  Exécutez InstallUtil.exe à partir de l'invite de commandes avec le fichier exécutable de votre projet comme paramètre :  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     Si vous utilisez l'invite de commandes de Visual Studio, InstallUtil.exe doit se trouver dans le répertoire système. Si ce n'est pas le cas, vous pouvez ajouter le chemin d'accès ou utiliser le chemin d'accès complet à l'appeler. Cet outil est installé avec le .NET Framework, et son chemin d'accès est `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`. Par exemple, pour la version 32 bits de .NET Framework 4 ou 4.5.*, si votre répertoire d'installation de Windows est C:\Windows, le chemin d'accès est `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`. Pour obtenir la version 64 bits de .NET Framework 4 ou 4.5. \*, le chemin d’accès par défaut est `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.  
  
### <a name="to-uninstall-your-service-manually"></a>Pour désinstaller votre service manuellement  
  
1.  Sur les fenêtres **Démarrer** menu ou **Démarrer** écran, choisissez **Visual Studio**, **Visual Studio Tools**, **développeur Invite de commandes**.  
  
     Une invite de commandes Visual Studio s'affiche.  
  
2.  Exécutez InstallUtil.exe à partir de l'invite de commandes avec la sortie de votre projet comme paramètre :  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  Parfois, après la suppression de l'exécutable d'un service est supprimée, le service peut encore être présent dans le Registre. Dans ce cas, utilisez la commande [sc delete](http://technet.microsoft.com/library/cc742045.aspx) pour supprimer l’entrée pour le service à partir du Registre.  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction aux applications de service Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Guide pratique pour créer des services Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Guide pratique pour ajouter des programmes d’installation à votre application de service](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Installutil.exe (outil Installer)](../../../docs/framework/tools/installutil-exe-installer-tool.md)
