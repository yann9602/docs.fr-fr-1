---
title: "Comment&#160;: configurer Visual Studio pour d&#233;boguer une application de navigateur XAML et appeler un service Web | Microsoft Docs"
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
  - "configurer Visual Studio pour déboguer des applications de navigateur XAML (WPF)"
  - "configurer Visual Studio pour déboguer des applications XBAP (WPF)"
  - "déboguer des exceptions de sécurité pour des applications de navigateur XAML (WPF)"
  - "déboguer des applications de navigateur XAML qui appellent un service Web (WPF)"
  - "exception de sécurité pour des applications de navigateur XAML (WPF), débogage"
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: configurer Visual Studio pour d&#233;boguer une application de navigateur XAML et appeler un service Web
Les [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] s'exécutent dans un bac à sable \(sandbox\) de sécurité de confiance partielle limité aux autorisations de la zone Internet.  Ce jeu d'autorisations limite les appels de service Web uniquement aux services Web situés sur le site d'origine de l'application [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  Toutefois, lorsqu'une [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] est déboguée depuis [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)], elle n'est pas considérée avoir le même site d'origine que le service Web auquel elle fait référence.  Cela provoque la levée d'exceptions de sécurité lorsque la [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] tente d'appeler le service Web.  Toutefois, un projet [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)][!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] peut être configuré pour faire croire qu'il a le même site d'origine que le service Web qu'il appelle lors du débogage.  Cela permet à [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] d'appeler sans risque le service Web sans lever des exceptions de sécurité.  
  
## Configuration de Visual Studio  
 Pour configurer [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] pour déboguer une [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] qui appelle un service Web :  
  
1.  Un projet étant sélectionné dans l'**Explorateur de solutions**, cliquez dans le menu **Projet** sur **Propriétés**.  
  
2.  Dans le **Concepteur de projets**, cliquez sur l'onglet **Déboguer**.  
  
3.  Dans la section **Action de démarrage**, sélectionnez **Démarrer le programme externe**, puis effectuez l'opération suivante :  
  
     `C:\WINDOWS\System32\PresentationHost.exe`  
  
4.  Dans la section **Options de démarrage**, entrez les éléments ci\-dessous dans la zone de texte **Arguments de la ligne de commande** :  
  
     `-debug`  *filename*  
  
     La valeur *NomFichier* du paramètre **\-debug** correspond au nom de fichier .xbap. Par exemple :  
  
     `-debug c:\example.xbap`  
  
> [!NOTE]
>  Il s'agit de la configuration par défaut pour les solutions créées avec le modèle de projet [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)][!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)].  
  
1.  Un projet étant sélectionné dans l'**Explorateur de solutions**, cliquez dans le menu **Projet** sur **Propriétés**.  
  
2.  Dans le **Concepteur de projets**, cliquez sur l'onglet **Déboguer**.  
  
3.  Dans la section **Options de démarrage**, ajoutez le paramètre de ligne de commande suivant à la zone de texte **Arguments de la ligne de commande** :  
  
     `-debugSecurityZoneURL`  *URL*  
  
     La valeur *URL* du paramètre **\-debugSecurityZoneURL** est l'[!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] de l'emplacement à simuler comme site d'origine de l'application.  
  
 Supposons, qu'une [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] utilise un service Web avec l'[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] suivante :  
  
 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`  
  
 Le site d'origine [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] du service Web est :  
  
 `http://services.msdn.microsoft.com`  
  
 Par conséquent, le paramètre de ligne de commande **\-debugSecurityZoneURL** complet et la valeur sont :  
  
 `-debugSecurityZoneURL http://services.msdn.microsoft.com`  
  
## Voir aussi  
 [Hôte WPF \(PresentationHost.exe\)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)