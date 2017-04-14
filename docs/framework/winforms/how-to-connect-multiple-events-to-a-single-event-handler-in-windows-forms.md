---
title: "Comment&#160;: connecter plusieurs &#233;v&#233;nements &#224; un m&#234;me gestionnaire d&#39;&#233;v&#233;nements dans les Windows Forms | Microsoft Docs"
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
  - "gestionnaires d'événements (Windows Forms), connecter les événements à"
  - "événements (Windows Forms), connecter plusieurs événements à un seul gestionnaire d'événements"
  - "éléments de menu, multicasting des méthodes de gestion d'événements"
  - "menus, méthodes de gestion d'événements pour plusieurs éléments de menu"
  - "contrôles Windows Forms, événements"
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: connecter plusieurs &#233;v&#233;nements &#224; un m&#234;me gestionnaire d&#39;&#233;v&#233;nements dans les Windows Forms
Dans votre design d'application, il peut parfois être nécessaire d'utiliser un même gestionnaire pour plusieurs événements ou d'avoir plusieurs événements effectuant une même procédure.  Par exemple, si tous deux exposent la même fonctionnalité, le fait d'avoir une commande de menu déclenchant le même événement qu'un bouton de votre formulaire peut vous faire gagner un temps précieux.  Pour cela, utilisez le mode Événements de la fenêtre Propriétés en C\# ou le mot clé `Handles` et les zones déroulantes **Nom de la classe** et **Nom de la méthode** dans l'éditeur de code Visual Basic.  
  
### Pour connecter plusieurs événements à un seul gestionnaire d'événements en Visual Basic  
  
1.  Cliquez avec le bouton droit sur le formulaire et choisissez **Afficher le code**.  
  
2.  Dans la zone déroulante **Nom de la classe**, sélectionnez un des contrôles auquel vous voulez associer le gestionnaire d'événements.  
  
3.  Dans la zone déroulante **Nom de la méthode**, sélectionnez un des événements auquel vous voulez associer le gestionnaire d'événements.  
  
4.  L'éditeur de code insère le gestionnaire  d'événements approprié et place le point d'insertion dans la méthode.  Dans l'exemple ci\-dessous, il s'agit de l'événement <xref:System.Windows.Forms.Control.Click> du contrôle <xref:System.Windows.Forms.Button>.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  Ajoutez éventuellement les autres événements que ce gestionnaire va devoir gérer à la clause `Handles` .  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  Ajoutez le code approprié au gestionnaire d'événements.  
  
### Pour lier plusieurs événements à un seul gestionnaire d'événements dans C\#  
  
1.  Sélectionnez le contrôle auquel vous voulez connecter un gestionnaire d'événements.  
  
2.  Dans la fenêtre Propriétés, cliquez sur le bouton **Événements** \(![Bouton Événements](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton\_PropertiesWindow")\).  
  
3.  Cliquez sur le nom de l'événement à gérer.  
  
4.  Dans la section valeur en regard du nom d'événement, cliquez sur le bouton pour afficher la liste déroulante des gestionnaires d'événements correspondant à la signature de la méthode de l'événement à gérer.  
  
5.  Sélectionnez dans la liste le gestionnaire d'événements approprié.  
  
     Le code sera ajouté au formulaire pour lier l'événement au gestionnaire existant.  
  
## Voir aussi  
 [Création de gestionnaires d'événements dans les Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)   
 [Vue d'ensemble des gestionnaires d'événements](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)