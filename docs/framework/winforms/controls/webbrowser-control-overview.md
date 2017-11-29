---
title: "Vue d'ensemble du contrôle WebBrowser"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c2dfae4cbd7f583ce69ff5591c24a573db0d4e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="webbrowser-control-overview"></a>Vue d'ensemble du contrôle WebBrowser
Le <xref:System.Windows.Forms.WebBrowser> contrôle fournit un wrapper managé pour le contrôle WebBrowser ActiveX. Le wrapper managé vous permet d’afficher des pages Web dans vos applications clientes Windows Forms. Vous pouvez utiliser la <xref:System.Windows.Forms.WebBrowser> contrôle de dupliquer les fonctionnalités de navigation Web d’Internet Explorer dans votre application, ou vous peut désactiver la fonctionnalité d’Internet Explorer par défaut et utiliser le contrôle comme une simple visionneuse de documents HTML. Vous pouvez également utiliser le contrôle à ajouter des éléments d’interface utilisateur DHTML à votre formulaire et masquer le fait qu’ils sont hébergés dans le <xref:System.Windows.Forms.WebBrowser> contrôle. Cette approche vous permet de combiner de façon transparente les contrôles Web avec des contrôles Windows Forms dans une application unique.  
  
## <a name="frequently-used-properties-methods-and-events"></a>Propriétés fréquemment utilisées, méthodes et événements  
 Le <xref:System.Windows.Forms.WebBrowser> contrôle possède plusieurs propriétés, méthodes et événements que vous pouvez utiliser pour implémenter des contrôles dans Internet Explorer. Par exemple, vous pouvez utiliser la `Navigate` méthode pour implémenter une barre d’adresses et le `GoBack`, `GoForward`, `Stop`, et `Refresh` méthodes à implémenter des boutons de navigation sur une barre d’outils. Vous pouvez gérer le `Navigated` événement pour mettre à jour de la barre d’adresses avec la valeur de la `Url` propriété et la barre de titre avec la valeur de la `DocumentTitle` propriété.  
  
 Si vous souhaitez générer votre propre contenu de page au sein de votre application, vous pouvez définir le `DocumentText` propriété. Si vous êtes familiarisé avec le modèle objet de document HTML (DOM), vous pouvez également manipuler le contenu de la page Web actuelle par le biais du `Document` propriété. Avec cette propriété, vous pouvez stocker et modifier des documents dans la mémoire au lieu de naviguer entre les fichiers.  
  
 Le `Document` propriété vous permet également d’appeler des méthodes implémentées dans du code à partir de votre code d’application cliente de script de page Web. Pour accéder à votre code d’application cliente à partir de votre code de script, définissez la `ObjectForScripting` propriété. L’objet que vous spécifiez est accessible par le code de votre script en tant que le `window.external` objet.  
  
|Nom|Description|  
|----------|-----------------|  
|Propriété <xref:System.Windows.Forms.WebBrowser.Document%2A>|Obtient un objet qui fournit l’accès managé pour le modèle objet de document HTML (DOM) de la page Web actuelle.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>événement|Se produit lorsqu’une page Web est chargée.|  
|Propriété <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>|Obtient ou définit le contenu de la page Web HTML.|  
|Propriété <xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A>|Obtient le titre de la page Web actuelle.|  
|Méthode <xref:System.Windows.Forms.WebBrowser.GoBack%2A>|Navigue vers la page précédente dans l’historique.|  
|Méthode <xref:System.Windows.Forms.WebBrowser.GoForward%2A>|Navigue vers la page suivante dans l’historique.|  
|Méthode <xref:System.Windows.Forms.WebBrowser.Navigate%2A>|Navigue vers l’URL spécifiée.|  
|<xref:System.Windows.Forms.WebBrowser.Navigating>événement|Se produit avant le début de la navigation, l’activation de l’action doit être annulée.|  
|Propriété <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A>|Obtient ou définit un objet de code de script de page Web peuvent utiliser pour communiquer avec votre application.|  
|Méthode <xref:System.Windows.Forms.WebBrowser.Print%2A>|Permet d’imprimer la page Web actuelle.|  
|Méthode <xref:System.Windows.Forms.WebBrowser.Refresh%2A>|Recharge la page Web actuelle.|  
|Méthode <xref:System.Windows.Forms.WebBrowser.Stop%2A>|Arrête la navigation en cours et arrête les éléments de page dynamique tels que des sons et des animations.|  
|Propriété <xref:System.Windows.Forms.WebBrowser.Url%2A>|Obtient ou définit l’URL de la page Web actuelle. Définition de cette propriété navigue le contrôle à la nouvelle URL.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventHandler>  
 <xref:System.Windows.Forms.WebBrowserEncryptionLevel>  
 <xref:System.Windows.Forms.WebBrowserNavigatedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserNavigatedEventHandler>  
 <xref:System.Windows.Forms.WebBrowserNavigatingEventArgs>  
 <xref:System.Windows.Forms.WebBrowserNavigatingEventHandler>  
 <xref:System.Windows.Forms.WebBrowserProgressChangedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserReadyState>  
 <xref:System.Windows.Forms.WebBrowserRefreshOption>  
 [Guide pratique pour naviguer vers une URL avec un contrôle WebBrowser](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)  
 [Guide pratique pour imprimer avec un contrôle WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)  
 [Guide pratique pour ajouter des fonctionnalités de navigateur Web à une application Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)  
 [Guide pratique pour créer une visionneuse de documents HTML dans une application Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)  
 [Guide pratique pour implémenter la communication bidirectionnelle entre le code DHTML et le code d'application cliente](../../../../docs/framework/winforms/controls/implement-two-way-com-between-dhtml-and-client.md)  
 [Sécurité WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-security.md)
