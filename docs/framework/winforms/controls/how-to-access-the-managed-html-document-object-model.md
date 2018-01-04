---
title: "Guide pratique pour accéder au modèle DOM (Document Object Model) HTML managé"
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
- HTML DOM [Windows Forms], accessing
- managed HTML DOM [Windows Forms], accessing
ms.assetid: 40fa5cd5-1ed8-42f6-a93f-9ac01608bbeb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83ee8c5e0cd578a0eb821a35a27c5ff0072e5533
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-access-the-managed-html-document-object-model"></a>Guide pratique pour accéder au modèle DOM (Document Object Model) HTML managé
Vous pouvez accéder au modèle DOM (Document Object Model) HTML géré à partir de deux types d'applications :  
  
-   l'application Windows Forms (.exe) qui a hébergé le contrôle <xref:System.Windows.Forms.WebBrowser> géré. Ces deux technologies se complètent mutuellement, avec le contrôle <xref:System.Windows.Forms.WebBrowser> qui affiche la page pour l'utilisateur et le modèle DOM HTML qui représente la structure logique du document ;  
  
-   l'<xref:System.Windows.Forms.UserControl> Windows Forms hébergé dans Internet Explorer. Vous pouvez accéder au modèle DOM HTML qui représente la page sur laquelle votre <xref:System.Windows.Forms.UserControl> est hébergé pour modifier la structure du document ou ouvrir des boîtes de dialogue modales, entre autres possibilités.  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a>Pour accéder au modèle DOM à partir d'une application Windows Forms  
  
1.  Hébergez un contrôle <xref:System.Windows.Forms.WebBrowser> dans votre application Windows Forms et surveillez l'événement <xref:System.Windows.Forms.WebBrowser.DocumentCompleted>. Pour plus d’informations sur l’hébergement de contrôles et la surveillance d’événements, consultez [Événements](../../../../docs/standard/events/index.md).  
  
2.  Récupérez <xref:System.Windows.Forms.HtmlDocument> pour la page actuelle en accédant à la propriété <xref:System.Windows.Forms.WebBrowser.Document%2A> du contrôle <xref:System.Windows.Forms.WebBrowser>.  

### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a>Pour accéder au modèle DOM à partir d'un UserControl hébergé dans Internet Explorer  
  
1.  Créez votre propre classe personnalisée dérivée de la classe <xref:System.Windows.Forms.UserControl>. Pour plus d’informations, consultez [Guide pratique pour créer des contrôles composites](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md).  
  
2.  Placez le code suivant dans votre gestionnaire d'événements Load pour <xref:System.Windows.Forms.UserControl> :  
  
 [!code-csharp[AccessHTMLDOMControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a>Programmation fiable  
  
1.  Quand vous utilisez le modèle DOM via le contrôle <xref:System.Windows.Forms.WebBrowser>, vous devez systématiquement attendre que l'événement <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> se produise avant de tenter d'accéder à la propriété <xref:System.Windows.Forms.WebBrowser.Document%2A> du contrôle <xref:System.Windows.Forms.WebBrowser>. L'événement <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> est déclenché une fois que le document entier a été chargé. Si vous utilisez le modèle DOM avant, cela risque de provoquer une exception au moment de l'exécution dans votre application.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
  
1.  Votre application ou <xref:System.Windows.Forms.UserControl> nécessite la confiance totale pour accéder au modèle DOM HTML géré. Si vous déployez une application Windows Forms à l’aide de [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], vous pouvez demander une confiance totale en utilisant les options d’élévation d’autorisations ou de déploiement d’application approuvée. Pour plus d’informations, consultez [Sécurisation des applications ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du modèle DOM HTML managé](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
