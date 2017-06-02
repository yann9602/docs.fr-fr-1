---
title: "Comment&#160;: utiliser des ressources d&#39;application | Microsoft Docs"
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
  - "ressources d'application"
  - "ressources, ressources d'application"
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: utiliser des ressources d&#39;application
Cet exemple indique comment utiliser des ressources d'application.  
  
## Exemple  
 L'exemple suivant affiche un fichier de définition d'application.  Le fichier de définition d'application définit une section de ressource \(une valeur pour la propriété <xref:System.Windows.Application.Resources%2A>\).  Les ressources définies au niveau application peuvent être accédées par toutes les autres pages faisant partie de l'application.  Dans ce cas, la ressource est un style déclaré.  Du fait qu'un style complet qui inclut un modèle de contrôle peut être long, cet exemple omet le modèle de contrôle défini dans l'accesseur Set de propriété <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> du style.  
  
 [!code-xml[ResourcesApplication#PreTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xml[ResourcesApplication#PostTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 L'exemple suivant affiche une page [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui référence la ressource au niveau de l'application que l'exemple précédent a définie.  La ressource est référencée à l'aide d'un [StaticResource, extension de balisage](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) qui spécifie la clé de ressource unique de la ressource demandée.  Aucune ressource avec la clé GelButton n'est trouvée dans la page actuelle, donc la portée de la recherche de la ressource pour la ressource demandée continue au delà de la page actuelle et dans les ressources définies au niveau de l'application.  
  
 [!code-xml[ResourcesApplication#ConsumingPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## Voir aussi  
 [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [Vue d'ensemble de la gestion d'applications](../../../../docs/framework/wpf/app-development/application-management-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)