---
title: "Comment&#160;: acc&#233;der au mod&#232;le objet de document HTML manag&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Modèle DOM HTML, l’accès à"
  - "Managed HTML DOM, l’accès à"
ms.assetid: 40fa5cd5-1ed8-42f6-a93f-9ac01608bbeb
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: acc&#233;der au mod&#232;le objet de document HTML manag&#233;
Vous pouvez accéder au modèle DOM (Document Object Model) HTML géré à partir de deux types d'applications :  
  
-   Une application Windows Forms (.exe) qui a hébergé la <xref:System.Windows.Forms.WebBrowser> contrôle. Ces deux technologies complètent mutuellement, avec la <xref:System.Windows.Forms.WebBrowser> contrôle affichant la page à l’utilisateur et le modèle DOM HTML qui représente la structure logique du document.  
  
-   Windows Forms <xref:System.Windows.Forms.UserControl> hébergé dans Internet Explorer. Le modèle DOM HTML qui représente la page sur laquelle vous pouvez accéder à votre <xref:System.Windows.Forms.UserControl> est hébergé pour modifier la structure du document ou ouvrir des boîtes de dialogue modales, parmi de nombreuses autres possibilités.  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a>Pour accéder au modèle DOM à partir d’une application Windows Forms  
  
1.  Hôte un <xref:System.Windows.Forms.WebBrowser> contrôler dans votre application Windows Forms et surveillez le <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> événement. Pour plus d’informations sur l’hébergement de contrôles et la surveillance des événements, consultez la page [événements](../../../../docs/standard/events/index.md).  
  
2.  Récupérer le <xref:System.Windows.Forms.HtmlDocument> pour la page actuelle en accédant à la <xref:System.Windows.Forms.WebBrowser.Document%2A> propriété de la <xref:System.Windows.Forms.WebBrowser> contrôle.  
  
<!-- TODO: review snippet reference  [!CODE [AccessHTMLDOMApp#1](AccessHTMLDOMApp#1)]  -->  
  
### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a>Pour accéder au modèle DOM à partir d'un UserControl hébergé dans Internet Explorer  
  
1.  Créer votre propre classe personnalisée dérivée de la <xref:System.Windows.Forms.UserControl> classe. Pour plus d’informations, consultez [Comment : créer des contrôles composites](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md).  
  
2.  Placez le code suivant dans votre gestionnaire d’événements Load pour votre <xref:System.Windows.Forms.UserControl>:  
  
 [!code-csharp[AccessHTMLDOMControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a>Programmation fiable  
  
1.  Lors de l’utilisation du modèle DOM via le <xref:System.Windows.Forms.WebBrowser> (contrôle), vous devez systématiquement attendre que la <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> événement se produit avant de tenter d’accéder à la <xref:System.Windows.Forms.WebBrowser.Document%2A> propriété de la <xref:System.Windows.Forms.WebBrowser> contrôle. Le <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> événement est déclenché après chargée de l’ensemble du document ; si vous utilisez le modèle DOM avant, cela risque de provoquer une exception d’exécution dans votre application.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
  
1.  Votre application ou <xref:System.Windows.Forms.UserControl> nécessite la confiance totale pour accéder à la DOM. HTML managé Si vous déployez une application Windows Forms à l’aide [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], vous pouvez demander une confiance totale à l’aide de l’élévation d’autorisations ou de déploiement d’applications approuvées, consultez [sécurisation des Applications ClickOnce](../Topic/Securing%20ClickOnce%20Applications.md) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du modèle objet de Document HTML managé](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)