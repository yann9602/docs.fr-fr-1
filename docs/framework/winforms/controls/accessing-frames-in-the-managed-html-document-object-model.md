---
title: "Acc&#232;s aux frames dans le mod&#232;le objet de document HTML manag&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "DOM, accéder aux frames en HTML managé"
  - "frames, accéder"
  - "DOM HTML, managé"
  - "HTML, DOM"
  - "HTML, managé"
  - "modèle DOM HTML managé"
ms.assetid: cdeeaa22-0be4-4bbf-9a75-4ddc79199f8d
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Acc&#232;s aux frames dans le mod&#232;le objet de document HTML manag&#233;
Certains documents HTML sont composés de *frames*, c'est\-à\-dire des fenêtres qui peuvent contenir leurs propres documents HTML.  L'utilisation de frames simplifie la création de pages HTML dans lesquelles un ou plusieurs éléments de la page \(tels qu'une barre de navigation\) restent statiques, tandis que d'autres frames changent constamment de contenu.  
  
 Les auteurs de code HTML peuvent créer des frames de deux façons :  
  
-   à l'aide des balises `FRAMESET` et `FRAME`, qui créent des fenêtres fixes.  
  
 ou  
  
-   à l'aide de la balise `IFRAME`, qui crée une fenêtre flottante pouvant être repositionnée au moment de l'exécution.  
  
1.  Les frames contenant des documents HTML, ils sont représentés dans le modèle DOM en tant qu'éléments de fenêtre et éléments de cadre.  
  
2.  Quand vous accédez à une balise `FRAME` ou `IFRAME` à l'aide de la collection Frames de <xref:System.Windows.Forms.HtmlWindow>, vous récupérez l'élément de fenêtre correspondant au frame.  Il représente toutes les propriétés dynamiques du frame, telles que son URL, son document et sa taille actuels.  
  
3.  Quand vous accédez à une balise `FRAME` ou `IFRAME` à l'aide de la propriété <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> de <xref:System.Windows.Forms.HtmlWindow>, de la collection <xref:System.Windows.Forms.HtmlElement.Children%2A> ou de méthodes telles que <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> ou <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>, vous récupérez l'élément de frame.  Il représente les propriétés statiques du frame, y compris l'URL spécifiée dans le fichier HTML d'origine.  
  
## Frames et sécurité  
 L'accès aux frames est compliqué par le fait que le modèle DOM HTML managé implémente une mesure de sécurité appelée *sécurité des scripts interframe*.  Si un document contient un `FRAMESET` avec plusieurs `FRAME` dans différents domaines, ces `FRAME` ne peuvent pas interagir.  Autrement dit, un `FRAME` qui affiche du contenu de votre site web ne peut pas accéder aux informations dans un `FRAME` qui héberge un site tiers, tel que http:\/\/www.adatum.com\/.  Cette sécurité est implémentée au niveau de la classe <xref:System.Windows.Forms.HtmlWindow>.  Vous pouvez obtenir des informations générales sur un `FRAME` qui héberge un autre site web, telles que son URL, mais vous ne pourrez pas accéder à son <xref:System.Windows.Forms.HtmlWindow.Document%2A> ni modifier la taille ou l'emplacement de son `FRAME` ou `IFRAME` hébergeur.  
  
 Cette règle s'applique également aux fenêtres que vous ouvrez à l'aide des méthodes <xref:System.Windows.Forms.HtmlWindow.Open%2A> et <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A>.  Si la fenêtre que vous ouvrez est dans un domaine différent de celui de la page hébergée dans le contrôle <xref:System.Windows.Forms.WebBrowser>, vous ne pourrez pas déplacer cette fenêtre ni examiner son contenu.  Ces restrictions s'appliquent également si vous utilisez le contrôle <xref:System.Windows.Forms.WebBrowser> pour afficher un site web différent de celui utilisé pour déployer votre application Windows Forms.  Si vous utilisez la technologie de déploiement [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] pour installer votre application à partir du site web A et que vous utilisez <xref:System.Windows.Forms.WebBrowser> pour afficher le site web B, vous ne pourrez pas accéder aux données du site web B.  
  
 Pour plus d'informations sur les scripts de site à site, consultez [À propos des scripts interframes et de la sécurité](http://msdn.microsoft.com/library/ms533028.aspx).  
  
## Voir aussi  
 [Élément Frame &#124; Objet Frame](http://msdn.microsoft.com/library/ms535250.aspx)   
 [Utilisation du modèle objet de document HTML managé](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)