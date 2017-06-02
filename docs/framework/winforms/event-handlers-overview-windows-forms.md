---
title: "Vue d&#39;ensemble des gestionnaires d&#39;&#233;v&#233;nements (Windows Forms) | Microsoft Docs"
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
  - "gestionnaires d'événements, à propos des gestionnaires d'événements"
  - "gestion des événements, Windows Forms"
  - "Windows Forms, gestion des événements"
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Vue d&#39;ensemble des gestionnaires d&#39;&#233;v&#233;nements (Windows Forms)
Un gestionnaire d'événements est une méthode liée à un événement.  Lorsque l'événement est déclenché, le code qu'il contient est exécuté.  Chaque gestionnaire d'événements fournit deux paramètres vous permettant de gérer l'événement comme il convient.  L'exemple suivant montre un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.Control.Click> d'un contrôle <xref:System.Windows.Forms.Button>.  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)   
{  
  
}  
  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 Le premier paramètre, `sender`, fournit une référence à l'objet qui a déclenché l'événement.  Le second paramètre, `e` dans l'exemple ci\-dessus, passe un objet propre à l'événement géré.  En référençant les propriétés de l'objet \(et parfois ses méthodes\), vous pouvez obtenir des informations, telles que l'emplacement de la souris pour les événements de souris ou les données transférées pour les événements de glissement\-déplacement.  
  
 En général, chaque événement produit un gestionnaire avec un type event\-object pour le second paramètre.  Certains gestionnaires d'événements, tels que ceux des événements <xref:System.Windows.Forms.Control.MouseDown> et <xref:System.Windows.Forms.Control.MouseUp>, ont le même type d'objet pour le second paramètre.  Dans ce cas, vous pouvez utiliser le même gestionnaire pour les deux événements.  
  
 Vous pouvez également utiliser un seul gestionnaire pour gérer le même événement pour plusieurs contrôles.  Prenons l'exemple d'un formulaire contenant un groupe de contrôles <xref:System.Windows.Forms.RadioButton>. Vous pouvez créer un seul gestionnaire pour l'événement <xref:System.Windows.Forms.Control.Click> et lier l'événement <xref:System.Windows.Forms.Control.Click> de chaque contrôle à ce gestionnaire.  Pour plus d'informations, consultez [Comment : connecter plusieurs événements à un même gestionnaire d'événements dans les Windows Forms](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).  
  
## Voir aussi  
 [Création de gestionnaires d'événements dans les Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)   
 [Vue d'ensemble des événements](../../../docs/framework/winforms/events-overview-windows-forms.md)