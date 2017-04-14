---
title: "Comment&#160;: identifier la touche de modification activ&#233;e | Microsoft Docs"
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
  - "touches alt"
  - "touches de contrôle"
  - "événements (Windows Forms), clavier"
  - "événements (Windows Forms), souris"
  - "entrée au clavier"
  - "claviers, entrée au clavier"
  - "clés, touches alt"
  - "clés, touches de contrôle"
  - "clés, déterminer la dernière touche activée"
  - "clés, touches de modification"
  - "clés, touches MAJ"
  - "Keys.Alt (membre de l'énumération)"
  - "Keys.ControlKey (membre de l'énumération)"
  - "Keys.Shift (membre de l'énumération)"
  - "touches de modification"
  - "touches MAJ"
  - "entrée d'utilisateur, vérifier le clavier"
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: identifier la touche de modification activ&#233;e
Lorsque vous créez une application qui accepte les séquences de touches de l'utilisateur, vous pouvez également vouloir surveiller les touches de modification, telles que MAJ, ALT et CTRL.  Lorsque vous appuyez sur une touche de modification en association avec d'autres touches, ou encore avec des clics de souris, votre application peut répondre de façon appropriée.  Par exemple, si vous appuyez sur la lettre S, cela peut afficher simplement un « s » à l'écran, mais si vous appuyez simultanément sur les touches CTRL\+S, le document actuel peut être enregistré.  Si vous gérez l'événement <xref:System.Windows.Forms.Control.KeyDown>, la propriété <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> de <xref:System.Windows.Forms.KeyEventArgs> reçue par le gestionnaire d'événements spécifie les touches de modification utilisées.  Par ailleurs, la propriété <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> de <xref:System.Windows.Forms.KeyEventArgs> indique le caractère sur lequel vous avez appuyé ainsi que les touches de modification combinées à un opérateur de bits OR.  Toutefois, si vous gérez l'événement <xref:System.Windows.Forms.Control.KeyPress> ou un événement de souris, le gestionnaire d'événements ne reçoit pas cette information.  Dans ce cas, vous devez utiliser la propriété <xref:System.Windows.Forms.Control.ModifierKeys%2A> de la classe <xref:System.Windows.Forms.Control>.  Dans les deux cas, vous devez exécuter une opération AND au niveau du bit pour la valeur <xref:System.Windows.Forms.Keys> appropriée et pour la valeur que vous testez.  L'énumération <xref:System.Windows.Forms.Keys> offre des variations de chaque touche de modification ; il est donc important d'exécuter l'opération AND au niveau du bit avec la valeur correcte.  Par exemple, la touche MAJ est représentée par <xref:System.Windows.Forms.Keys>, <xref:System.Windows.Forms.Keys>, <xref:System.Windows.Forms.Keys> et <xref:System.Windows.Forms.Keys>. La valeur correcte à utiliser pour tester MAJ en tant que touche de modification est <xref:System.Windows.Forms.Keys>.  De la même façon, pour tester les touches CTRL et ALT comme touches de modification, vous devez utiliser les valeurs <xref:System.Windows.Forms.Keys> et <xref:System.Windows.Forms.Keys>, respectivement.  
  
> [!NOTE]
>  Les programmeurs Visual Basic peuvent également accéder aux informations sur les touches via la propriété <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A>.  
  
### Pour identifier la touche de modification activée  
  
-   Utilisez l'opérateur de bits `AND` avec la propriété <xref:System.Windows.Forms.Control.ModifierKeys%2A> et une valeur de l'énumération <xref:System.Windows.Forms.Keys> pour déterminer si une touche de modification spécifique est activée.  L'exemple de code suivant indique comment déterminer si la touche MAJ est activée dans un gestionnaire d'événements <xref:System.Windows.Forms.Control.KeyPress>.  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## Voir aussi  
 <xref:System.Windows.Forms.Keys>   
 <xref:System.Windows.Forms.Control.ModifierKeys%2A>   
 [Entrée au clavier dans une application Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)   
 [How to: Determine If CapsLock is On in Visual Basic](http://msdn.microsoft.com/fr-fr/91e60f5c-dd61-4222-ba5f-39af803afd8c)