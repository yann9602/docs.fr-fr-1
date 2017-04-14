---
title: "Gestion des entr&#233;es utilisateur | Microsoft Docs"
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
  - "contrôles personnalisés (Windows Forms), événements de clavier à l'aide du code"
  - "contrôles personnalisés (Windows Forms), événements de souris à l'aide du code"
  - "contrôles personnalisés (Windows Forms), entrée d'utilisateur à l'aide du code"
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Gestion des entr&#233;es utilisateur
Cette rubrique décrit les principaux événements de clavier et de souris fournis par <xref:System.Windows.Forms.Control?displayProperty=fullName>.  Lors de la gestion d'un événement, les auteurs de contrôles doivent substituer la méthode `On`*NomÉvénement* protégée plutôt que d'attacher un délégué à l'événement.  Pour obtenir une révision des événements, consultez [Raising Events from a Component](../Topic/Raising%20Events%20from%20a%20Component.md).  
  
> [!NOTE]
>  S'il n'y a pas de données associées à un événement, une instance de la classe de base <xref:System.EventArgs> est passée comme argument à la méthode `On`*NomÉvénement*.  
  
## Événements de clavier  
 Les événements de clavier courants que votre contrôle peut gérer sont <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress> et <xref:System.Windows.Forms.Control.KeyUp>.  
  
|Nom de l'événement|Méthode à substituer|Description de l'événement|  
|------------------------|--------------------------|--------------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|Déclenché uniquement lors du premier appui d'une touche.|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|Déclenché à chaque appui d'une touche.  Si une touche est maintenue enfoncée, un événement <xref:System.Windows.Forms.Control.KeyPress> est déclenché selon le taux de répétition défini par le système d'exploitation.|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|Déclenché lorsqu'une touche est relâchée.|  
  
> [!NOTE]
>  La gestion des entrées au clavier est considérablement plus complexe que la substitution des événements du tableau précédent et n'est pas traitée dans cette rubrique.  Pour plus d'informations, consultez [Entrées d'utilisateur dans les Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).  
  
## Événements de souris  
 Les événements de souris que votre contrôle peut gérer sont <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove> et <xref:System.Windows.Forms.Control.MouseUp>.  
  
|Nom de l'événement|Méthode à substituer|Description de l'événement|  
|------------------------|--------------------------|--------------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|Déclenché lorsque le bouton de la souris est enfoncé alors que le pointeur se trouve sur le contrôle.|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|Déclenché lorsque le pointeur de la souris pénètre pour la première fois dans la région du contrôle.|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|Déclenché lorsque le pointeur de la souris passe sur le contrôle.|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|Déclenché lorsque le pointeur de la souris quitte la région du contrôle.|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|Déclenché lorsque le pointeur de la souris se déplace dans la région du contrôle.|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|Déclenché lorsque le bouton de la souris est relâché alors que le pointeur se trouve sur le contrôle ou quitte la région du contrôle.|  
  
 Le fragment de code suivant montre un exemple de substitution de l'événement <xref:System.Windows.Forms.Control.MouseDown>.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 Le fragment de code suivant montre un exemple de substitution de l'événement <xref:System.Windows.Forms.Control.MouseMove>.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 Le fragment de code suivant montre un exemple de substitution de l'événement <xref:System.Windows.Forms.Control.MouseUp>.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 Pour obtenir le code source complet pour l'exemple `FlashTrackBar`, consultez [Comment : créer un contrôle Windows Forms qui affiche la progression](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## Voir aussi  
 [Événements dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)   
 [Définition d'un événement](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)   
 [Événements](../../../../docs/standard/events/index.md)   
 [Entrées d'utilisateur dans les Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md)