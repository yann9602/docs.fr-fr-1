---
title: "IWpfHostSupport | Microsoft Docs"
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
  - "IWpfHostSupport (interface)"
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# IWpfHostSupport
Les applications qui hébergent le contenu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] via PresentationHost.exe implémentent cette interface pour fournir un point d'intégration entre l'hôte et PresentationHost.exe.  
  
## Notes  
 Les applications [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], telles que les navigateurs Web, peuvent héberger du contenu [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)], y compris [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] et XAML libre.  Pour héberger le contenu [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)], les applications [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] créent une instance du [contrôle WebBrowser](http://go.microsoft.com/fwlink/?LinkId=97911).  Pour être hébergé, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] crée une instance de PresentationHost.exe, ce qui fournit le contenu [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] hébergé à l'hôte à afficher dans le [contrôle WebBrowser](http://go.microsoft.com/fwlink/?LinkId=97911).  
  
 L'intégration activée par `IWpfHostSupport` permet à PresentationHost.exe d'effectuer les opérations suivantes :  
  
-   Découvrir et enregistrer avec les périphériques d'entrée bruts \(périphériques d'interface utilisateur\) auxquels l'application hôte s'intéresse.  
  
-   Recevoir des messages d'entrée des périphériques d'entrée bruts enregistrés et transmettre des messages appropriés à l'application hôte.  
  
-   Interroger l'application hôte pour fournir une progression personnalisée et des interfaces utilisateur d'erreur.  
  
> [!NOTE]
>  Cette API est conçue et prise en charge uniquement pour une utilisation sur l'ordinateur client local  
  
## Membres  
  
|Membre|Description|  
|------------|-----------------|  
|[GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md)|Permet à PresentationHost.exe de découvrir les périphériques d'entrée bruts \(périphériques d'interface utilisateur\) qui intéressent l'application hôte.|  
|[FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)|Appelé par PresentationHost.exe toutes les fois qu'un message est reçu à moins que E\_NOTIMPL ne soit retourné.|  
|[GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md)|Par défaut, PresentationHost.exe fournit sa propre progression de déploiement et les interfaces utilisateur d'erreur de déploiement affichées lorsque le contenu WPF est déployé.|