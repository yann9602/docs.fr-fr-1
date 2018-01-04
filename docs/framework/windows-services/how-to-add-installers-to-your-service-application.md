---
title: "Comment : ajouter des programmes d'installation à votre application de service"
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
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
caps.latest.revision: "14"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 0dcb666f317ab285ae0156d2df16947f71665aee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-installers-to-your-service-application"></a>Comment : ajouter des programmes d'installation à votre application de service
Visual Studio est fourni à des composants qui peuvent installer des ressources associées à vos applications de service. Composants d’installation inscrivent chaque service dans le système auquel il est en cours d’installation et informe le Gestionnaire de contrôle des Services de l’existence du service. Lorsque vous travaillez avec une application de service, vous pouvez sélectionner un lien dans la fenêtre Propriétés pour ajouter automatiquement les programmes d’installation appropriées à votre projet.  
  
> [!NOTE]
>  Les valeurs de propriété de votre service sont copiées à partir de la classe de service à la classe de programme d’installation. Si vous mettez à jour les valeurs de propriété sur la classe de service, ils ne sont pas automatiquement répercutées dans le programme d’installation.  
  
 Lorsque vous ajoutez un programme d’installation à votre projet, une nouvelle classe (qui, par défaut, se nomme `ProjectInstaller`) est créé dans le projet et les instances de l’installation appropriée des composants sont créés dans celui-ci. Cette classe sert de point central pour tous les composants d’installation a besoin de votre projet. Par exemple, si vous ajoutez un deuxième service à votre application et cliquez sur le lien Ajouter le programme d’installation, une deuxième classe de programme d’installation n’est pas créée ; au lieu de cela, le composant d’installation supplémentaires nécessaires pour le deuxième service est ajouté à la classe existante.  
  
 Vous n’avez pas besoin écrire un code spécial dans les programmes d’installation pour que vos services ne s’installe correctement. Toutefois, vous devrez peut-être parfois modifier le contenu des programmes d’installation si vous avez besoin ajouter des fonctionnalités spéciales pour le processus d’installation.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-installers-to-your-service-application"></a>Pour ajouter des programmes d’installation à votre application de service  
  
1.  Dans **l’Explorateur de solutions**, accès **conception** mode pour le service pour lequel vous souhaitez ajouter un composant d’installation.  
  
2.  Cliquez sur l’arrière-plan du concepteur pour sélectionner le service lui-même, plutôt que son contenu.  
  
3.  Avec le concepteur dans le focus, avec le bouton droit, puis cliquez sur **ajouter le programme d’installation**.  
  
     Une nouvelle classe, `ProjectInstaller`et deux composants d’installation, <xref:System.ServiceProcess.ServiceProcessInstaller> et <xref:System.ServiceProcess.ServiceInstaller>, sont ajoutés à votre projet et les valeurs de propriété pour le service sont copiés vers les composants.  
  
4.  Cliquez sur le <xref:System.ServiceProcess.ServiceInstaller> composant et vérifiez que la valeur de la <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> est définie sur la même valeur que le <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> propriété sur le service lui-même.  
  
5.  Pour déterminer le mode de démarrage de votre service, cliquez sur le <xref:System.ServiceProcess.ServiceInstaller> composant et définissez le <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> propriété la valeur appropriée.  
  
    |Value|Résultat|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|Le service doit être démarré manuellement après l’installation. Pour plus d’informations, consultez [Comment : démarrer des Services](../../../docs/framework/windows-services/how-to-start-services.md).|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|Le service démarre par lui-même chaque fois que l’ordinateur redémarre.|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|Le service ne peut pas être démarré.|  
  
6.  Pour déterminer le contexte de sécurité dans lequel s’exécute le service, cliquez sur le <xref:System.ServiceProcess.ServiceProcessInstaller> composant et définissez les valeurs de propriété appropriée. Pour plus d’informations, consultez [Comment : spécifier le contexte de sécurité pour les Services](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md).  
  
7.  Substituez toutes les méthodes pour lesquelles vous devez effectuer un traitement personnalisé.  
  
8.  Effectuez les étapes 1 à 7 pour chaque service supplémentaire de votre projet.  
  
    > [!NOTE]
    >  Pour chaque service supplémentaire de votre projet, vous devez ajouter un <xref:System.ServiceProcess.ServiceInstaller> composant du projet `ProjectInstaller` classe. Le <xref:System.ServiceProcess.ServiceProcessInstaller> composant ajouté à l’étape 3 fonctionne avec tous les programmes d’installation de service individuels dans le projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction aux applications de service Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Guide pratique pour installer et désinstaller des services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Guide pratique pour démarrer des services](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Guide pratique pour spécifier le contexte de sécurité des services](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)
