---
title: "Vue d&#39;ensemble du contr&#244;le WebBrowser | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WebBrowser"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "pages Web, afficher dans les applications"
  - "WebBrowser (contrôle Windows Forms), à propos de"
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Vue d&#39;ensemble du contr&#244;le WebBrowser
Le contrôle <xref:System.Windows.Forms.WebBrowser> fournit un wrapper managé destiné au contrôle ActiveX WebBrowser.  Le wrapper managé permet d'afficher des pages Web dans vos applications clientes Windows Forms.  Vous pouvez utiliser le contrôle <xref:System.Windows.Forms.WebBrowser> pour dupliquer les fonctionnalités de navigation Web d'Internet Explorer dans votre application ou encore désactiver les fonctionnalités Internet Explorer par défaut et utiliser ce contrôle comme une simple visionneuse de documents HTML.  Vous pouvez également utiliser le contrôle pour ajouter des éléments d'interface utilisateur DHTML à votre formulaire et masquer le fait qu'ils sont hébergés dans le contrôle <xref:System.Windows.Forms.WebBrowser>.  Cette approche vous permet de combiner de façon transparente les contrôles Web et Windows Forms dans une même application.  
  
## Propriétés, méthodes et événements fréquemment utilisés  
 Le contrôle <xref:System.Windows.Forms.WebBrowser> possède plusieurs propriétés, méthodes et événements que vous pouvez utiliser pour implémenter des contrôles d'Internet Explorer.  Par exemple, vous pouvez utiliser la méthode `Navigate` pour implémenter une barre d'adresses, et les méthodes `GoBack`, `GoForward`, `Stop` et `Refresh` pour implémenter des boutons de navigation sur une barre d'outils.  Vous pouvez gérer l'événement `Navigated` pour mettre à jour la barre d'adresses avec la valeur de la propriété `Url` et la barre de titre avec la valeur de la propriété `DocumentTitle`.  
  
 Si vous souhaitez générer votre propre contenu de page dans votre application, vous pouvez définir la propriété `DocumentText`.  Si vous connaissez le modèle DOM \(Document Object Model\) HTML, vous pouvez également manipuler le contenu de la page Web en cours via la propriété `Document`.  À l'aide de cette propriété, vous pouvez stocker et modifier des documents dans la mémoire au lieu d'explorer les fichiers.  
  
 La propriété `Document` vous permet également d'appeler des méthodes implémentées dans du code de script de page Web à partir de votre code d'application cliente.  Pour accéder au code d'application cliente à partir du code de script, définissez la propriété `ObjectForScripting`.  L'objet spécifié est accessible par votre code de script en tant qu'objet `window.external`.  
  
|Nom|Description|  
|---------|-----------------|  
|Propriété <xref:System.Windows.Forms.WebBrowser.Document%2A>|Obtient un objet qui fournit un accès managé au modèle DOM \(Document Object Model\) HTML de la page Web en cours.|  
|Événement <xref:System.Windows.Forms.WebBrowser.DocumentCompleted>|Se produit à la fin du chargement d'une page Web.|  
|Propriété <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>|Obtient ou définit le contenu HTML de la page Web en cours.|  
|Propriété <xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A>|Obtient le titre de la page Web en cours.|  
|Méthode <xref:System.Windows.Forms.WebBrowser.GoBack%2A>|Accède à la page précédente de l'historique.|  
|Méthode <xref:System.Windows.Forms.WebBrowser.GoForward%2A>|Accède à la page suivante de l'historique.|  
|Méthode <xref:System.Windows.Forms.WebBrowser.Navigate%2A>|Accède à l'URL spécifiée.|  
|Événement <xref:System.Windows.Forms.WebBrowser.Navigating>|Se produit avant le début de la navigation et permet d'annuler l'action.|  
|Propriété <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A>|Obtient ou définit un objet que le code de script de la page Web peut utiliser pour communiquer avec votre application.|  
|Méthode <xref:System.Windows.Forms.WebBrowser.Print%2A>|Imprime la page Web en cours.|  
|Méthode <xref:System.Windows.Forms.WebBrowser.Refresh%2A>|Recharge la page Web en cours.|  
|Méthode <xref:System.Windows.Forms.WebBrowser.Stop%2A>|Arrête la navigation en cours, ainsi que les éléments de page dynamiques, tels que les sons et animations.|  
|Propriété <xref:System.Windows.Forms.WebBrowser.Url%2A>|Obtient ou définit l'URL de la page Web en cours.  La définition de cette propriété permet au contrôle d'accéder à la nouvelle URL.|  
  
## Voir aussi  
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
 [Comment : naviguer vers une URL avec un contrôle WebBrowser](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)   
 [Comment : imprimer avec un contrôle WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)   
 [Comment : ajouter des fonctionnalités de navigateur Web à une application Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)   
 [Comment : créer une visionneuse de documents HTML dans une application Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)   
 [Comment : implémenter la communication bidirectionnelle entre le code DHTML et le code d'application cliente](../../../../docs/framework/winforms/controls/implement-two-way-com-between-dhtml-and-client.md)   
 [Sécurité WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-security.md)