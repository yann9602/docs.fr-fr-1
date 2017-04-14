---
title: "Comment&#160;: ajouter un &#233;cran de d&#233;marrage dans une application WPF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "écran de démarrage (WPF)"
  - "SplashScreen (classe WPF)"
  - "fenêtre de démarrage (WPF)"
  - "WPF, écran de démarrage"
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: ajouter un &#233;cran de d&#233;marrage dans une application WPF
Cette rubrique indique comment ajouter une fenêtre de démarrage, ou *écran de démarrage*, à une application Windows Presentation Foundation \(WPF\).  
  
### Pour ajouter une image existante en tant qu'écran de démarrage  
  
1.  Créez ou recherchez une image que vous souhaitez utiliser en tant qu'écran de démarrage.  Vous pouvez utiliser tout format d'image pris en charge par le composant WIC \(Windows Imaging Component\).  Par exemple, vous pouvez utiliser le format BMP, GIF, JPEG, PNG ou TIFF.  
  
2.  Ajoutez le fichier image au projet d'application WPF.  Pour plus d'informations, consultez [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/fr-fr/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).  
  
3.  Dans l'Explorateur de solutions, sélectionnez une image.  
  
4.  Dans la fenêtre Propriétés, cliquez sur la flèche de déroulement de la propriété **Action de génération**.  
  
5.  Sélectionnez **SplashScreen** dans la liste déroulante.  
  
    > [!NOTE]
    >  Si l'option **SplashScreen** n'apparaît pas, vérifiez que vous utilisez [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] SP1 ou version ultérieure.  
  
6.  Appuyez sur F5 pour générer et exécuter l'application.  
  
     L'image de l'écran de démarrage apparaît au milieu de l'écran, puis disparaît lorsque la fenêtre d'application principale s'affiche.  
  
### Pour supprimer l'écran de démarrage d'une application  
  
1.  Dans l'Explorateur de solutions, sélectionnez l'image de l'écran de démarrage.  
  
2.  Dans la fenêtre Propriétés, affectez à la propriété **Action de génération** la valeur **Aucune**.  
  
### Pour supprimer l'écran de démarrage d'une application  
  
-   Dans l'Explorateur de solutions, supprimez l'image de l'écran de démarrage.  
  
-   Excluez l'image de l'écran de démarrage du projet.  
  
## Voir aussi  
 <xref:System.Windows.SplashScreen>   
 [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/fr-fr/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)