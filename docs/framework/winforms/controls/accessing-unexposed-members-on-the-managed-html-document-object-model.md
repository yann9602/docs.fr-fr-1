---
title: "Accès aux membres non exposés sur le modèle objet de document HTML managé"
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
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dda2581ceed854fa5121076f0c7b9df414bffe52
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>Accès aux membres non exposés sur le modèle objet de document HTML managé
Le managé HTML modèle DOM (Document Object) contient une classe appelée <xref:System.Windows.Forms.HtmlElement> qui expose les propriétés, méthodes et événements que tous les éléments HTML ont en commun. Dans certains cas, toutefois, vous devez accéder aux membres de l’interface managée n’expose pas directement. Cette rubrique examine deux façons d’accéder aux membres non exposés, y compris [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] et les fonctions VBScript définies à l’intérieur d’une page Web.  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>L’accès aux membres non exposés via des Interfaces managées  
 <xref:System.Windows.Forms.HtmlDocument>et <xref:System.Windows.Forms.HtmlElement> fournissent quatre méthodes qui permettent d’accéder aux membres non exposés. Le tableau suivant indique les types et leurs méthodes correspondantes.  
  
|Type de membre|Méthode (s)|  
|-----------------|-----------------|  
|Propriétés (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|Méthodes|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|Événements (<xref:System.Windows.Forms.HtmlDocument>)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|Événements (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|Événements (<xref:System.Windows.Forms.HtmlWindow>)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 Lorsque vous utilisez ces méthodes, il est supposé que vous disposez d’un élément du type sous-jacent correct. Supposons que vous souhaitez écouter le `Submit` événement d’un `FORM` page de l’élément sur un élément HTML, afin que vous pouvez effectuer un prétraitement sur le `FORM`de valeurs avant que l’utilisateur les envoie au serveur. Dans l’idéal, si vous contrôlez le code HTML, vous devez définir le `FORM` d’avoir une valeur unique `ID` attribut.  
  
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
  
 Après le chargement de cette page dans le <xref:System.Windows.Forms.WebBrowser> (contrôle), vous pouvez utiliser la <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> pour récupérer le `FORM` au moment de l’exécution à l’aide `form1` comme argument.  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a>L’accès à des Interfaces non managées  
 Vous pouvez également accéder à des membres non exposés sur le modèle DOM HTML managé en utilisant les interfaces non managées de modèle COM (Component Object) exposées par chaque classe DOM. Cela est recommandé si vous devez effectuer plusieurs appels par rapport aux membres non exposés ou si les membres non exposés retournent d’autres interfaces non managées non encapsulés par le DOM. HTML managé  
  
 Le tableau suivant montre toutes les interfaces non managées exposées via le DOM. HTML managé Cliquez sur chaque lien pour obtenir une explication de son utilisation et par exemple de code.  
  
|Type|Interface non managée|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 Le moyen le plus simple d’utiliser les interfaces COM doit ajouter une référence à la bibliothèque DOM HTML non managée (MSHTML.dll) à partir de votre application, bien que ce soit non pris en charge. Pour plus d’informations, consultez [934368 de l’Article de Base de connaissances](http://support.microsoft.com/kb/934368).  
  
## <a name="accessing-script-functions"></a>L’accès aux fonctions de Script  
 Une page HTML peut définir une ou plusieurs fonctions à l’aide d’un langage de script comme [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] ou VBScript. Ces fonctions sont placées à l’intérieur d’un `SCRIPT` page dans la page et peut être exécuté à la demande ou en réponse à un événement sur le modèle DOM.  
  
 Vous pouvez appeler des fonctions de script que vous définissez dans une page HTML à l’aide du <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> (méthode). Si la méthode de script retourne un élément HTML, vous pouvez utiliser un cast pour convertir ce résultat en un <xref:System.Windows.Forms.HtmlElement>. Pour plus d’informations et l’exemple de code, consultez <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du modèle DOM HTML managé](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
