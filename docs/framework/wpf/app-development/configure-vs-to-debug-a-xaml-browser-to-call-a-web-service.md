---
title: "Comment : configurer Visual Studio pour déboguer une application de navigateur XAML et appeler un service Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 330ee213e147cfef709c919c95cb0e58159bc37b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>Comment : configurer Visual Studio pour déboguer une application de navigateur XAML et appeler un service Web
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]exécuter dans un sandbox de sécurité de confiance partielle est limité à l’ensemble de la zone Internet d’autorisations. Ce jeu d’autorisations restreint les appels de service Web uniquement les services Web qui sont trouvent dans le [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] site de l’application d’origine. Lorsqu’un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] du débogage à partir de [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)], bien qu’il n’est pas censé avoir le même site d’origine que le service Web qu’il référence. Cette causes des exceptions de sécurité à déclencher lorsque le [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] tente d’appeler le service Web. Toutefois, un [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] projet peut être configuré pour avoir le même site d’origine que le service Web qu’elle appelle lors du débogage. Cela permet la [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] en toute sécurité appeler le service Web sans provoquer des exceptions de sécurité.  
  
## <a name="configuring-visual-studio"></a>Configuration de Visual Studio  
 Pour configurer [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] pour déboguer un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] qui appelle un service Web :  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Dans le **Concepteur de projets**, cliquez sur le **déboguer** onglet.  
  
3.  Dans le **Action de démarrage** section, sélectionnez **démarrer le programme externe** et entrez les informations suivantes :  
  
     `C:\WINDOWS\System32\PresentationHost.exe`  
  
4.  Dans le **Options de démarrage** section, entrez le texte suivant dans le **arguments de ligne de commande** zone de texte :  
  
     `-debug`  *nom de fichier*  
  
     Le *nom de fichier* la valeur pour le **-déboguer** paramètre est le nom de fichier .xbap ; par exemple :  
  
     `-debug c:\example.xbap`  
  
> [!NOTE]
>  Cette configuration est la valeur par défaut pour les solutions qui sont créés avec le [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] modèle de projet.  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Dans le **Concepteur de projets**, cliquez sur le **déboguer** onglet.  
  
3.  Dans le **Options de démarrage** section, ajoutez le paramètre de ligne de commande suivant à la **arguments de ligne de commande** zone de texte :  
  
     `-debugSecurityZoneURL`  *URL*  
  
     Le *URL* la valeur pour le **- debugSecurityZoneURL** paramètre est le [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] pour l’emplacement que vous souhaitez simuler comme site d’origine de votre application.  
  
 Par exemple, considérez un [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] qui utilise un service Web par le code suivant [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:  
  
 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`  
  
 Le site d’origine [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] pour ce site Web service est :  
  
 `http://services.msdn.microsoft.com`  
  
 Par conséquent, le texte complet **- debugSecurityZoneURL** paramètre de ligne de commande et la valeur est :  
  
 `-debugSecurityZoneURL http://services.msdn.microsoft.com`  
  
## <a name="see-also"></a>Voir aussi  
 [Hôte WPF (PresentationHost.exe)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)
