---
title: "Acc&#232;s aux membres non expos&#233;s sur le mod&#232;le objet de document HTML manag&#233; | Microsoft Docs"
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
  - "modèle DOM HTML managé, accéder aux membres non exposés"
  - "membres non exposés"
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Acc&#232;s aux membres non expos&#233;s sur le mod&#232;le objet de document HTML manag&#233;
Le modèle DOM \(Document Object Model\) HTML managé contient une classe appelée <xref:System.Windows.Forms.HtmlElement>, qui expose les propriétés, les méthodes et les événements que tous les éléments HTML ont en commun.  Toutefois, vous devrez quelquefois accéder aux membres que l'interface managée n'expose pas directement.  Cette rubrique examine deux façons d'accéder aux membres non exposés, y compris les fonctions [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] et VBScript définies dans une page Web.  
  
## Accès aux membres non exposés via des interfaces managées  
 <xref:System.Windows.Forms.HtmlDocument> et <xref:System.Windows.Forms.HtmlElement> fournissent quatre méthodes qui permettent l'accès aux membres non exposés.  Le tableau suivant affiche les types et leurs méthodes correspondantes.  
  
|Type de membre|Méthode\(s\)|  
|--------------------|------------------|  
|Propriétés \(<xref:System.Windows.Forms.HtmlElement>\)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|Méthodes|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|Événements \(<xref:System.Windows.Forms.HtmlDocument>\)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|Événements \(<xref:System.Windows.Forms.HtmlElement>\)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|Événements \(<xref:System.Windows.Forms.HtmlWindow>\)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 Lorsque vous utilisez ces méthodes, vous devez posséder un élément du type sous\-jacent correct.  Supposons que vous souhaitiez écouter l'événement `Submit` d'un élément `FORM` figurant dans une page HTML afin de pouvoir exécuter un prétraitement sur les valeurs de `FORM` avant que l'utilisateur ne les soumette au serveur.  Idéalement, si vous contrôlez les données HTML, vous définissez `FORM` de façon à ce qu'il dispose d'un attribut `ID` unique.  
  
```  
<HTML>  
  
    <HEAD>  
        <TITLE>Form Page</TITLE>  
    </HEAD>  
  
    <BODY>  
        <FORM ID="form1">  
             ... form fields defined here ...  
        </FORM>  
    </BODY>  
  
</HTML>  
```  
  
 Après avoir chargé cette page dans le contrôle <xref:System.Windows.Forms.WebBrowser>, vous pouvez utiliser la méthode <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> pour récupérer `FORM` au moment de l'exécution en utilisant `form1` comme argument.  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## Accès aux interfaces non managées  
 Vous pouvez également accéder aux membres non exposés du modèle DOM HTML managé en utilisant les interfaces COM \(Component Object Model\) non managées exposées par chaque classe DOM.  Cela est recommandé si vous devez effectuer plusieurs appels concernant des membres non exposés ou si les membres non exposés retournent d'autres interfaces non managées, non encapsulées par le modèle DOM HTML managé.  
  
 Le tableau suivant affiche toutes les interfaces non managées exposées par l'intermédiaire du modèle DOM HTML managé.  Cliquez sur chaque lien pour obtenir une explication de son utilisation et pour afficher un exemple de code.  
  
|Type|Interface non managée|  
|----------|---------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 La façon la plus facile d'utiliser les interfaces COM consiste à ajouter une référence à la bibliothèque DOM HTML non managée \(MSHTML.dll\) de votre application, bien que ce ne soit pas prise en charge.  Pour plus d'informations, consultez [Article 934368 de la Base de connaissances](http://support.microsoft.com/kb/934368).  
  
## Accès aux fonctions de script  
 Une page HTML peut définir une ou plusieurs fonctions en utilisant un langage de script, tel que [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] ou VBScript.  Ces fonctions sont placées dans une page `SCRIPT` au sein de la page et peuvent être exécutées à la demande ou en réponse à un événement survenu dans le modèle DOM.  
  
 Vous pouvez appeler toutes les fonctions de script que vous définissez dans une page HTML à l'aide de la méthode <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.  Si la méthode de script retourne un élément HTML, vous pouvez utiliser un cast pour convertir ce résultat en un <xref:System.Windows.Forms.HtmlElement>.  Pour plus d'informations et pour obtenir un exemple de code, consultez <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.  
  
## Voir aussi  
 [Utilisation du modèle objet de document HTML managé](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)