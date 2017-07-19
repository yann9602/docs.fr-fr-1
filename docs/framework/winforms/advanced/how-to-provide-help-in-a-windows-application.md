---
title: "Comment&#160;: fournir de l&#39;aide dans une application Windows | Microsoft Docs"
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
  - "formulaires, fourniture d'aide"
  - "Aide, applications Windows"
  - "HelpProvider (composant Windows Forms)"
  - "HTML (aide), Windows Forms"
  - "applications Windows, fourniture d'aide"
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: fournir de l&#39;aide dans une application Windows
Vous pouvez utiliser le composant <xref:System.Windows.Forms.HelpProvider> pour joindre des rubriques d'aide d'un fichier d'aide à des contrôles spécifiques sur les Windows Forms.  Le fichier d'aide peut être de type HTML ou HTMLHelp 1.x ou d'un format supérieur.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour associer l'aide aux contrôles  
  
1.  À partir de la **Boîte à outils**, faites glisser un composant <xref:System.Windows.Forms.HelpProvider> vers votre formulaire.  
  
     Le composant résidera dans la barre d'état située au bas de la fenêtre Concepteur Windows Forms.  
  
2.  Dans la fenêtre **Propriétés**, attribuez à la propriété <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> la valeur du fichier d'aide .chm, .col ou .htm.  
  
3.  Sélectionnez un autre contrôle figurant dans votre formulaire, et dans la fenêtre **Propriétés**, définissez la propriété [HelpKeyword](frlrfSystemWindowsFormsHelpProviderClassSetHelpKeywordTopic).  
  
     Il s'agit de la chaîne passée via le composant <xref:System.Windows.Forms.HelpProvider> à votre fichier d'aide pour appeler la rubrique d'aide appropriée.  
  
4.  Dans la fenêtre **Propriétés**, attribuez à la propriété [HelpNavigator](frlrfSystemWindowsFormsHelpProviderClassSetHelpNavigatorTopic) la valeur de l'énumération <xref:System.Windows.Forms.HelpNavigator>.  
  
     Cette valeur détermine la façon dont la propriété **HelpKeyword** est passée au système d'aide.  Le tableau suivant affiche les paramètres possibles et leurs descriptions.  
  
    |Nom du membre|Description|  
    |-------------------|-----------------|  
    |AssociateIndex|Indique que l'index d'une rubrique spécifiée est exécuté dans l'URL spécifiée.|  
    |Find|Indique que la page de recherche d'une URL spécifiée est affichée.|  
    |Index|Indique que l'index d'une URL spécifiée est affiché.|  
    |KeywordIndex|Spécifie un mot clé à rechercher et l'action à effectuer dans l'URL spécifiée.|  
    |TableOfContents|Indique que le sommaire du fichier d'aide HTML 1.0 est affiché.|  
    |Rubrique|Indique que la rubrique à laquelle l'URL spécifiée fait référence est affichée.|  
  
 Au moment de l'exécution, le fait d'appuyer sur F1 lorsque le contrôle \(dont vous avez défini les propriétés **HelpKeyword** et **HelpNavigator** \) a le focus ouvre le fichier d'aide associé à ce composant <xref:System.Windows.Forms.HelpProvider>.  
  
 Actuellement, la propriété **HelpNamespace** prend en charge des fichiers d'aide aux formats suivants : HTMLHelp 1.x, HTMLHelp 2.0 et HTML.  Par conséquent, vous pouvez attribuer à la propriété **HelpNamespace** une adresse http:\/\/, telle qu'une page Web.  Le cas échéant, elle ouvrira le navigateur par défaut à la page Web avec la chaîne spécifiée dans la propriété **HelpKeyword**  utilisée comme ancre.  L'ancre est utilisée pour accéder à une partie spécifique d'une page HTML.  
  
> [!IMPORTANT]
>  Prenez soin de vérifier toute information envoyée par un client avant de l'utiliser dans votre application.  Des utilisateurs malveillants peuvent tenter d'envoyer ou d'injecter un script, des instructions SQL ou d'autres types de code exécutables.  Avant d'afficher une entrée d'utilisateur, stockez\-la dans une base de données ou vérifiez\-la afin de vous assurer qu'elle ne comporte pas d'information potentiellement nuisible.  Vous pouvez par exemple utiliser une expression régulière pour rechercher des mots clés, tels que « SCRIPT », lorsque vous recevez une entrée d'utilisateur.  
  
 Vous pouvez également utiliser le composant <xref:System.Windows.Forms.HelpProvider> pour afficher une aide contextuelle, même si vous l'avez configuré pour afficher des fichiers d'aide relatifs aux contrôles de vos Windows Forms.  Pour plus d'informations, consultez [Comment : afficher l'aide contextuelle](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).  
  
## Voir aussi  
 [Comment : afficher l'aide contextuelle](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)   
 [Affichage sous forme d'info\-bulles de l'aide relative aux contrôles](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)   
 [Intégration de l'aide d'utilisateur dans les Windows Forms](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)   
 [Windows Forms](../../../../docs/framework/winforms/index.md)