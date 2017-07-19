---
title: "Optimisation des performances&#160;: ressources d&#39;application | Microsoft Docs"
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
  - "ressources d'application, performances"
  - "pinceaux, performances"
  - "ressources, performances"
  - "partager des pinceaux sans copier"
  - "partager des ressources"
  - "ressources statiques"
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Optimisation des performances&#160;: ressources d&#39;application
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet de partager des ressources d'application afin que vous puissiez prendre en charge une apparence cohérente ou un comportement à travers des éléments type semblables.  Cette rubrique fournit quelques recommandations dans ce domaine qui peut vous aider à améliorer les performances de vos applications.  
  
 Pour plus d'informations sur les ressources, consultez [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
## Partage de ressources  
 Si votre application utilise des contrôles personnalisés et définit des ressources dans un <xref:System.Windows.ResourceDictionary> \(ou nœud de ressources XAML\), il est recommandé que vous définissiez les ressources au niveau <xref:System.Windows.Application> ou de l'objet <xref:System.Windows.Window>, ou dans le thème par défaut pour les contrôles personnalisés.  La définition de ressources dans <xref:System.Windows.ResourceDictionary> d'un contrôle personnalisé impose un impact sur les performances pour chaque instance de ce contrôle.  Par exemple, si vous avez des opérations de pinceau intensives définies dans le cadre de la définition de ressource d'un contrôle personnalisé et de nombreuses instances du contrôle personnalisé, le jeu de travail de l'application augmentera considérablement.  
  
 Pour illustrer ce point, considérez les éléments suivants.  Admettons que vous développez un jeu de cartes à l'aide de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Pour la plupart des jeux de cartes, vous avez besoin de 52 cartes avec 52 faces différentes.  Vous décidez d'implémenter une carte de contrôle personnalisé et vous définissez 52 pinceaux \(chacun représentant une face de carte\) dans les ressources de votre carte de contrôle personnalisé.  Dans votre application principale, vous créez initialement 52 instances de cette carte de contrôle personnalisé.  Chaque instance de la carte de contrôle personnalisé génère 52 instances des objets <xref:System.Windows.Media.Brush>, ce qui vous donne un total de 52 \* 52 objets <xref:System.Windows.Media.Brush> dans votre application.  En déplaçant les pinceaux hors des ressources de la carte de contrôle personnalisé au niveau <xref:System.Windows.Application> ou de l'objet <xref:System.Windows.Window>, ou en les définissant dans le thème par défaut pour le contrôle personnalisé, vous réduisez le jeu de travail de l'application, puisque vous partagez maintenant les 52 pinceaux parmi 52 instances de la carte de contrôle.  
  
## Partage d'un pinceau sans copier  
 Si vous avez plusieurs éléments utilisant le même objet <xref:System.Windows.Media.Brush>, définissez le pinceau comme une ressource et référencez\-le, plutôt que de définir le pinceau inline dans [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].  Cette méthode créera une instance et la réutilisera, alors que la définition de pinceaux inline dans [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] crée une instance pour chaque élément.  
  
 L'exemple de balise suivant illustre ce point :  
  
 [!code-xml[Performance#PerformanceSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## Utilisation de ressources statiques lorsque cela est possible  
 Une ressource statique fournit une valeur pour tout attribut de propriété XAML en recherchant une référence à une ressource déjà définie.  Le comportement de recherche pour cette ressource est analogue à recherche au moment de la compilation.  
  
 En revanche,  une ressource dynamique créera une expression temporaire pendant la compilation initiale et donc diffèrera la recherche de ressources jusqu'à ce que la valeur de ressource demandée soit réellement demandée pour construire un objet.  Le comportement de recherche pour cette ressource est analogue à la recherche au moment de l'exécution, qui entraîne un impact sur les performances.  Utilisez les ressources statiques quand cela est possible dans votre application, à l'aide de ressources dynamiques uniquement en cas de besoin.  
  
 L'exemple de balise suivant affiche l'utilisation des deux types de ressources :  
  
 [!code-xml[Performance#PerformanceSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## Voir aussi  
 [Optimisation des performances des applications WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [Planification des performances des applications](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [Tirer parti du matériel](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [Disposition et conception](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [Comportement d'objets](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [Liaison de données](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [Autres recommandations relatives aux performances](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)