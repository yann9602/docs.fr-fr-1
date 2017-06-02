---
title: "Comment&#160;: utiliser des ressources dans des applications localisables | Microsoft Docs"
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
  - "applications, localisables"
  - "applications localisables"
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: utiliser des ressources dans des applications localisables
La localisation est l'adaptation d'une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à différentes cultures.  Pour ce faire, du texte tel que les titres, les légendes, les éléments de zone de liste, etc. doivent être traduits.  Pour simplifier la traduction, les éléments à traduire sont rassemblés dans des fichiers de ressources.  Pour plus d'informations sur la création d'un fichier de ressources à des fins de localisation, consultez [Localiser une application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).  Pour qu'une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] soit localisable, les développeurs doivent générer toutes les ressources localisables dans un assembly de ressources.  L'assembly de ressources est localisé dans différentes langues et l'[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] de gestion des ressources est utilisée pour le chargement du code\-behind.  Un fichier projet \(.proj\) est requis pour toute application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Toutes les ressources que vous utilisez dans votre application doivent être incluses dans ce fichier projet.  L'exemple de code suivant illustre ce point.  
  
## Exemple  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 Pour utiliser une ressource dans votre application, créez une instance <xref:System.Resources.ResourceManager> et chargez la ressource souhaitée.  L'exemple suivant illustre la procédure à suivre pour réaliser cette opération.  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]