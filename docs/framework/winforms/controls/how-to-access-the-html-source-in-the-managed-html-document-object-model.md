---
title: "Comment : accéder à la source HTML dans le modèle objet de document HTML managé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM
- HTML [Windows Forms], accessing in Windows Forms
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7ef9839029e1c60cbc0d713e8982baa5708a281f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a>Comment : accéder à la source HTML dans le modèle objet de document HTML managé
Les propriétés <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> et <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> sur le contrôle <xref:System.Windows.Forms.WebBrowser> renvoient le code HTML du document actif comme il était quand il a été affiché pour la première fois. Toutefois, si vous modifiez la page à l'aide des appels de méthode et de propriété tels que <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> et <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, ces modifications n'apparaissent pas quand vous appelez <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> et <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>. Pour obtenir le code source HTML le plus à jour pour le modèle DOM, vous devez appeler la propriété <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> sur l'élément HTML.  
  
 La procédure suivante illustre comment récupérer la source dynamique et l'afficher dans un menu contextuel distinct.  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a>Récupération de la source dynamique avec la propriété OuterHtml  
  
1.  Créez une application Windows Forms. Démarrer avec un seul <xref:System.Windows.Forms.Form>et l’appeler `Form1`.  
  
2.  Hôte du <xref:System.Windows.Forms.WebBrowser> contrôle dans votre application Windows Forms et nommez-le `WebBrowser1`. Pour plus d’informations, consultez [Comment : ajouter des fonctionnalités de navigateur Web à une Application Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).  
  
3.  Créer un second <xref:System.Windows.Forms.Form> dans votre application appelé `CodeForm`.  
  
4.  Ajouter un <xref:System.Windows.Forms.RichTextBox> le contrôle à `CodeForm` et définir son <xref:System.Windows.Forms.Control.Dock%2A> propriété `Fill`.  
  
5.  Créez une propriété publique sur `CodeForm` appelée `Code`.  
  
     [!code-csharp[DisplayWebBrowserCode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6.  Ajouter un <xref:System.Windows.Forms.Button> contrôle nommé `Button1` à votre <xref:System.Windows.Forms.Form>et surveillez le <xref:System.Windows.Forms.Control.Click> événement. Pour plus d’informations sur la surveillance des événements, consultez [événements](../../../../docs/standard/events/index.md).  
  
7.  Ajoutez le code ci-après au gestionnaire d'événements <xref:System.Windows.Forms.Control.Click>.  
  
     [!code-csharp[DisplayWebBrowserCode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Testez systématiquement la valeur de <xref:System.Windows.Forms.WebBrowser.Document%2A> avant d'essayer de le récupérer. Si le chargement de la page active n'est pas terminé, l'initialisation de <xref:System.Windows.Forms.WebBrowser.Document%2A> ou de ses objets enfants peut éventuellement ne pas se produire.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du modèle DOM HTML managé](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)  
 [Vue d’ensemble du contrôle WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)
