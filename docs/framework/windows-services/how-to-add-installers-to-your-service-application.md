---
title: "How to: Add Installers to Your Service Application | Microsoft Docs"
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
  - "Windows Service applications, deploying"
  - "installation components, adding to services"
  - "installers, adding to services"
  - "Windows Service applications, adding installers"
  - "services, adding installers"
  - "ServiceInstaller class, adding installers to services"
  - "ServiceProcessInstaller class, adding installers to services"
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
caps.latest.revision: 14
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 14
---
# How to: Add Installers to Your Service Application
Visual Studio vous est fourni avec des composants qui vous permettent d'installer les ressources associées à vos applications de service.  Les composants d'installation inscrivent chaque service dans le système sur lequel il doit être installé et avertissent le Gestionnaire de contrôle des services de son existence.  Lorsque vous travaillez avec une application de service, vous pouvez sélectionner un lien dans la fenêtre Propriétés pour automatiquement ajouter les programmes d'installation à votre projet.  
  
> [!NOTE]
>  Les valeurs de propriété de votre service sont copiées de la classe de service dans la classe Installer.  Si vous mettez à jour la valeur de certaines propriétés dans la classe de service, la modification n'est pas automatiquement répercutée dans le programme d'installation.  
  
 Lorsque vous ajoutez un programme d'installation à votre projet, une nouvelle classe \(appelée par défaut `ProjectInstaller`\) est constituée dans le projet, et des instances des composants d'installation requis sont créées dans cette classe.  Cette classe centralise tous les composants d'installation nécessaires à votre projet.  Par exemple, si vous ajoutez un deuxième service à votre application, une deuxième classe Installer n'est pas créée lorsque vous cliquez sur le lien Ajouter le programme d'installation ; en revanche, le composant d'installation supplémentaire requis pour ce second service est ajouté à la classe existante.  
  
 Vous n'avez pas besoin d'écrire un code spécial dans les programmes d'installation pour que vos services s'installent correctement.  Toutefois, vous pouvez parfois avoir besoin de modifier le contenu des programmes d'installation pour ajouter certaines fonctionnalités au processus d'installation.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour ajouter des programmes d'installation à votre application de service  
  
1.  Dans l'**Explorateur de solutions**, activez le mode **Design** pour le service pour lequel vous voulez ajouter un composant d'installation.  
  
2.  Cliquez sur l'arrière\-plan du concepteur pour sélectionner le service lui\-même plutôt que son contenu.  
  
3.  Avec le concepteur dans le focus, cliquez avec le bouton droit, puis cliquez sur **Ajouter le programme d'installation**.  
  
     Une nouvelle classe, `ProjectInstaller`, et deux composants d'installation, <xref:System.ServiceProcess.ServiceProcessInstaller> et <xref:System.ServiceProcess.ServiceInstaller>, sont ajoutés à votre projet, et les valeurs de propriété du service sont copiées dans ces composants.  
  
4.  Cliquez sur le composant <xref:System.ServiceProcess.ServiceInstaller> et vérifiez que la valeur de la propriété <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> est identique à celle de la propriété <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> du service.  
  
5.  Pour connaître le mode de démarrage du service, cliquez sur le composant <xref:System.ServiceProcess.ServiceInstaller> et attribuez à la propriété <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> la valeur appropriée.  
  
    |Valeur|Résultat|  
    |------------|--------------|  
    |<xref:System.ServiceProcess.ServiceStartMode>|Le service doit être démarré manuellement après installation.  Pour plus d'informations, consultez [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).|  
    |<xref:System.ServiceProcess.ServiceStartMode>|Le service démarre automatiquement à chaque redémarrage de l'ordinateur.|  
    |<xref:System.ServiceProcess.ServiceStartMode>|Le service ne peut pas être démarré.|  
  
6.  Pour déterminer le contexte de sécurité dans lequel s'exécute le service, cliquez sur le composant <xref:System.ServiceProcess.ServiceProcessInstaller> et attribuez aux propriétés les valeurs appropriées.  Pour plus d'informations, consultez [How to: Specify the Security Context for Services](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md).  
  
7.  Substituez les méthodes pour lesquelles vous devez effectuer un traitement personnalisé.  
  
8.  Exécutez les étapes 1 à 7 pour chaque service supplémentaire de votre projet.  
  
    > [!NOTE]
    >  Pour chaque service supplémentaire de votre projet, vous devez ajouter un autre composant <xref:System.ServiceProcess.ServiceInstaller> à la classe `ProjectInstaller` du projet.  Le composant <xref:System.ServiceProcess.ServiceProcessInstaller> ajouté à l'étape 3 fonctionne avec tous les programmes d'installation de service du projet.  
  
## Voir aussi  
 [Introduction to Windows Service Applications](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)   
 [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)   
 [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md)   
 [How to: Specify the Security Context for Services](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)