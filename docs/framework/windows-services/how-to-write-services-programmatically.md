---
title: "How to: Write Services Programmatically | Microsoft Docs"
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
  - "services, creating"
  - "Windows Service applications, creating"
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
caps.latest.revision: 21
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 21
---
# How to: Write Services Programmatically
Si vous choisissez de ne pas utiliser le modèle de projet de service Windows, vous pouvez développer vos propres services en configurant vous\-même l'héritage et d'autres éléments d'infrastructure.  Lorsque vous créez un service par programmation, vous devez accomplir les tâches suivantes que le modèle prendrait autrement en charge à votre place :  
  
-   Vous devez configurer votre classe de service de telle sorte qu'elle hérite de la classe <xref:System.ServiceProcess.ServiceBase>.  
  
-   Vous devez créer pour votre projet de service une méthode `Main` qui définit les services à exécuter et qui appelle pour eux la méthode <xref:System.ServiceProcess.ServiceBase.Run%2A>.  
  
-   Vous devez substituer les procédures <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et <xref:System.ServiceProcess.ServiceBase.OnStop%2A>, et fournir le code que vous voulez qu'elles exécutent.  
  
### Pour créer un service par programmation  
  
1.  Créez un projet vide et une référence aux espaces de noms nécessaires en suivant ces étapes :  
  
    1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références** et cliquez sur **Ajouter une référence**.  
  
    2.  Sous l'onglet **.NET Framework**, placez\-vous sur **System.dll** et cliquez sur **Sélectionner**.  
  
    3.  Placez\-vous sur **System.Diagnostics.dll** et cliquez sur **Sélectionner**.  
  
    4.  Cliquez sur **OK**.  
  
2.  Ajoutez une classe et configurez\-la pour qu'elle hérite de <xref:System.ServiceProcess.ServiceBase> :  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3.  Ajoutez le code suivant pour configurer votre classe de service :  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4.  Créez une méthode `Main` pour votre classe et utilisez\-la pour définir le service que votre classe contiendra ; `userService1` est le nom de la classe :  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5.  Substituez la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et définissez le traitement que vous voulez lancer au démarrage de votre service.  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6.  Substituez toutes les méthodes pour lesquelles vous voulez définir un traitement personnalisé et écrivez du code pour déterminer les actions que le service doit accomplir dans chaque cas.  
  
7.  Ajoutez les programmes d'installation nécessaires à votre application de service.  Pour plus d'informations, consultez [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
8.  Générez votre projet en sélectionnant **Générer la solution** dans le menu **Générer**.  
  
    > [!NOTE]
    >  N'appuyez pas sur la touche F5 pour exécuter le projet ; il n'est pas possible d'exécuter un projet de service de cette manière.  
  
9. Créez un projet d'installation et des actions personnalisées pour installer votre service.  Pour obtenir un exemple, consultez [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
10. Installez le service.  Pour plus d'informations, consultez [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## Voir aussi  
 [Introduction to Windows Service Applications](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)   
 [How to: Create Windows Services](../../../docs/framework/windows-services/how-to-create-windows-services.md)   
 [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)   
 [How to: Log Information About Services](../../../docs/framework/windows-services/how-to-log-information-about-services.md)   
 [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)